---
name: construct-agent
description: Ingest a task list or implementation plan, analyze available skills, and construct a bounded agent configuration best suited to execute the current workload.
---

# /construct-agent

## Purpose

This command analyzes a task list and dynamically constructs the most appropriate agent configuration to execute those tasks.

It:

1. Reads task list or implementation list.
2. Scans available skills.
3. Clusters tasks by domain.
4. Determines if one agent or multiple agents are required.
5. Assigns relevant skills.
6. Defines scope boundaries.
7. Determines execution mode (subtask or same context).
8. Outputs agent definition and execution plan.

It does NOT execute tasks automatically unless explicitly confirmed.

---

# Step 1 — Ingest Task List

Read:

- tasks/*
- implementation list
- provided checklist
- bullet-based plan

Extract:

- Domain of each task
- Files impacted
- Required outputs
- Complexity level
- Dependencies between tasks

---

# Step 2 — Domain Clustering

Group tasks into domains:

- UI/UX
- Backend
- Database
- Architecture
- Testing
- DevOps
- Documentation
- Multi-domain

If all tasks fall into one domain:
→ Single agent.

If tasks span multiple domains:
→ Multi-agent configuration.

---

# Step 3 — Skill Scan

List all available skills.

For each skill determine:

- Domain alignment
- Input compatibility
- Output type
- File scope
- Tool requirements

Create skill-to-task mapping matrix.

---

# Step 4 — Agent Construction Logic

If existing skill directly covers task cluster:
→ Use that skill as core agent behavior.

If multiple skills required:
→ Compose agent with skill chaining.

If no skill matches:
→ Create temporary bounded agent with explicit workflow.

---

# Step 5 — Agent Definition Template

Generated Agent must include:

# Agent: [Generated Name]

## Mission
Concise task objective.

## Scope
Allowed directories:
Prohibited directories:

## Assigned Skills
- Skill A
- Skill B

## Tools Allowed
Explicitly inherited from assigned skills.

## Workflow
Deterministic sequence of steps.

## Validation Checklist
Pre-output checks.

## Execution Mode
Subtask / Same Context

## Dependencies
Which tasks must complete first.

---

# Step 6 — Execution Mode Decision

Use Subtask if:

- Heavy file modifications
- Isolated domain
- Large reasoning workload
- Risk of context overflow

Use Same Context if:

- Small batch
- Iterative refinement
- Shared reasoning required

If unclear:
Ask user.

---

# Step 7 — Conflict Detection

Before confirming:

Check:

- Scope overlap
- Duplicate ownership
- Skill conflicts
- Stack-definition violations
- Circular task dependencies

If conflict:
Pause and clarify.

---

# Step 8 — Output Plan

Return:

## Agent Construction Plan

1. Agent Name
2. Tasks Assigned
3. Skills Used
4. Execution Mode
5. Files Impacted
6. Validation Layer
7. Risks Identified

Await confirmation before execution.

---

# Constraints

NEVER:

- Execute tasks without plan confirmation.
- Create agent without scope boundary.
- Assign overlapping file ownership.
- Use skills outside declared domain.
- Modify stack-definition implicitly.

ALWAYS:

- Prefer specialization.
- Keep agent bounded.
- Respect stack-definition.md.
- Produce deterministic execution plan.
