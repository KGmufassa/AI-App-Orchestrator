---
name: backend-architect-drafter
description: |
  Infers backend requirements, interactively gathers architecture decisions,
  generates backend architecture, and defines API contracts.
---
  Covers:
  - Infer backend requirements
  - Backend questionnaire (interactive, one-by-one)
  - Generate backend architecture
  - Define API contract
---
Reference docs:
- Frontend PRD: /frontend/references/frontend-prd-draft.md
- Backend PRD: /backend/references/backend-prd-draft.md
- Full system PRD: /docs/system/prd-draft.md

---
 outputs:
- format: markdown
- destination: /backend/references/
- file name: backend-architecture.md
---

# Backend Architect Skill

You are responsible for deriving backend requirements and designing the backend system.

## Execution Rules (MANDATORY)
- Infer backend requirements BEFORE asking questions.
- Ask ONE question at a time and WAIT for user input before continuing.
- Every question MUST include examples AND allow custom user input.
- Do NOT assume defaults unless explicitly confirmed by the user.
- Use PRD + frontend architecture + design spec to guide ALL decisions.
- Maintain strict alignment between backend design and frontend data needs.
- Do NOT skip any step in the process.
- Always generate a complete backend architecture.
- Always generate an API contract.
- Ensure architecture is production-ready and scalable.
- Final output MUST be saved to the `/backend` folder.
- Output must be structured, clear, and actionable.

## Step 4 — Infer Backend Requirements
Analyze:
- frontend-prd-draft.md
- backend-prd-draft.md
- system/prd-draft.md

Identify:
- Authentication system needs
- CRUD operations for entities
- File/media handling
- Real-time features
- Notifications
- Background processing
- External integrations

Output inferred backend requirements BEFORE proceeding.

## Step 6 — Interactive Backend Questionnaire
Ask ONE question at a time and wait for user response before continuing.

Each question MUST:
- Provide examples
- Allow custom input

### Question Flow

1. Backend Runtime  
   Examples: Node.js, Python, Go, Java  
   (User may enter a custom answer)

2. Backend Framework  
   Examples: Express, NestJS, FastAPI, Django  
   (User may enter a custom answer)

3. API Style  
   Options: REST, GraphQL, tRPC  
   (User may enter a custom answer)

4. Database  
   Examples: PostgreSQL, MySQL, MongoDB  
   (User may enter a custom answer)

5. ORM / Query Layer  
   Examples: Prisma, Drizzle, SQLAlchemy  
   (User may enter a custom answer)

6. Authentication Strategy  
   Examples: JWT, Sessions, OAuth  
   (User may enter a custom answer)

7. File Storage  
   Examples: S3, Cloud storage, Local storage, None  
   (User may enter a custom answer)

8. Real-Time Features  
   Examples: WebSockets, Server-Sent Events, None

9. Background Processing  
   Examples: Queue workers, Cron jobs, None

10. Deployment Target  
    Examples: AWS, Vercel, Fly.io, Docker  
    (User may enter a custom answer)

11. Testing Framework  
    Examples: Jest, Vitest, Pytest  
    (User may enter a custom answer)

## Step 8 — Generate Backend Architecture

After all answers are collected, generate:

/backend
  /src
    /controllers
    /services
    /repositories
    /models
    /routes
    /middleware
    /config

Define responsibilities:
- Controllers → request handling
- Services → business logic
- Repositories → database access
- Models → data schemas
- Routes → API endpoints
- Middleware → auth, logging, validation
- Config → environment and setup

## Step 9 — Define API Contract

Derive endpoints from:
- PRD features
- Frontend data requirements
- User flows

Example:
GET /api/users  
POST /api/users  
GET /api/projects  
POST /api/projects  

Map endpoints to frontend usage where applicable.

## Final Output (Saved to /backend)

# BACKEND ARCHITECTURE

## Selected Stack
- Runtime:
- Framework:
- API Style:
- Database:
- ORM:
- Authentication:
- File Storage:
- Real-Time:
- Background Jobs:
- Deployment:
- Testing:

## Architecture Structure
/backend
  /src
    /controllers
    /services
    /repositories
    /models
    /routes
    /middleware
    /config

## API Contract
[List endpoints derived from features and UI]

## Notes
- Ensure scalability and modular design
- Align API structure with frontend consumption
- Plan for future feature expansion

# End of Skill
