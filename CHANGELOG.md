# LinkedIn Post Studio — Changelog

Plugin release history. Follows [Keep a Changelog](https://keepachangelog.com/) format.

## [Unreleased]

_No unreleased changes._

## [1.0.0] — 2026-04-20

First public release. Built from the approved v1 design spec — a hub-and-spoke orchestrator with 15 skills spanning natural-language dispatch and slash-command invocation.

### Added

- Hub-and-spoke orchestrator (`skills/linkedin-post-studio/SKILL.md`) with 12 output workflows
- 15 slash commands, each implemented as its own `skills/<name>/SKILL.md` with `disable-model-invocation: true` to avoid natural-language conflicts with the orchestrator
- Profile system with 6 voice-capture methods (paste, folder path, iPhone/iPad Notes dictation, Descript/Otter/Fireflies, Whisper, macOS native dictation)
- 12 industry modules (b2b-saas, professional-services, creator-economy, ecommerce, healthcare, legal, finance, real-estate, manufacturing, energy-utilities, dental-education, generic)
- Always-applied Anti-AI constraint (banned vocabulary, banned structures, required-one-of rules) and QA checklist (pre-publish gate)
- 12 reference files covering algorithm mechanics, content pillars, creator playbooks, engagement tactics, ethics/failures, formatting rules, plus split hook library (index + 12 categories) and post structure (index + 9 frameworks)
- Markdown drafts written to `~/Documents/LinkedIn Post Studio/drafts/` with full frontmatter (profile, goal, format, framework, hook-category, pillar, status, performance placeholders)
- Compatibility with all four Claude surfaces: Claude Code, Desktop (code and chat modes), Web, Cowork
- Installation guide with prominent "Restart required after install" section covering all surfaces and a self-diagnostic
- Full contributor docs (architecture, adding industries, adding output types, roadmap)
