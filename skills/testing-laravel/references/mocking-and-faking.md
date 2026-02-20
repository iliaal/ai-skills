# Mocking and Faking

Fake facades BEFORE the action that triggers them. Assert AFTER.

## Queue Faking

```php
public function test_dispatches_job_on_post_creation(): void
{
    Queue::fake();

    $user = User::factory()->create();
    $this->actingAs($user)
        ->postJson('/api/posts', ['title' => 'Test', 'body' => 'Content']);

    Queue::assertPushed(ProcessPost::class, fn ($job) => $job->post->title === 'Test');
    Queue::assertPushed(ProcessPost::class, 1); // exact count
}
```

## Event Faking

```php
public function test_fires_event_on_publish(): void
{
    Event::fake([PostPublished::class]);

    $post = Post::factory()->create();
    $post->publish();

    Event::assertDispatched(PostPublished::class, fn ($e) => $e->post->id === $post->id);
}
```

## Notification Faking

```php
public function test_sends_notification_to_post_author(): void
{
    Notification::fake();

    $post = Post::factory()->create();
    $post->approve();

    Notification::assertSentTo($post->user, PostApproved::class);
}
```

## Mail Faking

```php
public function test_sends_welcome_email(): void
{
    Mail::fake();

    $this->postJson('/api/register', [
        'email' => 'new@example.com',
        'password' => 'secret123',
    ]);

    Mail::assertSent(WelcomeMail::class, fn ($mail) => $mail->hasTo('new@example.com'));
}
```

## Storage Faking

```php
public function test_uploads_avatar(): void
{
    Storage::fake('public');
    $user = User::factory()->create();
    $file = UploadedFile::fake()->image('avatar.jpg');

    $this->actingAs($user)
        ->postJson('/api/avatar', ['avatar' => $file])
        ->assertOk();

    Storage::disk('public')->assertExists("avatars/{$file->hashName()}");
}
```

## HTTP Faking (External APIs)

```php
public function test_fetches_data_from_external_api(): void
{
    Http::fake([
        'api.example.com/*' => Http::response(['data' => ['id' => 1, 'name' => 'Test']], 200),
    ]);

    $service = app(ExternalApiService::class);
    $result = $service->fetchData();

    $this->assertSame('Test', $result['name']);

    Http::assertSent(fn ($request) =>
        $request->url() === 'https://api.example.com/data'
        && $request->hasHeader('Authorization')
    );
}
```

## Bus Faking (Batches & Chains)

```php
public function test_dispatches_batch(): void
{
    Bus::fake();

    $this->postJson('/api/import', ['file' => $file]);

    Bus::assertBatched(fn ($batch) => $batch->jobs->count() === 10);
}

public function test_dispatches_chain(): void
{
    Bus::fake();

    $this->postJson('/api/process');

    Bus::assertChained([ValidateJob::class, ProcessJob::class, NotifyJob::class]);
}
```

## Action Testing with resolve() + swap()

For invokable action classes, resolve from the container so DI works. Use `swap()` to replace dependencies with mocks:

```php
public function test_processes_order_and_notifies(): void
{
    $user = User::factory()->create();
    $order = Order::factory()->for($user)->create();

    // Mock dependency action and swap into container
    $calculateTotal = Mockery::mock(CalculateOrderTotalAction::class);
    $calculateTotal->shouldReceive('__invoke')
        ->once()
        ->with($order)
        ->andReturn(10000);
    $this->swap(CalculateOrderTotalAction::class, $calculateTotal);

    $notifyAction = Mockery::mock(NotifyOrderCreatedAction::class);
    $notifyAction->shouldReceive('__invoke')->once()->with($order);
    $this->swap(NotifyOrderCreatedAction::class, $notifyAction);

    // resolve() pulls from container with mocked dependencies injected
    $result = resolve(ProcessOrderAction::class)($order);

    $this->assertSame(10000, $result->total);
}
```

Only mock what you own — for external services (Stripe, etc.), create a service abstraction with a driver pattern and swap the driver config in tests, instead of mocking the SDK directly.

## Mockery (Service Mocking)

For non-facade services where DI mocking is needed:

```php
public function test_sends_notification_to_active_users(): void
{
    $repository = Mockery::mock(UserRepository::class);
    $repository->shouldReceive('findActive')
        ->once()
        ->andReturn(User::factory()->count(2)->make());

    $this->app->instance(UserRepository::class, $repository);

    $service = app(NotificationService::class);
    $result = $service->notifyActiveUsers('Important message');

    $this->assertSame(2, $result->count());
}
```

Prefer Laravel facade fakes over Mockery when both options exist. Use Mockery for custom services and repository interfaces.
