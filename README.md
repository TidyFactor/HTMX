<div align="center">

# ⚡ TidyFactor HTMX `v1.2.0`
### Server-Driven Hypermedia Interactivity & Contextual Decision Engine

**The official hypermedia interaction track within the TidyFactor Architecture Ecosystem.**

[![npm version](https://img.shields.io/npm/v/@tidyfactor/htmx.svg?style=for-the-badge&color=3366CC)](https://www.npmjs.com/package/@tidyfactor/htmx)
[![License: Apache 2.0](https://img.shields.io/badge/License-Apache%202.0-blue.svg?style=for-the-badge)](LICENSE)
[![RTL Ready](https://img.shields.io/badge/RTL-Native%20Arabic-emerald.svg?style=for-the-badge)](README.ar.md)
[![Zero Build](https://img.shields.io/badge/Build-Zero%20Build%20Step-purple.svg?style=for-the-badge)](#-three-lifecycle-modes)

[🚀 Quick Start](#-quick-start) • [⚡ 10 Commands](#-command-set) • [🏛️ Ecosystem](#%EF%B8%8F-tidyfactor-ecosystem-architecture) • [📖 بالعربية](README.ar.md)

<br/><br/>

<p align="center">
  <img src="assets/hero-banner.png" alt="TidyFactor HTMX Hero Banner" width="100%" />
</p>

</div>

---

This is a **layer, not a full stack**. It owns how fragments get
requested, swapped, validated, and made navigable — not backend
architecture or data. It pairs with `tidyfactor-php` or
`tidyfactor-php-micro` (or any other server that can render HTML),
rather than replacing them.

## Three lifecycle modes
- **Init** — add the htmx layer to a project (new or existing backend).
- **Convert** — replace ad hoc `fetch()`/full-page-reload interactivity
  with htmx.
- **Improve** — audit and fix an existing htmx implementation.

## Command set
`init` · `assets` · `fragments` · `swap` · `triggers` · `forms` ·
`indicators` · `history` · `modules` · `i18n` — see `SKILL.md` for full
sequencing and each command's reference file under
`references/commands/`.

## Related skills
Part of the TidyFactor skill library — see `tidyfactor-html` (no
backend), `tidyfactor-php` (vanilla backend), `tidyfactor-php-micro`
(opinionated Flight+Medoo+Plates backend), and the planned
`tidyfactor-js` / `tidyfactor-js-micro` tracks.

## Developer
Built and maintained by **alwkala** — github.com/alwkala

## License
Licensed under the Apache License 2.0.


---

## 🚀 Installation & Quick Start

Choose your preferred installation method:

### Option A: Via TidyFactor CLI (Recommended)
Install directly using the official ecosystem package runner into your active workspace:
```bash
npx @tidyfactor/cli add htmx
```
*Or if you have the CLI installed globally (`npm i -g @tidyfactor/cli`):*
```bash
tidyfactor add htmx
```

### Option B: Via Open Agent Skills Ecosystem (skills.sh / Vercel Labs)
Install using the universal multi-agent standard across all supported IDEs (Cursor, Antigravity, Claude Code, Windsurf, Trae, Codex):
```bash
npx skills add tidyfactor/htmx
```

### Option C: Standalone Zero-Dependency Runner (NPM Direct)
Run the dedicated skill installer directly with automatic cache invalidation:
```bash
npx @tidyfactor/htmx@latest
```

---

## 🏛️ TidyFactor Ecosystem Architecture

**TidyFactor** is a modular web architecture and AI coding agent skill ecosystem built on clear separation of concerns across the product lifecycle:

```
TidyFactor Organization (github.com/TidyFactor)
│
├── Design Skills
│   ├── Cinematic    → Experience / "Wow"     (Apple × Cartier Scroll-Driven Landing Pages)
│   ├── Design       → Prototype / "Build"    (Code-Native UI Design Engine & Figma Alternative)
│   └── Styler       → Production / "Ship"    (Framework Styler & RTL Polish Engine)
│
├── Development Skills
│   ├── HTML         → Content & Static       (Semantic SEO & Static Platform Starter)
│   ├── HTMX         → Hypermedia             (Server-Driven Micro-Interactions)
│   ├── JS           → Vanilla SPA            (Framework-Free Reactive ES Modules)
│   ├── PHP          → Server-Rendered        (Modern PHP 8.x Component UI & Architecture)
│   └── Next         → Multi-Tenant SaaS      (Next.js 16, React 19, Supabase RLS & Dev-Perf)
│
└── Growth Skills
    └── Marketing    → Growth / Revenue       (Direct Response, Pillar SEO & Content Lifecycles)
```

### 💎 Frontend Triad

```
                TidyFactor
                    │
          ┌─────────┼─────────┐
          │         │         │
      Cinematic   Design    Styler
          │         │         │
      Experience Prototype Production
          │         │         │
       "Wow"      "Build"   "Ship"
```

### 📦 Community Package & Skill Parity

| Track | Category | GitHub Repository | Agent Skill | NPM Package |
| :--- | :--- | :--- | :--- | :--- |
| **Cinematic** | Design | [`TidyFactor/Cinematic`](https://github.com/TidyFactor/Cinematic) | `tidyfactor-cinematic` | [`@tidyfactor/cinematic`](https://www.npmjs.com/package/@tidyfactor/cinematic) |
| **Design** | Design | [`TidyFactor/Design`](https://github.com/TidyFactor/Design) | `tidyfactor-design` | [`@tidyfactor/design`](https://www.npmjs.com/package/@tidyfactor/design) |
| **Styler** | Design | [`TidyFactor/Styler`](https://github.com/TidyFactor/Styler) | `tidyfactor-styler` | [`@tidyfactor/styler`](https://www.npmjs.com/package/@tidyfactor/styler) |
| **Next** | Development | [`TidyFactor/Next`](https://github.com/TidyFactor/Next) | `tidyfactor-next` | [`@tidyfactor/next`](https://www.npmjs.com/package/@tidyfactor/next) |
| **HTML** | Development | [`TidyFactor/HTML`](https://github.com/TidyFactor/HTML) | `tidyfactor-html` | [`@tidyfactor/html`](https://www.npmjs.com/package/@tidyfactor/html) |
| **HTMX** | Development | [`TidyFactor/HTMX`](https://github.com/TidyFactor/HTMX) | `tidyfactor-htmx` | [`@tidyfactor/htmx`](https://www.npmjs.com/package/@tidyfactor/htmx) |
| **JS** | Development | [`TidyFactor/JS`](https://github.com/TidyFactor/JS) | `tidyfactor-js` | [`@tidyfactor/js`](https://www.npmjs.com/package/@tidyfactor/js) |
| **PHP** | Development | [`TidyFactor/PHP`](https://github.com/TidyFactor/PHP) | `tidyfactor-php` | [`@tidyfactor/php`](https://www.npmjs.com/package/@tidyfactor/php) |
| **Marketing** | Growth | [`TidyFactor/Marketing`](https://github.com/TidyFactor/Marketing) | `tidyfactor-marketing` | [`@tidyfactor/marketing`](https://www.npmjs.com/package/@tidyfactor/marketing) |

---

## 👨‍💻 Organization & Support

- 🌐 **Official Website:** [https://tidyfactor.com/](https://tidyfactor.com/)
- 📚 **Official Documentation:** [https://tidyfactor.com/documentation](https://tidyfactor.com/documentation)
- 🤝 **Official Partner Website:** [Alwkala Digital Agency](https://alwkala.com/)
- 🐙 **GitHub Organization:** [github.com/TidyFactor](https://github.com/TidyFactor)
- 📧 **Business Inquiries:** [hello@tidyfactor.com](mailto:hello@tidyfactor.com)
- 📱 **WhatsApp:** [+20 101 665 6899](https://wa.me/201016656899)
- 📞 **Phone:** +20 101 665 6899
- 📍 **Location:** Cairo, Egypt

---

## 📜 License

Licensed under the **Apache License 2.0**. Copyright (c) 2026 [TidyFactor](https://tidyfactor.com) & [Alwkala](https://alwkala.com).
