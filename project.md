# Project — कंचन मॉम & सन स्टूडियो

A one-page **creator studio** that holds the ready-to-shoot script bank for the Hindi
mother-and-son comedy Shorts on [@kanchanrastogi5584](https://www.youtube.com/@kanchanrastogi5584).

Sibling project of the Milky planner at `../youtube` — same shell, its own identity.

## What the site does

- **Idea bank** — all 1,000 scripts (title, premise, punchline) with search, category
  filter, status filter, and pagination.
- **Today's lineup** — a 3-slot queue of the ideas you plan to shoot today.
- **Detail drawer** — every scene's visual, Hindi dialogue, background sound, on-screen
  text, plus video instructions, characters, hashtags, notes, and production status.
- **Copy / download** — one-click copy of a full script, a single scene, the video
  instructions, or the hashtags; plus a `.txt` download.
- **Hero reel** — a 9:16 preview of a random idea; step through its 3 scenes, shuffle to
  another idea, or send it straight to today's lineup.
- Everything persists locally (queue, saved, statuses, notes) via `localStorage`.

## Files

| File | Purpose |
|---|---|
| `index.html` | The app. Fonts (Baloo 2, Outfit, Mukta, IBM Plex Mono) + `style.css` + data script. |
| `style.css` | Theme layer: design tokens, component styling, focus/motion rules. |
| `mother_son_1000_full_youtube_shorts_scripts.json` | Source data: 1,000 scripts. |
| `mother_son_1000_full_youtube_shorts_scripts.js` | The same data wrapped as `window.MOTHERSON_FULL_SCRIPTS` for the page to load. |
| `design.md` | **Design source of truth** — tokens, typography, layout, signature, a11y. |
| `project.md` | This file — what it is, how to run, how to extend. |
| `README.md` | Short orientation for anyone opening the folder. |

## Run it

Static files — no build step.

```
start index.html            # Windows: double-click it, or:
npx serve .                 # optional local server, or: python -m http.server 8080
```

## Data shape

```jsonc
{
  "project": "YouTube SEO Expert - Chaman Rastogi",
  "language": "hi",
  "format": { "video_type": "YouTube Shorts", "duration_seconds": 30, "scene_count": 3, "style": "Hindi mother and son comedy", "aspect_ratio": "9:16" },
  "total_scripts": 1000,
  "scripts": [
    {
      "id": 1,
      "title": "होमवर्क का बहाना",
      "category": "Mother Son Comedy",
      "characters": ["Mother", "Son"],
      "duration_seconds": 30,
      "scene_count": 3,
      "scenes": [
        { "scene_number": 1, "time": "0-10 सेकंड", "heading": "…", "visual": "…",
          "dialogues": [ { "speaker": "मम्मी", "line": "…" } ],
          "background_sound": "…", "screen_text": "…" }
      ],
      "video_instructions": "…",
      "status": "script_ready"
    }
  ]
}
```

Eight categories, 125 scripts each: Mother Son, Family, School, Desi, Everyday, Food,
Phone, Study Comedy.

## Regenerating the data script

If the JSON changes, rebuild the browser file:

```
node -e "const fs=require('fs');const j=JSON.parse(fs.readFileSync('mother_son_1000_full_youtube_shorts_scripts.json','utf8'));fs.writeFileSync('mother_son_1000_full_youtube_shorts_scripts.js','window.MOTHERSON_FULL_SCRIPTS = '+JSON.stringify(j)+';\n','utf8');"
```

## How to extend

- **New palette / type** — edit the tokens at the top of `style.css`; update `design.md`.
- **New field on a script** — add it to the data, then surface it in `card()`,
  `sceneMarkup()`, or `openDrawer()` in `index.html`.
- **More queue slots** — change the `3` literals in the queue logic and the `queue-grid`.

## Content rules (from the channel brief)

- Natural, conversational Hindi — not literary Hindi — in the dialogue.
- No emojis in dialogue, titles, descriptions, tags, or hashtags.
- 30-second default: 3 scenes × 10 seconds; hook in scene 1, punchline in scene 3.
- Comedy comes from the mother-and-son back-and-forth and reactions, not long lines.
- Hashtags: `#KanchanRastogi #MotherSonComedy #HindiComedy #YouTubeShorts` + category/characters.

## Verification checklist

Open `index.html` and check, at mobile and desktop widths:

- [ ] No horizontal scrolling at 360px wide
- [ ] Hero reel loads without a console error and the "Scripts data is missing" screen never appears
- [ ] Sticky bars never cover a section heading after clicking a nav link
- [ ] Tab through the page — focus ring is visible on every control
- [ ] Reel `‹` / `›` / `⟳` change the preview; `Shoot this` adds to today's lineup
- [ ] Reel rise is absent when the OS "reduce motion" setting is on
- [ ] Copy buttons change label (e.g. "Copied") after a click
