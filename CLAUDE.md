# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static HTML/CSS/JS website for **FireBird Hacks** — a student hackathon at Arcadia High School in Oak Hall, VA. No build tools, bundlers, or package manager. The event date is not yet finalized (shown as "TBA" / "March ??, 2027" on the site); do not hardcode a specific date until one is confirmed.

## Development

Open HTML files directly in a browser, or serve the folder locally (e.g. `python -m http.server`) — no build step required.

## File Overview

| File | Purpose |
|------|---------|
| `index.html` | Main page — hero, about, sponsors, FAQ accordion |
| `tracks.html` | Hackathon tracks (Aerospace, Community & Health, Cybersecurity) |
| `tba.html` | Schedule page — notepad-style run of show (times may still shift) |
| `register.html` | Old/unused page, not linked from the nav. Kept around but not actively maintained — still on `style1.css` (see below) |
| `style1-small.css` | The stylesheet actually used by `index.html`, `tracks.html`, and `tba.html` |
| `style1.css` | Original stylesheet, now only used by the orphaned `register.html` |
| `style1-new.css` | An earlier revised/responsive pass, not currently linked by any page |

Despite the similar names, these three CSS files have diverged — don't assume a fix in one is present in the others. When editing a live page, confirm which stylesheet its `<link>` tag actually points to before touching CSS.

## CSS Architecture

Styles for the live site are in `style1-small.css`. Sections in order: reset → header/nav → mobile nav → hero → about → sponsors → FAQ → TBA/schedule page → tracks page → pre-register form → footer.

The mobile nav breakpoint is `1024px`. The hamburger menu toggles `nav-open` on `<header>` and `no-scroll` on `<body>`.

Clamp values use the pattern `clamp(min, vw-based, max)`. Keep vw multipliers conservative (2–4vw for body text, 5–8vw for headings) to avoid oversizing on large screens. Sections with full-bleed backgrounds need inner content containers with `max-width` to avoid text stretching against very wide screens.

## Sponsor Tiers

The sponsor grid (`index.html`) currently shows two confirmed sponsors (Taylor Bank, ANEC) in a single `.tier.spark` block. The old placeholder tier markup (`.mega-bird`, `.phoenix`, `.ember`, plus more `.spark` slots) is still present but commented out — uncomment and populate tiers as more sponsors are confirmed. The mobile carousel logic (auto-rotate every 5s on `<=1024px`) is in the inline script at the bottom of `index.html`.

## Schedule Page (`tba.html`)

Styled as a red-and-white notepad: a red header band for date/status notes, a white ruled body (internal scroll via `.schedule-body`, capped at `60vh` so the page itself doesn't grow long) with a gold margin rule, handwriting-style (`Caveat` font) times, and dashed dividers between entries — no boxed cards/dots. Event times reflect the 2027 judge/volunteer packet run-of-show (confirmed current over the older 2026 proposal doc, which has slightly different times for team registration and the hard submission deadline).

## Known Issues / Placeholders

- `LINK_TO_DOC` placeholder in the Chromebook FAQ answer (`index.html` line ~355) needs a real URL — intentionally left as-is, page is still in progress
- Event date is unconfirmed — schedule page shows times of day only, no calendar date
- Meal/food details are still being finalized (budget pending) — FAQ answer on `index.html` reflects this rather than promising specifics
