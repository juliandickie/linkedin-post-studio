---
# ============================================================================
# DRAFT TEMPLATE — the skill uses this frontmatter when writing drafts to
# <data_location>/drafts/YYYY-MM-DD-<slug>.md
# Field values are populated by the workflow that generated the draft.
# ============================================================================

# ---------------- Draft metadata ----------------
profile: <profile_id>                 # e.g., julian — matches a file in profiles/
goal: <goal>                          # lead-gen | thought-leadership | brand-awareness | community
format: <format>                      # text-post | carousel | poll | video-script | newsletter | hook-menu | idea-list | calendar | teardown
framework_used: <framework>           # e.g., PAS, SLAY, BAB; "n/a" for formats where framework doesn't apply
hook_category: <category>             # e.g., contrarian, statistic, story; "n/a" where not applicable
pillar: <pillar>                      # Problems | Processes | Proof | Perspective | Personal | Participation
status: draft                         # draft | needs-approval | approved | scheduled | posted | archived
created: YYYY-MM-DD
updated: YYYY-MM-DD
scheduled_for: null                   # ISO timestamp if scheduled, otherwise null

# ---------------- Performance tracking ----------------
# Manual in v1. Automated via API integration in v3.
performance:
  impressions: null
  reactions: null
  comments: null
  shares: null
  saves: null
  posted_at: null                     # ISO timestamp when actually published
  link: null                          # LinkedIn post URL once published

# ---------------- Generation metadata ----------------
# For repurpose/idea-mining workflows — track provenance.
source_content: null                  # null, or a short description of source if repurposed
source_url: null                      # null, or the source URL
repurpose_batch: null                 # null, or YYYY-MM-DD if part of a repurpose batch
---

# Draft: <slug>

## Post text

<The generated post, ready to copy-paste into LinkedIn. Preserve line breaks exactly
as they should appear — LinkedIn renders blank lines as paragraph separators.>

## Companion comment prompts

<Populated by the companion-comments workflow, or appended here when the user runs
that workflow on this draft. Five prompts per the §8 pattern: opinion, re-frame,
data-contribution, question-starter, respectful-disagreement.>

1. <prompt 1>
2. <prompt 2>
3. <prompt 3>
4. <prompt 4>
5. <prompt 5>

## Notes

<Anything from the workflow worth preserving — rationale for framework choice,
alternative hooks considered, compliance disclaimers applied, QA checklist items
that needed rewriting and why, cross-workflow suggestions offered.>
