---
name: problem-retro
description: Run a short retrospective after a problem has been defined or attacked, and append the result to the user's practice log. Captures which move actually cracked it, whether it was on the candidate list, and how well the user's predictions held up. Use at the end of any problem-solving session, when the user says "that worked" or "we're done", when a line of attack concludes either way, or when the user asks what they should have seen sooner. Use it even when the problem was dispatched rather than worked by hand, since the trace is still worth keeping.
---

Per-problem documents do not transfer. The pattern across problems is what transfers, and it is invisible from inside any single session. This skill exists to make it visible.

Keep it short — four questions, not a ceremony. A retro that costs more than a few minutes gets skipped, and a skipped retro produces no log, and no log means no fading and no diagnosis.

## The questions

1. **Which move actually cracked it?** Name it from the repertoire — change of representation, invariant, relaxation, specialize or generalize, bisection, inversion, analogy. If nothing cracked it, say what the session ruled out instead; that is a real result.
2. **Was it on the candidate list?** If yes, was it the first choice or a fallback. If no, what would have put it there.
3. **How did the predictions do?** Count the probes where the user predicted an outcome in advance, and how many landed. Over-confidence and under-confidence are different problems with different fixes, so record which one this was.
4. **What was assumed that turned out not to be?** Usually a constraint. This is the single most common source of wasted effort, so ask it every time even when the answer is "nothing".

In dispatch mode the user did not work the problem, so ask only 1 and 4, and take the answers from the sub-agents' reported moves rather than from the user.

## The practice log

Find it before assuming it does not exist — search for `practice-log.md`. If there is none, ask the user once where it should live. It is their file and it records their misses, so it may want to sit outside a shared repository. Do not create it silently in a directory their team can read.

Append one session block per session. Use `assets/practice-log-template.md` for the shape:

```md
## <date> — <problem title>

- **Mode**: practice | dispatch
- **Type**: known method | no known method | ill-defined | adversarial
- **Reached for unprompted**:
- **Missed**:
- **Cracked it**:
- **On the candidate list?**:
- **Predictions**: <n> made, <n> landed
- **Assumed but false**:
```

## The diagnosis

Once there are four or more sessions logged, read the whole file and say what the pattern is. This is the actual product of the whole flow — no single session can produce it:

- a move the user consistently skips
- a move they reach for first that is usually wrong for them
- systematic over- or under-confidence in predictions
- a problem type they routinely misclassify

State it as an observation about moves, never as a score. Then update the **Fading level** field at the top of the log if the pattern warrants it, and tell the user you changed it and why. They can change it back.

## Tone

This file is a record of what was tried, not a report card. People stop using tools that grade them, and a practice log that reads like an assessment will quietly stop being written. Keep it factual, keep it in the user's hands, and never surface a past miss in the middle of a live problem — the log is a session-start input and a retro output, and nothing else.