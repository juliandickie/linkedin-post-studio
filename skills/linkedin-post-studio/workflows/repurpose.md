---
title: Repurpose workflow
output_type: repurpose
last_updated: 2026-04-20
---

# Repurpose workflow

## When this workflow loads

Triggers on:

- "repurpose my newsletter"
- "turn this blog into LinkedIn posts"
- "convert podcast transcript to posts"
- `/linkedin-repurpose`

## Required references (loaded in this order)

1. `references/post-structure/post-structure-index.md` + 2–3 framework files — selection based on the chunk types found in the source (story chunks → `framework-slay.md` or `framework-hook-story-offer.md`; data chunks → `framework-pas.md`; case study chunks → `framework-bab.md` or `framework-star.md`)
2. `references/content-pillars.md` — for pillar assignment per chunk
3. `references/hook-library/hook-index.md` + 2–3 category files — selection based on chunk types and the profile's voice archetype
4. `references/industry/<profile.industry>.md` — fall back to `references/industry/generic.md` if missing

## Required inputs

- **source long-form content** — one of:
  - Pasted newsletter
  - Blog post URL or file path
  - Podcast transcript (pasted or file path)
  - Video transcript (pasted or file path)
  - Twitter/X thread (pasted or URL if WebFetch is available)
  - Book chapter (pasted or file path)

## Generation steps

1. **Take input.** Identify source type. If a URL is provided and the tool environment does not support WebFetch, ask the user to paste the content.

2. **Parse source into logical chunks.** One chunk equals one self-contained idea, argument, story, or framework. A 1,200-word newsletter typically yields 4–8 chunks. A 40-minute podcast transcript may yield 10–20 chunks. List chunks before proceeding.

3. **Propose a LinkedIn asset type per chunk:**
   - Story chunk → text post (SLAY or Hook-Story-Offer framework)
   - Framework or how-to chunk → carousel
   - Data or insight chunk → text post (statistic hook + PAS framework)
   - Controversial take → text post (contrarian hook)
   - Question or open debate → poll
   - Case study → text post (BAB or STAR framework)

4. **Produce the repurpose plan.** List all proposed assets — do not generate them yet. Each entry in the plan shows:
   - Asset type
   - Pillar
   - Suggested hook category
   - Estimated length (characters for text posts; slide count for carousels; poll options count for polls)

5. **Wait for user to select.** Present the plan and ask: "Which of these would you like me to generate? Reply with numbers or say 'all'." Do not generate any assets before confirmation — repurposing a long source can produce many files and the user should control scope.

6. **Generate each chosen asset.** Dispatch each to the appropriate workflow passing the chunk as topic input:
   - Text posts → `text-post.md`
   - Carousels → `carousel.md`
   - Polls → `poll.md`

7. **Apply shared frontmatter to every generated asset:**
   - `source_content`: short description of the source (e.g., "newsletter: Why AI Won't Replace You")
   - `source_url`: null if pasted, otherwise the URL
   - `repurpose_batch: YYYY-MM-DD` (today's date)

## Output format

**In chat:** Show the repurpose plan table first, before generating any content. After the user picks assets, show each generated asset with a note indicating which workflow it dispatched to.

**Written to files:** One file per generated asset, all under `<data_location>/drafts/YYYY-MM-DD-<source-slug>-<asset-n>.md`. Each file uses the frontmatter format matching its output type (text-post, carousel, poll) plus the three repurpose-batch linkage fields from step 7.

## Cross-workflow suggestions

- "Build a posting calendar from these assets?" → `content-calendar.md`
- "Generate companion comments for each asset?" → `companion-comments.md`

## Visual companion (v2+)

Visuals generated per asset via creators-studio integration when that module ships. No-op in v1.
