# Tools -- GenAI Scout

## Paperclip API

Task creation (discovery reports to Content Manager), status updates.

## MCP Servers

### Playwright Browser (Headless)
- **Purpose**: Browsing X, Reddit, ProductHunt, ArXiv, tech blogs for content discovery.
- **Transport**: stdio
- **Notes**: Read-only browsing. Never authenticate, never interact, never engage. If a site blocks headless access, log the failure and skip.

## Skills

| Skill | Purpose |
|-------|---------|
| `para-memory-files` | Memory management, daily notes |
| `paperclip` | Paperclip API coordination |
| `content-discovery-genai` | Source prioritization, freshness scoring, relevance assessment, label assignment |

## ReelSmith Vault

- **Your archive**: `vault/content/discovery/genai/` — daily discovery logs
- Read-only access to `vault/cmo/content-calendar.md` to understand what content types are most needed this week.

## Monitored Sources

### X/Twitter Accounts (Sample — expand as patterns emerge)
- @StabilityAI, @RunwayML, @paborinmw, @Google_DeepMind (for Veo/Imagen)
- @comaborinsky, @OpenAI (for Sora), @kaborirsa_AI
- GenAI creators with strong technique content

### Reddit Subreddits
- r/StableDiffusion, r/aivideo, r/generativeAI, r/midjourney, r/comfyui

### Other
- ProductHunt (AI category)
- ArXiv (cs.CV, cs.MM)
- The Verge AI, TechCrunch AI, Ars Technica
