---
industry_id: <industry-slug>                         # e.g., fintech — lowercase, hyphens
display_name: <Display Name>                         # e.g., Fintech
regulated: false                                     # true | false
voice_defaults:
  adjectives: [<adj1>, <adj2>, <adj3>]               # 3-4 industry-default voice adjectives
  archetype: <Visionary|Operator|Processor>          # default archetype for this industry
  emoji_policy: <none|minimal|moderate>
  sentence_rhythm: <short-staccato|medium-balanced|long-flowing>
compliance_rules: []                                 # list (only if regulated: true) — specific citations
default_disclaimers: []                              # list (only if regulated: true) — copy-pasteable strings
example_creators: []                                 # 3-5 creators worth studying
---

# <Industry> — Content patterns and compliance

## What works

<3-6 bullet points describing high-performing content patterns in this industry>

## What fails

<3-6 bullet points describing anti-patterns>

## Industry-specific hook adaptations

<2-4 example hooks that work well for this industry. Draw from §2 "Industry-specific hook adaptations" or §11 of the research doc>

## Industry-specific CTA patterns

<2-4 example CTAs from §2 "Industry-specific CTA examples">

## Compliance rules (if regulated)

<Detailed regulatory notes with specific rule citations — HIPAA sections, SEC rules, FINRA notices, state bar rules. Skip this section if regulated: false>

## Default disclaimers (if regulated)

<Copy-pasteable disclaimer strings that the skill should append to generated posts. Skip if regulated: false>

## Example creators to study

<Named list with 1-line description of each>

## How to add a new industry

1. Copy this file, renaming it `<industry-slug>.md`
2. Fill in frontmatter (industry_id, display_name, regulated, voice_defaults, compliance_rules, default_disclaimers, example_creators)
3. Replace each content section above with industry-specific content
4. Register in `onboarding/create-profile.md` Step 2 industry list
5. Test by onboarding a profile with `industry: <industry-slug>` and generating a sample post
6. Submit PR
