# Changelog

All notable changes to ai-skills will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

**Versioning rules:**
- **Major** — multiple new skills or major revisions across the collection
- **Minor** — new skill added
- **Patch** — tweaks, fixes, and improvements to existing skills

## [1.4.1] - 2026-02-22

### Changed

- **php-laravel** — change testing framework from Pest to PHPUnit

## [1.4.0] - 2026-02-22

### Changed

- **debugging** — add concurrency section (async race conditions, deadlocks, connection pool exhaustion) and postmortem template
- **php-laravel** — add PHP 8.4 features (property hooks, asymmetric visibility, `new` chaining, `array_find`/`array_any`/`array_all`), PHPStan level 8+, OPcache/JIT/preloading, Laravel ecosystem reference file

## [1.3.1] - 2026-02-21

### Changed

- **debugging** — add explicit root cause analysis section
- **nodejs-backend** — narrow security section to Node.js-specific tooling, reference security-sentinel for broader audits

## [1.3.0] - 2026-02-20

### Added

- **testing-laravel** — PHPUnit-based Laravel testing: feature tests, factories, mocking, time travel
- **testing-react** — Vitest and React Testing Library: component tests, hook tests, snapshot tests

### Changed

- **testing-laravel** — add time travel and `Http::preventStrayRequests()`
- **testing-laravel**, **testing-react** — add "tests expose bugs" rule
- Multiple coding skills — add Discipline section with workflow rules

## [1.2.0] - 2026-02-17

### Changed

- **meta-prompting** — add `/flip`, `/assumptions`, `/tensions` reasoning patterns

## [1.1.0] - 2026-02-16

### Added

- **reflect** — session retrospective and skill audit

### Changed

- **writing** — improve human emulation patterns

## [1.0.0] - 2026-02-16

### Added

Initial release with 16 skills:

- **code-review** — two-stage code reviews with severity-ranked findings
- **debugging** — systematic root-cause debugging
- **linux-bash-scripting** — defensive Bash scripting for Linux
- **md-docs** — manage AGENTS.md, README.md, CONTRIBUTING.md
- **meta-prompting** — enhanced reasoning patterns via slash commands
- **nodejs-backend** — Node.js backend patterns: Express/Fastify, TypeScript
- **php-laravel** — modern PHP and Laravel patterns
- **pinescript** — Pine Script v6 for TradingView
- **planning** — file-based implementation planning
- **postgresql** — PostgreSQL schema design, query optimization
- **python-services** — Python CLI tools, async parallelism, FastAPI
- **react-frontend** — React, TypeScript, and Next.js patterns
- **refine-prompt** — transform vague prompts into precise instructions
- **simplifying-code** — simplify and declutter code
- **terraform** — Terraform/OpenTofu configuration and modules
- **writing** — prose editing, rewriting, and humanizing text
