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

> **Each phase is an independent tool. Pick what you need, skip what you don't.**

**FULL pipeline (Phase 0–7) — for large, high-risk work:**
- User says "build a [feature/component/app]"
- Multi-step coding task with >2 files
- Task involves architecture decisions that are hard to undo
- Task has test implications
- Any project where you want a PR trail

**PARTIAL pipeline (Phase 0–2, then code directly):**
- Single-file change with some design choices
- Modifying an existing script (add flag, refactor function)
- Task you'll review yourself (no team PR needed)
- Prototype / spike that might be thrown away

**MINIMAL pipeline (Phase 0 only, then code directly):**
- Clear scope but need to align on 2-3 details (API choice, output format)
- User has a preference but needs help deciding between options
- Quick grill-me session (3-5 questions) then straight to coding

**SKIP pipeline entirely (fix directly):**
- Fixing a single-line typo
- Changing a config value
- Running a script
- Trivial rename / formatting
- User explicitly says "just do it, no need for planning"

### 🔀 Review vs Debug 分工

> **Review（事前預防）與 Debug（事後治療）是時間線上的不同點，不是並行選項。**

| Skill | 觸發時機 | 目的 | 輸出 |
|-------|---------|------|------|
| `requesting-code-review` / `deep-code-review` | 功能寫完、發 PR 前 | **預防** | bug 報告 + 嚴重度分級 |
| `systematic-debugging` / `hermes-debug-protocol` | bug 已發生、有異常行為 | **治療** | 根因 + 修復證據 |

**關鍵原則：**
1. **Review = 還沒壞，檢查會不會壞**（輸出 bug 報告與建議）
2. **Debug = 已經壞了，查為什麼**（輸出根因 + Before/After 證據）
3. **上下游關係**：review 發現問題 → 修復 → 若修了還壞 → 才進入 debug 8 步流程。不是並行、不是替代。
4. **debug skills 三選一，不疊加**：`hermes-debug-protocol`（整合版）或 `systematic-debugging` + `debug-agent`（拆件）。

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
6. **Toolbox, not assembly line** — pick the right depth for the risk

---

> 💡 Named in homage to [Superpowers](https://github.com/obra/superpowers) by obra — the progressive disclosure pattern that started it all.  
> *Built for Hermes Agent · MIT License · 2026*
