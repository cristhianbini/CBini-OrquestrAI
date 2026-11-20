# Changelog — CBini OrquestrAI

🇺🇸 **English** · 🇧🇷 [Português](CHANGELOG-BR.md) · 🇪🇸 [Español](CHANGELOG-ES.md)

How the product has changed, written for people rather than machines. Each entry says what someone using OrquestrAI can now do, or
what stopped going wrong. Internal tooling, test plumbing and security mechanics are summarised, not itemised.

OrquestrAI is conceived and led by **Cristhian Bini, founder of CBini Soluções em TI**. He sets the product vision, makes the product
decisions and approves every release. AI agents work as engineering collaborators: they write and test code, and they propose changes.
A person approves every change before it ships.

> **A IA acelera. O humano decide.** — AI accelerates. The human decides.

**Status labels.** **Released**: running on the live deployment. **In preparation**: built and tested, not yet released. **Planned**: not a
feature yet. Dates are in the format YYYY-MM-DD.

---

## 0.45.0 — 2026-11-20 · MVP · Released

This is the first version meant as a complete minimum product. It was released after three real builds passed the functional
check through the live cockpit: a business website, a loan simulator and a data dashboard. The website and the simulator were built
with free AI models at zero cost. The dashboard was built at the Smart level, with a low-cost paid model approved by the founder and a
maximum cost accepted before the build started. Complex dashboards are more reliable at the Smart level; the Economy level remains the
best free attempt.

**Delivered**
- **Telemetry restored and approved by the founder.** It shows the last 30 days and the full history: investment, tokens and estimated
  savings. It breaks cost down by billing type, project, agent and model, and it includes spending controls. A gap in the data no longer
  blanks the whole screen. An unknown cost is shown as "not measured", never as free.
- **Build side panel.** It shows which agents were not called and why, how long the build really took, and shortcuts to the preview and
  to the project.
- **Functional check on every build.** After a build, the generated app is opened and used automatically. The project then shows one of
  three verdicts: ACCEPTED, REJECTED or INCONCLUSIVE.
- **The Factory works on free models.** The model's internal reasoning gets only part of its output budget, so the generated code still
  fits. The most reliable free model is tried first.
- **Charts in generated apps.** Bar, line and pie charts come from a built-in component, at a readable size and with no external library.
- **Data filters in generated dashboards.** A built-in filter lets people pick a column and a value, for example *region = South*. The
  totals and charts follow the filter. When a build asks for a filter and the generated code doesn't use this component, the Factory
  sends that part back to be fixed.
- **Navigation that reaches every section.** On one-page websites, the menu now lists the sections that exist. A link that pointed to
  the page itself now takes the visitor to the first section.
- **KPIs on the right numeric column.** Indicators in a generated dashboard use a numeric column chosen by the platform, never the
  filter column.
- **Navigation that fits on a phone.** One-page website menus wrap on small screens, with no sideways scrolling.
- **More resilient free Factory.** A provider rate-limit refusal no longer uses up the attempts across free models, and the reason for
  each switch is recorded.
- **Demo contact form that responds.** The button submits and the page shows the notice that nothing is actually sent.
- **Smart level that completes dashboards.** The maximum cost of a paid site covers the build in parts, and the paid model's internal
  reasoning is capped so the code fits in the response.
- **Generated dashboards that don't freeze or get rejected by mistake.** A platform component no longer loops when the dashboard
  redraws, and the check recognizes more legitimate ways of using the components.
- **Release sign-off by the operator.** Every update to the live system needs a sign-off typed by the operator. The sign-off is tied to
  the exact files that were checked.

**Fixed**
- The telemetry screen failed to load when a run had no measured cost.
- The Factory had several faults that made a generation fail or ship broken:
  - a misread module contract stopped the generation;
  - one module called another by the wrong name, so the page showed "not defined";
  - an unreadable plan now gets one more try;
  - a rejected module now gets one more try;
  - runtime errors are now caught before the site is published.
- The header no longer shows a placeholder version number while the page loads.

## 0.44.2 — 2026-11-05 · Released
- **The Factory can use low-cost paid models.** The maximum cost is shown and approved before any spending.
- **Paid chat asks first.** Each paid message waits for the operator's approval, with a per-message limit. Clicking twice doesn't charge
  twice.
- **The chat reads the project's files by itself,** read-only, instead of asking the operator to run commands. It also knows whether the
  app is live, stopped or not yet published.
- **A larger built-in manual,** with search and new sections: what works today, your first app, and paid models.
- **Fixes:**
  - the project list could hide an error message;
  - a build interrupted by a restart kept showing as "generating";
  - the site card showed false red warnings;
  - a failure to record a cost now blocks new paid calls.

## 0.44.1 — 2026-11-04 · Released
- **The server refuses paid models without an open, approved spending window,** even when one is picked by hand. Before, only automatic
  switches were blocked.
- **Clearer messages:** a finished app's card no longer says the agents are still working, and refusals are written in plain Portuguese.

## 0.44.0 — 2026-11-04 · Released
- **New full-stack apps can include up to four related records,** for example customers and orders. Existing apps don't change.
- **The operator picks the AI model when creating an app.** A confirmed free model is selected by default.
- **An interrupted app can be resumed on a free model** without redoing finished work.
- **More AI providers:** MiniMax and DeepSeek can be set up.
- **Fixes:**
  - editing a record in a generated app failed inside the preview;
  - internal names leaked into the screen;
  - when a free model gives no answer, the cockpit now says so and offers another one.

## 0.43.0 — 2026-11-04 · Released
- **An interrupted website build explains itself:** why it stopped, what is done, what is missing, and how to continue. There is no
  automatic switch to a paid model.
- **The chat saves the request before calling the AI,** so a provider failure never loses it.
- **Favourite models,** saved per user.
- **A first-product status panel,** built from the product requirements.
- **Fewer false errors:** a change is now checked against what the request meant.

## 0.42.0 – 0.42.5 — 2026-10-15 to 2026-10-16 · Released
- **Richer generated apps:**
  - choice-list fields that show as coloured badges and can be filtered;
  - money fields in Brazilian reais, with totals;
  - correct grammatical gender in the labels;
  - a **Details** view for records with many fields.
- **Generated websites no longer invent professional registration numbers or company IDs.** Unknown details show as "to be informed".
- **Training an agent no longer cuts off part of its card.**
- **A weekly regression check with no red items,** a backup restore proven on a clean container, and an operator routine guide.

## 0.41.0 – 0.41.2 — 2026-10-14 to 2026-10-15 · Released
- **Generated apps gained:**
  - editing, and deletion with on-screen confirmation;
  - search and a success message after saving;
  - Brazilian number and date formats;
  - a card layout on phones;
  - a colour palette that suits the business;
  - column sorting, and lists that load in batches.
- **Rendered review of websites:** text contrast is measured the way the browser paints it.
- **A paid A/B test showed** that a design brief makes clearly better websites. Switching it on is a founder decision.

## 0.40.0 – 0.40.6 — 2026-10-12 to 2026-10-14 · Released
- **End-to-end use tested in a real browser:** creating a project, building it, previewing it, chatting, then preparing and confirming a
  change.
- **Every execution ends in a single, clear outcome:** failed with no change, partial, applied, already applied, no effect, or unknown.
  Each outcome says whether it is safe to run again.
- **Cockpit improvements:**
  - a new login starts with no project open;
  - a **+** button goes straight to the new-project wizard;
  - the neutral state is always one click away.
- **Security hardening:** the preview and the undo flow were hardened after independent review.
- **First installer for a new server.** It is tested in a container; a clean install on a real server is not yet proven.

## 0.39.0 — 2026-10-12 · Released
- **EXPLAIN is more resilient and can be configured.** It uses a low-cost model by default, and it says what a command will do and
  whether it can be undone.
- **Plain-language summaries of commands** for website projects, at no AI cost.

## 0.37.0 – 0.38.0 — 2026-10-06 · Released
- **The chat is the way to change a project.** Command blocks are kept per project and can't cross into another one. There is a single
  governed EXECUTE path.
- **Every change is checked against its intent after it runs.** Each item is marked as confirmed, failed or not verified. A successful
  exit code is no longer called a functional success.
- **The Factory shows its real stages,** with the current agent and real timings.

## 0.36.0 — 2026-09-21 · Released
- **Projects are isolated in the cockpit.** Command blocks, conversations and lessons belong to one project.

## 0.35.0 — 2026-08-13 · Released
- **A model can be set for each agent,** with an auditable fallback when a provider fails.
- **The lessons cycle is curated by a person.**

## 0.33.0 – 0.34.0 — 2026-07-25 to 2026-07-28 · Released
- **Security hardening of credentials and secrets.** Insecure fallbacks were removed. A full secret rotation was rehearsed and then
  carried out.

## 0.2.0 – 0.32.8 — 2026-06-30 to 2026-07-03 · Released
- **The cockpit moved to a React component layer,** with live agent cards and cost per run.
- **The version shown in the cockpit is read from this history.**

## 0.1.0 — 2026-06-19 · Released
- **First version:** a self-hosted, multi-AI cockpit with human approval before execution.

---

## Planned
These are not features yet. See the [roadmap](docs/roadmap.md).
- Full recovery on a clean server.
- A guided installer: one command plus a setup wizard.
- More stacks and databases.
