# Memory: quality-bar (HTMX Anti-Slop & Hypermedia Quality Gate)

Enforces hypermedia purity, zero JSON client re-rendering, local asset vendoring, and graceful degradation.

---

## 🛡️ 7-Axis Pre-Emit Self-Critique Stamp

Every generated HTMX endpoint, partial template, or form must be stamped:
`/* Pre-emit critique: P5 H5 E5 S5 R5 V5 D5 */`

| Axis | Dimension | Score 1 (Slop / Reject) | Score 5 (Production Pass) |
|:---:|---|---|---|
| **P** | **Philosophy & Hypermedia Purity** | Returns raw JSON expecting client JS parsing; heavy framework habits. | Server returns semantic HTML fragments directly into DOM targets. |
| **H** | **HTML Fragment Structure** | Full `<!DOCTYPE html>` returned on partial requests. | Clean partials with matching IDs, scoped wrappers, and clean swap tags. |
| **E** | **Error & State Handling** | Silent network failures; no `htmx-error` or offline feedback. | `hx-target-error` or `htmx:responseError` triggers with visual feedback. |
| **S** | **Security & CSRF Protection** | Forms submitted via `hx-post` without CSRF token headers. | `hx-headers='{"X-CSRF-Token": "..."}'` or hidden inputs on every mutation. |
| **R** | **RTL & Dynamic Content** | Swapped fragments break RTL layout or font rendering. | Swapped partials preserve `dir="rtl"` and semantic font hierarchies. |
| **V** | **Velocity & Debounce Discipline** | Rapid keyup triggers firing 50 HTTP requests per second. | `hx-trigger="keyup changed delay:300ms, search"` for input search. |
| **D** | **Decision Alignment** | Inconsistent swap strategy ignoring `.tidyfactor/htmx-brief.md`. | 100% compliant with confirmed Swap Strategy and Indicator model. |
