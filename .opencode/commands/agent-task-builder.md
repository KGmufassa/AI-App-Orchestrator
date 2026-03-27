
## Description
Analyze a list of tasks or implementation steps, evaluate available skills, and construct an optimized agent (or multi-agent system) to execute the tasks fully. The command determines execution strategy (inline vs subagent), builds agent configuration, and routes tasks using a hybrid controlled/uncontrolled subagent model.

---
# Agent Task Builder

## Inputs

### Required
- Task list OR implementation plan

### Optional
- Available skills registry
- User preferences:
```json
{
  "speed_vs_accuracy": "balanced | fast | high_accuracy",
  "parallelism": true,
  "execution_mode": "auto | controlled | flexible"
}
```
### Core Systems Used
- rule-engine-template.md → decision making
- communication-protocol-template.md → agent communication
- run-subtask-skill.md → controlled subagent execution

# Execution Pipeline
## STEP 1: INGEST & NORMALIZE INPUT
- Convert input into structured task list
- Ensure atomic granularity
```
{
  "task_id": "",
  "description": ""
}
```
## STEP 2: TASK DECOMPOSITION
Break tasks into smallest executable units.

**For each task identify:**

- dependencies
- required outputs
- domain (frontend/backend/db/etc.)

## STEP 3: TASK CLASSIFICATION (RULE ENGINE)

**For each task determine:**
```
{
  "type": "analysis | implementation | validation | orchestration",
  "complexity": "low | medium | high",
  "coupling": "tight | loose",
  "parallelizable": true,
  "dependencies": []
}
```
## STEP 4: SKILL MAPPING
- Match tasks → available skills
- Rank:
  - exact match
  - partial match
  - fallback (inline)
```
{
  "task_id": "",
  "skill": "",
  "confidence": "high | medium | low"
}
```
## STEP 5: EXECUTION STRATEGY DECISION

**Determine execution type:**

**Inline Execution**
- low complexity
- tightly coupled
- quick operations

**Subagent Execution**
- high complexity
- parallelizable
- isolated work

**Multi-Subagent Execution**
- large system tasks
- decomposable subtasks

## STEP 6: EXECUTION MODE DECISION (CRITICAL)

**Each subagent task must be labeled:**
```
{
  "mode": "controlled | flexible"
}
```
**Controlled Mode**

Use when:
  - deterministic output required
  - structured pipelines
  - repeatable builds

**Flexible Mode**

Use when:
  - exploration needed
  - research tasks
  - loosely defined outputs

## STEP 7: AGENT TYPE SELECTION
| Task Type |	Agent |
|-----------|-------|
| Planning | Plan |
| Implementation |	Build |
| Research	| Explore |
| Complex multi-step |	General |

## STEP 8: BUILD EXECUTION GRAPH

Construct:
```
{
  "execution_plan": [
    {
      "task_id": "",
      "execution": "inline | subagent",
      "mode": "controlled | flexible",
      "skill": "",
      "dependencies": []
    }
  ]
}
```
## STEP 9: AGENT CONFIG GENERATION

Create primary agent:
```
{
  "name": "generated-agent",
  "mode": "primary",
  "model": "opencode/gpt-5.1-codex",
  "permissions": {
    "edit": "allow",
    "bash": "allow"
  },
  "max_steps": 25
}
```
## STEP 10: SUBAGENT GENERATION

If required, generate subagents:
```
{
  "name": "auth-subagent",
  "mode": "subagent",
  "permissions": {
    "edit": "allow"
  }
}
```
## STEP 11: EXECUTION ROUTING ENGINE

**For each task:**

**CASE 1:INLINE**
- Execute directly in current context
- Maintain shared memory

**CASE 2: SUBAGENT (CONTROLLED)**
Invoke:
`run-subtask-skill.md`

With:
```
{
  "skill": "",
  "input": {},
  "context": "isolated"
}
```
**CASE 3: SUBAGENT (FLEXIBLE)**

Invoke subagent naturally:

`@subagent-name perform task`

## STEP 12: COMMUNICATION PROTOCOL ENFORCEMENT

All task transfers must follow:
```
{
  "sender": "",
  "receiver": "",
  "task_id": "",
  "instructions": "",
  "context": {},
  "expected_output": ""
}
```
## STEP 13: PARALLEL EXECUTION HANDLING

If tasks are parallelizable:
```
{
  "parallel_tasks": []
}
```
Execute simultaneously using subagents.

## STEP 14: ERROR HANDLING

If failure occurs:
```
{
  "status": "failed",
  "retry": true,
  "fallback": "inline | alternate skill"
}
```
## STEP 15: FINAL OUTPUT

Return:
```
{
  "agent_config": {},
  "execution_plan": [],
  "subagents": [],
  "task_routing": {},
  "summary": ""
}
```
### Behavior Rules
- Prefer subagents for high complexity tasks
- Avoid context overload
- Maximize safe parallel execution
- Use controlled mode for deterministic pipelines
- Use flexible mode for exploration
### Example Usage
```
agent-task-builder:
- Build authentication system
- Create database schema
- Build dashboard UI
- Add API routes
```
### Example Output (Simplified)
```
{
  "execution_plan": [
    {
      "task": "Create database schema",
      "execution": "subagent",
      "mode": "controlled",
      "skill": "db-schema-skill"
    },
    {
      "task": "Build auth system",
      "execution": "subagent",
      "mode": "controlled",
      "skill": "auth-module-skill"
    },
    {
      "task": "Build dashboard UI",
      "execution": "inline"
    }
  ]
}
```
#### Notes
- Uses rule-engine-template.md for all decisions
- Uses communication-protocol-template.md for all agent interactions
- Uses run-subtask-skill.md for controlled execution
- Supports multi-agent orchestration
- Designed for deterministic + scalable agent generation
