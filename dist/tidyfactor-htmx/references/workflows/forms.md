# Workflow: forms

Constructs type-safe HTMX forms with inline validation, CSRF tokens, and optimistic indicators.

---

## Steps

1. **Form Markup**:
   - Add `hx-post="/endpoint"` and `hx-target="#form-feedback"`.
   - Inject hidden CSRF token input.

2. **Validation Errors**:
   - Backend returns error alert fragment on validation failure with `422 Unprocessable Entity` or `200 OK` swap.

3. **Pre-Emit Self-Critique**:
   - `/* Pre-emit critique: P5 H5 E5 S5 R5 V5 D5 */`

---

## Validation checklist

- [ ] CSRF token included on all mutations.
- [ ] Inline feedback element targeted and rendered.
- [ ] Pre-emit critique stamp included.
