# Command: `history` — Navigation & Browser History

## Purpose
Make htmx-driven navigation (boosted links, partial-page updates that
represent a real "page") work correctly with the browser's back/forward
buttons, reload, and shareable URLs — the most common htmx footgun is a
UI state that a URL can't reproduce.

## When to run it
- The audit shows `hx-boost` or `hx-push-url` used inconsistently —
  some navigations update the URL, others silently don't, breaking
  back/forward.
- User says "back button is broken", "the URL doesn't update", "make
  this shareable", or runs `history`.

## What it does
1. Any htmx interaction that represents a real navigable "place" (a
   different list filter, a different tab, a different detail view) gets
   `hx-push-url="true"` (or a specific path via `hx-push-url="/path"`) —
   anything that's just a transient UI update (a toggle, an inline edit)
   deliberately does **not** push a URL.
2. `hx-boost` on the base layout (from `init.md`) means plain `<a>`/
   `<form>` elements already push URLs and support back/forward by
   default — verify nothing overrides that unintentionally with
   `hx-boost="false"` on a link that should behave normally.
3. Handle `htmx:historyRestore`/browser back-forward-cache correctly: the
   page must re-render its current state from the restored URL, not show
   stale content — test an actual back-navigation after a boosted swap,
   don't assume it works.
4. Every push-url'd state should be reachable by a direct GET to that
   URL too (full-page load, not just via htmx) — if `?filter=active`
   only works when arrived at via an htmx swap, that's a broken
   shareable link; fix it so the same route serves both the full page and
   the fragment (per `fragments.md`'s `HX-Request` header check).
5. `hx-select`/`hx-target` on boosted navigation should be set
   deliberately when only part of the response should replace the page,
   not left at htmx's default full-body swap if that's wasteful.

## Output convention
No new files in the common case — attribute changes on existing
navigation elements, plus verification that routes serve both full pages
and fragments.

## Checklist
- [ ] Every "real place" navigation pushes a URL; transient UI updates
      deliberately don't
- [ ] Back/forward tested manually after a boosted swap, not assumed
- [ ] Every push-url'd state is reachable by a direct GET, not
      htmx-only
- [ ] No unintentional `hx-boost="false"` breaking normal-looking links
