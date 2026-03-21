---
name: stack-optimizer
description: |
  Confirms frontend stack, validates backend compatibility, produces the final
  full-stack architecture, and generates per-technology best practice reference files
  using Context7 MCP.
---
  Covers:
  - Confirm frontend stack
  - Validate compatibility
  - Produce stack definition
  - Tech best practices generation (split into individual files)
---
Reference:
- Frontend PRD: /frontend/references/frontend-prd-draft.md
- Backend PRD: /backend/references/backend-prd-draft.md
---

# Stack Optimizer Skill

You are responsible for:
1. Confirming the frontend and backend stack
2. Generating best-practice reference files for EACH technology using Context7 MCP
3. Validating frontend ↔ backend compatibility

---

# Execution Rules (MANDATORY)

- ALWAYS validate stack before generating outputs  
- ALWAYS use Context7 MCP for best practices  
- NEVER combine multiple technologies into one reference file  
- ALWAYS normalize file names:
  - lowercase
  - remove special characters
  - replace spaces with hyphens  
- Ensure architecture is:
  - scalable
  - production-ready
  - aligned across stack  
- Output must include:
  - full stack definition
  - individual tech reference files  

---

# Step 1 — Confirm Frontend and Backend Stack

Display and confirm:

- Framework  
- Styling  
- Routing  
- State Management  

If unclear → ask ONE clarification question.

---

# Step 2 — Validate Compatibility

Validate:

- API style compatibility (REST, GraphQL, tRPC)  
- Deployment model (serverless vs stateful)  
- Authentication flow  
- Data fetching patterns  

### Output:
- Confirm compatibility OR  
- Flag mismatches  
- Suggest corrections  

---

# Step 3 — Produce Stack Definition

Generate:

# FULL STACK ARCHITECTURE

## Frontend Stack
- Framework:
- Styling:
- Routing:
- State Management:

---

## Backend Stack
- Runtime:
- Framework:
- Database:
- ORM:
- Authentication:

---

## Backend Architecture
- Controllers
- Services
- Repositories
- Models

---

## API Contract
[List endpoints]

---

## Deployment Strategy
[Infrastructure plan]

Save to:
`/docs/stack/stack.md`

---

# Step 4 — Parse Full Tech Stack

Combine:
- frontend_stack
- backend_choices

Extract individual technologies.

Example:
"Next.js, Tailwind, Node.js, Prisma, PostgreSQL"

→
- nextjs
- tailwindcss
- nodejs
- prisma
- postgresql

---

# Step 5 — Context7 MCP Research

For EACH technology:

Retrieve:
- Core best practices  
- Architecture patterns  
- Performance  
- Security  
- Scaling  
- Pitfalls  
- Ecosystem tools  

---

# Step 6 — Generate Individual Reference Files

For EACH technology:

Create file:

`/system/reference/{tech-name}-best-practices.md`

---

# File Template

# {TECH NAME} BEST PRACTICES

## Overview
[Short description]

---

## Core Best Practices
- ...

---

## Architecture Patterns
- ...

---

## Performance
- ...

---

## Security
- ...

---

## Scaling
- ...

---

## Common Pitfalls
- ...

---

## Recommended Tools / Ecosystem
- ...

---

## Integration Notes
- How it connects with other stack components

---

## Implementation Notes
- Setup and configuration tips

---

# Step 14 — Context Adaptation

If `context` is provided:

Adapt recommendations based on:
- scale
- real-time requirements
- deployment type
- performance constraints

---

# Step 15 — Validation

Ensure:
- One file per technology  
- Correct naming format  
- No duplication  
- All files are actionable  

---

# Final Output Behavior

- Save full stack architecture → `/system/reference/`
- Save stack definition → `/system/reference/stack.md`  
- Save individual best practice files → `/system/reference/`  
- Do NOT merge technologies into one file  

---

# Example Output Files

/system/reference/stack.md  
/system/reference/nextjs-best-practices.md  
/system/reference/nodejs-best-practices.md  
/system/reference/postgresql-best-practices.md  

---

# Behavior Summary

- Full-stack validation + optimization  
- Context-aware recommendations  
- Modular documentation system  
- Production-ready outputs  
- Fully compatible with agent pipelines  

---

# End of Skill
