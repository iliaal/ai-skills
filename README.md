# AI Skills

Compact, opinionated agent skills for AI coding assistants. Distilled and refined to stay small, hit hard, and waste nothing.

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

### Development

| Skill | Description |
|-------|------------|
| [react-frontend](skills/react-frontend) | React 18-19, TypeScript, Next.js App Router, Server Components, type-safe patterns |
| [nodejs-backend](skills/nodejs-backend) | Express/Fastify layered architecture, validation, error handling, production config |
| [python-services](skills/python-services) | CLI tools, async parallelism, FastAPI, project tooling (uv, ruff, ty) |
| [php-laravel](skills/php-laravel) | PHP 8.2+, Laravel, Eloquent, queues, Pest testing |
| [pinescript](skills/pinescript) | Pine Script v6 indicators, strategies, backtesting, TradingView |

### Infrastructure

| Skill | Description |
|-------|------------|
| [postgresql](skills/postgresql) | Schema design, query tuning, indexing, JSONB, partitioning, RLS, window functions |
| [terraform](skills/terraform) | Terraform/OpenTofu modules, testing, state management, multi-environment HCL |
| [linux-bash-scripting](skills/linux-bash-scripting) | Defensive Bash, argument parsing, production patterns, ShellCheck compliance |

### Workflow

| Skill | Description |
|-------|------------|
| [code-review](skills/code-review) | Two-stage review (spec compliance, then code quality) with severity-ranked findings |
| [debugging](skills/debugging) | Root-cause debugging: reproduce, investigate, hypothesize, fix, verify |
| [simplifying-code](skills/simplifying-code) | Declutter code without changing behavior |
| [planning](skills/planning) | File-based implementation planning with task breakdown and progress tracking |

### Writing

| Skill | Description |
|-------|------------|
| [writing](skills/writing) | Prose editing and rewriting with a natural tone |
| [refine-prompt](skills/refine-prompt) | Turn rough prompts into precise AI instructions |
| [meta-prompting](skills/meta-prompting) | Structured reasoning via /think, /verify, /adversarial, /edge, /compare |
| [md-docs](skills/md-docs) | Manage AGENTS.md, README.md, and CONTRIBUTING.md |

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

## License

MIT
