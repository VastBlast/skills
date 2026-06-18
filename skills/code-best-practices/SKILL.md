---
name: code-best-practices
description: Apply concise repository-aware coding best practices when the user explicitly requests this skill or asks to use these coding best-practice rules.
---

# Code Best Practices

When requested, use this skill as a baseline for coding work across repositories.

## Rule Loading

Read `references/general.md` before writing, editing, reviewing, testing, documenting, or explaining code.

## Priority

Resolve conflicts in this order:

1. Explicit user instructions in the current conversation.
2. Repository-local instructions, tests, configs, and established patterns.
3. General rules from this skill.

When a conflict is material, follow the higher-priority source and mention the tradeoff briefly if it affects the result.
