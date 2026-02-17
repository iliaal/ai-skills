---
name: meta-prompting
description: >-
  Enhanced reasoning patterns via slash commands (/think, /verify, /adversarial,
  /edge, /compare, /confidence, /budget, /constrain, /json, /analyze, /trade) or
  natural language ("argue against", "what could break", "show reasoning", "deep
  review", "meta-prompts", "thinking modes").
---

# Meta-Prompting

Enhanced reasoning via `/commands` or natural language. Commands combine left-to-right: `/verify /adversarial`. Auto-trigger when context warrants — note which pattern applied.

## Patterns

**`/think`** | `/show` — Show reasoning step-by-step: decision points, alternatives considered, why each accepted/rejected.

**`/adversarial`** | `/argue` — After answering, argue against it. 3 strongest counterarguments ranked by severity. Identify blind spots and unstated assumptions.

**`/constrain`** | `/strict` — Tight constraints: 3 sentences max, cite sources, no hedging. Override inline: `/constrain 5 sentences`.

**`/json`** | `/format` — Respond in valid JSON code block, no surrounding prose unless asked. Default schema:
```json
{"analysis": "", "confidence_score": 0-100, "methodology": "", "limitations": []}
```
Custom keys: `/json {keys: summary, risks, recommendation}`

**`/budget`** | `/deep` — Extended thinking space (~500 words) showing dead ends and reasoning pivots, then clearly separated final answer.

**`/compare`** | `/vs` — Compare options as table. Default dimensions: speed, accuracy, cost, complexity, maintenance. Custom: `/compare [dim1, dim2]`.

**`/confidence`** | `/conf` — Rate each claim 0-100. Flag below 70 as SPECULATIVE. Group by tier: HIGH (85+), MEDIUM (70-84), LOW (<70).

**`/edge`** | `/break` — 5+ inputs/scenarios that break the approach. Code: null/empty, concurrency, overflow, encoding, auth bypass. Strategies: market conditions, timing, dependencies.
*Auto-triggers on: security, validation, parsing contexts.*

**`/verify`** | `/check` — Three phases: (1) **Answer** direct response, (2) **Challenge** 3 ways it could be wrong, (3) **Verify** investigate each, update if needed. Mark final as `VERIFIED ANSWER:` or `REVISED ANSWER:`.
*Auto-triggers on: architecture decisions, critical choices, "Am I right?"*

## Combos

**`/analyze`** = `/think` + `/edge` + `/verify` — Code reviews, architecture, security-sensitive work.
*Auto-triggers on: code review requests.*

**`/trade`** = `/confidence` + `/adversarial` + `/edge` — Trade ideas, position analysis, market thesis.
*Auto-triggers on: trade/position discussions.*

## Conventions

- Separate combined pattern outputs with `---`
- Keep core answer prominent — patterns enhance, not bury the response
- New patterns can be defined mid-conversation ("Add `/eli5` for explain like I'm 5") — applied for the session
