# HEARTBEAT.md -- Tech Scout Heartbeat Checklist

## 1. Identity and Context

- `GET /api/agents/me` — confirm id, role, budget, chainOfCommand.
- Check wake context.

## 2. Local Planning Check

1. Read daily notes. Check last cycle's discoveries to avoid duplicates.

## 3. Discovery Sweep

### HackerNews (highest signal-to-noise)
1. Check front page for AI/ML/agents/coding stories.
2. Look for: new frameworks, benchmark results, significant technical discussions, funding news.
3. HN comments often contain more insight than the linked article — note standout comments.

### GitHub Trending
1. Check daily trending in: AI, machine-learning, agents, developer-tools.
2. For each promising repo: check star velocity, actual code quality, author credibility.
3. Only report repos with genuine substance, not README-only hype.

### X/Twitter
1. Check AI researcher accounts, framework authors, company accounts.
2. Look for: model announcements, technical threads, benchmark claims.
3. Verify claims against primary sources before reporting.

### Reddit
1. Check r/LocalLLaMA, r/MachineLearning, r/programming — sort by "hot" and "new".
2. Look for: in-depth technical posts, framework comparisons, deployment guides.

### Web / Blogs
1. Scan company engineering blogs (Anthropic, OpenAI, Google DeepMind, Meta AI).
2. Check for technical blog posts with deployment insights or architectural details.

## 4. Curate and Label

For each discovery worth reporting:
1. Assign label: `llm-news`, `agent-tutorial-source`, or `coding-news`.
2. Verify freshness.
3. Write discovery report in standard format.
4. Score technical depth: surface/medium/deep.
5. Create task assigned to Content Manager (Sable).

## 5. Deduplication

- Check recent tasks before creating. Same story = one report with best source.

## 6. Vault Archive

- Archive to `reelsmith-vault/content/discovery/tech/YYYY-MM-DD.md`.

## 7. Get Assignments

- Check for specific research tasks from Content Manager.

## 8. Fact Extraction

- Update daily notes. Note high-value sources.

## 9. Exit

- Comment on in_progress work. Log "no findings" if applicable.

---

## Rules

- Always use Paperclip for task creation.
- Always include `X-Paperclip-Run-Id` header on mutating calls.
- Never engage with posts. Discovery only.
- Label every discovery.
- Verify claims before reporting. Note unverified claims explicitly.
