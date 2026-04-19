---
# ============================================================================
# CONTENT CALENDAR TEMPLATE — written to
# <data_location>/drafts/YYYY-MM-DD-calendar-<week|month>.md
# by the content-calendar workflow.
# ============================================================================

title: "Content calendar — <profile_id> — <week|month> starting <YYYY-MM-DD>"
profile: <profile_id>
period: week                          # week | month
start_date: YYYY-MM-DD
end_date: YYYY-MM-DD

# Pillar mix (percentages — should sum to 100)
pillar_mix:
  Problems: 20
  Processes: 20
  Proof: 15
  Perspective: 15
  Personal: 15
  Participation: 15

# Format rotation — one per day, avoids same-format back-to-back penalty
format_rotation: [text-post, carousel, text-post, poll, text-post, video-script, text-post]

status: draft                         # draft | active | archived
created: YYYY-MM-DD
updated: YYYY-MM-DD
---

# Content calendar

## Week of YYYY-MM-DD (or month of YYYY-MM)

| Day | Pillar | Format | Topic | Hook category | Draft status |
|---|---|---|---|---|---|
| Mon | Problems | text-post | Why most practices underprice same-day dentistry | statistic | not started |
| Tue | Processes | carousel | The 5-step case acceptance framework | list | not started |
| Wed | Proof | text-post | Client case: $380K added in 12 months | achievement | not started |
| Thu | Perspective | poll | Biggest barrier to adding new procedures | question | not started |
| Fri | Personal | text-post | Walking away from the old practice model | story | not started |
| Sat | (off) | — | — | — | — |
| Sun | Participation | text-post | What's working for you in Q2? | question | not started |

## Pillar distribution check

- Problems: 1 slot (14%)
- Processes: 1 slot (14%)
- Proof: 1 slot (14%)
- Perspective: 1 slot (14%)
- Personal: 1 slot (14%)
- Participation: 1 slot (14%)
- (off): 1 slot

If any pillar is 0 slots or >30% of the week, adjust.

## Format distribution check

- text-post: 4
- carousel: 1
- poll: 1
- video-script: 1

Verify no same-format back-to-back pairs (algorithm penalizes this).

## Next actions

- [ ] Draft each post via `/linkedin-post` with the pillar + topic + hook category from the table
- [ ] Move drafts to `approved` status as you finalize
- [ ] Archive to `archive/` after posting (either manually or via `/linkedin-profile archive`)
- [ ] At end of period, review performance and populate `top_winning_posts` in profile for the "play the hits" workflow (v3)

## Notes

Freeform notes about the period: themes being tested, a product launch window, a
conference being attended, etc. Anything that informed the calendar design.
