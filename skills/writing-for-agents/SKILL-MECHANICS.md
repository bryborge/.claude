# Skill Mechanics

The skill branch of [`writing-for-agents`](SKILL.md): frontmatter, invocation, and router skills. Platform facts come from the [Claude Code skills docs](https://code.claude.com/docs/en/skills), checked 2026-10-23; recheck them when a detail matters.

## Frontmatter

- `name` defaults to the directory name.
- `description` is the skill's always-loaded context pointer, so the pointer rules in `SKILL.md` apply in full. Put the key use case first: the description plus any `when_to_use` text is truncated at 1,536 characters in the skill listing.
- Unrecognized fields are ignored without an error, so a misspelled field fails silently. Check field names against the docs.
- Add other fields (`allowed-tools`, `argument-hint`, `paths`, `model`, …) only when the skill needs them.

## Invocation

Three settings trade context cost against who can reach the skill:

| Setting | Who invokes | Description in context |
| --- | --- | --- |
| default | user and agent | always |
| `disable-model-invocation: true` | user only | never |
| `user-invocable: false` | agent only | always |

- A **model-invoked** skill (the default) can fire on its own, and other skills can reach it. Its description is model-facing and carries the trigger cases. A model-invoked skill that holds only reference is also a home for reference several skills share.
- A **user-invoked** skill costs no context, but you become the index that must remember it exists. Its description becomes a one-line summary for humans, with trigger lists removed.
- An **agent-only** skill suits background reference that a human would never type by name.

Choose model invocation only when the agent, or another skill, must reach the skill unprompted.

Reference that two user-invoked skills both need can live in neither, because neither can fire the other. Put it in a plain file outside the skill system and point to it from both.

Split off a new model-invoked skill only when a distinct leading word you actually use in prompts should trigger it alone, or when another skill must reach it. The new description costs context every turn, so that independent reach has to be worth it.

## Body

- Keep `SKILL.md` under 500 lines. Move detail into sibling files, each reached by a pointer that says what the file holds and when to read it.
- Once invoked, the body stays in context across turns and is not re-read, so write standing instructions rather than one-time steps. After auto-compaction only the first 5,000 tokens of a skill are re-attached, so put what must survive first.

## Router Skills

When user-invoked skills multiply past what you can remember, a **router skill** cures it: one user-invoked skill that names the others and when to reach for each, leaving one name to remember instead of many. It can only point to them; it cannot fire them.
