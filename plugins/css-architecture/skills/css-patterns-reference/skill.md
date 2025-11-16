---
name: css-patterns-reference
description: Comprehensive CSS architecture patterns reference. Use when searching for ITCSS, BEM, OOCSS, SMACSS patterns or CSS organization strategies.
---

# CSS Architecture Patterns Reference

A comprehensive, searchable knowledge base for CSS architecture patterns, methodologies, and best practices.

## Table of Contents

1. [CSS Methodologies Quick Reference](#css-methodologies-quick-reference)
2. [BEM (Block Element Modifier)](#bem-block-element-modifier)
3. [ITCSS (Inverted Triangle CSS)](#itcss-inverted-triangle-css)
4. [OOCSS (Object-Oriented CSS)](#oocss-object-oriented-css)
5. [SMACSS (Scalable and Modular Architecture for CSS)](#smacss-scalable-and-modular-architecture-for-css)
6. [Atomic CSS](#atomic-css)
7. [Pattern Decision Trees](#pattern-decision-trees)
8. [Common Patterns Library](#common-patterns-library)
9. [Anti-Patterns to Avoid](#anti-patterns-to-avoid)
10. [File Structure Templates](#file-structure-templates)
11. [Naming Convention Examples](#naming-convention-examples)
12. [Code Snippets Library](#code-snippets-library)
13. [Troubleshooting Guide](#troubleshooting-guide)

---

## CSS Methodologies Quick Reference

| Methodology | Core Principle | Best For | Learning Curve | Scalability |
|-------------|---------------|----------|----------------|-------------|
| **BEM** | Component-based naming | Medium-large projects | Medium | High |
| **ITCSS** | Layered specificity management | Large-scale projects | High | Very High |
| **OOCSS** | Separation of structure and skin | Reusable components | Medium | High |
| **SMACSS** | Categorization of CSS rules | Organized codebases | Low-Medium | High |
| **Atomic CSS** | Single-purpose utility classes | Rapid prototyping | Low | Medium |
| **CSS Modules** | Scoped styles | Component frameworks | Low | High |
| **Styled Components** | CSS-in-JS | React applications | Medium | High |
| **Tailwind CSS** | Utility-first framework | Fast development | Low | Medium-High |

---

## BEM (Block Element Modifier)

### Overview

**BEM** is a component-based approach that uses a strict naming convention to create reusable, maintainable CSS.

### Naming Convention

```
.block {}
.block__element {}
.block--modifier {}
.block__element--modifier {}
```

### Core Principles

1. **Block**: Standalone entity (e.g., `.header`, `.menu`, `.button`)
2. **Element**: Part of a block (e.g., `.menu__item`, `.button__icon`)
3. **Modifier**: Variation of a block or element (e.g., `.button--primary`, `.menu__item--active`)

### Pattern Examples

#### Pattern 1: Simple Button Component

```css
/* Block */
.button {
  display: inline-block;
  padding: 12px 24px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  cursor: pointer;
}

/* Modifiers */
.button--primary {
  background-color: #007bff;
  color: white;
}

.button--secondary {
  background-color: #6c757d;
  color: white;
}

.button--large {
  padding: 16px 32px;
  font-size: 18px;
}

.button--small {
  padding: 8px 16px;
  font-size: 14px;
}

/* Element */
.button__icon {
  margin-right: 8px;
}

/* Element with Modifier */
.button__icon--right {
  margin-right: 0;
  margin-left: 8px;
}
```

**HTML Usage:**
```html
<button class="button button--primary button--large">
  <span class="button__icon">+</span>
  Add Item
</button>
```

#### Pattern 2: Card Component

```css
/* Block */
.card {
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  overflow: hidden;
}

/* Elements */
.card__header {
  padding: 20px;
  border-bottom: 1px solid #e0e0e0;
}

.card__title {
  margin: 0;
  font-size: 20px;
  font-weight: 600;
}

.card__body {
  padding: 20px;
}

.card__footer {
  padding: 20px;
  border-top: 1px solid #e0e0e0;
  background-color: #f8f9fa;
}

/* Modifiers */
.card--elevated {
  box-shadow: 0 4px 8px rgba(0,0,0,0.15);
}

.card--compact {
  .card__header,
  .card__body,
  .card__footer {
    padding: 12px;
  }
}
```

#### Pattern 3: Navigation Menu

```css
/* Block */
.nav {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
}

/* Modifiers */
.nav--vertical {
  flex-direction: column;
}

.nav--horizontal {
  flex-direction: row;
}

/* Elements */
.nav__item {
  position: relative;
}

.nav__link {
  display: block;
  padding: 12px 20px;
  color: #333;
  text-decoration: none;
  transition: background-color 0.3s;
}

.nav__link:hover {
  background-color: #f0f0f0;
}

/* Element Modifiers */
.nav__link--active {
  background-color: #007bff;
  color: white;
}

.nav__icon {
  margin-right: 8px;
  display: inline-block;
}
```

### When to Use BEM

✅ **Use BEM when:**
- Building component libraries
- Working in large teams
- Need clear component ownership
- Want self-documenting CSS
- Building scalable applications

❌ **Avoid BEM when:**
- Prototyping quickly
- Very small projects (< 5 pages)
- Using CSS-in-JS solutions
- Team prefers other methodologies

---

## ITCSS (Inverted Triangle CSS)

### Overview

**ITCSS** organizes CSS into layers based on specificity, from generic to explicit.

### The Seven Layers

| Layer | Purpose | Example | Specificity |
|-------|---------|---------|-------------|
| 1. **Settings** | Variables, config | `$color-primary: #007bff;` | None |
| 2. **Tools** | Mixins, functions | `@mixin flex-center` | None |
| 3. **Generic** | Resets, normalize | `* { box-sizing: border-box; }` | Low |
| 4. **Elements** | Base styles | `h1 { font-size: 2em; }` | Low |
| 5. **Objects** | Layout patterns | `.o-container { max-width: 1200px; }` | Low-Medium |
| 6. **Components** | UI components | `.c-button { padding: 12px; }` | Medium |
| 7. **Utilities** | Helper classes | `.u-margin-top-0 { margin-top: 0; }` | High |

### File Structure Pattern

```
styles/
├── 1-settings/
│   ├── _colors.scss
│   ├── _typography.scss
│   ├── _spacing.scss
│   └── _breakpoints.scss
├── 2-tools/
│   ├── _mixins.scss
│   ├── _functions.scss
│   └── _helpers.scss
├── 3-generic/
│   ├── _normalize.scss
│   ├── _reset.scss
│   └── _box-sizing.scss
├── 4-elements/
│   ├── _headings.scss
│   ├── _links.scss
│   ├── _forms.scss
│   └── _tables.scss
├── 5-objects/
│   ├── _layout.scss
│   ├── _grid.scss
│   ├── _media.scss
│   └── _wrapper.scss
├── 6-components/
│   ├── _buttons.scss
│   ├── _cards.scss
│   ├── _navigation.scss
│   └── _modals.scss
├── 7-utilities/
│   ├── _spacing.scss
│   ├── _text.scss
│   ├── _display.scss
│   └── _visibility.scss
└── main.scss
```

### Layer Examples

#### Layer 1: Settings

```scss
// _colors.scss
$color-primary: #007bff;
$color-secondary: #6c757d;
$color-success: #28a745;
$color-danger: #dc3545;
$color-warning: #ffc107;
$color-info: #17a2b8;

$color-text: #212529;
$color-text-muted: #6c757d;
$color-border: #dee2e6;
$color-background: #f8f9fa;

// _spacing.scss
$spacing-unit: 8px;
$spacing-xxs: $spacing-unit * 0.5;  // 4px
$spacing-xs: $spacing-unit;          // 8px
$spacing-sm: $spacing-unit * 2;      // 16px
$spacing-md: $spacing-unit * 3;      // 24px
$spacing-lg: $spacing-unit * 4;      // 32px
$spacing-xl: $spacing-unit * 6;      // 48px
$spacing-xxl: $spacing-unit * 8;     // 64px

// _breakpoints.scss
$breakpoint-xs: 320px;
$breakpoint-sm: 576px;
$breakpoint-md: 768px;
$breakpoint-lg: 992px;
$breakpoint-xl: 1200px;
$breakpoint-xxl: 1400px;
```

#### Layer 2: Tools

```scss
// _mixins.scss
@mixin flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}

@mixin responsive($breakpoint) {
  @media (min-width: $breakpoint) {
    @content;
  }
}

@mixin truncate {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

@mixin visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

// _functions.scss
@function rem($pixels) {
  @return ($pixels / 16px) * 1rem;
}

@function spacing($multiplier) {
  @return $spacing-unit * $multiplier;
}
```

#### Layer 3: Generic

```css
/* _reset.scss */
*,
*::before,
*::after {
  box-sizing: border-box;
}

* {
  margin: 0;
  padding: 0;
}

html {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}

body {
  line-height: 1.5;
}

img,
picture,
video,
canvas,
svg {
  display: block;
  max-width: 100%;
}

input,
button,
textarea,
select {
  font: inherit;
}
```

#### Layer 4: Elements

```css
/* _headings.scss */
h1, h2, h3, h4, h5, h6 {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  font-weight: 600;
  line-height: 1.2;
  color: #212529;
}

h1 { font-size: 2.5rem; margin-bottom: 1rem; }
h2 { font-size: 2rem; margin-bottom: 0.875rem; }
h3 { font-size: 1.75rem; margin-bottom: 0.75rem; }
h4 { font-size: 1.5rem; margin-bottom: 0.625rem; }
h5 { font-size: 1.25rem; margin-bottom: 0.5rem; }
h6 { font-size: 1rem; margin-bottom: 0.5rem; }

/* _links.scss */
a {
  color: #007bff;
  text-decoration: none;
  transition: color 0.2s ease;
}

a:hover {
  color: #0056b3;
  text-decoration: underline;
}

a:focus {
  outline: 2px solid #007bff;
  outline-offset: 2px;
}
```

#### Layer 5: Objects

```css
/* _layout.scss - Prefix with 'o-' for objects */
.o-container {
  width: 100%;
  max-width: 1200px;
  margin-left: auto;
  margin-right: auto;
  padding-left: 16px;
  padding-right: 16px;
}

.o-container--fluid {
  max-width: 100%;
}

/* _grid.scss */
.o-grid {
  display: grid;
  gap: 24px;
}

.o-grid--2-col {
  grid-template-columns: repeat(2, 1fr);
}

.o-grid--3-col {
  grid-template-columns: repeat(3, 1fr);
}

.o-grid--4-col {
  grid-template-columns: repeat(4, 1fr);
}

/* _media.scss */
.o-media {
  display: flex;
  align-items: flex-start;
  gap: 16px;
}

.o-media__figure {
  flex-shrink: 0;
}

.o-media__body {
  flex: 1;
}
```

#### Layer 6: Components

```css
/* _buttons.scss - Prefix with 'c-' for components */
.c-button {
  display: inline-block;
  padding: 12px 24px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  font-weight: 500;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s ease;
}

.c-button--primary {
  background-color: #007bff;
  color: white;
}

.c-button--primary:hover {
  background-color: #0056b3;
}

/* _cards.scss */
.c-card {
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  overflow: hidden;
}

.c-card__header {
  padding: 20px;
  border-bottom: 1px solid #e0e0e0;
}

.c-card__body {
  padding: 20px;
}
```

#### Layer 7: Utilities

```css
/* _spacing.scss - Prefix with 'u-' for utilities */
.u-margin-0 { margin: 0 !important; }
.u-margin-xs { margin: 8px !important; }
.u-margin-sm { margin: 16px !important; }
.u-margin-md { margin: 24px !important; }
.u-margin-lg { margin: 32px !important; }

.u-margin-top-0 { margin-top: 0 !important; }
.u-margin-right-0 { margin-right: 0 !important; }
.u-margin-bottom-0 { margin-bottom: 0 !important; }
.u-margin-left-0 { margin-left: 0 !important; }

/* _text.scss */
.u-text-center { text-align: center !important; }
.u-text-left { text-align: left !important; }
.u-text-right { text-align: right !important; }

.u-text-bold { font-weight: 700 !important; }
.u-text-normal { font-weight: 400 !important; }

.u-text-uppercase { text-transform: uppercase !important; }
.u-text-lowercase { text-transform: lowercase !important; }
.u-text-capitalize { text-transform: capitalize !important; }

/* _display.scss */
.u-display-block { display: block !important; }
.u-display-inline { display: inline !important; }
.u-display-inline-block { display: inline-block !important; }
.u-display-flex { display: flex !important; }
.u-display-grid { display: grid !important; }
.u-display-none { display: none !important; }
```

### When to Use ITCSS

✅ **Use ITCSS when:**
- Managing large-scale projects
- Need predictable specificity
- Want organized file structure
- Working with preprocessors (Sass/LESS)
- Building design systems

❌ **Avoid ITCSS when:**
- Small projects
- Using CSS-in-JS
- Prototyping rapidly
- Team unfamiliar with layered architecture

---

## OOCSS (Object-Oriented CSS)

### Overview

**OOCSS** separates structure from skin and container from content to create reusable, modular CSS.

### Two Main Principles

#### 1. Separate Structure from Skin

**Structure**: Layout properties (width, height, padding, margin)
**Skin**: Visual properties (colors, fonts, shadows)

```css
/* Bad - Mixed structure and skin */
.button-blue {
  width: 200px;
  padding: 10px;
  background: blue;
  color: white;
  border-radius: 4px;
}

.button-red {
  width: 200px;
  padding: 10px;
  background: red;
  color: white;
  border-radius: 4px;
}

/* Good - Separated structure and skin */
.button {
  /* Structure */
  width: 200px;
  padding: 10px;
  border-radius: 4px;
}

.skin-primary {
  /* Skin */
  background: blue;
  color: white;
}

.skin-danger {
  /* Skin */
  background: red;
  color: white;
}
```

#### 2. Separate Container from Content

Content should look the same regardless of container.

```css
/* Bad - Content depends on container */
.sidebar h3 {
  font-size: 18px;
  color: blue;
}

.footer h3 {
  font-size: 18px;
  color: blue;
}

/* Good - Content independent of container */
.heading-tertiary {
  font-size: 18px;
  color: blue;
}
```

### OOCSS Pattern Examples

#### Pattern 1: Media Object

```css
/* Structure */
.media {
  display: flex;
  align-items: flex-start;
}

.media-figure {
  margin-right: 16px;
  flex-shrink: 0;
}

.media-body {
  flex: 1;
}

/* Skin variations */
.media--reversed .media-figure {
  margin-right: 0;
  margin-left: 16px;
  order: 2;
}

.media--centered {
  align-items: center;
}

.media--spaced .media-figure {
  margin-right: 24px;
}
```

#### Pattern 2: Grid System

```css
/* Structure */
.grid {
  display: flex;
  flex-wrap: wrap;
  margin-left: -12px;
  margin-right: -12px;
}

.grid-item {
  padding-left: 12px;
  padding-right: 12px;
}

/* Width variations */
.grid-item--1-2 { width: 50%; }
.grid-item--1-3 { width: 33.333%; }
.grid-item--2-3 { width: 66.666%; }
.grid-item--1-4 { width: 25%; }
.grid-item--3-4 { width: 75%; }

/* Gutter variations */
.grid--narrow {
  margin-left: -6px;
  margin-right: -6px;
}

.grid--narrow .grid-item {
  padding-left: 6px;
  padding-right: 6px;
}
```

#### Pattern 3: Box Model

```css
/* Base structure */
.box {
  padding: 20px;
  border: 1px solid;
}

/* Skin variations */
.box--primary {
  background-color: #007bff;
  border-color: #0056b3;
  color: white;
}

.box--secondary {
  background-color: #6c757d;
  border-color: #545b62;
  color: white;
}

.box--light {
  background-color: #f8f9fa;
  border-color: #dee2e6;
  color: #212529;
}

/* Size variations */
.box--small { padding: 12px; }
.box--large { padding: 32px; }

/* Border variations */
.box--no-border { border: none; }
.box--rounded { border-radius: 8px; }
```

#### Pattern 4: List Patterns

```css
/* Base list structure */
.list {
  list-style: none;
  margin: 0;
  padding: 0;
}

.list-item {
  padding: 12px 0;
}

/* Layout variations */
.list--inline {
  display: flex;
}

.list--inline .list-item {
  padding: 0 12px;
}

/* Divider variations */
.list--divided .list-item {
  border-bottom: 1px solid #dee2e6;
}

.list--divided .list-item:last-child {
  border-bottom: none;
}

/* Spacing variations */
.list--compact .list-item {
  padding: 6px 0;
}

.list--spacious .list-item {
  padding: 20px 0;
}
```

### When to Use OOCSS

✅ **Use OOCSS when:**
- Building reusable component libraries
- Need flexible, composable styles
- Want to reduce CSS bloat
- Creating design systems
- Working on e-commerce sites

❌ **Avoid OOCSS when:**
- Need highly specific styling
- Very simple projects
- Using scoped CSS solutions
- Team prefers other methodologies

---

## SMACSS (Scalable and Modular Architecture for CSS)

### Overview

**SMACSS** categorizes CSS rules into five types for better organization and maintainability.

### The Five Categories

| Category | Purpose | Naming | Example |
|----------|---------|--------|---------|
| **Base** | Element defaults | Element selectors | `body { }` |
| **Layout** | Page structure | `l-` or `.layout-` | `.l-header` |
| **Module** | Reusable components | Component name | `.card` |
| **State** | Dynamic states | `is-` or `.has-` | `.is-active` |
| **Theme** | Color schemes | `theme-` | `.theme-dark` |

### Category Examples

#### 1. Base Rules

```css
/* Base rules for elements */
html {
  font-size: 16px;
  -webkit-font-smoothing: antialiased;
}

body {
  font-family: 'Helvetica Neue', Arial, sans-serif;
  line-height: 1.6;
  color: #333;
  background-color: #fff;
}

h1, h2, h3, h4, h5, h6 {
  font-weight: 600;
  line-height: 1.2;
}

a {
  color: #007bff;
  text-decoration: none;
}

a:hover {
  text-decoration: underline;
}

ul, ol {
  margin: 0;
  padding: 0;
}

img {
  max-width: 100%;
  height: auto;
}
```

#### 2. Layout Rules

```css
/* Prefix with 'l-' or 'layout-' */
.l-header {
  position: sticky;
  top: 0;
  z-index: 100;
  background: white;
  border-bottom: 1px solid #e0e0e0;
}

.l-container {
  max-width: 1200px;
  margin: 0 auto;
  padding: 0 16px;
}

.l-sidebar {
  width: 250px;
  flex-shrink: 0;
}

.l-main {
  flex: 1;
  min-width: 0;
}

.l-footer {
  margin-top: auto;
  padding: 40px 0;
  background: #f8f9fa;
}

.l-grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: 24px;
}

/* Layout variations */
.l-two-column {
  display: grid;
  grid-template-columns: 250px 1fr;
  gap: 32px;
}

.l-three-column {
  display: grid;
  grid-template-columns: 200px 1fr 200px;
  gap: 24px;
}
```

#### 3. Module Rules

```css
/* Card module */
.card {
  background: white;
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
  overflow: hidden;
}

.card-header {
  padding: 20px;
  border-bottom: 1px solid #e0e0e0;
}

.card-title {
  margin: 0;
  font-size: 20px;
  font-weight: 600;
}

.card-body {
  padding: 20px;
}

.card-footer {
  padding: 20px;
  background: #f8f9fa;
  border-top: 1px solid #e0e0e0;
}

/* Button module */
.btn {
  display: inline-block;
  padding: 12px 24px;
  border: none;
  border-radius: 4px;
  font-size: 16px;
  font-weight: 500;
  text-align: center;
  cursor: pointer;
  transition: all 0.2s;
}

.btn-primary {
  background: #007bff;
  color: white;
}

.btn-secondary {
  background: #6c757d;
  color: white;
}

.btn-icon {
  margin-right: 8px;
}

/* Navigation module */
.nav {
  display: flex;
  list-style: none;
}

.nav-item {
  position: relative;
}

.nav-link {
  display: block;
  padding: 12px 20px;
  color: #333;
  transition: background 0.2s;
}

.nav-link:hover {
  background: #f0f0f0;
}
```

#### 4. State Rules

```css
/* State rules use 'is-' or 'has-' prefix */
.is-active {
  font-weight: 700;
  color: #007bff;
}

.is-disabled {
  opacity: 0.5;
  pointer-events: none;
  cursor: not-allowed;
}

.is-hidden {
  display: none;
}

.is-visible {
  display: block;
}

.is-loading {
  position: relative;
  pointer-events: none;
}

.is-loading::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 20px;
  height: 20px;
  margin: -10px 0 0 -10px;
  border: 2px solid #007bff;
  border-top-color: transparent;
  border-radius: 50%;
  animation: spin 0.6s linear infinite;
}

.is-error {
  border-color: #dc3545;
  background-color: #f8d7da;
}

.is-success {
  border-color: #28a745;
  background-color: #d4edda;
}

.has-dropdown {
  position: relative;
}

.has-icon {
  display: flex;
  align-items: center;
  gap: 8px;
}

/* Combined with modules */
.btn.is-active {
  background-color: #0056b3;
}

.nav-link.is-active {
  background-color: #007bff;
  color: white;
}

.card.is-loading {
  opacity: 0.6;
}
```

#### 5. Theme Rules

```css
/* Default theme */
.theme-default {
  --color-primary: #007bff;
  --color-secondary: #6c757d;
  --color-background: #ffffff;
  --color-text: #212529;
  --color-border: #dee2e6;
}

/* Dark theme */
.theme-dark {
  --color-primary: #0d6efd;
  --color-secondary: #6c757d;
  --color-background: #212529;
  --color-text: #f8f9fa;
  --color-border: #495057;
}

.theme-dark .card {
  background: var(--color-background);
  color: var(--color-text);
  border-color: var(--color-border);
}

.theme-dark .btn-primary {
  background: var(--color-primary);
}

/* Brand themes */
.theme-brand-a {
  --color-primary: #e74c3c;
  --color-secondary: #95a5a6;
}

.theme-brand-b {
  --color-primary: #2ecc71;
  --color-secondary: #34495e;
}

/* High contrast theme */
.theme-high-contrast {
  --color-background: #000000;
  --color-text: #ffffff;
  --color-primary: #ffff00;
  --color-border: #ffffff;
}
```

### SMACSS File Structure

```
styles/
├── base/
│   ├── _reset.css
│   ├── _typography.css
│   └── _forms.css
├── layout/
│   ├── _header.css
│   ├── _footer.css
│   ├── _sidebar.css
│   └── _grid.css
├── modules/
│   ├── _buttons.css
│   ├── _cards.css
│   ├── _navigation.css
│   └── _modals.css
├── state/
│   └── _states.css
├── theme/
│   ├── _default.css
│   ├── _dark.css
│   └── _brand.css
└── main.css
```

### When to Use SMACSS

✅ **Use SMACSS when:**
- Need clear categorization
- Managing medium to large projects
- Want flexible theming
- Building maintainable codebases
- Team needs simple mental model

❌ **Avoid SMACSS when:**
- Very small projects
- Using component frameworks
- Prefer stricter naming conventions
- Using CSS-in-JS

---

## Atomic CSS

### Overview

**Atomic CSS** uses single-purpose utility classes that do one thing well.

### Core Principles

1. Each class does one thing
2. Classes are immutable
3. Highly composable
4. Low specificity

### Atomic CSS Patterns

#### Spacing Utilities

```css
/* Margin utilities */
.m-0 { margin: 0; }
.m-1 { margin: 4px; }
.m-2 { margin: 8px; }
.m-3 { margin: 12px; }
.m-4 { margin: 16px; }
.m-5 { margin: 20px; }
.m-6 { margin: 24px; }
.m-8 { margin: 32px; }
.m-10 { margin: 40px; }
.m-12 { margin: 48px; }

/* Directional margin */
.mt-0 { margin-top: 0; }
.mt-1 { margin-top: 4px; }
.mt-2 { margin-top: 8px; }
.mt-4 { margin-top: 16px; }

.mr-0 { margin-right: 0; }
.mr-2 { margin-right: 8px; }
.mr-4 { margin-right: 16px; }

.mb-0 { margin-bottom: 0; }
.mb-2 { margin-bottom: 8px; }
.mb-4 { margin-bottom: 16px; }

.ml-0 { margin-left: 0; }
.ml-2 { margin-left: 8px; }
.ml-4 { margin-left: 16px; }

/* Horizontal & Vertical */
.mx-auto { margin-left: auto; margin-right: auto; }
.my-0 { margin-top: 0; margin-bottom: 0; }
.my-2 { margin-top: 8px; margin-bottom: 8px; }
.my-4 { margin-top: 16px; margin-bottom: 16px; }

/* Padding utilities */
.p-0 { padding: 0; }
.p-1 { padding: 4px; }
.p-2 { padding: 8px; }
.p-3 { padding: 12px; }
.p-4 { padding: 16px; }
.p-6 { padding: 24px; }
.p-8 { padding: 32px; }

/* Directional padding */
.pt-2 { padding-top: 8px; }
.pr-2 { padding-right: 8px; }
.pb-2 { padding-bottom: 8px; }
.pl-2 { padding-left: 8px; }

.px-4 { padding-left: 16px; padding-right: 16px; }
.py-4 { padding-top: 16px; padding-bottom: 16px; }
```

#### Display & Layout Utilities

```css
/* Display */
.d-none { display: none; }
.d-block { display: block; }
.d-inline { display: inline; }
.d-inline-block { display: inline-block; }
.d-flex { display: flex; }
.d-grid { display: grid; }

/* Flexbox */
.flex-row { flex-direction: row; }
.flex-column { flex-direction: column; }
.flex-wrap { flex-wrap: wrap; }
.flex-nowrap { flex-wrap: nowrap; }

.justify-start { justify-content: flex-start; }
.justify-center { justify-content: center; }
.justify-end { justify-content: flex-end; }
.justify-between { justify-content: space-between; }
.justify-around { justify-content: space-around; }

.items-start { align-items: flex-start; }
.items-center { align-items: center; }
.items-end { align-items: flex-end; }
.items-stretch { align-items: stretch; }

.flex-1 { flex: 1; }
.flex-auto { flex: auto; }
.flex-none { flex: none; }

/* Grid */
.grid-cols-1 { grid-template-columns: repeat(1, 1fr); }
.grid-cols-2 { grid-template-columns: repeat(2, 1fr); }
.grid-cols-3 { grid-template-columns: repeat(3, 1fr); }
.grid-cols-4 { grid-template-columns: repeat(4, 1fr); }

.gap-2 { gap: 8px; }
.gap-4 { gap: 16px; }
.gap-6 { gap: 24px; }
```

#### Typography Utilities

```css
/* Font size */
.text-xs { font-size: 12px; }
.text-sm { font-size: 14px; }
.text-base { font-size: 16px; }
.text-lg { font-size: 18px; }
.text-xl { font-size: 20px; }
.text-2xl { font-size: 24px; }
.text-3xl { font-size: 30px; }
.text-4xl { font-size: 36px; }

/* Font weight */
.font-thin { font-weight: 100; }
.font-light { font-weight: 300; }
.font-normal { font-weight: 400; }
.font-medium { font-weight: 500; }
.font-semibold { font-weight: 600; }
.font-bold { font-weight: 700; }
.font-black { font-weight: 900; }

/* Text alignment */
.text-left { text-align: left; }
.text-center { text-align: center; }
.text-right { text-align: right; }
.text-justify { text-align: justify; }

/* Text transform */
.uppercase { text-transform: uppercase; }
.lowercase { text-transform: lowercase; }
.capitalize { text-transform: capitalize; }
.normal-case { text-transform: none; }

/* Text decoration */
.underline { text-decoration: underline; }
.line-through { text-decoration: line-through; }
.no-underline { text-decoration: none; }

/* Line height */
.leading-none { line-height: 1; }
.leading-tight { line-height: 1.25; }
.leading-normal { line-height: 1.5; }
.leading-relaxed { line-height: 1.75; }
.leading-loose { line-height: 2; }
```

#### Color Utilities

```css
/* Text colors */
.text-black { color: #000000; }
.text-white { color: #ffffff; }
.text-gray-100 { color: #f7fafc; }
.text-gray-500 { color: #a0aec0; }
.text-gray-900 { color: #1a202c; }

.text-primary { color: #007bff; }
.text-secondary { color: #6c757d; }
.text-success { color: #28a745; }
.text-danger { color: #dc3545; }
.text-warning { color: #ffc107; }

/* Background colors */
.bg-black { background-color: #000000; }
.bg-white { background-color: #ffffff; }
.bg-gray-100 { background-color: #f7fafc; }
.bg-gray-500 { background-color: #a0aec0; }

.bg-primary { background-color: #007bff; }
.bg-secondary { background-color: #6c757d; }
.bg-success { background-color: #28a745; }
.bg-danger { background-color: #dc3545; }

/* Border colors */
.border-gray-200 { border-color: #e2e8f0; }
.border-gray-500 { border-color: #a0aec0; }
.border-primary { border-color: #007bff; }
```

#### Border & Shadow Utilities

```css
/* Border width */
.border-0 { border-width: 0; }
.border { border-width: 1px; }
.border-2 { border-width: 2px; }
.border-4 { border-width: 4px; }

/* Border radius */
.rounded-none { border-radius: 0; }
.rounded-sm { border-radius: 2px; }
.rounded { border-radius: 4px; }
.rounded-md { border-radius: 6px; }
.rounded-lg { border-radius: 8px; }
.rounded-full { border-radius: 9999px; }

/* Box shadow */
.shadow-none { box-shadow: none; }
.shadow-sm { box-shadow: 0 1px 2px rgba(0,0,0,0.05); }
.shadow { box-shadow: 0 2px 4px rgba(0,0,0,0.1); }
.shadow-md { box-shadow: 0 4px 6px rgba(0,0,0,0.1); }
.shadow-lg { box-shadow: 0 10px 15px rgba(0,0,0,0.1); }
.shadow-xl { box-shadow: 0 20px 25px rgba(0,0,0,0.15); }
```

#### Position & Z-Index Utilities

```css
/* Position */
.static { position: static; }
.fixed { position: fixed; }
.absolute { position: absolute; }
.relative { position: relative; }
.sticky { position: sticky; }

/* Top/Right/Bottom/Left */
.top-0 { top: 0; }
.right-0 { right: 0; }
.bottom-0 { bottom: 0; }
.left-0 { left: 0; }

.inset-0 {
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
}

/* Z-index */
.z-0 { z-index: 0; }
.z-10 { z-index: 10; }
.z-20 { z-index: 20; }
.z-30 { z-index: 30; }
.z-40 { z-index: 40; }
.z-50 { z-index: 50; }
```

### Atomic CSS Usage Example

```html
<!-- Card component using atomic classes -->
<div class="bg-white rounded-lg shadow-md overflow-hidden">
  <!-- Header -->
  <div class="p-6 border-b border-gray-200">
    <h2 class="text-2xl font-bold text-gray-900 m-0">Card Title</h2>
  </div>

  <!-- Body -->
  <div class="p-6">
    <p class="text-base text-gray-700 leading-relaxed mb-4">
      This is card content with atomic utility classes.
    </p>
    <div class="d-flex justify-between items-center gap-4">
      <button class="px-4 py-2 bg-primary text-white rounded font-medium">
        Primary Action
      </button>
      <button class="px-4 py-2 bg-gray-200 text-gray-900 rounded font-medium">
        Secondary Action
      </button>
    </div>
  </div>
</div>
```

### When to Use Atomic CSS

✅ **Use Atomic CSS when:**
- Rapid prototyping
- Using frameworks like Tailwind
- Want maximum flexibility
- Prefer utility-first approach
- Building design systems

❌ **Avoid Atomic CSS when:**
- Need semantic class names
- HTML must be clean/minimal
- Team unfamiliar with utilities
- Strict separation of concerns required

---

## Pattern Decision Trees

### Decision Tree 1: Choosing a Methodology

```
START: What type of project are you building?

├─ Small website (< 10 pages)
│  └─ Use: Simple CSS or Atomic CSS
│
├─ Medium application (10-50 components)
│  ├─ Need strict naming?
│  │  └─ YES: Use BEM + SMACSS
│  │  └─ NO: Use OOCSS + Atomic utilities
│  │
│  └─ Using component framework (React/Vue)?
│      └─ YES: Use CSS Modules or Styled Components
│      └─ NO: Use BEM or SMACSS
│
├─ Large enterprise application (50+ components)
│  ├─ Building design system?
│  │  └─ YES: Use ITCSS + BEM
│  │  └─ NO: Use SMACSS + OOCSS
│  │
│  └─ Need theming?
│      └─ YES: Use SMACSS with CSS Variables
│      └─ NO: Use ITCSS + BEM
│
└─ Prototype or MVP
   └─ Use: Atomic CSS (Tailwind) or Bootstrap
```

### Decision Tree 2: Naming Convention

```
START: What should I name this style?

├─ Is it a reusable component?
│  └─ YES:
│     ├─ BEM: .component-name__element--modifier
│     ├─ SMACSS: .module-name
│     └─ OOCSS: .object-name + .skin-name
│
├─ Is it a layout container?
│  └─ YES:
│     ├─ SMACSS: .l-layout-name
│     ├─ ITCSS: .o-object-name
│     └─ Simple: .container, .wrapper, .grid
│
├─ Is it a state change?
│  └─ YES:
│     ├─ SMACSS: .is-state or .has-state
│     └─ BEM: .block--modifier
│
├─ Is it a one-off utility?
│  └─ YES:
│     ├─ ITCSS: .u-utility-name
│     ├─ Atomic: .abbreviated-property
│     └─ SMACSS: .helper-name
│
└─ Is it a theme variation?
   └─ YES:
      ├─ SMACSS: .theme-name
      └─ Use CSS Variables: --theme-property
```

### Decision Tree 3: File Organization

```
START: How should I organize my CSS files?

├─ Using preprocessor (Sass/LESS)?
│  └─ YES:
│     ├─ Large project?
│     │  └─ Use ITCSS structure (7 layers)
│     └─ Medium project?
│        └─ Use SMACSS structure (5 categories)
│
├─ Component-based framework?
│  └─ YES:
│     ├─ Colocate styles with components
│     └─ Use CSS Modules or Styled Components
│
└─ Plain CSS?
   └─ Use SMACSS structure:
      ├─ base.css
      ├─ layout.css
      ├─ modules.css
      ├─ state.css
      └─ theme.css
```

---

## Common Patterns Library

### Pattern 1: Hero Section

```css
/* BEM Approach */
.hero {
  position: relative;
  min-height: 500px;
  display: flex;
  align-items: center;
  justify-content: center;
  background-size: cover;
  background-position: center;
}

.hero__overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
}

.hero__content {
  position: relative;
  z-index: 1;
  text-align: center;
  color: white;
  max-width: 800px;
  padding: 0 20px;
}

.hero__title {
  font-size: 48px;
  font-weight: 700;
  margin-bottom: 20px;
}

.hero__subtitle {
  font-size: 24px;
  margin-bottom: 30px;
  opacity: 0.9;
}

.hero__cta {
  display: inline-block;
  padding: 16px 40px;
  background: #007bff;
  color: white;
  border-radius: 4px;
  font-size: 18px;
  font-weight: 600;
  transition: background 0.3s;
}

.hero__cta:hover {
  background: #0056b3;
}

/* Variations */
.hero--fullscreen {
  min-height: 100vh;
}

.hero--compact {
  min-height: 300px;
}
```

### Pattern 2: Responsive Navigation

```css
/* SMACSS Approach */
.nav {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 16px 20px;
  background: white;
  box-shadow: 0 2px 4px rgba(0,0,0,0.1);
}

.nav-brand {
  font-size: 24px;
  font-weight: 700;
  color: #007bff;
}

.nav-menu {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 8px;
}

.nav-item {
  position: relative;
}

.nav-link {
  display: block;
  padding: 8px 16px;
  color: #333;
  border-radius: 4px;
  transition: background 0.2s;
}

.nav-link:hover {
  background: #f0f0f0;
}

.nav-link.is-active {
  background: #007bff;
  color: white;
}

.nav-toggle {
  display: none;
  flex-direction: column;
  gap: 4px;
  background: none;
  border: none;
  cursor: pointer;
  padding: 8px;
}

.nav-toggle-bar {
  width: 24px;
  height: 3px;
  background: #333;
  border-radius: 2px;
  transition: transform 0.3s;
}

/* Mobile responsive */
@media (max-width: 768px) {
  .nav-toggle {
    display: flex;
  }

  .nav-menu {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    flex-direction: column;
    background: white;
    box-shadow: 0 4px 6px rgba(0,0,0,0.1);
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.3s;
  }

  .nav.is-open .nav-menu {
    max-height: 500px;
  }

  .nav.is-open .nav-toggle-bar:nth-child(1) {
    transform: rotate(45deg) translate(6px, 6px);
  }

  .nav.is-open .nav-toggle-bar:nth-child(2) {
    opacity: 0;
  }

  .nav.is-open .nav-toggle-bar:nth-child(3) {
    transform: rotate(-45deg) translate(6px, -6px);
  }
}
```

### Pattern 3: Modal/Dialog

```css
/* BEM + SMACSS State */
.modal {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  z-index: 1000;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 20px;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.3s;
}

.modal.is-open {
  opacity: 1;
  pointer-events: auto;
}

.modal__backdrop {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.5);
  backdrop-filter: blur(2px);
}

.modal__container {
  position: relative;
  z-index: 1;
  background: white;
  border-radius: 8px;
  box-shadow: 0 10px 25px rgba(0,0,0,0.2);
  max-width: 600px;
  width: 100%;
  max-height: 90vh;
  overflow: auto;
  transform: scale(0.9);
  transition: transform 0.3s;
}

.modal.is-open .modal__container {
  transform: scale(1);
}

.modal__header {
  display: flex;
  align-items: center;
  justify-content: space-between;
  padding: 20px 24px;
  border-bottom: 1px solid #e0e0e0;
}

.modal__title {
  margin: 0;
  font-size: 20px;
  font-weight: 600;
}

.modal__close {
  background: none;
  border: none;
  font-size: 24px;
  cursor: pointer;
  padding: 4px 8px;
  color: #666;
  transition: color 0.2s;
}

.modal__close:hover {
  color: #000;
}

.modal__body {
  padding: 24px;
}

.modal__footer {
  display: flex;
  justify-content: flex-end;
  gap: 12px;
  padding: 20px 24px;
  border-top: 1px solid #e0e0e0;
  background: #f8f9fa;
}

/* Size variations */
.modal--small .modal__container {
  max-width: 400px;
}

.modal--large .modal__container {
  max-width: 900px;
}

.modal--fullscreen .modal__container {
  max-width: 100%;
  max-height: 100%;
  border-radius: 0;
}
```

### Pattern 4: Form Layout

```css
/* OOCSS Approach */
.form {
  max-width: 600px;
}

.form-group {
  margin-bottom: 20px;
}

.form-label {
  display: block;
  margin-bottom: 8px;
  font-weight: 500;
  color: #333;
}

.form-label--required::after {
  content: '*';
  color: #dc3545;
  margin-left: 4px;
}

.form-control {
  width: 100%;
  padding: 10px 12px;
  border: 1px solid #ced4da;
  border-radius: 4px;
  font-size: 16px;
  transition: border-color 0.2s, box-shadow 0.2s;
}

.form-control:focus {
  outline: none;
  border-color: #007bff;
  box-shadow: 0 0 0 3px rgba(0,123,255,0.1);
}

.form-control.is-invalid {
  border-color: #dc3545;
}

.form-control.is-valid {
  border-color: #28a745;
}

.form-help {
  display: block;
  margin-top: 4px;
  font-size: 14px;
  color: #6c757d;
}

.form-error {
  display: block;
  margin-top: 4px;
  font-size: 14px;
  color: #dc3545;
}

.form-row {
  display: flex;
  gap: 16px;
}

.form-row .form-group {
  flex: 1;
}

.form-actions {
  display: flex;
  gap: 12px;
  justify-content: flex-end;
  margin-top: 24px;
}

/* Inline form variation */
.form--inline {
  display: flex;
  gap: 12px;
  align-items: flex-end;
}

.form--inline .form-group {
  margin-bottom: 0;
  flex: 1;
}
```

### Pattern 5: Grid Gallery

```css
/* ITCSS Object Pattern */
.o-gallery {
  display: grid;
  gap: 16px;
}

.o-gallery--2-col {
  grid-template-columns: repeat(2, 1fr);
}

.o-gallery--3-col {
  grid-template-columns: repeat(3, 1fr);
}

.o-gallery--4-col {
  grid-template-columns: repeat(4, 1fr);
}

.o-gallery--auto-fit {
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
}

.o-gallery--auto-fill {
  grid-template-columns: repeat(auto-fill, minmax(250px, 1fr));
}

/* Responsive */
@media (max-width: 1024px) {
  .o-gallery--4-col {
    grid-template-columns: repeat(3, 1fr);
  }
}

@media (max-width: 768px) {
  .o-gallery--3-col,
  .o-gallery--4-col {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (max-width: 480px) {
  .o-gallery--2-col,
  .o-gallery--3-col,
  .o-gallery--4-col {
    grid-template-columns: 1fr;
  }
}

/* Gallery item component */
.c-gallery-item {
  position: relative;
  overflow: hidden;
  border-radius: 8px;
  aspect-ratio: 1;
}

.c-gallery-item__image {
  width: 100%;
  height: 100%;
  object-fit: cover;
  transition: transform 0.3s;
}

.c-gallery-item:hover .c-gallery-item__image {
  transform: scale(1.05);
}

.c-gallery-item__overlay {
  position: absolute;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background: rgba(0, 0, 0, 0.7);
  display: flex;
  align-items: center;
  justify-content: center;
  opacity: 0;
  transition: opacity 0.3s;
}

.c-gallery-item:hover .c-gallery-item__overlay {
  opacity: 1;
}

.c-gallery-item__title {
  color: white;
  font-size: 18px;
  font-weight: 600;
  text-align: center;
  padding: 0 20px;
}
```

### Pattern 6: Breadcrumbs

```css
/* BEM Pattern */
.breadcrumb {
  display: flex;
  align-items: center;
  list-style: none;
  margin: 0;
  padding: 12px 0;
  font-size: 14px;
}

.breadcrumb__item {
  display: flex;
  align-items: center;
}

.breadcrumb__item:not(:last-child)::after {
  content: '/';
  margin: 0 8px;
  color: #6c757d;
}

.breadcrumb__link {
  color: #007bff;
  transition: color 0.2s;
}

.breadcrumb__link:hover {
  color: #0056b3;
  text-decoration: underline;
}

.breadcrumb__item.is-active {
  color: #6c757d;
}

/* Icon separator variation */
.breadcrumb--icon .breadcrumb__item:not(:last-child)::after {
  content: '›';
  font-size: 18px;
}

/* Arrow separator variation */
.breadcrumb--arrow .breadcrumb__item:not(:last-child)::after {
  content: '→';
}
```

### Pattern 7: Tabs

```css
/* Component Pattern */
.tabs {
  border-bottom: 2px solid #e0e0e0;
}

.tabs__list {
  display: flex;
  list-style: none;
  margin: 0;
  padding: 0;
  gap: 4px;
}

.tabs__item {
  position: relative;
}

.tabs__button {
  display: block;
  padding: 12px 24px;
  background: none;
  border: none;
  font-size: 16px;
  color: #6c757d;
  cursor: pointer;
  border-bottom: 2px solid transparent;
  transition: color 0.2s, border-color 0.2s;
}

.tabs__button:hover {
  color: #333;
}

.tabs__button.is-active {
  color: #007bff;
  border-bottom-color: #007bff;
}

.tabs__panel {
  display: none;
  padding: 24px 0;
}

.tabs__panel.is-active {
  display: block;
}

/* Vertical tabs variation */
.tabs--vertical {
  display: flex;
  border-bottom: none;
}

.tabs--vertical .tabs__list {
  flex-direction: column;
  border-right: 2px solid #e0e0e0;
  min-width: 200px;
}

.tabs--vertical .tabs__button {
  text-align: left;
  border-bottom: none;
  border-right: 2px solid transparent;
}

.tabs--vertical .tabs__button.is-active {
  border-bottom-color: transparent;
  border-right-color: #007bff;
}

.tabs--vertical .tabs__panel {
  flex: 1;
  padding: 0 24px;
}
```

### Pattern 8: Accordion

```css
/* Accordion Pattern */
.accordion {
  border: 1px solid #e0e0e0;
  border-radius: 8px;
  overflow: hidden;
}

.accordion__item {
  border-bottom: 1px solid #e0e0e0;
}

.accordion__item:last-child {
  border-bottom: none;
}

.accordion__header {
  width: 100%;
  padding: 16px 20px;
  background: white;
  border: none;
  text-align: left;
  font-size: 16px;
  font-weight: 500;
  cursor: pointer;
  display: flex;
  align-items: center;
  justify-content: space-between;
  transition: background 0.2s;
}

.accordion__header:hover {
  background: #f8f9fa;
}

.accordion__icon {
  transition: transform 0.3s;
}

.accordion__item.is-open .accordion__icon {
  transform: rotate(180deg);
}

.accordion__content {
  max-height: 0;
  overflow: hidden;
  transition: max-height 0.3s ease;
}

.accordion__item.is-open .accordion__content {
  max-height: 1000px;
}

.accordion__body {
  padding: 0 20px 16px;
  color: #6c757d;
  line-height: 1.6;
}

/* Allow multiple open */
.accordion--multiple .accordion__item {
  /* No special styling needed */
}
```

### Pattern 9: Alert/Notification

```css
/* Alert Pattern */
.alert {
  padding: 16px 20px;
  border-radius: 4px;
  margin-bottom: 16px;
  display: flex;
  align-items: flex-start;
  gap: 12px;
}

.alert__icon {
  flex-shrink: 0;
  font-size: 20px;
}

.alert__content {
  flex: 1;
}

.alert__title {
  margin: 0 0 4px 0;
  font-weight: 600;
  font-size: 16px;
}

.alert__message {
  margin: 0;
  font-size: 14px;
}

.alert__close {
  flex-shrink: 0;
  background: none;
  border: none;
  font-size: 20px;
  cursor: pointer;
  opacity: 0.6;
  transition: opacity 0.2s;
}

.alert__close:hover {
  opacity: 1;
}

/* Type variations */
.alert--info {
  background: #d1ecf1;
  color: #0c5460;
  border-left: 4px solid #17a2b8;
}

.alert--success {
  background: #d4edda;
  color: #155724;
  border-left: 4px solid #28a745;
}

.alert--warning {
  background: #fff3cd;
  color: #856404;
  border-left: 4px solid #ffc107;
}

.alert--error {
  background: #f8d7da;
  color: #721c24;
  border-left: 4px solid #dc3545;
}
```

### Pattern 10: Tooltip

```css
/* Tooltip Pattern */
.tooltip {
  position: relative;
  display: inline-block;
}

.tooltip__trigger {
  border-bottom: 1px dotted #999;
  cursor: help;
}

.tooltip__content {
  position: absolute;
  bottom: 100%;
  left: 50%;
  transform: translateX(-50%);
  margin-bottom: 8px;
  padding: 8px 12px;
  background: #333;
  color: white;
  font-size: 14px;
  border-radius: 4px;
  white-space: nowrap;
  opacity: 0;
  pointer-events: none;
  transition: opacity 0.2s;
  z-index: 1000;
}

.tooltip__content::after {
  content: '';
  position: absolute;
  top: 100%;
  left: 50%;
  transform: translateX(-50%);
  border: 6px solid transparent;
  border-top-color: #333;
}

.tooltip:hover .tooltip__content,
.tooltip__trigger:focus + .tooltip__content {
  opacity: 1;
}

/* Position variations */
.tooltip--top .tooltip__content {
  bottom: 100%;
  margin-bottom: 8px;
}

.tooltip--bottom .tooltip__content {
  top: 100%;
  bottom: auto;
  margin-top: 8px;
}

.tooltip--bottom .tooltip__content::after {
  top: auto;
  bottom: 100%;
  border-top-color: transparent;
  border-bottom-color: #333;
}

.tooltip--right .tooltip__content {
  left: 100%;
  bottom: auto;
  top: 50%;
  transform: translateY(-50%);
  margin-left: 8px;
}

.tooltip--left .tooltip__content {
  right: 100%;
  left: auto;
  bottom: auto;
  top: 50%;
  transform: translateY(-50%);
  margin-right: 8px;
}
```

---

## Anti-Patterns to Avoid

### Anti-Pattern 1: Overly Specific Selectors

❌ **Bad:**
```css
body div.container div.content article.post div.post-content p.text {
  color: #333;
}
```

✅ **Good:**
```css
.post__text {
  color: #333;
}
```

**Why:** High specificity makes styles hard to override and maintain.

---

### Anti-Pattern 2: Magic Numbers

❌ **Bad:**
```css
.element {
  margin-top: 23px;
  padding: 17px;
  left: -3px;
}
```

✅ **Good:**
```css
.element {
  margin-top: var(--spacing-md);
  padding: var(--spacing-base);
  left: 0;
}
```

**Why:** Magic numbers are hard to maintain and don't follow a system.

---

### Anti-Pattern 3: !important Overuse

❌ **Bad:**
```css
.button {
  background: blue !important;
  color: white !important;
  padding: 10px !important;
}
```

✅ **Good:**
```css
.button {
  background: blue;
  color: white;
  padding: 10px;
}

/* If you must override, increase specificity properly */
.header .button {
  background: red;
}
```

**Why:** !important breaks the cascade and makes debugging difficult.

---

### Anti-Pattern 4: Location-Dependent Styling

❌ **Bad:**
```css
.sidebar h2 {
  font-size: 18px;
  color: blue;
}

.footer h2 {
  font-size: 18px;
  color: blue;
}
```

✅ **Good:**
```css
.heading-secondary {
  font-size: 18px;
  color: blue;
}
```

**Why:** Content should be styled independently of location.

---

### Anti-Pattern 5: Undoing Styles

❌ **Bad:**
```css
.list {
  margin: 20px;
  padding: 20px;
  border: 1px solid black;
}

.list--special {
  margin: 0;
  padding: 0;
  border: none;
}
```

✅ **Good:**
```css
.list {
  /* No default styling */
}

.list--default {
  margin: 20px;
  padding: 20px;
  border: 1px solid black;
}

.list--special {
  /* Different styling */
}
```

**Why:** Undoing styles creates unnecessary code and conflicts.

---

### Anti-Pattern 6: Overly Generic Class Names

❌ **Bad:**
```css
.left { float: left; }
.right { float: right; }
.bold { font-weight: bold; }
.big { font-size: 20px; }
```

✅ **Good:**
```css
.pull-left { float: left; }
.pull-right { float: right; }
.font-weight-bold { font-weight: bold; }
.text-lg { font-size: 20px; }
```

**Why:** Generic names can conflict and aren't searchable.

---

### Anti-Pattern 7: Non-Responsive Units

❌ **Bad:**
```css
.container {
  width: 1000px;
  font-size: 14px;
  padding: 25px;
}
```

✅ **Good:**
```css
.container {
  max-width: 1000px;
  font-size: clamp(14px, 1rem, 18px);
  padding: clamp(16px, 2vw, 32px);
}
```

**Why:** Fixed units don't adapt to different screen sizes.

---

### Anti-Pattern 8: Inline Styles in Production

❌ **Bad:**
```html
<div style="color: red; margin: 20px; padding: 10px;">
  Content
</div>
```

✅ **Good:**
```html
<div class="alert alert--error">
  Content
</div>
```

**Why:** Inline styles can't be reused and are hard to maintain.

---

### Anti-Pattern 9: Inconsistent Naming

❌ **Bad:**
```css
.btn-primary { }
.buttonSecondary { }
.Button--tertiary { }
.BUTTON_QUATERNARY { }
```

✅ **Good:**
```css
.btn-primary { }
.btn-secondary { }
.btn-tertiary { }
.btn-quaternary { }
```

**Why:** Consistency makes code easier to read and search.

---

### Anti-Pattern 10: Deep Nesting (Preprocessors)

❌ **Bad:**
```scss
.header {
  .nav {
    .menu {
      .item {
        .link {
          color: blue;

          &:hover {
            color: red;
          }
        }
      }
    }
  }
}
```

✅ **Good:**
```scss
.nav-link {
  color: blue;

  &:hover {
    color: red;
  }
}
```

**Why:** Deep nesting creates overly specific selectors.

---

## File Structure Templates

### Template 1: ITCSS Structure

```
styles/
├── settings/
│   ├── _variables.scss
│   ├── _colors.scss
│   ├── _typography.scss
│   ├── _spacing.scss
│   └── _breakpoints.scss
├── tools/
│   ├── _mixins.scss
│   ├── _functions.scss
│   └── _placeholders.scss
├── generic/
│   ├── _normalize.scss
│   ├── _reset.scss
│   └── _box-sizing.scss
├── elements/
│   ├── _page.scss
│   ├── _headings.scss
│   ├── _links.scss
│   ├── _forms.scss
│   ├── _tables.scss
│   └── _images.scss
├── objects/
│   ├── _container.scss
│   ├── _layout.scss
│   ├── _grid.scss
│   ├── _media.scss
│   └── _wrapper.scss
├── components/
│   ├── _buttons.scss
│   ├── _cards.scss
│   ├── _navigation.scss
│   ├── _header.scss
│   ├── _footer.scss
│   ├── _forms.scss
│   ├── _modals.scss
│   ├── _tabs.scss
│   └── _alerts.scss
├── utilities/
│   ├── _spacing.scss
│   ├── _text.scss
│   ├── _display.scss
│   ├── _colors.scss
│   └── _visibility.scss
└── main.scss
```

**main.scss:**
```scss
// Settings
@import 'settings/variables';
@import 'settings/colors';
@import 'settings/typography';
@import 'settings/spacing';
@import 'settings/breakpoints';

// Tools
@import 'tools/functions';
@import 'tools/mixins';
@import 'tools/placeholders';

// Generic
@import 'generic/normalize';
@import 'generic/reset';
@import 'generic/box-sizing';

// Elements
@import 'elements/page';
@import 'elements/headings';
@import 'elements/links';
@import 'elements/forms';
@import 'elements/tables';
@import 'elements/images';

// Objects
@import 'objects/container';
@import 'objects/layout';
@import 'objects/grid';
@import 'objects/media';
@import 'objects/wrapper';

// Components
@import 'components/buttons';
@import 'components/cards';
@import 'components/navigation';
@import 'components/header';
@import 'components/footer';
@import 'components/forms';
@import 'components/modals';
@import 'components/tabs';
@import 'components/alerts';

// Utilities
@import 'utilities/spacing';
@import 'utilities/text';
@import 'utilities/display';
@import 'utilities/colors';
@import 'utilities/visibility';
```

---

### Template 2: SMACSS Structure

```
styles/
├── base/
│   ├── _reset.css
│   ├── _typography.css
│   ├── _forms.css
│   └── _tables.css
├── layout/
│   ├── _header.css
│   ├── _footer.css
│   ├── _sidebar.css
│   ├── _grid.css
│   └── _container.css
├── modules/
│   ├── _buttons.css
│   ├── _cards.css
│   ├── _navigation.css
│   ├── _modals.css
│   ├── _tabs.css
│   ├── _alerts.css
│   └── _forms.css
├── state/
│   └── _states.css
├── theme/
│   ├── _default.css
│   ├── _dark.css
│   └── _brand.css
└── main.css
```

---

### Template 3: Component-Based Structure

```
src/
├── components/
│   ├── Button/
│   │   ├── Button.jsx
│   │   ├── Button.module.css
│   │   └── Button.test.js
│   ├── Card/
│   │   ├── Card.jsx
│   │   ├── Card.module.css
│   │   └── Card.test.js
│   └── Navigation/
│       ├── Navigation.jsx
│       ├── Navigation.module.css
│       └── Navigation.test.js
├── styles/
│   ├── global.css
│   ├── variables.css
│   ├── utilities.css
│   └── themes/
│       ├── default.css
│       └── dark.css
└── App.jsx
```

---

## Naming Convention Examples

### BEM Examples

```css
/* Block */
.product { }

/* Elements */
.product__image { }
.product__title { }
.product__price { }
.product__description { }
.product__button { }

/* Modifiers */
.product--featured { }
.product--on-sale { }
.product--out-of-stock { }

/* Element Modifiers */
.product__button--large { }
.product__button--disabled { }
.product__price--discounted { }

/* Complex component */
.search-form { }
.search-form__input { }
.search-form__button { }
.search-form__suggestions { }
.search-form__suggestion-item { }
.search-form__suggestion-item--active { }
```

### SMACSS Examples

```css
/* Base */
body { }
h1 { }
a { }

/* Layout */
.l-header { }
.l-container { }
.l-sidebar { }
.l-main-content { }

/* Module */
.card { }
.btn { }
.nav { }
.dropdown { }

/* State */
.is-active { }
.is-hidden { }
.is-loading { }
.is-error { }
.has-dropdown { }
.has-icon { }

/* Theme */
.theme-dark { }
.theme-light { }
.theme-brand { }
```

### OOCSS Examples

```css
/* Structure */
.box { }
.media { }
.grid { }

/* Skin */
.skin-primary { }
.skin-secondary { }
.skin-bordered { }

/* Combined */
<div class="box skin-primary">...</div>
<div class="media skin-bordered">...</div>
```

### ITCSS Examples

```css
/* Objects (prefix: o-) */
.o-container { }
.o-layout { }
.o-media { }
.o-grid { }

/* Components (prefix: c-) */
.c-button { }
.c-card { }
.c-navigation { }
.c-modal { }

/* Utilities (prefix: u-) */
.u-margin-top-0 { }
.u-text-center { }
.u-display-flex { }
.u-hidden { }
```

---

## Code Snippets Library

### Snippet 1: Flexbox Centering

```css
.flex-center {
  display: flex;
  justify-content: center;
  align-items: center;
}
```

### Snippet 2: Responsive Container

```css
.container {
  width: 100%;
  max-width: 1200px;
  margin-left: auto;
  margin-right: auto;
  padding-left: 16px;
  padding-right: 16px;
}

@media (min-width: 768px) {
  .container {
    padding-left: 24px;
    padding-right: 24px;
  }
}
```

### Snippet 3: Aspect Ratio Box

```css
.aspect-ratio-box {
  position: relative;
  width: 100%;
  padding-bottom: 56.25%; /* 16:9 */
}

.aspect-ratio-box__content {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
```

### Snippet 4: Truncate Text

```css
.truncate {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

.line-clamp-2 {
  display: -webkit-box;
  -webkit-line-clamp: 2;
  -webkit-box-orient: vertical;
  overflow: hidden;
}
```

### Snippet 5: Screen Reader Only

```css
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}
```

### Snippet 6: Custom Scrollbar

```css
.custom-scrollbar::-webkit-scrollbar {
  width: 8px;
}

.custom-scrollbar::-webkit-scrollbar-track {
  background: #f1f1f1;
}

.custom-scrollbar::-webkit-scrollbar-thumb {
  background: #888;
  border-radius: 4px;
}

.custom-scrollbar::-webkit-scrollbar-thumb:hover {
  background: #555;
}
```

### Snippet 7: Focus Visible

```css
.focus-visible:focus {
  outline: 2px solid #007bff;
  outline-offset: 2px;
}

.focus-visible:focus:not(:focus-visible) {
  outline: none;
}
```

### Snippet 8: Responsive Typography

```css
.responsive-text {
  font-size: clamp(1rem, 2vw + 0.5rem, 2rem);
}
```

### Snippet 9: Glass Morphism

```css
.glass {
  background: rgba(255, 255, 255, 0.1);
  backdrop-filter: blur(10px);
  border: 1px solid rgba(255, 255, 255, 0.2);
}
```

### Snippet 10: Smooth Scroll

```css
html {
  scroll-behavior: smooth;
}

@media (prefers-reduced-motion: reduce) {
  html {
    scroll-behavior: auto;
  }
}
```

---

## Troubleshooting Guide

### Issue 1: Styles Not Applying

**Symptoms:**
- CSS rules defined but not visible
- Changes don't appear in browser

**Solutions:**
1. Check selector specificity
2. Verify CSS file is linked correctly
3. Clear browser cache
4. Check for typos in class names
5. Inspect element in DevTools
6. Check if styles are overridden
7. Verify CSS is not minified incorrectly

```css
/* Check specificity */
/* Low specificity */
.button { color: blue; }

/* Higher specificity wins */
.header .button { color: red; }
```

---

### Issue 2: Specificity Wars

**Symptoms:**
- Need !important to override styles
- Styles unpredictable

**Solutions:**
1. Follow specificity hierarchy
2. Use BEM methodology
3. Avoid ID selectors
4. Keep selectors flat
5. Use CSS layers (new)

```css
/* Bad - specificity war */
#header .nav ul li a { }

/* Good - flat BEM selector */
.nav__link { }
```

---

### Issue 3: Layout Breaking on Mobile

**Symptoms:**
- Horizontal scrolling
- Elements overflow
- Text too small/large

**Solutions:**
1. Use responsive units (%, rem, vw)
2. Add viewport meta tag
3. Test with mobile DevTools
4. Use media queries
5. Apply mobile-first approach

```css
/* Mobile first */
.container {
  width: 100%;
  padding: 16px;
}

@media (min-width: 768px) {
  .container {
    max-width: 1200px;
    margin: 0 auto;
  }
}
```

---

### Issue 4: Vertical Centering Not Working

**Symptoms:**
- vertical-align doesn't work
- Margin auto doesn't center

**Solutions:**
1. Use flexbox
2. Use grid
3. Use position absolute
4. Ensure parent has height

```css
/* Flexbox solution */
.parent {
  display: flex;
  align-items: center;
  justify-content: center;
  min-height: 100vh;
}

/* Grid solution */
.parent {
  display: grid;
  place-items: center;
  min-height: 100vh;
}
```

---

### Issue 5: z-index Not Working

**Symptoms:**
- Element hidden behind others
- z-index seems ignored

**Solutions:**
1. Ensure position is set (not static)
2. Check stacking context
3. Verify parent z-index
4. Use consistent z-index scale

```css
/* Won't work */
.element {
  z-index: 999;
}

/* Will work */
.element {
  position: relative;
  z-index: 999;
}
```

---

### Issue 6: Flexbox Gap Not Working

**Symptoms:**
- Gap property ignored
- Spaces between items missing

**Solutions:**
1. Check browser support
2. Use margin as fallback
3. Update browser
4. Use spacer elements

```css
/* Modern approach */
.flex-container {
  display: flex;
  gap: 16px;
}

/* Fallback */
.flex-container > * + * {
  margin-left: 16px;
}
```

---

### Issue 7: CSS Variables Not Working

**Symptoms:**
- var() returns nothing
- Colors/values not applied

**Solutions:**
1. Check browser support
2. Ensure proper syntax
3. Define in :root
4. Provide fallback

```css
/* Proper usage */
:root {
  --primary-color: #007bff;
}

.element {
  color: var(--primary-color, blue); /* with fallback */
}
```

---

### Issue 8: Transitions Jumpy/Not Smooth

**Symptoms:**
- Animation stutters
- Transition doesn't work

**Solutions:**
1. Use transform instead of position
2. Add will-change hint
3. Use hardware acceleration
4. Optimize transition properties

```css
/* Performant transitions */
.element {
  transform: translateX(0);
  transition: transform 0.3s ease;
  will-change: transform;
}

.element:hover {
  transform: translateX(10px);
}
```

---

### Issue 9: Grid Items Not Sizing Correctly

**Symptoms:**
- Grid items overflow
- Uneven column widths

**Solutions:**
1. Use minmax()
2. Set grid-auto-rows
3. Use fr units correctly
4. Check min-content/max-content

```css
/* Responsive grid */
.grid {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 16px;
}
```

---

### Issue 10: Hover Effects Not Working on Touch

**Symptoms:**
- Hover stuck on mobile
- Touch doesn't trigger properly

**Solutions:**
1. Use :active for touch
2. Add @media hover query
3. Use JavaScript for complex interactions
4. Avoid :hover-only UI

```css
/* Touch-friendly */
.button {
  background: blue;
}

@media (hover: hover) {
  .button:hover {
    background: darkblue;
  }
}

.button:active {
  background: navy;
}
```

---

## Quick Reference Cheat Sheet

### BEM Naming Pattern
```
.block {}
.block__element {}
.block--modifier {}
.block__element--modifier {}
```

### ITCSS Layers (Specificity Order)
```
1. Settings (variables)
2. Tools (mixins)
3. Generic (reset)
4. Elements (h1, a)
5. Objects (.o-container)
6. Components (.c-button)
7. Utilities (.u-mt-0)
```

### SMACSS Categories
```
Base: element selectors
Layout: .l-header
Module: .card
State: .is-active
Theme: .theme-dark
```

### Common Responsive Breakpoints
```
xs: 320px
sm: 576px
md: 768px
lg: 992px
xl: 1200px
xxl: 1400px
```

---

**End of CSS Patterns Reference**

This comprehensive reference contains 50+ searchable patterns, methodologies, and solutions for CSS architecture. Use the table of contents to navigate to specific sections, or search for keywords to find relevant patterns and examples.
