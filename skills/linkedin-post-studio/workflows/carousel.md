---
title: Carousel workflow
output_type: carousel
last_updated: 2026-04-20
---

# Carousel workflow

## When this workflow loads

Triggers on:

- "carousel about X"
- "carousel brief for X"
- "slides for X"
- `/linkedin-carousel`

## Required references (loaded in this order)

1. `references/post-structure/post-structure-index.md`
2. `references/hook-library/hook-index.md` and 1–2 hook category files — for the cover slide headline
3. `references/formatting-rules.md` — slide density rules, aspect ratio specs, text overlay constraints
4. `references/industry/<profile.industry>.md` — conditional; fall back to `references/industry/generic.md` if missing
5. `references/content-pillars.md` — for pillar selection aligned to goal

## Required inputs

- **topic** — from the user's request. If absent, ask: "What topic should the carousel cover?"
- **goal** — from request override or `profile.default_goal`. If neither exists, ask: "Which goal? lead-gen | thought-leadership | brand-awareness | community"
- **slide count** — from request; default 8
- **aspect ratio** — from request; default 4:5 (1080×1350)
- **profile** — resolved by SKILL.md before this workflow loads

## Generation steps

1. **Determine goal, topic, slide count, and aspect ratio.** Apply defaults where not specified.

2. **Pick pillar and framework.** Same logic as the text-post workflow: match framework to goal using `post-structure-index.md`. The framework drives the narrative arc across slides.

3. **Cover slide (Slide 1).** A bold claim or specific outcome promise. Headline: 5–8 words, high-contrast type. Avoid vague headings like "My 2025 lessons" — use specific outcomes instead. Example: "8 pricing mistakes that cut my margins in half."

4. **Body slides (Slides 2 through n–1).** One idea per slide. Each slide:
   - Headline: 5–8 words
   - Body: 20–30 words maximum
   - Progress indicator: add a "3/8"-style marker to each body slide — this improves completion rates
   - Keep total slide count ≤12; engagement collapses above that threshold

5. **CTA slide (last slide).** A single direct ask with visual weight at least equal to the cover. Because PDF links are not clickable, put the destination URL as plain text on the slide AND include a clickable link in the post caption separately.

6. **Aspect ratio guidance.** Default: 4:5 (1080×1350) — maximizes mobile screen real estate. Safe alternative: 1:1 (1080×1080). Avoid 9:16 for carousels.

7. **Draft the post caption.** 700–900 characters. The caption earns the expansion click and previews what the carousel delivers — it should not simply repeat slide headlines. If `profile.compliance.required_disclaimers` is non-empty, note which slides the disclaimers should appear on (typically the last body slide before the CTA).

8. **Generate slug.** First 5 words of the cover slide headline, lowercase, hyphens, no punctuation.

## Output format

**In chat:** Slide-by-slide brief in this format, followed by the post caption:

```
Slide 1 (Cover): <headline>
Slide 2: <headline> / <body text> [2/8]
Slide 3: <headline> / <body text> [3/8]
...
Slide N (CTA): <headline> / <body text> / URL: <url as text>

---
Post caption:
<caption text>
```

**Written to file:** `<data_location>/drafts/YYYY-MM-DD-<slug>.md` using `templates/draft-template.md`.

Frontmatter fields: `profile`, `goal`, `format: carousel`, `framework_used`, `hook_category` (from cover slide hook), `pillar`, `status: draft` (or `needs-approval` if `profile.compliance.pre_approval_required`), `created: today`, `updated: today`. Add carousel-specific fields: `slide_count: <n>`, `aspect_ratio: <ratio>`, `slide_headlines: [array of each slide headline in order]`.

Body of the draft file: full slide briefs plus the post caption.

## Cross-workflow suggestions

- "Want a text post announcing this carousel?" → `workflows/text-post.md`
- "Poll on the same theme?" → `workflows/poll.md`

## Visual companion (v2+)

When creators-studio integration ships, generate one image per slide matching brand colors from the profile. No-op in v1.
