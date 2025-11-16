---
name: container-query-patterns
description: Comprehensive container query patterns library. Use when searching for responsive component patterns, container query syntax, or modern CSS responsive design techniques.
---

# Container Query Patterns Library

A comprehensive searchable reference for CSS Container Queries, container units, and modern component-based responsive design patterns.

## Table of Contents

1. [Container Query Syntax Reference](#container-query-syntax-reference)
2. [Container Units Quick Reference](#container-units-quick-reference)
3. [Common Responsive Patterns](#common-responsive-patterns)
4. [Component Recipes](#component-recipes)
5. [Layout Patterns](#layout-patterns)
6. [Performance Patterns](#performance-patterns)
7. [Fallback Strategies](#fallback-strategies)
8. [Troubleshooting Guide](#troubleshooting-guide)

---

## Container Query Syntax Reference

### Basic Container Setup

| Pattern | Syntax | Use Case |
|---------|--------|----------|
| **Inline Size** | `container-type: inline-size;` | Most common - width-based queries |
| **Block Size** | `container-type: block-size;` | Height-based queries (rare) |
| **Size** | `container-type: size;` | Width AND height queries |
| **Normal** | `container-type: normal;` | No containment (default) |
| **Named Container** | `container-name: sidebar;` | Target specific containers |
| **Shorthand** | `container: sidebar / inline-size;` | Name + type together |

### Query Syntax Patterns

```css
/* Basic width queries */
@container (min-width: 400px) { }
@container (max-width: 600px) { }
@container (width >= 400px) { } /* Modern syntax */
@container (width < 600px) { }

/* Range queries */
@container (min-width: 400px) and (max-width: 800px) { }
@container (400px <= width <= 800px) { } /* Modern range */

/* Named container queries */
@container sidebar (min-width: 300px) { }
@container card-container (width > 500px) { }

/* Orientation queries */
@container (orientation: portrait) { }
@container (orientation: landscape) { }

/* Aspect ratio queries */
@container (aspect-ratio > 16/9) { }
@container (aspect-ratio: 1/1) { } /* Square */

/* Height queries (with size or block-size) */
@container (min-height: 400px) { }
@container (height > 600px) { }
```

---

## Container Units Quick Reference

| Unit | Description | Example | Use Case |
|------|-------------|---------|----------|
| **cqw** | 1% of container width | `width: 50cqw;` | Horizontal sizing |
| **cqh** | 1% of container height | `height: 30cqh;` | Vertical sizing |
| **cqi** | 1% of container inline size | `font-size: 5cqi;` | Inline dimension (width in LTR) |
| **cqb** | 1% of container block size | `padding-block: 2cqb;` | Block dimension (height in LTR) |
| **cqmin** | 1% of smaller dimension | `padding: 2cqmin;` | Uniform spacing |
| **cqmax** | 1% of larger dimension | `margin: 1cqmax;` | Scale with larger axis |

### Practical Unit Examples

```css
/* Responsive typography */
.title {
  font-size: clamp(1rem, 5cqi, 3rem);
}

/* Responsive spacing */
.card {
  padding: clamp(0.5rem, 3cqi, 2rem);
  gap: max(0.5rem, 2cqi);
}

/* Responsive grid */
.grid {
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 25cqi), 1fr));
}

/* Responsive border radius */
.element {
  border-radius: clamp(0.25rem, 1cqi, 1rem);
}
```

---

## Common Responsive Patterns

### Pattern 1: Card Layout Transformation

**Use Case**: Card that changes from vertical stack to horizontal layout to overlay based on container width.

```css
.card-container {
  container-type: inline-size;
  container-name: card;
}

/* Mobile: Vertical stack (< 400px) */
@container card (max-width: 399px) {
  .card {
    display: flex;
    flex-direction: column;
  }

  .card__image {
    width: 100%;
    aspect-ratio: 16/9;
  }

  .card__content {
    padding: 1rem;
  }
}

/* Tablet: Horizontal layout (400px - 699px) */
@container card (min-width: 400px) and (max-width: 699px) {
  .card {
    display: grid;
    grid-template-columns: 200px 1fr;
  }

  .card__image {
    height: 100%;
    object-fit: cover;
  }

  .card__content {
    padding: 1.5rem;
  }
}

/* Desktop: Overlay layout (≥ 700px) */
@container card (min-width: 700px) {
  .card {
    position: relative;
    min-height: 400px;
  }

  .card__image {
    position: absolute;
    inset: 0;
    width: 100%;
    height: 100%;
    object-fit: cover;
  }

  .card__content {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 2rem;
    background: linear-gradient(to top, rgba(0,0,0,0.9), transparent);
    color: white;
  }
}
```

### Pattern 2: Navigation Toggle

**Use Case**: Navigation that switches from hamburger menu to full horizontal menu.

```css
.nav-container {
  container-type: inline-size;
}

/* Compact: Hamburger menu */
@container (max-width: 600px) {
  .nav__toggle {
    display: block;
  }

  .nav__list {
    position: absolute;
    top: 100%;
    left: 0;
    right: 0;
    background: white;
    max-height: 0;
    overflow: hidden;
    transition: max-height 0.3s;
  }

  .nav__list.open {
    max-height: 500px;
  }

  .nav__item {
    display: block;
    padding: 1rem;
    border-bottom: 1px solid #e5e7eb;
  }
}

/* Full: Horizontal menu */
@container (min-width: 601px) {
  .nav__toggle {
    display: none;
  }

  .nav__list {
    display: flex;
    gap: 1rem;
  }

  .nav__item {
    padding: 0.5rem 1rem;
  }
}
```

### Pattern 3: Responsive Grid

**Use Case**: Grid that adjusts column count based on container width.

```css
.grid-container {
  container-type: inline-size;
}

/* Auto-responsive grid */
.grid {
  display: grid;
  gap: 1rem;
}

@container (max-width: 499px) {
  .grid {
    grid-template-columns: 1fr;
  }
}

@container (min-width: 500px) and (max-width: 799px) {
  .grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@container (min-width: 800px) and (max-width: 1099px) {
  .grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

@container (min-width: 1100px) {
  .grid {
    grid-template-columns: repeat(4, 1fr);
  }
}

/* Alternative: CSS-only auto-responsive */
.grid-auto {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(100%, 250px), 1fr));
  gap: 1rem;
}
```

### Pattern 4: Responsive Typography

**Use Case**: Text size scales with container size using container units.

```css
.text-container {
  container-type: inline-size;
}

.heading {
  font-size: clamp(1.5rem, 5cqi, 3rem);
  line-height: calc(1.2 + 0.1cqi);
}

.body-text {
  font-size: clamp(0.875rem, 2cqi + 0.5rem, 1.125rem);
  line-height: calc(1.5 + 0.1cqi);
}

.caption {
  font-size: clamp(0.75rem, 1.5cqi, 0.9375rem);
}
```

### Pattern 5: Responsive Table

**Use Case**: Table that converts to card-based layout on small containers.

```css
.table-container {
  container-type: inline-size;
}

/* Mobile: Card layout */
@container (max-width: 600px) {
  table {
    display: block;
  }

  thead {
    display: none;
  }

  tbody, tr, td {
    display: block;
  }

  tr {
    margin-bottom: 1rem;
    border: 1px solid #e5e7eb;
    border-radius: 0.5rem;
    padding: 1rem;
  }

  td {
    position: relative;
    padding: 0.5rem 0 0.5rem 50%;
  }

  td::before {
    content: attr(data-label);
    position: absolute;
    left: 0;
    width: 45%;
    font-weight: 600;
  }
}

/* Desktop: Standard table */
@container (min-width: 601px) {
  table {
    width: 100%;
    border-collapse: collapse;
  }

  th, td {
    padding: 0.75rem;
    text-align: left;
    border-bottom: 1px solid #e5e7eb;
  }

  thead {
    background: #f9fafb;
  }
}
```

---

## Component Recipes

### Recipe 1: Responsive Sidebar Layout

```css
.layout {
  container-type: inline-size;
  display: grid;
}

@container (max-width: 768px) {
  .layout {
    grid-template-columns: 1fr;
  }

  .sidebar {
    order: 2;
  }

  .main {
    order: 1;
  }
}

@container (min-width: 769px) {
  .layout {
    grid-template-columns: 300px 1fr;
  }
}

@container (min-width: 1200px) {
  .layout {
    grid-template-columns: 350px 1fr 250px;
  }
}
```

### Recipe 2: Feature Card with Icon Position

```css
.feature-card-container {
  container-type: inline-size;
}

@container (max-width: 350px) {
  .feature {
    text-align: center;
  }

  .feature__icon {
    margin: 0 auto 1rem;
    width: 48px;
    height: 48px;
  }

  .feature__title {
    font-size: 1rem;
  }
}

@container (min-width: 351px) {
  .feature {
    display: flex;
    gap: 1rem;
    text-align: left;
  }

  .feature__icon {
    flex-shrink: 0;
    width: 64px;
    height: 64px;
  }

  .feature__title {
    font-size: 1.25rem;
  }
}
```

### Recipe 3: Product Card with Dynamic Actions

```css
.product-container {
  container-type: inline-size;
}

/* Compact: Stacked actions */
@container (max-width: 280px) {
  .product__actions {
    display: flex;
    flex-direction: column;
    gap: 0.5rem;
  }

  .product__button {
    width: 100%;
    font-size: 0.875rem;
  }
}

/* Medium: Horizontal actions */
@container (min-width: 281px) and (max-width: 400px) {
  .product__actions {
    display: flex;
    gap: 0.5rem;
  }

  .product__button {
    flex: 1;
    font-size: 0.9375rem;
  }
}

/* Large: Full layout with icons */
@container (min-width: 401px) {
  .product__actions {
    display: grid;
    grid-template-columns: 1fr auto auto;
    gap: 1rem;
  }

  .product__button {
    padding: 0.75rem 1.5rem;
    font-size: 1rem;
  }

  .product__button::before {
    content: attr(data-icon);
    margin-right: 0.5rem;
  }
}
```

---

## Layout Patterns

### Pattern 1: Holy Grail Layout

```css
.holy-grail {
  container-type: inline-size;
  display: grid;
  min-height: 100vh;
}

@container (max-width: 768px) {
  .holy-grail {
    grid-template-areas:
      "header"
      "main"
      "left"
      "right"
      "footer";
    grid-template-columns: 1fr;
  }
}

@container (min-width: 769px) {
  .holy-grail {
    grid-template-areas:
      "header header header"
      "left main right"
      "footer footer footer";
    grid-template-columns: 200px 1fr 200px;
    grid-template-rows: auto 1fr auto;
  }
}

@container (min-width: 1200px) {
  .holy-grail {
    grid-template-columns: 250px 1fr 300px;
  }
}
```

### Pattern 2: Pancake Stack

```css
.pancake {
  container-type: inline-size;
  display: grid;
}

@container (max-width: 600px) {
  .pancake {
    grid-template-columns: 1fr;
  }
}

@container (min-width: 601px) {
  .pancake {
    grid-template-columns: minmax(150px, 25%) 1fr;
  }
}

@container (min-width: 1000px) {
  .pancake {
    grid-template-columns: minmax(200px, 20%) 1fr minmax(200px, 20%);
  }
}
```

### Pattern 3: RAM Grid (Repeat Auto Minmax)

```css
.ram-grid-container {
  container-type: inline-size;
}

.ram-grid {
  display: grid;
  gap: 1rem;
}

@container (max-width: 500px) {
  .ram-grid {
    grid-template-columns: repeat(auto-fit, minmax(min(100%, 150px), 1fr));
  }
}

@container (min-width: 501px) {
  .ram-grid {
    grid-template-columns: repeat(auto-fit, minmax(min(100%, 250px), 1fr));
  }
}

@container (min-width: 1000px) {
  .ram-grid {
    grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
  }
}
```

---

## Performance Patterns

### Pattern 1: Efficient Container Setup

```css
/* ✅ Good: Minimal containment */
.efficient-container {
  container-type: inline-size; /* Only inline dimension */
  contain: layout style; /* Explicit containment */
}

/* ❌ Avoid: Over-containment */
.inefficient-container {
  container-type: size; /* Both dimensions - more expensive */
  contain: strict; /* Too restrictive */
}
```

### Pattern 2: Batched Queries

```css
/* ✅ Good: Group related changes */
@container (min-width: 400px) {
  .card,
  .card__header,
  .card__body {
    /* Apply changes together */
    padding: 1.5rem;
  }
}

/* ❌ Avoid: Repeated queries */
@container (min-width: 400px) {
  .card { padding: 1.5rem; }
}
@container (min-width: 400px) {
  .card__header { padding: 1.5rem; }
}
@container (min-width: 400px) {
  .card__body { padding: 1.5rem; }
}
```

### Pattern 3: CSS Custom Properties for Container Units

```css
/* ✅ Good: Cache container unit calculations */
.container {
  container-type: inline-size;
  --container-padding: clamp(1rem, 3cqi, 3rem);
  --container-gap: max(0.5rem, 2cqi);
}

.content {
  padding: var(--container-padding);
  gap: var(--container-gap);
}

/* ❌ Avoid: Repeated calculations */
.content {
  padding: clamp(1rem, 3cqi, 3rem);
  gap: max(0.5rem, 2cqi);
}

.other-content {
  padding: clamp(1rem, 3cqi, 3rem); /* Recalculated */
}
```

---

## Fallback Strategies

### Strategy 1: Progressive Enhancement

```css
/* Base styles (all browsers) */
.component {
  padding: 1rem;
  font-size: 1rem;
}

/* Container queries (modern browsers) */
@supports (container-type: inline-size) {
  .component-wrapper {
    container-type: inline-size;
  }

  @container (min-width: 400px) {
    .component {
      padding: 2rem;
      font-size: 1.25rem;
    }
  }
}
```

### Strategy 2: Media Query Fallback

```css
/* Fallback: Media queries */
@media (min-width: 768px) {
  .card {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
}

/* Enhancement: Container queries */
@supports (container-type: inline-size) {
  .card-container {
    container-type: inline-size;
  }

  @container (min-width: 400px) {
    .card {
      display: grid;
      grid-template-columns: 200px 1fr;
    }
  }
}
```

### Strategy 3: PostCSS Plugin Polyfill

```css
/* Original code with container queries */
.card-wrapper {
  container-type: inline-size;
}

@container (min-width: 30em) {
  .card {
    display: grid;
  }
}

/* PostCSS transpiles to fallback */
.card-wrapper {
  container-type: inline-size;
}

.card-wrapper[data-cq="30em"] .card {
  display: grid;
}
```

---

## Troubleshooting Guide

### Issue 1: Container Queries Not Working

**Symptoms**: Styles not applying when container resizes.

**Solutions**:
1. ✅ Check `container-type` is set on parent
2. ✅ Verify browser support (Chrome 105+, Safari 16+)
3. ✅ Ensure queries target correct container name
4. ✅ Check for conflicting styles with higher specificity

```css
/* ✅ Correct */
.parent {
  container-type: inline-size;
}

@container (min-width: 400px) {
  .child {
    display: grid;
  }
}

/* ❌ Wrong: Missing container-type */
@container (min-width: 400px) {
  .child {
    display: grid;
  }
}
```

### Issue 2: Named Containers Not Matching

**Symptoms**: Styles don't apply when using `container-name`.

**Solutions**:
1. ✅ Verify name matches exactly (case-sensitive)
2. ✅ Ensure `container-name` is set before `@container` rule
3. ✅ Check for typos in container name

```css
/* ✅ Correct */
.parent {
  container-name: sidebar;
}

@container sidebar (min-width: 300px) {
  .content { }
}

/* ❌ Wrong: Name mismatch */
.parent {
  container-name: sidebar;
}

@container side-bar (min-width: 300px) {
  .content { }
}
```

### Issue 3: Container Units Not Scaling

**Symptoms**: Container units (`cqi`, `cqw`) not responding to size changes.

**Solutions**:
1. ✅ Ensure parent has `container-type` set
2. ✅ Use appropriate unit (`cqi` for inline, `cqb` for block)
3. ✅ Check for fixed parent dimensions preventing scaling

```css
/* ✅ Correct */
.parent {
  container-type: inline-size;
  width: 100%; /* Allow container to resize */
}

.child {
  font-size: 5cqi;
}

/* ❌ Wrong: Fixed width prevents scaling */
.parent {
  container-type: inline-size;
  width: 500px; /* Fixed width */
}
```

### Issue 4: Performance Issues

**Symptoms**: Janky animations, slow rendering.

**Solutions**:
1. ✅ Use `inline-size` instead of `size` when possible
2. ✅ Add `contain: layout style` to containers
3. ✅ Avoid deeply nested containers
4. ✅ Batch container query styles

```css
/* ✅ Optimized */
.container {
  container-type: inline-size;
  contain: layout style;
}

@container (min-width: 400px) {
  .element-1,
  .element-2,
  .element-3 {
    /* Batched changes */
  }
}
```

---

## Browser Support

| Browser | Version | Support |
|---------|---------|---------|
| Chrome/Edge | 105+ | ✅ Full support |
| Safari | 16+ | ✅ Full support |
| Firefox | 110+ | ✅ Full support |
| Opera | 91+ | ✅ Full support |

**Note**: Always test with `@supports (container-type: inline-size)` for progressive enhancement.

---

## Quick Reference: When to Use Container Queries

✅ **Use Container Queries When**:
- Building reusable components
- Component needs to adapt to its parent, not viewport
- Sidebar content that appears in different widths
- Card components in various grid layouts
- Nested responsive layouts

❌ **Use Media Queries When**:
- Styling based on viewport size
- Global layout breakpoints
- Print styles
- Device orientation changes
- Browser feature detection

---

## Best Practices Summary

1. ✅ Use semantic container names
2. ✅ Prefer `inline-size` over `size`
3. ✅ Keep container queries near component styles
4. ✅ Use container units for responsive values
5. ✅ Implement progressive enhancement with `@supports`
6. ✅ Add `contain` property for performance
7. ✅ Test across browsers and devices
8. ✅ Batch related style changes
9. ✅ Document container query breakpoints
10. ✅ Use fallback strategies for older browsers
