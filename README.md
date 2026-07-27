# HTML & CSS Engineering Showcase

> A static web application demonstrating modern HTML5, CSS3, accessibility and responsive engineering practices, aligned with the competencies evaluated in the freeCodeCamp **Legacy Responsive Web Design v8** Certification.

**Author:** Onpux  
**Status:** v1.0.0  
**Dependencies:** Zero  
**Build step:** None (open `index.html` directly)

---

## Purpose

This project is a **piece of technical evidence**. It does not sell a brand, showcase a portfolio, or market a service. Its only objective is to verifiably demonstrate that the author masters the competencies evaluated by the freeCodeCamp Legacy Responsive Web Design v8 Certification through clean, accessible, and professionally organized code.

Every element exists to solve a concrete problem. Nothing was added to "show off" knowledge. Competencies are evidenced as a consequence of solving real layout, accessibility, and responsiveness challenges.

---

## How to Review (15–20 minutes)

1. **Read the [Project Constraints](#project-constraints)** — understand the deliberate limitations.
2. **Open DevTools → inspect CSS custom properties on `:root`** — verify the design tokens.
3. **Resize the viewport from 320px to 3840px** — verify responsive behaviour.
4. **Navigate using only the keyboard** (`Tab`, `Shift+Tab`, `Enter`, `Space`) — verify accessibility.
5. **Inspect semantic HTML structure** — verify `header`, `nav`, `main`, `section`, `article`, `figure`, `aside`, `footer`.
6. **Review [Engineering Decisions](docs/engineering-contract.md#el-mecanismo-de-decisión)** — understand why each choice was made.
7. **Open the repository** — review commit history and architecture.

---

## Project Constraints

| Constraint | Justification |
|------------|---------------|
| HTML5 only | Evaluates HTML Living Standard mastery without proprietary extensions |
| CSS3 only | No preprocessors (Sass, PostCSS), no frameworks (Bootstrap, Tailwind) |
| No JavaScript for CSS-solvable UI | Tabs, accordions, tooltips use native HTML/CSS — JS is the last resort |
| Zero external dependencies | No libraries, no CDNs, no icon sets, no font downloads |
| System font stack | Zero HTTP requests for typography. Better performance, privacy, offline |
| No build step | Open `index.html` directly. No bundlers, transpilers, or watchers |
| Mobile First | Base styles are for the smallest viewport. Desktop adds capabilities |
| WCAG 2.2 Level AA minimum | Accessibility is a requirement from the first line of code |

---

## Competency Matrix

| Competency | Evidence | Location |
|------------|----------|----------|
| HTML5 Semantic | `header`, `nav`, `main`, `section`, `article`, `figure`, `figcaption`, `aside`, `footer` | Technical Showcase → HTML |
| Flexbox | Navigation layout, card components | Navbar, Components Gallery |
| CSS Grid | Component gallery, QA cards layout | Technical Showcase → CSS |
| CSS Variables | Design tokens as custom properties on `:root` | `tokens.css` |
| `clamp()` / `min()` / `max()` | Fluid typography, responsive spacing | Technical Showcase → CSS |
| Media Queries | 3 breakpoints (640px, 1024px, 1440px), Mobile First | Quality → Responsive |
| `prefers-color-scheme` | Automatic dark/light theme, zero JavaScript | Quality → Accessibility |
| `prefers-reduced-motion` | Conditional animations respecting user preference | Quality → Accessibility |
| Pseudo-classes / pseudo-elements | `:hover`, `:focus-visible`, `:disabled`, `::before`, `::after` | Component Gallery |
| Keyboard Navigation | Skip link, `:focus-visible` on all interactive elements | Quality → Accessibility |
| WCAG AA Contrast | Verified for every colour token in both themes | Quality → Accessibility |

---

## Architecture

### CSS Layer Order

```
Reset → Tokens → Layout → Components → Pages → Utilities → Theme
```

Each layer builds on the previous one without breaking the cascade. Components are isolated. Theme changes affect only colour tokens.

### Naming Convention: BEM

```css
.block {}
.block__element {}
.block--modifier {}
```

### File Structure

```
src/
├── css/
│   ├── main.css                ← Entry point (14 @imports)
│   ├── base/                   ← reset.css, tokens.css
│   ├── layout/                 ← container.css, grid.css
│   ├── components/             ← navbar, button, badge, code-block, table, qa-card, decision
│   ├── pages/                  ← home.css
│   └── utilities/              ← helpers.css, theme.css

docs/
├── engineering-contract.md     ← Decision-making framework (read first)
├── design-principles.md        ← Quick reference
├── design-tokens.md            ← Token documentation with WCAG verification
├── design-system.md            ← Component rules
├── css-architecture.md         ← Methodology and conventions
└── postmortem.md               ← Lessons learned

index.html                      ← Single page application
LICENSE                         ← MIT
```

---

## Quality Assurance

All requirements are tracked with three distinct statuses:

| Column | Meaning |
|--------|---------|
| **Existe** | Does the code exist for this? (✅, N/A) |
| **Medido** | Has it been tested/measured? (✅, ⏳) |
| **Resultado** | What was the actual result? (OK, —, FAIL) |

**[Live QA dashboard](index.html#quality)** — see the full tables for Accessibility, Responsive, Performance, SEO, and Browser Compatibility.

---

## Versioning

| Phase | Status |
|-------|--------|
| C6 — Release | ✅ Ready |
| **C7 — Freeze** | **🔒 Active** — No new features. Bug fixes only. All functional improvements go to v1.1.0. |

---

## Documentation

- **[Engineering Contract](docs/engineering-contract.md)** — The single source of truth for how every implementation decision is made. Read this first.
- **[Design Tokens](docs/design-tokens.md)** — 8 token categories with WCAG AA verified contrast ratios.
- **[Visual Design System](docs/design-system.md)** — Component anatomy, states, and accessibility requirements.
- **[CSS Architecture](docs/css-architecture.md)** — 8-layer cascade, BEM, 7 rules.
- **[Postmortem](docs/postmortem.md)** — Lessons learned during development.

---

## How to Run

No build step. Open in a browser:

```bash
# Clone the repository
git clone https://github.com/Onpux/html-css-engineering-showcase.git

# Open directly
cd html-css-engineering-showcase
open index.html
```

Or serve with any static HTTP server (recommended for accurate protocol-relative links):

```bash
python3 -m http.server 8080
# Open http://localhost:8080
```

---

## License

MIT — see [LICENSE](LICENSE).
