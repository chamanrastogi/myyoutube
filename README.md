# KANCHAN · Mom & Son Studio

A creator studio for the Hindi mother-and-son comedy Shorts on
[@kanchanrastogi5584](https://www.youtube.com/@kanchanrastogi5584).

Search a bank of **1,000 ready-to-shoot scripts**, queue three for today, and copy or
download any full script — 30-second vertical Shorts, 3 scenes × 10 seconds.

Sibling of the Milky planner (`../youtube`); same shell, its own warm wine-and-rose look.

## Files

| File | What it is |
|---|---|
| `index.html` | The app. Fonts (Baloo 2, Outfit, Mukta, IBM Plex Mono) + `style.css` + data script. |
| `style.css` | Theme layer: design tokens + component styles. |
| `mother_son_1000_full_youtube_shorts_scripts.js` | The 1,000 scripts, loaded as `window.MOTHERSON_FULL_SCRIPTS`. |
| `mother_son_1000_full_youtube_shorts_scripts.json` | Source data. |
| `design.md` | **Design source of truth** (tokens, type, layout, signature, a11y). |
| `project.md` | What the project is, how to run and extend it. |
| `README.md` | This file. |

## Open it

No build step. Double-click `index.html`, or:

```
npx serve .
```

## What's on the page

- Hero with the wordmark and a **9:16 reel poster** previewing a random idea (step through
  scenes, shuffle, or "Shoot this")
- Today's lineup — 3 queue slots
- Studio stats — ideas, saved, published, pipeline progress
- Idea bank — search, category + status filters, pagination
- Detail drawer — scenes, dialogue, sound, screen text, video instructions, hashtags, notes
- Copy / download for full scripts, single scenes, instructions, and hashtags

## Ground rules

- Natural conversational Hindi; no emojis in content.
- 30-second Shorts: hook in scene 1, punchline in scene 3.
- Gold is reserved for the punchline — nothing else.

## Docs

- Design details → `design.md`
- Running and extending → `project.md`
