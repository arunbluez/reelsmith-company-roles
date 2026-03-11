# HEARTBEAT.md -- GenAI Scout Heartbeat Checklist

## 1. Identity and Context

- `GET /api/agents/me` — confirm id, role, budget, chainOfCommand.
- Check wake context: `PAPERCLIP_TASK_ID`, `PAPERCLIP_WAKE_REASON`, `PAPERCLIP_WAKE_COMMENT_ID`.

## 2. Local Planning Check

1. Read daily notes from `$AGENT_HOME/memory/YYYY-MM-DD.md`.
2. Check what was discovered in the last cycle to avoid duplicates.

## 3. Discovery Sweep

Run through each source in priority order:

### X/Twitter (highest velocity)
1. Check trending topics in GenAI space.
2. Check monitored accounts and hashtags: #AIVideo, #AIArt, #GenerativeAI, #StableDiffusion, #ComfyUI, #Flux, #Runway, #Pika, #Sora, #Kling.
3. Look for: model releases, impressive outputs, workflow tips, tool announcements.
4. Look for engagement targets: quality posts with < 100 likes, < 24h old, from creators with < 10K followers.

### Reddit
1. Check r/StableDiffusion, r/aivideo, r/generativeAI, r/midjourney, r/comfyui — sort by "hot" and "new".
2. Look for: detailed tutorials, technique breakdowns, interesting discussions, new tool discoveries.

### ProductHunt
1. Check AI category for new launches.
2. Only flag products directly relevant to image/video/audio generation.

### ArXiv (lowest frequency, highest impact)
1. Check cs.CV and cs.MM for new papers.
2. Only flag papers with clear practical implications for generation quality, speed, or control.

### Web / Blogs
1. Quick scan of The Verge AI, TechCrunch AI, Ars Technica for major GenAI stories.
2. Only flag stories not already covered by X/Reddit sources.

## 4. Curate and Label

For each discovery worth reporting:
1. Assign the correct label: `genai-news`, `genai-tutorial-source`, `viral-ai-video`, or `engagement-target`.
2. Verify freshness meets the requirement for that label.
3. Write the discovery report in the standard format (see AGENTS.md).
4. Score ReelSmith relevance (low/medium/high).
5. Create a task assigned to Content Manager (Sable) with the discovery report.

## 5. Deduplication

- Before creating a discovery task, check recent tasks to ensure this hasn't been reported.
- Same story from multiple sources = one discovery with the best/original source linked.

## 6. Vault Archive

- Archive notable discoveries to `reelsmith-vault/content/discovery/genai/YYYY-MM-DD.md`.
- This builds a long-term reference of what's happened in the GenAI space.

## 7. Get Assignments

- `GET /api/companies/{companyId}/issues?assigneeAgentId={your-id}&status=todo,in_progress`
- If Content Manager has assigned specific research tasks, prioritize those.

## 8. Fact Extraction

- Update daily notes with discovery summary.
- Note any sources that consistently produce quality content (for future monitoring priority).

## 9. Exit

- Comment on any in_progress work.
- If no discoveries found, create a brief "no findings" note in daily log.

---

## Rules

- Always use Paperclip for task creation.
- Always include `X-Paperclip-Run-Id` header on mutating API calls.
- Never engage with any post (no likes, comments, follows, retweets).
- Discovery only. Never write content.
- Label every discovery. Unlabeled output is useless.
- Respect platform rate limits.
