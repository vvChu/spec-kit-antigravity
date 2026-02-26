---
description: Review a spec for completeness and constitution compliance before architecture planning.
---

## User Input
$ARGUMENTS (path to spec.md)

## Instructions

1. **Load Spec**: Read the spec at `$ARGUMENTS`.
2. **Completeness Check** — verify that ALL 7 sections exist and are non-empty:
   - [ ] Section 1: Overview
   - [ ] Section 2: Visual Requirements
   - [ ] Section 3: Functional Requirements
   - [ ] Section 4: Data Model
   - [ ] Section 5: API Contract
   - [ ] Section 6: Edge Cases (minimum 4 items)
   - [ ] Section 7: Acceptance Criteria (minimum 2 items, at least 1 visual)
3. **Constitution Compliance**: Check the spec against `memory/constitution.md`:
   - Flag any requirement that implies hardcoded secrets.
   - Flag any requirement with no corresponding test criteria.
   - Flag any requirement that blocks parallel execution (violates Article III).
4. **Output**: Generate a **Spec Review Artifact** containing:
   - **Score**: [X / 7 sections complete]
   - **Missing / incomplete sections**: listed with suggested content
   - **Constitution violations**: listed with the relevant Article
   - **Verdict**: `✅ APPROVED` (score = 7 and no violations) or `❌ NEEDS REVISION` (anything else)
5. **If APPROVED**: Update the `Status` field in the spec file from `Draft` to `In Review` and suggest the user get a human sign-off before running `/architect`.
