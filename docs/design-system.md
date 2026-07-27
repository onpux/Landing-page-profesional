# Visual Design System

> **File:** `docs/design-system.md`
> **Phase:** A1 — Visual Design System
> **Purpose:** Define how components are built. Rules for states, accessibility, and usage.

---

## Component Anatomy

Every interactive component must define these states:

| State | Trigger | Visual requirement |
|-------|---------|--------------------|
| `rest` | Default appearance | Apply component tokens |
| `hover` | Cursor over element | Visual feedback (brightness, border, shadow) |
| `focus-visible` | Keyboard focus | 2px outline + 2px offset using accent color |
| `active` | Mouse press / touch | Inverted or pressed state |
| `disabled` | Non-interactive | 50% opacity, no pointer events |

### Accessibility requirements for all components

- Minimum touch target: 44×44px (WCAG 2.2 Target Size).
- Focus must never be removed without replacement (`:focus-visible` is fine, never `outline: none` without alternative).
- Color is never the only differentiator (use icons, text, or patterns alongside).
- ARIA attributes only when native HTML semantics are insufficient.

---

## 1. Buttons

### Variants

| Variant | Class | Usage |
|---------|-------|-------|
| Primary | `.btn--primary` | Main call-to-action |
| Secondary | `.btn--secondary` | Alternative action |
| Ghost | `.btn--ghost` | Low emphasis action |
| Icon | `.btn--icon` | Icon-only action (with aria-label) |

### Sizes

| Size | Class | Padding | Font |
|------|-------|---------|------|
| Small | `.btn--sm` | `var(--space-1) var(--space-3)` | `var(--text-sm)` |
| Medium | `.btn` (default) | `var(--space-2) var(--space-4)` | `var(--text-base)` |
| Large | `.btn--lg` | `var(--space-3) var(--space-6)` | `var(--text-lg)` |

### Example

```html
<button class="btn btn--primary" type="button">
  Default button
</button>
```

---

## 2. Cards

### Structure

```
.card
├── .card__media         (optional: image, video, icon)
├── .card__body
│   ├── .card__title     (required)
│   ├── .card__text      (required)
│   └── .card__footer    (optional: actions, tags)
```

### Usage

Cards contain related information as a single topic. Never use a card without a title.

---

## 3. Navigation

### Structure

```
.navbar (static or fixed)
├── .navbar__brand       (logo or site name)
├── .navbar__list        (ul)
│   ├── .navbar__item
│   │   └── .navbar__link
│   └── ...
└── .navbar__actions     (theme toggle, etc.)
```

### States

- Current page: `.navbar__link[aria-current="page"]` (accent color + underline).
- On mobile (<640px): `.navbar` collapses to hamburger using CSS `:target` or checkbox hack (no JS).

---

## 4. Forms

### Structure

```
.form
├── .form__group
│   ├── label.form__label
│   ├── input.form__input / textarea.form__input
│   └── .form__error (span, role="alert")
└── .form__actions
    └── button.btn[type="submit"]
```

### Validation

- Use native HTML5 validation (`required`, `type="email"`, `minlength`).
- `:user-invalid` pseudo-class for styling (no JS validation needed).
- Error messages via `.form__error` with `role="alert"`.

### Accessibility

- Every input must have an associated `<label>`.
- `aria-describedby` links inputs to their error messages.
- `autocomplete` attributes for common fields.

---

## 5. Badges & Tags

Small labels for metadata, categories, or status.

| Variant | Class | Color |
|---------|-------|-------|
| Default | `.badge` | Neutral |
| Success | `.badge--success` | Green |
| Warning | `.badge--warning` | Amber |
| Error | `.badge--error` | Red |

---

## 6. Code blocks

For showing HTML, CSS, or code snippets inline.

- Use `<code>` for inline code.
- Use `<pre><code>` for blocks.
- Both use `var(--font-mono)` and `var(--text-sm)`.
- Code blocks have a subtle background (`var(--color-bg-surface)`) and border.

---

## 7. Tables

For structured data display (e.g., the Competency Matrix).

- Use `<table>`, `<thead>`, `<tbody>`, `<th>` (with `scope`).
- Responsive: wrap in `.table-wrapper` with horizontal scroll on small viewports.
- Alternating row colors for readability.

---

## 8. Lists

### Types

| Type | Element | Marker |
|------|---------|--------|
| Unordered | `<ul>` | Bullet (default) |
| Ordered | `<ol>` | Numeric (default) |
| Definition | `<dl>` | Term + description |

Custom markers via `::before` pseudo-elements for decorative lists.
