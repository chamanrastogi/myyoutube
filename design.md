# Design System — KANCHAN · Mom & Son Studio

Source of truth for the visual design of the mother-and-son Shorts planner for
[@kanchanrastogi5584](https://www.youtube.com/@kanchanrastogi5584). Everything in
`style.css` derives from the tokens below.

---

## 1. Brief (pinned)

- **Subject**: **Kanchan Rastogi** — a Hindi mother-and-son comedy channel. Every Short is
  a 30-second vertical video: **3 scenes × 10 seconds**, one punchline at the end.
- **Page job**: a creator studio to plan, queue, and shoot from a **1,000-script bank** —
  search it, filter it, save ideas, put three into "today", and copy/download the full script.
- **Brief's own words that win**: Hindi dialogue, "no emojis", realistic 9:16 vertical look,
  mother-and-son family comedy.

## 2. Relationship to the Milky site

This is the sibling of `E:\youtube\youtube` (the Milky/dog planner for @chamanrastogi).
Same shell and behaviour (sidebar + idea bank + today's 3-slot queue + detail drawer),
**different identity**: this channel gets its own palette, display face, and hero device
rather than a recolour of Milky's biscuit-amber-on-brown.

## 3. Two-pass plan and the revision

**First pass (rejected).** Reuse Milky's amber accent and swap the wordmark. That is a
recolour, not an identity, and the two channels would be indistinguishable side by side.

**Revised plan (built).** Ground the design in the subject's world: a Hindi home at night,
where mother and son rehearse a scene. The palette is **wine-plum ink** (the lit room) with
**gulal rose** for action and **marigold gold** reserved for the punchline — the one moment
every Short is built to land. The signature is the **9:16 reel poster** in the hero, showing
an idea the way it will actually ship: vertical, with the on-screen caption baked in.

## 4. Color tokens

| Token | Hex | Role | Note |
|---|---|---|---|
| `--bg` | `#150e13` | Page background | Deep wine-plum ink, warm — not cold `#000` |
| `--panel` | `#1e151b` | Cards, fields | |
| `--panel-2` | `#281b23` | Nested surfaces, active nav | |
| `--line` | `#3b2a34` | Hairline borders | One border colour everywhere |
| `--text` | `#f9eef2` | Body text | Warm blush white |
| `--muted` | `#b7a4ae` | Secondary text | ≥ 4.5:1 on `--bg` |
| `--rose` | `#f2557e` | **Primary action / active** | Gulal rose; contrast on ink ≈ 5.4:1 |
| `--rose-hi` | `#ff7c9e` | Hover / active | |
| `--rose-ink` | `#2b0713` | Text on rose fills | |
| `--gold` | `#f2b64c` | **Punchline / reward** accent | Marigold; used only for punchlines + progress |
| `--teal` | `#5ec8b2` | Published + online dot | |
| `--violet` | `#a08cff` | Saved | |
| `--blue` | `#6fa8ff` | Filmed | |

Rose is the action colour; **gold is spent in one place — the punchline** (card punchline
rule, the reel's caption chip, the progress bar). Keeping them separate is what stops the
page turning into an orange mush.

## 5. Typography

| Role | Font | Why |
|---|---|---|
| Display / wordmark | **Baloo 2** (600–800) | Rounded, friendly, **Devanagari + Latin** in one family — family-comedy warmth, clearly not Milky's condensed poster face |
| Hindi content | **Mukta** (400–800) | Built for Devanagari, natural for conversational Hindi |
| Latin UI | **Outfit** (400–700) | Clean geometric sans for labels, buttons, metadata |
| Utility | **IBM Plex Mono** | Timecodes, shot counts, script numbers stay tabular |

Type scale: wordmark `22px` Baloo 2/700; hero `clamp(2.6rem, 4.6vw, 4.6rem)` uppercase;
idea title `20px` Mukta/600; drawer title `32px` Baloo 2/700; body `14px / 1.5`.

## 6. Layout

Two-column on desktop, single column on mobile. Scenes are read in shooting order, so the
numbered shot markers and the **3-segment scene strip** (10s | 10s | 10s, punchline gold)
encode something true about the format.

```
DESKTOP
+--------+------------------------------------------------------+
| SIDEBAR| TOPBAR                                                |
| 248px  +------------------------------------------------------+
|        | HERO   wordmark + specs + CTA |  9:16 reel poster      |
|        +------------------------------------------------------+
|        | TODAY'S LINEUP  (3 queue slots)                       |
|        | STATS  (ideas / saved / published / progress)         |
|        | LIBRARY  search · filters · idea grid · pagination    |
+--------+------------------------------------------------------+

MOBILE: sidebar hidden, sticky bottom nav; hero stacks (reel under copy).
```

## 7. Signature element

**The 9:16 reel poster** (`#reelFrame`). It shows a Script the way it will ship: vertical,
3 scene segments across the top, the Hindi dialogue-frame text, and the **on-screen caption
baked in as a gold chip** at the bottom. It cycles scenes with `‹` / `›`, shuffles to another
idea with `⟳`, and `Shoot this` drops it straight into today's lineup — so the signature is
also the first useful action on the page.

The single orchestrated motion moment is a soft rise-and-fade of the reel at load
(`.is-live`), disabled under `prefers-reduced-motion`.

## 8. Accessibility floor (non-negotiable)

- Contrast ≥ 4.5:1 for all text (rose on ink ≈ 5.4:1; muted on ink ≈ 5:1).
- One consistent `:focus-visible` ring (2px rose, 3px offset) on every interactive element.
- Skip-to-content link.
- Touch targets ≥ 44px tall for controls (reel buttons, buttons, search, selects).
- `prefers-reduced-motion: reduce` kills the rise and all transitions.
- `scroll-padding-top` so anchors clear the sticky/bottom bars.
- Semantic landmarks: `aside`, `header`, `main`, `section[aria-labelledby]`, `article`, `nav`, `figure`.
- No emoji as icons — text glyphs/SVG only, all decorative bits `aria-hidden`.
- Reel controls carry `aria-label`s; the frame is a labelled `figure`.

## 9. Anti-patterns to avoid

- Don't animate more than one element per view.
- Don't rely on hover for primary actions on touch.
- Don't use emoji as UI icons.
- Don't spend gold on anything except the punchline / progress — it loses its meaning.
- Keep only the bottom nav fixed on mobile; don't stack fixed layers.
