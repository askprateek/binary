# Phase 01 — Requirement Dump

**Goal:** Capture raw requirements through structured conversation. Output is `todo/requirement-dump.md` — raw, distilled, unstructured.

**Branch:** `feature/phase-01-requirement-dump`

---

## Conversation Protocol

Claude asks one question at a time. Never dumps a form. Follows this sequence:

1. **Problem Space** (Lean Canvas + JTBD)
   - What problem does this solve? For whom? Why now?
   - What is the user trying to accomplish — the core job?

2. **Workflows** (Event Storming lite)
   - Walk me through how a user uses this on day 1, step by step.
   - What happens if X fails? (probe every key action)

3. **Scope** (MoSCoW)
   - What must exist for this to be useful at all?
   - What is explicitly out of scope right now?

4. **Gap Fill** (structured checklist — Claude probes these if not mentioned)
   - Performance targets
   - Security / auth needs
   - Integrations / external services
   - Compliance / data residency
   - Scale assumptions

---

## Distillation Rules

- **Distill, not transcribe.** Strip filler words, repetition, tangents. Preserve intent exactly.
- **One idea = one bullet**, however it was said.
- **Never interpret or reframe.** If unclear, ask — don't assume.
- **Flag contradictions inline** with ⚠. Do not resolve them — that is Phase 02's job.
  - Example: `- Auth: email/password ⚠ Changed: user later said OAuth only`
- **User can change mind freely.** Capture the change, flag it, move on.

---

## Tasks

- [ ] Open conversation — ask first question (problem + who)
- [ ] Work through all 4 conversation stages
- [ ] Populate `todo/requirement-dump.md` throughout (append as conversation progresses)
- [ ] Probe all gap-fill items not volunteered by user
- [ ] User confirms "that's everything"
- [ ] Commit `todo/requirement-dump.md`
- [ ] Update `todo/index.md` — mark Phase 01 complete
- [ ] Update `progress.md`
- [ ] Merge to `main`

---

## Definition of Done

- All conversation stages covered
- `todo/requirement-dump.md` populated, committed
- User has confirmed dump is complete
- Branch merged to `main`
