---
name: bottom-out
description: Bottom out on a plan, decision, or idea through a relentless interview until we reach a shared understanding. Use when the user wants to bottom out on something, explore an idea for a project, audit an idea, or be grilled on it.
---

# Bottom Out

Interview the user relentlessly until you reach a shared understanding. Map the subject as a **design tree**: every decision branches into the decisions that hang off it, down to **leaves**.

A decision is a leaf, and settled, when all three hold:

1. The user has answered it.
2. The answer survived challenge: you found no gap in it, or the user has answered the one you raised.
3. Acting on it requires no further choice. Each choice still open becomes a child branch.

## Rounds

The **frontier** is every unsettled decision whose prerequisites are settled: the questions you can ask now without guessing at answers you haven't heard. Each round, ask up to four frontier questions, choosing the ones with the most decisions hanging off them; the rest of the frontier waits for a later round. Then wait for the user's answers.

```md
**Q1. <Question title>**

<The question, with the context needed to answer it and any options.>

**Recommendation:** <Your answer>. <One-line reason> (checked against <source>, or inferred).

---

**Q2. ...**
```

After each round, recompute the frontier: settled decisions unlock their children, and challenged ones stay on it.

## Challenge

Test each answer before it settles. When an answer has a gap, rests on an unstated assumption, or has a stronger alternative, lead the next round with the challenge and the strongest case against the answer. A revised answer is tested in turn.

## Facts and Decisions

Finding facts is your job; the decisions are the user's. Look up anything the environment can answer rather than asking the user for it:

- **A targeted lookup** (one file, one search, one command): do it yourself before the round.
- **A broad search** across many files or sources: dispatch a background subagent. Questions downstream of it wait for its report; ask the rest of the frontier now.

When a decision turns on what a domain term means, or is one an ADR might record, call the Skill tool with `domain-modeling`.

## Done

The interview is done when the frontier is empty: every branch followed to its leaves, nothing silently assumed. Then list the settled decisions, numbered, each with its one-line reason, and wait for the user to confirm the list before acting on any of it.
