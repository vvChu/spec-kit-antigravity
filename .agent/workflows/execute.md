---
description: Build the feature from the plan with error recovery and resumability.
---

## User Input
$ARGUMENTS

## Instructions

1. **Pre-flight**: Read `memory/constitution.md` and `memory/tech-stack.md`.
2. **State Check**: Look for a `specs/[feature_name]/.progress` file.
   - If it exists, resume from the last unchecked `- [ ]` item.
   - If it does not exist, start from the beginning.
3. **Execute Loop**:
   - Execute the next unchecked item `- [ ]` one at a time.
   - Mark as `- [x]` in `plan.md` immediately upon completion.
   - Write the last completed step index to `specs/[feature_name]/.progress`.
4. **Error Handling**:
   - If a step fails, annotate it with `- [!] Step X: [error summary]` in `plan.md`.
   - Attempt self-correction **once** automatically.
   - If the step still fails after one retry, **halt** and generate a **Blocker Artifact** containing:
     - The failing step description
     - The full error message
     - Suggested next actions for the user
5. **Vibe Check**: After every 3 completed steps:
   - Take a screenshot using the integrated Browser.
   - Compare to the visual requirements in `specs/[feature_name]/spec.md`.
   - If a discrepancy is found, fix it before continuing.
6. **Completion**:
   - Delete the `.progress` file.
   - Generate a **Build Summary Artifact** listing all completed steps and any skipped or blocked items.