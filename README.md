# Claude

My custom harness for Anthropic's AI ecosystem.

## Overview

Following is how I generally prefer to build software w/ AI. It closely resembles how I prefer to work in engineering teams (because these are processes and principles we have followed in software development for a long time with a high rate of success).

### General Terminology

- **Harness:** Everything around an LLM that decides what it "remembers," what it checks, which tasks get context and which get relegated to subagents.

### Prerequisites

Skills depend on the following cli tools:
- gh
- git

## Reference

This section must stay up to date: whenever an agent or skill is added, removed, or renamed, update the corresponding entry below in the same change.

### Skills

#### User-invoked

- **[grill-me](./skills/grill-me/SKILL.md)**: Get relentlessly interviewed about a plan or design until every branch of the design tree is resolved.
- **[to-adrs](./skills/to-adrs/SKILL.md)**: Create and maintain Architecture Decision Records — deciding whether a decision deserves one, picking a template, naming the file, and handling supersession.
- **[to-spec](./skills/to-spec/SKILL.md)**: Turn the current conversation into a spec (problem statement, user stories, implementation/testing decisions) and publish it to the project issue tracker.
- **[to-tickets](./skills/to-tickets/SKILL.md)**: Break a plan, spec, or conversation into tracer-bullet tickets, each declaring the tickets that block it, and publish them to the configured tracker.

#### Model-invoked

- **[codebase-design](./skills/codebase-design/SKILL.md)**: Shared vocabulary for designing deep modules — module, interface, depth, seam, adapter, leverage, locality. Use when designing or improving a module's interface, finding deepening opportunities, or deciding where a seam goes.
- **[code-review](./skills/code-review/SKILL.md)**: Review the diff since a fixed point along two axes — Standards (repo conventions plus a baseline of Fowler code smells) and Spec (does it match the originating issue) — run as parallel sub-agents and reported side by side.
- **[grilling](./skills/grilling/SKILL.md)**: Interview the user relentlessly about a plan, decision, or idea until every branch of the design tree is resolved. The reusable interview primitive behind `grill-me`.
- **[tdd](./skills/tdd/SKILL.md)**: Test-driven development reference for the red → green loop — what a good test is, where tests go (seams), and the anti-patterns (implementation-coupled, tautological, horizontal slicing) to avoid.
- **[writing-for-agents](./skills/writing-for-agents/SKILL.md)**: Writing documents for agents. Use when creating or editing skills, or modifying AGENTS.md or CLAUDE.md.
