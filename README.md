# Claude

My custom harness for Claude AI.

## Overview

### General Terminology

- **Harness:** Everything around an LLM that decides what it "remembers," what it checks, and which tasks get context and which get relegated to subagents.

## Reference

### Agents

- **[code-reviewer](./agents/code-reviewer.md)**: Reviews code for quality and best practices.

### Skills

#### User-invoked

- **[grill-me](./skills/grill-me/SKILL.md)**: Get relentlessly interviewed about a plan or design until every branch of the design tree is resolved.

#### Model-invoked

- **[grilling](./skills/grilling/SKILL.md)**: Interview the user relentlessly about a plan, decision, or idea until every branch of the design tree is resolved. The reusable interview primitive behind `grill-me`.
- **[writing-for-agents](./skills/writing-for-agents/SKILL.md)**: Writing documents for agents. Use when creating or editing skills, or modifying AGENTS.md or CLAUDE.md.
