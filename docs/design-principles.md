# Design Principles

> **File:** `docs/design-principles.md`
> **Phase:** A1 — Visual Design System
> **Purpose:** Summary of the engineering philosophy. The authoritative document is `docs/engineering-contract.md`. This file serves as a quick reference.

---

## Source of Truth

The **[Engineering Contract](../engineering-contract.md)** is the single source of truth for implementation decisions. Read it first.

---

## Principles (Summary)

### Consistency

One spacing scale, one palette, one typographic scale, one set of radii. The same problem always looks the same.

### Accessibility First

WCAG AA contrast, keyboard operability, readable without stylesheets, respects `prefers-reduced-motion`.

### Content First

Typography for readability, whitespace for hierarchy, color for meaning — never for decoration.

### Mobile First

Base styles = mobile. Desktop adds capability with `min-width`. No `max-width` queries.

### Performance First

System fonts, no icon libraries, no frameworks, inline SVG. Every byte justified.

### Progressive Enhancement

Semantic HTML provides the baseline. CSS enhances. JS is the last resort.

### Minimal Dependencies

Zero external libraries, zero build tools, zero preprocessors, zero CDNs.

---

## Quick Evaluation

Before writing any code, ask:

1. What competency does this element demonstrate?
2. Can I solve this with HTML or CSS alone?
3. Does it work at 320px?
4. Does it pass WCAG AA?
5. Can I simplify without losing functionality?

If you cannot answer the first question, the element should not exist.
