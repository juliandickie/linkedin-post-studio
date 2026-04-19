---
title: Idea mining workflow
output_type: idea-mining
last_updated: 2026-04-20
---

# Idea mining workflow

## When this workflow loads

Triggers on:

- "mine ideas from <source>"
- "ideas from this Reddit thread"
- "extract post angles from <url>"
- `/linkedin-mine`

## Required references (loaded in this order)

1. `references/content-pillars.md` — for mapping extracted angles to pillars and archetypes
2. `references/engagement-tactics.md` — specifically the anti-rage-bait filter; use §3 contrarian vs rage-bait distinction to screen every angle before output
3. `references/industry/<profile.industry>.md` — fall back to `references/industry/generic.md` if missing

## Required inputs

- **source material** — one of:
  - Pasted text (Reddit thread, review block, sales call transcript, customer feedback email)
  - File path (local markdown, txt, or transcript file)
  - URL — only valid if `config.features.online_idea_mining: true` AND the tool environment supports WebFetch or WebSearch

## Generation steps

1. **Take input.** Identify source type (pasted, file path, or URL).

2. **If URL provided:**
   - Check `config.features.online_idea_mining`. If false, tell the user this feature is off and ask them to paste the content instead.
   - If true, use WebFetch to retrieve the page.
   - For Reddit URLs, attempt structured parsing to separate the original post from top-level comments so each voice is weighted separately.

3. **Extract patterns from the source:**
   - **Pain points** ranked by frequency across the text
   - **Exact frustration phrasing** — pull verbatim quotes that could serve as hooks
   - **Repeated questions** appearing across multiple comments or messages
   - **Recurring myths** candidates for debunking posts

4. **Map each pattern to a pillar** using `content-pillars.md`. Note which of the 13 archetypes the pattern fits most naturally.

5. **Generate 10–15 post angles.** For each angle produce:
   - One-line angle description
   - Suggested pillar
   - Suggested hook category
   - One-line rationale explaining why the angle will work for the profile's audience

6. **Filter out rage-bait.** Any angle that would produce sweeping generalizations or identity-based attacks (per the contrarian vs rage-bait distinction in `engagement-tactics.md`) must be replaced with a specific, falsifiable version of the same claim before output. Do not include the original rage-bait version.

7. **Rank the 10–15 angles** by four factors:
   - Specificity (high weight) — the more concrete, the higher the rank
   - Proof availability (high weight) — does the profile have direct experience to back it up?
   - Audience relevance (high weight) — does it speak to the profile's target reader?
   - Novelty vs. recent drafts (medium weight) — deprioritize angles that duplicate the profile's recent content

## Output format

**In chat:** Ranked list of 10–15 angles. Each entry shows: angle description, pillar, hook category, rationale. Number them in rank order.

**Written to file:** `<data_location>/drafts/YYYY-MM-DD-ideas-<source-slug>.md` with frontmatter `format: idea-list`, `status: ready-to-use`. Body contains the full ranked list plus source provenance (URL, file path, or an excerpt from pasted content — limit excerpt to 3 sentences).

## Cross-workflow suggestions

- "Draft posts for the top 3 angles?" → `text-post.md` per angle
- "Add top angles to content calendar?" → `content-calendar.md`

## Visual companion (v2+)

Not applicable.
