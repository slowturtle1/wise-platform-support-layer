# WiseHackaton — Project Guide

## What this is
A hackathon prototype: **Wise Platform Support Layer** — a corridor-aware support widget Wise exposes via its B2B Platform API so partner apps can deflect cross-border delay tickets.

**The whole app is a single static file: `demo.html`.** No build, no framework, no npm, no bundler. Plain HTML + CSS + vanilla JS. Open it directly in a browser. Keep it that way unless asked otherwise.

---

# Motion Stack Guide (adapted for this project)

> ⚠️ **Project reality:** The original motion-stack guide assumes a **React/Next.js + Framer Motion + GSAP + Lenis** stack. **None of those exist here** — this is a static HTML file. Do **not** introduce React, a build step, or any of those libraries. Instead, honor the motion *language* below using **vanilla CSS transitions + IntersectionObserver**, which is how motion is already implemented in `demo.html`.

## Motion language
All motion should feel:
- **Unhurried** — nothing snaps or pops; things drift into place.
- **Confident** — no bounce or overshoot; elements arrive and stay.
- **Quiet** — motion supports content, never competes with it.

A page that *breathes* rather than *performs*.

## Standard values (the motion DNA)
```
Ease:            cubic-bezier(0.22, 1, 0.36, 1)   (soft deceleration)
Duration:        0.8s–1.2s  scroll reveals
                 1.2s–1.4s  large elements / hero
                 0.6s–0.9s  small UI elements / labels
Max Y offset:    16–32px    (subtle, never theatrical)
Max X offset:    0px        (vertical movement only)
Stagger gap:     0.12s per item
Viewport trigger: fire ~15% early  →  IntersectionObserver rootMargin "0px 0px -15% 0px"
```

## How it's implemented in `demo.html`
Landing-page sections use a `.reveal` system (see the `SCROLL MOTION` CSS block and the `initReveals()` IIFE at the end of the script):

- `<html>` gets `.js-anim` from an inline `<head>` script **before first paint** (prevents FOUC); skipped under `prefers-reduced-motion: reduce`.
- `.reveal` starts at `opacity:0; translateY(--reveal-y)`; adding `.in` animates it to rest. Per-element tuning via CSS vars `--reveal-y`, `--reveal-dur`, `--reveal-delay`.
- `.reveal-fade` = opacity-only (used for labels and the sticky `.phones-pair`, so transforms don't break `position: sticky`).
- Hero + stats are tagged **in the HTML** (above the fold → no flash). Below-the-fold sections are auto-tagged by selector in `initReveals()`.
- One `IntersectionObserver` reveals each element **once** (`unobserve` after firing).

When adding new landing content, tag it the same way: above-the-fold → class in HTML; below → add a selector in `initReveals()`.

## Patterns
- **Hero entrance** (on load): title → fade up 24px / 1.2s; subtitle → 16px / 1.0s / 0.3s delay; CTA → 16px / 1.0s / 0.55s delay; metadata → fade-only, last.
- **Scroll reveal** (most common): fade up 16–24px, 0.8–1.0s, once.
- **Staggered list**: per item fade up 16px / 0.9s, delay `i × 0.12s`.
- **Opacity-only** (eyebrows, labels): fade in, no movement.

## Anti-patterns (avoid)
- Re-triggering animations — always reveal **once**.
- Horizontal movement on scroll — **vertical only**.
- `spring` / `bounce` easing — use `cubic-bezier(0.22, 1, 0.36, 1)`.
- Translating more than 32px.
- Layout shift — only animate `opacity` / `transform`.
- Skipping `prefers-reduced-motion` — it's an accessibility requirement.
- Adding motion libraries or a build step to this static file.

## In-phone UI motion
The phone-mockup interactions (screen slides, bottom sheet, chat popup) intentionally use **faster** transitions (~0.35s) — they're direct UI responses, not ambient scroll motion. Leave those snappy; apply the slow scroll-reveal language to **landing-page sections** only.

---

# Design system (Wise brand)
- **Two brand colours only:** Forest Green `#163300` (`--forest`/`--navy`) and Bright Green `#9FE870` (`--bright`/`--lime`). No teal/blue accents.
- Soft positive/AI surfaces use the bright-green tint tokens: `--tint-bg #f1fae8`, `--tint-bg2 #e4f3d4`, `--tint-bd #cfeab0`, `--tint-ink #21501a`.
- Status badges = bright-green pill + forest text. Dark surfaces = forest bg + white/bright text (WCAG-safe).
- Type: headlines would use **Wise Sans** (proprietary, not bundled) → currently **Inter** (Wise's official secondary). Body = Inter.

# Running / verifying
- Just open `demo.html`, or serve: `python -m http.server 8765` then visit `http://127.0.0.1:8765/demo.html`.
- Optional live AI: paste a Claude API key in the demo to swap canned text for live `claude-haiku-4-5`. Works fully without a key.
