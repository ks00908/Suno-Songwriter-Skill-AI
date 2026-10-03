# Suno Songwriter: a Claude skill for Suno AI songs

A [Claude](https://claude.ai) skill that turns a vibe, a detailed brief, or your own lyrics into a song you can paste straight into [Suno](https://suno.com): a **Style** prompt, **lyrics marked up with Suno meta tags**, **Exclude styles**, a **title**, and **suggested settings** for Suno's current models.

Once installed, Claude uses it automatically whenever you ask for a Suno song. You don't need to mention the skill.

## What it does

- **Three ways to start.** Give it a one-line vibe, a detailed brief (genre, mood, story, voice), or paste your own lyrics. With your own lyrics it keeps every word and only adds structure and tags.
- **Any language.** Lyrics in the language you ask for, with tags and Style prompt in English (which Suno reads best). Includes specific guidance for Polish lyrics and Polish rap.
- **Suno-safe output.** Character counts checked against Suno's limits, no artist or franchise names in the Style prompt (Suno filters them), stage directions in square brackets so they never get sung.
- **Fan songs with real lore.** For songs set in a franchise (Halo, Star Trek, Star Wars, Warhammer 40k, Elder Scrolls, Tolkien and ~30 more), it looks up the lore on the franchise's primary wiki first (Halopedia, Memory Alpha, Wookieepedia, Lexicanum, UESP...), keeps the era accurate, and writes original lyrics rather than reworking songs from the franchise.
- **Formats that usually break.** Call-and-response cadences, chants, shanties, rap verses, screamed metal, sparse EDM and spoken word each get their own rules.
- **Suggested settings.** Model, Weirdness, Style Influence, Variety and Max Mode recommendations for each song. It doesn't assume your Suno plan; paid-only models and tools are labelled, with a free alternative.
- **Stays current.** Suno retires models when it releases new ones. The skill records when its Suno info was last verified and checks for changes when it has web search.

## Example

> **You:** A running cadence for ODSTs, based on the one in Forward Unto Dawn

Claude checks Halopedia, then returns a Style prompt, Exclude styles, call-and-response lyrics with a voice tag on every turn, and settings. See the full output and three more in [`examples/`](examples/):

| Example | Shows |
|---|---|
| [Klucze](examples/01-klucze-polish-indie-pop.md) | Vibe-only request, Polish lyrics |
| [Empty Chairs](examples/02-empty-chairs-halo-drinking-song.md) | Fan song with lore lookup (Halo, Insurrection era) |
| [Burning Ground](examples/03-burning-ground-odst-cadence.md) | Call-and-response cadence formatting |
| [Stary dom](examples/04-stary-dom-own-lyrics-polish.md) | User's own lyrics converted to Suno format |

## Install

### Claude (web, desktop, mobile)
1. Download [`dist/suno-songwriter.skill`](dist/suno-songwriter.skill).
2. In Claude, go to **Customize > Skills** and upload the file.
3. Make sure the skill is turned on. For fan songs and up-to-date Suno info, also turn on web search.

On Team and Enterprise plans, uploading skills may need to be enabled by your organization owner.

### Claude Code (plugin marketplace)
```
/plugin marketplace add YOUR_GITHUB_USERNAME/suno-songwriter
/plugin install suno-songwriter@suno-songwriter
```

### Manual
Copy `plugins/suno-songwriter/skills/suno-songwriter/` into your skills folder (for Claude Code: `~/.claude/skills/`).

## How to use

Just ask in plain language, for example:
- "Write me a Suno song: melancholic synthwave about a night drive, female vocals"
- "Napisz piosenkę do Suno o jesieni, folk, po polsku"
- "Tag these lyrics for Suno:" followed by your lyrics
- "A Klingon victory chant for Suno"

If a result in Suno isn't right, tell Claude what happened ("the chorus came in too soft", "the squad sang the caller's lines"). The skill includes troubleshooting for common Suno problems and changes one thing at a time.

## Repository layout

```
.claude-plugin/marketplace.json        Claude Code marketplace listing
plugins/suno-songwriter/
  .claude-plugin/plugin.json           Plugin manifest
  skills/suno-songwriter/
    SKILL.md                           Main instructions
    references/tags.md                 Suno meta tag reference and structure templates
    references/suno-controls.md        Models, sliders, editing tools, plan caveats
    references/genre-writing.md        Rap, metal, EDM, ballad, shanty, spoken word rules
    references/lore-sources.md         Primary lore wiki per franchise
dist/suno-songwriter.skill             Packaged skill for upload to Claude
examples/                              Example outputs
```

## Contributing

Suno changes often. If a tag stops working, a limit changes, a new model arrives, or you know a better lore source for a franchise, open an issue or a pull request. Please include the Suno model you tested on and what happened.

After editing the skill, rebuild the `.skill` file by zipping the `suno-songwriter` skill folder (the folder itself, not just its contents) and renaming the extension to `.skill`.

## Disclaimer

Unofficial community project. Not affiliated with or endorsed by Suno, Inc. or Anthropic. Franchise names in the examples belong to their owners; the example songs are original fan works. Tag behaviour and settings are based on community testing and Suno's public information as of the date in `references/suno-controls.md`, and Suno may change them at any time.

## License

[MIT](LICENSE)
