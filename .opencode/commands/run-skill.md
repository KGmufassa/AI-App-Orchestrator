---
name: execute-skill
description: |
  Dynamically executes a specified skill as a subtask. Acts as a universal dispatcher
  that allows agents to invoke any registered skill with arguments in a controlled,
  validated manner.
agent: build
subtask: true
---
  Use when:
  - An agent needs to call a skill dynamically
  - Building orchestrator pipelines
  - Running subtask-based workflows
  - Enabling modular agent execution
---

# Execute Skill Command (Dynamic Dispatcher)

This command dynamically routes execution to a specified skill.

---

# Inputs

- skill (string, required)  
- args (object, optional)

Example:
```json
{
  "skill": "systematic-debugger",
  "args": {
    "error": "test failure"
  }
}
```

# Execution Rules (MANDATORY)
- MUST validate skill before execution
- MUST pass args directly to skill
- MUST run skill as subtask
- MUST NOT contain business logic
- MUST return raw skill output
- MUST fail safely on invalid input

# Step 1 — Validate Input

### IF `skill` is missing:
→ STOP
→ Output:
```
Error: No skill provided
```
# Step 2 — Skill Registry Validation

**Define allowed skills:**

- Mapping-Ux-flows
- Test-driven-development
- Wireframe-generator
- backend-architecture-drafter
- debugging-wizard
- defined-best-practices
- defining-tech-stack
- dynamic-prd-drafter
- dynamic-wireframe-mapper
- frontend-architecture
- security-review
- swift-expert
- systematic-debugger
- ui-ux-design-draft
- using-git-worktrees
- worktree-manager

**IF `skill` NOT in registry:**
→ STOP
→ Output:
```
Error: Invalid skill `"<skill>"`
```
# Step 3 — Normalize Args

**IF `args` is missing:**
→ set `args = {}`

# Step 4 — Execute Skill
`runSkill(skill, args)`

# Step 5 — Return Output

Return result exactly as produced by the skill.

## Error Handling
### Missing Skill
- Stop execution
### Invalid Skill
- Reject execution
### Skill Failure
- Pass error through (do NOT modify)

## Behavior Summary
- Universal skill dispatcher
- Enables dynamic orchestration
- Supports subagent-like execution
- Keeps system modular and scalable
- No embedded logic (pure routing layer)

Example Usage
```
runCommand("execute-skill", {
  skill: "test-driven-development",
  args: {
    feature: "user login"
  }
})
```

