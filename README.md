# CBini OrquestrAI

![Self-hosted](https://img.shields.io/badge/deployment-self--hosted-2f3b4c) ![Human in the loop](https://img.shields.io/badge/governance-human--in--the--loop-2f3b4c) ![Node.js 24](https://img.shields.io/badge/Node.js-24-2f3b4c) ![Status](https://img.shields.io/badge/status-active%20development-2f3b4c)

🇧🇷 Built in Brazil by CBini Soluções em TI

🇺🇸 **English** · 🇧🇷 [Português](README.pt-BR.md)

[Why](#why-orquestrai) · [How it works](#how-it-works) · [Architecture](docs/technical-overview.md) · [Security](docs/security-model.md) · [Maturity](#current-maturity) · [Roadmap](docs/roadmap.md) · [FAQ](docs/faq.md) · [Feedback](#feedback)

**The engineering layer around AI: agents propose, people decide, the system keeps the evidence.**

A self-hosted cockpit where specialized AI agents plan and build software, every change waits for human approval,
runs in isolation, and can be traced, measured and undone.

---

## Why OrquestrAI

AI can already write a large share of the code for real applications. Production needs more than code: someone must decide what is
allowed to run, keep one project from touching another, prove what changed, undo mistakes, and account for what it cost.

OrquestrAI is built for that part. It does not try to make the model smarter. It makes AI engineering **governed, observable,
reversible and economically controllable** — on infrastructure you choose.

**AI agents are engines. OrquestrAI is the engineering layer that decides how their work becomes real.** It does not replace the best
models or coding agents — it organizes, governs, isolates, measures and records their work, so models can change without the governance
changing with them.

## Built from the execution boundary inward

OrquestrAI did not start with features. It started with the question *what happens when AI output touches a real system* — and answered
it first: human confirmation, isolated execution, measured and reversible changes, tamper-evident records, cost accounting, encrypted
backups and recovery procedures, and fail-closed behavior at critical points. Every capability is counted only after an automated test
and a human operator have both proven it. Features are built on top of that foundation, not beside it.

## The principle

> **AI proposes. People decide. The system keeps the evidence.**
>
> The AI builds the product. OrquestrAI lays the track. You decide where it goes.

## What makes it different

| | |
|---|---|
| **Human approval at the critical point** | The chat never executes. Every concrete change becomes a reviewable command block that runs only after a person confirms it. |
| **Explain before you approve** | Any proposed change can be explained in plain language — intent, steps, impact, risk — without running anything. |
| **Isolated execution** | Approved commands run in a disposable, network-less, unprivileged environment that sees only their own project. |
| **Reversible operations** | The system records what a change may touch and measures what it actually changed; undo shows what will be reverted first. |
| **Evidence by default** | Executions are recorded in a tamper-evident chain; terminal sessions are sealed. You can see who proposed, who approved and what ran. |
| **Chat, command and terminal are different things** | Conversation, change and inspection are separate surfaces with separate permissions. The project terminal is read-only. |
| **Specialized agents** | A planner assembles a team of specialized agents per task — strategy, architecture, code, review, testing, documentation. |
| **Cost visibility** | Every model call is attributed to project, agent and surface. Unknown prices stay unknown instead of becoming zero. |
| **Multi-provider** | Agents can be routed to different model providers; you bring your own accounts and keys. |
| **Governed knowledge** | The system proposes lessons from its own work; they reach the agents only after a person approves them. |
| **Self-hosted** | One dedicated deployment per organization, on infrastructure it controls. |

## How it works

```mermaid
flowchart LR
    H([Human intent]) --> A[Specialized agents<br/>plan and build]
    A --> P[Proposal<br/>command block]
    P --> R{Review}
    R -- explain --> P
    R -- veto + reason --> A
    R -- approve --> X[Isolated execution]
    X --> E[Evidence<br/>result · preview · cost]
    E --> K[Keep]
    E --> U[Revert]
    K --> L[Lessons<br/>proposed → approved]
```

## The OrquestrAI Factory

Describe a project in a few sentences; the factory plans it, builds it and opens a preview.

- **Static websites — available end to end:** brief → agent plan → generated site → automated checks → preview on a separate origin.
- **Full-stack applications — in validation:** a single, fully supported path — **React + Vite + TypeScript, Express and SQLite** in one
  process. The AI writes the application *specification*; OrquestrAI generates the application from a tested template, so the
  infrastructure is the same every time. Generation is proven; running each application in its own isolated runtime with a preview is
  the work in progress.
  *How validation works here:* the generator passed its functional tests, then an independent read-only audit found failure cases the
  happy path does not exercise. It was not promoted. It will be, after those cases are fixed and the audit passes.
- **More stacks — planned,** built on the same pattern once the first full-stack path is complete.

## Architecture

High-level view below; boundaries and the life of a change are in the [technical overview](docs/technical-overview.md).

```mermaid
flowchart TB
    op([Operator]) --> ck[Cockpit]
    ck --> mesh[Agent mesh + planner]
    ck --> gov[Approval & evidence]
    mesh --> prov[(AI providers)]
    mesh --> fac[Project factory]
    gov --> exe[Isolated execution]
    fac --> prj[(Isolated projects)]
    exe --> prj
    prj --> prev[Previews]
    mesh --> tel[Cost telemetry]
    mesh --> kb[Knowledge & lessons]
    ck --> bk[(Encrypted backup & recovery)]
```

## Engineering evidence

A capability is not counted because the code exists. It is counted when the path has been proven:
**design → automated proof → human proof on a live system → independent review when sensitive → promotion.**
Passing the happy path is not enough: the first full-stack generator passed its functional tests, an independent review found failure cases,
and it was held back. Details: [technical overview](docs/technical-overview.md#engineering-evidence).

## Security by design

Full model — proven properties, work in validation, assumptions, limits and non-goals: [docs/security-model.md](docs/security-model.md).
In short — design properties, not guarantees:

- **Least privilege** — execution without network, privileges or access outside the project.
- **Explicit execution** — no path runs AI output without human confirmation; administrative access is separate and requires a second factor.
- **Isolation** — approved commands and project terminals run in per-project, network-less containers; previews are served from a separate origin. Per-project network isolation for long-running applications is in validation.
- **Reversibility** — where supported, changes are undone with a preview of the undo.
- **Audit trail** — tamper-evident execution records; sealed terminal sessions.
- **Independent review** — changes to execution, isolation and recovery pass a read-only external audit before promotion.
- **Recovery discipline** — version control, encrypted off-site backups with automatic verification, and server snapshots.

## AI providers

Agents are routed per role. The validated routes use Anthropic and OpenAI models today. Other providers — Groq, Gemini, OpenRouter,
Cerebras, Z.ai and any OpenAI-compatible API — can be configured and tested from the control panel.

Self-hosting gives you control over infrastructure, providers and data flow. When a cloud AI provider is used, the content sent to it
is subject to that provider's terms.

## Current maturity

| Capability | Status |
|---|---|
| Cockpit with project-scoped chat, commands, terminal and cost | Available |
| Command blocks with explain, approve and veto | Available |
| Isolated execution of approved changes | Available |
| Revert with preview of the undo | Available |
| Read-only project terminal | Available |
| Two-factor authentication and step-up for sensitive actions | Available |
| Agent mesh with planner | Available |
| Cost telemetry per project, agent and call | Available |
| Governed lessons | Available |
| Factory: static websites | Available |
| Encrypted off-site backup with verification | Available |
| Factory: full-stack applications (React · Express · SQLite) | In validation |
| Additional AI providers | Configurable |
| Full recovery on a clean server | Planned |
| Guided installer (one command + setup wizard) | Planned |
| Additional stacks and databases | Planned |

"Available" means proven by automated tests and by a human operator on a live deployment.

## Roadmap

- Full-stack factory end to end: isolated runtime, preview, changes through approved commands, backup of application data.
- Reproducible self-hosted deployment and recovery validated on a clean server.
- Guided installer and setup wizard.
- More validated stacks and databases on the same foundation.
- Governance features for larger teams.

## Built for

Software factories and development agencies · internal engineering teams · AI-native teams · organizations that need AI work to run under
their own governance.

## Why it matters for a company

- Put human approval exactly where changes become real, and nowhere else.
- Know who proposed, who approved and what ran — for every change.
- Undo supported changes instead of repairing them by hand.
- See what AI costs, per project and per agent, and route work across providers instead of depending on one.
- Run on the infrastructure you choose, with your own provider accounts.
- Turn a set of AI tools into an organized team with a process.

## Feedback

We are building OrquestrAI in public enough to learn, while keeping the production engineering private. We want rigorous feedback — on architecture, security, governance, user experience,
developer experience, business use cases and missing capabilities. Discussions and issues will open with this repository.
Security concerns: please do not open public issues; a private reporting channel will be listed here.

## About

**CBini OrquestrAI** — conceived and directed by Cristhian Bini, CBini Soluções em TI.

This repository is the public documentation and showcase for CBini OrquestrAI. The product source code is not published here and
this is not an open-source project. Licensing and commercial terms are under preparation. All rights reserved.

More: [technical overview](docs/technical-overview.md) · [security model](docs/security-model.md) · [public roadmap](docs/roadmap.md) · [FAQ](docs/faq.md)
