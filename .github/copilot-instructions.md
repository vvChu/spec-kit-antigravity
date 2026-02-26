# Copilot Instructions for spec-kit-antigravity

## Repository Summary

**spec-kit-antigravity** is an agent-first Specification & Orchestration Kit for **Google Antigravity** (Gemini 3). It is a pure Markdown/documentation toolkit — there is **no compiled code, no build system, and no test runner**. Its purpose is to provide reusable workflow prompts, templates, and governance rules that structure how AI agents (running inside the Antigravity IDE) plan, build, verify, and refactor features via Spec-Driven Development.

- **Type**: Documentation / Agent-Workflow Kit (no source code to compile)
- **Language**: Markdown only (no JavaScript, Python, or other compiled language)
- **Size**: ~10 KB, 10 files total
- **Default branch**: `main`
- **Forked from**: `waveupHQ/spec-kit-antigravity`

---

## Repository Layout

```
spec-kit-antigravity/
├── README.md                        # Project overview and quick-start guide
├── .agent/
│   └── workflows/                   # Antigravity slash-command workflow definitions
│       ├── define.md                # /define  — generate a feature spec
│       ├── architect.md             # /architect — generate an implementation plan
│       ├── execute.md               # /execute  — build from the plan
│       ├── verify.md                # /verify   — visual + logic QA
│       └── refactor.md             # /refactor — modernise legacy code
├── memory/
│   └── constitution.md              # Project-wide coding rules (the "constitution")
└── templates/
    ├── spec.md                      # Blank spec template (Visual + Functional + Data Model)
    └── tasks.md                     # Blank parallel-task template (Backend / Frontend / Integration)
```

> **Note**: There is no `.github/workflows/` directory — this repository has **no CI/CD pipeline** and no GitHub Actions. There are also no `package.json`, `Makefile`, `pyproject.toml`, or any other build files.

---

## Build, Test & Validation

Because the repository is pure Markdown, there is **no build step, no install step, and no test runner**. There are no commands to run to "build" or "test" this repository.

**Validation is manual:**
1. Ensure every `.md` file is valid Markdown (well-formed headings, lists, code blocks).
2. Ensure workflow files in `.agent/workflows/` keep the YAML front-matter block (`---` / `description:` / `---`) at the top.
3. Ensure `memory/constitution.md` headings follow the `## Article N: Title` convention.
4. Ensure template files in `templates/` use checkbox syntax (`- [ ]`) for actionable items.

There are no linting tools configured; a manual review of Markdown formatting is sufficient.

---

## Key Architecture & Conventions

### Workflow Files (`.agent/workflows/*.md`)
Each file defines one Antigravity slash-command. The structure is:
```
---
description: <one-line summary>
---

## User Input
$ARGUMENTS

## Instructions
1. ...
```
- `$ARGUMENTS` is the placeholder for text the user types after the slash command.
- Instructions are numbered steps; keep them concise.
- **Do not** add extra sections or split a workflow across multiple files.

### The Constitution (`memory/constitution.md`)
Governs all agent behaviour. Articles currently defined:
- **Article I** – Artifact Mandate: always write outputs to files, not chat.
- **Article II** – Vision Verification: take screenshots for UI work.
- **Article III** – Agent Independence: design tasks to run in parallel; never block.
- **Article IV** – Code Health: use modern patterns (React Hooks, ES6+, Python 3.12+); self-correct failing tests once before escalating.

When updating the constitution, always use `## Article N: Title` heading format and keep rules imperative and brief.

### Templates (`templates/`)
- `spec.md` — canonical spec structure: Overview → Visual Requirements → Functional Requirements → Data Model.
- `tasks.md` — parallel task breakdown: Backend group (🔴) → Frontend group (🔵) → Integration phase (🟢).

Workflow instructions reference these templates by convention; keep template structure stable.

### Generated Artifact Paths (convention)
When an agent runs a workflow, it writes output under `specs/`:
```
specs/[feature_name]/spec.md    # produced by /define
specs/[feature_name]/plan.md    # produced by /architect
```
The `specs/` directory does not exist in the repo by default; agents create it at runtime. Do **not** commit `specs/` output to the repo unless explicitly asked.

---

## Making Changes

- **Adding a new workflow**: Create a new `.md` file in `.agent/workflows/` following the front-matter + `$ARGUMENTS` + numbered-steps structure.
- **Editing the constitution**: Add or modify articles in `memory/constitution.md` using the existing heading format. Do not remove existing articles without explicit instruction.
- **Editing templates**: Preserve the checkbox (`- [ ]`) format so Antigravity can render them as interactive task lists.
- **README changes**: Keep the workflow table in `## ⚡️ Quick Start` in sync with the actual files in `.agent/workflows/`.

Trust these instructions. Only search the repository if the information above appears incomplete or incorrect.