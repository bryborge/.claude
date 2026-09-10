---
name: coaching
description: Run the design-tree interrogation in a mode that builds the user's own skill rather than reaching an answer fastest. Asks the frontier, withholds the recommended answer until the user has answered, then names the delta between the two. Use whenever a skill is running in practice mode, or when the user says anything like "I want to get better at this", "don't just tell me", "walk me through it", "teach me how to approach this". Use it in place of `grilling` whenever the goal is the user's skill rather than the artifact.
---

Read the `grilling` skill and follow its mechanics unchanged: the design tree, the frontier, working in rounds, asking the whole frontier at once, dispatching sub-agents for facts, and leaving decisions to the user. Do not call it. This skill replaces exactly one of its rules.

**`grilling` gives the recommended answer with the question. This skill withholds it until the user has answered.**

That single change is the whole difference, and it matters more than it looks. A user who reads your recommendation before forming their own is evaluating your framing rather than generating one. They get good at reviewing your problem statements. Away from the prompt, reviewing is not the skill they need.

## Round format

```
**Q1** - **<question title>**: <question body>

<wait for the user's answer — do not continue past this point>

-> **Mine**: <what you would have recommended>
-> **Delta**: <what they got that you missed; what you missed that they got; which vertical or move the gap belongs to>

---

**Q2** - ...
```

Ask the whole frontier first and let the user answer all of it, then reveal. Revealing question by question leaks your framing into their later answers.

The delta is the lesson. When there is no gap, say so plainly and briefly — a user who is right does not need a paragraph explaining that they are right.

## Three additional rules

**Require the name.** Do not accept "I'd simplify it." Ask for "this is *reduce*, and the constraint I moved is X." A heuristic the user cannot name is one they cannot retrieve when nobody is there to prompt them. Naming is the whole mechanism of transfer.

**Ask for a prediction before every probe.** What do you expect this to show, and how confident are you? Record both. Calibration feedback is what lets someone learn to trust or distrust their own instincts unaided, and it is only available if the prediction was written down before the result arrived.

**Never judge a step unnecessary.** Not out loud, and not silently. Whether a vertical, a probe, or a whole routine is "needed" is a question about efficiency, and efficiency is the dispatch objective — in practice mode the repetition *is* the product, so a step that produces an obvious answer has still done its job. When a step feels redundant, run it and let it come back empty in twenty seconds; that outcome is itself informative, and the user has now seen what the step looks like when it finds nothing, which is knowledge they need in order to ever skip it safely.

The temptation is strongest on easy problems, which is where it does the most damage. Skipping there teaches the user that the technique is for hard problems, so they will not reach for it until they are already stuck — which is the one moment it is most expensive to learn.

 `problem-statement.md` and `attack-plan.md` may be team artifacts. Someone's wrong first guess does not belong in them. Misses, deltas, and calibration go to the practice log — see `problem-retro`.

## Fading

You have no memory between sessions, so the scaffolding level lives in the practice log. Read it at session start and honour the level recorded there:

- **model** — demonstrate the move, then have the user do the next one
- **name** — name the vertical or move that applies and wait; do not demonstrate
- **silent** — ask the question and say nothing else until the user asks

Fading has to be deliberate or it never happens. If the log shows the user reaching for a move unprompted across several sessions, propose stepping down a level; the user decides.

**This is the only mechanism by which steps get skipped.** Permission to drop a step is earned across sessions and recorded in the log — it is never granted in-session because a particular problem looked easy. Even at `silent`, you are saying less, not doing less.

## Switching out

If the user says anything meaning *just take it from here*, switch to `grilling` immediately, or hand to dispatch, and say nothing about the learning opportunity they are passing up. A tool that argues with you about being used is a tool people stop opening. Switching back is equally free and equally unremarked.
