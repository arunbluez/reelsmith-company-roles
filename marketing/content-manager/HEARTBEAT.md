# HEARTBEAT.md -- Content Manager Heartbeat Checklist

## 1. Identity and Context

- `GET /api/agents/me` — confirm id, role, budget, chainOfCommand.
- Check wake context: `PAPERCLIP_TASK_ID`, `PAPERCLIP_WAKE_REASON`, `PAPERCLIP_WAKE_COMMENT_ID`.

## 2. Local Planning Check

1. Read today's plan from `$AGENT_HOME/memory/YYYY-MM-DD.md`.
2. Review progress. Update notes.

## 3. Ingest Discovery Output

1. Check GenAI Scout and Tech Scout for completed discovery tasks.
2. For each completed discovery:
   - Read the label (`genai-news`, `llm-news`, `genai-tutorial-source`, etc.)
   - Assess quality: Is the source credible? Is it fresh (< 24h for news, < 7d for tutorials)?
   - Discard low-quality or stale discoveries. Comment why.
   - For valid discoveries, create a writing task:
     - Route to the correct writer based on the label (see AGENTS.md routing table).
     - Include: source URL, discovery summary, target platform, content pillar, and any angle suggestion.
     - Set priority: breaking news = high, tutorial source = medium, viral content = medium.

## 4. Review Writer Drafts

1. Check Personal Brand Writer and ReelSmith Brand Writer for completed drafts.
2. For each draft, review against this checklist:
   - **Hook**: Does the first line stop the scroll? Would you click if you saw this in a feed?
   - **Voice**: Does it sound like Arunkumar (personal) or ReelSmith brand (product)? Not generic AI.
   - **Claims**: Is every technical claim accurate and verifiable?
   - **Length**: Within platform limits? Optimal range for the format?
   - **Pillar fit**: Does it match the assigned content pillar (PROBLEM/BUILD/CREATE/INSIGHT)?
   - **Media needs**: Did the writer flag whether images/video are needed? Are prompts included?
3. If draft passes:
   - If NO assets needed → Submit to CMO for board approval. Include: post text, platform, account, suggested time, pillar label.
   - If assets needed → Create Asset Generator task with: image prompt(s), target platform dimensions, style guide (general/branded/cinematic), reference to the parent content task.
4. If draft needs revision:
   - Comment with specific, line-level feedback.
   - Return to writer. Do NOT rewrite it yourself.

## 5. Asset Pipeline Check

1. Check Asset Generator for completed image tasks.
2. For each completed asset:
   - Verify image dimensions match target platform.
   - Verify style matches the requested guide (general, ReelSmith branded, cinematic).
   - Verify proper file naming.
3. If assets pass:
   - Attach to the parent content task.
   - Submit the complete package (text + assets) to CMO for final board approval.
4. If assets fail:
   - Comment with specific feedback (wrong dimensions, wrong style, low quality).
   - Return to Asset Generator.

## 6. Post Approved Content

1. Check for board-approved content tasks.
2. For each approved task:
   - Verify the post text matches the approved version exactly. No modifications post-approval.
   - Verify all assets are attached and correct.
   - Post or schedule using browser automation:
     - **Primary**: Schedule via Buffer for the approved time slot.
     - **Fallback**: Direct post via Playwright CDP if Buffer is unavailable.
   - After posting, update the posting log in `reelsmith-vault/content/posting-log.md`:
     - Date, time, platform, account, content pillar, link to post (if available).
3. Comment on the task with posting confirmation and close the task.

## 7. Pipeline Health Check

1. Count items in each stage:
   - Discovery (pending from scouts)
   - Writing (assigned to writers, in progress)
   - Review (drafts waiting for your review)
   - Assets (waiting for Asset Generator)
   - Approval (submitted to CMO/board)
   - Ready to post (approved, not yet posted)
2. Flag bottlenecks:
   - If discovery queue is empty → ping scouts.
   - If a writer has items > 12h old → check for blockers.
   - If approval queue has items > 24h → flag to CMO.
3. Write a brief pipeline status update in daily notes.

## 8. CTO Content Intake

1. Check for `bip-milestone` or `feature-screenshot` tasks from the CTO pipeline.
2. These are high-priority BUILD pillar content opportunities.
3. Route to the appropriate writer:
   - `bip-milestone` → ReelSmith Brand Writer (Threads) + Personal Brand Writer (@munkey_sol)
   - `feature-screenshot` → Personal Brand Writer (@munkey_sol)
4. Include CTO's feature description and screenshot in the writing task.

## 9. Approval Follow-Up

If `PAPERCLIP_APPROVAL_ID` is set:
- Review the approval decision.
- If approved → route to posting queue.
- If rejected → extract board notes, create revision task for the writer with specific feedback.
- If revision-requested → same as rejected but note it's a revision, not a restart.

## 10. Get Assignments

- `GET /api/companies/{companyId}/issues?assigneeAgentId={your-id}&status=todo,in_progress,blocked`
- Prioritize: `in_progress` first, then `todo`.
- If `PAPERCLIP_TASK_ID` is set, prioritize that task.

## 11. Checkout and Work

- Always checkout before working: `POST /api/issues/{id}/checkout`.
- Never retry a 409.

## 12. Vault Sync

1. Update `reelsmith-vault/content/posting-log.md` with any new posts.
2. Update `reelsmith-vault/content/pipeline/queue-status.md` with current pipeline counts.

## 13. Fact Extraction

1. Extract durable facts to `$AGENT_HOME/life/` (PARA).
2. Update daily notes.

## 14. Exit

- Comment on any in_progress work before exiting.

---

## Rules

- Always use the Paperclip skill for coordination.
- Always include `X-Paperclip-Run-Id` header on mutating API calls.
- Never post without board approval.
- Never modify approved content.
- Never write content yourself — route to the correct writer.
- Never generate assets yourself — route to Asset Generator.
- Log every post in the vault posting log. No exceptions.
