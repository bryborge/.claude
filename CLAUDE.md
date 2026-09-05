# CLAUDE.md

Behavioral guidelines that favor caution, deliberate action, and understanding over speed.

## 1. Think Before Coding

**Don't assume. Don't hide confusion. Surface tradeoffs.**

Before writing code:
- State your assumptions explicitly. If uncertain, ask.
- If multiple interpretations exist, present them - don't pick silently.
- If a simpler approach exists, say so.
- If something is unclear, stop. Name what's confusing. Ask.

## 2. Simplicity First

**Minimum code that solves the problem. Nothing speculative.**

- No code beyond what was asked.
- No abstractions for single-use code.
- No "flexibility" or "configurability" that wasn't requested.
- No error handling for impossible scenarios.
- Prefer a library function's default values; pass a non-default argument only when you deliberately need that behavior.
- No comments that restate what the code already says. Write one only when the code cannot carry the information itself: a non-obvious "why", a workaround, a constraint imposed from outside the file. An explicit argument, a good name, or a docstring already saying it makes the comment noise.
- If the code you're adding runs 200 lines and could be 50, rewrite what you added.
- Scaffolding is for code that has users. `argparse`, a `main()`, exit codes, error handling, logging, retries: each exists to serve a caller who isn't in the room. A script the asker runs by hand has exactly one caller, so hardcode the values they named and keep only the lines that do the work.
- Sad paths belong in the test suite. A script that demonstrates behavior shows the happy path; re-covering the error cases there is duplication, not diligence.
- When the request comes with an example, the example is the spec, not a starting point. Match its scale.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

Then delete: take out each line you added and ask whether the code still does what was asked. If it does, it stays out. Stop when every remaining line is load-bearing.

## 3. Surgical Changes

**Touch only what you must. Clean up only your own mess.**

When editing existing code:
- Don't "improve" adjacent code, comments, or formatting.
- Don't refactor things that aren't broken.
- Match existing style, even if you'd do it differently.
- If you notice unrelated dead code, mention it - don't delete it.
- Don't expand the diff into existing code just to hit a simplicity target; simplify only what you added.

When your changes create orphans:
- Remove imports/variables/functions that your changes made unused.
- Don't remove pre-existing dead code unless asked.

The test: Every changed line should trace directly to the user's request.

## 4. Goal-Driven Execution

**Define success criteria. Loop until verified — and show your work.**

Transform tasks into verifiable goals:
- "Add validation" → "Write tests for invalid inputs, then make them pass"
- "Fix the bug" → "Write a test that reproduces it, then make it pass"
- "Refactor X" → "Ensure tests pass before and after"

For multi-step tasks, state the plan:
```
1. [Step] → verify: [check]
2. [Step] → verify: [check]
3. [Step] → verify: [check]
```

## 5. Patch Last, Not First

**Monkeypatching is a smell. It's a signal about the code, not a routine test tool.**

Reaching for `monkeypatch`, `mock.patch`, or any runtime rebinding says the code has a
hard-wired dependency the test can't reach from the outside. Sometimes that's true. Work
down this list and stop at the first thing that works:

- Can real input values drive the code down the branch you want? Use them.
- Can you pass a stub *in* — an argument, a fake collaborator, a fixture object — rather
  than reaching in and rewriting a global? Do that.
- Is the thing genuinely uncontrollable from outside — wall-clock time, randomness,
  network, filesystem, hardware? Patch it. That's what the technique is for.

Never add a patch defensively, because a call *looks* like it needs one. Before keeping any
patch, prove it's load-bearing: replace it with something that fails loudly
(`lambda *_: pytest.fail("called")`) and run the suite. If the suite still passes, the
patch was never on the path — delete it.

When a patch is genuinely required, name in your response what design forced it. "I had to
patch X" is a finding about the code worth surfacing, not a test detail to bury.

## 6. Teach As You Go

**Explain the reasoning that isn't obvious from the code — in your response, not in comments.**

After generating code, if a decision wouldn't be obvious from reading it:
- Name the pattern, algorithm, or library feature you used, in a form that's searchable (e.g., "this is a debounce," "this uses a context manager") so there's a term to look up.
- State the key decision and why you made it, in plain language.
- Point to primary sources (official docs, not blogs) when you rely on a library feature the reader may not know.

If asked "why," answer with the underlying concept before specific lines of code. The concept transfers to the next problem; the line does not.

## 7. Commit Messages

**Never add a "Co-Authored-By" trailer.**

- Omit it from the title and the body, in every commit you create.

**One logical change per commit.**

- Never bundle a feature with a bugfix you hit along the way, a refactor with a behavior change, or a rename with an edit. Separate commits.
- Every commit must build and pass tests on its own. If a refactor needs an intermediate state to stay green, write the intermediate state.
- Order so each commit stands alone: preparatory refactors and incidental fixes before the change that needs them.
- Never commit until I've asked for it. When I do, propose the sequence of subjects and wait for my go-ahead before writing any of them.
- Subject: imperative mood, no type prefix. Body: what was wrong and why this change, not a restatement of the diff.
