---
title: Compliance setup (regulated industries)
purpose: Configure compliance disclaimers and pre-approval workflow for regulated industries
last_updated: 2026-04-20
---

# Compliance setup

**When to run:** Only when the profile's `industry` is in the regulated set:
- `healthcare`
- `legal`
- `finance`
- `real-estate`
- `manufacturing`
- `energy-utilities`
- `dental-education`

Triggered from `onboarding/create-profile.md` Step 5. Not run for unregulated industries.

**Output:** Populated `compliance:` frontmatter block in the profile file.

## Steps

### Step 1 — Load industry defaults

Read `references/industry/<industry>.md`. Extract:

- `compliance_rules` (array of applicable regulations with citations)
- `default_disclaimers` (array of pre-written disclaimer strings)
- Industry-specific notes on practical implications

### Step 2 — Show the user the industry's baseline

Tell the user:

> "Your industry (<display_name>) has compliance requirements. Here's what typically applies:
>
> **Rules:**
> - <rule 1>
> - <rule 2>
> - ...
>
> **Default disclaimers I can append to generated posts:**
> - <disclaimer 1>
> - <disclaimer 2>
> - ...
>
> I'll walk through each and let you confirm, customize, or skip."

### Step 3 — Confirm each rule

For each rule in `compliance_rules`, ask:

> "Applies to you? (y/n/customize)"

- **y** → keep as-is in the user's profile.
- **n** → remove from the user's profile. Example: a finance content creator who is NOT a registered RIA or broker-dealer doesn't need FINRA Rule 2210. Removing it prevents over-application.
- **customize** → let the user edit the wording. Preserve the citation anchor (e.g., "HIPAA Privacy Rule 45 CFR 164.502") but let them adjust how it's phrased in their profile.

### Step 4 — Confirm each default disclaimer

For each disclaimer in `default_disclaimers`, ask:

> "Include this disclaimer at the end of posts? (y/n/customize)"

Store the final list in `compliance.required_disclaimers`. The skill will append these to generated posts per profile — they are not added automatically to every draft, only when the profile has them configured.

### Step 5 — Pre-approval workflow

Ask:

> "Does someone need to review and approve your posts before they go live? (e.g., compliance officer, legal team, account manager, managing partner)"

- **Yes** → set `compliance.pre_approval_required: true`. Ask follow-up:
  > "Who reviews (name or role)? And what's their turnaround expectation?"

  Store reviewer name/role and SLA in profile body under "## Compliance context". Future drafts will be written with `status: needs-approval` instead of `status: draft`, so they're visible in the queue for review.

- **No** → `compliance.pre_approval_required: false`.

### Step 6 — Topic red lines

Ask:

> "Any topics you absolutely cannot post about? Examples:
> - Specific clients or patients by name
> - Competitors by name (especially for regulated industries)
> - Pending litigation or confidential settlements
> - Pre-announcement products or regulatory filings
> - Personal medical/legal/financial details about family members
> - Political positions that could violate firm policy"

Store list in `compliance.topic_red_lines`. The skill will warn at generation time if a user's requested topic matches any red line (exact or semantic match).

### Step 7 — Industry-specific extras

Ask targeted follow-ups based on `industry`:

#### healthcare

> "Will you mention specific patients, cases, or clinical trials?"

- If yes → confirm they have a HIPAA-compliant consent process or will always use de-identified scenarios. Note the choice in profile body.

> "Do you work in a setting where the Stark Law or Anti-Kickback Statute could apply (referrals, joint ventures, speaker fees)?"

- If yes → flag in profile body for extra caution on sponsored content disclosure.

#### finance

> "Are you a registered RIA, broker-dealer, or neither?"

- **RIA** → confirm SEC Marketing Rule applies.
- **Broker-dealer** → confirm FINRA Rule 2210 applies (static content needs principal pre-approval).
- **Neither (fintech commentator / educator)** → wider latitude, but FTC endorsement rules still apply.

Store in profile body.

#### legal

> "Which state(s) are you barred in?"

Affects which state-specific rules apply (Florida filing, NY 7.4, California 7.1–7.5, Texas 7.04, Louisiana 7.2). Store states in profile body.

> "Do you hold yourself out as a specialist in any area?"

- If yes → some states require board certification and prominent disclaimers. Flag in profile body.

#### real-estate

> "What state(s) are you licensed in, and what's your license number?"

Store state + license number — they go into the required disclaimer for online advertising in most states.

#### manufacturing

> "Any defense-adjacent work? (ITAR/EAR compliance)"

- If yes → flag in profile body; visual content showing product details must be reviewed before posting.

#### energy-utilities

> "Publicly traded utility? If so, SEC Regulation FD applies — material information can't be shared individually."

- If yes → flag in profile body; posts about material events must go through corporate comms first.

#### dental-education

> "Will you show patient cases or treatment photos?"

- If yes → confirm HIPAA-compliant consent process OR de-identification workflow. Store choice in profile body.

> "Do you hold yourself out as a specialist in endo, perio, ortho, pedo, pros, or OMS?"

- If yes → most state dental boards require ABDS certification to claim specialty. Flag.

### Step 8 — Confirm and save

Show the user the final `compliance:` block and body notes. Ask for confirmation before saving.

On confirmation:
- Set `compliance.required: true`
- Write all fields into the profile file
- Update profile's `updated` date

Tell the user:

> "Compliance setup saved. Your generated posts will automatically include the selected disclaimers, and any topic matching your red lines will trigger a warning before generation."

### Step 9 — Resume

Return control to `create-profile.md` Step 6 (voice capture offer).

## Troubleshooting

- **User's actual compliance situation doesn't match the industry defaults** — e.g., they're a healthcare-adjacent consultant, not a practicing clinician. Ask targeted questions to determine which rules actually apply. Remove non-applicable rules and note the scope in the profile body.
- **User has multi-jurisdiction exposure** — e.g., a lawyer barred in CA and NY, or a financial advisor serving US and EU clients. Store all applicable jurisdictions in profile body. The skill will prompt at generation time if a post's topic could trigger jurisdiction-specific rules.
- **User says "just apply everything to be safe"** — gently push back. Over-disclosure can hurt engagement and sometimes creates its own liability (e.g., claiming attorney-client relationship by disclaimer wording). Apply only what's genuinely applicable.

## Notes for contributors

When a new regulated industry is added, its `references/industry/<new-industry>.md` file must include `compliance_rules` and `default_disclaimers` arrays, plus (if needed) a new Step 7 sub-section here with industry-specific follow-up questions. Keep the sub-sections alphabetized in Step 7 for maintainability.
