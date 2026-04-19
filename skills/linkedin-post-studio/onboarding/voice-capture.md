---
title: Voice capture
purpose: Capture a user's writing voice via one of 6 methods and write it to their profile
last_updated: 2026-04-20
---

# Voice capture

**When to run:**
- User explicitly asks: "add voice samples", "capture my voice", "/linkedin-onboard voice"
- Dispatch from `onboarding/create-profile.md` when user chooses "capture voice now"
- User wants to update an existing profile's voice as their writing evolves

**Output:**
- Updated `voice:` frontmatter in the profile file at `<data_location>/profiles/<profile_id>.md`
- Inline voice samples in the profile body, OR a populated `<data_location>/voice-samples/<profile_id>/` folder
- A "## Voice observations from capture" section appended to the profile body

## Prerequisites

- A profile already exists (if not, run `onboarding/create-profile.md` first)
- Handoff schema: `templates/voice-profile-template.md`

## The 6 capture methods

Offer the user any (or a combination). Emphasize: **the more samples, the better the result.** Aim for ≥5 samples; 10–15 is ideal.

---

### Method 1 — Paste past posts directly

Ask:

> "Paste 3–15 of your best past LinkedIn posts, each separated by `---`. Include date and rough performance if known (e.g., '2026-02-14, 12K impressions')."

When the user pastes:

1. Split on `---` separators
2. For each sample, save to `<data_location>/voice-samples/<profile_id>/YYYY-MM-DD-<slug>.md` where the slug is derived from the first 5 words of the post (lowercase, hyphens, strip punctuation)
3. Also preserve the count and first 80 chars of each sample in the profile body under "## Voice samples (inline)"
4. Update `voice.voice_samples_inline` to the count pasted

---

### Method 2 — Folder path

Ask:

> "Provide a folder path containing your past posts as `.md` or `.txt` files."

When the user provides a path:

1. Validate the path exists. If not, ask again.
2. Read all `.md` and `.txt` files in that directory (recursively if it has subfolders)
3. Set `voice.voice_samples_path` to the folder path (preserve the absolute path as the user gave it, don't rewrite to `~/...` unless they used that form)

---

### Method 3 — iPhone / iPad dictation via Notes

Provide these instructions to the user:

> 1. Open the Notes app on your iPhone or iPad
> 2. Create a new note titled "LinkedIn voice capture"
> 3. Tap the microphone icon on the keyboard
> 4. Speak for 5 minutes about the following four prompts (~1 min each):
>    - Your work (what you do, for whom, with what result)
>    - A recent client win or successful project — include specific numbers
>    - An industry take you hold strongly that most peers would disagree with
>    - A lesson you learned the hard way (include the cost)
> 5. Copy the transcribed text and paste it back here

Process the transcript the same as Method 1 (save as sample files, preserve summary in profile body).

---

### Method 4 — Descript / Otter / Fireflies transcript

Provide these instructions:

> 1. Open your transcription tool (Descript, Otter, Fireflies, etc.)
> 2. Record a 5-minute voice memo covering the four prompts listed in Method 3
> 3. Export or copy the transcript
> 4. Paste it back here

Process as Method 1.

---

### Method 5 — Voice memo + Whisper

Provide these instructions:

> 1. Record a 5-minute voice memo on your phone (any recorder app)
> 2. Export the audio file to your Mac
> 3. Run it through a local Whisper tool:
>    - **MacWhisper** (macOS app, drag-and-drop — easiest)
>    - **whisper.cpp** (command line: `whisper audio.m4a --model medium --language en`)
>    - **OpenAI Whisper API** (if you have credits)
> 4. Copy the transcript and paste it back here

Process as Method 1.

---

### Method 6 — macOS native dictation

Provide these instructions:

> 1. Open System Settings → Keyboard → Dictation → enable
> 2. Optionally set a custom shortcut (default is press Fn twice)
> 3. Open any text field (Notes, a new TextEdit document, even this chat)
> 4. Trigger dictation and speak for 5 minutes covering the four prompts in Method 3
> 5. Stop dictation and paste the text back here

Process as Method 1.

---

## After samples are collected

### Step A — Analyze voice patterns

Read all collected samples (inline + folder, if both). Extract:

- **Opening patterns** — how they typically start posts (number-first, observation, question, quote, specific name)
- **Sentence length distribution** — average length in words, range, and where they use short punctuation sentences
- **Signature phrases** — phrases that recur across 2+ samples
- **Metaphor families** — domains they borrow metaphors from (sports, cooking, military, nature, family, tech)
- **Closing structures** — how they typically end (question, observation, CTA, single line, P.S. hook)
- **Formatting habits** — emoji use, dashes, bullet style, capitalization, line-break patterns

### Step B — Detect executive archetype

Compare the samples against the three archetypes. If ambiguity arises, **load `references/creator-playbooks.md`** (which is load-on-demand — only load it here because archetype detection is one of its trigger conditions):

- **Visionary** — long-term strategy, predictions, category-creation, "mantra" beliefs
- **Operator** — execution, workflows, day-in-the-life, specific tooling
- **Processor** — data, detail, risk, decision frameworks, myth-busting

If samples span archetypes (common for hybrid operators), ask the user which resonates most when describing their work.

### Step C — Build the Voice Profile

Using `templates/voice-profile-template.md` as the schema, populate:

- `voice.adjectives` (3–5, derived from Step A)
- `voice.archetype` (from Step B)
- `voice.emoji_policy` (based on observed use in samples: none, minimal, moderate)
- `voice.sentence_rhythm` (based on average length: short-staccato < 10 words, medium-balanced 10–18, long-flowing 18+)
- `voice.signature_phrases` (2–5 phrases observed in samples)

### Step D — Banned phrases

Start with the default AI-slop list from `references/anti-ai-constraint.md`:

```
delve, dive deep, unlock, leverage (verb), synergy, journey,
tapestry, testament, ever-evolving, resonate
```

Ask the user:

> "These are the AI-slop defaults. Want to add any phrases of your own to avoid? (Industry jargon you dislike, words that feel preachy, overused phrases you've noticed in your niche.)"

Append user additions to `voice.banned_phrases`.

### Step E — Save and confirm

Update the profile file:

- Overwrite the `voice:` frontmatter block with the new values
- Append "## Voice observations from capture" to the profile body (use the markdown section from `templates/voice-profile-template.md`)
- Update `voice.status`:
  - `complete` if ≥5 samples captured
  - `partial` if 1–4 samples captured
  - `missing` (should not happen — user chose to capture, so at least some samples came in)
- Update profile's `updated` date

Show the user:

- Number of samples captured and where they're stored
- Detected archetype + adjectives
- Path to profile file
- Offer: "Want me to generate a sample post right now so you can see how your voice sounds?"

### Step F — Resume original request (if any)

If voice-capture was triggered mid-request via `create-profile.md`, return control to that flow so it can finish.

## Troubleshooting

- **Samples span multiple years with shifting voice** → ask the user which period represents their current voice. Use only those samples.
- **Only 1–2 samples available** → set `voice.status: partial`, use what's there, warn the user that generation quality depends on sample diversity.
- **Samples are all from one format** (e.g., all carousels) → note this limits voice fidelity for other formats. Flag in the "Voice observations" section.
- **User pastes AI-generated content as their "voice"** → gently flag suspected AI-slop patterns during Step A. Ask: "Did you write these yourself, or were they drafted by an AI? If the latter, we want your raw human samples — even rough voice memos beat polished AI drafts."

## Notes for contributors

If a new voice-capture method becomes viable (e.g., a new transcription tool enters the market), add it as Method 7+. Do not remove existing methods unless they stop working — users may have personal preferences.
