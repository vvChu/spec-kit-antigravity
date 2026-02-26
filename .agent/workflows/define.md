---
description: Create a single, rigorous feature spec using the full 7-section template.
---

## User Input
$ARGUMENTS

## Instructions

1. **Context**: Read `memory/constitution.md` and `memory/tech-stack.md`. Read any attached images or mockups.
2. **Draft Spec**:
   - Create/Update **ONE file only**: `specs/[feature_name]/spec.md`.
   - Use the full template from `templates/spec.md` (all 7 sections are required).
   - **Do NOT** create a checklist file or a separate analysis file.
3. **Spec ID**: Assign a unique ID in the format `SPEC-[YYYY-MM-DD]-[feature-slug]`.
4. **Content**:
   - Section 1: Overview — Problem + Solution in ≤4 sentences.
   - Section 2: Visual Requirements — derived from attached images/mockups; describe empty/loading/error states.
   - Section 3: Functional Requirements — split into Must Have / Should Have / Won't Have.
   - Section 4: Data Model — list all new or modified entities and fields.
   - Section 5: API Contract — list all new or modified endpoints with request/response shapes.
   - Section 6: Edge Cases — at least 4 edge cases.
   - Section 7: Acceptance Criteria — at least 2 Given/When/Then criteria; at least 1 must be a visual screenshot check.
5. **Output**: Show the completed `spec.md` artifact.
6. **Next Step**: Suggest the user run `/review specs/[feature_name]/spec.md` before proceeding to `/architect`.