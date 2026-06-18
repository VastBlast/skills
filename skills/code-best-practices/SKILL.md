---
name: code-best-practices
description: Apply the user's concise code-best-practices rules only when the user explicitly requests this skill or asks to use these coding best-practice rules.
---

# Code Best Practices

- Understand the project goal and affected workflow before changing code.
- For bugs, find the root cause; the real issue may be deeper than the first visible symptom or example.
- Follow the project's existing style, formatting, APIs, helpers, and idioms, including choices between equivalent patterns, unless they hurt correctness, performance, or code quality.
- Keep code concise, maintainable, and easy to change later. Avoid hacky, lazy, brittle, or overcomplicated easily-breakable solutions.
- Avoid redundancy: redundancy includes but is not limited to duplicate logic in different places, tiny helpers that are only used once, explicit types that can be inferred, and unnecessary wrappers that provide no real value unless they clearly improve readability, create real reuse, or define a useful boundary. Also constants that are only used once should be inlined, you may add a short comment to explain the value if it is not obvious.
- Keep simple control flow compact when the project style allows it, but do not compress complex logic or side effects just to make code shorter.
- Think through realistic edge cases and side effects and always consider how your changes could directly or indirectly affect other code, including future changes.
- Use helpful comments when they make code easier to read or maintain; keep them concise and plain (do not use fancy hard to understand wording).
- Prefer minimal dependencies, but do not reinvent mature (especially complex) functionality. If adding a dependency, prefer modern, performant, lightweight, maintained packages with healthy adoption.
