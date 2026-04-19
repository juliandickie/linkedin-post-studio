---
title: Poll workflow
output_type: poll
last_updated: 2026-04-20
---

# Poll workflow

## When this workflow loads

Triggers on:

- "poll about X"
- "poll on X"
- "LinkedIn poll for X"
- `/linkedin-poll`

## Required references (loaded in this order)

1. `references/algorithm-mechanics.md` — poll performance multiplier (1.64x personal profiles), 7-day duration rule, 140-character question limit, LinkedIn prohibited sensitive data categories
2. `references/engagement-tactics.md` — poll design principles and audience fatigue guidance
3. `references/industry/<profile.industry>.md` — conditional; fall back to `references/industry/generic.md` if missing

## Required inputs

- **topic** — from request. If absent, ask: "What do you want the poll to explore?"
- **poll angle** (optional) — specific framing; if absent, infer from topic
- **profile** — resolved by SKILL.md before this workflow loads

## Generation steps

1. **Take input:** topic and optional poll angle.

2. **Sensitive data check.** LinkedIn prohibits polls on race, religion, politics, health conditions, and precise geolocation. If the topic touches a prohibited category, stop: "LinkedIn prohibits polls on this topic. Here's an alternative angle: [reframe]." Do not proceed.

3. **Draft context paragraph.** 140–300 characters. Sets up why the poll matters. Goes above the poll in the post.

4. **Draft poll question.** ≤140 characters.

5. **Draft 4 options.** Three substantive choices covering the realistic range, plus "Other / Just here for results" as option 4 (per §2 in `engagement-tactics.md`).

6. **Set duration: 7 days.** 1-day polls see approximately 80% reach reduction. Do not change unless the user explicitly requests otherwise.

7. **Frequency warning.** Check `<data_location>/drafts/` for poll files in the past 30 days. If more than 2 exist, warn: "2+ polls already this month — best practice is 2–3 maximum."

8. **Slug:** first 5 words of the poll question, lowercase, hyphens.

## Output format

**In chat:**

```
Context paragraph: <text>
Question: <question>
Options: A) <option> / B) <option> / C) <option> / D) Other / Just here for results
Duration: 7 days
```

**Written to file:** `<data_location>/drafts/YYYY-MM-DD-<slug>.md` using `templates/draft-template.md`.

Frontmatter: `profile`, `goal`, `format: poll`, `status: draft`, `created: today`, `updated: today`, `question: <text>`, `options: [array]`, `duration_days: 7`.

## Cross-workflow suggestions

- "Want a follow-up text post responding to likely results?" → `workflows/text-post.md`
- Note: "Max 2–3 polls per month for best results."

## Visual companion (v2+)

N/A for polls.
