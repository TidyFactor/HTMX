# Memory: architecture (HTMX Layout & Vendoring Rules)

Directory structure and event lifecycle rules for HTMX hypermedia apps.

---

## 📁 Standard HTMX Directory Layout

```
project-root/
├── public/
│   ├── js/
│   │   └── vendor/
│   │       └── htmx.min.js      # Vendored locally (NEVER unpinned public CDN)
│   └── css/
│       └── htmx-indicators.css  # Indicator opacity and spinner styles
├── views/
│   ├── layouts/
│   │   └── base.php             # Master layout with #main-content
│   └── fragments/               # Reusable server-rendered partials
│       ├── search-results.php
│       ├── user-row.php
│       └── cart-drawer.php
```

---

## 🔒 Vendoring Invariant

HTMX must be vendored locally at `js/vendor/htmx.min.js`. Never rely on external CDN links (`unpkg.com/htmx.org`) in production deployments.
