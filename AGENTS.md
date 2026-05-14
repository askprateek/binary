# AGENTS.md

Universal AI agent instructions for this repository. Applies to Claude Code, Cursor, Codex, and any other AI tool.

---

## Bootstrap Protocol

**Read this on every new session, before doing anything.**

1. Read `progress.md` — get current phase and context
2. Check `docs/01-requirements.md` — if empty, do nothing else: start requirements discussion with user
3. Check phase summary in `progress.md` — only do work valid for current phase

**Phase gates:**
- `docs/01-requirements.md` empty → stop. Gather requirements first.
- Requirements done, `docs/02-architecture.md` empty → fill architecture docs before writing any code.
- All docs filled → proceed to build phases per `todo/index.md`.

Never skip a gate. Never write code before requirements and architecture docs are filled.

---

## Repo Structure

```
docs/                        — documentation (clean, approved, structured)
code/                        — source code
todo/                        — phase files + working artifacts
todo/requirement-dump.md     — raw dump (Phase 01 only, added to .claudeignore after Phase 02)
progress.md                  — session context file (read this first when resuming)
AGENTS.md                    — this file
```

**Rule:** Never read `todo/requirement-dump.md` after Phase 02 complete. It will be in `.claudeignore`.

---

## progress.md

**Purpose:** session-resume context. Captures decisions made, architectural context, open questions. New session reads this first, then digs into `todo/` for task specifics.

**Structure:**

```
## Phase Summary
| Phase | Name | Status |
| ...   | ...  | done / in-progress / pending |

## Last Session
- What was done
- Key decisions made and why

## Resume Here
- Exact next task
- Any blockers or open questions
```

**When to update:** after meaningful work chunks. Always update before ending session. Stale `progress.md` = useless resume.

---

## Phase Execution Principles

### 1. Git Workflow

- One branch per phase: `feature/phase-N-<short-name>`
- One task = one commit. Commit immediately after each task. Never batch.
- Commit format: `[PHASE-N] <verb> <what>` — e.g. `[PHASE-2] Add invite creation endpoint`
- Never commit to `main` directly. All work via feature branch → PR.
- Merge to `main` only after phase fully complete and all tasks checked off.

### 2. Task Execution Order

- Follow phase plan top-to-bottom. No skipping, no reordering.
- Mark each task complete in the phase file (`todo/0N-phase-X.md`) immediately after done.
- Do not start next task until current task is committed.
- If blocked, surface it immediately — never work around silently.

### 3. Code Rules

- **No new packages without discussion.** Every new dependency proposed and approved before adding to `package.json`.
- **No secrets in source.** All secrets go in env vars / Wrangler bindings. Never hardcode keys, tokens, or credentials.
- **Zod for all request validation.** Every external input (request body, query params) validated with Zod schema before use.
- **Web Crypto only.** Use `crypto.subtle` for all crypto operations. No Node.js `crypto` module, no third-party crypto libs.
- **File changes via Read/Edit/Write tools only.** Never use bash (`sed`, `awk`, `echo >`, `cat <<EOF`) to modify source files.
- **Ask user to run commands** when sandbox cannot execute them (package installs, test runs, migrations). Provide exact command to copy-paste.

### 4. Definition of Done (per phase)

Phase is done only when ALL true:

- [ ] Every task in `todo/0N-phase-X.md` checked off
- [ ] Every task has its own commit on feature branch
- [ ] `todo/index.md` updated to mark phase complete
- [ ] Feature branch merged to `main`

### 5. Task Execution Protocol

For every task, follow this order strictly:

```
Plan → Confirm → Code → Verify
```

1. **Plan** — List files to change, logic to add, steps in order. No code yet — logic only.
2. **Confirm** — Present plan to user. Do not write any code until user approves.
3. **Code** — Implement exactly what was approved. No scope creep, no bonus improvements.
4. **Verify** — Check implementation matches plan. Run relevant tests or type checks.

If plan changes mid-implementation, stop and re-confirm before continuing.
