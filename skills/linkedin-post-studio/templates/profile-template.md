---
# ============================================================================
# PROFILE TEMPLATE — copy this file to ~/Documents/LinkedIn Post Studio/profiles/<slug>.md
# and fill in the values below. Fields are marked REQUIRED, RECOMMENDED, or OPTIONAL.
# Delete the `# REQUIRED` etc. comments after filling in to keep the file clean.
# ============================================================================

# ---------------- METADATA (auto-managed by the skill) ----------------
profile_id: <slug>                  # REQUIRED — filename slug, used for context inference (lowercase, hyphens)
profile_type: personal              # REQUIRED — personal | company | client
created: 2026-04-20                 # REQUIRED — YYYY-MM-DD
updated: 2026-04-20                 # REQUIRED — auto-updated by the skill on changes
schema_version: 1.0

# ---------------- IDENTITY ----------------
name: <Full Name>                   # REQUIRED — the name used for third-person reference ("What IDD says...")
positioning: ""                     # RECOMMENDED — one-sentence positioning, e.g., "Helping dental practices add same-day dentistry profitably"
industry: generic                   # REQUIRED — maps to references/industry/<industry>.md
# Supported industries: b2b-saas, professional-services, creator-economy, ecommerce,
# healthcare, legal, finance, real-estate, manufacturing, energy-utilities,
# dental-education, generic
niche: ""                           # OPTIONAL — sub-specialty, e.g., "same-day dentistry training"

# ---------------- AUDIENCE ----------------
audience:
  primary_role: ""                  # REQUIRED — e.g., "dental practice owner"
  seniority: ""                     # OPTIONAL — e.g., "business owner", "VP", "IC"
  sophistication: intermediate      # RECOMMENDED — beginner | intermediate | expert
  pain_points:                      # REQUIRED — at least 1, ideally 3-5
    - ""
    - ""
    - ""
  hangouts: []                      # OPTIONAL — where your audience congregates online (subreddits, newsletters, podcasts)

# ---------------- VOICE ----------------
voice:
  status: missing                   # REQUIRED — missing | partial | complete
  archetype: Operator               # RECOMMENDED — Visionary | Operator | Processor (see creator-playbooks.md on-demand)
  adjectives: []                    # RECOMMENDED — 3-5 adjectives, e.g., [direct, evidence-based, practical, dry-witted]
  emoji_policy: minimal             # RECOMMENDED — none | minimal | moderate
  sentence_rhythm: medium-balanced  # OPTIONAL — short-staccato | medium-balanced | long-flowing
  banned_phrases:                   # RECOMMENDED — starts with AI-slop defaults; add your own
    - delve
    - dive deep
    - unlock
    - leverage                      # as verb
    - synergy
    - journey
    - tapestry
    - testament
    - ever-evolving
    - resonate
  signature_phrases: []             # OPTIONAL — phrases you reuse ("the math doesn't lie", "what I see in 50+ practices")
  voice_samples_path: ""            # OPTIONAL — path to a folder of past posts, e.g., "~/Documents/LinkedIn Post Studio/voice-samples/<slug>/"
  voice_samples_inline: 0           # OPTIONAL — count of samples pasted inline in the body below

# ---------------- GOALS ----------------
goals_supported: [lead-gen, thought-leadership, brand-awareness, community]
default_goal: lead-gen              # used when a post-time goal is not specified

# ---------------- COMPLIANCE (conditional — populate if industry is regulated) ----------------
compliance:
  required: false                   # auto-set from industry mapping (true if regulated)
  required_disclaimers: []          # e.g., ["General educational content, not medical advice."]
  pre_approval_required: false      # if true, drafts are written with status: needs-approval
  topic_red_lines: []               # topics you will never post about (pending litigation, specific clients, competitors)

# ---------------- OPERATIONS (optional) ----------------
operations:
  posting_cadence: 3-per-week       # informs content-calendar generation
  preferred_formats: [text, carousel]
  default_cta_style: dm-keyword     # dm-keyword | link-comment | soft-close | hard-cta
  top_winning_posts: []             # paths to past hits (manual in v1; automated in v3)
---

# Voice samples

Paste your best 3–15 past LinkedIn posts here, each under its own heading. The more
samples, the better the generator will match your voice. Include date and rough
performance where known — the skill uses these as signals.

## Sample 1 — "<Short descriptive title>" (<YYYY-MM-DD>, <N>K impressions)

<Full post text, exactly as published. Preserve line breaks and formatting.>

## Sample 2 — "<title>" (<date>, <perf>)

<Full post text>

## Sample 3 — ...

# Notes

Freeform notes. Anything that doesn't fit the frontmatter goes here:

- Voice quirks: e.g., "I avoid the word 'transformation' — sounds preachy"
- Preferred framings: e.g., "I prefer concrete dollar figures over percentages"
- Closing habits: e.g., "Never end with 'Thoughts?'"
- Reference material: e.g., "I worked at Practice X from 2018–2022; often reference that experience"
- Employer disclaimer: e.g., "The opinions here are my own, not those of [employer]"
- Banned phrases with rationale: e.g., "Don't use 'journey' — feels performative in my niche"
