# Problem types

Classification decides which strategies are eligible. Getting it wrong wastes the session, so treat it as a decision to put to the user rather than a label to apply quietly.

Read the tells, then put your placement to the user with your reasoning and your recommended answer.

---

## 1. Known method

**Tells** Someone has solved this exact shape before. A standard technique, library, runbook, or precedent exists. The difficulty is volume, care, or tedium.

**Eligible strategies** None, really. This is execution.

**What to do — dispatch mode** Say so plainly and get out of the way. Confirm the method applies, check the constraint ledger for anything that would invalidate it, then let the user work. Reaching for a strategy repertoire here manufactures ceremony around a problem that just needs doing, which is a real cost — it burns the user's patience for the skill on an occasion that did not need it.

**What to do — practice mode** Run the routine anyway. The value is not in discovering a strategy, it is in the user *arriving at* "known method" by working the verticals rather than by pattern-matching. Those two look identical from the outside and are completely different skills: one is transferable, the other only fires on problems they have already seen. Bowing out here deprives them of the single cheapest full repetition available, and it is exactly the occasion where a full pass costs almost nothing.

---

## 2. No known method

**Tells** The problem is stated clearly and the target is well defined, but no route to it is known. Attempts so far have been searches rather than arguments.

**Eligible strategies** The full repertoire, with change of representation, invariant hunting, and constraint relaxation first. Analogy transfer is high-value here and also the most dangerous — check that mechanism transfers, not just vocabulary.

**What to do** This is the case the skill is built for. Run the normal order of operations.

---

## 3. Ill-defined

**Tells** The success criteria are vague or contested. Different people describe the problem differently. The statement contains a theory of the cause rather than an observation. Requirements keep arriving. Nobody can say what "done" looks like.

**Eligible strategies** None yet.

**What to do** Stop and call the Skill tool with `define-problem`. This is the most common misroute — an ill-defined problem *feels* like a hard one, so it attracts strategy selection, and every strategy then fails for reasons that look technical but are not. If two consecutive lines of attack have failed for unrelated-seeming reasons, suspect this and come back here.

---

## 4. Adversarial or reflexive

**Tells** Another party responds to your moves. Or your own solution changes the problem: publishing the metric changes the behaviour it measured, deploying the fix shifts the load, pricing the good moves the demand.

**Eligible strategies** Inversion first — enumerating how an opponent or a feedback loop defeats you is usually more tractable than planning a win. Bisection and invariant hunting still work if the invariant holds under response. Anything that assumes a static target is unsafe here, including most relaxation, because the relaxed problem may not bend back once the environment has moved.

**What to do** Set the budget shorter than you would otherwise, and make the abandon condition an observation about the *environment's response*, not about your own progress. A solution that works in test and moves the problem in production has not failed the test; it has failed the classification.

---

## When it fits more than one

Take the more demanding classification. A problem that is partly ill-defined and partly hard is ill-defined — the undefined part will contaminate the attack. A problem that is reflexive and also has a known method is reflexive, because the known method was validated in a world that did not respond.
