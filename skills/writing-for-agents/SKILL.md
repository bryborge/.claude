---
name: writing-for-agents
description: Writing documents an agent reads. Use when creating, editing, or reviewing a skill, an AGENTS.md, or a CLAUDE.md.
---

A document written for an agent succeeds when the agent takes the same _process_ every run, even though its outputs differ. The levers below reduce that run-to-run variance. They apply to any document an agent consumes: a skill, an instruction file, or a doc reached by a pointer.

- When the document is a skill, also read [`SKILL-MECHANICS.md`](SKILL-MECHANICS.md) for frontmatter, invocation, and router skills.
- When the document is an `AGENTS.md` or `CLAUDE.md`, also read [`INSTRUCTION-FILES.md`](INSTRUCTION-FILES.md) for loading rules, scope, and what belongs in each.

## Context Pointers

A **context pointer** is a line held in context that names material outside it and says when to reach for that material. A skill's description is one; a line in `AGENTS.md` naming a doc is another. The pointer's wording, not its target, decides how reliably the agent reaches the material. When a must-have target goes unread, sharpen the pointer first, and inline the material only if sharpening fails.

A pointer states what the material is and lists the distinct cases that should trigger it. An always-loaded pointer spends tokens and attention every turn, whether or not it fires, so prune it harder than any body:

- Lead with the leading word (see below); the opening is where the triggering happens.
- Give one trigger per case. Synonyms for one case are that case written twice.
- Leave description of the material to the material itself.

Each always-loaded line spends the agent's context. Each document with no pointer spends the human's memory instead, because the human must remember it exists and when to use it. Spend human memory where human judgment should decide when material is used; everywhere else, give the material a pointer.

## Information Hierarchy

Content is either **steps** (ordered actions the agent performs) or **reference** (rules, definitions, and facts consulted on demand), and a document may hold either or both. Place each piece on a three-rung ladder by how immediately the agent needs it:

1. **In-file steps**: what the agent does, in order.
2. **In-file reference**: consulted while doing it. A flat set of peer rules is a fine shape here.
3. **Disclosed reference**: a separate file behind a pointer, loaded only when the pointer fires. It may be a sibling file or one anywhere on disk.

The test for moving material down the ladder: inline what every case needs, and disclose what only some cases reach. Disclose too little and the steps are buried, so attending to them becomes a coin flip. Disclose too much and you hide material the agent needs. Balancing those two is the whole decision.

Within a file, keep a concept's definition, rules, and caveats under one heading, so reading one part brings its neighbors along. A document can fail by length alone, even when every line is live; split it by case or by sequence so each path carries only what it needs.

## Completion Criteria

Every step ends on a condition that tells the agent it is done. Two properties make that condition a lever:

- **Clarity.** A vague bound ("understanding reached") invites premature completion, because the visible later steps pull attention toward finishing. Sharpen the bound first. If it stays irreducibly fuzzy and you observe the rush, split the sequence so the later steps are out of view. Splitting only helps across a real context boundary, such as a hand-off or a subagent; an inline call leaves the later steps in context.
- **Demand.** "Every modified model accounted for" forces digging that "produce a change list" does not. Demand binds reference as well as steps: "every rule applied" sets an exhaustiveness bar for a document with no steps at all.

The strongest criteria are both checkable and exhaustive.

## Leading Words

A **leading word** is a compact concept the model already knows from pretraining (_lesson_, _fog of war_, _tracer bullets_) that it thinks with while running the document. Repeated as a token and never re-explained, it anchors a region of behavior in very few tokens. A coined word works if you define it, but it recruits no priors, so you pay in definition what an existing word gives for free; reach for an existing word first. When the same word appears in your prompts, docs, and code, pointers that use it also fire more reliably.

Look for restatements that a leading word can collapse:

- "fast, deterministic, low-overhead" → _tight_ (a _tight_ loop).
- "a loop you believe in" → _red_, which turns a fuzzy gate into a binary, observable state (the loop goes _red_ on the bug, or it doesn't).

State the target behavior positively. A prohibition puts the forbidden behavior into context and makes it more available, not less. Write "write one-line comments" rather than banning long ones. Reserve prohibitions for hard guardrails that have no positive phrasing, and pair each one with its positive target.

## Pruning

- **One source of truth.** Keep each meaning in one place. Duplication costs maintenance, and it also inflates a meaning's prominence above its real rank.
- **The environment is a source of truth.** Config files, scripts, the directory layout, and `--help` output already say what they say; a document that restates them is a cache that goes stale. Cache only what the agent cannot find by looking: the unwritten convention, the reason behind a choice, the gotcha no config confesses.
- **Relevance.** Every line should still bear on the task. Lines go stale as the code or the world changes. Without regular pruning, stale layers settle, because adding feels safe and removing feels risky.
- **No-ops.** An instruction the model already follows by default pays load to say nothing. Judge it against the model's default, not against what a human reader would need, and settle disagreements by running the document. Delete the whole failing sentence rather than trimming its words. A leading word too weak to beat the default (_be thorough_) is a no-op too; replace it with a stronger word (_relentless_).

## Review Pass

An edit is done when every item holds:

- Each always-loaded pointer leads with its leading word and names only distinct cases.
- Material that only some cases need sits behind a pointer.
- Every step ends on a checkable completion criterion.
- Every directive names the target behavior; any prohibition is a guardrail paired with its positive.
- Every line is live: it bears on the task, appears once, and tells the agent something the environment and its defaults do not.

