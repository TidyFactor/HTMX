# Command: `init` — HTMX Layer Scaffold

## Purpose
Add a working htmx interaction layer to a project: htmx vendored locally
(no CDN dependency), a base layout wired for it, and one real working
fragment exchange — not a placeholder `<button>` demo.

## When to run it
- Mode is Init (Step 0) — either a brand-new project, or adding htmx onto
  an existing server-rendered backend (vanilla PHP, PHP Micro, or
  anything else that can return an HTML fragment).
- User says "add htmx to this project", "set up htmx", "scaffold htmx",
  or runs `init`.

## What it does
1. Confirm (ask only if genuinely unclear): does a backend already
   exist? If yes, identify how it renders (Plates/PHP includes/other) —
   `fragments.md`'s convention builds on whatever that already is, it
   doesn't replace it. If no backend exists yet, generate a minimal one
   in plain PHP (this family's default) purely to demonstrate the
   pattern — and say clearly that `tidyfactor-php`/`tidyfactor-php-micro`
   own real backend architecture, this skill only owns the htmx layer.
2. Vendor `htmx.min.js` into `/assets/js/vendor/htmx.min.js` (or the
   project's existing vendor convention) — pinned version, no CDN
   `<script src>` dependency, so the interaction layer keeps working on
   any host with no external network dependency at request time.
3. Wire it once, globally, in the base layout: one `<script>` tag,
   `hx-boost` on the `<body>` (or main nav) if full-page htmx-driven
   navigation is wanted — ask if not obvious, since `hx-boost` changes
   how every link/form on the page behaves by default.
4. Build one real example end-to-end: a fragment endpoint (e.g. a
   search-as-you-type or a counter) demonstrating `hx-get`/`hx-post`,
   `hx-target`, `hx-swap`, and a returned partial that's a real fragment
   template per `fragments.md`'s convention — not string-built HTML
   inline in the route handler.
5. Add `hx-indicator` wiring and a basic `htmx:responseError` handler
   (see `indicators.md`) so the example doesn't silently fail on error —
   set the pattern once here, every later fragment reuses it.
6. Document the vendored version and upgrade path in `README.md`.

## Output convention
```
assets/js/vendor/htmx.min.js
assets/js/htmx-config.js        (global event listeners, error handling)
<fragment templates per the project's existing template convention>
README.md                        (documents vendored version + pattern)
```

## Checklist
- [ ] htmx vendored locally, pinned version, no runtime CDN dependency
- [ ] `hx-boost` decision made explicitly (on or off), not left ambiguous
- [ ] One real working fragment exchange, not a placeholder
- [ ] Global error/loading handling wired once, not per-fragment
- [ ] Backend rendering convention matches whatever the project already
      uses — this command does not introduce a second templating system
