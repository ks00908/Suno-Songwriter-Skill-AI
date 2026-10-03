# Genre-Specific Lyric Writing

The general singability rules in SKILL.md assume sung melodic lyrics. These genres need different rules. In v6, lyric phrasing and flow shape the result more than long style lists, so getting this right matters.

## Contents
1. Rap / hip-hop
2. Metal and screamed vocals
3. EDM and dance
4. Ballads and musical theatre
5. Folk, shanties, storytelling
6. Spoken word and narration

## 1. Rap / hip-hop
**Density.** Rap lines carry far more syllables than sung lines: roughly 10-16 syllables per bar for mid-tempo boom bap or trap, 16+ for fast/double-time. Keep density consistent within a verse unless the switch is deliberate.

**Bars and sections.** Verses are usually 16 bars (16 lines), sometimes 8 or 12. Hooks are 4-8 lines, sung or chanted, much simpler and more repetitive than verses. One line = one bar.

**Rhyme.** Go beyond end rhymes:
- Multisyllabic rhymes: "elevator / never later / better paper".
- Internal rhymes within a line.
- Rhyme chains that hold one sound across 2-4 bars, then switch.
Avoid predictable one-syllable rhyme pairs (fire/higher, day/way) carrying whole verses.

**Flow cues.**
- Tags: `[Rap]`, `[Fast Rap]`, `[Double-Time]`, `[Half-Time]`, `[Melodic Rap]`, `[Hook]`, `[Verse 1 - Rap]`.
- Commas and line breaks act as breath points; use them where the rapper should pause.
- For a beat switch or flow change mid-verse, start a new tagged block rather than writing it in prose.
- Ad-libs in round brackets at line ends: `(yeah)`, `(skrrt)`, `(uh)`. One per line at most, not every line.

**Content.** Specific detail and wordplay over generic boasts. Punchlines usually land on the 4th bar of a 4-bar group.

**Style prompt.** Name the subgenre and beat (boom bap, trap, drill, cloud rap, jazz rap, phonk), the delivery (aggressive, laid-back, melodic, raspy) and BPM; e.g. `boom bap hip-hop, dusty jazz sample, laid-back confident male rap, crisp snares, 90 BPM`.

**Polish rap.** Polish has lots of multisyllabic rhyme potential because of inflection; use it. Mind penultimate stress when rhyming: the rhyme should match from the stressed syllable on ("kieszeni / zmieni", not "kieszeni / ni"). Clusters are fine in fast rap but simplify them on held hook notes.

## 2. Metal and screamed vocals
- Tag delivery per section: `[Screamed]`, `[Growl]`, `[Clean Vocals]`, `[Gang Vocals]`. Alternating clean chorus with harsh verses is common in metalcore; state it in Style ("harsh screamed verses, soaring clean chorus").
- Screamed lines can be shorter and more percussive; clean choruses should be singable and melodic.
- `[Breakdown]` works well; leave it with one short shouted line or no lyrics.

## 3. EDM and dance
- Lyrics are sparse: a few repeated lines carry the song. Over-writing makes Suno cram vocals into drops.
- Leave `[Drop]` and `[Build]` without lyrics, or a single chopped word.
- Repetition is a feature: a 1-2 line hook repeated is normal.

## 4. Ballads and musical theatre
- Longer held notes: fewer syllables per line (5-8), open vowels on line endings (oh, ay, ee rather than closed consonants).
- Musical theatre is narrative: verses move the story forward, the title line lands at chorus end.
- Use `[Soft]` / `[Belted]` to shape the dynamic arc toward the final chorus.

## 5. Folk, shanties, storytelling
- Ballad meter (alternating 8 and 6 syllables, ABCB rhyme) fits folk storytelling naturally.
- Shanties: short call lines and big group refrains; a real sung group chorus can use `[Chorus]` (unlike cadences - see tags.md section 7).
- Concrete names, places and objects carry the story better than emotion words.

## 6. Spoken word and narration
- Tag `[Spoken Word]` or `[Narration]`; write in natural sentences with punctuation, since Suno uses it for pacing.
- Keep spoken sections short inside a song (2-6 lines); long ones can drift into singing.
- If spoken lines get sung anyway, try `[Shouted]` (for commands) or reduce the music under it with `[Sparse]`.
