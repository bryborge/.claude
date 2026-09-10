# Commit Messages

**One logical change per commit.**

- Never bundle a feature with a bugfix you hit along the way, a refactor with a behavior
  change, or a rename with an edit. Separate commits.
- Every commit must build and pass tests on its own. If a refactor needs an intermediate
  state to stay green, write the intermediate state.
- Order so each commit stands alone: preparatory refactors and incidental fixes before the
  change that needs them.

**Wait for the ask.** Commit only once I've asked. When I do, propose the sequence of
subjects and wait for my go-ahead before writing any of them.

**Format.** Subject: imperative mood, no type prefix. Body: what was wrong and why this
change, not a restatement of the diff. No "Co-Authored-By" trailer, in the title or body,
in any commit.
