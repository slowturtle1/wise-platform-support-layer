# Wise Platform Support Layer

A hackathon prototype exploring how Wise's B2B Platform can reduce partner support load through intelligent, corridor-aware support widgets embedded directly in partner apps.

## The Problem

When Wise powers international transfers for partners like Monzo, support tickets spike around transfer delays. Most of these tickets are:

- **Automatable** — delay is expected, corridor-specific, no action needed
- **Actionable** — customer needs to provide something (e.g. RBI purpose code for India)
- **Informational** — settlement windows or AML routing (e.g. Thai baht, US ACH)

Today, these land in human support queues. They don't need to.

## The Solution

A lightweight support widget that Wise exposes as part of its Platform API. Partners embed it in their app. When a customer's transfer is delayed, the widget:

1. Detects the corridor (destination country + currency)
2. Explains the specific reason in plain language
3. Tells the customer exactly what to do (or confirms no action needed)
4. Deflects the support ticket before it's ever raised

## Demo

Single-file HTML prototype — no build step, no dependencies.

**Open `demo.html` in any browser.**

Five tabs:
| Tab | Description |
|-----|-------------|
| Split Bill | Group expense splitting via Wise |
| Fee Saver | Smart fee comparison tool |
| Trip Budget | Multi-currency travel budget tracker |
| Send Money Tracker | Real-time transfer status |
| **Support Widget** | Corridor-aware partner support layer (main concept) |

### Support Widget Scenarios

Switch between three live scenarios from outside the phone mockup:

- **Thailand** — AML routing delay, no action required
- **India** — RBI purpose code missing, customer must act
- **US** — ACH settlement window, informational

## UNFILTERED (experiment)

A separate single-file concept exploring AI model bias: ask a question, pick one or more
models (Claude, ChatGPT, Grok, DeepSeek), and compare how each frames the same question
through its own lens. Includes three demo questions with illustrative per-model responses.

**Open `unfiltered.html` in any browser** — also linked from the nav bar in `demo.html`.

> Responses are simulated illustrations of each model's house style, not live API output.

## Design

- Wise design system: `#163300` navy, `#9FE870` lime, `#00b9a9` teal
- Monzo UI style: iOS-clean, coral accent `#FF3B2F`
- Phone mockup with slide transitions and bottom sheet overlay

## Built for

Wise Hackathon — B2B Platform track
GitHub: [slowturtle1](https://github.com/slowturtle1)
