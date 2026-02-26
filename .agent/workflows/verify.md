---
description: Visual and logic verification of the feature against every Acceptance Criterion.
---

## User Input
$ARGUMENTS (feature_name)

## Antigravity QA Instructions

1. **Load Spec**: Read `specs/[feature_name]/spec.md`. Extract every item under **Section 7: Acceptance Criteria**.
2. **Environment**: Spin up the app in the Integrated Terminal/Browser.
3. **Visual Audit**:
   - Navigate to the new feature.
   - **TAKE SCREENSHOT**.
   - Compare screenshot pixel-by-pixel to the Visual Requirements in `spec.md` Section 2.
   - Report: `✅ Match` or `❌ Discrepancy: [description]`.
4. **Acceptance Criteria Audit**: For each `AC-XX` item in Section 7:
   - Execute the Given/When/Then scenario.
   - Mark as `✅ PASS` or `❌ FAIL: [reason]`.
5. **Regression Check**:
   - Run the full test suite.
   - Report any newly failing tests as `❌ REGRESSION: [test name]`.
6. **Report**: Generate `specs/[feature_name]/verify-report.md` containing:
   - Visual audit result
   - AC-by-AC results table
   - Regression check result
   - Final verdict: `✅ RELEASE READY` or `❌ BLOCKED: [list of failures]`