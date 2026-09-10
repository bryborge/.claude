# Claude

My custom harness for Claude AI.

## Overview

### General Terminology

- **Harness:** Everything around an LLM that decides what it "remembers," what it checks, and which tasks get context and which get relegated to subagents.

## Reference

This section must stay up to date: whenever an agent or skill is added, removed, or renamed, update the corresponding entry below in the same change.

### Agents

- **[code-reviewer](./agents/code-reviewer.md)**: Reviews code for quality and best practices.

### Skills

#### User-invoked

- **[adr-doc](./skills/adr-doc/SKILL.md)**: Create an Architecture Decision Record (ADR) to scope out an architectural decision, align the model and user vision of the technical trade-offs, consequences, and context that precipitated the need for this decision, and to clarify how the decision will be enacted.
- **[define-problem](./skills/define-problem/SKILL.md)**: Turn an ill-defined problem into a written problem statement, working Pólya's seven heuristics as the seed set for a grilling session.
- **[grill-me](./skills/grill-me/SKILL.md)**: Get relentlessly interviewed about a plan or design until every branch of the design tree is resolved.
- **[prd-doc](./skills/prd-doc/SKILL.md)**: Create a Product Requirements Document (PRD) to scope out work, align the model and user vision of the goals and objectives, and clarify what to build and why we must build it.

#### Model-invoked

- **[attack-problem](./skills/attack-problem/SKILL.md)**: Choose and run a line of attack on an already-defined problem: audit which constraints are real, classify the problem, pick a strategy with a budget and an abandon condition, and log what's already failed.
- **[coaching](./skills/coaching/SKILL.md)**: Run the `grilling` design-tree interrogation in a mode that builds the user's own skill, withholding the recommended answer until they've answered.
- **[constraint-audit](./skills/constraint-audit/SKILL.md)**: Sort a problem's stated constraints into walls, prices, and assumptions to reveal where the real design freedom is.
- **[grilling](./skills/grilling/SKILL.md)**: Interview the user relentlessly about a plan, decision, or idea until every branch of the design tree is resolved. The reusable interview primitive behind `grill-me`.
- **[problem-retro](./skills/problem-retro/SKILL.md)**: Run a short retrospective after a problem is defined or attacked, capturing what worked and appending it to the user's practice log.
- **[writing-for-agents](./skills/writing-for-agents/SKILL.md)**: Writing documents for agents. Use when creating or editing skills, or modifying AGENTS.md or CLAUDE.md.
