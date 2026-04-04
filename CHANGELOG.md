# Changelog

All notable changes to ai-skills will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/).
Versions track the upstream [compound-engineering plugin](https://github.com/iliaal/compound-engineering-plugin).

## [2.52.1] - 2026-04-04

### Changed

- **planning**: Vertical slicing principle in anti-patterns table and verify checklist. Task duration heuristic (>2h = split) in phase sizing rules.
- **frontend-design**: Four new banned AI patterns -- colored icon circles, left-border accent cards, cookie-cutter section rhythm, bubbly rounded containers. Fixed stock imagery alternative.
- **writing-tests**: DAMP over DRY principle and test pyramid ratios (~80/15/5) as separate subsections. DAMP caveat added to "When Stuck" table.
- **debugging**: Reduce step (1c) with stopping criterion -- strip to minimal failing case before investigating.
- **nodejs-backend**: Contract-first principle with named artifact (route schemas). Reconciled with existing OpenAPI generation guidance.
- **verification-before-completion**: Removed duplicate empty Integration heading.

## [2.52.0] - 2026-04-02

### Added

- **debugging**: Three new reference docs -- `defense-in-depth.md` (4-layer validation pattern), `competing-hypotheses.md` (full ACH methodology with 6 failure categories and evidence scoring), `root-cause-tracing.md` (backward call-chain tracing with test pollution detection).
- **code-review**: `reliability-patterns.md` reference -- error handling, timeouts, retries, circuit breakers, resource cleanup, queue resilience. New reliability agent in deep-review specialist roster.
- **code-review**: `false-positive-suppression.md` reference -- 8 suppression categories with override rules.
- **frontend-design**: `redesign-audit.md` reference -- 60+ checks across typography, color, layout, interactivity, content, and component patterns for existing UI improvement.
- **writing**: Quality Gate section with 5-dimension scoring rubric (Directness, Rhythm, Trust, Authenticity, Density) and 8-item quick audit checklist.
- **writing/phrases.md**: Three structural anti-pattern categories (Dramatic Fragmentation, Formulaic Constructions, Narrator-from-a-Distance).
- **writing-tests**: Four new rationalization table entries (hard-to-test code, understanding-first delay, prototype excuse, deadline pressure).
- **postgresql**: Expanded anti-patterns table (7 patterns) with 3 detection queries (slow queries, table bloat, unused indexes).
- **simplifying-code**: Two AI slop patterns (redundant error wrapping, verbose stdlib reimplementations).
- **verification-before-completion**: `system-wide-test-check.md` reference -- blast-radius verification for task completion.
- **receiving-code-review**: Headless mode extracted to `references/headless-mode.md`.

### Changed

- **meta-prompting**: Description trimmed to under 80 tokens while preserving all 15 slash command triggers.
- **code-review**: Description trimmed. FP suppression consolidated into reference file.
- **verification-before-completion**: Description trimmed with "Use when" trigger.
- **planning**: Clarified `.plan/` overwrite scope (between features vs within multi-phase). Strengthened no-placeholder rule.
- **brainstorming**: Phases 4-5 trimmed to delegate orchestration to `workflows:brainstorm` command.
- **orchestrating-swarms**: Best Practices trimmed from 7 to 4 items (removed generic agent hygiene).
- **writing**: Self-Check trimmed from 11 to 5 items (merged overlap with Quality Gate).
- **compound-docs**: "BLOCK until valid" replaced with actionable "fix and re-run" fallback.

## [2.51.0] - 2026-03-31

### Added

- **planning**: Execution posture signals (test-first, characterization-first, external-delegate) for phase-level implementation sequencing.
- **planning**: Plan deepening section for targeted strengthening of existing plans.
- **frontend-design**: Design variance parameters (DESIGN_VARIANCE, MOTION_INTENSITY, VISUAL_DENSITY) to prevent aesthetic convergence.
- **frontend-design**: `references/banned-ai-patterns.md` -- comprehensive banned AI design patterns (layout, color, typography, decoration, interaction, content).

## [2.50.0] - 2026-03-29

### Added

- **code-review**: Deep multi-agent review mode -- auto-detects complex diffs (3+ signals) and dispatches parallel specialist agents (correctness, security, testing, maintainability, performance). New `references/deep-review.md` with agent prompt templates, merge algorithm, and model selection.
- **code-review**: Confidence rubric (0.0-1.0 scoring) with false-positive suppression categories. Intent verification in review process.
- **receiving-code-review**: Headless mode for programmatic triage (AUTO-FIX / AUTO-DECLINE / ESCALATE classification). Prior-feedback check on re-reviews.
- **document-review**: 5 conditional review lenses (Product, Design, Security, Scope guardian, Adversarial) activated by document signals.
- **orchestrating-swarms**: Handoff protocol for structured agent-to-agent transfers. Coordination models comparison (stateless vs stateful). Reference map table.
- **frontend-design**: 6 banned AI design patterns (purple gradient, centered-cards layout, uniform corners, accent lines, emoji headers, generic placeholder copy).
- **git-worktree**: Environment detection (existing worktree, sandbox, bare repo).
- **planning**: Test discovery phase for existing projects. Verify section with 6 measurable criteria.
- **verification-before-completion**: 3 new rationalization entries (just this once, CI will catch it, zero issues on first pass).
- **brainstorming**: Success criteria section.
- **writing**: Short-form/long-form mode labels for self-check. Two new self-check items (contrast structures, vague declaratives).

### Changed

- **agent-native-architecture**: Converted non-standard XML tags to standard markdown. Added H1 heading. Removed duplicate References section. Linked orphan `quick-start.md`.
- **orchestrating-swarms**: Removed duplicate Best Practices rules 1 and 8 (covered by Verify and Dispatch Discipline).
- **php-laravel**: Removed duplicate Anti-Patterns section (4/5 entries already covered; moved unique entry to Discipline).
- **postgresql**: Removed 10 duplicate Anti-Patterns entries (kept 1 genuinely new).
- **linux-bash-scripting**: Compressed Linux-Specific section to non-obvious items only (GNU coreutils differences, timeout).
- **compound-docs**: Replaced verbose Integration Points block with slim Integration section.
- **reflect**: Replaced vague "auto memory system" with concrete file path. Folded Proactive Trigger into Process step.
- **document-review**: Renumbered steps 1-8 sequentially (was 1, 2, 2b, 3, 4, 5, 5b, 6). Broadened description to cover specs, ADRs, and any doc.

## [2.48.0] - 2026-03-22

### Improved

- **brainstorming** -- explore project context before questions, isolation/clarity design principles in Phase 3, collapsed redundant YAGNI/Incremental Validation/Integration sections
- **debugging** -- under-pressure inoculation in Iron Law, trimmed Common Patterns to 3 non-obvious entries, removed duplicate anti-pattern row
- **verification-before-completion** -- "I'm tired" and spirit-over-letter rationalization rows
- **receiving-code-review** -- deleted redundant Forbidden Responses (covered by Common Mistakes table)
- **planning** -- zero-context engineer framing for tasks, merged Relationship + Integration sections
- **postgresql** -- pg_stat_statements slow-query detection, table bloat check
- **php-laravel** -- DatabaseTransactions/DatabaseMigrations distinction, Http::fake(), Gate::forUser(), coverage target, dropped stale "since Laravel 9" pin, fixed Kernel.php framing for Laravel 11+

## [2.47.2] - 2026-03-21

### Improved

- **code-review** -- scope drift check integrated into review process step 1, search-before-recommending anti-pattern
- **debugging** -- sanitize-before-search rule, scope lock on hypothesis, structured debug report format, recurring fix site detection
- **writing** -- changelog voice section (sell test, contributor subsection, verb tense)
- **verification-before-completion** -- review staleness check, merged Red Flags into Rationalization Prevention
- **planning** -- scope challenge trigger (8+ files or 2+ new classes)
- **nodejs-backend** -- new `references/api-design.md` (cursor pagination, filtering, sorting, deprecation)
- **react-frontend** -- flaky test quarantine workflow in e2e-testing reference
- **simplifying-code** -- placeholder stub bans in AI Slop Removal
- **frontend-design** -- extracted Creative Arsenal and Redesigning to references
- **agent-native-architecture** -- extracted quick-start template to references, flattened reference index
- **linux-bash-scripting** -- added output format definition

## [2.45.8] - 2026-03-18

### Fixed

- **brainstorming/planning** -- explicit handoff: brainstorm outputs approved spec to `docs/brainstorms/`, planning takes it as input
- **code-review** -- prior comments instruction bolded and repositioned for visibility

## [2.0.5] - 2026-03-17

### Changed

- **code-review** -- fetch MR/PR discussions before writing findings to avoid re-raising resolved issues
- **code-review** -- use diff content directly for added files instead of reading from working tree on remote branches

## [2.0.4] - 2026-03-14

### Changed

- **meta-prompting** -- added output format awareness to intro line
- **writing** -- converted Self-Check to 4-step procedural checklist with done definition
- **pinescript** -- added Workflow section with development cycle and overfit detection
- **linux-bash-scripting** -- added Verify section (shellcheck + shfmt + edge cases)
- **nodejs-backend** -- added verify line to Discipline section
- **postgresql** -- added Verify section (EXPLAIN ANALYZE + FK check)
- **python-services** -- added verify line to Discipline section

## [2.0.3] - 2026-03-14

### Changed

- **code-review** -- added untracked files to scope resolution fallback chain
- **receiving-code-review** -- added `gh api` reply command for inline PR thread replies
- **brainstorming** -- added trivially-scoped escape hatch and multi-subsystem decomposition signal
- **planning** -- added execution handoff line pointing to `workflows:work`
- **simplifying-code** -- added dense transform chain pattern to Smell-to-Fix table
- **frontend-design** -- added Motion library performance guardrails, strengthened Tailwind version check
- **tailwind-css** -- expanded border radius v3-to-v4 rename table
- **refine-prompt** -- added missing-context sub-checklist to Context assessment row
- **verification-before-completion** -- added verification phase order (build, typecheck, lint, test, diff)
- **react-frontend** -- added RSC safety rules to App Router decision section

## [2.0.0] - 2026-02-27

### Changed

- **Mirror mode** -- this repo is now a read-only mirror of skills from the [compound-engineering plugin](https://github.com/iliaal/compound-engineering-plugin). All edits happen upstream.
- **Skill consolidation (19 > 31 skills)** -- all plugin skills are now mirrored here, including 14 previously plugin-native skills and updated versions of all existing skills.

### Added

- **agent-native-architecture** -- build AI agents using prompt-native architecture
- **brainstorming** -- explore requirements and approaches through dialogue
- **compound-docs** -- capture solved problems as categorized documentation
- **document-review** -- improve documents through structured self-review
- **file-todos** -- file-based todo tracking system
- **frontend-design** -- create production-grade frontend interfaces
- **git-worktree** -- manage Git worktrees for parallel development
- **orchestrating-swarms** -- multi-agent swarm orchestration
- **receiving-code-review** -- process review feedback critically
- **verification-before-completion** -- fresh verification evidence before completion claims
- **writing-tests** -- generic test discipline: quality, anti-patterns, rationalization resistance

### Removed

- **testing-laravel** -- absorbed into php-laravel (testing content as references)
- **testing-react** -- absorbed into react-frontend (testing content as references)

## [1.4.3] - 2026-02-22

### Changed

- **writing** -- add "PR descriptions" and "plans" to trigger keywords

## [1.4.2] - 2026-02-22

### Changed

- **testing-laravel**, **testing-react** -- add "review tests" and "check tests" trigger keywords to descriptions

## [1.4.1] - 2026-02-22

### Changed

- **php-laravel** -- change testing framework from Pest to PHPUnit

## [1.4.0] - 2026-02-22

### Changed

- **debugging** -- add concurrency section (async race conditions, deadlocks, connection pool exhaustion) and postmortem template
- **php-laravel** -- add PHP 8.4 features (property hooks, asymmetric visibility, `new` chaining, `array_find`/`array_any`/`array_all`), PHPStan level 8+, OPcache/JIT/preloading, Laravel ecosystem reference file

## [1.3.1] - 2026-02-21

### Changed

- **debugging** -- add explicit root cause analysis section
- **nodejs-backend** -- narrow security section to Node.js-specific tooling, reference security-sentinel for broader audits

## [1.3.0] - 2026-02-20

### Added

- **testing-laravel** -- PHPUnit-based Laravel testing: feature tests, factories, mocking, time travel
- **testing-react** -- Vitest and React Testing Library: component tests, hook tests, snapshot tests

### Changed

- **testing-laravel** -- add time travel and `Http::preventStrayRequests()`
- **testing-laravel**, **testing-react** -- add "tests expose bugs" rule
- Multiple coding skills -- add Discipline section with workflow rules

## [1.2.0] - 2026-02-17

### Changed

- **meta-prompting** -- add `/flip`, `/assumptions`, `/tensions` reasoning patterns

## [1.1.0] - 2026-02-16

### Added

- **reflect** -- session retrospective and skill audit

### Changed

- **writing** -- improve human emulation patterns

## [1.0.0] - 2026-02-16

### Added

Initial release with 16 skills:

- **code-review** -- two-stage code reviews with severity-ranked findings
- **debugging** -- systematic root-cause debugging
- **linux-bash-scripting** -- defensive Bash scripting for Linux
- **md-docs** -- manage AGENTS.md, README.md, CONTRIBUTING.md
- **meta-prompting** -- enhanced reasoning patterns via slash commands
- **nodejs-backend** -- Node.js backend patterns: Express/Fastify, TypeScript
- **php-laravel** -- modern PHP and Laravel patterns
- **pinescript** -- Pine Script v6 for TradingView
- **planning** -- file-based implementation planning
- **postgresql** -- PostgreSQL schema design, query optimization
- **python-services** -- Python CLI tools, async parallelism, FastAPI
- **react-frontend** -- React, TypeScript, and Next.js patterns
- **refine-prompt** -- transform vague prompts into precise instructions
- **simplifying-code** -- simplify and declutter code
- **terraform** -- Terraform/OpenTofu configuration and modules
- **writing** -- prose editing, rewriting, and humanizing text
