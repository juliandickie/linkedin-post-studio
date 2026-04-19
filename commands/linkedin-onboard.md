---
description: Create a new LinkedIn Post Studio profile or re-onboard an existing one
arguments:
  - name: profile-name
    description: Optional profile name; if omitted, the wizard asks
    required: false
  - name: section
    description: "Specific section to re-onboard: 'voice' | 'compliance' | 'audience'. If omitted, does full onboarding."
    required: false
---

Invoke the `linkedin-post-studio` skill to dispatch onboarding.

Input: `{{profile-name}}` and `{{section}}`.

Routing:

- If `{{section}}` is `voice` → dispatch to `skills/linkedin-post-studio/onboarding/voice-capture.md`
- If `{{section}}` is `compliance` → dispatch to `skills/linkedin-post-studio/onboarding/compliance-setup.md`
- If `{{section}}` is `audience` → resume `skills/linkedin-post-studio/onboarding/create-profile.md` at Step 3 (Collect audience)
- Otherwise → dispatch to `skills/linkedin-post-studio/onboarding/create-profile.md` (full wizard)

If `{{profile-name}}` is provided:
- For full onboarding, use it as the proposed `profile_id`
- For section-specific onboarding, use it to identify which existing profile to edit; ask the user to confirm before making changes
