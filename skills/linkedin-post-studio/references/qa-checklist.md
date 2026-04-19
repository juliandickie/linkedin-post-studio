---
title: QA Checklist
source_sections: ["§14 QA checklist for any generated post"]
last_updated: 2026-04-19
always_loaded: true
---

# QA Checklist

**Purpose:** Pre-publish gate. Run every item below on every generated draft. If ANY item fails, rewrite the affected section and re-run the checklist. Do not output until all items pass.

## Overview

This checklist is the last line of defense before a draft is handed to the user. It runs AFTER the Anti-AI constraint has been applied, catching voice, structure, distribution, and ethics issues that may have survived the constraint pass.

The orchestrator loads this file on every generation (it is always-loaded, alongside `anti-ai-constraint.md`). Workflows do not need to re-declare it.

## Hook

- [ ] Hook fits in 140 mobile characters (first 2 lines). **Pass criterion:** first two lines total ≤140 chars. **Rewrite trigger:** line 1 or 2 pushes the cutoff — tighten to under 140.
- [ ] Creates curiosity without engagement bait. **Pass criterion:** no "Comment YES", "Tag 3 people", "Like if you agree", "Agree or disagree?" phrasing. **Rewrite trigger:** any engagement-bait phrase — replace with a specific question or observation.
- [ ] No emoji in the hook. **Pass criterion:** lines 1–3 contain no emoji. **Rewrite trigger:** any emoji present — remove it.
- [ ] No "Unpopular opinion" or "I was today years old when" openers. **Pass criterion:** neither phrase appears in the hook. **Rewrite trigger:** present — rewrite with a specific claim instead.

## Structure

- [ ] Post length 800–2,000 characters (sweet spot: 800–1,000). **Pass criterion:** total post body between 800 and 2,000 chars. **Rewrite trigger:** under 800 — expand with a specific example; over 2,000 — cut 20%.
- [ ] Paragraphs of 1–3 sentences. **Pass criterion:** no paragraph exceeds 3 sentences. **Rewrite trigger:** any paragraph of 4+ sentences — break it.
- [ ] 14+ short paragraphs in long posts (>1,500 chars). **Pass criterion:** if the post is over 1,500 chars, it has ≥14 paragraphs. **Rewrite trigger:** long post with few paragraphs — break into more.
- [ ] Blank line between every paragraph. **Pass criterion:** visible whitespace between paragraphs. **Rewrite trigger:** missing — insert.
- [ ] Reading level grade 4–6. **Pass criterion:** Hemingway Editor (or equivalent) reports grade 4–6. **Rewrite trigger:** grade 10+ — simplify sentence structures and word choice.

## CTA

- [ ] Exactly one CTA. **Pass criterion:** one explicit ask in the post. **Rewrite trigger:** two or more asks — pick the highest-priority one, cut the rest.
- [ ] CTA aligned with post goal. **Pass criterion:** lead-gen → DM keyword or booked call; thought-leadership → save/share; brand-awareness → comment/share; community → open question. **Rewrite trigger:** mismatch — swap the CTA to match goal.
- [ ] Not competing with another ask. **Pass criterion:** no implicit secondary asks (no "also, if you want X, do Y"). **Rewrite trigger:** secondary ask present — remove.

## Voice

- [ ] No banned phrases. **Pass criterion:** none of the vocabulary from `anti-ai-constraint.md` appears. **Rewrite trigger:** any match — rewrite the sentence.
- [ ] No em-dashes as primary punctuation. **Pass criterion:** punctuation uses commas, parentheses, or periods. **Rewrite trigger:** em-dashes used liberally — replace most with commas or periods.
- [ ] At least one specific number, proper noun, or first-person detail only the writer could know. **Pass criterion:** specific, checkable, or personal marker present. **Rewrite trigger:** post reads generic — add a specific.
- [ ] Not indistinguishable from AI-generated baseline. **Pass criterion:** a trusted peer reading the post would recognize the writer's voice. **Rewrite trigger:** sounds like anyone — add a signature phrase, awkward sentence, or idiom.

## Distribution

- [ ] External link placed in first comment, not post body. **Pass criterion:** post body is link-free; any link is in the first-comment note. **Rewrite trigger:** link in body — move to first comment, note that in the draft frontmatter.
- [ ] Format fresh vs. previous 2 posts. **Pass criterion:** this post's format (text, carousel, poll, video) differs from the creator's last 2 posts. **Rewrite trigger:** third consecutive same-format post — either change format or defer posting.
- [ ] Scheduled within audience's tested peak window (if known). **Pass criterion:** scheduled time matches the profile's known peak (if set in operations). **Rewrite trigger:** outside peak — reschedule.

## Ethics and compliance

- [ ] Would survive the r/LinkedInLunatics screenshot test. **Pass criterion:** the post would NOT be mocked if screenshotted and posted to r/LinkedInLunatics. **Rewrite trigger:** post uses manufactured vulnerability, trauma-for-engagement, or centers the author during someone else's pain — rewrite.
- [ ] Passes the ghostwriter test. **Pass criterion:** the client (or author) would say this in a board meeting with industry peers watching. **Rewrite trigger:** post relies on rage-bait or sweeping generalizations — soften or replace with a specific claim.
- [ ] If a real person is identifiable in a story, written consent is obtained. **Pass criterion:** either no identifiable real person, or consent note in the draft body. **Rewrite trigger:** identifiable person without consent — anonymize or remove.
- [ ] Regulated industries: required disclosures present. **Pass criterion:** for healthcare (HIPAA de-identification, FDA fair balance), legal (ABA rules, state variants), finance (SEC Marketing Rule, FINRA 2210), real-estate (Fair Housing, RESPA), manufacturing (OSHA, ITAR), energy-utilities (FERC, NERC CIP), dental-education (HIPAA, state dental boards) — the profile's required_disclaimers are appended. **Rewrite trigger:** missing — append per profile.

## Pass/fail decision rule

- **Pass** — every item above checked. Proceed to output: show in chat, write draft file, offer cross-workflow suggestions.
- **Fail** — any item unchecked. Identify the specific failing item, apply the rewrite trigger, re-run the full checklist (not just the failed item — other items may have been affected by the rewrite). Do NOT output until all items pass.

## Integration with pre-approval workflows

If the profile's `compliance.pre_approval_required: true` is set, a passing QA checklist does NOT mean the post is publishable. The draft is written with `status: needs-approval` and the user is told to route it through their reviewer before publishing. QA is the plugin's gate; human approval is the compliance gate.
