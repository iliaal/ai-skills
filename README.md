# AI Skills

Compact, opinionated agent skills for AI coding assistants. Distilled and refined to stay small, hit hard, and waste nothing.

> **Note:** This repo is a read-only mirror of skills from the [compound-engineering plugin](https://github.com/iliaal/compound-engineering-plugin). Edits happen upstream; this repo is for distribution via `npx skills add`.

## Install

```bash
npx skills add iliaal/ai-skills

# Pick one skill
npx skills add iliaal/ai-skills -s code-review

# Target a specific agent
npx skills add iliaal/ai-skills -a claude-code
```

Works with Claude Code, OpenCode, OpenClaw and its derivatives, Codex, Cursor, Kilo Code, and [35+ other agents](https://agentskills.io).

## Skills

### Architecture & Design

| Skill | Description |
|-------|------------|
| [agent-native-architecture](skills/agent-native-architecture) | Build AI agents using prompt-native architecture |
| [frontend-design](skills/frontend-design) | Create production-grade frontend interfaces |
| [simplifying-code](skills/simplifying-code) | Declutter code without changing behavior |

### Development

| Skill | Description |
|-------|------------|
| [react-frontend](skills/react-frontend) | React, TypeScript, Next.js patterns, Vitest/RTL testing |
| [nodejs-backend](skills/nodejs-backend) | Express/Fastify layered architecture, validation, error handling, production config |
| [python-services](skills/python-services) | CLI tools, async parallelism, FastAPI, project tooling (uv, ruff, ty) |
| [php-laravel](skills/php-laravel) | PHP 8.4, Laravel, Eloquent, queues, PHPUnit testing |
| [pinescript](skills/pinescript) | Pine Script v6 indicators, strategies, backtesting, TradingView |

### Infrastructure

| Skill | Description |
|-------|------------|
| [postgresql](skills/postgresql) | Schema design, query tuning, indexing, JSONB, partitioning, RLS, window functions |
| [terraform](skills/terraform) | Terraform/OpenTofu modules, testing, state management, multi-environment HCL |
| [linux-bash-scripting](skills/linux-bash-scripting) | Defensive Bash, argument parsing, production patterns, ShellCheck compliance |

### Testing

| Skill | Description |
|-------|------------|
| [writing-tests](skills/writing-tests) | Generic test discipline: quality, anti-patterns, rationalization resistance |

### Code Quality & Review

| Skill | Description |
|-------|------------|
| [code-review](skills/code-review) | Two-stage review (spec compliance, then code quality) with severity-ranked findings |
| [receiving-code-review](skills/receiving-code-review) | Process review feedback critically: verify, push back, no blind agreement |
| [debugging](skills/debugging) | Root-cause debugging: reproduce, investigate, hypothesize, fix, verify, postmortem |
| [verification-before-completion](skills/verification-before-completion) | Fresh verification evidence before any completion claim |
| [planning](skills/planning) | File-based implementation planning with task breakdown and progress tracking |

### Content & Workflow

| Skill | Description |
|-------|------------|
| [brainstorming](skills/brainstorming) | Explore requirements and approaches through dialogue |
| [compound-docs](skills/compound-docs) | Capture solved problems as categorized documentation |
| [document-review](skills/document-review) | Improve documents through structured self-review |
| [file-todos](skills/file-todos) | File-based todo tracking system |
| [finishing-branch](skills/finishing-branch) | Workflow closer: merge, PR, keep, or discard with safety checks |
| [git-worktree](skills/git-worktree) | Manage Git worktrees for parallel development |
| [md-docs](skills/md-docs) | Manage AGENTS.md, README.md, and CONTRIBUTING.md |
| [resolve-pr-parallel](skills/resolve-pr-parallel) | Resolve PR review comments in parallel |
| [setup](skills/setup) | Configure which review agents run for your project |
| [writing](skills/writing) | Prose editing, rewriting, and humanizing text |

### AI & Prompting

| Skill | Description |
|-------|------------|
| [meta-prompting](skills/meta-prompting) | Structured reasoning via /think, /verify, /adversarial, /edge, /compare |
| [refine-prompt](skills/refine-prompt) | Turn rough prompts into precise AI instructions |
| [reflect](skills/reflect) | Session retrospective and skill audit |

### Multi-Agent Orchestration

| Skill | Description |
|-------|------------|
| [orchestrating-swarms](skills/orchestrating-swarms) | Comprehensive guide to multi-agent swarm orchestration |

## Design

Skills eat context. Every token a skill spends is one the agent can't use on your code. So these are built tight.

Each skill goes through a distillation process: multiple expert sources are analyzed, overlapping advice is merged, filler is stripped, and contradictions are resolved. What's left is one focused instruction set per topic. The approach follows Anthropic's prompting principles and patterns refined by experienced skill authors.

What that looks like in practice:

- **Under 1K tokens, 2K hard cap.** If it doesn't fit, it gets split into a reference file the agent loads on demand.
- **Front-loaded.** The most important rules come first. Model attention drops off, so the critical stuff leads.
- **Actions, not explanations.** Tell the agent what to do, not what things are. Skip anything the model already knows.
- **Every "don't" has a "do instead."** Bare prohibitions leave the agent guessing. Alternatives give it a clear path.
- **One good default per decision.** A single best practice beats a menu of options.
- **Keyword-rich descriptions under 80 tokens.** The description is the only part loaded at startup across all installed skills. It's what the agent uses to decide whether to activate a skill, so it's packed with the exact phrases developers type. The skill body only loads when triggered.

## Tips

Claude Code sometimes skips skills even when they match your request. If that happens, add this to your `CLAUDE.md` or `MEMORY.md`:

```markdown
## Always check skills before starting work
Before starting any task, scan the full available skills list in the system prompt
and check if any skill's trigger matches the user's request. If a match exists,
invoke it via the Skill tool BEFORE generating any manual response. Do not skip
skills in favor of doing the work manually.
```

This turns skill activation from "when it feels like it" into a reliable first step.

## Version History

See [CHANGELOG.md](CHANGELOG.md) for detailed version history.

## License

MIT
