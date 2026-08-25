---
name: tidyfactor-htmx
description: "TidyFactor HTMX track — Server-Driven Hypermedia Interactivity with Contextual Decision Layer (CDL). Features locally vendored HTMX (zero CDN dependency) layered over server-rendered fragments (pairs naturally with PHP, Node, or Python). Trigger on commands 'brief', 'init', 'fragments', 'swap', 'triggers', 'forms', 'indicators', 'history', 'assets', 'modules', 'i18n', or requests like 'add htmx to project', 'fix janky swap', 'vendor htmx locally', 'inline form validation htmx'. Anti-triggers: Do NOT use for React/Next.js or client-side JSON SPAs."
---

# TidyFactor HTMX (Server-Driven Hypermedia Interactivity)

A command dispatcher for hypermedia-driven interfaces. This router declares commands and workflows without performing execution directly.

## Commands

| User intent | Command | What it loads |
|---|---|---|
| Strategic Hypermedia Discovery & Brief Resolution | `references/commands/brief.md` | `references/workflows/brief.md` + `references/memory/decision-points.md` + `references/memory/quality-bar.md` |
| Primary deliverable — setup vendored HTMX layer | `references/commands/init.md` | `references/workflows/init.md` + `references/memory/architecture.md` |
| Server-rendered HTML partials & fragment routes | `references/commands/fragments.md` | `references/workflows/fragments.md` + `references/memory/architecture.md` |
| DOM swap strategies (innerHTML, outerHTML, morphdom) | `references/commands/swap.md` | `references/workflows/swap.md` + `references/memory/decision-points.md` |
| Event triggers, polling intervals, SSE, debouncing | `references/commands/triggers.md` | `references/commands/triggers.md` + `references/memory/quality-bar.md` |
| Forms, inline validation errors, CSRF protection | `references/commands/forms.md` | `references/workflows/forms.md` + `references/memory/quality-bar.md` |
| Loading spinners, skeleton shimmers, button disabling | `references/commands/indicators.md` | `references/commands/indicators.md` + `references/memory/quality-bar.md` |
| Browser back-button & URL history synchronization | `references/commands/history.md` | `references/commands/history.md` + `references/memory/decision-points.md` |
| Local vendoring of htmx.min.js & extension scripts | `references/commands/assets.md` | `references/commands/assets.md` + `references/memory/architecture.md` |
| Companion JavaScript hooked to htmx lifecycle events | `references/commands/modules.md` | `references/commands/modules.md` + `references/memory/architecture.md` |
| Fragment translation & dynamic Arabic RTL rendering | `references/commands/i18n.md` | `references/commands/i18n.md` + `references/memory/quality-bar.md` |

Read only the command file that matches the request. Do not load all commands simultaneously.

## Non-Negotiable Invariants

1. **Contextual Decision Layer (CDL)**: Resolve hypermedia baselines via `/brief` or `.tidyfactor/htmx-brief.md` before emitting code.
2. **Zero Third-Party CDN Dependency**: HTMX and all extensions MUST be vendored locally at `js/vendor/htmx.min.js`.
3. **Fragment HTML Only**: Endpoints respond with clean HTML fragments, not JSON and not full `<html>` documents.
4. **CSRF On All Mutations**: Every `hx-post`, `hx-put`, `hx-delete` request MUST include CSRF tokens.
5. **7-Axis Pre-Emit Critique**: All generated components must be evaluated with `/* Pre-emit critique: P5 H5 E5 S5 R5 V5 D5 */`.
