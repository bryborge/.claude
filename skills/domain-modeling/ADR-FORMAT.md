# ADR Format

ADRs live in `docs/adr/` as `0001-slug.md`, `0002-slug.md`, numbered in sequence.

## What Qualifies

Decisions like these usually pass the gate in [SKILL.md](SKILL.md):

- **Architectural shape.** "The current loop runs in the PWM-synchronous ADC interrupt, not in an RTOS task." "Release builds run in hermetic containers."
- **Integration between contexts.** "Telemetry reads Frames from a lock-free ring buffer and never blocks the control ISR."
- **Choices that carry lock-in.** MCU family, RTOS, bootloader, signing-key custody. Record only the ones that would take a board spin or a quarter to undo.
- **Boundary and scope.** "Only the Delivery pipeline can reach the signing key; no other CI job sees it." The explicit no's are as valuable as the yes's.
- **Deliberate deviations from the obvious path.** "Control math is Q15 fixed-point so the ISR never stacks FPU context." These stop the next engineer from "fixing" something deliberate.
- **Constraints invisible in the code.** "Overcurrent shutdown must finish inside the power MOSFETs' short-circuit withstand time." "Builds must be reproducible so customers can verify the SBOM against the Image."
- **Non-obvious rejections.** "We considered Zephyr and chose FreeRTOS because …" Record it, or someone will propose Zephyr again in six months.

## Template

```md
# {Short title of the decision}

{1-3 sentences: the context, the decision, and why.}
```

An ADR can be a single paragraph. Its value is recording _that_ a decision was made and _why_.

## Optional Sections

Add one only when it carries something the paragraph cannot:

- **Status** frontmatter (`proposed | accepted | deprecated | superseded by ADR-NNNN`): when decisions get revisited
- **Considered Options**: when the rejected alternatives are worth remembering
- **Consequences**: when downstream effects are non-obvious
