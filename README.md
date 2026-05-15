# Binary

A Claude Code starter template for building any application — structured, phase-driven, stack-agnostic.

## What is this?

Binary is a GitHub template repo that gives developers a structured workflow for building apps with Claude Code. It handles the process — requirements, architecture, phases, testing — so you focus on building.

**Who it's for:** Developers who know their stack but want an opinionated Claude Code workflow.

## How to use

1. Click **Use this template** on GitHub
2. Open your new repo in Claude Code
3. Run `/check` — Claude reads your project state and tells you the next step
4. Follow the guided flow from requirements to deployment

## Commands

| Command | What it does |
|---------|-------------|
| `/check` | Snapshot — current phase, what's done, what's next |
| `/next` | Resume — continues current task or advances to the next one |
| `/add` | Add a new app to `code/` — Claude asks questions, gives you setup commands |
| `/test` | Run full regression suite across all apps |
| `/done` | Mark current task or phase complete |

## Workflow

```
Requirements → Architecture → Phases → Build → Test → Deploy
```

1. `/check` shows empty requirements → Claude grills you until docs are filled
2. Docs complete → Claude auto-generates phases in `todo/`
3. `/next` from any state — mid-task, new task, or new phase — always resumes correctly
4. Each phase includes tests; `/test` runs everything, every time
5. `progress.md` is Claude's memory — updated after every task, never stale

## Structure

```
docs/           — requirements, architecture, decisions (filled before any code)
code/           — one subfolder per app (api/, web/, worker/, ...)
todo/           — phase files, auto-generated after design docs complete
tests/          — registry.md (master test list) + reports/ (e2e output)
progress.md     — Claude's session memory, auto-updated
AGENTS.md       — workflow rules for Claude (read this)
```

## Rules Claude follows

- Never writes code before requirements and architecture docs are filled
- One branch per phase: `feature/phase-N-<name>`
- One commit per task, immediately after completion
- No new packages without discussion
- Updates `progress.md` after every meaningful action

## Multi-app support

`/add` can be run multiple times. Each app gets its own folder inside `code/`. Tests live co-located with each app. `tests/registry.md` tracks what's covered across the whole project.

---

Open source. Built by [Epyc](https://epyc.in).
