# AI Skills

Read-only mirror of skills from the [compound-engineering plugin](https://github.com/iliaal/compound-engineering-plugin). 31 skills across architecture, development, infrastructure, testing, workflow, and writing.

**Do not edit skills here.** All changes happen in the upstream plugin repo and are mirrored via `mirror-to-ai-skills.sh`.

## Repository Structure

```
ai-skills/
├── skills/
│   └── <skill-name>/
│       ├── SKILL.md           # Skill content (loaded on trigger)
│       └── references/        # Optional supplementary files
├── CHANGELOG.md
└── README.md
```

## Versioning

Uses [Semantic Versioning](https://semver.org/spec/v2.0.0.html):

- **Major** (1.0.0 → 2.0.0) — breaking changes, major reorganization
- **Minor** (1.0.0 → 1.1.0) — new skills added
- **Patch** (1.0.0 → 1.0.1) — tweaks, fixes, and improvements to existing skills

Current version: **2.0.0**
