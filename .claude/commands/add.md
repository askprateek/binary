Add a new app to this project. Runs a structured conversation, then outputs exact terminal commands for the developer to run.

Do the following in order:

1. **Discover existing apps** — list contents of `code/` to show what's already there
2. **Ask what to add** — what kind of app? (backend API, frontend web app, worker, CLI, mobile, etc.)
3. **Ask stack** — what language/framework? Suggest options based on app type if unsure
4. **Ask hosting target** — where will it run? (Cloudflare Workers, Vercel, AWS, Docker, bare server, etc.)
5. **Ask integrations** — database? auth? external APIs? queue?
6. **Confirm** — summarize choices, ask user to confirm before generating commands

Then:
7. **Search for current setup commands** — use web search to get up-to-date scaffold commands for the chosen stack
8. **Output exact terminal commands** — numbered, copy-pasteable, in order
9. **Create folder** — create `code/<app-name>/` with a `README.md` describing the app and its stack
10. **Update `progress.md`** — note new app added

**Rules:**
- Ask one question at a time
- Never assume the stack — always confirm
- Commands must be exact and runnable — no placeholders like `<your-value>`
- Tell the developer to run commands in their terminal (Claude cannot run installs)
