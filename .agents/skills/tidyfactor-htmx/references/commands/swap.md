# Command: `swap` — Swap & Target Strategy

## Purpose
Make `hx-target`/`hx-swap` choices deliberate and consistent across the
project instead of copy-pasted per element without thinking about what
actually needs to update.

## When to run it
- The audit shows `hx-swap="innerHTML"` used everywhere by default
  (htmx's default) without considering whether `outerHTML`, `beforeend`,
  or an out-of-band swap fits the interaction better, or shows more DOM
  being replaced than the interaction actually changed.
- User says "this update feels janky", "fix the swap behavior", or runs
  `swap`.

## What it does
1. For each `hx-get`/`hx-post`/etc., confirm `hx-target` points at the
   smallest element that actually needs to change — not a large parent
   container swapped just because it was convenient.
2. Choose the swap strategy deliberately:
   - `innerHTML` (default) for replacing a container's contents.
   - `outerHTML` when the element itself (including its attributes) must
     change — e.g. toggling a component's own state-bearing attributes.
   - `beforeend`/`afterbegin` for list append/prepend (infinite scroll,
     new chat message) instead of re-rendering the whole list.
   - `hx-swap-oob` (paired with `fragments.md`'s OOB fragment) for
     updating a second, unrelated part of the page in the same response
     (e.g. a cart-count badge alongside the main content swap).
3. Add `hx-swap="... settle:200ms"` (or the project's chosen timing) only
   where a visible transition genuinely improves the UX — not as a
   blanket default that just adds latency.
4. Verify swap + target combinations against real content size — an
   `outerHTML` swap on an element with `hx-trigger="load"` inside it can
   cause a re-trigger loop; flag anything shaped like that.

## Output convention
No new files in the common case — this command edits `hx-target`/
`hx-swap` attributes on existing elements per `fragments.md`'s templates.

## Checklist
- [ ] Every `hx-target` is the smallest element that actually needs to
      change
- [ ] Swap strategy chosen deliberately per interaction, not left at the
      default everywhere
- [ ] List append/prepend uses `beforeend`/`afterbegin`, not a full
      list re-render
- [ ] No swap+trigger combination that can cause a re-trigger loop
