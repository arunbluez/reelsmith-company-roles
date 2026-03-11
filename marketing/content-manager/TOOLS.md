# Tools -- Content Manager

## Paperclip API

Task management, delegation to scouts/writers/asset generator, approval submission to CMO.

## MCP Servers

### Playwright CDP (Real Chrome)
- **Purpose**: Posting approved content to social platforms, scheduling via Buffer.
- **Profiles**: Separate browser profile per social account.
- **Notes**: Only used for board-approved content. If a session expires, log the failure and flag to CMO — do not attempt re-authentication.

## Skills

| Skill | Purpose |
|-------|---------|
| `para-memory-files` | Memory management, daily notes, planning |
| `paperclip` | Paperclip API coordination |
| `content-pipeline-router` | Label-based routing logic for discovery → writer assignment |

## ReelSmith Vault

- **Your section**: `vault/content/pipeline/` — queue status, routing decisions
- **Posting log**: `vault/content/posting-log.md` — every post, every platform, every timestamp
- **Content calendar**: `vault/cmo/content-calendar.md` (read — CMO maintains this, you execute against it)

## Platform Quick Reference

| Platform | Handle | Max Text | Optimal Image | Best Time (CET) |
|----------|--------|----------|---------------|-----------------|
| X | @munkey_sol | 25K (Blue) | 16:9 or 1:1 | 8-10 AM, 6-8 PM |
| LinkedIn | @arunbluez | 3000 chars | 1.91:1 or 1:1 | 8-10 AM Tue-Thu |
| X | @ReelsmithApp | 280 chars | 16:9 or 1:1 | 12-2 PM |
| Instagram | @Reelsmith.app | 2200 chars | 1:1, 4:5, 9:16 | 12-2 PM, 6-8 PM |
| Threads | @Reelsmith.app | 500 chars | 1:1 or 16:9 | 6-8 PM |
