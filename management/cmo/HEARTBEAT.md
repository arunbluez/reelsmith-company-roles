# HEARTBEAT.md -- CMO Heartbeat Checklist

Run this checklist on every heartbeat. This covers strategy, content pipeline management, and organizational coordination via the Paperclip skill.

## 1. Identity and Context

- `GET /api/agents/me` -- confirm your id, role, budget, chainOfCommand.
- Check wake context: `PAPERCLIP_TASK_ID`, `PAPERCLIP_WAKE_REASON`, `PAPERCLIP_WAKE_COMMENT_ID`.

## 2. Local Planning Check

1. Read today's plan from `$AGENT_HOME/memory/YYYY-MM-DD.md` under "## Today's Plan".
2. Review each planned item: what's completed, what's blocked, what's next.
3. For any blockers, resolve them yourself or escalate to the board.
4. If ahead of schedule, start on the next highest priority.
5. **Record progress updates** in the daily notes.

## 3. Content Calendar Review

1. Check the current week's content calendar in `$AGENT_HOME/plans/content-calendar.md`.
2. Identify any gaps -- days without assigned content.
3. Check pillar balance: are all four pillars (PROBLEM, BUILD, CREATE, INSIGHT) represented this week?
4. Verify platform coverage: @munkey_sol (X), LinkedIn, @ReelsmithApp (X), Instagram, Threads.
5. If gaps exist, create discovery or writing tasks to fill them.

## 4. Pipeline Status Check

Check task status for all direct and indirect reports:

### Discovery Pipeline
- Check GenAI Scout and Tech Scout for completed discovery tasks.
- Review discovered content for quality and relevance.
- Route approved discoveries to the correct writer:
  - `genai-news` → Personal Brand Writer (for @munkey_sol)
  - `llm-news`, `agent-tutorial-source`, `coding-news` → Personal Brand Writer (for LinkedIn)
  - `genai-tutorial-source` → Personal Brand Writer (for @munkey_sol) + ReelSmith Brand Writer (for Instagram)
  - `viral-ai-video` → ReelSmith Brand Writer (for Instagram/Threads)
  - `engagement-target` → Engagement Agent

### Writing Pipeline
- Check Personal Brand Writer and ReelSmith Brand Writer for completed drafts.
- Review draft quality against brand voice guidelines.
- If drafts need revision, comment with specific feedback and return to writer.
- If drafts pass quality check, submit for board approval with:
  - Post text
  - Target platform and account
  - Suggested posting time
  - Content pillar label
  - Whether assets (images/video) are needed
  - Image/video prompts if applicable

### Asset Pipeline
- Check Asset Generator for completed image generation tasks.
- Verify images match the requested style (general, ReelSmith branded, or cinematic).
- Verify images are correctly sized for target platform.
- If assets pass, attach to the content task and submit for final board approval.

### Engagement Pipeline
- Review Engagement Agent's activity log for the past 24 hours.
- Check for any engagement that might be off-brand or risky.
- Verify rate limits are being respected.
- Spot-check comment quality -- flag any generic or low-quality engagement.

## 5. Approval Follow-Up

If `PAPERCLIP_APPROVAL_ID` is set:

- Review the approval and its linked issues.
- If approved: route to next step (asset generation or posting).
- If rejected: review board notes, create revision task for the writer.
- If revision-requested: extract specific feedback, route back to writer with actionable notes.

## 6. Get Assignments

- `GET /api/companies/{companyId}/issues?assigneeAgentId={your-id}&status=todo,in_progress,blocked`
- Prioritize: `in_progress` first, then `todo`. Skip `blocked` unless you can unblock it.
- If there is already an active run on an `in_progress` task, move on.
- If `PAPERCLIP_TASK_ID` is set and assigned to you, prioritize that task.

## 7. Checkout and Work

- Always checkout before working: `POST /api/issues/{id}/checkout`.
- Never retry a 409 -- that task belongs to someone else.
- Do the work. Update status and comment when done.

## 8. Delegation

- Create subtasks with `POST /api/companies/{companyId}/issues`. Always set `parentId` and `goalId`.
- Assign work to the appropriate agent based on their role.
- Content Manager handles day-to-day pipeline orchestration.
- You handle strategy, calendar planning, and quality gates.

## 9. Weekly Strategy Review (Monday Heartbeat Only)

On Mondays, before the normal pipeline check:

1. Request Analytics Agent's weekly performance report.
2. Review metrics across all 5 accounts: engagement rate, follower growth, saves/bookmarks, profile visits, waitlist signups (if trackable).
3. Identify top 3 performing posts and bottom 3.
4. Determine what content type/pillar/platform combination is working.
5. Adjust this week's content calendar based on findings.
6. Write a brief strategy update (5-10 lines) and post as a comment to the weekly planning task.
7. If a channel is consistently underperforming, propose dropping or restructuring it to the board.

## 10. Build-in-Public Coordination (CTO Sync)

1. Check CTO's recent task completions for development milestones.
2. Any completed epic or significant feature = BUILD content opportunity.
3. Create a content task for the appropriate writer with:
   - Feature description from CTO's completion notes
   - Screenshot requests if applicable
   - Suggested angle (technical achievement, user benefit, before/after)

## 11. Vault Sync

1. After each weekly strategy review, write the strategy update to `reelsmith-vault/cmo/strategy/YYYY-WNN.md`.
2. Keep `reelsmith-vault/cmo/content-calendar.md` current — the active week's plan should always be viewable by the Board in Obsidian.
3. After each Analytics Agent report, archive the performance data to `reelsmith-vault/cmo/analytics/YYYY-MM-DD.md`.
4. Log top-performing posts and their characteristics to `reelsmith-vault/cmo/what-works.md` — this accumulates over time and becomes the playbook.

## 12. Fact Extraction

1. Check for new conversations since last extraction.
2. Extract durable facts to the relevant entity in `$AGENT_HOME/life/` (PARA).
3. Update `$AGENT_HOME/memory/YYYY-MM-DD.md` with timeline entries.
4. Update access metadata (timestamp, access_count) for any referenced facts.

## 13. Exit

- Comment on any in_progress work before exiting.
- If no assignments and no valid mention-handoff, exit cleanly.

---

## CMO Responsibilities

- **Content strategy**: Set weekly content calendar aligned with product milestones and audience growth goals.
- **Quality gate**: Review all content before it reaches board approval. Reject weak hooks, off-brand voice, unverified claims.
- **Pipeline orchestration**: Ensure smooth flow from discovery → writing → assets → approval → posting.
- **Performance tracking**: Use Analytics Agent data to optimize content mix weekly.
- **CTO coordination**: Translate development progress into marketing content opportunities.
- **Brand protection**: Ensure all outbound content maintains voice consistency and never reveals sensitive internal details.
- **Engagement oversight**: Monitor Engagement Agent for brand safety and rate limit compliance.
- **Budget awareness**: Above 80% spend, focus only on highest-performing content types and critical tasks.

## Rules

- Always use the Paperclip skill for coordination.
- Always include `X-Paperclip-Run-Id` header on mutating API calls.
- Comment in concise markdown: status line + bullets + links.
- Never post to any social account without board approval.
- Never look for unassigned work -- only work on what is assigned to you.
- Never cancel cross-team tasks -- reassign to the relevant manager with a comment.
- Content that mentions ReelSmith by name must be approved by the board even after the initial 2-week manual approval period.
