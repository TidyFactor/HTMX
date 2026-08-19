# Command: `triggers` — Trigger & Event Strategy

## Purpose
Make `hx-trigger` choices deliberate: the right DOM event, debounced/
throttled where the interaction needs it, and polling/SSE reserved for
where they're actually needed instead of used as a default.

## When to run it
- The audit shows a search-as-you-type field firing on every keystroke
  with no debounce, a poll interval left at htmx's default without
  considering server load, or a custom event that could be a plain
  trigger instead.
- User says "this search is too chatty", "add live updates", "poll for
  changes", or runs `triggers`.

## What it does
1. Text input triggers (`hx-trigger="keyup changed delay:300ms"` or
   similar) get an explicit debounce — never a bare `keyup` firing a
   request per keystroke.
2. Polling (`hx-trigger="every 5s"`) only where the data genuinely
   changes on the server independent of user action, and only with a
   deliberate interval — flag any polling interval that looks copy-pasted
   without considering actual server load.
3. For genuinely real-time needs (chat, live notifications), prefer the
   SSE (`hx-ext="sse"`) or WebSocket extension over aggressive polling —
   flag the tradeoff (extension = one more small script to vendor per
   `assets.md`) and confirm with the user before adding it.
4. Custom events (`hx-trigger="myEvent from:body"`) only where a plain
   DOM event genuinely doesn't fit — document why in a comment next to
   the trigger, since custom events are harder to trace than standard
   ones.
5. `hx-trigger="load"` used deliberately (lazy-loading a fragment on
   initial render) — verify it can't create a request storm if the
   element it's on gets swapped back in repeatedly (cross-check with
   `swap.md`'s loop warning).

## Output convention
No new files in the common case — this command edits `hx-trigger`
attributes on existing elements.

## Checklist
- [ ] No un-debounced trigger firing on every keystroke
- [ ] Every polling interval is a deliberate choice, not a leftover
      default
- [ ] Real-time needs use SSE/WebSocket, not aggressive polling, once
      confirmed with the user
- [ ] Every custom event trigger has a one-line comment explaining why a
      standard event didn't fit
