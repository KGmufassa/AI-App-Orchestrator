---
Command Name: modular-skill-generator.md
Description: Creates modular, production-grade skills from documentation by extracting intent, synthesizing workflows, patterns, decisions, constraints, and failures, embedding security and best practices, and routing execution through reference-linked, lightweight skill logic for agents
Agent: build
Subtask: true
---


# Modular Skill Generator

## PURPOSE
Compile documentation into a modular, production-grade skill system where:

- `skill.md` = routing + decision engine
- `/references` = execution intelligence
- Content is dynamically routed using intent (not format)
- Security, best practices, and execution context are enforced globally

---

## INPUT
- skill_name: string
- source_path: optional
- source_type: auto | local | context7 | hybrid
- min_relevance_score: 0.65
- max_chunks_per_category: 40

---

## OUTPUT STRUCTURE
```
/skills/{skill_name}
  skill.md

  /references
    fundamentals.md
    patterns.md
    anti-patterns.md
    workflows.md
    decision-frameworks.md
    constraints.md
    failure-modes.md

  metadata.json
```
---

## CORE PRINCIPLES

1. NEVER store raw documentation
2. ALWAYS synthesize into action-ready knowledge
3. ROUTE by intent, NOT by document type
4. EVERY entry must include execution context
5. Security + best practices are mandatory layers
6. skill.md contains routing ONLY

---

## EXECUTION PIPELINE

---

### 1. RESOLVE SOURCE
- IF source_type == auto:

  - IF source_path exists → local

  - ELSE → context7

- IF hybrid:
     → combine both

---

### 2. TARGETED INGESTION
**Retrieve ONLY:**
- actionable steps
- decisions
- examples
- errors
- limits
- configs

---

### 3. NORMALIZATION
- Deduplicate
- Merge overlaps
- preserve traceability

---

### 4. RELEVANCE FILTER

**score =
  actionability**
+ decision relevance
+ example presence
+ frequency

KEEP score >= min_relevance_score

---

## 5. CONTENT CHUNKING

**Break content into atomic units:**

- step
- command
- input/output
- decision statement
- error/failure
- constraint/limit
- explanation

---

## 6. INTENT EXTRACTION (CORE UPGRADE)

**ASSIGN PRIMARY INTENT FOR EACH CHUNK:**

- execute → user is trying to perform steps
- implement → user is applying a method or API
- decide → user must choose between options
- limit → describes system constraints
- fix → describes error or troubleshooting
- understand → explains concept
- avoid → warns against bad usage

ALLOW secondary intents if applicable

---

## 7. INTENT-BASED TRANSFORMATION

**MAP intents → categories:**

- execute → workflows  
- implement → patterns  
- decide → decision-frameworks  
-limit → constraints  
- fix → failure-modes  
- understand → fundamentals  
- avoid → anti-patterns  

---

## 8. CLUSTERING (CRITICAL)

**GROUP chunks by:**
- goal (deploy, run, scale)
- decision type (X vs Y)
- failure type
- constraint type

**MERGE:**
- similar workflows
- similar patterns
- similar failures

**OUTPUT:**
- ONE workflow per goal
- ONE pattern per method
- ONE failure per issue type

---

## 9. SYNTHESIS

**Transform grouped content into:**

- core steps
- variations
- tradeoffs
- fallback paths

**REMOVE:**
- redundancy
- non-actionable text

---

## 10. EXECUTION CONTEXT ENRICHMENT

**FOR EACH ENTRY ADD:**

- Preconditions
- Inputs / Outputs
- Dependencies
- State Impact (stateless/persistent)
- Idempotency Notes
- Signals to Check (logs/responses)
- Fallback Strategy

---

## 11. SECURITY + BEST PRACTICE INJECTION

### DETECTION

**IF involves:**
- user input
- API calls
- auth
- data handling
- environment variables

→ mark security-relevant

---

### INJECTION

**ADD:**

- Security Considerations
- Security Steps
- Security Risk
- Prevention

**ADD:**

- Recommended Default
- Best Practice Notes

---

### SEVERITY

**Assign:**
- low | medium | high | critical

---

## 12. FILE GENERATION

---
# Skill: {skill_name}

**File path:** `skill/{skill-name}/skill.md` (ROUTING ENGINE)

## Purpose

---

## Table of Capabilities

| Task | Decision | Go To |
|------|----------|-------|
| {{task}} | {{decision}} | references/{{file}}.md#{{anchor}} |

---

## How to Use

1. Identify goal  
2. Select decision  
3. Follow reference  
4. Execute  
5. If failure → failure-modes  

---

## Routing

- deploy → workflows  
- decide → decision-frameworks  
- debug → failure-modes  

---

## Output Requirements

- decision reasoning  
- reference link  
- execution steps  
- fallback  

---

### REFERENCES FILES (ENRICHED)

---
## Pattern: {name} {#anchor}

**File path:** `skill/{skill-name}/references/patterns.md`

- When to Use
- Preconditions
- Inputs / Outputs
- Steps
- Variations
- Dependencies
- State Impact
- Idempotency Notes
- Tradeoffs
- Recommended Default
- Security Considerations
Severity: {level}

---

## Workflow: {goal} {#anchor}

**File path:** `skill/{skill-name}/references/workflows.md`

- Preconditions
- Steps
- Variations
- Dependencies
- State Impact
- Failure Points
- Signals to Check
- Best Practice Notes
- Security Steps
- Fallback Strategy

---

## Decision: {name} {#anchor}

**File path:** `skill/{skill-name}/references/decision-frameworks.md`

-  Use X When
-  Use Y When
- Constraints
- Tradeoffs
- Cost Impact
- Time Impact
- Security Implications
- Default Recommendation
- Fallback Strategy

---

## Constraint: {name} {#anchor}

**File path:** `skill/{skill-name}/references/constraints.md`

- Description
- Impact
- Detection
- Workarounds
- Security Impact

---
## Failure: {issue} {#anchor}

**File path:** `skill/{skill-name}/references/failure-modes.md`

- Cause
- Symptoms
- Detection
- Signals to Check
- Fix
- Recovery Path
- Prevention
- Security Risk
Severity: {level}

---
## Anti-Pattern: {name}

**File path:** `skill/{skill-name}/references/anti-patterns.md`

- Description
- Why It Fails
- Consequences
- Correct Approach
- Security Risk
Severity: {level}
---

## Concept: {name}

**File path:** `skill/{skill-name}/references/fundamentals.md`

- Definition
- Why It Matters
- Key Properties

---

## 13. LINKING SYSTEM

- All entries MUST include anchors
- skill.md MUST link to references
- references MUST cross-link:
  - workflows ↔ patterns
  - failures ↔ constraints
  - decisions ↔ workflows

---

## 14. VALIDATION

**REJECT if:**

- missing workflows
- missing decisions
- missing failures
- missing constraints

**ENSURE:**

- no duplicates
- all entries actionable
- execution context present
- security present where applicable
- fallback logic present

---

## 15. METADATA
```
{
  "skill_name": "{skill_name}",
  "pattern_density": 0.0,
  "decision_clarity_score": 0.0,
  "security_coverage_score": 0.0,
  "reliability_score": 0.0
}
```
---

## SUCCESS CRITERIA

**Skill MUST:**

- be decision-driven
- be execution-ready
- be safe and secure
- handle retries and failures
- minimize ambiguity
