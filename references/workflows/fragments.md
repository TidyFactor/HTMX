# Workflow: fragments

Builds server-rendered HTML partials and matching backend endpoint handlers.

---

## Steps

1. **Fragment Template**:
   - Create template file returning only HTML fragment markup without outer `<html>`/`<body>` tags.

2. **Backend Route**:
   - Return rendered fragment directly with `Content-Type: text/html`.

3. **Pre-Emit Self-Critique**:
   - `/* Pre-emit critique: P5 H5 E5 S5 R5 V5 D5 */`

---

## Validation checklist

- [ ] Fragment is self-contained HTML without outer document shells.
- [ ] Endpoint returns HTML header and handles errors gracefully.
- [ ] Pre-emit critique stamp included.
