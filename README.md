<p align="center">
  <img src="assets/icon-256.png" alt="LinkedIn Post Studio icon" width="128" height="128">
</p>

# LinkedIn Post Studio

Profile-driven LinkedIn content generation built on a comprehensive 2025–2026 LinkedIn knowledge base. Generates text posts, carousels, hooks, polls, video scripts, newsletters, calendars, companion comments, and more — in YOUR voice, with built-in defenses against AI slop.

## What it does

- **12 output types** — text posts, carousels, hook variations, companion comments, polls, video scripts, newsletters, content calendars, QA reviews, idea mining, content repurposing, post teardowns
- **Profile-driven** — captures your voice once (6 methods including macOS/iPhone dictation, Whisper, paste), reuses across every generation
- **Industry-aware** — 12 shipped industry modules with voice defaults and compliance rules (healthcare HIPAA, legal ABA, finance SEC/FINRA, and more)
- **Anti-AI-slop** — every draft passes through banned-vocabulary, banned-structure, and required-element checks before output
- **Local-first** — your data stays on your machine; no analytics, no cloud sync (unless you point `data_location` at a synced folder)

## Why it's different

- **Voice preservation over templates** — we capture how you actually write; we don't apply a template to your topic
- **Compliance built in** — regulated industries get proper disclosures; no retrofitting disclaimer text
- **Always-on QA** — every generation runs a pre-publish checklist regardless of workflow; nothing ships without passing

## Where it works

| Surface | Skill (natural language) | Full plugin (slash commands) |
|---|---|---|
| **Claude Code** (terminal)       | ✅ | ✅ |
| **Claude Desktop** — code mode   | ✅ | ✅ |
| **Claude Desktop** — chat mode   | ✅ | ❌ |
| **Claude Web** (claude.ai)       | ✅ | ❌ |
| **Cowork**                       | ✅ | ✅ |

**Full plugin** gives you 15 slash commands and profile management UX. **Skill-only** gives you full generation capability via natural language — just say "write me a LinkedIn post about X."

## Installation

### Option A — Marketplace install (recommended, Claude Code / Desktop code mode / Cowork)

This repo ships its own Claude Code plugin marketplace, so you get one-line install and one-line updates:

```bash
# Inside Claude Code (or Desktop code mode / Cowork)
/plugin marketplace add juliandickie/linkedin-post-studio
/plugin install linkedin-post-studio@idd-plugins
```

To update later:

```bash
/plugin marketplace update idd-plugins
/plugin update linkedin-post-studio
```

Both Claude Code commands also work in non-interactive mode from your shell:

```bash
claude plugin marketplace add juliandickie/linkedin-post-studio
claude plugin install linkedin-post-studio@idd-plugins
```

### Option B — Manual git clone (Claude Code / Desktop code mode / Cowork)

If you'd rather manage the install with `git` directly:

```bash
cd ~/.claude/plugins/
git clone https://github.com/juliandickie/linkedin-post-studio.git
```

All 15 slash commands and the skill are auto-discovered. To update, `cd` into the cloned directory and `git pull`.

### Option C — Skill only (Claude Web / Desktop chat mode)

```bash
# Copy the skill directory
cp -r linkedin-post-studio/skills/linkedin-post-studio ~/.claude/skills/

# Or symlink for automatic updates when you git pull
ln -sfn "$(pwd)/linkedin-post-studio/skills/linkedin-post-studio" ~/.claude/skills/linkedin-post-studio
```

No slash commands, but the skill triggers on natural language in any Claude surface.

### Option D — Project-scoped (Claude Code only)

For users who want the plugin only for one project (e.g., an agency working on a single client):

```bash
cd /path/to/your-project
mkdir -p .claude/plugins/
git clone https://github.com/juliandickie/linkedin-post-studio.git .claude/plugins/linkedin-post-studio
```

Or, project-scoped via the marketplace (auto-prompts teammates to install it when they trust the project):

```jsonc
// .claude/settings.json
{
  "extraKnownMarketplaces": {
    "idd-plugins": {
      "source": { "source": "github", "repo": "juliandickie/linkedin-post-studio" }
    }
  },
  "enabledPlugins": {
    "linkedin-post-studio@idd-plugins": true
  }
}
```

### ⚠️ Restart required after install

Claude loads plugins and skills at startup, not on the fly. **After installing (or updating) the plugin, restart your Claude surface** so the 15 slash commands and the skill show up:

- **Claude Desktop** — fully quit the app (⌘Q on macOS) and relaunch
- **Claude Code** (terminal) — exit your current session and start a new one
- **Claude Web** — reload the browser tab
- **Cowork** — restart the Cowork session

If you install the plugin and type `/linkedin-` and see no auto-complete suggestions, you haven't restarted yet. After restart, typing `/linkedin-` should show all 15 commands, and natural language like "write me a LinkedIn post about pricing strategy" should trigger the orchestrator.

## First-time setup (5 minutes)

On first invocation, the skill walks you through onboarding:

1. **Identity** — name, profile type (personal / company / client), industry
2. **Audience** — primary role, pain points, sophistication level
3. **Goals** — default goal (lead-gen / thought-leadership / brand-awareness / community)
4. **Compliance** — only runs for regulated industries; loads defaults and lets you customize
5. **Voice capture** (optional, deferrable) — 15 min to capture your voice from past posts; defer with a quality warning if you prefer

The onboarding offers 6 voice-capture methods (see below).

## Commands

| Command | Purpose |
|---|---|
| `/linkedin-post-studio` | Show status, profiles, recent drafts, full command menu |
| `/linkedin-onboard` | Create a new profile or re-onboard an existing one |
| `/linkedin-profile` | Manage profiles (list, switch, edit, delete, view) |
| `/linkedin-post` | Generate a text post (800–1,000 chars) |
| `/linkedin-carousel` | Generate a carousel brief (6–10 slides) |
| `/linkedin-hooks` | Generate 15 hook variations mixing categories |
| `/linkedin-companion` | Generate 5 companion comment prompts on a theme |
| `/linkedin-poll` | Generate a poll (3 options + "Other", 7-day) |
| `/linkedin-video` | Generate a 60–90s video script with caption plan |
| `/linkedin-newsletter` | Generate a newsletter edition + promo post |
| `/linkedin-calendar` | Generate a content calendar (week or month) |
| `/linkedin-qa` | Run QA checklist on an existing draft |
| `/linkedin-mine` | Mine post angles from a source (Reddit, reviews, transcripts) |
| `/linkedin-repurpose` | Convert long-form content into multiple LinkedIn assets |
| `/linkedin-teardown` | Analyze a viral post + generate your version |

## Voice capture methods

The more samples, the better the output. Aim for 5+ samples; 10–15 is ideal.

1. **Paste posts directly in chat** — simplest; paste 3–15 past posts separated by `---`
2. **Folder path** — point at a folder of `.md` or `.txt` files; the skill reads all of them
3. **iPhone / iPad dictation via Notes** — 5-minute voice memo in Notes, paste the transcript
4. **Descript / Otter / Fireflies** — record, export transcript, paste
5. **Voice memo + Whisper** — record on phone, run through MacWhisper or whisper.cpp, paste
6. **macOS native dictation** — System Settings → Keyboard → Dictation → enable; speak directly into any text field

## Supported industries

Out-of-the-box compliance and voice defaults for:

- **B2B SaaS** — founder-led narratives, specific metrics, case studies
- **Professional Services** — consulting, accounting, agencies
- **Creator Economy** — transformation stories, revenue screenshots, cohort launches
- **E-commerce / DTC** — operator-to-operator content, CAC/LTV math, creative teardowns
- **Healthcare** (regulated) — HIPAA, FDA
- **Legal** (regulated) — ABA Model Rules, state variants
- **Finance** (regulated) — SEC Marketing Rule, FINRA 2210
- **Real Estate** (regulated) — Fair Housing, RESPA
- **Manufacturing** (regulated) — OSHA, ITAR
- **Energy & Utilities** (regulated) — FERC, NERC CIP
- **Dental Education** (IDD-style, regulated-adjacent)
- **Generic** (fallback for any other industry)

Adding a new industry: copy `references/industry/industry-template.md` and fill in. See [docs/adding-industries.md](../docs/adding-industries.md).

## Where your data lives

| Data | Location | Purpose |
|---|---|---|
| App config | `~/.claude/data/linkedin-post-studio/config.md` | Default profile pointer, feature flags, `data_location` override |
| Profiles | `~/Documents/LinkedIn Post Studio/profiles/` | Per-profile markdown files |
| Voice samples | `~/Documents/LinkedIn Post Studio/voice-samples/<profile>/` | Past posts the skill reads for voice matching |
| Drafts | `~/Documents/LinkedIn Post Studio/drafts/` | Every generated draft |
| Archive | `~/Documents/LinkedIn Post Studio/archive/` | Posted drafts (move manually or via command) |

Your data is never sent anywhere outside your Claude session. No analytics, no tracking, no cloud sync (unless you point `data_location` at a synced folder for team sharing).

## Roadmap

See [docs/roadmap.md](../docs/roadmap.md) for the full roadmap with status.

Highlights:
- **v2** — Creators-studio integration (images and videos from posts), pre-publish hook, scheduling
- **v3** — Automated performance tracking, Apify-based competitive research, performance dashboard
- **v4** — Multi-language support, team/agency profiles, custom pillar frameworks

Explicitly NOT on the roadmap: engagement pods, third-party DM automation tools (ToS violations), auto-publishing without user review, "guaranteed viral" promises.

## Contributing

- **Architecture** — [docs/architecture.md](../docs/architecture.md) — how the orchestrator dispatches
- **Adding industries** — [docs/adding-industries.md](../docs/adding-industries.md)
- **Adding output types** — [docs/adding-output-types.md](../docs/adding-output-types.md)

Design spec: [specs/2026-04-19-linkedin-post-studio-design.md](../specs/2026-04-19-linkedin-post-studio-design.md).

## License

MIT — see [LICENSE](LICENSE).
