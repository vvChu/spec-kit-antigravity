# Project Constitution

> Agents MUST read this file at the start of every workflow.

---

## Article I: The Artifact Mandate
**Agents shall not perform work without a visible Artifact.**
- Every planning step must produce a Markdown Artifact (Plan, Spec, Checklist, or Report).
- Never rely on "chat memory" alone. If it is important, write it to a file.

## Article II: Vision Verification
**Trust but Verify (Visually).**
- When implementing UI, the Agent MUST take a screenshot using the integrated Browser.
- Compare the screenshot to the original requirement or mockup in `spec.md` Section 2.
- If pixels do not match, the task is incomplete.

## Article III: Agent Independence
**Build for Parallelism.**
- Tasks must be atomic and self-contained.
- Frontend agents should mock API responses if the Backend agent has not finished.
- Never block a thread waiting for another agent.

## Article IV: Code Health
- **No Legacy Patterns**: Use modern syntax (e.g., React Hooks, ES6+, Python 3.12+, async/await).
- **Self-Correction**: If a test fails, attempt to fix it *once* before asking the user.
- See `memory/tech-stack.md` for the full list of forbidden and preferred patterns.

## Article V: Security First
- **Never** hardcode secrets, API keys, tokens, or credentials anywhere in source code.
- All secrets must be stored in environment variables and accessed via the pattern defined in `memory/tech-stack.md`.
- All user inputs must be validated and sanitised before use.
- Never log sensitive user data (passwords, tokens, PII).

## Article VI: Test Coverage
- Every new feature must include unit tests covering the core business logic.
- Every API endpoint must have at least one integration test.
- Minimum acceptable test coverage threshold: **80%** (line coverage, branch coverage, and function coverage).
- Tests must be written before a feature is considered complete.

## Article VII: Spec Traceability
- Every code change must reference a spec file (`specs/[feature_name]/spec.md`).
- No code shall be written without a corresponding, approved spec artifact.
- Spec IDs must appear in commit messages: e.g., `feat(SPEC-2026-02-26-auth): implement login flow`.

## Article VIII: Rollback Safety
- Before any refactoring, the working tree must be clean (all changes committed or stashed).
- After refactoring, the full test suite must pass before the refactor is considered complete.
- If any test fails after a refactor, **auto-rollback** all changes and report to the user.