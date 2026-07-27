# CSS Architecture

> **File:** `docs/css-architecture.md`
> **Phase:** A1 — Visual Design System
> **Purpose:** Define how CSS is organized, how layers are ordered, and naming conventions.

---

## Layer Order

CSS is organized in progressive layers. Each layer builds on the previous one.

```
1. RESET       — Normalize cross-browser inconsistencies
2. TOKENS      — CSS custom properties (design tokens)
3. BASE        — Element-level styles (headings, paragraphs, links)
4. LAYOUT      — Grid, container, structural components
5. COMPONENTS  — Reusable UI components (buttons, cards, forms)
6. PAGES       — Page-specific overrides (only when necessary)
7. UTILITIES   — Single-purpose helper classes (layout overrides)
8. THEME       — prefers-color-scheme overrides (always last)
```

### Why this order?

- **Lowest specificity first:** Reset and base styles have the least specificity, making them easy to override.
- **Component styles are self-contained:** A button component knows nothing about the page it lives in.
- **Theme as a final override:** Theme changes only affect color tokens, never layout or structure.

---

## Naming Convention: BEM (Block__Element--Modifier)

```css
/* Block */
.card { }

/* Element */
.card__title { }
.card__image { }

/* Modifier */
.card--featured { }
.card--compact { }

/* State (via data attributes or pseudo-classes) */
.card:focus-visible { }
.card[aria-disabled="true"] { }
```

### Why BEM and not utility-first?

| Approach | Pros | Cons | Verdict |
|----------|------|------|---------|
| **BEM** | Predictable, standard in industry, works at scale | Verboser | ✅ Selected |
| Utility-first (Tailwind) | Fast prototyping | HTML bloat, not semantic | ❌ |
| SMACSS | Flexible | Less prescriptive | ❌ |
| CSS-in-JS | Scoped styles | Requires JS runtime | ❌ |

---

## File Organization

```
src/css/
├── main.css              ← Entry point (@import all layers)
├── base/
│   ├── reset.css         ← Box-sizing, margin removal, base font
│   └── tokens.css        ← CSS custom properties (design tokens)
├── layout/
│   ├── container.css     ← .container, .section
│   └── grid.css          ← .grid, .grid__col-*
├── components/
│   ├── button.css
│   ├── card.css
│   ├── navbar.css
│   ├── form.css
│   ├── badge.css
│   ├── code.css
│   └── table.css
├── pages/
│   └── home.css          ← Page-specific section styles
├── utilities/
│   ├── helpers.css       ← .sr-only, .mt-*, .text-center
│   └── theme.css         ← prefers-color-scheme (the last layer)
```

---

## Rules

### 1. One component per file

Each `.css` file contains styles for exactly one BEM block. If a file needs styles for two blocks, split it.

### 2. No ID selectors

IDs have extremely high specificity and cannot be reused. Use classes exclusively.

### 3. No `!important` except in utilities

Utilities (`.sr-only`, `.text-center`, `.hidden`) are the only place where `!important` is acceptable.

### 4. Specify selector depth

```css
/* ✅ Good */
.card__title { }

/* ❌ Bad */
.card .card__body .card__title { }
```

Maximum recommended depth: 3 levels (`.block__element--modifier`).

### 5. Custom properties over preprocessor variables

| Need | Solution |
|------|----------|
| Single value | CSS custom property |
| Computation | `calc()` with custom properties |
| Dark/Light theme | Custom property reassignment in `prefers-color-scheme` |
| Math operations | Not needed (design tokens are pre-calculated) |

### 6. No `px` other than base font

Use `rem` for sizing and spacing. The only exception is `1px` for borders.

### 7. Mobile First

```css
/* ✅ Good: base = mobile, min-width adds complexity */
.card {
  padding: var(--space-4);
}

@media (min-width: 640px) {
  .card {
    padding: var(--space-6);
  }
}

/* ❌ Bad: max-width removes complexity */
.card {
  padding: var(--space-6);
}

@media (max-width: 639px) {
  .card {
    padding: var(--space-4);
  }
}
```
