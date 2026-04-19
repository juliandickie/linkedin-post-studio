---
name: linkedin-onboard
description: Create a new LinkedIn Post Studio profile or re-onboard an existing one
disable-model-invocation: true
argument-hint: "[profile-name] [section]"
---

Invoke the `linkedin-post-studio` orchestrator to dispatch onboarding.

Inputs (positional):
- `$1` — optional profile-name: if omitted, the wizard asks
- `$2` — optional section: `voice` | `compliance` | `audience`; if omitted, runs full onboarding

Routing:

- If `$2` is `voice` → follow `../linkedin-post-studio/onboarding/voice-capture.md`
- If `$2` is `compliance` → follow `../linkedin-post-studio/onboarding/compliance-setup.md`
- If `$2` is `audience` → resume `../linkedin-post-studio/onboarding/create-profile.md` at Step 3 (Collect audience)
- Otherwise → follow `../linkedin-post-studio/onboarding/create-profile.md` (full wizard)

If `$1` is provided:
- For full onboarding, use it as the proposed `profile_id`
- For section-specific onboarding, use it to identify which existing profile to edit; ask the user to confirm before making changes
