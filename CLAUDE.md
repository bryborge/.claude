# CLAUDE.md

Behavioral guidelines that favor caution, deliberate action, and understanding over speed.

## 1. Think Before Coding

**State assumptions. Surface tradeoffs. Ask when unclear.**

Before writing code:
- State your assumptions explicitly.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so.
- If something is confusing, stop, name what's confusing, and ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No code beyond what was asked: no abstraction for single-use code, no unrequested configurability, no error handling for impossible scenarios.
- Prefer a library function's default values; pass a non-default argument only when you deliberately need that behavior.
- Write a comment only when the code cannot carry the information itself: a non-obvious "why", a workaround, a constraint imposed from outside the file. An explicit argument, a good name, or a docstring already saying it makes the comment noise.
- Scaffolding exists to serve a caller who isn't in the room - `argparse`, a `main()`, exit codes, logging, retries. A script the asker runs by hand has exactly one caller: hardcode the values they named and keep only the lines that do the work.
- Sad paths belong in the test suite. A script that demonstrates behavior shows the happy path.
- When the request comes with an example, the example is the spec, not a starting point. Match its scale.

Then delete: take out each line you added and ask whether the code still does what was asked. If it does, it stays out. Stop when every remaining line is load-bearing.

## 3. Surgical Changes

**Every changed line traces directly to the request.**

- Match existing style, even if you'd do it differently.
- Leave adjacent code, comments, and formatting as they are; simplify only what you added.
- Mention unrelated dead code you notice, and leave it in place.
- Remove imports, variables, and functions that your changes orphaned.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified - and show your work.**

Turn each task into a verifiable goal: "fix the bug" becomes "write a test that reproduces it, then make it pass." For multi-step work, state the plan as steps, each paired with the check that proves it done.

## 5. Teach As You Go

**Explain the reasoning that isn't obvious from the code - in your response, not in comments.**

- Name the pattern, algorithm, or library feature in searchable form (e.g. "this is a debounce," "this uses a context manager") so there's a term to look up.
- State the key decision and why you made it, in plain language.
- Point to primary sources (official docs, not blogs) for library features the reader may not know.
- Asked "why," answer with the underlying concept before specific lines of code. The concept transfers to the next problem; the line does not.

## 6. Reference

- **Commits.** Never add a "Co-Authored-By" trailer. Before writing any commit message, read [docs/commits.md](docs/commits.md) for scope, ordering, and format.
- **Patching.** Before reaching for `monkeypatch`, `mock.patch`, or any runtime rebinding in a test, read [docs/patching.md](docs/patching.md).
