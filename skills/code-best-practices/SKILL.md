---
name: code-best-practices
description: Apply the user's concise code-best-practices rules only when the user explicitly requests this skill or asks to use these coding best-practice rules.
---

# Code Best Practices

Use this skill only when requested. Treat these as preferences for better code, not as reasons to avoid necessary work.

- Understand the project goal and affected workflow before changing code. For bugs, find the root cause; the real issue may be deeper than the first visible symptom or example.
- Follow the project's existing style, formatting, APIs, helpers, and idioms, including choices between equivalent patterns, unless they hurt correctness, performance, or code quality.
- Keep code concise, maintainable, and easy to change later. Avoid hacky, lazy, brittle, or overcomplicated solutions.
- Stay focused on the requested work while decluttering directly related code when it helps.
- Avoid redundancy: do not add tiny one-use helpers, unnecessary wrappers, duplicate logic, redundant constants, or explicit types that can be inferred unless they clearly improve readability or define a useful boundary.
- Keep simple control flow compact when the project style allows it, but do not compress complex logic or side effects just to make code shorter.
- Think through realistic edge cases and side effects, but do not add handling for cases that cannot occur in the actual path unless they are likely to occur in practice or in future code edits.
- Use helpful comments when they make code easier to read or maintain; keep them concise and plain.
- Prefer minimal dependencies, but do not reinvent mature functionality. When adding a dependency, prefer modern, performant, lightweight, maintained packages with healthy adoption.
- Add or update tests only when a relevant test suite exists and the test adds meaningful confidence to your changes.
