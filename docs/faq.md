# FAQ — CBini OrquestrAI

🇺🇸 **English** · 🇧🇷 [Português](faq.pt-BR.md)

**Is OrquestrAI open source?**
No. This repository is the public showcase and documentation. The product source code is private; licensing and commercial terms are under preparation.

**Is this repository the source code?**
No. It contains only public documentation. The product is developed in a private repository.

**What is available today, and what is in validation?**
See the maturity table in the [README](../README.md#current-maturity). *Available* means proven by automated tests and by a human operator
on a live deployment; *in validation* means built and tested but not yet promoted.

**Does the AI execute changes on its own?**
No. The chat never executes. Every concrete change becomes a command block that runs only after a person reviews and confirms it.

**What does "reversible" mean here?**
For supported changes, the system records what a change may touch and measures what it actually changed; undoing it shows what will be
reverted before doing it. Data written by a running application is outside this mechanism by design; backing up application data
is part of the full-stack work in validation.

**Does my data stay on my server?**
OrquestrAI runs on infrastructure you control. When external AI providers are used, the content sent to those providers is subject to
their respective services and policies. You choose which providers to configure.

**Which AI providers are supported?**
The validated agent routes use Anthropic and OpenAI models today. Groq, Gemini, OpenRouter, Cerebras, Z.ai and OpenAI-compatible APIs can
be configured and tested from the control panel.

**Can it build full applications?**
Static websites work end to end today. The first full-stack path (React + Vite + TypeScript, Express, SQLite) is in validation.

**Can I install it myself?**
Today installation follows a documented manual procedure. A guided installer is planned.

**How can I give feedback?**
Through this repository's Discussions and Issues once enabled. Please do not report security issues publicly.

[← Back to README](../README.md)
