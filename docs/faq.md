# FAQ — CBini OrquestrAI

🇺🇸 **English** · 🇧🇷 [Português](faq-br.md) · 🇪🇸 [Español](faq-es.md)

**Is OrquestrAI an AI?**
No. It is an engineering layer that coordinates AI models and providers, specialized agents, per-project context, supervised execution,
audit and reversibility, with a person deciding where a change becomes real.

**Does it replace developers?**
No. It organizes AI work so a team can use it under governance: someone defines the intent, reviews and approves.

**Is context tied to one model? Do projects share memory?**
Context belongs to the project: the operator can switch models and the next one receives the same context. Another project starts from
its own context and does not inherit the first one.

**Is OrquestrAI open source?**
No. This repository is the public showcase and documentation. The product source code is private; this project is not distributed as open-source software, and its licensing model is currently being defined.

**Is this repository the source code?**
No. It contains only public documentation. The product is developed in a private repository.

**What is available today, and what is in validation?**
See the maturity table in the [README](../README.md#current-maturity). *Available* means proven by automated tests and by a human operator
on a live deployment; *in validation* means built and tested but not yet promoted.

**Does the AI execute changes on its own?**
No. The chat never executes. Every concrete change becomes a command block that runs only after a person reviews and confirms it.

**What does "reversible" mean here?**
For supported changes, the system records what a change may touch and measures what it actually changed; undoing it shows what will be
reverted before doing it. Data written by a running application is outside this mechanism by design; it is protected by the nightly backup instead. Undoing a
change to a full-stack application restores its code and republishes the previous version; database columns already added are kept,
so no data is lost.

**Does my data stay on my server?**
OrquestrAI runs on infrastructure you control. When external AI providers are used, the content sent to those providers is subject to
their respective services and policies. You choose which providers to configure.

**Which AI providers are supported?**
The validated agent routes use Anthropic and OpenAI models today. Groq, Gemini, OpenRouter, Cerebras, Z.ai and OpenAI-compatible APIs can
be configured and tested from the control panel.

**Can it build full applications?**
Yes, within one supported path. Static websites and the first full-stack path (React + Vite + TypeScript, Express, SQLite) work end to end
today; a generated application has one data model and evolves through additive changes you approve.

**Can I install it myself?**
Today installation follows a documented manual procedure. A guided installer is planned.

**How can I give feedback?**
Through this repository's Discussions and Issues once enabled. Please do not report security issues publicly.

[← Back to README](../README.md)
