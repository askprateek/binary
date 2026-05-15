Mark the current task or phase as complete.

Do the following:

1. Read `progress.md` to identify current phase and active task
2. Read the active phase file in `todo/` to find the task

**If marking a task done:**
- Verify the task work is committed (check git status)
- If uncommitted work exists: commit it first with format `[PHASE-N] <verb> <what>`
- Check off the task in the phase file: `- [ ]` → `- [x]`
- Commit the updated phase file
- Update `progress.md` — set Resume Here to the next task
- Report: "Task done. Next: [next task name]"

**If all tasks in phase are done:**
- Mark phase complete in `todo/index.md`
- Update `progress.md` — set phase status to `done`, Resume Here to next phase
- Commit both files
- Report: "Phase N complete. Merge branch and start Phase N+1."

**Rules:**
- Never mark done without a commit — done means committed
- If tests are part of the phase, `/test` must pass before marking done
- Confirm with user before merging feature branch to `main`
