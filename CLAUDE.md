# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project

Static HTML/CSS/JS website for **FireBird Hacks** — a student hackathon at Arcadia High School on May 9th, 2026. No build tools, bundlers, or package manager.

## Development

Open HTML files directly in a browser — no server required. To preview, just open `index.html`.

## File Overview

| File | Purpose |
|------|---------|
| `index.html` | Main page — hero, about, sponsors (commented out), FAQ accordion |
| `tracks.html` | Hackathon tracks (Aerospace, Community & Health, Cybersecurity) |
| `tba.html` | Schedule page — placeholder until schedule is finalized |
| `style1.css` | The one stylesheet used by all pages |
| `style1-new.css` | Revised responsive version of `style1.css` (under review) |

All pages link to `style1.css`. There is no `responsive.css` or `style2.css` — do not reference these.

## CSS Architecture

All styles live in `style1.css`. Sections in order: reset → header/nav → mobile nav → hero → about → sponsors → FAQ → TBA page → tracks page → pre-register form → footer.

The mobile nav breakpoint is `1024px`. The hamburger menu toggles `nav-open` on `<header>` and `no-scroll` on `<body>`.

Clamp values use the pattern `clamp(min, vw-based, max)`. Keep vw multipliers conservative (2–4vw for body text, 5–8vw for headings) to avoid oversizing on large screens. Sections with full-bleed backgrounds need inner content containers with `max-width` to avoid text stretching across very wide screens.

## Sponsor Tiers

The sponsor grid (`index.html`) is commented out pending actual sponsors. Tier classes are `.mega-bird`, `.phoenix`, `.ember`, `.spark` with descending logo sizes. The mobile carousel logic (auto-rotate every 5s on `<=1024px`) is in the inline script at the bottom of `index.html`.

## Known Issues / Placeholders

- `LINK_TO_DOC` placeholder in the Chromebook FAQ answer (`index.html` line ~332) needs a real URL
- Sponsor section is fully commented out — uncomment and populate when sponsors are confirmed
- `tba.html` schedule content is a placeholder
