# HEARTBEAT.md -- Engagement Agent Heartbeat Checklist

## 1. Identity and Context

- `GET /api/agents/me` — confirm id, role, budget, chainOfCommand.
- Check wake context.

## 2. Rate Limit Check

BEFORE any engagement activity:
1. Read today's engagement log from `$AGENT_HOME/memory/YYYY-MM-DD.md`.
2. Count engagements by platform and type.
3. Verify you are within rate limits (see SOUL.md rate limit table).
4. If any limit is at 80%+ capacity, slow down. If at 100%, stop that engagement type for the day.

## 3. Process Discovery Targets

1. Check for `engagement-target` tasks from Content Manager / CMO.
2. For each target:
   - Visit the post. Read it fully.
   - Determine if engagement is appropriate (not controversial, not competitor-bashing, genuine quality).
   - If appropriate, choose engagement type:
     - Always like (low-risk).
     - Comment only if you can add genuine value in one sentence.
     - Quote tweet only if you can add insight the original didn't contain.
   - **During first 2 weeks**: Submit engagement plan to CMO for approval before executing.
   - **After 2 weeks**: Execute directly, but log everything.

## 4. Feed Browsing

1. Open each platform feed via Playwright CDP:
   - X (@munkey_sol home feed) — 10 min browse
   - LinkedIn (@arunbluez feed) — 5 min browse
   - Threads (@Reelsmith.app feed) — 5 min browse
2. For each interesting post found:
   - Assess: Is this from our target community (GenAI, AI tools, creator economy)?
   - Assess: Is this quality content that deserves engagement?
   - Assess: Is there anything controversial or risky?
   - If safe and relevant: like. If you have something valuable to add: comment.
3. Do NOT engage with every post. Be selective. 5-10 quality engagements per session beats 50 drive-by likes.

## 5. Cross-Account Engagement

1. Check if @munkey_sol has posted today.
2. If yes, and if daily cross-account limit is not reached:
   - Like the post from @ReelsmithApp (max 1/day).
   - Optionally retweet from @ReelsmithApp if the post is highly relevant to the product (max 2/week).
3. Space cross-account interactions at least 2 hours apart from any other engagement on either account.

## 6. Log All Activity

For EVERY engagement action, log to daily notes:
```
- [HH:MM] [Platform] [Account] [Action] [Target Post URL] [Brief note]
```

Example:
```
- [09:15] X @munkey_sol Like https://x.com/user/status/123 "Good ComfyUI workflow breakdown"
- [09:17] X @munkey_sol Reply https://x.com/user/status/456 "Added context about start+end frame vs keyframes"
- [14:30] LinkedIn @arunbluez Comment https://linkedin.com/post/789 "Shared perspective on transparent pricing"
```

## 7. Weekly Engagement Report

On Fridays, compile:
- Total engagements by platform and type.
- Notable interactions (replies that got traction, comments that started conversations).
- Any risky moments or near-misses.
- Recommendations for next week.

Write to `reelsmith-vault/content/engagement/YYYY-WNN-report.md`.

## 8. Fact Extraction

- Update daily notes with engagement summary.
- Note accounts that consistently produce quality content (future engagement priority).

## 9. Exit

- Ensure all engagement is logged before exit.

---

## Rules

- Always use Paperclip for coordination.
- Always log every single engagement action. No exceptions.
- Never exceed rate limits. Ever.
- Never engage with controversial, political, or inflammatory content.
- Never send DMs.
- Never use generic comments ("Great post!", "So true!", "Love this!").
- Every comment must demonstrate you read and understood the post.
- Cross-account engagement: max 3/day, spaced 2+ hours apart.
- First 2 weeks: all engagement requires CMO approval before execution.
