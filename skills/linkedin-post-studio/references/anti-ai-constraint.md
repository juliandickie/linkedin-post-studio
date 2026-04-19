---
title: Anti-AI Constraint
source_sections: ["§5 Ghostwriter and top creator playbooks — The Anti-AI constraint", "§10 Ethics, risk, and common failure modes — AI slop"]
last_updated: 2026-04-19
always_loaded: true
---

# Anti-AI Constraint

**Purpose:** Prevent generated content from reading as AI-generated. Applied universally by the orchestrator to every draft before QA.

## Overview

LinkedIn's audience and the platform's own ranking signals both detect AI-slop patterns. Audiences call it out openly on r/LinkedInLunatics; the platform's Authenticity Update (March 2025) and semantic analysis layers demote content that matches slop fingerprints. This constraint layer is the single biggest quality delta between ghostwritten output that sounds human and output that reads as machine polish.

The principle is deliberate imperfection, specificity, and voice differentiation. The constraint is NOT applied during drafting — it's applied as a final pass (Pass 3 in the Three Passes drafting method) after structure and voice are in place.

## Banned vocabulary (auto-reject any use)

These words and phrases have become reliable AI tells across 2024–2026. Any draft containing them should be rewritten before output:

- delve, dive deep
- unlock, leverage (as verb, e.g., "leverage this insight")
- synergy, game-changer
- journey, tapestry, landscape
- elevate, transform, empower
- navigate, robust, seamless
- testament, ever-evolving, harness
- resonate

Detection: scan the draft case-insensitively. One hit = rewrite the affected sentence. Two or more hits = rewrite the section.

## Banned structures

Structural patterns that read as AI-generated even when vocabulary is clean:

- **"It's not X, it's Y" formulations** — overused contrast structure
- **"I was today years old when..."** opener — pattern-recognized and openly mocked
- **Tri-phrase structures** — "not just X, but Y and Z"; "this is about A, B, and C"
- **Perfectly parallel lists** — break parallelism deliberately in at least one item so the list reads human
- **Stacked arrow bullets** — "→" at the start of every line signals AI templating (and a broader slop signal when combined with checkmark/X bullets)
- **Em-dashes as primary punctuation** — prefer commas, parentheses, or periods; em-dashes are a strong AI tell when used liberally
- **"Here's the kicker" / "Here's the thing"** — formulaic transitions

## Required elements (at least one of each per post)

Every draft must contain ALL THREE of:

1. **One specific proper noun OR number** only the writer could plausibly know. Generic stats ("most people struggle with X") don't qualify; "In Q3 of 2024, my team shipped 47 campaigns" does.
2. **One sentence that sounds slightly awkward or colloquial** — preserves the human tell. A perfectly polished post reads synthetic.
3. **One sentence that would NOT appear in a LinkedIn best-practice guide** — preserves voice differentiation. This is the writer's idiom bleeding through.

If any of these is missing after drafting, insert one before output.

## Detection signals to check before approving

Beyond vocabulary and structure, audit against these broader signals (per Daphne Ippolito, Google Brain, and platform signals as of 2026):

- **Over-use of "the"** — AI text tends toward higher-frequency determiners. Humans skip "the" more often in casual voice.
- **Absence of typos and contractions** — AI output is too clean. Real writing has the occasional "dont" or run-on.
- **Generic adjectives** at high density — resilience, adaptability, impactful, meaningful.
- **Structure repetition across recent posts** — if your last three posts opened with a number and used the same bullet style, the algorithm flags it as templated.
- **Decorative emojis at line starts** — 🎯 💡 ♻️ at the beginning of every paragraph is an AI-slop fingerprint.

## Application order

The Anti-AI constraint is applied in this order after the workflow produces a draft:

1. **Workflow produces draft** — the text-post, carousel, newsletter, or other workflow completes its generation steps and hands off a draft.
2. **Scan for banned vocabulary** — regex-match against the vocabulary list. Each hit triggers a rewrite of the affected sentence.
3. **Scan for banned structures** — pattern-match the structures above. Each hit triggers a restructure.
4. **Check required elements** — verify all three required elements are present. Insert any that are missing.
5. **Detection signal audit** — spot-check against the broader signals (the over-use of "the", excessive emoji decoration, etc.).
6. **Pass to QA checklist** — only proceed once the Anti-AI constraint is satisfied.

## Notes for contributors

This file is a living document. As LinkedIn's detection evolves and new slop patterns emerge, update the banned lists. Keep additions specific and defensible — vague bans ("avoid corporate-speak") lead to false positives and drift. Every addition should have a source (observed slop example, platform signal, or creator/researcher attribution).

When updating, bump `last_updated` and note the addition in `linkedin-post-studio/CHANGELOG.md` under the current version's "Changed" section.
