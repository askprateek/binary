Convert an existing repository into Binary workflow structure. Fetches latest files from the Binary template repo. Safe — never overwrites user content except AGENTS.md, CLAUDE.md, and commands.

---

## Step 0: Self-update check

Before doing anything, fetch the latest version of this command:
```
https://raw.githubusercontent.com/askprateek/binary/main/.claude/commands/convert.md
```
Compare with current content. If different, tell the user: "A newer version of /convert is available. Update ~/.claude/commands/convert.md from the URL above before continuing." Then stop — let user update and re-run.

---

## Step 1: Announce and confirm

Tell the user:
- This will add Binary workflow files to the current repo
- It will NOT overwrite existing docs, todos, or progress files
- It WILL overwrite AGENTS.md, CLAUDE.md, and .claude/commands/
- Ask: "Proceed?"

Wait for confirmation before continuing.

---

## Step 2: Drop workflow files

Fetch and write each file using curl from `https://raw.githubusercontent.com/askprateek/binary/main/`:

**Always overwrite:**
- `AGENTS.md`
- `CLAUDE.md`
- `.claude/commands/check.md`
- `.claude/commands/next.md`
- `.claude/commands/add.md`
- `.claude/commands/test.md`
- `.claude/commands/done.md`

**Only create if file/folder does not exist:**
- `docs/01-requirements.md`
- `docs/02-architecture.md`
- `docs/03-data-model.md`
- `docs/04-api-design.md`
- `docs/05-security.md`
- `docs/06-flows.md`
- `docs/07-infrastructure.md`
- `docs/08-decisions.md`
- `todo/index.md`
- `todo/01-phase-requirement-dump.md`
- `todo/02-phase-requirement-synthesis.md`
- `todo/03-phase-design-docs.md`
- `tests/registry.md`
- `progress.md`

**Merge, never overwrite:**
- `.claudeignore` — append Binary entries, skip any already present
- `.gitignore` — append `todo/requirement-dump.md` if not already present

Run these curl commands:
```bash
curl -fsSL https://raw.githubusercontent.com/askprateek/binary/main/AGENTS.md -o AGENTS.md
curl -fsSL https://raw.githubusercontent.com/askprateek/binary/main/CLAUDE.md -o CLAUDE.md
mkdir -p .claude/commands
curl -fsSL https://raw.githubusercontent.com/askprateek/binary/main/.claude/commands/check.md -o .claude/commands/check.md
curl -fsSL https://raw.githubusercontent.com/askprateek/binary/main/.claude/commands/next.md -o .claude/commands/next.md
curl -fsSL https://raw.githubusercontent.com/askprateek/binary/main/.claude/commands/add.md -o .claude/commands/add.md
curl -fsSL https://raw.githubusercontent.com/askprateek/binary/main/.claude/commands/test.md -o .claude/commands/test.md
curl -fsSL https://raw.githubusercontent.com/askprateek/binary/main/.claude/commands/done.md -o .claude/commands/done.md
mkdir -p docs todo tests/reports code
```
Ask the developer to run these commands in their terminal.

For "only if not exists" files — check existence first, fetch only missing ones. Provide a single curl block for all missing files.

---

## Step 2.5: Reload plugins

After user confirms the curl commands ran successfully, tell the user to run `/reload-plugins` in the current Claude Code session to activate the newly installed commands without restarting.

Instruct: "Run `/reload-plugins` now — this loads the new commands into this session."

Wait for user to confirm reload done before continuing.

---

## Step 2.6: Load CLAUDE.md instructions

Read `CLAUDE.md` in the current repo using the Read tool. Parse any `@filename` references (lines starting with `@`). For each referenced file, read it too using the Read tool.

This loads all project instructions into the current session so they take effect immediately.

Confirm to the user: "Instructions from CLAUDE.md (and referenced files) loaded into this session."

---

## Step 3: Code restructure check

Scan the repo root for common code folders: `src/`, `app/`, `lib/`, `server/`, `client/`, `backend/`, `frontend/`.

If found, check these files for hardcoded path references:
- `Dockerfile` — look for `COPY src/`, `WORKDIR` with path
- `.github/workflows/*.yml` — look for `working-directory:`, path filters
- `package.json` — look for `"main"`, `"scripts"` containing folder names
- `tsconfig.json` / `jsconfig.json` — look for `"rootDir"`, `"include"`
- `vite.config.*` / `webpack.config.*` / `next.config.*` — entry points
- `Makefile` — any path references

**If path-sensitive config found:**
Tell the user exactly which files block the move. Skip restructure. Example:
> "Found `src/` but `package.json` references it in scripts. Safe to skip — restructure manually if needed."

**If no path-sensitive config found:**
Offer: "Found `src/` at root. Safe to move to `code/<app-name>/`. What should the app be called?" 
Wait for name. Then provide the git commands:
```bash
git mv src/ code/<app-name>/
```
Ask developer to run. After they confirm done, update `progress.md` to note the app.

---

## Step 4: Wrap up

- Show a summary: files added, files skipped (already existed), restructure status
- Update `progress.md` — note Binary workflow installed, set Resume Here to Phase 01
- Tell user: "Run `/check` to see project state. Run `/next` to begin."
