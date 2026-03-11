# HEARTBEAT.md -- ReelSmith Brand Writer Heartbeat Checklist

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
2. Read the content brief / discovery report.
3. Identify the target platform:
   - `viral-ai-video` → Instagram / @Reelsmith.app
   - `bip-milestone` → Threads / @Reelsmith.app (primary) + sometimes @ReelsmithApp X
   - `genai-news` (filtered) → X / @ReelsmithApp (vault for launch)
   - CMO-directed content → as specified
4. Determine format:
   - Instagram: Single image + caption, carousel (multi-slide), reel script
   - Threads: Text post (2-3 paragraphs), text + image
   - X: Single tweet, tweet + image
5. **Write the draft.**
   - Match the brand voice (see SOUL.md). You are a studio, not a person.
   - For Instagram: write caption AND visual brief (what each image/slide should contain).
   - For carousels: specify each slide's text overlay and visual description.
   - For reels: write a shot list with timing (e.g., "0-3s: hook text overlay on dark bg, 3-8s: reference sheet montage").
6. **Write asset prompts.**
   - Every visual need gets a full generation prompt using the appropriate skill.
   - Instagram images: specify 1:1 or 4:5 dimensions.
   - Include ReelSmith brand elements where appropriate (gradients, glassmorphism, brand colors).
7. Format per standard template (see AGENTS.md).
8. Comment on task with complete draft and update status.

## 5. Handle Revisions

1. Read specific feedback from Content Manager.
2. Implement precisely.
3. Resubmit with change notes.

## 6. Build-in-Public Series (Threads)

When no specific tasks are assigned, and if the content calendar has gaps for Threads:
1. Check `reelsmith-vault/cto/` for recent development milestones.
2. Draft a Threads post that translates the technical milestone into product philosophy.
3. Frame as: what we believe → what we built → why it matters for creators.
4. Submit to Content Manager as a self-initiated draft.

## 7. Vault Archive

- Archive drafts to `reelsmith-vault/content/reelsmith-brand/drafts/YYYY-MM-DD-[platform]-[slug].md`.

## 8. Fact Extraction

- Update daily notes.

## 9. Exit

- Comment on in_progress work.

---

## Rules

- Always use Paperclip for coordination.
- Never post. Drafts only.
- All ReelSmith-named content requires board approval.
- Never overpromise features. Only reference what's built.
- Every image need includes a full generation prompt.
- Instagram carousels specify every slide.
