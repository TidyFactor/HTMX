# Workflow: brief

Discovers and records core HTMX hypermedia baselines (Backend Pairing, Swap Strategy, Indicator Model, History Sync) using CDL.

---

## Steps

1. **Check Existing State**:
   - Inspect `.tidyfactor/htmx-brief.md` and server routes for existing setup.

2. **Conduct Structured Discovery (Max 3 Questions)**:
   - If not specified, ask:
     1. **Backend Pairing (X1)**: PHP Flight, Node Express, or Python FastAPI?
     2. **DOM Swap Strategy (X2)**: innerHTML, outerHTML, or morphdom?
     3. **Loading Indicator (X3)**: CSS spinner or skeleton shimmer?

3. **Record Decisions**:
   - Save `.tidyfactor/htmx-brief.md` with confirmed parameters.

4. **Report Summary**:
   - Confirm baseline parameters and prompt user to invoke `/init` or `/fragments`.

---

## Validation checklist

- [ ] `.tidyfactor/htmx-brief.md` exists and contains confirmed values for X1–X5.
- [ ] No more than 3 questions were asked in a single round.
- [ ] Hypermedia baseline conforms to `references/memory/quality-bar.md`.
