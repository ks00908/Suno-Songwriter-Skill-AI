---
name: suno-songwriter
description: Advanced generator of ready-to-paste Suno AI songs - a Style prompt plus full lyrics marked up with Suno-supported meta tags ([Intro], [Verse], [Chorus], [Bridge], [Drop], [Whisper], [Guitar Solo], [Fade Out] etc.), in any language including Polish and English. Use this skill whenever the user mentions Suno, AI song or AI music generation, wants lyrics "for Suno", wants a song written from a vibe, topic or brief, wants their own lyrics tagged, polished or structured for Suno, asks for a style prompt, exclude styles, or song title - even if they don't say "Suno" but clearly want a song to generate with an AI music tool. Also use for translating or adapting a song into another language for Suno, and for fan songs set in any franchise or fictional universe (Halo, Star Trek, Star Wars, Warhammer, Elder Scrolls, Tolkien, anime, games), where it looks up lore on the franchise's primary wiki before writing.
---

# Suno Songwriter

Turn anything from a one-word vibe to a full brief or the user's own lyrics into a song the user can paste straight into Suno's Custom mode: a **Style** prompt, **tagged Lyrics**, a **Title**, and (when useful) **Exclude styles**.

Suno is not a human singer. It reads the Style box as the overall sound, reads bracketed tags in the Lyrics field as stage directions, and sings everything else. Almost every bad Suno result comes from one of three things: a vague or overstuffed Style prompt, lyrics with no clear structure, or instructions written as plain text that end up being sung. This skill exists to prevent all three.

Read `references/tags.md` for the full tag reference before writing tags beyond the basic structure ones. For songs set in a franchise or fictional universe, also follow "Franchise and fandom songs" below and use `references/lore-sources.md`. For rap, metal, EDM, ballads, musical theatre, shanties or spoken word, read `references/genre-writing.md`. For model choice, slider settings and Suno's editing tools, read `references/suno-controls.md`.

## Step 0: Check that the Suno info is current

Suno changes fast and retires old models when new ones launch (v6 replaced everything before it in September 2026), so the limits, tags and settings in this skill can go stale. `references/suno-controls.md` records when it was last verified. If a search tool is available and that date is more than about two months old, or the user mentions a model or feature you don't recognise, run a quick search (e.g. "Suno latest model", "Suno new features") before writing. If something has changed, follow the newer information and mention the change in one line in the Notes. Skip this check for quick follow-up edits within the same conversation.

## Step 1: Figure out what you were given

Users arrive in three ways. Handle each without making them fill in a form:

- **Just a vibe or topic** ("sad song about leaving Wrocław", "gym banger"): make confident creative choices for genre, tempo, voice and structure, write the song, and list the 2-3 key choices in one line at the end so they can redirect.
- **Detailed brief** (genre, mood, story, voice, language): follow it exactly. Fill only the gaps they left.
- **Their own lyrics**: keep their words. Your job is structure, tags and a Style prompt. Fix only what will break in Suno (lines far too long to sing, a missing chorus, stage directions written as plain text). If you think a line should change for singability, suggest it after the output rather than silently rewriting. Never "improve" their lyrics into your own.
  - When splitting an overlong line, keep every word; only move the line break. Dropping even a filler word ("kiedyś", "and") changes their writing.
  - Convert their plain-text markup in any language into Suno tags: section labels ("Zwrotka", "Refren", "Strophe", "Estribillo", "Verse:", "Chorus:") become `[Verse 1]`, `[Chorus]` etc.; "x2" / "repeat" becomes the section written out in full each time; stage directions in round brackets like "(szeptem)" or "(whispered)" become square-bracket tags in English (`[Whisper]`), since round brackets would be sung.
  - Any tag you add that changes delivery beyond what they marked (e.g. `[Belted]` on a final chorus) goes in the Notes so they can remove it.
  - If their song is short (under ~20 sung lines), say it will come out short (around 2 minutes) and offer, don't add, an extra verse or bridge.

Ask a question only when something essential is genuinely unknowable and a wrong guess would waste their credits, e.g. the language when the request is ambiguous. One question at most, otherwise just write.

**Language:** write lyrics in the language the user asks for, or the language they write to you in if they don't say. Tags and the Style prompt stay in **English** regardless of lyric language, because Suno's tag interpretation is trained on English descriptors. See "Non-English lyrics" below.

## Step 2: Build the Style prompt

The Style box sets the sound for the whole song. Write it as a comma-separated list of descriptors, most important first, because Suno weights the start of the prompt most and truncates silently past the limit.

Order:
1. Genre + subgenre (1-2), optionally era: `melancholic indie folk, 2010s`
2. Mood / energy (1-2): `bittersweet, slow-building`
3. Vocals: gender, character, delivery: `intimate male vocals, airy falsetto in chorus`
4. Key instruments (2-4): `fingerpicked acoustic guitar, soft cello, brushed drums`
5. Production / texture (1-2): `warm analog, close-mic, room reverb`
6. Tempo if it matters: `78 BPM` or `slow tempo`
7. Optional key: `D minor`

Guidelines and why they matter:
- **Aim for roughly 150-400 characters.** Hard limit is about 1,000, but a focused prompt steers better than a long one. Count the characters with code rather than estimating, and report the count.
- **No real artist or band names.** Suno filters them. Translate the reference into sonic traits instead: not "like Dawid Podsiadło" but "Polish alt-pop, soft breathy male tenor, intimate piano, airy synth pads, melancholic".
- **No contradictions** ("aggressive calm lullaby metal"). Fusions are fine if deliberate: `Slavic folk meets dark techno`.
- **Avoid the word "live"** and related words unless the user wants crowd noise; Suno tends to add audience sounds.
- Avoid putting structure tags like [Verse] here; they belong in Lyrics.

**Exclude styles** (Suno's separate "Exclude" field): add it when there's a predictable failure to prevent, e.g. `autotune, EDM drops, female vocals` for a raw male folk song. Keep it short. Skip it if nothing needs excluding.

## Step 3: Write the lyrics with tags

### Structure
Choose a structure that fits the genre (see `references/tags.md` for genre templates). A safe default:

```
[Intro]
[Verse 1]
[Pre-Chorus]
[Chorus]
[Verse 2]
[Pre-Chorus]
[Chorus]
[Bridge]
[Chorus]
[Outro]
[End]
```

- Aim for about 30-45 sung lines for a full-length song. Under ~15 lines Suno makes a short track; far over 60 it tends to rush or cut off.
- Hard limit for the Lyrics field is about 5,000 characters. Count it. Songs can run up to 8 minutes on v6, so long epics are possible, but more lines still means more chances for Suno to rush or drift.
- Repeat the full chorus text each time it appears. Writing just `[Chorus]` with no lines, or "(repeat chorus)", is unreliable.
- End with `[Outro]` and then `[End]` (or `[Fade Out]`) to reduce the chance Suno keeps generating or ends abruptly mid-word.

### Tag rules
- Each section tag goes **on its own line** directly before the lines it controls.
- Stack a section tag with a modifier on the same line when you want a specific delivery: `[Chorus] [Belted]`, or a pipe style: `[Bridge | whispered | sparse piano]`. Keep modifiers to 1-3 per tag; more gets ignored.
- Instrumental sections get a tag and no lyrics: `[Guitar Solo]`, `[Instrumental Break]`, `[Drop]`.
- Anything in **square brackets is an instruction, not sung**. Anything in **round brackets is sung**, usually as backing vocals or ad-libs: `(oh-oh-oh)`, `(hey!)`. Never put stage directions in round brackets, and never write "Verse:" or "Chorus:" as plain text, because Suno will sing them.
- For call-and-response songs (cadences, chants, shanties, gospel, duets with echoes), never put whole response lines in round brackets; follow section 7 of `references/tags.md` (a voice tag before every turn, response in CAPS or as a short answer, alternation described in Style, moderate tempo).
- Use only tags that Suno reliably responds to (listed in `references/tags.md`). Inventive tags sometimes work, but if you use an unusual one, say so in the notes so the user knows it's experimental.

### Writing singable lyrics
Suno sings what it reads, so write for the ear:
- Keep lines short and consistent in syllable count within a section; 6-10 syllables per line is a comfortable singing range for most sung genres. Rap, metal, EDM and other genres follow different rules: see `references/genre-writing.md`.
- On v6, the phrasing and flow of the lyrics shape the melody more than a long Style prompt does, so spend effort here.
- Make the chorus the simplest, most repeatable part, with the title or hook in its first or last line.
- Use concrete images over abstractions, a fresh angle on the topic, and rhyme or near-rhyme that sounds natural rather than forced.
- Spell out sounds you want sung: "la-la-la", "na-na-na", "yeah-eh-eh".
- Spell numbers and tricky abbreviations as words, and write stressed or unusual words phonetically if they are likely to be mispronounced (mention it in the notes).
- All lyrics must be original. Don't reproduce or lightly rework lyrics of existing songs, even if asked to "use the chorus of X"; offer an original hook in that spirit instead.

### Non-English lyrics (including Polish)
- Lyrics in the target language; tags and Style prompt in English.
- Put the language in the Style prompt explicitly near the front: `Polish-language indie pop` or `sung in Polish`. Without it, Suno may drift into English pronunciation or accent.
- Polish specifics: Polish stress falls on the penultimate syllable, so line endings rhyme best on feminine (two-syllable) rhymes like "miasto / ciasto". Avoid piling consonant clusters (e.g. "zszywszy", "wstrząs") on long held notes; put them on fast passages instead. Keep diacritics (ą, ę, ł, ś, ż, ź, ć, ń, ó); Suno handles them and removing them changes pronunciation.
- For bilingual songs, mark the switch so the user sees it, e.g. English chorus with Polish verses, and say "bilingual Polish and English vocals" in the Style prompt.

## Franchise and fandom songs

When the song is set in a fictional universe (Halo, Star Trek, Star Wars, Warhammer 40k, The Elder Scrolls, Mass Effect, Tolkien, etc.), fans will notice wrong lore at once, and correct details are what make a fan song feel real. So research before writing.

### 1. Look up the lore on the primary fan wiki
Read `references/lore-sources.md` to find the main wiki for the franchise (e.g. Halopedia for Halo, Memory Alpha for Star Trek, Wookieepedia for Star Wars, Lexicanum for Warhammer 40k).

- Search with the wiki name plus the subject (e.g. `Halopedia Insurrection`, `Memory Alpha Klingon drinking`), then fetch the most relevant article pages from the results. Fetch 2-4 pages: usually the era/conflict, the faction or unit, and one or two concrete details (a place, ship, weapon, ritual, battle).
- If the franchise isn't listed, search for `<franchise> wiki` and prefer a wiki that the community treats as canonical, cites its sources, and separates canon from fanon or "Legends".
- Note the canon status. Where canon and non-canon sources conflict (e.g. Star Wars Canon vs. Legends, Star Trek Kelvin vs. Prime timeline), follow the user's choice, or default to current canon and mention it.
- If no search tool is available, write from your own knowledge, stick to well-established facts, and say in the notes that the lore wasn't checked.

### 2. Pin down the setting before writing
Before writing lyrics, decide on: **who** is singing (faction, rank, species, culture); **when** (era, war, before/after key events); **where** (planets, ships, cities); and **what they would and wouldn't know**. Period accuracy is the most common fan complaint: a Halo song set during the Insurrection shouldn't mention the Covenant, and a Star Trek TOS-era song shouldn't mention the Dominion.

### 3. Use the lore in the lyrics
- Use real in-universe vocabulary, slang, place names, unit mottos, ranks and gear, but woven in naturally. Three to six specific details make a song feel authentic; a list of every term you found makes it feel like a quiz.
- Match the culture's musical tradition where the lore defines one (Klingon opera, Nord bardic songs, Mandalorian chants) and translate that into Suno descriptors in the Style prompt.
- Invented names (fallen soldiers, minor ships) are fine and often better than canon heroes, but make them fit the setting's naming conventions.
- Constructed languages (Klingon, Elvish, Mando'a, High Gothic) work well for a hook or chant line. Use only words you've verified from the wiki, and note the pronunciation.

### 4. Keep it original and Suno-safe
- **No franchise, studio or composer names in the Style prompt.** Like artist names, Suno may filter trademarked names, and they don't describe a sound anyway. Describe the sound: not "Halo theme" but "Gregorian male choir, epic orchestral, soaring strings, solemn"; not "Star Wars" but "grand symphonic space opera, heroic brass fanfare".
- Franchise terms in the **lyrics** are fine; that's the point of a fan song.
- Write fully original lyrics. Don't reproduce or rework songs that exist in the franchise (official in-game songs, in-universe anthems with published lyrics) and don't copy wiki text into lyrics; offer an original song in that tradition instead.
- In the Notes, list the lore details you used and where they come from, in one or two lines, so the user can check them.

## Step 4: Output format

Always deliver in this order, each paste-ready block in its own code block so the user can copy it with one click:

**Title:** <title, under 80 characters>

**Style** (<N> chars)
```
<style prompt>
```

**Exclude styles** (only if used)
```
<excludes>
```

**Lyrics** (<N> chars)
```
<tagged lyrics>
```

**Suggested settings** - one line: model, Weirdness, Style Influence, Variety, Max Mode, and Vocal Gender if it matters. Pick from the table in `references/suno-controls.md` based on how strict the song's format is. Example: `v6 (Pro+; on Free use v6-mini) · Weirdness 35 · Style Influence 65 · Variety 0 · Max Mode on for the final · Vocal Gender: male`. Never assume the user's Suno plan: if it's unknown, label paid-only models and features as such and give the free alternative; if they've said their plan, tailor to it.

**Notes** - 2-4 short lines max: the key creative choices you made if the user gave little direction, any experimental tags, pronunciation hints, and one practical tip (e.g. "If the chorus comes in too soft, add [Belted] to the chorus tag"). Skip notes that add nothing.

Compute the character counts with code when a code tool is available; otherwise count carefully. If a block is over its limit, trim it before delivering rather than warning about it.

If the user asks for **variations**, give 2-3 versions with different Style prompts (e.g. acoustic vs. synth-pop vs. rock) on the same lyrics, since that's the cheapest way for them to explore in Suno.

If the user asks for an **instrumental**, omit lyrics; give a Style prompt, plus a Lyrics block containing only section tags (e.g. `[Intro]`, `[Build]`, `[Drop]`, `[Breakdown]`, `[Outro]`) to shape the arrangement, and tell them to tick Suno's Instrumental toggle.

## Iterating

Suno is random; the same prompt can give very different results. When the user reports a problem, change one thing at a time and explain what you changed, so the user can tell which change helped. Before adding tags, check whether the problem is actually the writing: a chorus that doesn't land usually needs a stronger, more repeatable hook, not more chorus descriptors, and piling on tags to compensate makes results less predictable. Before suggesting a full regeneration, check whether only one part of an otherwise good take is wrong; if so, suggest Suno's section edit (Replace Section, or a plain-language edit of one section, line or word), since it keeps everything that worked, but these tools can require a paid plan or a higher tier, so say so and always give the any-plan fallback from `references/suno-controls.md` (usually: regenerate 2-3 takes and keep the best, or fix just the problem part's formatting).

Common fixes:
- Wrong genre or feel: move the genre to the very start of Style, remove conflicting descriptors, check Variety is 0 (otherwise Suno rewrites the prompt), and raise Style Influence.
- Results too generic or samey: raise Weirdness (stay under ~90), or try v6-wild for ideas.
- Song drifts or loses consistency over its length: turn on Max Mode.
- Song jumps straight to the chorus or skips sections: make verses clearly distinct from chorus, add `[Intro]` with a short instrumental cue.
- Call and response gets mixed up (calls sung by the group, lines repeated): switch from parentheses to per-turn voice tags, make responses differ from calls, slow the tempo; see `references/tags.md` section 7.
- Tags are being sung: check for round brackets or plain-text labels and convert to square brackets.
- Wrong voice: set Vocal Gender in More Options, put the vocal descriptor earlier in Style, and add the voice tag (e.g. `[Female Vocal]`) to the first sung section.
- Bad pronunciation: respell the word phonetically or swap it for a synonym.
- Abrupt or endless ending: add `[Outro]` with 1-2 short lines, then `[Fade Out]` or `[End]`.
