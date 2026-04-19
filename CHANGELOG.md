# LinkedIn Post Studio — Changelog

Plugin release history. Follows [Keep a Changelog](https://keepachangelog.com/) format.

## [Unreleased]

### Added
- Installation guide: prominent "Restart required after install" section in README covering all four Claude surfaces (Desktop, Code, Web, Cowork), including a diagnostic check (empty `/linkedin-` auto-complete = restart needed).

### Changed
- Migrated 15 slash commands from legacy `commands/*.md` flat format to modern `skills/<name>/SKILL.md` directory format. Each command-style skill uses `disable-model-invocation: true` so natural-language triggers still flow through the orchestrator. Installation no longer surfaces the "legacy commands/ format" warning.
- Absorbed the former `/linkedin-post-studio` help-screen behavior directly into the orchestrator's `SKILL.md` — it now shows a help/status screen when invoked with empty args, and dispatches normally when given a request.

### Fixed
- Plugin manifest moved to `.claude-plugin/plugin.json` (required by Claude Code loader).
- All 15 slash commands converted from invalid `arguments:` array frontmatter to `argument-hint:` string, and from invalid `{{var}}` templating to `$1`/`$2`/`$ARGUMENTS` positional substitution.
- Flattened `repository` manifest field from object to URL string.
- Removed stray `.DS_Store` files.

## [1.0.0] — TBD

First public release. See the [v1 spec](../specs/2026-04-19-linkedin-post-studio-design.md) for the full feature set.

### Added
- Hub-and-spoke orchestrator (`SKILL.md`) with 12 output workflows
- 15 slash commands (Claude Code / Desktop code mode / Cowork)
- Profile system with 6 voice-capture methods
- 12 industry modules (b2b-saas, professional-services, creator-economy, ecommerce, healthcare, legal, finance, real-estate, manufacturing, energy-utilities, dental-education, generic)
- Always-applied Anti-AI constraint and QA checklist
- Markdown drafts written to `~/Documents/LinkedIn Post Studio/drafts/`
- Compatibility with Claude Web and Claude Desktop chat mode (skill-only)
