---
title: Newsletter workflow
output_type: newsletter
last_updated: 2026-04-20
---

# Newsletter workflow

## When this workflow loads

Triggers on:

- "newsletter on X"
- "LinkedIn newsletter about X"
- "write an edition on X"
- `/linkedin-newsletter`

## Required references (loaded in this order)

1. `references/post-structure/post-structure-index.md`
2. 1–2 `references/post-structure/framework-*.md` files — selection depends on the edition goal (e.g., `framework-slay.md` for thought-leadership editions, `framework-pas.md` for lead-gen editions)
3. `references/content-pillars.md`
4. `references/engagement-tactics.md` — load the newsletter strategy section specifically: weekly cadence guidance, 800–1,200 word sweet spot, 25–35% open rate target
5. `references/industry/<profile.industry>.md` — fall back to `references/industry/generic.md` if the industry file is missing

## Required inputs

- **topic/theme** — from the user's request. If absent, ask: "What topic or theme is this edition covering?"
- **subtopics** (optional) — supporting angles or sections the user wants included
- **goal** — from an explicit request override first, then `profile.default_goal`. If neither is set, ask: "Which goal? lead-gen | thought-leadership | brand-awareness | community"

## Generation steps

1. **Take input.** Confirm topic/theme. Note any subtopics and resolve goal.

2. **Target length: 800–1,200 words** per the newsletter strategy section in `engagement-tactics.md`. If the topic is narrow, aim for the lower bound; if it is a flagship edition, push toward 1,200.

3. **Structure the newsletter edition:**
   - **Title** — 6–10 words, outcome-focused. The reader must be able to tell what they will know or be able to do after reading.
   - **Subheader** — 1 sentence that states the promise of the edition directly.
   - **Opening** — 50–100 words. The hook that earns the email open. Lead with a specific observation, an uncomfortable fact, or a short scene. Do not open with pleasantries.
   - **Body: 3–5 sub-sections with H2 headings** — 150–250 words each. Each sub-section should cover one idea completely. Use short paragraphs and concrete examples. Where the profile's industry permits, include a specific data point or case per section.
   - **Key takeaways** — 3–5 bullets. One insight per bullet. Write in full sentences; no bullet should be a sentence fragment.
   - **CTA** — one only. Choose the most appropriate single action: subscribe, DM for more, or book a call. Do not stack CTAs.

4. **Generate a promo post for the LinkedIn feed.** This is a separate asset published on the same day to drive clicks to the full edition:
   - Format: text post
   - Length: 500–800 characters (including line breaks)
   - Content: 3 specific takeaways from the newsletter + "Read the full edition at the link" CTA at the end
   - Apply the same hook constraints used in `text-post.md` generation steps (line 1 ≤62 mobile characters, no emoji, no banned openers)

5. **Apply compliance.** If `profile.compliance.required_disclaimers` is non-empty, append each disclaimer at the end of the newsletter body (after the CTA) and repeat the most relevant disclaimer at the bottom of the promo post.

## Output format

**In chat:** Full newsletter edition followed by the promo post, clearly labelled as two separate assets.

**Written to files:** Two files are created:

- `<data_location>/drafts/YYYY-MM-DD-<slug>-newsletter.md` — format: newsletter; frontmatter fields: `profile`, `goal`, `format: newsletter`, `word_count`, `section_count`, `status: draft`, `created: today`, `updated: today`
- `<data_location>/drafts/YYYY-MM-DD-<slug>-promo.md` — format: text-post; frontmatter fields include `source_content: <slug>-newsletter` linking to the newsletter draft

## Cross-workflow suggestions

- "Repurpose this newsletter into 8 LinkedIn posts?" → `workflows/repurpose.md`
- "Add to content calendar?" → `workflows/content-calendar.md`
- "Generate 5 companion comment prompts tied to this theme?" → `workflows/companion-comments.md`

## Visual companion (v2+)

Header image generation via creators-studio integration. No-op in v1.
