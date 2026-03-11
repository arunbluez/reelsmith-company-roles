# Tools -- Asset Generator

## Paperclip API

Task checkout, status updates, file attachment, delivery notifications.

## MCP Servers

### Playwright CDP (Real Chrome)
- **Purpose**: Google Labs Flow image generation via persistent browser session.
- **Transport**: CDP
- **Profile**: Authenticated Google account with access to Labs Flow.
- **Notes**: If the session expires, flag to Content Manager. Do not attempt re-authentication.

### Image Processing (CLI)
- **Purpose**: Resize, crop, and format images for platform-specific dimensions.
- **Tools**: ImageMagick / Sharp (available via CLI).
- **Notes**: Always verify output dimensions after processing.

## Skills

| Skill | Purpose |
|-------|---------|
| `para-memory-files` | Memory management, daily notes |
| `paperclip` | Paperclip API coordination |

## ReelSmith Vault

- **Your log**: `vault/content/assets/` — generation logs with prompts, results, success rates
- Read-only: platform dimension specs are in AGENTS.md

## Platform Dimension Quick Reference

| Target | Dimensions | Use |
|--------|------------|-----|
| 1200×675 | X post landscape | Default X image |
| 1080×1080 | Square (all platforms) | Instagram, Threads, LinkedIn, X |
| 1080×1350 | Instagram portrait | Instagram feed |
| 1080×1920 | Vertical full | Instagram Story/Reel, Threads |
| 1200×627 | LinkedIn landscape | LinkedIn post |
