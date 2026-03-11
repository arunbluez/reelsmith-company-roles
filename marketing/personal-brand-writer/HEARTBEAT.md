# HEARTBEAT.md -- Personal Brand Writer Heartbeat Checklist

## 1. Identity and Context

- `GET /api/agents/me` — confirm id, role, budget, chainOfCommand.
- Check wake context.

## 2. Local Planning Check

1. Read daily notes. Check drafts in progress and pending assignments.

## 3. Get Assignments

- `GET /api/companies/{companyId}/issues?assigneeAgentId={your-id}&status=todo,in_progress`
- Prioritize: `in_progress` (revisions) first, then `todo` (new drafts).
- If `PAPERCLIP_TASK_ID` is set, prioritize that task.

## 4. Checkout and Write

For each assigned task:

1. `POST /api/issues/{id}/checkout` — claim the task.
2. Read the discovery report or content brief attached to the task.
3. Identify the target platform:
   - `genai-news`, `genai-tutorial-source`, `bip-milestone`, `feature-screenshot` → X / @munkey_sol
   - `llm-news`, `agent-tutorial-source`, `coding-news` → LinkedIn / @arunbluez
4. Identify the content pillar (PROBLEM/BUILD/CREATE/INSIGHT) if not specified.
5. Determine format:
   - Single tweet (X default for news, commentary)
   - Tweet + Image (X for visual content, features, screenshots)
   - Thread 2-4 tweets (X for tutorials, process breakdowns)
   - LinkedIn post (all LinkedIn content)
6. **Write the draft.**
   - Start with the hook. Write 5 options, pick the best.
   - Match the voice guide for the target platform (see SOUL.md).
   - Include suggested posting time.
7. **Assess asset needs.**
   - If the post needs an image: write the generation prompt using the appropriate skill.
   - If a screenshot exists (from CTO pipeline): reference it, don't generate a new one.
   - Note: `[attach: description]` + `[image-prompt: full prompt]` in the output.
8. Format output per the standard template (see AGENTS.md).
9. Comment on the task with the complete draft and update status to done.

## 5. Handle Revisions

When Content Manager returns a draft with feedback:
1. Read the specific feedback carefully.
2. Implement precisely — don't add unrequested changes.
3. Resubmit with a note on what changed.

## 6. Reference Check

Before finalizing any draft:
- Is every technical claim accurate? Cross-check against source material.
- Is there any internal information that shouldn't be public?
- Does the voice feel like Arunkumar, not like a content agency?
- Would this post get engagement from the target audience?

## 7. Vault Archive

- Archive final approved drafts to `reelsmith-vault/content/personal-brand/drafts/YYYY-MM-DD-[platform]-[slug].md`.
- This builds a corpus for voice consistency over time.

## 8. Fact Extraction

- Update daily notes with drafts completed and revision patterns.

## 9. Exit

- Comment on any in_progress work before exiting.

---

## Rules

- Always use Paperclip for coordination.
- Always include `X-Paperclip-Run-Id` header on mutating calls.
- Never post. Drafts only.
- Never reveal internal details (roadmap, pricing, competitive analysis).
- Every draft must use the standard output format.
- Every image need must include a generation prompt, not just a description.
