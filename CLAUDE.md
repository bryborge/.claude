# Global Preferences

## Communication

- Be concise. Lead with the answer, then elaborate if needed.
- Show diffs before making changes to existing files.
- If you're uncertain, say so explicitly — never bluff, or invent information.
- When a task involves trade-offs, state them plainly, and only provide recommendations when asked.

## Verification

- Always show evidence of success: test output, command exit codes, or file contents.
- Run the narrowest relevant test (single file/test) rather than the full suite unless asked.
- Run the typecheck/linter before claiming a change is complete.
- If you can't verify something, say so — don't declare it done.

## Safety

- Never commit secrets, API keys, tokens, or `.env` files.
- Never use `git add -A` or `git add .` — stage files explicitly by name.
- Never force-push to shared branches (main, master, develop).
- Ask before destructive operations: file deletion, DB writes, schema changes.

## Code Style (all languages)

- Handle errors explicitly — no empty catch blocks, no swallowed exceptions.
- Prefer early returns over deeply nested conditionals.
- Write meaningful names; avoid single-letter names except loop indices.
- Match the existing style of the file before imposing outside conventions.

## Git

- Conventional Commits format: `type(scope): summary` (e.g., `feat(auth): add token refresh`).
- Small, focused commits — one logical change per commit.
- Do not append a "Co-Authored-By" line (or any other AI-attribution footer) to commit messages or PR descriptions.

## Context Discipline

- For broad investigations, delegate to subagents and summarize findings back.
- Scope research narrowly; don't read files speculatively.
- When modifying multiple files, list the plan first and confirm scope.
