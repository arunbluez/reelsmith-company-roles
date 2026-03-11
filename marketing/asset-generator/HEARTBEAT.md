# HEARTBEAT.md -- Asset Generator Heartbeat Checklist

## 1. Identity and Context

- `GET /api/agents/me` — confirm id, role, budget, chainOfCommand.
- Check wake context.

## 2. Get Assignments

- `GET /api/companies/{companyId}/issues?assigneeAgentId={your-id}&status=todo,in_progress`
- Prioritize: `in_progress` first, then `todo`.
- If `PAPERCLIP_TASK_ID` is set, prioritize that.

## 3. Checkout and Generate

For each assigned task:

1. `POST /api/issues/{id}/checkout` — claim the task.
2. Read the task brief:
   - Image generation prompt(s)
   - Target platform and dimensions
   - Style guide (general / ReelSmith branded / cinematic)
   - Number of images needed (single, carousel slides, variants)
3. **Generate via Google Labs Flow:**
   - Open Playwright CDP session (persistent Google account profile).
   - Navigate to Google Labs Flow.
   - Input the prompt exactly as provided.
   - Wait for generation to complete.
   - Download the output image.
4. **Verify output:**
   - Does it match the requested subject/style?
   - Is the quality acceptable (no artifacts, no mangled text, no wrong subjects)?
   - If output is bad: retry once with same prompt. On second failure, flag as blocked with screenshot.
5. **Post-process:**
   - Resize/crop to exact target dimensions (see AGENTS.md dimension table).
   - Apply consistent naming: `YYYY-MM-DD_[platform]_[slug]_[variant].png`
   - Verify final file dimensions are correct.
6. **Deliver:**
   - Attach processed images to the parent content task.
   - Comment with: filename(s), dimensions, file size.
   - Update task status to done.

## 4. Carousel Handling

For Instagram carousels (multiple slides):
1. Generate each slide sequentially.
2. Maintain visual consistency across slides — if slide 1 uses a specific color scheme, all slides should match.
3. If one slide fails while others succeed, deliver the successful slides and flag the failed one.
4. Number slides clearly in filenames: `_slide1`, `_slide2`, etc.

## 5. Fallback Procedure

If Google Labs Flow is unavailable:
1. Log the error with timestamp and screenshot.
2. Flag the task as blocked immediately.
3. Comment: "Google Labs Flow unavailable. Error: [description]. Awaiting Content Manager guidance."
4. Do NOT attempt alternative platforms without explicit approval.

## 6. Vault Log

- Log all generated assets to `reelsmith-vault/content/assets/YYYY-MM-DD.md`:
  - Filename, dimensions, platform, prompt used, generation success/failure.
- This builds a reference of what prompts work well over time.

## 7. Fact Extraction

- Update daily notes with generation counts and success rate.

## 8. Exit

- Comment on in_progress work.

---

## Rules

- Always use Paperclip for coordination.
- Never modify prompts. Generate exactly what's requested.
- Max 2 retries per image. Then flag as blocked.
- Always verify dimensions match platform spec before delivery.
- Consistent file naming. No exceptions.
- Report failures with screenshots, not just text descriptions.
