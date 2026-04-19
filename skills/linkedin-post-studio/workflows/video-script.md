---
title: Video script workflow
output_type: video-script
last_updated: 2026-04-20
---

# Video script workflow

## When this workflow loads

Triggers on:

- "video script for X"
- "LinkedIn video about X"
- "60-second script on X"
- `/linkedin-video`

## Required references (loaded in this order)

1. `references/post-structure/post-structure-index.md` — hook rules for the first 3 seconds
2. `references/formatting-rules.md` — caption specs and thumbnail specs
3. `references/engagement-tactics.md` — video retention and watch-time tactics
4. `references/industry/<profile.industry>.md` — conditional; fall back to `references/industry/generic.md` if missing

## Required inputs

- **topic** — from request. If absent, ask: "What do you want the video to cover?"
- **length preference** (optional) — 15s / 60s / 90s; default is 60–90 seconds. Note: under-15s performs exceptionally well for short-form, so surface this option if the topic suits it.
- **profile** — resolved by SKILL.md before this workflow loads

## Generation steps

1. **Take input:** topic and optional length preference. Apply the 60–90 second default if none given.

2. **First 3 seconds (hook).** This window drives approximately 70% of viewer retention. Use one of:
   - A specific promise: "In 47 seconds, I'll show you exactly how to..."
   - A direct question aimed at the viewer's pain
   - A bold claim backed by a named detail

3. **Script sections with timing:**
   - **Hook (0–3s):** Pattern interrupt — one of the three forms above
   - **Setup (3–15s):** Why this matters now, who it's for
   - **Content (15–60s):** The core argument, method, or story — follow the chosen framework from `post-structure-index.md`
   - **CTA (60–90s):** One direct ask, consistent with the goal from the profile's `default_goal`

4. **Caption plan.** 85% of LinkedIn videos are watched without sound initially — captions are mandatory, not optional. Spec:
   - ≤42 characters per caption line
   - 1–2 lines on screen at a time
   - 2–4 seconds per caption block
   - White text on a semi-transparent black background, anchored to the lower third

5. **Custom thumbnail spec.** Dimensions: 1920×1080. Suggest a specific image concept: what to shoot, what text overlay to use, whether to include a face.

6. **Post caption.** 500–800 characters. Earns the click and teases the payoff without giving it away. No spoilers of the main takeaway.

7. **Technical reference (for user).** MP4, H.264 codec, 1080p, ≤200MB, 30fps standard.

8. **Compliance check.** If `profile.compliance.required_disclaimers` is non-empty, note where disclaimers appear in the script (typically the end of the Content section or the CTA).

9. **Slug:** first 5 words of the hook line, lowercase, hyphens.

## Output format

**In chat:** Full time-coded script, followed by caption blocks with timing, then thumbnail suggestion, then post caption:

```
[0–3s] <hook text>
[3–15s] <setup text>
[15–60s] <content text>
[60–90s] <CTA>

Caption blocks:
[0–3s] Line 1 / Line 2
...

Thumbnail: <concept description>

Post caption:
<caption text>
```

**Written to file:** `<data_location>/drafts/YYYY-MM-DD-<slug>.md` using `templates/draft-template.md`.

Frontmatter: `profile`, `goal`, `format: video-script`, `framework_used`, `status: draft`, `created: today`, `updated: today`. Add video-specific fields: `duration_sec: <number>`, `thumbnail_spec: <one-line description>`. Body contains the time-coded script and the post caption.

## Cross-workflow suggestions

- "Convert the script to a carousel for variety?" → `workflows/carousel.md`
- "Want a text post announcing the video when it's ready?" → `workflows/text-post.md`

## Visual companion (v2+)

When creators-studio integration ships, render the script with AI voice and visuals. No-op in v1.
