---
name: domain-modeling
description: Domain modeling, building a project's ubiquitous language and bounded contexts. Use when the user wants to do domain modeling or nail down a project's domain, when a domain term is contested or used loosely during design, or when writing or editing a CONTEXT.md, CONTEXT-MAP.md, or ADR.
---

# Domain Modeling

Build the project's **ubiquitous language** while you design: challenge terms, stress-test them with scenarios, and write each one down the moment it resolves. `CONTEXT.md` is the glossary for one **bounded context**; ADRs record the decisions that shape it.

## Files

A single-context repo has one `CONTEXT.md` at the root and its ADRs in `docs/adr/`. A `CONTEXT-MAP.md` at the root means the repo has several contexts; read [CONTEXT-MAP-FORMAT.md](CONTEXT-MAP-FORMAT.md) before working in such a repo or splitting off a second context.

Create each file when you first have something to write in it.

## During the Session

### Challenge against the glossary

When the user uses a term in a way that conflicts with its `CONTEXT.md` entry, call it out at once: "Your glossary defines a Fault as latched until the host clears it, but you're describing one that clears itself. Which is it?"

### Sharpen fuzzy language

When the user uses a vague or overloaded term, propose a precise canonical one: "You're saying 'build': do you mean the Image or the pipeline run that produced it?"

### Stress-test with scenarios

When relationships between concepts are under discussion, invent edge-case scenarios that force a precise boundary between them: a Fault that fires mid-update, an Image signed by a revoked key.

### Cross-reference with code

When the user states how something works, check whether the code agrees, and surface any contradiction: "Your overcurrent ISR clears the Fault on the next PWM cycle, but you just said Faults latch until the host clears them. Which is right?"

### Defer to the datasheet

When a term names hardware (a peripheral, register, field, signal, or pin), the datasheet or reference manual's name is the default canonical term. Challenge drift from it and cite the section. When the project deliberately uses its own name, the glossary entry records the source term.

### Write each term as it resolves

Update `CONTEXT.md` the moment a term resolves, in this format:

```md
# {Context Name}

{One or two sentences: what this context is and why it exists.}

## Language

### Control

**Sample**:
One ADC conversion result for one current-sense channel.
_Avoid_: reading, measurement

**Fault**:
A latched condition in which the power stage stays disabled until the host clears it.
_Avoid_: error, alarm, trip

### Release

**Image**:
A signed firmware binary that the bootloader verifies before launch.
_Avoid_: build, binary, artifact

**Release**:
A tagged Image published together with its SBOM and provenance attestation.
_Avoid_: version, drop
```

- **Be opinionated.** Pick one word per concept and list the others under `_Avoid_`.
- **Define what the term is**, in one or two sentences. Behavior and implementation belong in the code and the ADRs.
- **Include a term only when its meaning is specific to this context.** "ADC" and "retry" are general; "Sample" as defined above is the project's own.
- **Name the hardware source.** When a term differs from the datasheet name it maps to, add `_Datasheet_: {source name} ({document} §{section})`.

### Offer ADRs at the gate

Offer an ADR only when a decision is all three:

1. **Hard to reverse**: changing your mind later carries a real cost.
2. **Surprising without context**: a future reader will ask "why did they do it this way?"
3. **The result of a real trade-off**: there were genuine alternatives, and one was picked for specific reasons.

When a decision passes or nearly passes, read [ADR-FORMAT.md](ADR-FORMAT.md) for examples of what qualifies and the template.

## Done

The session's modeling is done when every domain term used in it either matches its glossary entry or has been resolved and written, and every decision that passed the gate has been offered as an ADR.
