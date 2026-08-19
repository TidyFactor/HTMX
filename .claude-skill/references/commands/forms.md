# Command: `forms` — Form Submission & Validation

## Purpose
Wire htmx-driven forms (`hx-post`/`hx-put`/`hx-delete`) with the same
security and validation discipline a full-page-submit form would have —
an htmx request is not exempt from CSRF or server-side validation just
because it's asynchronous.

## When to run it
- The audit shows an htmx-driven form with no CSRF token, or validation
  errors handled only client-side (or not at all).
- User says "add a form with htmx", "handle validation errors inline",
  or runs `forms`.

## What it does
1. Every state-changing form (`hx-post`/`hx-put`/`hx-delete`) carries a
   CSRF token — either a hidden field (submitted normally as form data)
   or via `hx-headers`/`hx-vals` if the backend expects it as a header.
   Match whichever convention `secure.md` already established on the
   backend skill in use; don't invent a second one.
2. Server-side validation is authoritative — client-side (`required`,
   `pattern`) is a UX nicety, never the only check.
3. On validation failure, the server re-renders the **same form
   fragment** with inline error messages and the submitted values
   preserved — `hx-target` points at the form itself (or a wrapping
   container) so the error response replaces the form in place, not a
   separate error panel disconnected from the field it refers to.
4. On success, decide deliberately: does the form fragment get replaced
   with a success state, or does the response target a different element
   (e.g. a list the new item was added to, via `hx-swap-oob` per
   `swap.md`) — don't leave a submitted form sitting there unchanged.
5. Disable the submit control during the request (`hx-indicator` +
   `disabled` toggling per `indicators.md`) to prevent duplicate
   submissions from a fast double-click.

## Output convention
No new files in the common case — edits land in the existing form
fragment template and its backend handler.

## Checklist
- [ ] Every state-changing form includes CSRF, matching the backend's
      existing convention
- [ ] Server-side validation is authoritative, not just client-side
- [ ] Validation failure re-renders the form fragment with inline errors
      and preserved values
- [ ] Success state is a deliberate choice, not a form left unchanged
- [ ] Double-submission prevented via indicator/disabled state
