# Design decisions — CBini OrquestrAI

🇺🇸 **English** · 🇧🇷 [Português](design-br.md) · [README](../README.md) · [Architecture](arch.md) · [Security](security.md)

Why the product is shaped the way it is. Each decision states the trade-off it accepts.

| Decision | Why | Trade-off accepted |
|---|---|---|
| **The chat never executes** | Conversation is where uncertainty lives; execution needs a stable, reviewable artifact. | One extra step between asking and changing. |
| **Chat, command block and terminal are separate surfaces** | Talking, changing and inspecting carry different risks, so they get different permissions. The project terminal is read-only. | Operators learn three surfaces instead of one. |
| **Commands require explicit approval** | The person accountable for a change should see it before it runs, in plain language if needed. | Slower than autonomous execution; deliberately so at the point where changes become real. |
| **A vetoed version can never run** | A rejection must be final, and its reason should improve the next plan. | A corrected command needs a new version. |
| **Refuse when the effect cannot be analyzed** | A guess about scope is worse than a refusal; the operator can restate the change explicitly. | Some valid commands are refused and must be rewritten more literally. |
| **The project is the unit of isolation** | Conversations, commands, terminals, previews and costs share one boundary, so switching projects switches all of them. | Cross-project work is intentionally not a single operation. |
| **Previews live on a separate origin** | Generated pages must not see the operator's session. | Previews cannot reuse the cockpit's login. |
| **Unknown cost is not zero** | A missing price that reads as zero hides spending; unknown stays visible as unknown. | Some totals are incomplete and say so. |
| **Lessons need human approval** | Knowledge that reaches every agent is a change to behavior and gets the same governance as code. | Learning is slower than auto-learning. |
| **Code that exists is not a capability** | A capability is *Available* only after automated and human proof; sensitive changes also need independent review. | Features wait in validation longer than they could. |
| **One full stack done end to end before many** | A single proven path teaches more than several partial ones and becomes the template for the next. | Fewer stack options for now. |
| **Not competing with models** | Models and coding agents improve fast; the durable layer is governance, isolation, evidence and cost around them. | OrquestrAI depends on external models for intelligence. |
| **Self-hosted, one organization per deployment** | The customer controls infrastructure and provider choice. | No hosted multi-tenant offering in the current version. |

The thesis behind the last two rows is a product bet, not a proven market advantage. Disagree with any row?
[Challenge the architecture](https://github.com/cristhianbini/CBini-OrquestrAI/discussions/2).
