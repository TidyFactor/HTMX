# TidyFactor HTMX — Workflow Discipline

Applies underneath every command in `commands/`.

## 1. Audit
- Map every `hx-*` attribute in the project: what triggers it, what it
  targets, what swap strategy it uses, whether the returned fragment is
  a real template or a hand-built string, whether CSRF/validation is
  present on state-changing requests.
- Report findings and the proposed changes.
- **Stop for confirmation** before editing, unless told to proceed
  automatically.

## 2. Execute in batches
- One interaction/endpoint at a time — highest risk (unvalidated forms,
  missing CSRF) first, then highest UX impact (broken back button,
  un-debounced search).
- Never one giant diff across every htmx interaction in a single pass.
- After changing a fragment endpoint, actually trigger it (or describe
  triggering it) and confirm the returned fragment matches what
  `hx-target`/`hx-swap` expect — a fragment shape mismatch is a silent
  bug, not a visible error.

## 3. Verify
- Confirm no visual/functional regression, including a manual
  back/forward check after any `history.md` change.
- Report: interactions changed, remaining un-debounced/un-indicated
  requests, remaining fragment endpoints still using hand-built HTML
  strings.

## Mode-specific notes

**Init** — audit step is replaced by the Step 0 questions in `SKILL.md`
(does a backend already exist, what does it render with) — everything
else (execute in batches, verify) still applies once files start being
generated.

**Convert** — audit the *existing* interactivity approach first (full
page reloads, a client-side framework being partially replaced, ad hoc
`fetch()` calls) before proposing which parts become htmx interactions.
Not everything needs to become htmx — flag interactions genuinely better
served by `modules.md`'s plain JS instead of forcing a round-trip.

**Improve** — audit is the primary deliverable if the user just wants a
report; only move to execute once they confirm which findings to act on.
Always report missing CSRF/validation on state-changing requests
regardless of what was asked — that finding doesn't wait to be
requested.
