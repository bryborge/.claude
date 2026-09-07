---
name: attack-problem
description: Choose and run a line of attack on a problem that is already stated. Audits which constraints are real, classifies the problem, selects strategies with a budget and an abandon condition, and keeps a log of what has already failed. Use when the user is stuck, going in circles, has burned time without movement, has a problem statement and needs a way in, or says anything like "how should I approach this", "I've tried everything", "help me attack this", "I'm out of ideas". Use it whenever someone brings a hard problem wanting movement rather than a definition, even if they never say "attack".
---

This skill starts where `define-problem` stops. That skill is forbidden from solving; this one is the sanctioned exit from it.

A problem does not get solved by trying harder. It gets solved by finding the representation, the invariant, or the movable constraint that collapses it — and by abandoning lines that are not collapsing it fast enough. Both halves matter. Most stuck problems are not under-worked, they are over-worked along one line nobody agreed to stop.

## Declare the mode first

Ask which mode this session is in, unless the user's phrasing already settles it. Do not infer it from how hard the problem looks, and do not infer it from how much of a hurry the user seems to be in — ask, or take what they said.

- **Practice** — the user's skill is the point. Use `coaching` in place of `grilling` at step 5, propose candidate strategies only *after* the user has named theirs, and require them to name the move rather than describe it.
- **Dispatch** — the result is the point. Use `grilling`, and sub-agents may run whole lines of attack on the user's behalf.

Switching mid-session is free and goes unremarked. If the user says anything meaning *just take it from here*, switch to dispatch and say nothing about what they are passing up.

Even in dispatch mode, have each sub-agent return one line naming the move it used and the constraint it moved, alongside its result. That costs nothing, keeps the practice log fed, and builds the vocabulary passively while the user gets throughput.

## Before anything: find the statement

Search the project for the problem statement rather than asking where it is. Finding facts is your job.

**In practice mode, if no statement exists, call the Skill tool with `define-problem` and stop. Always. Do not first assess whether the problem is well-specified enough to skip it.** Whether the problem is small, unambiguous, or already written as a complete spec has no bearing on this: the user chose practice, which means the definition routine is the thing they came for, and a clean problem is the easiest one to learn it on. Judging that a problem "doesn't need" the format is dispatch reasoning, and it silently converts a practice session into a dispatch session without the user agreeing to the switch.

In dispatch mode, use judgment:

- **No statement exists** → call the Skill tool with `define-problem` and stop. An undefined problem attacked is just motion.
- **A statement exists but its Symptom section carries a theory of the cause** → the problem is not actually stated. Say so, and route back to `define-problem`.
- **A statement exists and holds up** → read it in full. Its Known/Unknown, Reduced problem, and Experiments sections are inputs here. Do not re-elicit them.

An `attack-plan.md` may already sit next to the statement from an earlier session. If it does, read the Attempt log first. Repeating a line that already failed is the single most expensive mistake available here.

## Order of operations

The four branch roots below are the seed set for the design tree that `grilling` will work. They have real dependencies, and the frontier honours them: **constraints settle before strategy; strategy settles before budget and abandon condition.** A question about how long to spend on a strategy nobody has chosen belongs to a later round.

### 1. Audit the constraints

Call the Skill tool with `constraint-audit`. Everything downstream depends on it, because choosing a strategy is mostly choosing which constraint you are allowed to move. A constraint you believe is a wall, but which is only a price, is the most common reason a problem looks impossible.

Carry its ledger into the attack plan unchanged.

### 2. Classify the problem

Read `references/problem-types.md` and place the problem. The type determines which strategies are even eligible, so this is not a labelling exercise — the wrong classification wastes the whole session. Put your classification to the user with your reasoning; it is a decision, not a fact.

### 3. Select candidate strategies

Read `references/strategies.md`. Propose two or three candidates that the classification admits, and for each one state up front:

- **the move** — what you would actually do first
- **the budget** — time, attempts, or spend
- **the abandon condition** — the observation that would end this line

A strategy without an abandon condition stated in advance is a commitment, not an experiment. Write it down before starting, because once you are inside a line you will find reasons to keep going.

In practice mode, ask the user which moves they would reach for *before* you read the file to them, then reveal your candidates and name the delta. Which move someone reaches for first, unprompted, is the thing the practice log is tracking; supplying the list first destroys the only measurement available.

### 4. Probe cheaply, in parallel

Where a candidate is cheap to test, dispatch a sub-agent per candidate to attempt it and report back only: *collapsed / did not collapse / what it ruled out.* Run them concurrently and do not block the rest of the frontier on them — a running probe is an unsettled prerequisite, so only questions downstream of it wait.

This is the same division `grilling` draws. Probes are facts and they are yours to find. Which line to commit to is a decision and it is the user's.

### 5. Grill the plan

Call the Skill tool with `grilling`, or with `coaching` if this session is in practice mode, with the roots above as the tree. Do not act on the plan until the user confirms shared understanding.

### 6. Run it, and say in advance how you will know

State the first move and the observation that would tell you it worked. Borrow the standard from `define-problem`: a probe that rules nothing out is a guess.

### 7. Stop on the condition, not on exhaustion

When a line hits its abandon condition, stop and write down *why* — what was tried, what it ruled out, what it cost. Then return to step 3 with the ruled-out territory removed. If two consecutive lines fail for the same underlying reason, the problem is misclassified or misstated; go back to step 2, or back to `define-problem`.

The attempt log is the part of this document that compounds. Everything else is reconstructible; the record of what has already been eliminated is not.

## The document

Write to `attack-plan.md` beside the problem statement, in the same directory. Preserve the blockquote under each heading, as `define-problem` does — keeping the question visible above the answer is what makes the document readable by someone who was not in the room, including you in three months.

The routine is done when each heading is filled or explicitly marked not applicable, and the user agrees the line of attack is worth committing to. In practice mode the same restriction applies as in `define-problem`: the user marks a heading not applicable, not you, and they say why.

```md
# Attack Plan: Problem Title

This is an Attack Plan for `Problem Title`. It reads from `problem-statement.md` in this directory.

## Constraint ledger

> Which constraints are walls, which are prices and at what cost, and which are only assumed?

## Problem type

> Which type is this, and what does that rule in and out?

## Strategies considered

> Which candidates were eligible, and why these?

## Committed line

> The move, the budget, and the abandon condition — all stated before starting.

## Verification

> What observation would show this worked, and what would show it failed?

## Attempt log

> For each line tried: what was done, what it cost, why it stopped, and what it ruled out.
```

## Closing

When the line concludes — cracked, abandoned, or parked — call the Skill tool with `problem-retro`. This holds in both modes: in dispatch the sub-agents' reported moves are the input rather than the user's answers, but the trace is still worth keeping. A session whose attempt log never reaches the practice log teaches nothing beyond this one problem.
