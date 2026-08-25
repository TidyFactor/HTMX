# Changelog - TidyFactor HTMX

All notable changes to the **[@alwkala/tidyfactor-htmx](https://www.npmjs.com/package/@alwkala/tidyfactor-htmx)** package will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.0.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.1.0] - 2026-08-25

### Added
- **Contextual Decision Layer (CDL v1.0)**: Added `references/memory/decision-points.md` with thin arbitration protocol (X1–X5: Backend Pairing, Swap Strategy, Loading Indicator, Browser History, Output Scope).
- **Brief Command (`/brief`)**: Added `references/commands/brief.md` and `references/workflows/brief.md` for pre-flight hypermedia discovery.
- **7-Axis Hypermedia Quality Gate (`P/H/E/S/R/V/D`)**: Added `references/memory/quality-bar.md` enforcing fragment purity, local vendoring, and CSRF protection.
- **Structured References & Workflows Architecture**: Created `references/memory/` and `references/workflows/` (init, fragments, forms, swap, brief).
- **Validation & CLI Suite**: Added `bin/add-skill.js`, updated `package.json` `"bin"` map, created `tools/validate_skill.py`, and updated `brand.json` version.

---

## [1.0.0] - 2026-07-28
- Initial Release of `@alwkala/tidyfactor-htmx`
