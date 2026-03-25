---
name: defining-tech-stack
description: Ingests a draft MVP PRD and frontend blueprint to determine and confirm the appropriate backend and supporting technologies. Asks qualifying questions one at a time to remove ambiguity before outputting a finalized stack-definition.md file.
compatibility: opencode
metadata:
  domain: architecture
  workflow: stack-selection
  output: stack-definition
---

# Defining Tech Stack

## Purpose

This skill determines the correct technology stack for a project based on:

- Draft MVP PRD
- Frontend blueprint
- Existing frontend decisions (if any)
- Functional and non-functional requirements

It asks qualifying architectural questions one at a time.

It outputs a finalized:

stack-definition.md

This file becomes the source of truth for downstream stack research.

---

# Core Principles

1. Never guess stack decisions.
2. Ask one clarifying architectural question at a time.
3. Respect existing frontend constraints.
4. Choose backend technologies based on requirements, not trends.
5. Document reasoning clearly.
6. Do not output stack until ambiguity is resolved.

---

# Step 1 — Ingest Inputs

Read:

- Draft MVP PRD
- Draft frontend blueprint

Extract:

- Frontend framework
- Expected traffic level
- Real-time requirements
- Auth needs
- Database needs
- File storage needs
- Payment integration
- AI integration
- Third-party APIs
- Deployment constraints
- Scalability expectations
- Compliance requirements (HIPAA, SOC2, etc.)

If frontend is already defined:
Lock it.

---

# Step 2 — Constraint Detection

Detect:

- Does frontend require SSR?
- Is SEO required?
- Is real-time communication needed?
- Is heavy compute expected?
- Is large data storage expected?
- Is multi-tenancy required?
- Is role-based access required?
- Is serverless acceptable?
- Is long-running background job required?

Do not recommend backend yet.

---

# Step 3 — Clarifying Questions

Ask one at a time.

Examples:

- Is this app expected to handle real-time updates?
- What is your expected concurrent user count at launch?
- Do you require relational data or flexible schema?
- Will you need background job processing?
- Is vendor lock-in acceptable?
- Do you need strict type safety across frontend and backend?
- Is this a monolith or microservices goal?
- Are you optimizing for speed of development or long-term scalability?

Do not proceed until critical ambiguity is resolved.

---

# Step 4 — Stack Decision Engine

Based on answers, determine:

## Backend Framework
Examples:
- Node.js (Express / Fastify)
- NestJS
- Django
- Rails
- Go (Fiber / Gin)
- Serverless (AWS Lambda / Vercel Functions)

## Database
Examples:
- PostgreSQL
- MySQL
- MongoDB
- DynamoDB
- Supabase
- PlanetScale

## ORM
- Prisma
- Drizzle
- TypeORM
- Sequelize

## Auth
- Clerk
- Auth.js
- Firebase Auth
- Custom JWT
- OAuth providers

## Hosting
- Vercel
- AWS
- GCP
- Fly.io
- Railway
- Render

## DevOps
- Docker
- CI/CD provider
- Monorepo vs Polyrepo

## Testing
- Unit framework
- E2E framework
- API testing

Each choice must be justified by requirement.

---

# Step 5 — Conflict Validation

Before output:

Ensure:

- Backend aligns with frontend.
- ORM aligns with database.
- Hosting aligns with architecture.
- Auth integrates cleanly.
- Real-time needs are supported.
- Background job requirements are supported.

If mismatch detected:
Explain and re-ask clarifying question.

---

# Step 6 — Output File

Create:

stack-definition.md

Format:

# Stack Definition

## Frontend
- Framework:
- State Management:
- Routing:
- Styling:
- Rationale:

## Backend
- Framework:
- Architecture Pattern:
- Rationale:

## Database
- Type:
- Hosting:
- Rationale:

## Authentication
- Provider:
- Rationale:

## Hosting / Deployment
- Frontend Hosting:
- Backend Hosting:
- Rationale:

## DevOps
- Containerization:
- CI/CD:
- Repo Structure:

## Testing
- Unit:
- Integration:
- E2E:

## Observability
- Logging:
- Monitoring:
- Error Tracking:

## Scalability Strategy

## Known Tradeoffs

## Future Upgrade Path

All sections must be filled.
No empty headings allowed.

---

# Constraints

NEVER:

- Recommend technology without justification.
- Select trendy stack without requirement alignment.
- Skip scalability discussion.
- Skip security considerations.
- Ignore frontend constraints.
- Assume traffic scale.

ALWAYS:

- Choose based on constraints.
- Explain reasoning.
- Ensure full-stack compatibility.
- Keep structure production-ready.

---

# Completion Output

Return:

1. Stack confirmed
2. Key architectural decisions
3. Major tradeoffs
4. File path written
5. Any unresolved future decisions
