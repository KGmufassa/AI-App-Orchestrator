---
name: designing-ui-ux-prd
description: Ingests draft PRDs from selected paths and produces a structured UI/UX PRD with page-by-page layouts, button mappings, glyph suggestions, and interaction definitions. Use when locking frontend visual structure for an MVP. Asks UI/UX clarifying questions one at a time before proceeding.
compatibility: opencode
metadata:
  domain: frontend
  workflow: ui-ux-planning
  output: frontend-prd
---

# Designing UI/UX PRD

## Purpose

This skill converts draft PRDs into a fully structured UI/UX blueprint that defines:

- Required MVP pages
- Page-by-page layout
- Assigned buttons and functions
- Navigation logic
- Symbol glyph suggestions
- Interaction descriptions
- Final UI/UX PRD output written to `/frontend`

The goal is to lock one deterministic frontend visual direction before implementation.

---

# Core Rules

1. Never guess.
2. Ask UI/UX design clarifying questions one at a time.
3. Only ask UI/UX-related questions.
4. Do not proceed to page design until required design decisions are confirmed.
5. Always output structured documentation.

Allowed clarifying examples:
- What color theme is the web app?
- What type of navigation do you prefer? (sidebar, top nav, tabbed)
- Is the experience mobile-first or desktop-first?
- Is the design minimal, modern, enterprise, playful, etc.?

---

# Workflow

Copy this checklist and track progress:

UI/UX Design Progress:
- [ ] Step 1: Ingest draft PRD(s)
- [ ] Step 2: Ask clarifying UI/UX questions (one at a time)
- [ ] Step 3: Define MVP page count
- [ ] Step 4: Page-by-page structural breakdown
- [ ] Step 5: Define buttons and actions
- [ ] Step 6: Suggest symbol glyphs
- [ ] Step 7: Generate final UI/UX PRD draft
- [ ] Step 8: Write file to `/frontend/ui-ux-design/ui-ux-draft.md`

---

# Step 1 — Ingest Draft PRDs

- Read PRD files from provided paths.
- Extract:
  - Core features
  - User types
  - MVP scope
  - Functional constraints
  - Required flows

Do not design yet.

---

# Step 2 — Clarifying UI/UX Questions

Ask one question at a time.

Wait for user answer before asking the next.

Categories:

- Visual theme
- Navigation style
- Device priority
- User interaction style
- Accessibility level
- Branding requirements
- Layout density (compact vs spacious)
- Animation level (none, subtle, expressive)

---

# Step 3 — Determine MVP Page Count

Based on:
- Feature clustering
- User flows
- Logical separation of responsibilities

Output:


MVP Page Architecture:

Landing / Marketing

Authentication

Dashboard

Feature Page A

Feature Page B
...


Each page must have a purpose definition.

---

# Step 4 — Page-by-Page Breakdown

For each page define:

## Page Name

### Purpose
Why it exists.

### Layout Structure
- Header
- Navigation
- Main content zones
- Side panels
- Footer

### Sections
List each section clearly.

### State Variations
- Empty state
- Loading state
- Error state
- Success state

### Map Features to page

---

# Step 5 — Buttons and Function Assignments

For each page:

| Button Name | Location | Action | Backend Hook | State Change |
|------------|----------|--------|--------------|--------------|

Define:
- What it does
- Where it routes
- What state it changes
- If modal or redirect

No undefined buttons allowed.

---

# Step 6 — Symbol Glyph Suggestions

For applicable buttons suggest standard UI glyphs.

Use widely recognized conventions:

| Function | Suggested Glyph |
|----------|----------------|
| Add | plus (+) |
| Delete | trash can |
| Edit | pencil |
| Settings | gear |
| Notifications | bell |
| Search | magnifying glass |
| Back | left arrow |
| Upload | upward arrow |
| Download | downward arrow |

If branding is custom, ask before deciding.

---

# Step 7 — Generate Final UI/UX PRD Draft

Output structured document:

UI/UX PRD
Visual Identity
Navigation System
Page Architecture
Detailed Page Definitions
Component Library Overview
Interaction Rules
Accessibility Rules
Design Guardrails

All pages must be deterministic and implementation-ready.

---

# Step 8 — Write Output

Write file to:

`/frontend/ui-ux-design/ui-ux-draft.md`

If folder does not exist:
- Create it.

Confirm file path after writing.

---

# Constraints

NEVER:
- Assume color themes
- Assume device priority
- Merge pages without justification
- Skip accessibility consideration
- Proceed without clarifications

ALWAYS:
- Enforce one locked frontend visual direction
- Ensure reproducible layout
- Keep structure implementation-ready
