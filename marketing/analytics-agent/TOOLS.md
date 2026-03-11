# Tools -- Analytics Agent

## Paperclip API

Task creation (weekly reports to CMO), status updates, anomaly alerts.

## MCP Servers

### Playwright CDP (Real Chrome)
- **Purpose**: Scraping analytics pages from X Analytics, LinkedIn Analytics, Instagram Insights, Threads.
- **Transport**: CDP
- **Profiles**: Read-only access via persistent sessions on each platform.
- **Notes**: Analytics pages are scrape-fragile — platform UI changes can break extraction. If a scrape fails, log the error and note "Data unavailable" in the report. Do not guess.

## Skills

| Skill | Purpose |
|-------|---------|
| `para-memory-files` | Memory management, daily notes |
| `paperclip` | Paperclip API coordination |
| `social-analytics-scraper` | Platform-specific scraping patterns, metric extraction, report formatting |

## ReelSmith Vault

- **Your reports**: `vault/cmo/analytics/` — weekly, monthly, and daily reports
- **Daily snapshots**: `vault/cmo/analytics/daily/`
- Read-only: `vault/content/posting-log.md` — cross-reference posts with metrics

## Metrics Reference

### Primary Metrics (always report)
| Metric | Definition | Source |
|--------|-----------|--------|
| Follower count | Current total followers | All platforms |
| Follower Δ | Net change since last period | Calculated |
| Impressions / Reach | Times content was displayed | X, LinkedIn, Instagram |
| Engagement rate | (Engagements / Impressions) × 100 | Calculated |
| Saves / Bookmarks | Users saving content for later | X, Instagram |
| Profile visits | Users visiting the profile | X, LinkedIn, Instagram |

### Secondary Metrics (report when available)
| Metric | Source |
|--------|--------|
| Link clicks | X, LinkedIn |
| Shares / Reposts | All platforms |
| Comments | All platforms |
| Story/Reel views | Instagram |
| Video watch time | Instagram |

### Known Data Gaps
- Threads analytics are limited — follower count and basic engagement only.
- Waitlist conversion tracking requires UTM parameter setup (flag if not configured).
- Cross-platform attribution (which platform drives the most waitlist signups) may not be trackable.
