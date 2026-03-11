# HEARTBEAT.md -- Analytics Agent Heartbeat Checklist

## 1. Identity and Context

- `GET /api/agents/me` — confirm id, role, budget, chainOfCommand.
- Check wake context.

## 2. Daily Snapshot

Every heartbeat, capture baseline numbers:

1. Open each platform's analytics page via Playwright CDP.
2. Record for each account:
   - Current follower count
   - Last 24h impressions/reach (if available)
   - Any notable spikes or anomalies
3. Write daily snapshot to `$AGENT_HOME/memory/YYYY-MM-DD.md`:
```
## Daily Snapshot
| Account | Followers | Δ | 24h Impressions | Notes |
|---------|-----------|---|-----------------|-------|
| @munkey_sol | X | +/- | X | ... |
| @arunbluez | X | +/- | X | ... |
| @ReelsmithApp | X | +/- | X | ... |
| @Reelsmith.app (IG) | X | +/- | X | ... |
| @Reelsmith.app (Threads) | X | +/- | X | ... |
```

## 3. Weekly Performance Report (Monday Only)

On Monday heartbeats, produce the full weekly report:

### Data Collection
1. For each account, scrape the past 7 days:
   - Total impressions/reach
   - Total engagements (likes, comments, shares, saves)
   - Engagement rate (engagements / impressions)
   - Profile visits
   - Follower net change
   - Top 3 posts by engagement rate (include post summary and numbers)
   - Bottom 3 posts by engagement rate
2. Cross-reference with the posting log (`vault/content/posting-log.md`) to tag each post with its content pillar.

### Report Compilation
Write to `reelsmith-vault/cmo/analytics/YYYY-WNN-weekly.md`:

```markdown
---
type: weekly-report
week: WNN
date_range: YYYY-MM-DD to YYYY-MM-DD
---

## Summary
[3-line summary: overall direction, biggest win, biggest concern]

## Account Performance
[Table: account, followers, Δ, impressions, engagement rate, profile visits]

## Top Performers
[For each of top 3: post summary, platform, pillar, engagement rate, saves, why it worked (correlation only)]

## Bottom Performers
[For each of bottom 3: post summary, platform, pillar, engagement rate, what might explain it]

## Pillar Breakdown
[Table: pillar, # posts, avg engagement rate, avg saves]

## Platform Comparison
[Table: platform, total posts, avg engagement rate, follower growth rate]

## Data Notes
[Correlations observed, data gaps, anomalies, platform-specific context]
```

### Delivery
- Create a Paperclip task for CMO with the report link.
- Tag as high priority — CMO needs this for Monday strategy review.

## 4. Monthly Summary (First Monday of Month)

Add to the weekly report:
- Month-over-month growth rates per account
- Best performing content type/pillar/platform combination
- Engagement rate trendline (improving/declining/flat)
- Save rate trend
- Write to `reelsmith-vault/cmo/analytics/YYYY-MM-monthly.md`

## 5. Anomaly Detection

If during any data collection you notice:
- Follower count drop > 5% in a day → flag to CMO immediately
- Engagement rate drop > 30% WoW → flag to CMO
- Unusual spike in profile visits → note in report (could indicate viral post or external mention)
- Platform analytics unavailable → log error, note in report, skip rather than estimate

## 6. Vault Sync

- All reports go to `reelsmith-vault/cmo/analytics/`
- Daily snapshots accumulated in `vault/cmo/analytics/daily/YYYY-MM-DD.md`
- This creates a complete historical dataset for trend analysis.

## 7. Fact Extraction

- Update daily notes with collection status.

## 8. Exit

- Ensure daily snapshot is saved.

---

## Rules

- Always use Paperclip for coordination.
- Never engage with any post. Read-only analytics access.
- Never modify account settings.
- Report facts, not strategy recommendations. Label correlations explicitly.
- If data is unavailable, say so. Never estimate silently.
- Weekly report delivered by Monday end-of-day. Non-negotiable.
