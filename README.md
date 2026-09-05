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

- **[grill-me](./skills/grill-me/SKILL.md)**: Get relentlessly interviewed about a plan or design until every branch of the design tree is resolved.
- **[prd-doc](./skills/prd-doc/SKILL.md)**: Create a Product Requirements Document (PRD) to scope out work, align the model and user vision of the goals and objectives, and clarify what to build and why we must build it.

#### Model-invoked

- **[grilling](./skills/grilling/SKILL.md)**: Interview the user relentlessly about a plan, decision, or idea until every branch of the design tree is resolved. The reusable interview primitive behind `grill-me`.
- **[writing-for-agents](./skills/writing-for-agents/SKILL.md)**: Writing documents for agents. Use when creating or editing skills, or modifying AGENTS.md or CLAUDE.md.
