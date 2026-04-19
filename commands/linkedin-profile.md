---
description: Manage LinkedIn Post Studio profiles (list, switch, edit, delete, view)
arguments:
  - name: action
    description: "list | switch | edit | delete | view. Defaults to 'list' if omitted."
    required: false
  - name: profile-name
    description: "Profile ID (for switch, edit, delete, view actions)"
    required: false
---

Invoke the `linkedin-post-studio` skill in profile management mode.

Action semantics (if `{{action}}` is not specified, default to `list`):

- **`list`** — Read every file under `~/Documents/LinkedIn Post Studio/profiles/` (respect `data_location` override from `~/.claude/data/linkedin-post-studio/config.md`). Show a table: profile_id, name, industry, voice.status, default? (yes/no).
- **`switch {{profile-name}}`** — Update `default_profile` in `config.md` to the specified profile_id. Confirm before writing. Verify the target profile file exists.
- **`edit {{profile-name}}`** — Ask the user: "Which section? (identity | audience | voice | compliance | operations)". Then open the profile file for direct editing OR resume `onboarding/create-profile.md` at the relevant step for guided edits.
- **`delete {{profile-name}}`** — Ask for confirmation (user must type the profile name). Then MOVE the file to `~/Documents/LinkedIn Post Studio/profiles/archive/` (create directory if missing). Never permanently delete. If the deleted profile was the default, clear `default_profile` in config.md.
- **`view {{profile-name}}`** — Print the full profile file contents to chat for inspection.

If `{{profile-name}}` is missing for a non-`list` action, ask the user which profile to act on.
