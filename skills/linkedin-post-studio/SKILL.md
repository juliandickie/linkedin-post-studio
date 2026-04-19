---
name: linkedin-post-studio
description: Use when the user wants to create LinkedIn content — text posts, carousels, hooks, polls, video scripts, newsletters, content calendars, companion comments, draft QA reviews, post teardowns, content repurposing from newsletters/blogs/transcripts, or post idea mining from external sources. Triggers on phrases like "write a LinkedIn post", "draft a carousel", "generate hooks for", "linkedin newsletter", "review my linkedin draft", "ideas for linkedin", "repurpose my newsletter", "analyze this viral post", "linkedin content calendar", "post for [name]", or any /linkedin-* slash command. Profile-driven with built-in defenses against AI slop and industry-specific compliance support.
---

# LinkedIn Post Studio

Orchestrator for high-quality LinkedIn content. Dispatches to the right workflow, which loads only the references it needs. Every generation is filtered through Anti-AI constraints and the QA checklist before output.

## Dispatch flow

1. **Resolve active profile** (see Profile resolution below)
2. **Detect output type** from the user's request (see Output type dispatch table)
3. **Load the workflow file** and follow its instructions exactly
4. **Always apply** `references/anti-ai-constraint.md` (banned vocab, required elements)
5. **Always run** `references/qa-checklist.md` (pre-publish gate)
6. **Output** to chat AND write to `~/Documents/LinkedIn Post Studio/drafts/YYYY-MM-DD-<slug>.md` using `templates/draft-template.md`
7. **Suggest** cross-workflow next actions (see each workflow's "Cross-workflow suggestions" section)

## Profile resolution

1. Parse the user's request for a profile hint (`for IDD`, `as IDD`, `IDD post about`) — match against `profile_id` or `name` in any file under `~/Documents/LinkedIn Post Studio/profiles/`
2. If hint matches → use that profile
3. If no hint AND only one profile exists → use it silently
4. If no hint AND `config.md` has `default_profile` set → use the default
5. If no hint AND no default AND >1 profile exists → ask the user: "Which profile? 1) <a>, 2) <b>, 3) create new"
6. If no profile exists at all → trigger `onboarding/create-profile.md` immediately
7. If the selected profile is missing REQUIRED fields (name, industry, audience.primary_role, audience.pain_points, OR voice.archetype/adjectives) → trigger onboarding for just those fields

Respect the `data_location` field in `~/.claude/data/linkedin-post-studio/config.md` if present — it overrides the default `~/Documents/LinkedIn Post Studio/` path for all user data.

## Output type dispatch

| User says... | Workflow file |
|---|---|
| write/draft a post about X | `workflows/text-post.md` |
| carousel about X / carousel brief | `workflows/carousel.md` |
| hooks for X / generate hooks | `workflows/hook-variations.md` |
| companion comments / 5 comment prompts | `workflows/companion-comments.md` |
| poll about X | `workflows/poll.md` |
| video script / linkedin video for | `workflows/video-script.md` |
| newsletter / linkedin newsletter on | `workflows/newsletter.md` |
| content calendar / post plan for [period] | `workflows/content-calendar.md` |
| review/qa my draft | `workflows/qa-review.md` |
| ideas from [url/source] / mine ideas | `workflows/idea-mining.md` |
| repurpose my newsletter/blog/podcast/video | `workflows/repurpose.md` |
| teardown / analyze this post / why did this go viral | `workflows/post-teardown.md` |
| onboard / new profile / create profile | `onboarding/create-profile.md` |
| voice capture / add voice samples | `onboarding/voice-capture.md` |
| Ambiguous | Ask the user to clarify using the table above |

## Load-on-demand reference

`references/creator-playbooks.md` is NOT auto-loaded by any workflow. Load it only when:
- User explicitly references a creator ("how does Welsh do this?", "write more like Acosta")
- Onboarding voice-capture detects archetype ambiguity
- QA review is checking against a known creator's published pattern

## Universal post-processing

Every workflow's draft passes through these steps before output:

1. **Apply Anti-AI constraint** — load `references/anti-ai-constraint.md`, scan for banned vocabulary, banned structures; ensure all three required elements (specific proper noun/number, slightly awkward sentence, non-best-practice sentence) are present. Rewrite if needed.
2. **Run QA checklist** — load `references/qa-checklist.md`, evaluate every item. If any item fails, rewrite the affected section and re-run the full checklist.
3. **Output** — show the final post in chat AND write the draft file under `~/Documents/LinkedIn Post Studio/drafts/` using `templates/draft-template.md` as the frontmatter schema. Filename pattern: `YYYY-MM-DD-<slug>.md`.
4. **Offer cross-workflow suggestions** — the workflow file specifies which (e.g., after a text post, offer companion comments or a carousel variant).

## User data locations

- Profiles: `~/Documents/LinkedIn Post Studio/profiles/<profile_id>.md`
- Voice samples: `~/Documents/LinkedIn Post Studio/voice-samples/<profile_id>/`
- Drafts: `~/Documents/LinkedIn Post Studio/drafts/`
- Archive: `~/Documents/LinkedIn Post Studio/archive/`
- App config: `~/.claude/data/linkedin-post-studio/config.md` (contains `data_location` override, feature flags)

If `~/.claude/data/linkedin-post-studio/config.md` does not exist, create it during the first onboarding flow.

## Cross-references

- **Profile schema:** `templates/profile-template.md`
- **Draft schema:** `templates/draft-template.md`
- **Calendar schema:** `templates/calendar-template.md`
- **Voice profile schema (handoff):** `templates/voice-profile-template.md`
- **Onboarding:** `onboarding/create-profile.md`, `onboarding/voice-capture.md`, `onboarding/compliance-setup.md`
- **Workflows:** `workflows/` (12 files — one per output type)
- **References:** `references/` — `algorithm-mechanics.md`, `content-pillars.md`, `creator-playbooks.md` (on-demand), `engagement-tactics.md`, `ethics-failures.md`, `formatting-rules.md`, plus always-loaded `anti-ai-constraint.md` and `qa-checklist.md`
- **Hook library:** `references/hook-library/hook-index.md` + 12 category sub-files
- **Post structure:** `references/post-structure/post-structure-index.md` + 9 framework sub-files
- **Industry modules:** `references/industry/<industry>.md` — 12 shipped + `generic.md` fallback + `industry-template.md` for extensions
