---
name: linkedin-profile
description: Manage LinkedIn Post Studio profiles (list, switch, edit, delete, view)
disable-model-invocation: true
argument-hint: "[list|switch|edit|delete|view] [profile-name]"
---

Invoke the `linkedin-post-studio` orchestrator in profile management mode.

Inputs (positional):
- `$1` — action: `list` | `switch` | `edit` | `delete` | `view`. Defaults to `list` if omitted.
- `$2` — profile-name: required for `switch`, `edit`, `delete`, `view`. Ask the user if missing.

Action semantics:

- **`list`** — Read every file under `~/Documents/LinkedIn Post Studio/profiles/` (respect `data_location` override from `~/.claude/data/linkedin-post-studio/config.md`). Show a table: profile_id, name, industry, voice.status, default? (yes/no).
- **`switch $2`** — Update `default_profile` in `config.md` to the specified profile_id. Confirm before writing. Verify the target profile file exists.
- **`edit $2`** — Ask the user: "Which section? (identity | audience | voice | compliance | operations)". Then open the profile file for direct editing OR resume `../linkedin-post-studio/onboarding/create-profile.md` at the relevant step for guided edits.
- **`delete $2`** — Ask for confirmation (user must type the profile name). Then MOVE the file to `~/Documents/LinkedIn Post Studio/profiles/archive/` (create directory if missing). Never permanently delete. If the deleted profile was the default, clear `default_profile` in config.md.
- **`view $2`** — Print the full profile file contents to chat for inspection.

If `$2` is missing for a non-`list` action, ask the user which profile to act on.
