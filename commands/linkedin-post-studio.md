---
description: Show LinkedIn Post Studio status, available profiles, recent drafts, and the full command menu
---

Invoke the `linkedin-post-studio` skill in help/status mode.

Show the user:

1. **Active profile**: read `~/.claude/data/linkedin-post-studio/config.md` for `default_profile`; display its name, industry, and voice status.
2. **All available profiles**: list every file under `~/Documents/LinkedIn Post Studio/profiles/` (respect `data_location` override from config.md). For each: profile_id, name, industry, voice.status, whether it's the current default.
3. **Recent drafts**: list the last 5 files in `~/Documents/LinkedIn Post Studio/drafts/` sorted by modification date. For each: filename, format, status.
4. **The 12 output types**: text-post, carousel, companion-comments, hook-variations, poll, video-script, newsletter, content-calendar, qa-review, idea-mining, repurpose, post-teardown.
5. **The 15 slash commands**:
   - `/linkedin-post-studio` — this help screen
   - `/linkedin-onboard` — create or re-onboard a profile
   - `/linkedin-profile` — manage profiles (list/switch/edit/delete/view)
   - `/linkedin-post` — generate a text post
   - `/linkedin-carousel` — generate a carousel brief
   - `/linkedin-hooks` — 15 hook variations
   - `/linkedin-companion` — 5 companion comment prompts
   - `/linkedin-poll` — generate a poll
   - `/linkedin-video` — 60–90s video script
   - `/linkedin-newsletter` — newsletter edition + promo post
   - `/linkedin-calendar` — content calendar (week or month)
   - `/linkedin-qa` — QA review on an existing draft
   - `/linkedin-mine` — mine post angles from a source
   - `/linkedin-repurpose` — convert long-form content to LinkedIn assets
   - `/linkedin-teardown` — analyze a viral post

Tell the user they can also invoke any of these via natural language (e.g., "write me a LinkedIn post about X") — the slash commands are shortcuts.
