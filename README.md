# HA-POWERS — Full-Stack Development Pipeline

> **HA-POWERS** is inspired by [obra's Superpowers](https://github.com/obra/superpowers).
>
> 🇹🇼 [繁體中文說明](zh-TW.md)
>
> **HA-POWERS = Hermes Agent Superpowers.**
> A complete development pipeline from raw idea to merged PR, designed for Hermes Agent but applicable to any AI-assisted workflow.

---

## 🚀 Quick Start

In any Hermes session, type:

```
@skill:ha-powers
```

This loads the full 7-phase pipeline with a visible Progress Tracker and guided walkthrough.

> **Auto-detect mode:** When the skill is loaded, saying "build X" or "implement a feature" makes Hermes automatically decide whether to run the full pipeline or skip to a quick fix.

## 📦 Installation

HA-POWERS is distributed as a **Hermes Agent skill**. No separate install needed — just place the skill in your `skills/` directory and load it.

> 🤖 **For Agents:** [Download SKILL.md](SKILL.md) + [references/](references/) — copy the **entire directory** (`SKILL.md` + `references/`) into your `skills/software-development/ha-powers/` directory to deploy the complete skill definition.

### Prerequisites
- Hermes Agent installed and running
- Connected to a provider (Anthropic, OpenRouter, etc.)

### Optional: Kanban Board
For persistent multi-feature tracking, also load the kanban skill:
```
@skill:kanban
```

## 📋 Pipeline Overview

HA-POWERS guides you through **7 gated phases**:

| Phase | What Happens |
|-------|-------------|
| 1. Brainstorming | Write a spec, get user approval |
| 2. Writing Plans | Decompose into 2–5 min tasks with exact file paths |
| 3. Git Worktrees | Isolated workspace on `feat/<name>` |
| 4. Subagent Dev | Developer + optional Reviewer subagents (TDD) |
| 5. Code Review | Correctness, maintainability, security, performance |
| 6. PR + CI | Push, create PR, auto-fix CI, merge |
| 7. Cleanup | Remove worktree, clean branches |

**See [ARCHITECTURE.md](ARCHITECTURE.md) for the full design philosophy, progress tracker, and diagrams.**

## 🔧 When to Use

### YES — use full pipeline when:
- User says "build a [feature/component/app]"
- Multi-step coding task with >2 files
- Task involves architecture decisions
- Task has test implications
- Any project where you want a PR trail

### NO — skip pipeline (handle directly) when:
- Fixing a single-line typo
- Changing a config value
- Running a script
- Trivial rename / formatting
- User explicitly says "just do it, no need for planning"

## 📁 Project Structure

```
project-root/
├── docs/
│   ├── specs/          # Phase 1 output
│   └── plans/          # Phase 2 output
├── .worktrees/
│   └── feat/           # Phase 3 output
├── KANBAN.json         # Optional kanban board
└── src/                # Implementation
```

## ⚡ Key Takeaways

1. **Every phase has a gate** — must pass before moving to next
2. **Progress Tracker is always visible** — you always know where you are
3. **Kanban persists** — cross-session tracking for all features
4. **Git-friendly** — all outputs are files, version controlled
5. **Zero dependencies** — pure Python stdlib, no server or database
6. **Flexible** — skip phases for small features

---

> 💡 Named in homage to [Superpowers](https://github.com/obra/superpowers) by obra — the progressive disclosure pattern that started it all.  
> *Built for Hermes Agent · MIT License · 2026*
