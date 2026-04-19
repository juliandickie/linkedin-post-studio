---
title: Post teardown workflow
output_type: post-teardown
last_updated: 2026-04-20
---

# Post teardown workflow

## When this workflow loads

Triggers on:

- "teardown this post"
- "analyze why this went viral"
- "break down this LinkedIn post"
- "explain what's working here"
- `/linkedin-teardown`

## Required references (loaded in this order)

1. `references/hook-library/hook-index.md` + 1–2 category files — selection based on the hook pattern detected in the post being analyzed
2. `references/post-structure/post-structure-index.md`
3. `references/content-pillars.md`
4. `references/algorithm-mechanics.md` — for checking ranking signals: save-worthiness, substantive comment bait, dwell time indicators
5. `references/ethics-failures.md` — for the rage-bait vs contrarian check and the cringe pattern check (Wallake/Baltzell patterns)

## Required inputs

- **post** — a URL or pasted post text. If neither is provided, ask: "Please paste the post text or share a URL."
- **performance data** (optional) — impressions, reactions, comment count if the user knows them. Include in the report if provided.

## Generation steps

1. **Take input.** If a URL is provided and `config` allows WebFetch, retrieve the post text. If WebFetch is not available, ask the user to paste the text directly.

2. **Analyze structure across four dimensions:**
   - **Hook category** — match the opening lines against hook-library categories. Name the pattern (e.g., "specific number + outcome", "contrarian opener").
   - **Framework** — match the overall structure against post-structure frameworks. Name it: AIDA, PAS, BAB, SLAY, Hook-Story-Offer, STAR, or hybrid.
   - **Pillar archetype** — identify which of the 13 archetypes from `content-pillars.md` this post occupies.
   - **Voice signals** — sentence rhythm, emoji use, formatting, parallel structures, any patterns the profile could borrow.

3. **AI-slop check.** Run `anti-ai-constraint.md` against the post text: banned vocabulary, banned structures, and required elements (specific proper noun or number, a slightly awkward sentence, a non-best-practice sentence).

4. **Algorithm fitness check.** Against `algorithm-mechanics.md`: length (within 800–2,000 character sweet spot?), above-the-fold hook (earns the "See more" click?), CTA placement (post body vs first comment?), format freshness (same-format back-to-back penalty risk?), and which ranking signals the post likely triggers (save-worthiness, substantive comment bait, dwell time).

5. **Ethics check.** Against `ethics-failures.md`: rage-bait vs contrarian (is the claim falsifiable?), cringe risk (Wallake/Baltzell pattern — author centered during someone else's pain), fabricated story tells (no names, no dates, suspiciously perfect arc).

6. **Produce the teardown report** covering: Hook, Framework, Pillar, Voice signals, AI-slop score (pass/fail), Algorithm fitness, Ethics (pass/fail with rationale). Include any provided performance data alongside the fitness check.

7. **Generate "your version."** Write a post in the active profile's voice on a related angle, using a similar structural approach but with original content. Do not copy the analyzed hook verbatim — that would fail the anti-ai-constraint. The "your version" post goes through the same hook constraints as `text-post.md` generation step 5.

## Output format

**In chat:** Structured teardown report followed by the "your version" draft, clearly labelled.

**Written to file:** `<data_location>/drafts/YYYY-MM-DD-teardown-<slug>.md` with frontmatter: `format: teardown`, `source_post_url` (if any), `detected_hook_category`, `detected_framework`, `detected_pillar`, `ai_slop_score` (pass/fail), `ethics_score` (pass/fail), `your_version_slug` (cross-reference to the "your version" post if saved separately).

## Cross-workflow suggestions

- "Teardown another post for comparison?" → re-dispatch this workflow
- "Apply the lessons to your content calendar?" → `content-calendar.md`
- "Save the 'your version' as a standalone draft?" → `text-post.md`

## Visual companion (v2+)

Not applicable for teardowns.
