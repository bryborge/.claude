# Strategy repertoire

Each entry has the same four fields so candidates can be compared side by side:

- **Reach for it when** — the tell that makes this strategy eligible
- **The move** — what you actually do
- **Working looks like** — the early signal that it is paying off
- **Abandon when** — the observation that ends the line

Propose candidates from here; do not run through all of them. Two or three eligible strategies is a round. Seven is a lecture.

---

## Change of representation

**Reach for it when** effort is going into searching rather than seeing, or when the obvious formulation forces you to enumerate cases.

**The move** Re-express the problem in different terms — different coordinates, a different data structure, a graph instead of a list, a picture instead of an equation, money instead of time. Ask what the problem is *in terms of*, not how to search it harder.

**Working looks like** the case analysis collapsing. In a good re-representation the answer often becomes almost immediate rather than merely faster.

**Abandon when** two or three re-framings in, each new representation is as messy as the last. That usually means the difficulty is real rather than notational.

---

## Invariant hunting

**Reach for it when** many moves are available and none seem to make progress, or when you suspect the goal may be unreachable.

**The move** Find something that does not change no matter what move you make. Conserved quantities, parities, monotonic measures, things that only ever increase.

**Working looks like** the invariant deciding the question outright — including deciding that the target is unreachable, which is a real answer and often a valuable one.

**Abandon when** the candidate quantities you can construct all turn out to vary. Weak invariants rarely become strong ones with more effort.

---

## Constraint relaxation

**Reach for it when** the constraint ledger shows prices or assumed constraints rather than walls, or when the problem is easy to describe and hard to satisfy.

**The move** Drop or loosen one constraint, solve the easier problem, then bend the solution back toward the original. Name the constraint you moved.

**Working looks like** the relaxed problem being solvable *and* the gap between it and the real one being informative — you learn which constraint is actually binding, which is worth more than the relaxed solution itself.

**Abandon when** the relaxed version is still hard. Relaxing further just produces a different problem you also cannot solve.

---

## Specialize or generalize

**Reach for it when** the problem has parameters, a size, or a dimension you could turn down — or up.

**The move** Solve the smallest non-trivial case. If that stalls, try the *more* general version: stripping away specifics sometimes removes the distraction rather than adding difficulty.

**Working looks like** a pattern in the small cases that suggests the mechanism, or a general argument that no longer depends on the awkward specific.

**Abandon when** the small cases are degenerate — they lose the feature that makes the real problem hard — or the general case has clearly wandered off the original question.

---

## Bisection

**Reach for it when** there is a working state and a broken state and something in between, or when the failure is somewhere in a long chain you can cut.

**The move** Cut the space in half, determine which half contains the fault, repeat. Applies to code, to systems, to timelines, to organisations, and to arguments.

**Working looks like** each cut genuinely halving the space, with a cheap and unambiguous test at each step.

**Abandon when** you cannot construct a reliable test for "which half", or the fault is not localized — intermittent, distributed, or emergent faults defeat bisection and will waste a lot of time first.

---

## Inversion

**Reach for it when** you cannot see how to succeed, or when the success criteria are vague but the failure modes are vivid.

**The move** Ask how you would *guarantee* failure. Enumerate the ways to lose, then design against them. Often much easier than enumerating ways to win.

**Working looks like** a short list of failure modes that turns out to be nearly exhaustive, so avoiding them leaves only good outcomes.

**Abandon when** the failure list grows without bound. That means success is narrow and specific, and needs to be attacked directly.

---

## Analogy transfer

**Reach for it when** the shape of the problem feels familiar even though the domain does not.

**The move** Name a solved problem this one resembles, and say precisely *what transfers*: the method, the data structure, the proof shape, or only the vocabulary.

**Working looks like** the transfer being mechanical — the analogous solution's steps map onto this problem's objects one for one.

**Abandon when** only the vocabulary transfers. A shared metaphor with no shared mechanism will produce confident and wrong work, so this line is more dangerous than the others when it fails; check the mapping early and explicitly.
