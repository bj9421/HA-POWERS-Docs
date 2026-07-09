# Publishing a Skill for Dual Audience (Human + Agent)

When publishing a skill to a public repo (README.md + SKILL.md), both humans and agents will visit. Structure for each.

## Convention: Three-File Layout

| File | For | Purpose |
|------|-----|---------|
| `README.md` | Humans | Design philosophy, usage, architecture, comparison tables |
| `SKILL.md` | Agents | Complete skill definition — copy into `skills/` to deploy |
| `zh-TW.md` (optional) | Humans | Localized documentation |

## Installation Section: Always Include Agent Link

In the `## Installation` section, add this block for agents:

```markdown
> 🤖 **For Agents:** [Download SKILL.md](SKILL.md) — copy this file into your `skills/software-development/<name>/` directory to deploy the complete skill definition.
```

And always clarify it's NOT built-in:

```markdown
> ⚠️ **Not built into Hermes Agent.** This is a community-contributed skill authored by the Hermes user. It is not part of the Hermes Agent core distribution.
```

## Design Philosophy Section

Every published skill should have `## 🧠 Design Philosophy` explaining:

1. **Problems being solved** (failure modes without the skill)
2. **Why N phases/steps** (each maps to a specific failure)
3. **What's added on top of upstream** (e.g., Superpowers)
4. **The guiding principle** (one-liner mantra)

## Commit & Push

```bash
git add -A
git commit -m "docs: <summary>"
git push
```

Commit message format: `docs: add <thing> — <brief why>`
