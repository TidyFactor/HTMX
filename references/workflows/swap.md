# Workflow: swap

Calibrates DOM swap strategies (`innerHTML`, `outerHTML`, `morphdom`) and target resolution.

---

## Steps

1. **Target Identification**:
   - Ensure target element has a unique ID (e.g. `id="results-container"`).

2. **Swap Strategy Selection**:
   - Add `hx-swap="innerHTML"` or `hx-swap="morphdom"` with transition easing.

3. **Pre-Emit Self-Critique**:
   - `/* Pre-emit critique: P5 H5 E5 S5 R5 V5 D5 */`

---

## Validation checklist

- [ ] Target element exists in DOM before swap execution.
- [ ] Swap mode avoids unintended parent destruction.
- [ ] Pre-emit critique stamp included.
