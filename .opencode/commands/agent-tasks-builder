---
name: orchestrate
description: Analyze project documents and available skills, determine optimal execution strategy, and route the task via direct execution, subtask-skill, multi-skill chaining, or temporary agent creation.
agent: build
---

# /orchestrate

## Purpose

This command acts as the orchestration control layer.

It:

1. Reads user-defined documents.
2. Reads available skills.
3. Analyzes the requested task.
4. Determines the optimal execution strategy.
5. Executes via:
   - Direct skill
   - subtask-skill
   - Skill chaining
   - Temporary agent creation

It never performs the task directly unless explicitly required.

---

# Execution Flow

## Step 1 — Ingest Context

Read:

- PRDs
- stack-definition.md
- flow documents
- agent definitions
- available skills

Extract:

- Task intent
- Scope
- File impact
- Domain classification
- Dependencies
- Required output type

---

## Step 2 — Skill Inventory

List all available skills.

For each skill identify:

- Domain
- Inputs required
- Outputs generated
- Tool usage
- Side effects

Create capability map.

---

## Step 3 — Task Classification

Classify task as:

- UI/UX
- Backend
- Database
- Architecture
- Research
- Testing
- Multi-domain
- Documentation
- DevOps

Determine:

- Single-domain?
- Cross-domain?
- High-risk?
- Long-running?
- File-impact heavy?

---

## Step 4 — Routing Decision

### If existing skill fully satisfies task:
→ Execute that skill.

### If multiple skills required:
→ Chain skills.
→ Determine execution order.

### If no skill matches:
→ Create temporary bounded agent.

---

# Subtask vs Same Context Logic

Use `subtask-skill` when:

- Task is independent.
- Requires isolated reasoning.
- Risk of context pollution.
- Long-running.
- Heavy file modification.

Use same context when:

- Small task.
- Requires shared reasoning.
- Iterative refinement.
- Cross-skill dependency within same reasoning window.

If ambiguous:
Ask user.

---

# Temporary Agent Template

If required:

Create bounded agent:

Mission:
Scope:
Allowed Files:
Prohibited Files:
Tools Allowed:
Workflow Steps:
Validation Checklist:
Failure Protocol:

Agent must respect:
- stack-definition.md
- Governance rules
- File ownership matrix

---

# Conflict Detection

Before execution:

Check:

- Scope overlap
- Stack violations
- File ownership collision
- Skill redundancy
- Circular dependency

If conflict:
Pause and request clarification.

---

# Execution Plan Output

Before running:

Return:

Execution Plan:

1. Selected Skill(s)
2. Execution Mode (Subtask / Same Context)
3. Temporary Agent Created? (Yes/No)
4. Files Impacted
5. Validation Strategy
6. Risk Assessment

Require confirmation if:
- Cross-domain changes
- Stack modifications
- File-wide edits

---

# Constraints

NEVER:

- Execute blindly.
- Overwrite files silently.
- Combine unrelated skills.
- Bypass governance.
- Modify stack-definition without explicit approval.

ALWAYS:

- Prefer deterministic routing.
- Prefer specialized skill over general reasoning.
- Provide execution transparency.
- Maintain file ownership discipline.
