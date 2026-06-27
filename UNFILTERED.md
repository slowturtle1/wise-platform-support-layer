# UNFILTERED

> Ask the question. See the bias.

A standalone hackathon prototype — a separate idea from the Wise Platform Support Layer
that happens to live in the same repo. It's a "news page with no editorial filter": you ask
a question, pick one or more AI models, and compare how each one frames the same question
through its own lens. The point isn't a single truth — it's making each model's **bias**
visible so you can judge for yourself.

## Demo

Single-file HTML — no build, no dependencies.

**Open `unfiltered.html` in any browser.**

## The click-through

A guided, screen-by-screen flow:

1. **Intro** — what UNFILTERED is, and the four model lenses
2. **Pick a question** — three demo questions, or write your own
3. **Choose your models** — Claude, ChatGPT, Grok, DeepSeek (one or many)
4. **Thinking** — per-model loading state
5. **Answers** — side-by-side comparison, each card tagged with the bias on display

A progress rail at the top tracks where you are; every screen has Back / restart navigation.

## The models (and their "lens")

| Model | Lens | House style |
|-------|------|-------------|
| Claude | Careful / nuanced | Slows down, weighs perspectives, flags what it doesn't know |
| ChatGPT | Consensus / balanced | Tidy frameworks, even-handed, institution-friendly |
| Grok | Contrarian / blunt | Anti-establishment, distrusts consensus, direct |
| DeepSeek | Reserved / technical | Optimisation-minded, reserved on contested topics |

## Demo questions

1. You have 100 days to keep humanity alive. What do you do?
2. I need to vote in UK elections, but don't know who to vote for.
3. How has war in Iran occurred?

The UK voting question deliberately has **no model endorse a party** — each instead offers a
neutral method and points to primary sources.

## Important

The responses are **simulated illustrations** of each model's general reputation and house
style — not live API output, not real quotes. They exist to make the idea of "model bias"
visible and debatable. For real decisions (especially how to vote), use primary, authoritative
sources.
