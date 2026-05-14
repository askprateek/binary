# Phase 03 — Design & Documentation

**Goal:** Fill all remaining docs using requirements as input. One continuous design conversation. Output is complete, approved docs ready for development.

**Branch:** `feature/phase-03-design-docs`

**Prerequisite:** `docs/01-requirements.md` approved and merged (Phase 02 done).

---

## Protocol

Claude drives a design conversation using `docs/01-requirements.md` as sole input. Tasks run in order — each doc depends on the previous. One doc at a time, user reviews and approves before moving to next.

---

## Tasks

**Architecture**
- [ ] Draft `docs/02-architecture.md` — components, responsibilities, high-level diagram
- [ ] User approves architecture
- [ ] Commit `docs/02-architecture.md`

**Data Model**
- [ ] Draft `docs/03-data-model.md` — schema derived from requirements + architecture
- [ ] User approves data model
- [ ] Commit `docs/03-data-model.md`

**API Design**
- [ ] Draft `docs/04-api-design.md` — endpoints derived from data model + requirements
- [ ] User approves API design
- [ ] Commit `docs/04-api-design.md`

**Flows**
- [ ] Draft `docs/06-flows.md` — state machines + key request flows from API design
- [ ] User approves flows
- [ ] Commit `docs/06-flows.md`

**Security**
- [ ] Draft `docs/05-security.md` — auth, encryption, rate limiting derived from requirements + flows
- [ ] User approves security design
- [ ] Commit `docs/05-security.md`

**Infrastructure**
- [ ] Draft `docs/07-infrastructure.md` — project structure, deployment, config
- [ ] User approves infrastructure
- [ ] Commit `docs/07-infrastructure.md`

**Decisions**
- [ ] Write `docs/08-decisions.md` — trade-offs made during this phase, build order, future considerations
- [ ] Commit `docs/08-decisions.md`

**Wrap up**
- [ ] Update `todo/index.md` — mark Phase 03 complete
- [ ] Update `progress.md` — summarize design decisions, set resume point to Phase 04
- [ ] Merge to `main`

---

## Definition of Done

- All 7 docs filled, no placeholders remaining
- Each doc explicitly approved by user before commit
- `docs/08-decisions.md` captures key trade-offs made
- Branch merged to `main`
