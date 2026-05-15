# Test Registry

Master list of all test cases across all apps. Updated by Claude after each phase that adds tests.

## Coverage Map

<!-- Claude fills this in as tests are written -->
<!-- Format: app | area | test file | what it covers -->

| App | Area | Test File | Covers |
|-----|------|-----------|--------|

## Intended Coverage

<!-- Claude derives this from docs/01-requirements.md during Phase 03 -->
<!-- Dev can add or remove items -->

<!-- Example:
- [ ] Auth: login flow (happy path + wrong password)
- [ ] Auth: session expiry
- [ ] API: create resource (valid + invalid input)
-->

## Reports

E2e and integration test reports are saved to `tests/reports/` after each `/test` run.
Unit test output stays in each app's own test runner.
