Run the full test suite across all apps. Regression — every test, every time.

Do the following:

1. **Discover apps** — list all subdirectories in `code/`
2. **Detect test runner per app** — look for `package.json`, `pyproject.toml`, `Cargo.toml`, `go.mod`, etc. to determine test command
3. **Read `tests/registry.md`** — check what should be covered; note any gaps
4. **Output test commands** — for each app, provide the exact command to run tests

Then ask the developer to run each command and paste results back, or:
- If running in an environment where commands can execute, run them directly

5. **After results received:**
   - Report pass/fail per app
   - Flag any regressions (tests that passed before, now fail)
   - Update `tests/registry.md` if new tests were discovered
   - Save e2e/integration reports to `tests/reports/YYYY-MM-DD-<phase>.md`

**Rules:**
- Never skip an app — run all or explain why one was skipped
- Regressions are blockers — do not mark phase done if tests regress
- Unit test output: report summary only. E2e output: save full report to `tests/reports/`
