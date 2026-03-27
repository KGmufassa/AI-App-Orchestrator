---
name: agent-task-builder
description: Ingest a task list or implementation plan, analyze available skills, construct the optimal bounded agent, and execute assigned skills via run-subtask-skill when subtask execution is required.
---

# /construct-agent

## Purpose

This command:

1. Reads a task list or implementation plan.
2. Scans available skills.
3. Clusters tasks by domain.
4. Constructs the optimal bounded agent configuration.
5. Assigns skills.
6. Determines execution mode.
7. If subtask execution is required, invokes run-subtask-skill.md.
8. Returns deterministic execution plan.

This command does NOT directly execute skills.
It delegates execution through run-subtask-skill when required.

---

# Step 1 — Ingest Task Source

Read:

- tasks/*
- implementation lists
- user-provided checklist
- structured plan

Extract:

- Task objectives
- File impact zones
- Required outputs
- Domain classification
- Dependency chains

---

# Step 2 — Domain Clustering

Group tasks:

- UI/UX
- Backend
- Database
- Architecture
- Testing
- DevOps
- Documentation

If single-domain → Single agent.
If multi-domain → Multi-agent plan.

---

# Step 3 — Skill Mapping

Scan available skills.

For each skill identify:

- Domain alignment
- Required inputs
- Output type
- Tool usage
- File scope

Create skill-to-task assignment matrix.

---

# Step 4 — Agent Construction

Generate agent:

# Agent: [Generated Name]

## Mission
Clear objective.

## Scope
Allowed directories:
Prohibited directories:

## Assigned Skills
List of skills.

## Workflow
Ordered execution plan.

## Validation Checklist
Pre-output verification.

## Execution Mode
Subtask / Same Context

---

# Step 5 — Execution Mode Decision

Use Subtask Mode when:

- Heavy file modifications
- Multi-step skill logic
- Isolation required
- Cross-domain risk
- Context overflow risk

When Subtask Mode selected:

DO NOT execute skill directly.

Instead:

Invoke:

run-subtask-skill.md

With:

- skill name
- task description
- scoped instructions
- file boundaries
- validation checklist

---

# Subtask Invocation Format

When calling run-subtask-skill:

Provide:

Skill:
Task:
Scope:
Expected Output:
Validation Requirements:

Never omit scope.
Never omit validation requirements.

---

# Step 6 — Conflict Validation

Before execution:

Check:

- Scope overlap
- Duplicate file ownership
- Stack-definition violations
- Circular dependencies
- Skill redundancy

If conflict detected:
Pause and request clarification.

---

# Step 7 — Output Plan

Return:

## Agent Construction Plan

1. Agent Name
2. Tasks Assigned
3. Skills Used
4. Execution Mode
5. Files Impacted
6. run-subtask-skill invoked? (Yes/No)
7. Risk Assessment

Require confirmation if:
- Cross-domain impact
- Stack changes
- Broad file modification

---

# Hard Constraints

NEVER:

- Execute skills directly when subtask required.
- Modify files outside defined scope.
- Chain skills without order definition.
- Overwrite stack-definition implicitly.
- Bypass run-subtask-skill for isolated tasks.

ALWAYS:

- Delegate subtask execution properly.
- Maintain bounded agent scope.
- Provide deterministic execution plan.
- Respect stack-definition.md.
