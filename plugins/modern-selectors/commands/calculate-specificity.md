---
description: Calculate CSS specificity and debug selector conflicts
---

I'll help you calculate CSS specificity and debug selector conflicts to solve styling issues.

## What This Does

This command helps you:
- Calculate specificity for any CSS selector
- Compare multiple selectors to see which wins
- Debug why your styles aren't being applied
- Understand :is(), :where(), and :has() specificity
- Find solutions to specificity conflicts
- Refactor selectors for better maintainability

## How Specificity Works

CSS specificity is calculated as four numbers: `a,b,c,d`

- **a**: Inline styles (1,0,0,0)
- **b**: ID selectors (0,1,0,0)
- **c**: Classes, attributes, pseudo-classes (0,0,1,0)
- **d**: Elements, pseudo-elements (0,0,0,1)

**Higher numbers win** (compared left to right).

## Quick Reference

### Basic Specificity Values

```css
/* 0,0,0,1 */
p { }

/* 0,0,1,0 */
.text { }

/* 0,1,0,0 */
#header { }

/* 0,0,1,1 */
p.text { }

/* 0,0,2,0 */
.card .text { }

/* 0,1,0,1 */
#header p { }
```

### Modern Selector Specificity

```css
/* 0,0,0,0 - :where() always has 0 specificity */
:where(.btn, #special) { }

/* 0,1,0,0 - :is() takes highest from list (from #special) */
:is(.btn, #special) { }

/* 0,0,1,0 - :not() takes specificity of argument */
:not(.danger) { }

/* 0,0,1,0 - :has() takes specificity of argument */
:has(.active) { }

/* 0,0,2,0 - :is() with multiple classes */
:is(.active, .selected) :is(.highlight, .focus) { }
```

## Calculate Specificity

### Example 1: Basic Selectors

```css
/* Which selector wins? */

/* Selector A: 0,0,0,1 */
p {
  color: black;
}

/* Selector B: 0,0,1,0 - WINS */
.text {
  color: blue;
}

/* Selector C: 0,1,0,0 - WINS */
#content {
  color: red;
}
```

**Winner**: `#content` (0,1,0,0)

### Example 2: Combined Selectors

```css
/* Selector A: 0,0,1,1 */
article.featured {
  font-size: 1.5rem;
}

/* Selector B: 0,0,2,0 - WINS (0,0,2,0 > 0,0,1,1) */
.blog .post {
  font-size: 1.25rem;
}

/* Selector C: 0,1,0,1 - WINS OVERALL */
article#main {
  font-size: 2rem;
}
```

**Winner**: `article#main` (0,1,0,1)

### Example 3: :is() and :where()

```css
/* Selector A: 0,0,0,0 - :where() always 0 */
:where(.btn, #special) {
  padding: 0.5rem;
}

/* Selector B: 0,0,1,0 - WINS (simple class beats :where()) */
.btn-large {
  padding: 1rem;
}

/* Selector C: 0,1,0,0 - :is() takes highest (from #special) - WINS OVERALL */
:is(.btn, #special) {
  padding: 1.5rem;
}
```

**Winner**: `:is(.btn, #special)` (0,1,0,0)

### Example 4: :has() Specificity

```css
/* Selector A: 0,0,1,1 */
.card:has(img) {
  display: grid;
}

/* Selector B: 0,0,2,1 - WINS */
.card.featured:has(img) {
  display: flex;
}

/* Selector C: 0,1,1,1 - WINS OVERALL */
#special.card:has(img) {
  display: block;
}
```

**Winner**: `#special.card:has(img)` (0,1,1,1)

## Common Specificity Problems & Solutions

### Problem 1: Can't Override Framework Styles

**Issue**:
```css
/* Framework CSS: 0,0,2,0 */
.btn.btn-primary {
  background-color: blue;
}

/* Your CSS: 0,0,1,0 - LOSES */
.custom-btn {
  background-color: red;
}
```

**Solutions**:

1. **Match specificity**:
```css
/* 0,0,2,0 - WINS */
.custom-btn.custom-btn {
  background-color: red;
}
```

2. **Use :where() in framework** (if you control it):
```css
/* 0,0,0,0 */
:where(.btn.btn-primary) {
  background-color: blue;
}

/* 0,0,1,0 - WINS */
.custom-btn {
  background-color: red;
}
```

3. **Increase your specificity**:
```css
/* 0,0,2,0 - WINS */
.theme .custom-btn {
  background-color: red;
}
```

### Problem 2: ID Selector Fights

**Issue**:
```css
/* 0,1,0,0 */
#header {
  color: blue;
}

/* 0,0,1,0 - LOSES */
.header-custom {
  color: red;
}
```

**Solutions**:

1. **Avoid IDs for styling** (best):
```css
/* Replace ID with class */
.header {
  color: blue;
}

.header-custom {
  color: red;
}
```

2. **Use :where() with ID** (if you must use ID):
```css
/* 0,0,0,0 */
:where(#header) {
  color: blue;
}

/* 0,0,1,0 - WINS */
.header-custom {
  color: red;
}
```

### Problem 3: Deep Nesting

**Issue**:
```css
/* 0,0,4,3 - Too specific! */
.container .sidebar .nav .link.active {
  color: red;
}

/* Can't override easily */
.custom-link {
  color: blue; /* LOSES */
}
```

**Solutions**:

1. **Flatten selectors** (best):
```css
/* 0,0,1,0 or 0,0,2,0 */
.nav-link-active {
  color: red;
}
```

2. **Use :where() for base**:
```css
/* 0,0,1,0 */
:where(.container .sidebar .nav) .link.active {
  color: red;
}
```

3. **BEM or utility classes**:
```css
.nav__link--active {
  color: red;
}
```

### Problem 4: Inline Styles

**Issue**:
```html
<!-- 1,0,0,0 - Beats everything! -->
<div style="color: blue;"></div>
```

```css
/* 0,1,0,0 - LOSES to inline */
#important {
  color: red;
}
```

**Solutions**:

1. **Remove inline styles** (best)

2. **Use !important** (last resort):
```css
#important {
  color: red !important;
}
```

3. **Use JavaScript to remove inline style**:
```javascript
element.style.removeProperty('color');
```

## Strategic Specificity Patterns

### Pattern 1: Layered Specificity

```css
/* Layer 1: Resets (0 specificity) */
:where(*, *::before, *::after) {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

/* Layer 2: Elements (0,0,0,1) */
button {
  font-family: inherit;
  cursor: pointer;
}

/* Layer 3: Utilities (0,0,1,0) */
.text-center { text-align: center; }
.mt-4 { margin-top: 1rem; }

/* Layer 4: Components (0,0,1,0 to 0,0,2,0) */
.btn { padding: 0.5rem 1rem; }
.btn.btn-large { padding: 1rem 2rem; }

/* Layer 5: States (0,0,2,0) */
.btn:hover { transform: translateY(-2px); }
.btn.btn-primary:hover { background-color: #2563eb; }

/* Layer 6: Overrides (0,0,2,0+) */
.btn.is-loading { opacity: 0.6; }
```

### Pattern 2: Component-First with :where()

```css
/* Base component - 0 specificity */
:where(.button) {
  display: inline-flex;
  align-items: center;
  justify-content: center;
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 0.375rem;
  font-weight: 500;
  cursor: pointer;
  transition: all 0.2s;
}

/* Variants - 0,0,1,0 easily overrides */
.button-primary { background-color: #3b82f6; color: white; }
.button-secondary { background-color: #6b7280; color: white; }
.button-outline { background-color: transparent; border: 2px solid currentColor; }

/* Sizes - 0,0,1,0 */
.button-small { padding: 0.25rem 0.5rem; font-size: 0.875rem; }
.button-large { padding: 0.75rem 1.5rem; font-size: 1.125rem; }

/* States - 0,0,2,0 */
.button-primary:is(:hover, :focus-visible) { background-color: #2563eb; }
.button-secondary:is(:hover, :focus-visible) { background-color: #4b5563; }

/* Modifiers - 0,0,2,0 */
.button-primary.is-loading { opacity: 0.6; pointer-events: none; }
```

### Pattern 3: Utility-First (Tailwind-style)

```css
/* Use :where() for low specificity utilities */
:where(.flex) { display: flex; }
:where(.grid) { display: grid; }
:where(.hidden) { display: none; }

/* Regular specificity for modifiers */
.flex-col { flex-direction: column; }
.gap-4 { gap: 1rem; }

/* Responsive with :is() */
@media (min-width: 768px) {
  :is(.md\:flex-row) { flex-direction: row; }
  :is(.md\:gap-8) { gap: 2rem; }
}
```

## Specificity Calculator Tool

### Calculate Your Selector

Provide your selector, and I'll calculate its specificity:

**Examples**:

```
Input: "p"
Output: 0,0,0,1

Input: ".text"
Output: 0,0,1,0

Input: "#header"
Output: 0,1,0,0

Input: "div.container p.text"
Output: 0,0,2,2

Input: ":is(.active, #special)"
Output: 0,1,0,0 (from #special)

Input: ":where(.active, #special)"
Output: 0,0,0,0 (always)

Input: ".card:has(img:hover)"
Output: 0,0,3,0 (.card + .hover + img)

Input: "article#main .post:first-child"
Output: 0,1,1,2
```

## Compare Selectors

### Example Comparison

**Scenario**: Both selectors target the same element. Which one wins?

```css
/* Selector A */
.card.featured {
  background-color: blue;
}

/* Selector B */
.cards .card {
  background-color: red;
}
```

**Calculation**:
- Selector A: `.card` (0,0,1,0) + `.featured` (0,0,1,0) = **0,0,2,0**
- Selector B: `.cards` (0,0,1,0) + `.card` (0,0,1,0) = **0,0,2,0**

**Result**: **TIE** - last one in source order wins (Selector B)

**Solutions**:
1. Increase A's specificity: `.card.featured.featured` (0,0,3,0)
2. Decrease B's specificity: `:where(.cards) .card` (0,0,1,0)
3. Reorder source code
4. Use :is() or :where() strategically

## Debugging Checklist

When your styles aren't applying:

1. **Check specificity** (use browser DevTools)
2. **Check source order** (later rules win ties)
3. **Check for !important**
4. **Check for inline styles**
5. **Check selector validity**
6. **Check browser support** (especially for :has())

## Browser DevTools

### Chrome/Edge DevTools
1. Right-click element → Inspect
2. Look at "Styles" panel
3. Crossed-out styles = overridden
4. Hover over selector to see specificity

### Firefox DevTools
1. Right-click element → Inspect Element
2. "Rules" panel shows all matching rules
3. Specificity shown on hover
4. Filter by source

## Best Practices

### ✅ DO

1. **Use classes for components**
```css
.button { }
.button-primary { }
```

2. **Use :where() for base styles**
```css
:where(.reset) { margin: 0; padding: 0; }
```

3. **Keep specificity low and consistent**
```css
/* 0,0,1,0 to 0,0,2,0 range */
.component { }
.component__element { }
.component--variant { }
```

4. **Use :is() for grouping**
```css
:is(h1, h2, h3) { font-weight: 700; }
```

### ❌ DON'T

1. **Avoid IDs for styling**
```css
/* BAD */
#header { }

/* GOOD */
.header { }
```

2. **Avoid deep nesting**
```css
/* BAD: 0,0,4,4 */
.container .sidebar .nav .item .link {  }

/* GOOD: 0,0,1,0 */
.nav-link { }
```

3. **Avoid !important**
```css
/* BAD */
.text { color: red !important; }

/* GOOD: Fix specificity instead */
.text.text { color: red; }
```

4. **Avoid inline styles**
```html
<!-- BAD -->
<div style="color: red;">

<!-- GOOD -->
<div class="text-red">
```

## Modern CSS Layers

Use `@layer` for ultimate specificity control:

```css
@layer reset, base, components, utilities, overrides;

@layer reset {
  * { margin: 0; padding: 0; }
}

@layer base {
  button { font-family: inherit; }
}

@layer components {
  .btn { padding: 0.5rem 1rem; }
  .btn-primary { background-color: #3b82f6; }
}

@layer utilities {
  .m-0 { margin: 0; }
  .p-4 { padding: 1rem; }
}

@layer overrides {
  .force-hide { display: none; }
}
```

Layers have lower priority than unlayered styles, regardless of specificity!

## What Happens Next

1. **Provide your selector(s)** and I'll calculate specificity
2. **Describe your issue** and I'll help debug
3. **Show conflicting selectors** and I'll explain which wins
4. **Ask for refactoring advice** for better specificity management

**Just tell me what you need help with, and I'll solve your specificity issues!**
