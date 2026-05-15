Resume from current state. Context-aware — works regardless of where you are.

Do the following:

1. Read `progress.md` to understand current phase and last position
2. Read the active phase file in `todo/` to find current task status
3. Determine state:
   - **Mid-task**: task started but not committed → continue it
   - **Task done, next pending**: advance to next task in phase file → start it
   - **All tasks done in phase**: mark phase complete, propose next phase
   - **No phase active**: check if requirements exist → if not, start Phase 01

4. Announce what state you found and what you are doing next
5. Execute the next action (do not just describe it)
6. Update `progress.md` after completing meaningful work

**Rules:**
- Never ask "should I continue?" — just continue
- If blocked, surface the blocker explicitly with options
- One task at a time — complete and commit before moving on
