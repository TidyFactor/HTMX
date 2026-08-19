# Command: `assets` — Vendoring & Version Hygiene

## Purpose
Keep htmx and any extensions (SSE, WebSocket, etc.) locally vendored,
version-pinned, and free of CDN dependency — consistent with TidyFactor's
"portable, no lock-in" principle applied to a third-party script.

## When to run it
- The audit shows htmx (or an extension) loaded from a CDN `<script
  src="https://...">`, an unpinned "latest" reference, or multiple
  versions of htmx loaded across different pages.
- User says "stop using the CDN for htmx", "pin the htmx version", or
  runs `assets`.

## What it does
1. Download the exact pinned version of `htmx.min.js` (and any
   extensions in use — `sse.js`, `ws.js`, etc.) into
   `assets/js/vendor/`, named with the version in the filename or
   tracked in `README.md`/a small `vendor.json` manifest — never
   "latest".
2. Remove every CDN `<script src>` reference; every page loads the
   vendored copy via one shared layout include, never a per-page
   duplicate `<script>` tag.
3. Record the exact version and source URL it was downloaded from in
   the manifest, so upgrading later is a deliberate, auditable change —
   not a silent drift.
4. If an extension is added, confirm with the user first (each one is a
   small addition to what's loaded on every page) rather than vendoring
   speculatively.
5. Apply the same cache-busting convention the project's backend skill
   already uses for other assets (`?v=<version>` from `logic.md`'s
   config, or the build-time hash if on `tidyfactor-html`) — don't
   invent a separate scheme just for htmx.

## Output convention
```
assets/js/vendor/htmx.min.js
assets/js/vendor/htmx-ext-sse.js      (only if actually used)
assets/js/vendor/vendor.json           (version + source manifest)
```

## Checklist
- [ ] No CDN `<script src>` for htmx or any extension remains
- [ ] Exact version pinned and recorded in the manifest
- [ ] Loaded once via a shared layout include, no per-page duplication
- [ ] Any extension present was a confirmed addition, not speculative
- [ ] Cache-busting matches the project's existing convention
