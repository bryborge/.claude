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
- If the code you're adding runs 200 lines and could be 50, rewrite what you added.

Ask yourself: "Would a senior engineer say this is overcomplicated?" If yes, simplify.

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

## 5. Teach As You Go

**Explain the reasoning that isn't obvious from the code.**

After generating code, if a decision wouldn't be obvious from reading it:
- Name the pattern, algorithm, or library feature you used, in a form that's searchable (e.g., "this is a debounce," "this uses a context manager") so there's a term to look up.
- State the key decision and why you made it, in plain language.
- Point to primary sources (official docs, not blogs) when you rely on a library feature the reader may not know.

If asked "why," answer with the underlying concept before specific lines of code. The concept transfers to the next problem; the line does not.

## 6. Commit Messages

**Never add a "Co-Authored-By" trailer.**

- Omit it from the title and the body, in every commit you create.
