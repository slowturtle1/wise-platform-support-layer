# Wise Platform Support Layer

A hackathon prototype for the **Wise Platform (B2B) track**. It shows how Wise can turn data only Wise has — live transfer, corridor, and settlement status — into a support layer that partner banks embed in their own apps to stop cross-border delay tickets before they're raised.

## The idea in one line

> Wise already knows *why* a customer's transfer is stuck — so it explains it to them, and the partner's support team never has to.

## Why this is different from generic AI support

Tools like Intercom Fin answer from the *partner's* knowledge base — which knows nothing about a live SEPA cut-off or a pending RBI purpose code. Only Wise sees the per-transfer state. The moat is **data, not the model**: corridor rules, settlement calendars, and AML routing that no partner (and no horizontal CX tool) can replicate.

- **Buyer:** the partner's Head of Payments / Embedded Finance (who owns the Wise relationship), not the CX team.
- **Pain:** cross-border "where's my money" tickets are the costliest, least-deflectable category (~£8–50 each).

## How it works

1. Partner's app queries Wise Platform for transfer status + corridor metadata.
2. The embedded widget renders the right plain-language explanation for that corridor.
3. The customer is either reassured (no action) or resolves the action in-app.
4. The ticket is deflected — or, if escalated, it reaches the agent **pre-diagnosed**.

Each delayed transfer falls into one of three buckets:

| Bucket | Example | Outcome |
|--------|---------|---------|
| **Automatable** | EU/Germany SEPA batch cut-off; US ACH window | No action needed — reassure |
| **Actionable** | India RBI purpose code missing | Customer resolves it in-app |
| **Informational** | Settlement / AML routing timing | Explained, or routed to agent |

## Demo

Single-file HTML prototype — no build, no dependencies. **Open `demo.html` in any browser.**

A landing page wraps an interactive **dual-phone mockup**:

- **Customer phone (Monzo-style)** — lock-screen push → transaction detail → bottom-sheet support widget with an AI diagnosis card, delivery timeline, action/OK cards, a typewriter AI explanation, and a floating AI chat popup.
- **Agent phone** — the partner's support inbox. Escalated tickets arrive pre-diagnosed and auto-tagged with a one-tap suggested reply.

### What to click

1. Tap the lock-screen notification → read the corridor explanation.
2. Tap **"Got it — that answers my question."** Watch a ticket **appear on the agent phone and dissolve** ("Ticket avoided"), and the live **deflected-today counter** tick up.
3. Or tap **"Contact support →"** to see the *escalation* path: the agent gets a pre-diagnosed ticket instead of a blank one.

### Scenarios (toggle outside the phone)

- **🇩🇪 EU · SEPA cut-off** — no action needed
- **🇮🇳 India · RBI purpose code** — customer must act
- **🇺🇸 US · ACH window** — informational

### Optional live AI

Paste a Claude API key in the demo to switch the explanations and chat from canned text to live `claude-haiku-4-5` responses. Works fully without a key (demo mode).

## ROI framing (kept defensible)

- £8–50 per delay ticket and 40–76% generic AI deflection are citable industry numbers.
- Deflection *within the corridor-delay category* runs above the generic ~40% ceiling because these tickets have deterministic, known causes.
- The demo deliberately avoids inventing absolute ticket volumes.

## Design

- Wise system: `#163300` navy, `#9FE870` lime, `#00b9a9` teal
- Monzo-style customer UI; dark agent-console UI
- Phone mockups with slide transitions, bottom sheet, and a live deflection meter

## Built for

Wise Hackathon — B2B Platform track · GitHub: [slowturtle1](https://github.com/slowturtle1)
