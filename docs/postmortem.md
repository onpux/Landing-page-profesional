# Postmortem — HTML & CSS Engineering Showcase

> **File:** `docs/postmortem.md`
> **Phase:** C5 — Postmortem
> **Date:** 2026-07-26
> **Purpose:** Reflect on the development process, what worked, what didn't, and what would be done differently.

---

## What worked well

### 1. Starting with constraints before code

Defining the project constraints (zero dependencies, Mobile First, WCAG AA, no JS for CSS-solvable UI) before writing any code prevented scope creep. Every decision could be evaluated against these constraints.

### 2. Separating "implemented" from "verified"

The Quality Assurance section started with a single "Pass" column for everything. Changing to **Implemented | Verified** revealed how much work remained and forced honesty about what had actually been tested.

### 3. The Engineering Contract as a single source of truth

Having one document that explains how decisions are made (problem → alternatives → implementation → verification → documentation) eliminated endless debates about "what's the right way to do this."

### 4. HTML-first discovery

The original hypothesis was 8 components. Writing the HTML first revealed that:
- `<details>/<summary>` was the right solution for expandable decisions (not a custom JS component)
- Constraint lists benefited from `<dl>` semantic structure
- The QA cards naturally formed a grid pattern

These discoveries would not have happened if we had designed components on paper first.

### 5. YAGNI discipline

Resisting the urge to add:
- A contact form (no portfolio, no need)
- JavaScript accordions (`<details>` was sufficient)
- External fonts (system font stack was faster and more private)
- Icon libraries (no decorative icons that don't add meaning)

Each of these saved complexity and maintenance burden.

---

## What could be improved

### 1. Too much documentation early

The project accumulated 5 documents before any CSS was written. While each document serves a purpose, a leaner start would have been:

```
engineering-contract.md (always needed)
tokens.md (always needed)
→ then write HTML
→ then write CSS
→ then document what emerged
```

The `design-system.md` and `css-architecture.md` could have waited until the code revealed patterns.

### 2. The "hypothesis as certainty" trap

Early in the process, the project stated things like "there are 8 components" before confirming them through code. This created a subtle pressure to implement all 8 even if some weren't needed. The shift to "hypothesis → implement → verify → document" was the right correction.

### 3. Not catching the false Pass status earlier

The original QA tables showed "Pass" for everything before any verification had been done. This is the equivalent of marking a test as passed before running it. The fix (Existe | Medido | Resultado columns) should have been the design from day one.

The final model resolves a subtle issue with the previous Implemented | Verified split: metrics like Lighthouse scores and W3C validation results cannot be "implemented" — they are measurements. The **Existe | Medido | Resultado** model separates existence (N/A for metrics) from measurement (⏳ until DevTools is opened), making the status honest without semantic contortion.

### 4. Over-engineering the documentation format

Documents were written with metadata headers, phase markers, and file references — patterns better suited to a team wiki than a personal project. A simpler README-centric approach would have been sufficient.

---

## What would be done differently

### Next time:

1. **Write code first, document decisions second.** Start with `index.html` and `main.css`, capture decisions as they arise, not before.
2. **Keep a single `docs/` file until there's a reason to split.** One `decisions.md` file that grows with the project, then refactored into separate files only when it becomes unwieldy.
3. **Use the "Implemented | Verified" column split from the start.** It forces honesty about the difference between "I built it" and "I proved it works."
4. **Ship earlier.** Get the HTML in front of a browser (or a reviewer) before worrying about documentation formatting.

---

## Lessons for future projects

### The most important lesson

> **"No implementes para demostrar conocimientos; implementa para resolver un problema, y deja que el conocimiento se evidencie como consecuencia."**

Every element in a project should exist because it solves a concrete problem, not because it demonstrates a technique. If the code is clean and the architecture is sound, the competencies will be obvious.

### The second most important lesson

> **"La implementación es la fuente de verdad. La documentación describe únicamente aquello que existe."**

Documentation written before code makes promises that may never be kept. Documentation written after code records decisions that have already been validated.

### The third most important lesson

> **"'Verified' es un estado distinto de 'implemented'."**

Code can exist without being tested. Testing without verifying the result is meaningless. An honest "Pending" is worth more than a false "Pass."

---

## Metrics

| Metric | Value |
|--------|-------|
| Files | 24 |
| CSS files | 15 |
| JavaScript | 0 |
| External dependencies | 0 |
| Phases | 7 (A0 · A0.5 · A1 · A2 · B1 · B2 · B3 · C1–C7) |
| Feature freeze | Active (C7) — bug fixes only from v1.0.0 |
| Components | 7 verified + 1 detail/summary (native) |
| HTML validation errors | Pending |
| Lighthouse scores | Pending |
