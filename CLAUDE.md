# CLAUDE.md

Every skill must have a reference in the top-level README.md, and each skill entry in the top-level README.md must link the skill name to its SKILL.md.

No em-dashes anywhere in this repo's prose (SKILL.md files, docs, README.md, CHANGELOG.md, ADRs, changesets, code comments). Where a sentence reaches for one, rewrite it instead with a comma, colon, period, parentheses, or a conjunction, whichever the sentence actually wants; never do a blind character substitution.

## Commits

Never add a "Co-Authored-By" trailer.

**One logical change per commit.**

- Never bundle a feature with a bugfix you hit along the way, a refactor with a behavior change, or a rename with an edit. Separate commits.
- Every commit must build and pass tests on its own. If a refactor needs an intermediate state to stay green, write the intermediate state.
- Order so each commit stands alone: preparatory refactors and incidental fixes before the change that needs them.

**Wait for the ask.** Commit only once I've asked. When I do, propose the sequence of subjects and wait for my go-ahead before writing any of them.

**Format.** Subject: imperative mood, no type prefix. Body: what was wrong and why this change, not a restatement of the diff. No "Co-Authored-By" trailer, in the title or body, in any commit.

## Write the smallest amount of code that does the job

An argument that restates a signature default, a wrapper with one caller, a config key set to the value it already had: each is a **no-op**, and a no-op is a smell. The test is one question, asked of every line you write and every line you read on the way past:

**Does this change behavior versus doing nothing?**

If the answer is no, remove it. Say what you removed and why it was inert. Removing the last line of a file removes the file.

Two bounds on the rule:

- Report no-ops you spot in code the current task does not touch, and remove them in their own commit, separate from the change you were asked for.
- An explicit default earns its place when a comment states what breaks without it (pinning against an upstream change, say). No comment, no exemption.
