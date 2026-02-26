# Copilot Instructions — spec-kit-antigravity

## What This Repository Is

**spec-kit-antigravity** is an agent-first **Specification & Orchestration Kit** for **Google Antigravity** (Gemini 3). It is a **pure Markdown toolkit** — there is no compiled code, no build system, no package manager, and no test runner. It provides slash-command workflow definitions, governance rules, and templates that structure how AI agents plan, build, verify, refactor, and deploy features using Spec-Driven Development.

- **Type**: Documentation / Agent-Workflow Kit (Markdown only)
- **Languages**: Markdown exclusively — no JavaScript, Python, or any compiled language
- **Size**: ~20 KB, 13 files across 4 directories
- **Default branch**: `main`
- **Forked from**: `waveupHQ/spec-kit-antigravity`

---

## Complete Repository Layout

```
spec-kit-antigravity/
├── README.md
├── .github/
│   └── copilot-instructions.md
├── .agent/
│   └── workflows/
│       ├── define.md       # /define    — create a 7-section feature spec
│       ├── review.md       # /review    — validate spec completeness & compliance
│       ├── architect.md    # /architect — generate implementation plan from approved spec
│       ├── execute.md      # /execute   — build from the plan with error recovery
│       ├── verify.md       # /verify    — visual + AC-by-AC QA audit
│       ├── refactor.md     # /refactor  — modernise legacy code with rollback safety
│       └── deploy.md       # /deploy    — package and deploy a verified feature
├── memory/
│   ├── constitution.md     # 8-article governance rules — MUST read at start of every workflow
│   └── tech-stack.md       # Preferred/forbidden patterns — calibrate to your project
└── templates/
    ├── spec.md             # 7-section spec template (all sections required)
    └── tasks.md            # Parallel task template (Backend / Frontend / Integration)
```

> **No CI pipeline exists.** There is no `.github/workflows/` directory, no `package.json`, no `Makefile`, and no linting config. Do not attempt to run build, install, or test commands — they will fail.

---

## Build, Test & Validation

**There are no build, install, test, or lint commands.** This is a documentation-only repository.

Manual validation checklist before committing:
1. Every `.md` file is well-formed Markdown.
2. All workflow files in `.agent/workflows/` have a front-matter block at the top (`---` / `description:` / `---`).
3. `memory/constitution.md` uses `## Article N: Title` heading format.
4. `templates/spec.md` preserves all 7 sections and all checkbox (`- [ ]`) items.
5. `memory/tech-stack.md` retains all 5 top-level sections.

---

## The Mandatory Workflow Order

Always follow this pipeline — **order matters**:

```
/define → /review → /architect → /execute → /verify → /deploy
```

| Slash Command | Input | Output |
|---|---|---|
| `/define <feature>` | Feature description + optional images | `specs/[feature_name]/spec.md` |
| `/review specs/[name]/spec.md` | Path to spec | Spec Review Artifact; Status → `In Review` |
| `/architect specs/[name]/spec.md` | Path to **Approved** spec | `specs/[feature_name]/plan.md` |
| `/execute` | Reads `plan.md` automatically | Checked-off `plan.md`; Build Summary Artifact |
| `/verify <feature_name>` | Feature name | `specs/[feature_name]/verify-report.md` |
| `/deploy staging\|production` | Target env | `specs/[feature_name]/release.md` |

Critical gate rules:
- `/architect` **halts** if spec `Status` ≠ `Approved`. Always run `/review` first.
- `/deploy` **halts** if `verify-report.md` verdict ≠ `✅ RELEASE READY`.

---

## Key Architecture & Conventions

### Workflow Files (`.agent/workflows/*.md`) — Required Structure

```markdown
---
description: <one-line summary>
---

## User Input
$ARGUMENTS

## Instructions
1. ...
```
Never split a workflow across multiple files. Never omit the front-matter block.

### The Constitution (`memory/constitution.md`) — 8 Articles
Always read at the start of every workflow:
- **I** — Artifact Mandate: all work produces a Markdown file.
- **II** — Vision Verification: take screenshots for all UI work.
- **III** — Agent Independence: design tasks atomically; never block on another agent.
- **IV** — Code Health: modern syntax only (React Hooks, ES6+, Python 3.12+, async/await).
- **V** — Security First: never hardcode secrets; validate and sanitise all inputs; never log PII.
- **VI** — Test Coverage: ≥80% line/branch/function; every API endpoint needs an integration test.
- **VII** — Spec Traceability: every commit must include a Spec ID: `feat(SPEC-YYYY-MM-DD-slug): ...`.
- **VIII** — Rollback Safety: working tree must be clean before refactor; auto-rollback if tests fail.

### Tech Stack (`memory/tech-stack.md`)
A **placeholder template** — must be calibrated to the actual project before use.
- **Preferred**: `const`/`let`, `async/await`, React functional Hooks, named exports, Zod validation, `process.env.VAR` (validated at startup).
- **Forbidden**: `var`, raw `.then()` chains, `any` in TypeScript, hardcoded secrets, inline SQL, `console.log` in production, sync file I/O in request handlers.
- Build command and health-check endpoint are defined here under `## DevOps & Deployment`.

### Spec Template (`templates/spec.md`) — 7 Required Sections
All 7 sections are mandatory:

| # | Section | Key requirement |
|---|---|---|
| 1 | Overview | Problem + Solution in ≤4 sentences |
| 2 | Visual Requirements | All UI states (empty / loading / error) |
| 3 | Functional Requirements | Must Have / Should Have / Won't Have |
| 4 | Data Model | All new/modified entities and fields |
| 5 | API Contract | All new/modified endpoints with request/response shapes |
| 6 | Edge Cases | Minimum 4 items |
| 7 | Acceptance Criteria | Minimum 2 Given/When/Then; ≥1 must be a visual screenshot check |

Spec header metadata: `Status` (Draft → In Review → Approved), `Spec ID` (`SPEC-YYYY-MM-DD-slug`), `Author`, `Linked Plan`, `Created`, `Last Updated`.

### Runtime Artifacts (generated by agents; not committed by default)
```
specs/[feature_name]/spec.md              # /define
specs/[feature_name]/plan.md              # /architect
specs/[feature_name]/.progress            # /execute bookmark (deleted on completion)
specs/[feature_name]/verify-report.md     # /verify
specs/[feature_name]/release.md           # /deploy
specs/refactor-[date]/refactor-report.md  # /refactor
```

---

## Making Changes

| Change | Location | Rule |
|---|---|---|
| New workflow | `.agent/workflows/new-name.md` | Must have front-matter + `$ARGUMENTS` + numbered steps |
| Constitution update | `memory/constitution.md` | Keep `## Article N: Title` format; do not delete articles |
| Tech stack update | `memory/tech-stack.md` | Keep all 5 sections; replace `[e.g., ...]` placeholders |
| Spec template update | `templates/spec.md` | Never remove any of the 7 sections; preserve `- [ ]` syntax |
| README update | `README.md` | Keep workflow table in sync with `.agent/workflows/` files |

**Trust these instructions. Only search the repository if information here appears incomplete or incorrect.**