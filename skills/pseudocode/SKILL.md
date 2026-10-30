---
name: pseudocode
description: Pseudocode, capturing algorithm decisions as structured-English pseudocode in docs/algorithms.md for the user to implement themselves as practice. Use when the user asks to pseudocode something they mean to design or build ("/pseudocode", "let's pseudocode the parser"), or when bottom-out reaches an algorithmic decision. A one-off question like "what's the pseudocode for binary search" gets a plain chat answer instead.
---

# Pseudocode

Capture each algorithmic decision as pseudocode in `docs/algorithms.md`, a **map** the user reads and then builds into code themselves. The point is deliberate practice: the user does the translation into whatever language they are studying, and the bugs they meet along the way are part of the lesson.

## Hand-off

Hand over the map; the user builds from it. Write implementation code only when the user explicitly asks for it.

## The File

`docs/algorithms.md` is a **working draft**, shaped in real time like clay on the wheel, so it can serve as the shared reference during the discussion.

- Write each entry as soon as its algorithm has a shape, and revise it in place as answers change. The draft is exempt from bottom-out's rule to wait for confirmation before acting.
- Mark each undecided point inline where it occurs, as `[OPEN: what happens when the buffer is full?]`, and remove the marker when the decision settles.
- When the file already exists, append new entries to it.
- Leave git to the user. Delete the file only when the user asks.

## Inside a bottom-out Session

At the first algorithmic decision of the session, ask once who leads on algorithms:

- **Recommend:** you recommend, as bottom-out does for every question. This is the default if the user skips the question.
- **Propose first:** you lay out the problem and its constraints and ask how the user would approach it. Give your view only after they commit to an answer, then challenge it.

Apply the answer to every algorithmic decision for the rest of the session.

## Direct Invocation

When the user invokes the skill outside a bottom-out session, write from what the conversation has already settled. Ask a clarifying question wherever the pseudocode would otherwise require you to guess. If it is unclear what the user wants captured, offer to bottom out on it first.

## Entry Format

~~~md
## Debounce the start button

```
FUNCTION debounce(sample)
    IF sample equals last_sample THEN
        INCREMENT stable_count
    ELSE
        SET stable_count TO 0
    END IF
    RETURN stable_count is at least THRESHOLD
END FUNCTION
```

### Suggested order

1. Write the stable-count update first; it is the core of the
   debounce. Counting matching samples instead of timing them:
   no dependency on a clock.
2. Add the threshold check ...
~~~

- One `##` heading per subject, so appended entries stay separable.
- Write the pseudocode inside a plain code fence, in plain English, with these uppercase keywords: `FUNCTION`/`RETURN`, `IF`/`THEN`/`ELSE`/`END IF`, `FOR`/`END FOR`, `WHILE`/`DO`/`END WHILE`, `REPEAT`/`UNTIL`, `CASE`/`END CASE`, `SET`/`INCREMENT`. Close every block with its `END` marker and indent its body.
- Keep the pseudocode language-neutral. Language-specific hazards such as overflow, ISR safety, and floating point are for the user to find while building.
- Under `### Suggested order`, list the order in which to build the pseudocode. Attach a one-line *why* to the step where a design choice is made.

## Done

An entry is done when it has no `[OPEN: …]` markers left. The skill's work is done when every algorithmic decision in the conversation has a done entry, or when the user declares it done ("I'm done", "ready to implement in Rust now"). Leave any remaining `[OPEN: …]` markers in place for the user to resolve while building.
