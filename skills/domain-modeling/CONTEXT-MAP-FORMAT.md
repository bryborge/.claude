# CONTEXT-MAP.md Format

A `CONTEXT-MAP.md` at the repo root lists each bounded context, where its `CONTEXT.md` lives, and how the contexts relate. Each context keeps its own decisions in a `docs/adr/` beside its `CONTEXT.md`; decisions that span contexts go in the root `docs/adr/`.

```md
# Context Map

## Contexts

- [Motor Control](./firmware/control/CONTEXT.md): closes the current and speed loops and owns Faults
- [Telemetry](./firmware/telemetry/CONTEXT.md): streams Frames to the host over CAN
- [Boot](./firmware/boot/CONTEXT.md): verifies and launches Images
- [Delivery](./pipeline/CONTEXT.md): builds, signs, and publishes Releases

## Relationships

- **Motor Control → Telemetry**: Motor Control writes Frames to a ring buffer; Telemetry drains it without blocking the control ISR
- **Delivery → Boot**: Delivery signs each Image; Boot verifies the signature before launch
- **Motor Control ↔ Telemetry**: Shared `FaultCode` type
```
