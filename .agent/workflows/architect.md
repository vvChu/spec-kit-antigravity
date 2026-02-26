---
description: Create a unified implementation plan from an approved spec.
---

## User Input
$ARGUMENTS (path to spec.md)

## Instructions

1. **Pre-flight Check**: Read the spec at `$ARGUMENTS`.
   - Confirm the spec **Status** field is `Approved`. If it is `Draft` or `In Review`, halt and ask the user to run `/review` first.
2. **Read Stack**: Load `memory/tech-stack.md` to understand preferred libraries and forbidden patterns.
3. **Draft Plan**:
   - Create/Update **ONE file**: `specs/[feature_name]/plan.md`.
   - **Section 1 — Architecture**: List all files to be created or modified, and any data model changes.
   - **Section 2 — Dependency Graph**: Draw an ASCII dependency graph showing which tasks must complete before others.
   - **Section 3 — Step-by-Step Tasks**: List every implementation step as a checkbox `- [ ]`. Tag each with `[Frontend]`, `[Backend]`, `[Test]`, or `[DevOps]`.
   - **Section 4 — Parallel Groups**: Group tasks into parallel execution groups (Group A, Group B, etc.) for Manager View.
4. **Constraint**: Do NOT create `tasks.md`. Keep everything in `plan.md`.
5. **Output**: Show the completed `plan.md` artifact.