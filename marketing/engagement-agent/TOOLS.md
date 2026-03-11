# Tools -- Engagement Agent

## Paperclip API

Task checkout, status updates, engagement reports.

## MCP Servers

### Playwright CDP (Real Chrome)
- **Purpose**: Engaging with posts on X, LinkedIn, and Threads via persistent authenticated sessions.
- **Transport**: CDP
- **Profiles**: Separate browser profile per account (@munkey_sol, @arunbluez, @ReelsmithApp, @Reelsmith.app Threads).
- **Notes**: Handle with extreme care. Session invalidation = manual re-auth. If any session fails, stop engagement on that platform and flag to CMO.

## Skills

| Skill | Purpose |
|-------|---------|
| `para-memory-files` | Memory management, daily notes, engagement logging |
| `paperclip` | Paperclip API coordination |
| `social-engagement-rules` | Rate limits, quality guidelines, platform-specific rules, comment templates |

## ReelSmith Vault

- **Your log**: `vault/content/engagement/` — daily logs, weekly reports
- Read-only: `vault/cmo/content-calendar.md` — to understand current content priorities

## Rate Limit Reference

| Platform | Likes/hr | Likes/day | Comments/hr | Comments/day | QTs/hr | QTs/day |
|----------|----------|-----------|-------------|-------------|--------|---------|
| X | 15 | 50 | 5 | 15 | 2 | 5 |
| LinkedIn | 10 | 30 | 3 | 10 | - | - |
| Threads | 10 | 30 | 3 | 10 | - | - |
| Cross-acct | 1 | 3 | - | - | - | - |

## Engagement Personality Per Account

| Account | Persona | Comment Style |
|---------|---------|---------------|
| @munkey_sol | Curious builder | Technical, questions, shares experience |
| @arunbluez | Professional peer | Business context, connects dots |
| @ReelsmithApp | Industry participant | Likes and amplifies. Minimal commenting. |
| @Reelsmith.app (Threads) | Community member | Authentic, brief reactions |
