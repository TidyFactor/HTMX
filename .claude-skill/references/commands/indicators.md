# Command: `indicators` — Loading States & Error Handling

## Purpose
Make every htmx request give the user visible feedback while it's in
flight and a clear signal if it fails — no request should look like
nothing happened.

## When to run it
- The audit shows htmx requests with no `hx-indicator`, or no handling
  for a failed/errored response.
- User says "add a loading spinner", "handle request errors", or runs
  `indicators`.

## What it does
1. Every non-trivial request (anything not instant — a search, a form
   submit, a list refresh) gets an `hx-indicator` pointing at a small,
   consistent loading element (spinner, disabled-state, skeleton) — reuse
   one shared indicator pattern/CSS class project-wide, not a bespoke one
   per interaction.
2. A global `htmx:responseError`/`htmx:sendError` listener (set up once
   in `init.md`'s config script) shows a consistent error notification —
   a toast, an inline banner — rather than a silently failed request the
   user has no feedback on.
3. For form-specific failures, prefer `forms.md`'s inline-fragment-
   re-render pattern over the global error banner — the global handler
   is the fallback for requests that aren't form submissions (a list
   refresh, a delete action).
4. Disable the triggering element for the request's duration
   (`htmx:beforeRequest`/`htmx:afterRequest` toggling a `disabled`
   attribute, or htmx's built-in `hx-disabled-elt`) to prevent
   duplicate/overlapping requests from the same control.
5. Long-running requests (file upload, a slow report) get a real progress
   indicator via `hx-on::htmx:xhr:progress`/htmx's progress events
   instead of an indefinite spinner, when the backend can report
   progress.

## Output convention
```
assets/js/htmx-config.js       (global error/loading listeners — extends init.md's file)
assets/css/htmx-indicators.css  (shared spinner/loading classes)
```

## Checklist
- [ ] Every non-trivial request has a visible loading indicator
- [ ] A global error handler exists and gives real user-facing feedback
- [ ] Form failures use inline re-render, not just the global banner
- [ ] Triggering elements disable for the request's duration
- [ ] Shared indicator styling reused, not reinvented per interaction
