# Stitch Briefs — Wise Platform Support Layer

Prompts for generating design iterations of this product in **Google Stitch**.

**How to use:** one surface per generation. Paste the **Brand block** first, then a **screen prompt**, then iterate one change at a time. Set the right canvas mode per surface (Mobile vs Web). Stitch makes *static* screens — add motion and the live "ticket dissolves" beat back in code afterward.

---

## Brand block — prepend to EVERY prompt

```
Design system — Wise Platform. Two brand colors only:
Forest Green #163300 (dark surfaces, primary text, primary buttons) and
Bright Green #9FE870 (accents, highlights, CTAs on dark, status pills).
Backgrounds near-white #F7F8F4 and white cards; text #1A1A1A, secondary green-grey #5F6B58.
Soft positive/AI surfaces: light-green tint #F1FAE8, border #CFEAB0, dark-green text #21501A.
No teal, no blue. Font: Inter — heavy tight headlines (700–900), clean body.
Geometry: large rounded corners (16–24px cards, fully-rounded pill buttons), generous spacing, calm.
Tone: trustworthy, plain-language, fintech-premium. WCAG-AA contrast.
```

---

## Per-surface prompts

### A · Embedded support widget — `Mobile` (core surface)
```
Mobile screen: a banking app transaction-detail view with a support bottom-sheet overlay.
Sheet title "Your transfer to Germany is delayed". Inside: a small "WISE · AI" pill;
a diagnosis card (light-green tint) explaining a SEPA batch cut-off in plain language;
a vertical 4-step transfer-progress timeline (Payment received ✓, Missed SEPA batch ✓,
Processing in next batch ⏳ with an ETA chip, Delivered — pending); an AI-explanation text block;
a primary bright-green button "Got it — that answers my question"; a secondary "Chat with AI" button;
a subtle "Contact support" link; "powered by Wise Platform" footer.
```

### B · Proactive push + lock screen — `Mobile`
```
Mobile lock screen, dark gradient. A notification card from a banking app:
title "Transfer to Germany delayed", body "Your £750 to Klaus missed today's SEPA batch. Tap for details.",
with a small "WISE — delay context" badge. Calm, premium, glassy notification.
```

### C · Support agent console — `Mobile` (the other side of the story)
```
Mobile support-agent inbox on a dark forest-green header. Title "Support Queue · Wise Platform Partners",
tabs Open/Resolved/All. A highlighted NEW ticket (bright-green pill) "Transfer delay — SEPA cut-off, via Monzo",
auto-tagged, with an AI-suggested reply preview. Below: a list of resolved tickets with green check dots.
Then a ticket-detail view: transfer fields, an AI diagnosis card, and a primary "Mark resolved" button.
```

### D · Partner analytics dashboard — `Web` (sells the buyer)
```
Web dashboard "Wise Platform — Support Insights". Top row of stat cards: tickets deflected,
deflection rate %, support cost saved (£), avg resolution time. A bar chart of weekly delay tickets
before/after the widget. A table of deflection rate by corridor (EU/SEPA, India/RBI, US/ACH).
Clean, lots of whitespace, white cards on near-white background, bright-green data accents.
```

### E · India action flow (purpose code) — `Mobile`
```
Mobile support bottom-sheet, title "Your transfer to India needs attention".
Diagnosis card (light-green tint): "India's Reserve Bank requires every international transfer to
declare its purpose — your transfer is on hold until you confirm this." A 4-step timeline with an
"Action required — waiting on you" step. An action card on dark forest-green with label "Action required",
text "Select the purpose of your transfer to India", and a bright-green button "Confirm transfer purpose →".
Then a purpose-code picker list (Family maintenance, Salary, Education, Gift, Investment).
```

---

## Iterating inside Stitch
- **One change per turn**: "make the timeline horizontal", "tighten card spacing", "darker header" — don't rewrite the whole prompt or it drifts off-brand.
- **Re-pin the brand** if colors wander: "keep the palette to #163300 and #9FE870 only — remove any teal/blue."
- **Ask for variants explicitly**: "give me 3 layouts for the diagnosis card."
- **Mobile vs Web**: A/B/C/E = Mobile, D = Web.
- Stitch exports HTML/CSS + Figma — a winning iteration can be folded back into `demo.html`.

## What Stitch won't do
- Scroll-reveal motion / the live "ticket dissolves" + deflection-counter beat → add in code (see `CLAUDE.md` motion section).
- Real corridor logic / live Claude AI text → already wired in `demo.html`.
