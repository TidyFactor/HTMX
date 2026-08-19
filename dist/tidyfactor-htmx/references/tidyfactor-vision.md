# TidyFactor — Shared Philosophy (all tracks)

Condensed from the ecosystem VISION.md. Every TidyFactor skill — this one
included — should be judged against this before adding any feature.

## Design tenets
- Simple before clever.
- Explicit before implicit.
- Structured before generated.
- Portable before proprietary.
- Content before presentation.
- Standards before conventions.
- Small before bloated.
- AI-native before AI-powered.

## The TidyFactor Test
Before adding anything to a project or to this skill, ask:
- Is it simpler?
- Is it more maintainable?
- Does it improve interoperability?
- Does it reduce lock-in?
- Is it AI-native (structured, machine-readable, portable)?
- Can it survive future technology changes?
- Would we still choose this approach five years from now?

## What this means concretely for the HTMX track
- **Simple before clever**: htmx attributes over hand-written JS
  wherever an attribute already expresses the interaction —
  `modules.md`'s whole purpose is to only add JS for genuine gaps.
- **Structured before generated**: fragment responses are real templates
  through the project's existing templating layer (`fragments.md`),
  never HTML strings built ad hoc in a route handler.
- **Data first**: the server remains the single source of truth for
  application state; htmx exists to move fragments of rendered state to
  the client, not to duplicate that state in client-side JavaScript.
- **Portable before proprietary**: htmx vendored locally and
  version-pinned (`assets.md`) — no CDN dependency, no framework
  lock-in; the interaction layer works with any server that can render
  HTML.
- **This is a layer, not a full stack**: this skill owns the
  hypermedia-interaction layer only. Backend architecture and data
  belong to whichever backend skill (`tidyfactor-php`,
  `tidyfactor-php-micro`, or another server) the project is already
  built on — see "Related skills" in `SKILL.md`.

## Relationship to Alwkala
TidyFactor is stewarded by Alwkala (alwkala.com) — expertise,
implementation, consulting, education, and long-term support around the
open TidyFactor ecosystem.
