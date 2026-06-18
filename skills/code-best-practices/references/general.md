# General Code Best Practices

Apply these rules to all coding tasks unless higher-priority project or user instructions override them.

## Fit the Codebase

- Read nearby code before editing so the change matches local structure, naming, error handling, and test style.
- Understand the project's goal and affected workflow before changing code so the result fits the intended behavior.
- Follow the project's existing style, formatting, APIs, idioms, and helpers unless doing so would hurt correctness, performance, or code quality.
- Preserve public APIs, data formats, migrations, and user-facing behavior unless the request requires changing them.
- Keep changes scoped to the user's request. Avoid unrelated formatting churn, broad rewrites, and opportunistic refactors.

## Keep Code Clean

- Write concise, readable, maintainable code that is easy to change later.
- Prefer clear, boring solutions over "clever", hacky, brittle, lazy, or surface-level fixes.
  - there are *some* cases where you may have no choice but to use a clever solution, but you should always consider whether a simpler solution is possible first.
- Use the simplest solution that fits the current requirements and project design. Do not add complexity where it is not needed.
- If applicable, a restructure that improves maintainability or performance is fine when you are very confident it will not change behavior or introduce side effects (and if your change is related to the core problem you're solving).
- Do not add unnecessary ceremony, wrappers, variables, branches, types, indirection, or tiny one-off helpers unless they improve readability or isolate tricky logic.
- Keep simple control flow compact when the project style allows it, but do not compress complex logic or side effects just to make code shorter.
- Declutter code that directly affects the change, but do not do unrelated cleanup.

## Avoid Redundancy

- Reuse existing helpers, types, schemas, constants, and validation logic instead of duplicating them.
- Add an abstraction only when it removes real duplication, clarifies ownership, or matches an established local pattern. Avoid adding abstractions for one-off cases or to "future-proof" code.
- Prefer inlining values over adding constants when the value is used once. Add a constant only when it is reused, names a useful configuration knob, or meaningfully clarifies intent; use a concise comment instead when that is clearer.
- In typed languages, avoid explicit types that the compiler can infer unless the annotation improves clarity, protects a boundary, documents a constraint, or is required by the project.
- In TypeScript, avoid unnecessary type aliases, interfaces, generic parameters, return annotations, and variable annotations when inference already gives the right type.
- Keep explicit types at useful boundaries, such as exported APIs, component props, request and response shapes, database records, complex generics, and unclear inference cases.

## Correctness

- Think through realistic edge cases and side effects while implementing.
- When fixing a bug, assume it may be deeper than the first visible symptom; identify the root cause and affected paths before patching the provided example.
- Handle cases that can occur in the actual code path. Do not add defensive branches for cases that upstream types, validation, or invariants already make impossible.
- Keep side effects intentional, scoped, and visible at the right boundary.
- Validate untrusted input at boundaries and fail with actionable errors.
- Do not silently swallow errors or catch and ignore them. Handle, propagate, or surface failures with enough context to act on, and do not leak sensitive details in error messages.
- Preserve idempotency for operations that may be retried.
- Avoid hidden global state and shared mutable state unless the codebase already has a clear pattern for it.
- Avoid obvious performance pitfalls on real code paths, such as N+1 queries or repeated work in hot loops, but do not add speculative optimization that hurts clarity.
- Match the project's logging conventions for new diagnostics.

## Security

- Preserve existing auth, authorization, tenant isolation, CSRF, and permission checks when touching request paths or data access.
- Treat untrusted data as a boundary: use established parsers, escaping, and parameterized APIs before passing it into queries, shell commands, paths, templates, deserialization, or dynamic imports.
- Never hardcode secrets, API keys, tokens, or credentials. Use the project's existing config, environment, or secret-management mechanism, and never log or commit them.

## Dependencies

- Avoid new dependencies unless they clearly reduce risk or complexity and fit the project.
- Strive for minimal dependencies, but do not reinvent mature, well-tested functionality that the project should reasonably delegate to a dependency.
- Prefer modern, performant, lightweight, maintained dependencies with healthy adoption when choosing new tooling.
- Do not replace established project tooling solely because a newer option exists; extend the existing setup unless the user asks for migration or the change materially benefits the task.
- Check existing lockfiles, package managers, runtime targets, and deployment compatibility before adding a dependency.

## Tests and Validation

- Add or update tests only when a relevant test suite exists and the test adds meaningful confidence, especially for bug fixes, edge cases, and regressions.
- Prefer tests that exercise public behavior over tests that lock in implementation details.
- Keep tests deterministic by controlling time, random data, network access, and filesystem paths.
- Run the narrowest useful test, formatter, or linter first; broaden validation when the change touches shared behavior.

## Comments and Documentation

- Update docs, examples, config comments, and type declarations when behavior or usage changes.
- Add comments when they make code easier to understand or maintain than code alone.
- Keep comments concise, plain, and easy to understand. Avoid fancy wording.
- Use comments to explain intent, tradeoffs, invariants, lifecycle constraints, surprising behavior, or external requirements.
- Avoid comments that merely restate ordinary control flow; keep comments accurate when behavior changes.

## Final Check

- Inspect the diff before finishing.
- Confirm the change answers the user's newest request.
