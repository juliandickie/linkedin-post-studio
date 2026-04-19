---
title: Text post workflow
output_type: text-post
last_updated: 2026-04-20
---

# Text post workflow

## When this workflow loads

Triggers on:

- "write a post about X" or "draft a post about X"
- "LinkedIn post about X"
- "generate a post on X"
- `/linkedin-post`

Default workflow when the user asks for LinkedIn content without specifying a format. When output type is ambiguous, dispatch here first.

## Required references (loaded in this order)

1. `references/post-structure/post-structure-index.md`
2. 1–2 framework files from `references/post-structure/framework-*.md` — selection based on goal (see Generation steps)
3. `references/hook-library/hook-index.md`
4. 1–3 hook category files from `references/hook-library/hook-*.md` — selection based on goal and profile voice archetype
5. `references/formatting-rules.md`
6. `references/industry/<profile.industry>.md` — conditional; fall back to `references/industry/generic.md` if the industry file is missing
7. `references/content-pillars.md` — for pillar selection and goal-based balancing mix

## Required inputs

- **topic** — from the user's request. If absent, ask: "What topic or angle do you want to write about?"
- **goal** — from an explicit request override first, then `profile.default_goal`. If `profile.default_goal` is null and no override exists, ask: "Which goal? lead-gen | thought-leadership | brand-awareness | community"
- **profile** — resolved by SKILL.md before this workflow loads
- **pillar** (optional) — inferred from goal via `content-pillars.md` §"Balancing pillars for different goals" unless the user specifies one

## Generation steps

1. **Determine goal.** Request override → `profile.default_goal` → ask.

2. **Pick pillar.** Use the pillar mix table in `content-pillars.md` §"Balancing pillars for different goals". Use user-specified pillar if provided.

3. **Pick framework based on goal:**
   - `lead-gen` → PAS or AIDA. Load `framework-pas.md`; optionally also `framework-aida.md`.
   - `thought-leadership` → SLAY. Load `framework-slay.md`.
   - `brand-awareness` → BAB, STAR, or SLAY. Load `framework-bab.md`; optionally also `framework-star.md`.
   - `community` → Hook-Story-Offer. Load `framework-hook-story-offer.md`.

4. **Pick hook categories.** Consult `hook-index.md` for the goal-and-archetype mapping. Load 1–3 matching `hook-*.md` files.

5. **Draft the hook.** 1–3 lines. Constraints per Chris Donnelly:
   - Line 1: ≤62 mobile characters
   - Line 2: ≤62 mobile characters
   - Line 3 (if used): ≤50 mobile characters
   - Total: ≤140 mobile characters
   - No emoji. Banned openers: "Unpopular opinion", "I was today years old when", plus any flagged in `anti-ai-constraint.md`.

6. **Draft the body.** Target 800–1,000 characters (sweet spot per `algorithm-mechanics.md`). Paragraphs of 1–3 sentences, blank line between every paragraph. If body exceeds 1,500 characters, use ≥14 paragraphs across hook and body combined.

7. **Draft the CTA.** One CTA only — no stacking. Style per `profile.operations.default_cta_style`. Align with goal:
   - `lead-gen` → DM keyword prompt
   - `thought-leadership` → save or share ask
   - `brand-awareness` → comment prompt
   - `community` → open question

8. **Append disclaimers.** If `profile.compliance.required_disclaimers` is non-empty, append each after the CTA on its own line.

9. **Generate slug.** First 5 words of hook line 1, lowercase, hyphens, no punctuation. Example: "3 things I got wrong about pricing" → `3-things-i-got-wrong`.

## Output format

**In chat:** Full post text formatted as it should appear on LinkedIn (blank lines between paragraphs). Below it, a brief generation summary:

```
Hook category: <category>
Framework: <framework>
Pillar: <pillar>
Goal: <goal>
```

**Written to file:** `<data_location>/drafts/YYYY-MM-DD-<slug>.md` using `templates/draft-template.md`.

Frontmatter fields to populate: `profile`, `goal`, `format: text-post`, `framework_used`, `hook_category`, `pillar`, `status: draft` (or `needs-approval` if `profile.compliance.pre_approval_required` is true), `created: today`, `updated: today`, `performance:` all null.

**Export offer:** If `config.features.word_pdf_export: true`, ask: "Export to Word or PDF?" If yes, dispatch to `anthropic-skills:docx` or `anthropic-skills:pdf`.

## Cross-workflow suggestions

- "Want 5 companion comment prompts for this theme?" → `workflows/companion-comments.md`
- "Convert to a carousel?" → `workflows/carousel.md`
- "Suggest 2 other post angles on this topic?" → `workflows/hook-variations.md`

## Visual companion (v2+)

When creators-studio integration ships, offer to generate a matching image with faces, text overlay, and brand colors from the profile. No-op in v1.
