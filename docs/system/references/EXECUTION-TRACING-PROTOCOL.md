# FULL EXECUTION TRACING PROTOCOL

## PURPOSE
Provide complete visibility, traceability, and replay capability for all agent, subagent, and skill executions.

---

## CORE STRUCTURE

{
  "task_id": "",
  "execution_id": "",
  "parent_task_id": "",
  "status": "pending | running | completed | failed",
  "skill": "",
  "agent": "",
  "mode": "controlled | flexible",
  "start_time": "",
  "end_time": "",
  "duration_ms": 0,
  "input": {},
  "output": {},
  "error": null,
  "logs": [],
  "metrics": {},
  "trace": []
}

---

## TRACE ENTRY STRUCTURE

Each step in execution:

{
  "step_id": "",
  "skill": "",
  "input": {},
  "output": {},
  "status": "",
  "timestamp": ""
}

---

## RULES

1. Every execution MUST generate execution_id
2. Every step MUST be logged in trace[]
3. All timestamps MUST be recorded
4. Duration MUST be calculated
5. Logs MUST capture important decisions

---

## MULTI-SKILL PIPELINE

{
  "skill_bundle": [],
  "execution_order": [],
  "trace": [
    {
      "step_id": "1",
      "skill": "",
      "input": {},
      "output": {},
      "status": ""
    }
  ]
}

---

## DATA FLOW

Each step MUST:

1. receive previous output  
2. transform data  
3. pass structured output forward  

---

## PARALLEL EXECUTION TRACKING

{
  "parallel_group_id": "",
  "tasks": [
    {
      "task_id": "",
      "execution_id": ""
    }
  ]
}

---

## ERROR HANDLING

{
  "status": "failed",
  "error": {
    "type": "",
    "message": "",
    "step_id": "",
    "recoverable": true
  },
  "recovery_action": ""
}

---

## LOGGING SYSTEM

{
  "logs": [
    {
      "level": "info | warning | error",
      "message": "",
      "timestamp": ""
    }
  ]
}

---

## METRICS

{
  "metrics": {
    "execution_time_ms": 0,
    "steps_count": 0,
    "success_rate": 0
  }
}

---

## REPLAY CAPABILITY

To replay execution:

{
  "execution_id": "",
  "replay": true
}

RULE:
- system must re-run steps using trace[]

---

## AUDIT TRAIL

{
  "audit": {
    "created_by": "agent",
    "created_at": "",
    "version": ""
  }
}

---

## COMPLETION

{
  "status": "completed",
  "output": {},
  "metrics": {}
}

---

## END
