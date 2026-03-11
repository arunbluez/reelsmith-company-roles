# Tools -- CTO

## Paperclip API

Primary coordination tool. Used for task management, delegation, approvals, code review routing, and agent communication.

- Task CRUD, checkout, status updates
- Issue creation with parentId and goalId for subtask delegation
- Approval submission (production deployments, architectural changes)
- Agent queries for developer and testing status

## MCP Servers

### GitHub MCP
- **Purpose**: PR creation, code review, branch management, issue tracking
- **Transport**: HTTP
- **Repos**: `reelsmith-app` (monorepo), `reelsmith-waitlist`, `reelsmith-docs` (planned)
- **Notes**: All PRs target a development branch. Main branch is protected. Merge to main = deployment.

### Playwright Browser (Headless)
- **Purpose**: End-to-end testing for critical user flows (delegated to Testing Manager/Testers)
- **Transport**: stdio
- **Notes**: Used sparingly. API-level testing is preferred. Browser tests only for: auth flow, project creation wizard, scene generation trigger, video export download.

## Skills

### Assigned to CTO

| Skill | Purpose |
|-------|---------|
| `para-memory-files` | Memory management, daily notes, knowledge graph, planning |
| `paperclip` | Paperclip API coordination |
| `code-review` | Structured code review against architectural standards |
| `epic-task-breakdown` | PRD → atomic task decomposition |

### Assigned to Reports (for reference)

| Agent | Model | Key Skills |
|-------|-------|------------|
| Program Manager | Claude | `sprint-planner` (task breakdown, dependency mapping, assignment), `prd-reader` (PRD parsing and acceptance criteria extraction) |
| Sr. Fullstack Developer | Claude | `claude-code` (full-stack implementation), `drizzle-orm` (database operations), `nextjs-14` (frontend patterns), `hono-api` (backend patterns) |
| Sr. Frontend Developer | Gemini | `glassmorphism-design-system` (design tokens, gradients, glass-frost), `nextjs-14-ui` (component polish), `tailwind-advanced` (responsive, animation), `react-flow-styling` (canvas node visual refinement) |
| Testing Manager | Claude | `test-orchestrator` (test case decomposition, tester lifecycle management, result compilation) |
| Tester 1/2 (ephemeral) | Claude | `atomic-tester` (single-flow test execution, evidence capture, pass/fail reporting) |
| Docs Writer | Claude | `technical-docs` (feature documentation from code and PRDs), `obsidian-markdown` (vault-compatible output) |

## ReelSmith Vault (Obsidian)

Shared knowledge base repo: `reelsmith-vault`. Connected to Obsidian for Board browsing.

- **Your section**: `vault/cto/` — sprint logs, architectural decisions, epic status, code review notes
- **Shared section**: `vault/shared/` — cross-team docs, company decisions
- Write in Obsidian-compatible markdown: `[[wikilinks]]`, YAML frontmatter, standard heading hierarchy.
- The vault is for durable documentation. `para-memory-files` is for working memory.

### Vault Structure (CTO)
```
reelsmith-vault/
├── cto/
│   ├── decisions/           # Architectural decision records
│   ├── sprint-log.md        # Running sprint progress
│   ├── epic-status.md       # Board-facing epic tracker
│   └── code-review-notes/   # Per-PR review summaries
├── dev/
│   ├── fullstack/           # Fullstack Dev's working notes
│   └── frontend/            # Frontend Dev's working notes
├── testing/
│   └── test-reports/        # Compiled test results
├── docs/
│   └── features/            # Published feature documentation
└── shared/
    └── ...                  # Cross-team artifacts
```

## Technical Stack Reference

Quick reference for task creation and code review. Full details in the PRDs.

### Monorepo Structure
```
reelsmith-app/
├── apps/
│   └── web/                  # Next.js 14 frontend
│       ├── app/              # App Router pages
│       ├── components/       # React components
│       └── lib/              # Client utilities
├── packages/
│   ├── api/                  # Hono backend
│   │   ├── routes/           # API route handlers
│   │   ├── services/         # Business logic
│   │   └── db/               # Drizzle schema + migrations
│   ├── shared/               # Shared types, constants, validation
│   └── ui/                   # Shared UI components
└── turbo.json                # Turborepo config
```

### Database (Drizzle ORM on Neon)
- Schema defined in `packages/api/db/schema/`
- Migrations via `pnpm db:generate` → `pnpm db:migrate`
- Key tables: projects, videos, scenes, references, generated_assets, users, credits, transactions
- Always use Drizzle query builder. No raw SQL unless absolutely necessary.

### API Pattern (Hono)
- Routes in `packages/api/routes/`
- Auth middleware via Better Auth
- Validation via Zod schemas (shared with frontend)
- Error handling via consistent error response format

### Frontend Pattern (Next.js 14)
- App Router with server components where possible
- Client components for interactive UI (scene list, canvas, chat)
- React Flow for node editor / canvas view
- Glassmorphism design tokens in Tailwind config
- Right-sheet overlay pattern for panels (scene details, chat, settings)

### AI Integration (WaveSpeed.ai)
- 165 models across Image, Video, Voice, Avatar categories
- 4 tiers: Ultra, Premium, Standard, Budget + Edit tier for overrides
- API integration in `packages/api/services/wavespeed/`
- Job queue for async generation (BullMQ or similar)
- WebSocket for real-time progress updates

### Deployment
- Frontend + Backend: Railway.app
- Database: Neon DB (serverless Postgres)
- File Storage: Cloudflare R2
- Auth: Better Auth (self-hosted)

## PRD Location

All epic PRDs are in the project knowledge base. Always search project knowledge before creating tasks for a new epic. Key documents:

- `1-project-initialization.md` through `12-node-editor-preview-v3.md`
- `mvp-scope.md` -- overall scope and feature priority
- `frontend-design.md` -- UI/UX specifications and glassmorphism design system (critical for Frontend Developer task briefs)
- `reelsmith-workflow-documentation.md` -- end-to-end workflow reference

Completed feature documentation lives in `reelsmith-vault/docs/features/`.

## Notes

- Tools listed here are current as of agent creation. Update this file as new MCP servers or skills are added.
- If GitHub MCP authentication fails, log the error and flag to the board. Do not attempt workarounds.
- Developers should have their own GitHub MCP connections for direct code interaction. The CTO's GitHub access is for review and oversight.
