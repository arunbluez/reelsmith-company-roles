# Tools -- CMO

## Paperclip API

Primary coordination tool. Used for task management, delegation, approvals, and agent communication.

- Task CRUD, checkout, status updates
- Issue creation with parentId and goalId for subtask delegation
- Approval submission and follow-up
- Agent queries for report status

## MCP Servers

### Playwright Browser (Headless)
- **Purpose**: Content scheduling via Buffer, analytics scraping (delegated to Analytics Agent)
- **Transport**: stdio
- **Notes**: Used for scheduling approved content. Not used for direct posting in the first 2 weeks -- all posting goes through board approval.

### Playwright CDP (Real Chrome)
- **Purpose**: Persistent sessions for social media platforms that require login
- **Transport**: CDP
- **Notes**: Each social account has its own browser profile. Handle with care -- session invalidation requires manual re-auth.

## Skills

### Assigned to CMO

| Skill | Purpose |
|-------|---------|
| `para-memory-files` | Memory management, daily notes, knowledge graph, planning |
| `paperclip` | Paperclip API coordination |
| `content-calendar-planner` | Weekly content calendar generation and optimization |

### Assigned to Reports (for reference)

| Agent | Key Skills |
|-------|------------|
| Personal Brand Writer | `reelsmith-twitter-bip` (Build-in-Public X posts), `linkedin-content-writer` (LinkedIn posts), `genai-tutorial-thread` (Tutorial threads) |
| ReelSmith Brand Writer | `reelsmith-brand-voice` (Brand-consistent copy), `instagram-caption-writer`, `threads-content-writer`, `reelsmith-bip-threads` |
| Asset Generator | `general-image-prompt` (General image generation), `reelsmith-marketing-image-prompt` (Branded marketing materials), `cinematic-image-prompt` (Cinematic video thumbnails) |
| GenAI Scout | `content-discovery-genai` (Source identification, labeling, freshness scoring) |
| Tech Scout | `content-discovery-tech` (Source identification, labeling, freshness scoring) |
| Engagement Agent | `social-engagement-rules` (Rate limits, quality guidelines, platform-specific rules) |
| Analytics Agent | `social-analytics-scraper` (Metrics extraction, report formatting) |

## ReelSmith Vault (Obsidian)

Shared knowledge base repo: `reelsmith-vault`. Connected to Obsidian for Board browsing.

- **Your section**: `vault/cmo/` — content calendars, strategy docs, analytics reports, what-works playbook, campaign plans
- **Shared section**: `vault/shared/` — cross-team docs, company decisions
- Write in Obsidian-compatible markdown: `[[wikilinks]]`, YAML frontmatter, standard heading hierarchy.
- The vault is for durable strategy and content history. `para-memory-files` is for working memory.

### Vault Structure (CMO)
```
reelsmith-vault/
├── cmo/
│   ├── strategy/            # Weekly strategy updates (YYYY-WNN.md)
│   ├── analytics/           # Performance reports per date
│   ├── content-calendar.md  # Active week's content plan
│   ├── what-works.md        # Accumulating playbook of top performers
│   └── campaigns/           # Campaign-specific plans and retrospectives
├── content/
│   ├── personal-brand/      # Drafts/archives for @munkey_sol + LinkedIn
│   ├── reelsmith-brand/     # Drafts/archives for @ReelsmithApp, Instagram, Threads
│   └── discovery/           # Scout outputs and source material
└── shared/
    └── ...                  # Cross-team artifacts
```

## Content Pipeline Labels

When routing content between agents, always use these labels:

| Label | Source | Destination |
|-------|--------|-------------|
| `genai-news` | GenAI Scout | Personal Brand Writer → @munkey_sol |
| `llm-news` | Tech Scout | Personal Brand Writer → LinkedIn |
| `agent-tutorial-source` | Tech Scout | Personal Brand Writer → LinkedIn |
| `coding-news` | Tech Scout | Personal Brand Writer → LinkedIn |
| `genai-tutorial-source` | GenAI Scout | Personal Brand Writer → @munkey_sol |
| `viral-ai-video` | GenAI Scout | ReelSmith Brand Writer → Instagram |
| `engagement-target` | GenAI Scout | Engagement Agent |
| `bip-milestone` | CTO pipeline | ReelSmith Brand Writer → Threads + @munkey_sol |
| `feature-screenshot` | CTO pipeline | Personal Brand Writer → @munkey_sol |

## Platform Constraints (Reference)

| Platform | Max Text | Image Sizes | Notes |
|----------|----------|-------------|-------|
| X (Twitter) | 280 chars (or 25K with Blue) | 16:9, 1:1 | Blue subscription active on @munkey_sol |
| LinkedIn | 3000 chars | 1.91:1, 1:1 | Long-form performs well |
| Instagram | 2200 chars | 1:1, 4:5, 9:16 | Visual-first. Carousels get highest saves. |
| Threads | 500 chars | 1:1, 16:9 | Text-first but images boost reach |

## Notes

- Tools listed here are current as of agent creation. Update this file as new MCP servers or skills are added.
- If a tool fails silently (especially Playwright sessions), log the failure and flag to the board rather than retrying blindly.
- Buffer is the preferred scheduling tool. Direct posting via Playwright is the fallback.
