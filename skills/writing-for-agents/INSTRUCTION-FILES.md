# Instruction Files

The `AGENTS.md` and `CLAUDE.md` branch of [`writing-for-agents`](SKILL.md). Sources: the [AGENTS.md standard](https://agents.md/), the [Claude Code memory docs](https://code.claude.com/docs/en/memory), and Anthropic's [CLAUDE.md article](https://claude.com/resources/articles/using-claude-md-files), checked 2026-10-23. Loading behavior varies by Claude Code version; recheck it when a detail matters.

## What Belongs

Both files load into every session, so they hold only what every session needs and the agent cannot discover by looking:

- Exact build, test, and run commands. The agent runs them, so they must work.
- Conventions, architectural decisions, and project-specific gotchas.
- Workflow rules, such as the commit format and testing requirements.

Add a line in response to real friction: the same mistake made twice, the same correction typed again, or something a code review caught. A multi-step procedure, or a rule that matters only for part of the codebase, belongs in a skill or a path-scoped rule instead. Keep secrets out entirely, and write the file as if it will be made public.

Write instructions concrete enough to verify: "Run `npm test` before committing," not "Test your changes." When two instructions contradict each other, the agent may follow either one, so resolve every conflict in the text.

## Size and Disclosure

- Claude Code recommends keeping each `CLAUDE.md` under 200 lines, and warns at startup when a file runs longer.
- An `@path` import keeps the file organized, but it does **not** save context: the imported file loads along with the file that imports it. To actually disclose material, use one of these:
  - A plain pointer: the path in backticks plus the condition for reading it. Backticks also stop `@` from being parsed as an import.
  - A path-scoped rule: a file in `.claude/rules/` with `paths:` frontmatter, which loads only when the agent touches matching files.
  - A skill.
- Block-level HTML comments are stripped before the file reaches the agent, so maintainer notes in them cost no context.

## AGENTS.md

- Plain Markdown with no required fields. It is a README for agents: it complements the human README rather than repeating it.
- Suggested sections: project overview, build and test commands, code style, testing, and security.
- The `AGENTS.md` nearest the edited file wins, and the user's chat prompts override every file. In a monorepo, nest one file per subproject.

## CLAUDE.md

- Scopes, in load order: managed policy, user (`~/.claude/CLAUDE.md`), project (`./CLAUDE.md` or `./.claude/CLAUDE.md`), and local (`./CLAUDE.local.md`, kept out of git).
- Files concatenate rather than override. They are read from the filesystem root down to the working directory, and a subdirectory's file loads once the agent touches a file there. Unlike `AGENTS.md`, the nearer file does not win; it is only read later.
- `/init` produces a draft. Strip its generic guidance and add what the agent cannot discover on its own.
- Import paths resolve relative to the importing file, up to four hops deep.

## Using Both

Claude Code reads `AGENTS.md` directly, but only when no `CLAUDE.md`, `.claude/CLAUDE.md`, or `CLAUDE.local.md` exists in the working directory or above it; the user-level `~/.claude/CLAUDE.md` does not count. To keep `AGENTS.md` as the single source of truth while still adding instructions specific to Claude, start `CLAUDE.md` with an `@AGENTS.md` import and put the Claude-only instructions below it. A symlink (`ln -s AGENTS.md CLAUDE.md`) also works, but it breaks in Windows clones. A `CLAUDE.md` that only tells the agent in words to read `AGENTS.md` is a weak pointer, because the agent opens the file only if it chooses to; use the import instead.
