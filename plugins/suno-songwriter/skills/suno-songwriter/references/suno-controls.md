# Suno Models, Settings and Editing Tools

Last verified: October 2026 (Suno v6 family, released 9 September 2026). Suno retires old models when it launches new ones, so check freshness as described in SKILL.md before relying on anything here.

## Contents
1. Models
2. Field limits
3. Advanced-mode settings (sliders)
4. Recommended settings by situation
5. Editing and extension tools
6. Voice consistency

## 1. Models (v6 family)
All pre-v6 models (v4 to v5.5) are retired for new generations; old songs stay in the library.
| Model | Plan | Use it for |
|---|---|---|
| v6 | Pro / Premier | Finished songs. Follows the prompt most closely; usually a keeper in 1-2 tries. |
| v6-wild | Pro / Premier | Ideas and surprises. Pushes away from the prompt, blends genres, may ignore structure tags. Needs 3+ tries. |
| v6-mini | All plans incl. Free | Drafts and quick tests. Slightly flatter sound than v6. |

Model availability also depends on the plan (v6 and v6-wild are paid). If the plan is unknown, recommend v6 and add "(Pro+; on Free use v6-mini)"; if the user is on Free, recommend v6-mini only. Recommend v6-wild only when the user wants exploration (and warn that it may ignore tags like a carefully built cadence structure).

## 2. Field limits
- Style: ~1,000 characters
- Lyrics: ~5,000 characters
- Exclude styles: ~1,000 characters
- Title: ~80-100 characters (keep under 80 to be safe)
- Song length: up to 8 minutes per generation on all v6 models (Duration can be set in More Options).

## 3. Advanced-mode settings (More Options)
- **Exclude styles** - genres, instruments, production habits to keep out.
- **Vocal Gender** - set it explicitly when gender matters; more reliable than text alone.
- **Duration** - target length.
- **Weirdness** - how much the model experiments. 0 tends to sound stale; 30-50 for detailed, specific prompts; 50-90 for exploring; above ~90 artifacts appear.
- **Style Influence** - how strictly the Style prompt is followed. Lower (~40) for generic/short prompts so the model fills gaps; higher (~65) when the prompt specifies exact sounds.
- **Variety** - at 0 the Style prompt is used as written; higher values let Suno rewrite the prompt before generating (changes vocals and style). Use 0 whenever the skill wrote a detailed Style prompt; raise it to get fresh takes on the same lyrics.
- **Max Mode** (may not be available on every plan) - more compute for whole-song consistency; costs more credits (roughly double). Recommend for songs to publish or edit later, long songs, and covers; off for testing.
- **Personalize** - tailors to the user's taste profile; leave to the user.

## 4. Recommended settings by situation
| Situation | Model | Weirdness | Style Influence | Variety | Max Mode |
|---|---|---|---|---|---|
| Detailed brief, wants it as written | v6 | 30-45 | 60-70 | 0 | on for final |
| Strict format (cadence, chant, call-and-response) | v6 | 20-35 | 65-75 | 0 | on |
| Loose vibe, open to interpretation | v6 | 45-60 | 40-50 | 0-low | off |
| Exploring / brainstorming | v6-wild | 55-80 | 35-45 | medium | off |
| Free plan draft | v6-mini | 35-50 | 50-60 | 0 | n/a |
These are starting points from community testing, not official values. Present them as suggestions.

## 5. Editing and extension tools (all run on v6)
**Plan gating:** these tools are not available to every user. Some need a paid plan (Pro), some only the top tier (Premier: Suno Studio), and Suno moves features between plans and gives new features to higher tiers first. The exact gating per tool isn't reliably documented, so:
- Label every tool suggestion as possibly needing a paid plan, e.g. "(may need Pro or higher)", unless the user has said which plan they're on.
- Always pair it with a fallback that works on every plan (see the table below).
- If the user tells you their plan, remember it for the rest of the conversation and stop suggesting tools above it.

- **Edit / Replace Section** - regenerate one section, or change a single word or line, while keeping the rest. v6 accepts plain-language edit instructions (e.g. "make this chorus a gospel choir"). First fix to suggest when one part of an otherwise good take is wrong (a misread call-and-response line, a mispronounced word, a weak bridge).
- **Extend** - continue a song past where it ended; useful for epics, extra verses, or adding an outro.
- **Cover** - re-generate an existing song in a new style; good for "same lyrics, different genre" variations.
- **Remix / mashup** - combine parts of different songs and describe how they fit.
- **Simple mode** can pick Cover/Remix/Extend itself from a description.
- **Suno Studio** (Premier only) - stems, adding instruments, MIDI.
- Starting points beyond text: voice memo, image or video references.

When the user reports a problem in an otherwise good take, suggest the targeted edit before regenerating the whole song, with the plan caveat and fallback.

| Paid tool | Fallback on any plan |
|---|---|
| Replace Section / line or word edit | Regenerate 2-3 takes with the same inputs and keep the best; fix the formatting of just the problem part (tags, brackets, line breaks) and regenerate |
| Extend | Write the full song length into the Lyrics field and set Duration; or split into Part 1 / Part 2 songs |
| Cover (new style, same song) | Reuse the same lyrics with a new Style prompt as a fresh generation |
| Stems / Studio (Premier) | Export the song and edit in a free DAW (e.g. Audacity, Cakewalk) or use a third-party stem splitter |
| Saved voices / Personas | Keep an identical vocal description at the front of Style for every song in the set |

## 6. Voice consistency
For a recurring singer across songs (a band, an album, a character), point the user to Suno's saved-voice features (Personas / Voices / Custom Models, depending on what their plan currently offers) and keep the vocal description in Style identical across songs. Feature names and plan availability change; describe the goal and let the user find the current control in their Suno UI if unsure.
