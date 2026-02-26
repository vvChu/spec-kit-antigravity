# Feature: [Name]

> **Status**: Draft
> **Spec ID**: SPEC-[YYYY-MM-DD]-[feature-slug]
> **Author**: [your-github-handle]
> **Linked Plan**: `specs/[feature_name]/plan.md`
> **Created**: [YYYY-MM-DD]
> **Last Updated**: [YYYY-MM-DD]

---

## 1. Overview
*What are we building and why? Describe the problem (1–2 sentences) and the proposed solution (1–2 sentences).*

**Problem**: ...
**Solution**: ...

---

## 2. Visual Requirements (Vision)
*Describe the UI/UX derived from uploaded mockups. If no mockup is provided, describe the expected UI in detail. Cover all states.*

- [ ] Component A: [description, dimensions, colour, behaviour]
- [ ] Component B: [description]
- [ ] Layout: [grid / flex / responsive breakpoints]
- [ ] Empty state: [what the user sees when there is no data]
- [ ] Loading state: [skeleton / spinner / etc.]
- [ ] Error state: [inline error / toast / modal]

---

## 3. Functional Requirements

### Must Have
- [ ] User can...
- [ ] System must...

### Should Have
- [ ] ...

### Won't Have (this iteration)
- [ ] ...

---

## 4. Data Model
*Define new or modified entities. Mark as `[N/A]` if no data model changes are required.*

```
Entity: [Name]
Fields:
  - id:         UUID (primary key, auto-generated)
  - created_at: DateTime (auto)
  - updated_at: DateTime (auto)
  - [field]:    [type] — [description / constraints]
```

---

## 5. API Contract
*List all new or modified endpoints. Mark as `[N/A]` if no API changes are required.*

```
[METHOD] /api/[endpoint]

Request Headers:
  Authorization: Bearer <token>

Request Body:
  {
    "[field]": "[type]"
  }

Response 200:
  {
    "[field]": "[type]"
  }

Response 4XX:
  {
    "error": "[message]"
  }
```

---

## 6. Edge Cases
*List at least 4 edge cases that the implementation must handle.*

1. [Edge case description]
2. [Edge case description]
3. [Edge case description]
4. [Edge case description]

---

## 7. Acceptance Criteria
*At least 2 Given/When/Then criteria. At least 1 must be a visual screenshot check.*

**AC-01**
- **Given**: ...
- **When**: ...
- **Then**: ...

**AC-02 (Visual)**
- **Given**: ...
- **When**: ...
- **Then**: Screenshot matches the design in Section 2.