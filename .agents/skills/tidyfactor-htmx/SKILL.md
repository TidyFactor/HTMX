---
name: tidyfactor-htmx
description: TidyFactor HTMX track — the hypermedia interaction layer (htmx over server-rendered fragments), vendored locally with no CDN dependency, layered on top of any server backend (pairs naturally with tidyfactor-php / tidyfactor-php-micro). Trigger on commands "init", "fragments", "swap", "triggers", "forms", "indicators", "history", "assets", "modules", "i18n" (htmx setup, server-rendered partials, hx-swap/hx-target strategy, hx-trigger/debounce/polling/SSE, htmx-driven forms with CSRF, loading/error states, back-button/URL history, vendoring htmx, companion JS hooked to htmx events, fragment translation), or requests like "add htmx to this project", "set up htmx", "this update feels janky", "the back button is broken", "stop using the CDN for htmx", "add a loading spinner to this request", "handle validation errors inline with htmx". Covers three modes — Init (add the htmx layer), Convert (replace ad hoc fetch()/full-reload interactivity with htmx), Improve (audit and fix an existing htmx implementation).
---

# TidyFactor HTMX (Hypermedia Interaction Layer)

Part of the TidyFactor skill library (see `references/tidyfactor-vision.md`
for the shared philosophy). This skill is a **layer, not a full stack**:
it owns how server-rendered fragments get requested, swapped, validated,
and made navigable — not backend architecture or data. It composes with
`tidyfactor-php` or `tidyfactor-php-micro` (or any other server that can
render HTML), rather than replacing them. See "Related skills" below.

## Step 0 — Identify the mode (ask if not obvious)

> "What are we doing?
> 1. **Init** — add the htmx layer to a project (new or existing backend)
> 2. **Convert** — replace ad hoc `fetch()`/full-page-reload
>    interactivity with htmx
> 3. **Improve** — audit and fix an existing htmx implementation"

Also confirm what the project's backend already renders with (Plates,
PHP includes, something else) — `fragments.md` builds on that, it never
introduces a second templating mechanism.

## Command Index

| Command | Purpose | Reference | Phase |
|---|---|---|---|
| `init` | Scaffold — vendor htmx, base layout wiring, one real fragment exchange | `references/commands/init.md` | — |
| `assets` | Vendoring & Version Hygiene — no CDN dependency | `references/commands/assets.md` | 1 |
| `fragments` | Server-Rendered Partials — the reusable swap unit | `references/commands/fragments.md` | 2 |
| `swap` | `hx-swap`/`hx-target` Strategy | `references/commands/swap.md` | 2 |
| `triggers` | `hx-trigger` — debounce, polling, SSE | `references/commands/triggers.md` | 2 |
| `forms` | htmx-Driven Forms — CSRF, validation, error re-render | `references/commands/forms.md` | 2 |
| `indicators` | Loading States & Error Handling | `references/commands/indicators.md` | 2 |
| `history` | Browser History — back/forward, shareable URLs | `references/commands/history.md` | 2 |
| `modules` | Companion JS — hooked to htmx lifecycle events, for genuine gaps only | `references/commands/modules.md` | 2 |
| `i18n` | Translation for fragments — stays correct across swaps | `references/commands/i18n.md` | 3 |

New commands follow `references/commands/_template.md`.

## Command Sequencing & Phases

`init` runs standalone first — see Running a full mode below. For
Convert/Improve on an existing htmx implementation:

1. **Phase 1 — Foundation.** `assets` first — a locally vendored,
   version-pinned htmx makes every later command's changes reproducible
   and CDN-independent.
2. **Phase 2 — Interaction Layer.** `fragments` establishes the partial
   convention → `swap`/`triggers` tune how and when requests fire →
   `forms` adds validated, CSRF-protected submissions → `indicators`
   makes every request give visible feedback → `history` makes
   navigable interactions back/forward-safe and shareable → `modules`
   fills any genuine gap htmx attributes can't express.
3. **Phase 3 — Scale.** `i18n` last, always — fragments must be stable
   before wiring translation into them.

Never run two commands "at the same time" — each finishes, gets
verified, and gets reported before the next starts.

## Running a single command
1. Confirm mode (Step 0) and the backend's existing templating
   convention.
2. Read the matching reference file in full before acting.
3. Do a scoped audit for just that command's concern.
4. Execute in small batches per the reference file's steps.
5. Report using that command's checklist.

## Running a full mode end-to-end
- **Init**: run `init` alone — it wires the base layer and one real
  working example, ready for `fragments`/`swap`/`forms` to extend as
  more interactions are added.
- **Convert / Improve**: follow the Phase 1→3 order above in full.

Within each command, still follow the underlying audit → execute →
verify discipline in `references/workflow.md`.

## Hard constraints (apply to every command)
- Zero functionality/visual regressions — flag anything risky instead of
  guessing.
- htmx (and any extension) stays locally vendored and version-pinned —
  never a CDN `<script src>`.
- Never introduce a second templating mechanism alongside whichever one
  the backend already uses.
- Every state-changing htmx request (`hx-post`/`hx-put`/`hx-delete`)
  carries CSRF protection, matching the backend's existing convention —
  no exception for being asynchronous.
- Don't reach for custom JS (`modules`) before checking whether an
  `hx-*` attribute already covers the interaction.
- `assets` runs first on Convert/Improve; `i18n` always runs last.

## Two operating modes (execution style)
- **Mode A — do it directly.** Files are uploaded or accessible via
  `view`/`bash_tool`/`str_replace`/`create_file`. Run Step 0, then
  execute directly.
- **Mode B — generate a handoff prompt.** The user wants a copy-paste
  prompt for an external agent instead. Still run Step 0 first. Build it
  from the matching `references/commands/<name>.md` file(s).

## Related skills
- No backend at all, purely static → `tidyfactor-html` — note htmx
  requires a server to return fragments, so this skill needs
  `tidyfactor-html`'s build-time or runtime pieces to also expose an
  endpoint, or it belongs on a backend track instead.
- Backend architecture, data, and routing → `tidyfactor-php` (vanilla)
  or `tidyfactor-php-micro` (opinionated Flight+Medoo+Plates starter) —
  this skill only owns the interaction layer on top.
- Wants a client-side JS framework's reactivity model instead of
  server-rendered fragments → `tidyfactor-js-micro` (Alpine/Lit/VanJS,
  planned) is the better fit than forcing htmx into that shape.
