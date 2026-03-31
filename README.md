# LLM Council

A browser-based decision tool that runs any question through 5 independent AI advisors, has them peer-review each other anonymously, then synthesises a final verdict from a chairman.

Adapted from [Andrej Karpathy's LLM Council](https://x.com/karpathy) methodology — multiple independent perspectives, anonymous peer review, one synthesised answer.

---

## How it works

1. **5 advisors** analyse your question independently, each from a distinct thinking style:
   - 🔴 The Contrarian — finds the fatal flaw
   - 🔵 First Principles Thinker — strips the problem to its core
   - 🟢 The Expansionist — finds the upside being missed
   - ⚪ The Outsider — sees what experts can't
   - 🟡 The Executor — asks "what do you do Monday morning?"

2. **Peer review** — all 5 responses are anonymised and each advisor reviews the full set

3. **Chairman synthesis** — one final pass over everything: where the council agrees, where it clashes, blind spots caught, a clear recommendation, and the one thing to do first

---

## Setup

No server, no backend, no build step. Single HTML file.

1. Clone or download this repo
2. Open `index.html` in any browser
3. Enter your [Anthropic API key](https://console.anthropic.com/) — it saves to `localStorage` and persists across sessions
4. Ask the council anything

**Or use the hosted version:** `https://yourusername.github.io/llm-council`

---

## Cost

~$0.10 USD per full council session (11 API calls to `claude-sonnet-4-20250514` at $3/$15 per million tokens).

---

## Best use cases

Good council questions have genuine uncertainty and a meaningful cost to getting it wrong:

- "Should I take this job offer or stay and negotiate?"
- "Which of these two positioning angles is stronger for my consulting practice?"
- "I'm thinking of pivoting from X to Y — what am I missing?"
- "Here's my proposal. What's the weakest part?"

Not suited for factual lookups, simple yes/no questions, or tasks with one clearly correct answer.

---

## Privacy

Your API key is stored in your browser's `localStorage` only. It is never sent anywhere except directly to `api.anthropic.com` in the API call. The repo contains no backend, no analytics, and no tracking.

---

## Tech

- Vanilla HTML/CSS/JS — no frameworks, no dependencies
- Calls `api.anthropic.com/v1/messages` directly from the browser using `anthropic-dangerous-direct-browser-access: true`
- All 5 advisor calls and all 5 peer review calls run in parallel via `Promise.all`

---

## License

MIT
