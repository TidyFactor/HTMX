# Memory: decision-points (Contextual Decision Layer — CDL v1.0)

A thin arbitration protocol for resolving hypermedia interaction models, swap strategies, and backend pairings before emitting code.

---

## 🏛️ Decision Matrix (X1–X5)

| Code | Decision Dimension | Options (Reference SSOT) | Default Fallback | Trigger / Ambiguity Condition |
|:---:|---|---|---|---|
| **X1** | **Backend Pairing** | • `php-flight` (PHP 8.x + Flight + Plates/Blade)<br>• `node-express` (Node.js + Express + EJS/JSX partials)<br>• `python-fastapi` (Python + FastAPI + Jinja2) | `php-flight` | When prompt asks to build an HTMX endpoint without declaring backend. |
| **X2** | **DOM Swap Strategy** | • `innerHTML` (Replace child contents of target)<br>• `outerHTML` (Replace target element completely)<br>• `morphdom` (Morphdom DOM diffing extension for input preservation)<br>• `beforeend` (Append to list / infinite scroll) | `innerHTML` | When creating dynamic partial replacements or forms. |
| **X3** | **Loading & Indicator Model** | • `htmx-indicator` (CSS opacity/spinner on `.htmx-request`)<br>• `skeleton-shimmer` (Swap in skeleton loader partial)<br>• `inline-disable` (Disable submit button during flight) | `htmx-indicator` | When designing interactive forms, filters, or search bars. |
| **X4** | **Browser History & URL Sync** | • `hx-push-url="true"` (Updates browser address bar & push history)<br>• `hx-replace-url="true"` (Replaces current history entry)<br>• `none` (Silent in-place DOM update without URL change) | `none` (Filters/Modals) / `true` (Tabs/Pages) | When building tabs, filters, or paginated lists. |
| **X5** | **Output Scope & Depth** | • `single-interaction` (Single HTMX form / widget)<br>• `complete-hypermedia-app` (Full hypermedia MPA with vendored assets) | `single-interaction` | When user request could mean a quick snippet or full view. |

---

## ⚡ Boolean Skip Conditions (Deterministic Bypass)

Skip interactive elicitation and proceed silently when ANY of the following are true:
1. **Cached Brief Exists**: `.tidyfactor/htmx-brief.md` exists.
2. **Explicit User Declaration**: Prompt explicitly declares backend and swap strategy (e.g. `"Add HTMX search with innerHTML and PHP backend"`).
3. **Direct Command Invocation**: User invokes explicit commands (`/fragments`, `/swap`, `/triggers`, `/forms`, `/indicators`).

---

## 💾 Brief Persistence Protocol

When `/brief` runs, save confirmed decisions to `.tidyfactor/htmx-brief.md`:
```markdown
# HTMX Hypermedia Brief
- Backend Pairing: [php-flight | node-express | python-fastapi]
- DOM Swap Strategy: [innerHTML | outerHTML | morphdom | beforeend]
- Loading Indicator: [htmx-indicator | skeleton-shimmer | inline-disable]
- History & URL: [hx-push-url | hx-replace-url | none]
- Scope Depth: [single-interaction | complete-hypermedia-app]
- Confirmed At: YYYY-MM-DD
```
