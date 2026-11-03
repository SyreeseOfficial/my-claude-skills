---
name: podcasts
description: Organize my Obsidian podcast tracker files and create missing episode notes. Only run when the user invokes /podcasts (optionally with args like "/podcasts JRE 348" or "/podcasts Lex"). Do not trigger on general podcast talk.
---

# /podcasts

Vault: `/home/sy/Documents/Panacea`. Trackers (one bullet list of `[[wikilinks]]` per show):

| Show | Tracker | Note prefix |
|---|---|---|
| JRE | `Done/JRE Podcast.md` | `JRE <num> <Guest>` |
| Theo Von | `Done/Theo Von Podcast.md` | `Theo Von <num> <Guest>` |
| Shawn Ryan | `Done/Shawn Ryan Podcast.md` | `Shawn Ryan <num> <Guest>` |
| Modern Wisdom | `Done/Modern Wisdom Podcast.md` | `Modern Wisdom <num> <Guest>` |
| Lex Fridman | `Done/Lex Fridman Podcast.md` | `Lex Fridman <num> <Guest>` |
| Dropping Bombs | `Dropping Bombs Podcast.md` (move into `Done/`) | `Dropping Bombs <Guest>` (no numbers) |

With an arg, only touch the matching show or episode. With none, do all trackers. The user listens while driving and jots bare numbers (e.g. `348`) or half-formed entries, so expect messy input.

## Rules (the user decided these; don't re-ask)

1. **Plan first, apply after OK.** Read everything, then show one summary (table of changes, proposed names, creations, flags). Edit nothing until the user approves.
2. **Sort** each tracker by episode number ascending. Unnumbered entries go at the end, alphabetical.
3. **Clean up automatically** (as part of the plan): stray backticks, empty `- ` bullets, trailing spaces, exact duplicate lines. Fold the `Sort` pile into the main list. Same guest on different episode numbers is NOT a duplicate.
4. **Fix guest name typos** in link text and rename the note file to match (e.g. `Marc Andressen` -> `Marc Andreessen`). Renaming in Obsidian breaks other links, so grep the vault for `[[Old Name` and update those too.
5. **Aliases** (`[[A|B]]`): never change one silently. List each in the plan and ask what to do.
6. **Bare numbers / half entries** (`348`, `Theo Von 590`): web-search the episode to get the guest, propose the full name as `<Prefix> <num> <Guest>` in the plan. Only rewrite after approval.
7. **Missing notes**: for every tracker link whose file doesn't exist (search the vault root AND `Done/`, Obsidian resolves by name anywhere), create the note in the **vault root** `/home/sy/Documents/Panacea/<exact link name>.md`. Never overwrite an existing note.
8. **Note body**: first line `*Auto-summary*` (so generated notes are distinguishable from the user's own), then a bullet-point summary written in your own words from a web search (no pasted descriptions). 5-8 bullets, no frontmatter, tags, or backlinks. Use the same format for boring episodes.
9. **Multi-guest episodes**: include every guest in the name (`Modern Wisdom 1148 Gabrielle Lyon, Ben Greenfield, Brigham Buhler`).
10. **Existing thin notes** (file exists but has little or no summary): never edit on your own. List them in the plan and let the user choose per note.
11. **Unknown show** (not in the table): offer to create `Done/<Show> Podcast.md`, don't create it unasked.
12. **Unclear entries** (can't identify the episode, ambiguous guest): leave untouched, list them at the end under "Couldn't identify".

## Flow

1. Read the trackers in scope; list existing note filenames (`find` vault, `-name "*.md"`).
2. Web-search each bare number and each missing note's episode. With more than a handful, fan the lookups out to parallel subagents (one per show or chunk of ~10) and collect their results before planning.
3. Present the plan: cleanups, sorts, renames, aliases to decide, notes to create, unclear entries.
4. On approval: apply edits, create notes, move Dropping Bombs tracker if not yet moved.
5. Report in 3 lines: what changed, how many notes created, what's still unclear.

If a search can't confirm the guest or content, don't invent a summary. Flag it as unclear instead.
