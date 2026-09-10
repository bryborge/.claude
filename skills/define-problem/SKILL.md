---
name: define-problem
description: Help the user practice good problem-solving technique and empower them to sharpen their skillset at turning a problem into a well-defined problem statement.
disable-model-invocation: true
---

> [!IMPORTANT]
> Do not solve or supply any solution to the user's problem! The primary objective is to empower the user to use the tools they know to solve any problem they face. The secondary objective is to capture all the details of the problem that the user identifies in a problem statement document.

## Declare the mode first

Ask which mode this session is in, unless the user's phrasing already settles it — *"help me get better at this"* is practice, *"I just need this scoped"* is dispatch. Do not infer it from how hard the problem looks. A skill that decides to teach you when you are on a deadline is one you stop opening.

- **Practice** — the user's skill is the point. Call the Skill tool with `coaching` rather than `grilling`, and follow the additional rules below.
- **Dispatch** — the artifact is the point. Call the Skill tool with `grilling` as normal and skip the additional rules.

Switching mid-session is free and goes unremarked in either direction.

> [!IMPORTANT]
> **In practice mode the routine is the deliverable, not the document.** Run all seven verticals, every time, whatever the problem looks like. Do not assess whether the problem "needs" this format. Size, difficulty, and apparent clarity are not criteria — a small, fully-specified, unambiguous problem is the *best* occasion to practice, because the technique is cheap to execute and the user can watch it work end to end. Nobody learns a technique they only reach for when desperate.
>
> A spec that appears fully specified is a claim, and vertical 1 is the test of it. Skipping the routine because there is "no ambiguity to untangle" removes the exact step that would have shown whether that was true. It usually isn't.
>
> Deciding a step is unnecessary is dispatch reasoning. It has no place in a practice session, and a student cannot yet tell when skipping is safe — that judgment is what the fading level in the practice log exists to build, over sessions, rather than something to grant them in session one.

## The seven verticals

The seven verticals below are Pólya's *How to Solve It* heuristics, and they are the seed set for the design tree: one branch root each. Work them in order. The inventory feeds every vertical under it, and the plan falls out of the definition rather than preceding it.

1. **Start with what you know.** List what the problem statement gives us (especially the operational constraints), then list what it withholds. Every vertical below reads from those two lists.
2. **Restate.** State the problem twice: once formally, once by analogy.
3. **Divide.** Name the parts that separate and can be worked in isolation.
4. **Reduce.** Move constraints until what remains is a problem the user already knows how to solve, and name the constraint you moved.
5. **Look for analogies.** Name solved problems this one resembles, and say what transfers from each.
6. **Experiment.** Propose controlled probes. An experiment names in advance what each outcome rules out; a probe that rules nothing out is a guess.
7. **Plan.** State the first move and how we will know it worked.

Use the template below to guide the statement. Every heading maps to a vertical. The routine is done once each one is filled or explicitly marked not applicable, and the user agrees the problem is stated well enough to attack.

In practice mode, *the user* marks a vertical not applicable, never you, and they say why. "This problem has no separable parts because X" is a worked vertical; it takes twenty seconds and it is a real answer. Silently dropping the heading is not. Offering to drop it is worse, because it teaches that the step is optional under conditions the user cannot yet evaluate.

Then write the statement to a new directory at the project root with the file named `problem-statement` (e.g. `projectroot/<problem-title>/problem-statement.md`). When filling out the document, preserve the blockquotes containing the specific question under each heading.

```md
# Problem Title

This is a Problem Statement for `Problem Title`.

## Symptom

> What is observed, stated without a theory of the cause?

## Known / Unknown

> What does the problem statement give us? What does it withhold?

## Restatement

> The problem stated formally, and again by analogy.

## Sub-problems

> Which parts can be worked in isolation?

## Reduced problem

> The smallest version we already know how to solve, and the constraint moved to get there.

## Analogies

> Which solved problems does this resemble, and what transfers from each?

## Experiments

> Each probe, and what each outcome rules out.

## Plan

> The first move, and how we will know it worked.
```

## In practice mode

The document is the residue. The gap between the user's answer and yours is the lesson, so protect the order: they answer, then you reveal, then you name the delta. `coaching` carries the mechanics; these are the parts specific to defining a problem.

**Make them name the vertical.** Not "I'd simplify it" but "this is *reduce*, and the constraint I moved is X." A heuristic they cannot name is one they cannot retrieve at a whiteboard.

**Get a prediction before every probe.** Vertical 6 already demands that an experiment say what each outcome rules out. Point it at the user as well: what do you expect, and how sure are you? Both go in the practice log, not in the statement.

**Keep the misses out of the statement.** `problem-statement.md` may be read by their team. Wrong first guesses belong in the practice log.

**End with the card, not the document.** Give the user `assets/pocket-card.md` and say plainly what it is for: the seven questions, the three constraint bins, and the seven moves, on one page they could rebuild from memory with no prompt in front of them. That page is the transferable deliverable. The statement is just this problem.

## Closing

Call the Skill tool with `grilling`, or with `coaching` if this session is in practice mode.

Once the statement is written and the user agrees the problem is stated well enough to attack, offer to hand off: call the Skill tool with `attack-problem`, which reads this document and chooses a line of attack. This is the sanctioned exit from the prohibition above — the handoff is how the problem gets solved, not this routine. Do not take it unprompted. If the user would rather attack it themselves, that is the better outcome and the session ends here.

Either way, if the session ends here rather than continuing into `attack-problem`, call the Skill tool with `problem-retro` first. A defining session with no attack still produced moves worth logging.
