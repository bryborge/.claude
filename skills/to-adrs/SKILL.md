---
name: to-adrs
description: Use when a user wants to create, write, name, place, or organize an Architecture Decision Record (ADR) in a software project — e.g. "write an ADR for choosing a database", "document this architecture decision", "set up an adr/ or decisions/ directory", "which ADR template should I use", "supersede an old ADR". Covers picking a template, naming the file, filling in context/decision/consequences, and deciding whether a decision even needs an ADR.
disable-model-invocation: true
---

# Architecture Decision Record (ADR) Skill

Helps a developer or team create and maintain architecture decision records: short documents that capture an important architecture decision, the context that led to it, and its consequences.

This skill is general-purpose: it applies to any repository the user is working in, not just this one. `templates.md` and `writing-guide.md` are self-contained — no need to read the rest of this repo to use them.

## 1. Decide if this Decision Deserves an ADR

Not every decision needs one. Recommend an ADR when the decision:

- Is architecturally significant (affects structure, external interfaces, quality attributes, or is expensive/risky to reverse).
- Needs to be understood by future developers who weren't in the room.
- Involved real trade-offs worth recording (not a one-line style choice already covered by a linter or style guide).

Skip an ADR when the decision is tiny, self-contained, single-developer, already covered by policy/standards, or purely a temporary workaround/POC.

If the user is unsure, ask what the decision is and who needs to understand "why" later — that usually settles it.

## 2. Find or Create the ADR Directory

Look for an existing convention first:

```sh
git ls-files | grep -iE '(^|/)(adr|adrs|decisions?)(/|$)'
```

- If one exists, follow its naming/format/numbering so far.
- If none exists, ask the user (or default to) a top-level `decisions/` or `adr/` directory. Some teams prefer `decisions/` because the word "architecture" and the abbreviation "ADR" put some contributors off, while "decisions" invites broader use (vendor, planning, scheduling decisions too).
- Some projects number files (`0001-choose-database.md`, adr-tools style); others don't. Match what's already there; otherwise unnumbered present-tense file names (see below) are simplest to start with.

## 3. Name the File

Convention used across this ecosystem:

- A present-tense imperative verb phrase, e.g. `choose-database.md`, `format-timestamps.md`, `manage-passwords.md`, `handle-exceptions.md`.
- Lowercase with dashes.
- `.md` extension.
- If the project numbers ADRs, prefix with a zero-padded sequence number, e.g. `0007-choose-database.md`.

## 4. The Template

Use the [adr-template.md](adr-template.md).

## 5. Write it Well

Load `writing-guide.md` for the fuller checklist. The essentials:

- **One decision per ADR.** Don't bundle multiple architecturally distinct decisions into one file.
- **Context** should explain the organization's situation, constraints, and the forces in tension — not just "we needed a database."
- **Decision** should state the chosen direction plainly, not hedge.
- **Consequences** should cover both what gets easier and what gets harder, plus any follow-on ADRs this decision now requires.
- **Timestamp it.** Costs, vendor pricing, and scaling numbers change — date anything that might go stale.
- Give the record a status: `proposed | accepted | rejected | deprecated | superseded by <link>`.

## 6. Handle Supersession, Not Silent Edits

ADRs are treated as immutable. When a new decision replaces an old one:

1. Create a new ADR file describing the new decision.
2. Update the old ADR's Status to `Superseded by [new-adr](path)`.
3. Link back from the new ADR's Status/Links section: `Supersedes [old-adr](path)`.
