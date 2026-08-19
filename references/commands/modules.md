# Command: `modules` — Companion JS Modules

## Purpose
Handle the interactivity htmx attributes genuinely can't express (a
chart re-render after a swap, a third-party widget re-initialization,
client-only UI state like an open/closed dropdown) as small, scoped
vanilla JS modules hooked to htmx's lifecycle events — never a bespoke
framework, never fighting htmx by re-implementing what an attribute
already does.

## When to run it
- The audit shows JS manually re-querying the DOM after every action
  instead of listening for htmx's events, or a chunk of interactivity
  that could be a plain `hx-*` attribute instead of hand-written JS.
- User says "re-init this widget after swap", "add some custom
  behavior", or runs `modules`.

## What it does
1. Before writing custom JS, check whether an `hx-*` attribute already
   covers it (`swap.md`/`triggers.md`) — modules are for genuine gaps,
   not a habit of reaching for JS first.
2. One module per concern under `assets/js/modules/name.js`, hooked to
   the relevant htmx event: `htmx:afterSwap` (re-init a widget in newly
   inserted content), `htmx:configRequest` (attach a header to every
   request), `htmx:beforeRequest`/`htmx:afterRequest` (already covered by
   `indicators.md` for loading state — don't duplicate that logic here).
3. Scope the listener to the swapped element (`evt.detail.target`), never
   a blanket `document`-wide re-init that re-runs on every swap
   everywhere.
4. No global namespace pollution — same rule as the backend skills'
   `modules.md` — each module exposes at most one intentional global, or
   none if using real ES modules.
5. Client-only UI state (a dropdown's open/closed) that doesn't need the
   server at all stays plain JS/CSS — don't route something through an
   htmx round-trip just because htmx is present in the project.

## Output convention
```
assets/js/modules/name.js   (e.g. chart-reinit.js, third-party-widget-init.js)
```

## Checklist
- [ ] Confirmed no `hx-*` attribute already covered this before writing
      custom JS
- [ ] Listener scoped to the swapped element, not document-wide
- [ ] No duplication of loading-state logic already handled by
      `indicators.md`
- [ ] No unintentional global-scope leakage
- [ ] Purely client-only state stays plain JS, not routed through htmx
