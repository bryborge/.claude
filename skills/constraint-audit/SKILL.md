---
name: constraint-audit
description: Sort every stated constraint into walls, prices, and assumptions, so it is clear where the design freedom actually is. Use when a problem looks impossible, when a plan is boxed in by requirements nobody has questioned, when scoping work or writing requirements, or when the user says anything like "we can't because", "the constraint is", "that's not an option", "our hands are tied". Use it before choosing an approach to any hard problem, since most stated constraints turn out to be conventions wearing the costume of requirements.
---

Constraints are what make a problem solvable at all. "Build a bridge" is a wish; "build a bridge for this budget that survives a hundred-year flood" is a problem you can attack, because the space is now finite and you can tell whether a candidate is any good. Constraints prune, and pruning is what makes search tractable.

But most stated constraints are false. They are conventions, preferences, or someone's habit in a requirement's clothing. The work is not listing them — it is sorting them, because you cannot sensibly relax a constraint until you know what kind it is.

## Collect

List every constraint in play: from the problem statement, from the conversation, and from what nobody has said out loud but everyone is designing around. Unstated constraints are the ones that do the most damage, so ask directly what the user is assuming they cannot change.

## Sort

For each constraint, ask two questions — **who imposed it**, and **what actually happens if it is violated** — then place it in one bin:

**Wall.** Physics, arithmetic, hard law. Violation is not priced, it is impossible or prosecuted. Walls are rarer than people think. Test the claim: many things called impossible are merely expensive or unfamiliar.

**Price.** Budget, schedule, compatibility, headcount, appetite. Violable at a cost. A price is only useful once it is named, so put a number or a concrete consequence on it. "Expensive" is not a price; "three extra weeks and one more engineer" is.

**Assumed.** No one can say who imposed it or what happens if it goes. This is where nearly all the design freedom hides, and it is the direct input to any relaxation strategy.

## Report

Return a ledger to whatever called this, or to the user directly if invoked alone:

```md
| Constraint | Bin | Imposed by | Cost of violating |
|---|---|---|---|
| ... | wall / price / assumed | ... | ... |
```

Then say two things plainly:

1. **Which assumed constraints are worth testing first** — ranked by how much freedom each would return if it dissolved.
2. **Which constraints are actually binding** — the ones that, if loosened, would change the answer. Most constraints are not binding and can be ignored while choosing an approach.

## Two traps to name if you see them

**Preferences encoded as constraints.** Once everything is mandatory, nothing can be traded, and the problem becomes artificially impossible. Keep the objective separate from the constraints so trades remain available.

**Over-specifying early.** A constraint list accepted as input can eliminate the good solution before anyone sees it. Treat the list as a working hypothesis to keep testing, not a box handed down.
