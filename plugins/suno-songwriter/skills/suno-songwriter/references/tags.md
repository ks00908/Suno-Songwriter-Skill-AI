# Suno Tag Reference

Community-compiled reference, built on v5/v5.5 testing and still valid on v6 as far as known (October 2026); v6 understands more musical terminology, so plain musical language in tags works increasingly well. Suno has no official exhaustive tag list, so treat "reliable" as "usually works", not guaranteed. Tags are case-insensitive.

## Contents
1. Structure tags
2. Instrumental / section tags
3. Vocal and delivery tags
4. Dynamics and production tags
5. Combining tags
6. Style prompt vocabulary
7. Call-and-response, cadences, chants, shanties
8. Genre structure templates

## 1. Structure tags (Lyrics field, own line)
Reliable: `[Intro]`, `[Verse]`, `[Verse 1]`, `[Verse 2]`, `[Verse 3]`, `[Pre-Chorus]`, `[Chorus]`, `[Post-Chorus]`, `[Hook]`, `[Bridge]`, `[Outro]`, `[End]`
Also useful: `[Refrain]`, `[Interlude]`, `[Break]`, `[Breakdown]`, `[Build]`, `[Build-Up]`, `[Drop]`, `[Final Chorus]`

Notes:
- Number verses; it helps Suno track progression.
- `[Hook]` suits hip-hop/trap; `[Drop]` suits EDM, dubstep, phonk.
- `[End]` is more abrupt than `[Outro]`; using both in that order is common.

## 2. Instrumental / section tags (no lyrics under them)
`[Instrumental]`, `[Instrumental Break]`, `[Guitar Solo]`, `[Piano Solo]`, `[Synth Solo]`, `[Sax Solo]`, `[Violin Solo]`, `[Bass Solo]`, `[Drum Solo]`, `[Drum Break]`, `[Beat Drop]`, `[Bass Drop]`

Tip: describe the solo in-tag for more control: `[Guitar Solo | melodic, bluesy bends]`.

## 3. Vocal and delivery tags
Voice: `[Male Vocal]`, `[Female Vocal]`, `[Duet]`, `[Choir]`, `[Gospel Choir]`, `[Children's Choir]`, `[Harmony]`, `[Backing Vocals]`
Delivery: `[Whisper]` / `[Whispered]`, `[Spoken Word]`, `[Narration]`, `[Rap]`, `[Fast Rap]`, `[Belted]`, `[Falsetto]`, `[Soft]`, `[Breathy]`, `[Raspy]`, `[Growl]`, `[Scream]`, `[Chant]`, `[Humming]`, `[Vocalise]`, `[Ad-libs]`, `[Call and Response]`
Gender tags are among the most reliable. Emotional delivery tags (e.g. `[Vocal Emotion: wistful]`) are hit-and-miss; state emotion in Style too.

For duets, label who sings: `[Verse 1 - Male Vocal]`, `[Verse 2 - Female Vocal]`, `[Chorus - Duet]`.

## 4. Dynamics and production tags
`[Fade In]`, `[Fade Out]`, `[Crescendo]`, `[Build]`, `[Silence]`, `[Stop]`, `[Key Change]`, `[Tempo Up]`, `[Half-Time]`, `[Double-Time]`, `[Acapella]`, `[Stripped Down]`, `[Full Band]`, `[Sparse]`
Less reliable, use sparingly and flag as experimental: tempo/BPM inside Lyrics tags, exact key changes, `[Callback: ...]`-style instructions, sound effects like `[Applause]`, `[Rain]`, `[Phone Ring]`.

## 5. Combining tags
- Same-line stack: `[Chorus] [Belted]`
- Pipe style: `[Chorus | full band | anthemic]`
- Colon style: `[Mood: euphoric]`, `[Instruments: piano, strings]` - works sometimes; descriptors in the Style box are more dependable.
- Keep to 1-3 modifiers per tag. Structure first, then delivery, then instruments.

## 6. Style prompt vocabulary
**Genres (examples):** pop, synth-pop, indie pop, dream pop, K-pop, disco-pop, rock, indie rock, alt-rock, punk rock, pop-punk, grunge, post-rock, shoegaze, metal, metalcore, doom metal, folk, indie folk, Slavic folk, country, Americana, blues, soul, neo-soul, R&B, funk, gospel, jazz, lo-fi jazz, swing, bossa nova, hip-hop, boom bap, trap, drill, phonk, cloud rap, EDM, house, deep house, techno, trance, drum and bass, dubstep, synthwave, retrowave, ambient, cinematic orchestral, epic trailer, classical, chanson, reggae, reggaeton, Latin pop, Afrobeats, disco polo, sea shanty
**Moods:** euphoric, melancholic, bittersweet, nostalgic, dark, brooding, dreamy, hopeful, triumphant, aggressive, playful, romantic, haunting, intimate, anthemic, chill
**Vocals:** male/female vocals, deep baritone, soaring tenor, smoky alto, breathy, raspy, gritty, powerful belting, airy falsetto, auto-tuned, layered harmonies, choir backing
**Instruments:** acoustic/electric guitar, fingerpicked guitar, distorted guitar, piano, Rhodes, organ, strings, cello, violin, brass, saxophone, accordion, synth pads, analog synth, arpeggiated synth, 808s, sub bass, slap bass, live drums, brushed drums, trap hi-hats
**Production/texture:** lo-fi, vinyl crackle, warm analog, polished modern production, wide stereo, heavy sidechain, reverb-drenched, dry close-mic, gritty, crisp, cinematic
**Experimental descriptors (strong effect, use sparingly):** cinematic (can reshape structure and sound dramatically), modal flavours like Mixolydian or Dorian, turntablism (scratching can overpower the track), delays / tape delay
**Tempo:** slow, mid-tempo, upbeat, driving, or explicit BPM (e.g. 120 BPM)

## 7. Call-and-response, cadences, chants, shanties
Suno can't truly assign lines to singers; it infers parts from formatting, so make the switch between voices impossible to miss.

- **Don't use parentheses for a full response line.** Parentheses render as a quieter, reverb-y backing layer behind the lead and collapse into unison at fast tempos, dense lyrics, or when every line has one. They're for short ad-libs and echoes only: `(hey!)`, `(oh-oh)`.
- **Give each voice its own tag on its own line**, before every turn: `[Drill Sergeant]` / `[Squad] [Shouted]`, `[Shantyman]` / `[Crew]`, `[Lead Vocal]` / `[Choir]`. Repeat the tag at every switch, not just once per section.
- **Make the response text look different from the call.** Identical text confuses Suno about which copy is the lead. Write the group response in CAPS (also nudges a louder, shouted delivery), or make it a short answer rather than a full echo.
- **Blank line between each call and response.**
- **Describe the alternation in the Style prompt explicitly:** "one solo caller voice calls each line alone, then a large group shouts it back in unison, clear alternation between solo and group".
- **Don't use song-section tags in cadences and chants**, especially `[Chorus]`, `[Hook]`, `[Final Chorus]`. Suno treats a chorus as the hook and gives it to the full ensemble, so the caller's lines get sung by the group. Verse tags also nudge toward melodic singing. Use only the voice tags, separate stanzas with blank lines, and put any delivery change on the voice tag itself (`[Drill Sergeant] [Slow]`). The repeated "chorus" stanza of a cadence is still just call and response. Shanties and gospel songs with a real sung group chorus can keep `[Chorus]`.
- **Keep tempo moderate** ("jog pace", "mid-tempo"); fast tempos make Suno merge the two parts.
- Expect some takes to still mix parts up; tell the user to generate 2-3 takes and keep the best.

Example:
```
[Drill Sergeant]
Way up high where the cold stars gleam

[Squad] [Shouted]
WAY UP HIGH WHERE THE COLD STARS GLEAM
```

## 8. Genre structure templates
**Hook-forward (short, catchy, social-media length):** Intro - Chorus - Verse 1 - Chorus - Verse 2 - Chorus - Outro
**Story-led (narrative, ballads, folk):** Intro - Verse 1 - Verse 2 - Chorus - Verse 3 - Bridge - Final Chorus - Outro
**Pop / rock:** Intro - Verse 1 - Pre-Chorus - Chorus - Verse 2 - Pre-Chorus - Chorus - Bridge - Final Chorus - Outro - End
**Ballad:** Intro (piano/guitar) - Verse 1 - Verse 2 - Chorus - Verse 3 - Chorus - Bridge [Soft] - Final Chorus [Belted] - Outro [Fade Out]
**Hip-hop / trap:** Intro - Hook - Verse 1 [Rap] - Hook - Verse 2 [Rap] - Hook - Outro
**EDM:** Intro - Verse - Build - Drop - Breakdown - Verse - Build - Drop - Outro
**Folk / storytelling:** Intro - Verse 1 - Chorus - Verse 2 - Chorus - Verse 3 - Instrumental Break - Chorus - Outro
**Metal:** Intro [Guitar riff] - Verse 1 - Pre-Chorus - Chorus - Verse 2 - Chorus - Breakdown - Guitar Solo - Final Chorus - Outro
