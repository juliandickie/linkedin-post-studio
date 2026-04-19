---
title: Algorithm Mechanics (2025–2026)
source_sections: ["§1 LinkedIn algorithm and platform mechanics"]
last_updated: 2026-04-20
load_when: ["text-post", "carousel", "poll", "post-teardown", "content-calendar", "newsletter"]
---

# Algorithm Mechanics (2025–2026)

## Three-stage distribution pipeline

Every post goes through three sequential gates. Primary source: Richard van der Blom's Algorithm Insights Report 2025 (Just Connecting, Netherlands), which analyzed 1.8 million posts across 58,000 profiles and 31,000 company pages over 12 months. AuthoredUp's independent dataset (621,833–994,894 posts) and LinkedIn Engineering's publicly documented LiRank neural ranker (arXiv) corroborate this architecture.

**Stage 1 — Quality filter (0–60 minutes).** Every post is classified as spam, low quality, or high quality before any ranking occurs. LinkedIn currently rejects more than 50% of posts at this gate — up from 40% in 2024. The classifier uses semantic NLP to evaluate topical clarity, coherence, and the presence of engagement-bait phrases. "Comment YES if you agree," "Tag 3 people," "Like this if you relate," and "Agree or disagree?" are pattern-flagged and heavily demoted. The filter also penalizes hook-body mismatch: if you open with "The one LinkedIn tactic that tripled my leads" and the body contains five generic tactics, the semantic gap triggers a quality penalty.

**Stage 2 — Golden hour (60–90 minutes).** The post is shown to roughly 2–5% of first-degree connections who historically engage with similar content. Van der Blom's data marks the first 30–60 minutes as the most critical window. Dwell time, "See more" expansion clicks, and saves are weighted most heavily. If engagement rate in the test cohort exceeds the creator's baseline, the post is promoted to Stage 3. If not, distribution dies. Video and carousel posts get a slightly longer window (up to 120 minutes) because completion rate takes longer to measure; text-only posts get 45–60 minutes.

**Stage 3 — Extended distribution (2 hours to 2–3 weeks).** Content lifespan has expanded materially. Posts that generate genuine conversation can remain actively surfaced for 2–3 weeks versus the historical 24-hour rule. Reach expands to second- and third-degree connections, then to topic-matched non-connections via LinkedIn's interest graph. The 360Brew model (a 150-billion-parameter LLM-based ranker described in a January 2025 research paper) can match post topics to user interest signals even when vocabulary differs — a post about "customer retention for recurring-revenue businesses" will surface to users who engage with "churn reduction" content without keyword overlap.

## Ranking signals hierarchy

Ordered by weight, highest to lowest (combined data from van der Blom, AuthoredUp, Shield Analytics):

1. **Save (bookmark)** — weighted roughly 5–10x a like. A single save is approximately equivalent to two meaningful comments. Saves signal long-term utility.
2. **Substantive comment (15+ words, or a multi-reply thread)** — approximately 2x a like. Indirect comments (replies to other commenters) can deliver up to 2.4x additional reach per thread because they extend session time.
3. **Dwell time and "See more" expansion click** — top-tier signal. A dwell time of 10–15 seconds is the commonly cited quality threshold. Posts read only in preview state rank materially lower than those that earn the expansion click.
4. **Share with original commentary** — high signal. A share with commentary acts as a new post with borrowed authority. Blind reposts (share without commentary) are "practically invisible" in 2026 (van der Blom). The algorithm now treats these as low-value cross-posting.
5. **Like or reaction** — baseline and least weighted. Different reactions (celebrate, support, insightful, funny) carry marginally different weights — "insightful" and "support" outperform "like" slightly — but the gap is negligible compared to comments and saves.

## Reciprocal engagement boosts

Van der Blom 2025 documents bidirectional relationship signals:

- Commenting on someone's post → ~80% chance of seeing their next post in your feed.
- Viewing someone's profile → ~60% boost in mutual feed visibility.
- Sending a DM → ~90% chance of future feed appearance.

**Tactical implication — the top-comment-on-Giants strategy.** By consistently engaging with specific large creators, you both get seen by their audience (through your comment) and increase the probability they see your future content and reciprocate. This is one of the highest-leverage distribution levers currently available.

## Dwell-based ranking era

LinkedIn has moved decisively from pure reaction counting toward dwell-weighted ranking. Specific implications:

- The "See more" click is specifically weighted, not just passive viewing. Passive scroll-through counts for far less than it did in 2023–2024.
- Low carousel completion now penalizes reach. The older conventional wisdom that "swipes alone boost reach" is dead in 2025–2026.
- Video completion rate now matters more than raw view count.

Two practical implications follow:

- **Hook quality matters more than it ever has.** If the hook fails, no dwell occurs and the post dies at Stage 2 regardless of body quality.
- **Length must earn itself.** Posts between 800 and 1,800 characters perform well because they generate dwell without exceeding attention span. Posts over 2,000 characters increasingly underperform unless the topic genuinely warrants depth.

## Media type performance

AuthoredUp multipliers are relative to the creator's baseline reach. Absolute reach is down across all formats year-over-year, so a 1.64x multiplier in 2025 is not equivalent to 1.64x in 2023.

**Personal profiles (2025):**

- Polls: 1.64x (up from 1.32x). Required interaction — clicking an option generates an engagement signal — rewards this format.
- Documents / PDF carousels: 1.45x. Long dwell time (30–90 seconds per carousel) drives this.
- Images: 1.18x. Single image with text caption remains a reliable baseline.
- Video: 1.10x. Native video was up 69% YoY in absolute terms, but the multiplier vs. baseline is modest.
- Text-only: 0.88x. Declined relative to other formats; still viable for creators with strong voice.

**Company pages (2025):**

- Documents: 1.40x.
- Images: 1.21x.
- Polls: 1.19x (crashed from 1.64x YoY — the personal-page advantage does not transfer).
- Video: 1.05x.
- Text-only: 0.42x (van der Blom reports as low as 0.28). Catastrophic for brands relying on company-page organic reach.

**Cross-format notes:**

- Median reach declined ~25–28% across all formats year-over-year.
- Faces in images can lift engagement by up to 50% — human recognition circuits respond to them.
- Portrait/vertical content outperforms landscape by 10–40%. 72% of LinkedIn engagement happens on mobile — vertical content fills the screen; landscape does not.

## Post length sweet spots

The 2025 sweet spot has compressed compared to 2023–2024:

- **Overall 2025 sweet spot:** 800–1,000 characters (down from 1,200–2,000 in prior years).
- **Text plus image optimal caption:** 700–900 characters.
- **Best-performing posts:** 16–20 sentences, paragraphs of maximum 4 lines.
- **Hooks:** 1 line only. Multi-line hooks perform ~20% worse; hooks with negative words perform ~30% worse (Jasmin Alic dataset).
- **Closing:** 3 lines maximum, ideally 1.
- **Reading level target:** grade 4–6 (Hemingway Editor). Posts above grade 10 get 35%+ less reach because they fail mobile scannability.
- **Hard character limit:** 3,000. Posts approaching this limit almost never outperform shorter posts unless the topic genuinely warrants it.

## Above-the-fold character budget

The text visible before the "See more" click is the most important real estate on LinkedIn:

- **Mobile cutoff:** ~140 characters (2 lines).
- **Desktop cutoff:** ~210 characters (3 lines).
- **Highest-engagement zone for whole post:** 1,200–2,000 characters (AuthoredUp, ConnectSafely, and Socialinsider data converge on this range).

The hook must create enough curiosity in those first 2–3 lines to earn the expansion click. Without that click, dwell time is effectively zero and the post stalls at Stage 2.

## Posting frequency and timing

**Frequency:**

- Van der Blom 2025: 2–3 posts per week is optimal. Over-posting reduces performance by up to 20%, particularly same-format back-to-back posts.
- AuthoredUp: 3–5 posts per week. Never more than once per 24 hours.
- Mixing formats (text, carousel, video, poll) prevents format-fatigue penalties.

**Timing (data is contradictory across sources):**

- Buffer 2026 (4.8M posts analyzed): 3–8 PM weekdays, peak Wednesday 4 PM and Friday 3–4 PM. Worst days Monday and Tuesday.
- Hootsuite 2025 (1M posts): Tuesday–Wednesday 4–9 AM.
- Sprout Social: Tuesday–Thursday 9 AM–2 PM local time.

**Resolution:** Timing signals are diverging because evening engagement rose materially in 2026 — users scroll LinkedIn during "second screen" time while watching TV. The reliable path is to test against your own audience using Shield Analytics, Taplio, or native LinkedIn analytics over a 60-day window. Do not rely on any single source's timing data.

## External links

2025–2026 guidance includes acknowledged disagreement between major sources:

- Van der Blom 2025: posts with links see a +5% reach gain vs. no-link. Posts with 3+ links yield +20% reach.
- AuthoredUp: 1 link in post is the worst case. 4+ links produce 3–5x higher median reach than single-link posts.
- Link in first comment: declining effectiveness. Van der Blom says it "no longer works." AuthoredUp still recommends it as a low-penalty placement.
- Edit-to-add-link trick (post clean, then add link after the 60–90 minute golden hour): still works per observed creator practice.

**Consolidated rule, ordered from medium to worst penalty:**

1. Link at end of post with preview card removed — medium penalty.
2. Link in first comment — low penalty.
3. Post without link, edit to add after 90 minutes — lowest penalty; reliably used by top creators.
4. Link at top of post with full preview card — worst penalty.

## LinkedIn Newsletter impact

Newsletters became a serious distribution asset in 2024–2025 and are now a key owned-audience play within LinkedIn's walls:

- Newsletters get 20–30% higher reach than regular posts.
- Launch auto-invites all connections and followers once only.
- Every new edition triggers three notifications (email, push, in-app).
- Average open rate: 40–60% — vastly higher than typical email open rates.
- Weekly cadence correlates with highest success; nearly 60% of top-performing newsletters publish weekly.
- Monetization becomes available at 150+ subscribers via LinkedIn's newsletter program.

## Shadow-banning triggers and recovery

LinkedIn does not use the term "shadow ban" publicly but does throttle reach aggressively. Confirmed triggers based on creator reports and platform statements:

**Triggers:**

- Engagement-bait phrases ("Comment YES," "Tag 3," "Agree or disagree?" as sole CTA).
- Copy-pasting identical content across posts in a short window.
- Recycling old posts without new insight or meaningful revision.
- Third-party comment automation and pod tools (Lempod, Comment Booster, Expandi automation).
- Mass tagging of irrelevant people — especially large accounts with no prior relationship.
- High percentage of self-replies in your own comment thread.
- External links at top of post with preview card.
- Excessive promotion: up to 70% reach reduction when active selling is detected across multiple consecutive posts.

**Recovery protocol:**

1. Pause posting for 48–72 hours.
2. Disconnect all third-party apps with LinkedIn OAuth permissions.
3. Delete the most problematic recent posts.
4. Return with high-value original posts that contain no bait phrases or links.
5. Typical recovery duration: 1–4 weeks.

## What works now vs. what's dead

**Works in 2025–2026:**

- 800–1,000 character text-plus-image posts with tight one-line hooks.
- Carousels with 8–10 slides and a strong first slide (outcome-focused, not vague).
- Vertical native video under 60–90 seconds with captions.
- Polls with 3 answer options plus "Other" and 7-day duration.
- Posts that invite multi-sentence replies (open-ended questions).
- Consistent topic focus across 8+ consecutive posts.
- Faces in images.
- Responding to every comment in the first 90 minutes.
- Engaging with 3–5 other posts immediately before and after publishing.
- Newsletters as owned-audience infrastructure.
- Saving-worthy content: frameworks, checklists, reusable templates.
- Reposts with added commentary (not blind shares).

**Dead or dying:**

- "Comment YES if you agree" engagement bait.
- Pods and third-party comment automation.
- Blind reposts (share without your own commentary).
- Text-only on company pages.
- Hashtag stuffing (5+ hashtags).
- Link-in-post with preview card.
- More than 1 post per 24 hours regularly.
- Same-format back-to-back posts.
- Mass-tagging unrelated people.
- AI-templated content with obvious tells (see `anti-ai-constraint.md`).
- Recycled posts without new hook or added context.
