---
description: Package and deploy a verified feature to the target environment.
---

## User Input
$ARGUMENTS (target environment: staging | production)

## Instructions

1. **Pre-flight Check**:
   - Read `specs/[feature_name]/verify-report.md`.
   - Confirm the final verdict is `✅ RELEASE READY`. If not, **halt** and show the list of failures to the user.
   - Confirm all checkboxes in `specs/[feature_name]/plan.md` are marked `- [x]`.
2. **Environment Confirmation**:
   - Target: `$ARGUMENTS` (default: `staging` if not provided).
   - Show the user the target and ask for explicit confirmation before proceeding.
3. **Build**:
   - Run the build command defined in `memory/tech-stack.md` under `## DevOps & Deployment`.
   - Capture build output. If build fails, halt and surface the error.
4. **Deploy**:
   - Execute the deployment script for the target environment.
   - Stream deployment logs as a live artifact.
5. **Post-Deploy Smoke Test**:
   - Hit the health-check endpoint.
   - Navigate to the deployed feature in the integrated Browser.
   - Take a screenshot and compare to the `verify-report.md` screenshot.
6. **Release Artifact**: Create `specs/[feature_name]/release.md` containing:
   - Feature name and Spec ID
   - Deploy timestamp (ISO 8601)
   - Target environment
   - Build hash / commit SHA
   - Smoke test result: `✅ HEALTHY` or `❌ DEGRADED`
