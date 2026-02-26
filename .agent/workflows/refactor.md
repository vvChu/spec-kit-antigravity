---
description: Clean up legacy code before feature work, with rollback safety.
---

## User Input
$ARGUMENTS

## Instructions

1. **Git Snapshot**: Before touching any file, instruct the user to commit or stash current changes. Verify the working tree is clean.
2. **Audit**: Scan the target directory `$ARGUMENTS` and list all files to be changed.
3. **Constitution Check**: Compare every pattern found against `memory/constitution.md` and `memory/tech-stack.md`.
   - List each violation found as a **Refactor Audit Artifact** before making any changes.
4. **Refactor**: Apply modern patterns (e.g., convert Promises to Async/Await, replace `var` with `const`/`let`, convert class components to React Hooks) **WITHOUT** changing business logic.
5. **Verify**:
   - Run the full existing test suite.
   - If **any** test fails after refactoring, **auto-rollback** all changes in `$ARGUMENTS` to the pre-refactor state.
   - Report the rollback clearly to the user.
6. **Report**: Generate a `specs/refactor-[date]/refactor-report.md` artifact listing:
   - Files changed
   - Patterns fixed (with before/after examples)
   - Test result: PASS or ROLLED BACK