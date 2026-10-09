# Security model — CBini OrquestrAI

🇺🇸 **English** · 🇧🇷 [Português](security-br.md) · 🇪🇸 [Español](security-es.md) · [README](../README.md) · [Technical overview](arch.md)

This page states what OrquestrAI is designed to protect, what is proven, what is still being validated, what it assumes and what it does
not try to do. It is a public summary; operational details are intentionally omitted. Please report vulnerabilities privately, never in
public issues or discussions.

## What it protects against

- AI output changing a system without a person deciding it.
- One project's commands, sessions or data affecting another project.
- Changes that cannot be explained, attributed or undone.
- Silent loss of operational state.

## Proven properties

| Property | What it means |
|---|---|
| Explicit execution | No AI-proposed command runs without a human confirmation step; the chat cannot execute. Factory-generated project content is written by validated generators, not by executing AI-written commands. |
| Veto is final | A vetoed version of a command can never be executed. |
| Isolated execution | Approved commands run in a disposable environment with no network, a read-only system, no privileges and only their own project mounted. |
| Refuse when unsure | Commands whose effect cannot be analyzed safely are refused before running. |
| Read-only inspection | The project terminal is read-only and network-less, in a container per connection. |
| Step-up for sensitive access | Login uses two factors; terminal and administrative sessions require a fresh second factor. |
| Tamper-evident evidence | Executions are recorded in a hash-chained log; terminal sessions are sealed. |
| Reversible changes | Supported file changes are measured and can be reverted with a preview of the undo. |
| Secrets at rest | Provider keys are encrypted on the server and never returned to the browser. |
| Separate origins | Project previews are served from a different origin than the cockpit. |
| Recovery discipline | Daily encrypted off-site backups, automatically verified for completeness and for secrets in clear text; restore proven in isolation. |
| Full-stack applications | Each generated application runs in its own runtime without network access, from immutable releases, reached only through the preview origin; a failed new version leaves the previous one online. |
| Application data in backups | Databases of generated applications are included in the nightly backup through a consistent snapshot. |

"Proven" means covered by automated tests and confirmed by a human operator on a live deployment.

## In validation

- **Full recovery on a clean server.**

## Assumptions

- The host is operated by a trusted administrator and kept up to date.
- Operators protect their own credentials and second-factor devices.
- AI providers process the content sent to them under their own terms.

## Limitations and non-goals

- **Data boundary.** Self-hosting keeps the control plane, projects and records on your infrastructure. When a cloud AI provider is used,
  the content needed for each call — prompts, context and code excerpts — is sent to that provider. OrquestrAI does not prevent this; it
  lets you choose which providers are configured.
- **Revert scope.** Revert covers files changed through command blocks. It does not roll back data written by a running application;
  that is the role of backups.
- **Not a sandbox for arbitrary code.** Isolation is built for operator-approved changes to the operator's own projects, not for running
  untrusted third-party workloads.
- **No compliance certification** is claimed.
- **Single-organization deployment.** Multi-tenant hosting is not a design goal of the current version.

## Independent review

Changes that touch execution, isolation or recovery are reviewed by an independent auditor with read-only access before promotion. A finding
that blocks promotion stops it, regardless of functional test results.
