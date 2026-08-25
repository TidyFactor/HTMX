# Workflow: init

Scaffolds a zero-CDN, locally vendored HTMX hypermedia layer on top of a server backend.

---

## Steps

0. **Step 0: CDL Resolution & Brief Check**:
   - Check `.tidyfactor/htmx-brief.md`. If missing, apply default `php-flight` and `innerHTML`.

1. **Vendor HTMX Locally**:
   - Save `htmx.min.js` to `public/js/vendor/htmx.min.js`.
   - Inject `<script src="./js/vendor/htmx.min.js" defer></script>` into master layout.

2. **Setup Indicator CSS**:
   - Inject `.htmx-indicator { display: none; } .htmx-request .htmx-indicator { display: inline-block; }`.

3. **Pre-Emit Self-Critique**:
   - `/* Pre-emit critique: P5 H5 E5 S5 R5 V5 D5 */`

---

## Validation checklist

- [ ] HTMX library vendored locally; no third-party CDN dependency.
- [ ] Indicator CSS classes present in stylesheet.
- [ ] Pre-emit critique stamp included.
