# AI Skills

Compact, opinionated agent skills for AI coding assistants. 19 skills across development, infrastructure, testing, workflow, and writing.

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

- **Major** (1.0.0 → 2.0.0) — multiple new skills or major revisions across the collection
- **Minor** (1.0.0 → 1.1.0) — new skill added
- **Patch** (1.0.0 → 1.0.1) — tweaks, fixes, and improvements to existing skills

Current version: **1.4.1**

## Updating Skills

When modifying skills:

1. Make changes to the relevant `SKILL.md` or reference files
2. Update `CHANGELOG.md` with the changes under a new version heading
3. Bump version in `CHANGELOG.md` following the rules above
4. Update `README.md` if skill descriptions or tables change

## Skill Design Rules

- Under 1K tokens, 2K hard cap per SKILL.md
- Front-load the most important rules
- Actions, not explanations — tell the agent what to do
- Every "don't" has a "do instead"
- One good default per decision
- Keyword-rich descriptions under 80 tokens
