---
description: Interactive wizard to find the perfect modern CSS selector for your use case
---

I'll help you find the perfect modern CSS selector pattern for your specific need.

## What This Does

This wizard helps you discover the right selector by:
- Understanding your use case
- Recommending the best selector approach
- Providing complete code examples
- Explaining browser compatibility
- Offering fallback strategies

## Common Use Cases

Tell me what you're trying to do, and I'll provide the exact selector pattern:

### 1. Parent/Container Styling

**"Style a parent based on its children"**

Examples:
- "Style a card when it contains an image"
- "Highlight a form group when input is invalid"
- "Show different layout when sidebar exists"
- "Style parent when child is hovered"

**Selector**: `:has()`

### 2. Form Validation

**"Style forms based on validation state"**

Examples:
- "Show error styling when input is invalid"
- "Highlight form group when field is focused"
- "Disable submit button when form has errors"
- "Show success indicator when all fields are valid"

**Selectors**: `:has()`, `:invalid`, `:valid`, `:focus`, `:placeholder-shown`

### 3. Interactive Elements

**"Make elements interactive without JavaScript"**

Examples:
- "Create tabs with only CSS"
- "Build an accordion without JS"
- "Toggle content visibility"
- "Highlight entire row on button hover"

**Selectors**: `:has()`, `:checked`, `+`, `~`

### 4. Simplify Repetitive Selectors

**"Group similar selectors together"**

Examples:
- "Style all headings the same way"
- "Apply hover styles to multiple elements"
- "Target multiple input types"
- "Combine state selectors"

**Selector**: `:is()`

### 5. Base Styles (Easy to Override)

**"Create default styles that won't fight specificity"**

Examples:
- "Reset button styles"
- "Default link colors"
- "Base form field styling"
- "Typography defaults"

**Selector**: `:where()`

### 6. Exclude Elements

**"Select everything except..."**

Examples:
- "All items except the first"
- "All buttons except disabled ones"
- "Inputs except checkboxes and radios"
- "Links that aren't external"

**Selector**: `:not()`

### 7. Position-Based Styling

**"Style based on element position"**

Examples:
- "Every 3rd item"
- "First 5 items"
- "Last 3 items"
- "Items 4-8"
- "Zebra striping (alternating colors)"

**Selector**: `:nth-child()`, `:nth-last-child()`

### 8. Keyboard Navigation

**"Show focus only for keyboard users"**

Examples:
- "Focus ring only on keyboard navigation"
- "Highlight parent when child is focused"
- "Expand search when focused"
- "Show dropdown menu on focus"

**Selectors**: `:focus-visible`, `:focus-within`

### 9. Attribute-Based Styling

**"Style based on HTML attributes"**

Examples:
- "Required form fields"
- "External links"
- "File type indicators (PDF, DOC)"
- "Data attributes for state"
- "ARIA attributes"

**Selector**: `[attribute]`, `[attribute="value"]`, `[attribute^="value"]`, etc.

### 10. Element Relationships

**"Style based on DOM structure"**

Examples:
- "Paragraph immediately after heading"
- "All siblings after an element"
- "Direct children only"
- "Label after checked checkbox"

**Combinators**: `+`, `~`, `>`, ` `

## Quick Examples by Category

### Parent Selection with :has()

```css
/* Card with image vs without */
.card:has(img) {
  display: grid;
  grid-template-columns: 200px 1fr;
}

.card:not(:has(img)) {
  display: block;
}

/* Form validation */
.form-group:has(input:invalid) {
  border-left: 3px solid #ef4444;
  background-color: #fef2f2;
}

.form-group:has(input:valid) {
  border-left: 3px solid #10b981;
  background-color: #f0fdf4;
}

/* Interactive highlighting */
.list-item:has(button:hover) {
  background-color: #f3f4f6;
  transform: translateX(4px);
}

/* Empty state */
.gallery:not(:has(img))::after {
  content: "No images to display";
}

/* Quantity-based layout */
.grid:has(> .item:nth-child(n+7)) {
  grid-template-columns: repeat(4, 1fr);
}
```

### Selector List with :is()

```css
/* Multiple elements */
:is(h1, h2, h3, h4, h5, h6) {
  font-family: 'Inter', sans-serif;
  font-weight: 700;
}

/* Multiple states */
button:is(:hover, :focus-visible, :active) {
  outline: 2px solid #3b82f6;
}

/* Form elements */
:is(input, select, textarea):is(:focus, :focus-visible) {
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

/* Data attributes */
:is([data-state="loading"], [data-state="pending"]) {
  pointer-events: none;
  opacity: 0.6;
}
```

### Zero Specificity with :where()

```css
/* Base button styles (easy to override) */
:where(button, .btn) {
  padding: 0.5rem 1rem;
  border: none;
  border-radius: 0.375rem;
}

/* Simple class wins */
.btn-large {
  padding: 1rem 2rem;
}

/* Reset styles */
:where(h1, h2, h3, h4, h5, h6) {
  margin: 0;
  font-weight: inherit;
}

/* Theme defaults */
:where([data-theme="dark"]) :where(h1, h2, p) {
  color: #f9fafb;
}
```

### Negation with :not()

```css
/* Exclude elements */
button:not(.btn-danger) {
  background-color: #3b82f6;
}

/* All but first/last */
.list-item:not(:first-child) {
  margin-top: 1rem;
}

.list-item:not(:last-child) {
  border-bottom: 1px solid #e5e7eb;
}

/* Accessibility */
img:not([alt]) {
  outline: 3px solid #ef4444;
}

/* Type exclusions */
input:not([type="checkbox"]):not([type="radio"]) {
  width: 100%;
  padding: 0.5rem;
}

/* With :has() */
.card:not(:has(img)) {
  padding: 2rem;
}
```

### Position with :nth-child()

```css
/* Zebra striping */
tr:nth-child(odd) {
  background-color: #f9fafb;
}

/* Every nth */
.grid-item:nth-child(3n) {
  grid-column: span 2;
}

/* First n items */
.list-item:nth-child(-n+3) {
  font-weight: 600;
  background-color: #eff6ff;
}

/* Last n items */
.list-item:nth-last-child(-n+3) {
  opacity: 0.6;
}

/* Range */
.item:nth-child(n+4):nth-child(-n+8) {
  border-left: 3px solid #3b82f6;
}

/* Color patterns */
.tag:nth-child(5n+1) { background-color: #ef4444; }
.tag:nth-child(5n+2) { background-color: #3b82f6; }
.tag:nth-child(5n+3) { background-color: #10b981; }
```

### Keyboard Focus with :focus-visible

```css
/* Keyboard-only focus */
button:focus-visible {
  outline: 2px solid #3b82f6;
  outline-offset: 2px;
}

/* Hide mouse-click focus */
button:focus:not(:focus-visible) {
  outline: none;
}

/* Parent focus */
.form-group:focus-within {
  background-color: #eff6ff;
  border-left: 3px solid #3b82f6;
}

/* Search expansion */
.search-container:focus-within {
  width: 400px;
}

/* Skip link */
.skip-link:focus-visible {
  position: static;
  padding: 1rem 2rem;
}
```

### Attributes

```css
/* Required fields */
input[required] {
  border-left: 3px solid #ef4444;
}

/* External links */
a[href^="http://"]::after,
a[href^="https://"]::after {
  content: " ↗";
}

/* Email links */
a[href^="mailto:"] {
  color: #3b82f6;
}

/* File types */
a[href$=".pdf"]::after {
  content: " (PDF)";
  color: #ef4444;
}

/* Data state */
[data-state="loading"] {
  pointer-events: none;
  opacity: 0.6;
}

/* ARIA */
[aria-expanded="true"] .icon {
  transform: rotate(180deg);
}
```

### Combinators

```css
/* Descendant */
article p {
  line-height: 1.6;
}

/* Direct child */
nav > ul {
  display: flex;
  gap: 1rem;
}

/* Adjacent sibling */
h2 + p {
  font-size: 1.125rem;
  font-weight: 500;
}

/* General sibling */
h2 ~ p {
  text-align: left;
}

/* Checkbox UI */
input[type="checkbox"]:checked + label {
  color: #10b981;
  font-weight: 600;
}
```

## Complete Use Case Examples

### 1. CSS-Only Tabs

```html
<div class="tabs">
  <input type="radio" name="tab" id="tab1" checked>
  <input type="radio" name="tab" id="tab2">
  <input type="radio" name="tab" id="tab3">

  <label for="tab1">Tab 1</label>
  <label for="tab2">Tab 2</label>
  <label for="tab3">Tab 3</label>

  <div id="panel1" class="panel">Panel 1 content</div>
  <div id="panel2" class="panel">Panel 2 content</div>
  <div id="panel3" class="panel">Panel 3 content</div>
</div>
```

```css
.tabs input[type="radio"] {
  display: none;
}

.tabs label {
  padding: 0.75rem 1.5rem;
  cursor: pointer;
  border-bottom: 2px solid transparent;
}

.tabs input:checked + label {
  background-color: white;
  border-bottom-color: #3b82f6;
  font-weight: 600;
}

.panel {
  display: none;
  padding: 1.5rem;
}

.tabs:has(#tab1:checked) #panel1,
.tabs:has(#tab2:checked) #panel2,
.tabs:has(#tab3:checked) #panel3 {
  display: block;
}
```

### 2. Form Validation with Real-Time Feedback

```css
.form-field {
  margin-bottom: 1.5rem;
}

.form-field:has(input:focus) {
  background-color: #eff6ff;
}

.form-field:has(input:not(:placeholder-shown):invalid) {
  border-left: 3px solid #ef4444;
  background-color: #fef2f2;
}

.form-field:has(input:not(:placeholder-shown):valid) {
  border-left: 3px solid #10b981;
  background-color: #f0fdf4;
}

.error-message {
  display: none;
  color: #ef4444;
  font-size: 0.875rem;
}

.form-field:has(input:invalid:not(:placeholder-shown)) .error-message {
  display: block;
}

.submit-btn {
  opacity: 0.6;
  cursor: not-allowed;
}

.form:not(:has(input:invalid)) .submit-btn {
  opacity: 1;
  cursor: pointer;
}
```

### 3. Interactive Card Grid

```css
.card {
  border: 1px solid #e5e7eb;
  border-radius: 0.5rem;
  padding: 1.5rem;
  transition: all 0.3s;
}

.card:has(img) {
  display: grid;
  grid-template-columns: 200px 1fr;
  gap: 1rem;
}

.card:has(a:hover),
.card:has(button:hover) {
  border-color: #3b82f6;
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1);
  transform: translateY(-4px);
}

.card:has(.bookmark:checked) {
  border-color: #f59e0b;
  background-color: #fffbeb;
}
```

### 4. Quantity-Based Layout

```css
/* Default: 1 column */
.grid {
  display: grid;
  gap: 1rem;
}

/* 2-3 items: 2 columns */
.grid:has(> .item:nth-child(n+2):nth-child(-n+3)) {
  grid-template-columns: repeat(2, 1fr);
}

/* 4-6 items: 3 columns */
.grid:has(> .item:nth-child(n+4):nth-child(-n+6)) {
  grid-template-columns: repeat(3, 1fr);
}

/* 7+ items: 4 columns */
.grid:has(> .item:nth-child(n+7)) {
  grid-template-columns: repeat(4, 1fr);
}
```

## Browser Support Check

### :has()
**Support**: Chrome 105+, Safari 15.4+, Firefox 121+

**Fallback**:
```css
@supports not selector(:has(*)) {
  /* Fallback styles */
  .card {
    display: block;
  }
}

@supports selector(:has(*)) {
  /* Enhanced styles */
  .card:has(img) {
    display: grid;
  }
}
```

### :is() and :where()
**Support**: Chrome 88+, Safari 14+, Firefox 78+

**Fallback**:
```css
/* Old way */
h1, h2, h3, h4, h5, h6 {
  font-weight: 700;
}

/* Modern way (with fallback above) */
:is(h1, h2, h3, h4, h5, h6) {
  font-weight: 700;
}
```

### :focus-visible
**Support**: Chrome 86+, Safari 15.4+, Firefox 85+

**Fallback**:
```css
/* Use :focus as fallback */
button:focus {
  outline: 2px solid #3b82f6;
}

@supports selector(:focus-visible) {
  button:focus:not(:focus-visible) {
    outline: none;
  }

  button:focus-visible {
    outline: 2px solid #3b82f6;
  }
}
```

## What Happens Next

1. Tell me your specific use case
2. I'll provide the exact selector pattern
3. Complete code example with explanations
4. Browser compatibility notes
5. Fallback strategies if needed
6. Performance tips
7. Accessibility considerations

**Just describe what you're trying to achieve, and I'll provide the perfect modern CSS selector solution!**
