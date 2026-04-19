---
title: Content calendar workflow
output_type: content-calendar
last_updated: 2026-04-20
---

# Content calendar workflow

## When this workflow loads

Triggers on:

- "content calendar for X"
- "post plan for this week/month"
- "plan my next 30 days"
- `/linkedin-calendar`

## Required references (loaded in this order)

1. `references/content-pillars.md` — six-pillar system, 13 archetypes, and goal-based pillar mixes
2. `references/creator-playbooks.md` — **Load-on-demand exception:** this workflow is one of the explicit load-on-demand trigger conditions for `creator-playbooks.md`. Load it here specifically for the batching practices section (Welsh, Alic, Acosta cadence guidance). Do not skip this reference.
3. `references/industry/<profile.industry>.md` — fall back to `references/industry/generic.md` if missing
4. `references/algorithm-mechanics.md` — format rotation rules to avoid the same-format back-to-back ranking penalty

## Required inputs

- **period** — week or month. Pull from the user's request ("this week", "next 30 days") or ask: "Are we planning a week or a month?"
- **pillar mix override** (optional) — if the user specifies proportions, use them; otherwise fall through to profile defaults
- **posting cadence** — from `profile.operations.posting_cadence`. If not set, ask: "How many posts per week are you targeting?"

## Generation steps

1. **Take input.** Confirm period and resolve posting cadence.

2. **Pull pillar mix.** Use `profile.operations.pillar_mix` if set. If not set, apply goal-based defaults from `content-pillars.md`:
   - `lead-gen` default: 30% Personal, 20% Proof, 20% Problem, 10% Process, 10% Perspective, 10% Promotion
   - `thought-leadership` default: 30% Perspective, 30% Personal, 20% Process, 10% Proof, 10% Problem, 0% Promotion
   - Adjust proportions for other goals using the goal-based mixes table in `content-pillars.md`

3. **Calculate post slots:**
   - Week: 5–7 slots total, capped by `posting_cadence` (default 3 posts/week if not set)
   - Month: 12–20 slots total, based on posting_cadence × 4 weeks

4. **Assign pillar per slot.** Distribute slots to respect the mix percentages. Round-robin across pillars in each week to avoid pillar clusters.

5. **Assign format per slot.** Rotate formats to avoid the same-format back-to-back penalty per `algorithm-mechanics.md`. Recommended base rotation: text → carousel → text → poll → text → video → text. Adjust for what the profile produces.

6. **Suggest topic per slot:**
   - Pull from `profile.top_winning_posts` to seed "play the hits" repeats or updated takes, if any are recorded
   - For empty slots, use idea categories from `content-pillars.md` §4 (10 myths in my niche, 10 mistakes I made, 10 frameworks I use, client questions I keep getting, etc.)
   - Tailor suggestions to the industry file

7. **Suggest hook category per slot.** Pair each slot with a hook category appropriate for the pillar and format assigned.

8. **Apply batching practices** from `creator-playbooks.md`. Welsh-style batching means writing 5–7 posts in a single sitting scheduled across the week. Alic and Acosta cadence guidance covers the optimal gap between high-performing post types (e.g., do not schedule two "hot take" posts back-to-back in the same week). Note any batching flags in the calendar's draft column.

9. **Compile the calendar** using the `templates/calendar-template.md` schema.

## Output format

**In chat:** Grid view of the calendar with columns: Day | Pillar | Format | Topic | Hook category | Draft status. Each row is one post slot. Week plans show Mon–Fri (or Mon–Sun if cadence is daily). Month plans group by week.

**Written to file:** `<data_location>/drafts/YYYY-MM-DD-calendar-<week|month>.md` using `templates/calendar-template.md`; frontmatter: `format: calendar`, `status: draft`, `period`, `posting_cadence`, `pillar_mix_used`.

## Cross-workflow suggestions

- "Draft the first post from this calendar now?" → `text-post.md`
- "Mine ideas to populate any empty topics?" → `idea-mining.md`

## Visual companion (v2+)

Not applicable for calendars.
