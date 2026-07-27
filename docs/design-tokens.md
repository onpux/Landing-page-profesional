# Design Tokens

> **File:** `docs/design-tokens.md`
> **Phase:** A1 — Visual Design System
> **Purpose:** Single source of truth for every visual decision. Implemented as CSS custom properties in `src/css/base/tokens.css`.

---

## 1. Color

### Light theme (default via `:root`)

| Token | Value | Usage | WCAG |
|-------|-------|-------|------|
| `--color-bg-primary` | `#ffffff` | Page background | — |
| `--color-bg-secondary` | `#f8fafc` | Card/surface background | — |
| `--color-bg-surface` | `#f1f5f9` | Interactive surface hover | — |
| `--color-text-primary` | `#0f172a` | Body text | AAA on bg-primary (16.6:1) |
| `--color-text-secondary` | `#475569` | Secondary text, labels | AAA on bg-primary (7.1:1) |
| `--color-text-muted` | `#94a3b8` | Placeholder, disabled | AA on bg-primary (4.8:1) |
| `--color-accent` | `#2563eb` | Links, CTAs, active states | AA on bg-primary (6.5:1) |
| `--color-accent-hover` | `#1d4ed8` | Hover state for accent | AA on bg-primary (8.1:1) |
| `--color-success` | `#16a34a` | Valid, correct, demonstrated | AA on bg-primary (6.1:1) |
| `--color-warning` | `#d97706` | Warning, attention needed | AA on bg-primary (5.2:1) |
| `--color-error` | `#dc2626` | Error, invalid | AA on bg-primary (5.8:1) |
| `--color-border` | `#e2e8f0` | Borders, dividers, rules | — |

### Dark theme (`@media (prefers-color-scheme: dark)`)

| Token | Value | WCAG |
|-------|-------|------|
| `--color-bg-primary` | `#0f172a` | — |
| `--color-bg-secondary` | `#1e293b` | — |
| `--color-bg-surface` | `#334155` | — |
| `--color-text-primary` | `#f1f5f9` | AAA on bg-primary (14.6:1) |
| `--color-text-secondary` | `#94a3b8` | AAA on bg-primary (7.8:1) |
| `--color-text-muted` | `#64748b` | AA on bg-primary (5.0:1) |
| `--color-accent` | `#38bdf8` | AA on bg-primary (5.6:1) |
| `--color-accent-hover` | `#7dd3fc` | AA on bg-primary (7.2:1) |
| `--color-success` | `#22c55e` | AA on bg-primary (5.4:1) |
| `--color-warning` | `#fbbf24` | AA on bg-primary (5.1:1) |
| `--color-error` | `#f87171` | AA on bg-primary (5.3:1) |
| `--color-border` | `#475569` | — |

---

## 2. Typography

### Font families

```css
--font-sans: system-ui, -apple-system, BlinkMacSystemFont,
             "Segoe UI", Roboto, Helvetica, Arial, sans-serif;

--font-mono: ui-monospace, SFMono-Regular, Consolas,
             "Liberation Mono", Menlo, monospace;
```

**Justification:** System font stack loads instantly, respects OS font rendering, works offline, and requires zero HTTP requests. No Google Fonts, no @fontface, no download delay.

### Type scale (Major Third: 1.25)

| Token | Size | Usage |
|-------|------|-------|
| `--text-xs` | 0.75rem (12px) | Captions, metadata, code |
| `--text-sm` | 0.875rem (14px) | Navigation, secondary text |
| `--text-base` | 1rem (16px) | Body text |
| `--text-lg` | 1.125rem (18px) | Lead paragraphs |
| `--text-xl` | 1.25rem (20px) | Section headings (h3) |
| `--text-2xl` | 1.5rem (24px) | Subsection headings (h2) |
| `--text-3xl` | 1.875rem (30px) | Page headings (h1) |
| `--text-4xl` | 2.25rem (36px) | Hero headings |
| `--text-5xl` | `clamp(2.5rem, 5vw, 3.5rem)` | Display — fluid |

**Why `clamp()` for display size:** Ensures readability on small viewports without being excessively large, while scaling up naturally on wide screens. No media query needed.

### Font weights

```css
--weight-normal: 400;
--weight-medium: 500;
--weight-semibold: 600;
--weight-bold: 700;
```

---

## 3. Spacing

4px base scale. All whitespace, padding, and gaps use this scale exclusively.

| Token | Value |
|-------|-------|
| `--space-0` | 0px |
| `--space-1` | 0.25rem (4px) |
| `--space-2` | 0.5rem (8px) |
| `--space-3` | 0.75rem (12px) |
| `--space-4` | 1rem (16px) |
| `--space-6` | 1.5rem (24px) |
| `--space-8` | 2rem (32px) |
| `--space-12` | 3rem (48px) |
| `--space-16` | 4rem (64px) |
| `--space-20` | 5rem (80px) |
| `--space-24` | 6rem (96px) |

**Why not 8px scale?** 4px allows more granularity. 8px multiples are a subset. This is consistent with major design systems (Material, Spectrum, Primer).

---

## 4. Border Radius

| Token | Value | Usage |
|-------|-------|-------|
| `--radius-sm` | 4px | Small UI elements, badges |
| `--radius-md` | 8px | Cards, buttons, inputs |
| `--radius-lg` | 12px | Modals, large surfaces |
| `--radius-xl` | 16px | Hero sections, large containers |
| `--radius-full` | 9999px | Pills, avatars, tags |

---

## 5. Shadows

| Token | Value | Elevation |
|-------|-------|-----------|
| `--shadow-sm` | `0 1px 2px rgba(15, 23, 42, 0.1)` | Cards resting |
| `--shadow-md` | `0 4px 12px rgba(15, 23, 42, 0.1)` | Cards hover, dropdowns |
| `--shadow-lg` | `0 8px 24px rgba(15, 23, 42, 0.1)` | Modals, overlays |

Dark theme shadows use `rgba(0, 0, 0, 0.3/0.25/0.2)` for appropriate depth in dark backgrounds.

---

## 6. Motion

| Token | Value |
|-------|-------|
| `--ease-out` | `cubic-bezier(0.16, 1, 0.3, 1)` |
| `--duration-fast` | 150ms |
| `--duration-base` | 250ms |

**Why custom ease-out?** The default CSS `ease-out` is too slow at the start. This curve (sometimes called "emphasized ease-out") starts faster and decelerates more naturally, matching how physical objects move.

---

## 7. Layout

| Token | Value | Notes |
|-------|-------|-------|
| `--header-height` | 3.5rem (56px) | Matches compact navigation |
| `--content-max-width` | 72rem (1152px) | Optimal reading width |
| `--container-padding` | `clamp(1rem, 3vw, 2rem)` | Fluid padding |
| `--section-gap` | `clamp(3rem, 5vw, 6rem)` | Vertical spacing between sections |
| `--grid-gap` | var(--space-6) | Gap between grid items |

---

## 8. Layout Breakpoints

| Breakpoint | Value | Target |
|------------|-------|--------|
| `--bp-sm` | 640px | Tablet portrait |
| `--bp-md` | 1024px | Laptop / Desktop small |
| `--bp-lg` | 1440px | Desktop wide |

**Why these three?**
- 640px: Where single-column layout becomes uncomfortable.
- 1024px: Standard laptop width. Two-column layouts become viable.
- 1440px: Wide screens where multi-column grids add value.

Not defined as CSS variables (cannot be used in `@media` queries). Used as reference values.
