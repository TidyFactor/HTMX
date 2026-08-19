# Command: `fragments` — Server-Rendered Partials

## Purpose
Establish (or clean up) the convention for what a fragment endpoint
returns: a real partial template, rendered through the project's
existing templating layer, never a string concatenated by hand in a
route handler. This is htmx's equivalent of `compo` — the reusable unit
htmx swaps into the page.

## When to run it
- The audit shows route handlers building HTML with string
  concatenation/`printf`, or the same fragment markup duplicated across
  more than one endpoint.
- User says "clean up my fragment endpoints", "this HTML string in my
  route is getting messy", or runs `fragments`.

## What it does
1. Every htmx-targeted endpoint renders through the project's existing
   partial system (a Plates partial if on `tidyfactor-php-micro`, a PHP
   include if on `tidyfactor-php`, or the equivalent on whatever backend
   the project uses) — `fragments` never introduces a second templating
   mechanism alongside the one already in place.
2. A fragment template contains **only** the swapped-in markup — no
   `<html>`/`<body>`/layout wrapper. If a route needs to serve both a
   full page (direct visit) and a fragment (htmx request), it renders
   the same partial either bare (fragment request) or wrapped in the
   layout (full page request) — detect via the `HX-Request` header, not
   a duplicated template.
3. Name fragment templates by what they render (`search-results.html`,
   `todo-item.html`), not by the route that returns them — the same
   fragment is often reused across a list-refresh, an add, and an
   inline-edit response.
4. Out-of-band swaps (`hx-swap-oob`) get their own named fragment,
   composed alongside the primary response fragment — never inlined as
   an ad hoc string appended to the main response.
5. Escape everything by default in the fragment template — same rule as
   `secure.md` on the backend skills; a fragment is not exempt just
   because it's small.

## Output convention
```
<partials-dir>/fragments/
  search-results.<ext>
  todo-item.<ext>
  todo-item-oob.<ext>       (out-of-band variant, if needed)
```

## Checklist
- [ ] No route handler builds fragment HTML via string concatenation
- [ ] Fragment templates contain no layout wrapper markup
- [ ] Full-page vs. fragment response decided via `HX-Request` header,
      not a duplicated template
- [ ] Reused fragments named by content, not by originating route
- [ ] All dynamic values in a fragment are escaped
