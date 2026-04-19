---
title: Create profile (onboarding quick-start)
purpose: Walk a user through creating a new profile in ~5 minutes
last_updated: 2026-04-20
---

# Create profile wizard

**When to run:**
- First-time user (no profile exists in `~/Documents/LinkedIn Post Studio/profiles/`)
- User explicitly asks: "onboard me", "create a new profile", "/linkedin-onboard"
- Dispatch from `SKILL.md` when no profile exists and a generation request arrives

**Output:** A new profile file at `<data_location>/profiles/<profile_id>.md`, plus an initialized `~/.claude/data/linkedin-post-studio/config.md` on first run.

## Prerequisites

- Template to copy: `templates/profile-template.md`
- Default data location: `~/Documents/LinkedIn Post Studio/` — check for user override in `~/.claude/data/linkedin-post-studio/config.md` `data_location` field

## Steps

### Step 1 — Confirm data location

If `~/.claude/data/linkedin-post-studio/config.md` does not exist, create it with these default contents:

```yaml
---
default_profile: null
data_location: ~/Documents/LinkedIn Post Studio/
features:
  online_idea_mining: true
  word_pdf_export: true
  performance_tracking: false
---

# Notes

(Freeform user notes about their LinkedIn Post Studio setup.)
```

Tell the user:

> "I'll store your profiles and drafts at `~/Documents/LinkedIn Post Studio/`. This is easy to find via Finder or Spotlight. Want to use a different location (e.g., a synced Dropbox folder for team sharing)?"

- If user accepts the default → continue.
- If user specifies an override → update `data_location` in `config.md`, create the specified folder, and ensure `profiles/`, `voice-samples/`, `drafts/`, `archive/` subdirectories exist inside it.

### Step 2 — Collect identity

Ask ONE question at a time. Do not batch.

1. **"Are you setting this up for yourself, your company, or a client?"** → sets `profile_type: personal | company | client`.
2. **"What's the name?"** → sets `name`.
3. **"Short identifier (filename slug)?"** Default to a slugified version of the name (lowercase, hyphens). Check for collisions against existing files in the profiles directory. If a collision, ask the user to choose a new slug or confirm overwrite. → sets `profile_id`.
4. **"What industry?"** Offer multiple choice from the 12 shipped industries:
   - b2b-saas
   - professional-services
   - creator-economy
   - ecommerce
   - healthcare
   - legal
   - finance
   - real-estate
   - manufacturing
   - energy-utilities
   - dental-education
   - other (→ fallback to `generic`)

   → sets `industry`. If "other", set to `generic` and note the actual industry in the profile body under "## Notes".

5. **"Niche or sub-specialty?"** (optional) → sets `niche`. If skipped, leave blank.
6. **"One-sentence positioning?"** (recommended but optional) → sets `positioning`. Example prompt to help: "Who you help, with what, toward what outcome."

### Step 3 — Collect audience

Ask one question at a time:

1. **"What's your primary audience role?"** (e.g., "dental practice owner", "Series B SaaS founder", "VP of Marketing at a $50M agency") → `audience.primary_role`.
2. **"Seniority level?"** (optional — business owner, VP, director, manager, IC) → `audience.seniority`.
3. **"Sophistication level?"** (beginner / intermediate / expert) → `audience.sophistication`. Default to `intermediate` if unsure.
4. **"What are the top 3 pain points your audience has?"** Ask for ≥1; 3–5 ideal. → `audience.pain_points` (array).
5. **"Where does your audience hang out online?"** (optional — subreddits, newsletters, podcasts, Slack communities) → `audience.hangouts`.

### Step 4 — Confirm goals

Tell the user:

> "You'll pick a goal per-post from: lead-gen, thought-leadership, brand-awareness, community. Which is your most common default?"

→ sets `default_goal`. Confirm all four remain available in `goals_supported`.

### Step 5 — Regulated industry check

If `industry` is in the regulated set: `healthcare`, `legal`, `finance`, `real-estate`, `manufacturing`, `energy-utilities`, `dental-education`:

Tell the user:

> "Your industry (<industry>) has specific compliance requirements. I'll walk you through setting them up now (~5 min)."

Dispatch to `onboarding/compliance-setup.md`. When it returns, continue with Step 6.

Otherwise, set `compliance.required: false` and skip to Step 6.

### Step 6 — Voice capture offer

Tell the user:

> "Voice capture takes about 15 minutes and dramatically improves generation quality. You can do it now, or defer and proceed with industry-inferred defaults (you'll get a warning on each generation reminding you to complete it). Which do you prefer?"

- **If "now"** → dispatch to `onboarding/voice-capture.md`. When it returns, continue with Step 7.
- **If "defer"** → set `voice.status: missing`. Load the industry's `voice_defaults` from `references/industry/<industry>.md` and copy them into the profile's `voice:` block. Tell the user:

  > "I'll use industry-inferred defaults for now. Your posts will be technically sound but won't sound distinctly like you. Run `/linkedin-onboard voice` when you're ready (takes 15 min)."

### Step 7 — Write the profile file

Copy `templates/profile-template.md` to `<data_location>/profiles/<profile_id>.md`. Fill in every frontmatter field from Steps 2–6. Set:

- `created` and `updated` to today's date (YYYY-MM-DD)
- `schema_version: 1.0`
- `goals_supported: [lead-gen, thought-leadership, brand-awareness, community]`

If voice was deferred, the `voice:` block uses industry defaults with `status: missing`.

Write the profile file. Preserve the body sections (Voice samples, Notes) from the template — they're empty placeholders the user can fill in later.

### Step 8 — Default profile handling

Read `config.md` `default_profile`:

- **If null** (no default yet) → set `default_profile: <profile_id>` in `config.md`. Tell the user: "This is now your default profile."
- **If already set** → ask: "Make this your new default? (y/n)"
  - If yes → update `default_profile` in `config.md`.
  - If no → leave the existing default alone.

### Step 9 — Confirm

Show the user:

- Path to the new profile file
- Summary of what was captured (name, industry, goal, voice status)
- What they can do next:
  - `/linkedin-post <topic>` — generate a text post
  - `/linkedin-onboard voice` — complete voice capture (if deferred)
  - `/linkedin-profile edit <profile_id>` — edit fields later

If voice was deferred, remind them to complete it for best quality.

### Step 10 — Resume original request (if any)

If onboarding was triggered mid-request (e.g., user asked "write me a LinkedIn post about X" and no profile existed), return to that request now with the new profile as context. Dispatch to the appropriate workflow per `SKILL.md` Output type dispatch table.

## Error handling

- **Profile ID collision** → ask user to choose a new slug or confirm overwrite. Never silently overwrite.
- **Data location not writable** → tell user the path failed, ask for an alternate path, update `config.md` accordingly.
- **User aborts midway** → write a partial profile with `voice.status: missing` and note in body which steps were skipped. Tell the user how to resume (`/linkedin-onboard <profile_id> --resume`).

## Notes for contributors

When a new industry is added to the project, update Step 2's industry list here AND register it in `docs/adding-industries.md`. Failure to register here means new industries will be invisible to the onboarding flow.
