---
name: css-performance-guide
description: CSS performance optimization reference. Use when searching for performance patterns, Core Web Vitals optimization, or CSS efficiency techniques.
---

# CSS Performance Optimization Guide

Comprehensive reference for optimizing CSS performance, improving Core Web Vitals, and implementing efficient styling patterns.

## Table of Contents

1. [Core Web Vitals Optimization](#core-web-vitals-optimization)
2. [Critical CSS Patterns](#critical-css-patterns)
3. [Render-Blocking Elimination](#render-blocking-elimination)
4. [CSS Selector Performance](#css-selector-performance)
5. [Performance Measurement Tools](#performance-measurement-tools)
6. [Performance Anti-Patterns](#performance-anti-patterns)
7. [Optimization Decision Trees](#optimization-decision-trees)
8. [Performance Budget Templates](#performance-budget-templates)

---

## Core Web Vitals Optimization

### Largest Contentful Paint (LCP)

**Target: < 2.5 seconds**

#### Optimization Checklist

- [ ] **Inline Critical CSS**: Embed above-the-fold styles in `<head>`
- [ ] **Preload Key Resources**: Use `<link rel="preload">` for fonts and critical images
- [ ] **Optimize Web Fonts**: Use `font-display: swap` or `optional`
- [ ] **Remove Unused CSS**: Eliminate dead code (target < 100KB initial CSS)
- [ ] **Minimize CSS File Size**: Compress and minify (target < 50KB gzipped)
- [ ] **Use CSS Containment**: Apply `contain` property for layout isolation
- [ ] **Optimize Images**: Proper sizing, lazy loading, modern formats (WebP, AVIF)
- [ ] **Reduce Server Response Time**: Optimize backend (target < 200ms)

#### LCP-Specific CSS Patterns

```css
/**
 * Pattern 1: Critical Above-the-Fold Styles
 * Description: Inline only styles needed for initial viewport
 * Impact: Reduces LCP by 0.5-1.5s
 */
/* Critical CSS - Inline in <head> */
body {
  margin: 0;
  font-family: system-ui, -apple-system, sans-serif;
  font-size: 16px;
  line-height: 1.5;
}

.hero {
  min-height: 100vh;
  display: grid;
  place-items: center;
}

/**
 * Pattern 2: Font Loading Optimization
 * Description: Prevent invisible text and layout shift
 * Impact: Reduces LCP by 0.3-0.8s, improves CLS
 */
@font-face {
  font-family: 'CustomFont';
  src: url('/fonts/custom.woff2') format('woff2');
  font-display: swap; /* or 'optional' for fastest LCP */
  font-weight: 400;
  font-style: normal;
}

/**
 * Pattern 3: Image Optimization with aspect-ratio
 * Description: Prevent layout shift while loading
 * Impact: Improves CLS, maintains LCP stability
 */
.hero-image {
  width: 100%;
  height: auto;
  aspect-ratio: 16 / 9;
  object-fit: cover;
}

/**
 * Pattern 4: CSS Containment for LCP Element
 * Description: Isolate rendering of LCP element
 * Impact: Reduces rendering complexity by 20-40%
 */
.lcp-container {
  contain: layout style paint;
  content-visibility: auto;
}
```

### Cumulative Layout Shift (CLS)

**Target: < 0.1**

#### Optimization Checklist

- [ ] **Reserve Space for Images**: Use `aspect-ratio` or explicit dimensions
- [ ] **Reserve Space for Ads**: Set min-height for dynamic content
- [ ] **Avoid Dynamic Injection**: Load content placeholders
- [ ] **Use Transform/Opacity**: For animations (not top/left/width/height)
- [ ] **Preload Fonts**: Prevent font-swap layout shift
- [ ] **Avoid Late-Loading CSS**: Load critical styles early
- [ ] **Set Dimensions on Embeds**: YouTube, social media, etc.
- [ ] **Use CSS Grid/Flexbox Properly**: Stable layouts

#### CLS Prevention Patterns

```css
/**
 * Pattern 5: Stable Image Loading
 * Description: Prevent layout shift during image load
 * Impact: CLS score improvement of 0.05-0.15
 */
img, video {
  max-width: 100%;
  height: auto;
  aspect-ratio: attr(width) / attr(height); /* Future spec */
}

/* Current best practice */
.responsive-image {
  aspect-ratio: 16 / 9;
  width: 100%;
  object-fit: cover;
}

/**
 * Pattern 6: Ad Container Placeholder
 * Description: Reserve space for dynamic advertisements
 * Impact: Prevents major layout shifts (0.1-0.3 CLS reduction)
 */
.ad-container {
  min-height: 250px;
  background: linear-gradient(90deg, #f0f0f0 25%, #e0e0e0 50%, #f0f0f0 75%);
  background-size: 200% 100%;
  animation: shimmer 1.5s infinite;
}

@keyframes shimmer {
  0% { background-position: -200% 0; }
  100% { background-position: 200% 0; }
}

/**
 * Pattern 7: Performance-Optimized Animations
 * Description: Use GPU-accelerated properties only
 * Impact: Eliminates layout shift, maintains 60fps
 */
.animated-element {
  /* GOOD: GPU-accelerated, no layout shift */
  transform: translateX(100px);
  opacity: 0.5;
  will-change: transform, opacity;
}

.animated-element-bad {
  /* BAD: Triggers layout recalculation */
  /* left: 100px; */
  /* width: 200px; */
}

/**
 * Pattern 8: Font Loading Strategy
 * Description: Prevent FOIT/FOUT layout shift
 * Impact: CLS reduction of 0.02-0.08
 */
@font-face {
  font-family: 'WebFont';
  src: url('/fonts/webfont.woff2') format('woff2');
  font-display: optional; /* Best for CLS */
  size-adjust: 95%; /* Match fallback font metrics */
}

body {
  font-family: 'WebFont', -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, sans-serif;
}
```

### First Input Delay (FID) / Interaction to Next Paint (INP)

**Target: < 100ms (FID), < 200ms (INP)**

#### Optimization Checklist

- [ ] **Minimize JavaScript Execution**: Reduce main thread blocking
- [ ] **Avoid Complex CSS Selectors**: Reduce selector matching time
- [ ] **Use CSS Containment**: Isolate rendering work
- [ ] **Debounce Resize/Scroll**: Limit layout recalculations
- [ ] **Optimize Animations**: Use `transform` and `opacity` only
- [ ] **Reduce CSS Complexity**: Simplify rules and declarations
- [ ] **Avoid @import**: Use bundling instead
- [ ] **Minimize Reflows**: Batch DOM reads/writes

#### FID/INP CSS Patterns

```css
/**
 * Pattern 9: Efficient Hover States
 * Description: Optimize interactive element performance
 * Impact: Reduces interaction latency by 10-30ms
 */
.button {
  /* Use transform instead of changing dimensions */
  transition: transform 0.2s ease, opacity 0.2s ease;
}

.button:hover {
  transform: scale(1.05);
  opacity: 0.9;
}

/**
 * Pattern 10: CSS Containment for Interactive Elements
 * Description: Limit rendering scope during interactions
 * Impact: 15-40% faster interaction response
 */
.interactive-card {
  contain: layout paint;
}

.interactive-list-item {
  contain: layout style;
  will-change: transform;
}

/**
 * Pattern 11: Optimized Scrolling Performance
 * Description: Enable passive scrolling and GPU acceleration
 * Impact: Maintains 60fps during scroll
 */
.scroll-container {
  overflow-y: auto;
  -webkit-overflow-scrolling: touch; /* iOS momentum */
  overscroll-behavior: contain;
}

.scroll-item {
  contain: layout style paint;
  content-visibility: auto; /* Virtual scrolling */
}
```

---

## Critical CSS Patterns

### Inline Critical CSS Strategy

```html
<!--
  Pattern 12: Critical CSS Inlining
  Description: Embed above-the-fold styles directly in HTML
  Impact: Eliminates render-blocking CSS requests (1-2s faster FCP)
  Size Target: < 14KB (fits in first TCP round-trip)
-->
<!DOCTYPE html>
<html>
<head>
  <style>
    /* Critical CSS - Above the fold only */
    body{margin:0;font:16px/1.5 system-ui,sans-serif}
    .header{height:60px;background:#fff;box-shadow:0 2px 4px rgba(0,0,0,.1)}
    .hero{min-height:100vh;display:grid;place-items:center}
  </style>

  <!-- Preload non-critical CSS -->
  <link rel="preload" href="/css/main.css" as="style" onload="this.onload=null;this.rel='stylesheet'">
  <noscript><link rel="stylesheet" href="/css/main.css"></noscript>
</head>
</html>
```

### Critical CSS Extraction Patterns

```css
/**
 * Pattern 13: Mobile-First Critical CSS
 * Description: Prioritize mobile viewport styles
 * Impact: 80% of users see optimized experience
 */
/* Critical - Mobile viewport */
.container {
  padding: 0 1rem;
  max-width: 100%;
}

/* Non-critical - Desktop enhancement */
@media (min-width: 768px) {
  .container {
    padding: 0 2rem;
    max-width: 1200px;
    margin: 0 auto;
  }
}

/**
 * Pattern 14: Progressive Enhancement Loading
 * Description: Layer styles by priority
 * Impact: Faster perceived performance
 */
/* Layer 1: Critical structure (inline) */
.layout { display: grid; }

/* Layer 2: Core styles (preload) */
.layout { gap: 1rem; padding: 1rem; }

/* Layer 3: Enhancements (async load) */
.layout { box-shadow: 0 4px 6px rgba(0,0,0,.1); }
```

---

## Render-Blocking Elimination

### Techniques to Eliminate Render-Blocking CSS

```html
<!--
  Pattern 15: Async CSS Loading
  Description: Load non-critical CSS asynchronously
  Impact: Reduces blocking time by 0.5-2s
-->
<!-- Method 1: Preload with media query -->
<link rel="preload" href="/css/main.css" as="style" onload="this.onload=null;this.rel='stylesheet'">

<!-- Method 2: Media attribute switching -->
<link rel="stylesheet" href="/css/print.css" media="print" onload="this.media='all'">

<!-- Method 3: Conditional loading -->
<link rel="stylesheet" href="/css/desktop.css" media="(min-width: 1024px)">

<!--
  Pattern 16: Font Loading Optimization
  Description: Prevent font-related render blocking
  Impact: 0.3-1s faster initial render
-->
<!-- Preload critical fonts -->
<link rel="preload" href="/fonts/main.woff2" as="font" type="font/woff2" crossorigin>

<!-- Use font-display in CSS -->
<style>
  @font-face {
    font-family: 'Main';
    src: url('/fonts/main.woff2') format('woff2');
    font-display: swap; /* Show fallback immediately */
  }
</style>

<!--
  Pattern 17: Resource Hints
  Description: Optimize resource loading priority
  Impact: 0.2-0.8s faster resource loading
-->
<!-- DNS prefetch for third-party resources -->
<link rel="dns-prefetch" href="https://fonts.googleapis.com">

<!-- Preconnect for critical third-party resources -->
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Prefetch for next-page resources -->
<link rel="prefetch" href="/css/about.css">
```

### CSS Loading Strategies

```css
/**
 * Pattern 18: Media Query Loading
 * Description: Load CSS conditionally based on media
 * Impact: Reduces initial CSS by 30-60%
 */
/* Always loaded - mobile base styles */
.nav { display: flex; }

/* Loaded only on large screens */
@media (min-width: 1024px) {
  .nav-desktop { display: grid; grid-template-columns: repeat(5, 1fr); }
}

/**
 * Pattern 19: CSS Custom Properties for Dynamic Theming
 * Description: Reduce duplicate code, enable runtime theming
 * Impact: 20-40% smaller CSS files
 */
:root {
  --color-primary: #007bff;
  --color-secondary: #6c757d;
  --spacing-unit: 0.5rem;
  --border-radius: 4px;
}

.button {
  background: var(--color-primary);
  padding: calc(var(--spacing-unit) * 2);
  border-radius: var(--border-radius);
}

/**
 * Pattern 20: Component-Scoped CSS
 * Description: Modular CSS for better caching
 * Impact: Improved cache hit ratio (40-60%)
 */
/* header.css - can be cached independently */
.header { /* styles */ }

/* footer.css - can be cached independently */
.footer { /* styles */ }
```

---

## CSS Selector Performance

### Selector Performance Reference

**Performance Ranking (Fast → Slow)**

1. **ID Selectors**: `#header` (Fastest)
2. **Class Selectors**: `.button`
3. **Tag Selectors**: `div`
4. **Adjacent Sibling**: `.item + .item`
5. **Child Selectors**: `.parent > .child`
6. **Descendant Selectors**: `.ancestor .descendant`
7. **Universal Selectors**: `*`
8. **Attribute Selectors**: `[type="text"]`
9. **Pseudo-classes**: `:hover`, `:nth-child()`
10. **Complex Combinations**: `.a .b .c:nth-child(2n+1)` (Slowest)

### Selector Optimization Patterns

```css
/**
 * Pattern 21: Efficient Selector Structure
 * Description: Optimize selector matching performance
 * Impact: 2-5x faster CSS matching
 */

/* BAD: Deep nesting, right-to-left matching expensive */
.sidebar .nav .menu .item .link:hover {
  color: blue;
}

/* GOOD: Specific class, shallow matching */
.nav-link:hover {
  color: blue;
}

/**
 * Pattern 22: Avoid Universal Selectors
 * Description: Reduce selector matching overhead
 * Impact: 10-50x performance improvement
 */

/* BAD: Matches every element */
* {
  box-sizing: border-box;
}

/* GOOD: Targeted reset */
html {
  box-sizing: border-box;
}

*, *::before, *::after {
  box-sizing: inherit;
}

/**
 * Pattern 23: Optimize Pseudo-Class Usage
 * Description: Reduce expensive pseudo-class calculations
 * Impact: 3-8x faster rendering
 */

/* BAD: Complex nth-child calculations */
.list-item:nth-child(3n+2):not(:last-child) {
  margin-bottom: 1rem;
}

/* GOOD: Simple class-based approach */
.list-item-spaced {
  margin-bottom: 1rem;
}

/**
 * Pattern 24: Attribute Selector Optimization
 * Description: Use efficient attribute matching
 * Impact: 2-4x faster than complex attribute selectors
 */

/* BAD: Substring matching is slow */
[class*="btn-"] {
  padding: 0.5rem 1rem;
}

/* GOOD: Exact or prefix matching is faster */
[data-type="button"] {
  padding: 0.5rem 1rem;
}

/**
 * Pattern 25: Avoid Over-Qualified Selectors
 * Description: Remove unnecessary specificity
 * Impact: Faster matching, better maintainability
 */

/* BAD: Over-qualified */
div.container > ul.list > li.item {
  color: black;
}

/* GOOD: Minimal qualification */
.list-item {
  color: black;
}

/**
 * Pattern 26: Use BEM Methodology
 * Description: Flat, performant selector structure
 * Impact: Consistent performance, no specificity issues
 */

/* Block */
.card { }

/* Element */
.card__header { }
.card__body { }

/* Modifier */
.card--featured { }
.card__header--large { }
```

---

## Performance Measurement Tools

### Browser DevTools

```javascript
/**
 * Pattern 27: Performance API Measurements
 * Description: Measure CSS impact on performance metrics
 */

// Measure CSS load time
performance.getEntriesByType('resource')
  .filter(r => r.initiatorType === 'link' || r.name.endsWith('.css'))
  .forEach(r => {
    console.log(`${r.name}: ${r.duration.toFixed(2)}ms`);
  });

// Measure layout recalculations
const observer = new PerformanceObserver((list) => {
  for (const entry of list.getEntries()) {
    if (entry.entryType === 'layout-shift') {
      console.log('Layout shift score:', entry.value);
    }
  }
});
observer.observe({ entryTypes: ['layout-shift'] });

// Measure paint timing
performance.getEntriesByType('paint').forEach(entry => {
  console.log(`${entry.name}: ${entry.startTime.toFixed(2)}ms`);
});
```

### Lighthouse Metrics

```yaml
# Pattern 28: Lighthouse Performance Budget
# Description: Define performance targets
# Impact: Measurable performance goals

performance_budget:
  metrics:
    - first-contentful-paint: 1800  # ms
    - largest-contentful-paint: 2500
    - cumulative-layout-shift: 0.1
    - total-blocking-time: 300
    - speed-index: 3400

  resources:
    - stylesheet: 100  # KB
    - font: 200
    - image: 500
    - total: 1600

  counts:
    - stylesheet: 3
    - font: 4
    - third-party: 5
```

### CSS Performance Testing Tools

```bash
# Pattern 29: Automated CSS Performance Testing
# Description: Command-line tools for CSS analysis

# Analyze CSS file size and complexity
npx cssstats styles.css

# Identify unused CSS
npx purgecss --css styles.css --content index.html --output purged.css

# Analyze CSS selector performance
npx css-analyzer styles.css

# Measure critical CSS coverage
npx critical index.html --base ./ --inline --minify

# Run Lighthouse CI
npx lighthouse https://example.com --view --preset=desktop
```

### Real User Monitoring (RUM)

```javascript
/**
 * Pattern 30: Web Vitals Monitoring
 * Description: Track real-world CSS performance impact
 * Impact: Data-driven optimization decisions
 */
import {getCLS, getFID, getFCP, getLCP, getTTFB} from 'web-vitals';

function sendToAnalytics({name, delta, value, id}) {
  // Send metrics to analytics service
  gtag('event', name, {
    event_category: 'Web Vitals',
    event_label: id,
    value: Math.round(name === 'CLS' ? delta * 1000 : delta),
    non_interaction: true,
  });
}

getCLS(sendToAnalytics);
getFID(sendToAnalytics);
getFCP(sendToAnalytics);
getLCP(sendToAnalytics);
getTTFB(sendToAnalytics);
```

---

## Performance Anti-Patterns

### Common CSS Performance Mistakes

```css
/**
 * ANTI-PATTERN 1: Excessive Nesting
 * Problem: Slow selector matching, high specificity
 * Impact: 5-10x slower CSS matching
 */
/* BAD */
.header .nav .menu .item .link .icon {
  width: 20px;
}

/* GOOD */
.nav-link-icon {
  width: 20px;
}

/**
 * ANTI-PATTERN 2: Layout-Triggering Properties in Animations
 * Problem: Causes expensive reflows during animation
 * Impact: Dropped frames, janky animations
 */
/* BAD */
@keyframes slide-in {
  from { left: -100px; width: 0; }
  to { left: 0; width: 300px; }
}

/* GOOD */
@keyframes slide-in {
  from { transform: translateX(-100px) scaleX(0); }
  to { transform: translateX(0) scaleX(1); }
}

/**
 * ANTI-PATTERN 3: @import Usage
 * Problem: Sequential loading blocks rendering
 * Impact: 2-5x slower CSS loading
 */
/* BAD */
@import url('reset.css');
@import url('typography.css');
@import url('layout.css');

/* GOOD - Use build tool to concatenate, or link tags */
/* styles.css includes all necessary styles */

/**
 * ANTI-PATTERN 4: Unoptimized Images in CSS
 * Problem: Large background images block rendering
 * Impact: 2-10s slower LCP
 */
/* BAD */
.hero {
  background: url('/images/hero-4k.jpg');
}

/* GOOD */
.hero {
  background: url('/images/hero-mobile.webp');
}

@media (min-width: 768px) {
  .hero {
    background: url('/images/hero-desktop.webp');
  }
}

/**
 * ANTI-PATTERN 5: Forcing Reflows in JavaScript
 * Problem: Reading layout properties triggers synchronous reflow
 * Impact: Blocks main thread, poor INP
 */
/* Avoid this pattern in JavaScript */
// BAD
elements.forEach(el => {
  el.style.width = el.offsetWidth + 10 + 'px'; // Read then write
});

// GOOD - Batch reads and writes
const widths = elements.map(el => el.offsetWidth); // Batch reads
elements.forEach((el, i) => {
  el.style.width = widths[i] + 10 + 'px'; // Batch writes
});

/**
 * ANTI-PATTERN 6: Expensive Box Shadows and Filters
 * Problem: Heavy GPU load, poor scrolling performance
 * Impact: Reduced framerate, battery drain
 */
/* BAD */
.card {
  box-shadow: 0 0 100px 50px rgba(0,0,0,0.5);
  filter: blur(20px) brightness(1.5) contrast(2);
}

/* GOOD */
.card {
  box-shadow: 0 2px 8px rgba(0,0,0,0.1);
}

/**
 * ANTI-PATTERN 7: Missing Content-Visibility
 * Problem: Renders off-screen content unnecessarily
 * Impact: 2-5x slower initial render for long pages
 */
/* BAD */
.article-section {
  /* No optimization */
}

/* GOOD */
.article-section {
  content-visibility: auto;
  contain-intrinsic-size: 0 500px; /* Estimated height */
}

/**
 * ANTI-PATTERN 8: Unoptimized Fonts
 * Problem: FOIT (Flash of Invisible Text) or FOUT
 * Impact: Poor LCP, CLS issues
 */
/* BAD */
@font-face {
  font-family: 'CustomFont';
  src: url('/fonts/custom.ttf'); /* Large format, no display strategy */
}

/* GOOD */
@font-face {
  font-family: 'CustomFont';
  src: url('/fonts/custom.woff2') format('woff2');
  font-display: swap;
  unicode-range: U+0000-00FF; /* Latin subset only */
}
```

---

## Optimization Decision Trees

### CSS Loading Strategy Decision Tree

```
START: Does CSS affect above-the-fold content?
│
├─ YES: Is CSS < 14KB?
│  ├─ YES: Inline in <head>
│  └─ NO: Is it critical for LCP?
│     ├─ YES: Extract critical CSS, inline it
│     │       Load full CSS async
│     └─ NO: Load async with preload
│
└─ NO: Is CSS needed on first interaction?
   ├─ YES: Preload with low priority
   └─ NO: Lazy load on interaction or prefetch
```

### Animation Performance Decision Tree

```
START: Need to animate element?
│
├─ What property to animate?
│  ├─ Transform/Opacity: Safe, GPU-accelerated
│  ├─ Color/Background: Moderate, paint only
│  └─ Width/Height/Position: Expensive, causes reflow
│
└─ Will it affect many elements?
   ├─ YES: Use CSS containment
   │       will-change: transform
   └─ NO: Standard GPU animation
          transform + opacity
```

### Selector Optimization Decision Tree

```
START: Writing CSS selector?
│
├─ How many elements will match?
│  ├─ 1-10: Class selector fine
│  ├─ 10-100: Avoid complex pseudo-classes
│  └─ 100+: Use simple class, avoid nesting
│
└─ What's the nesting depth?
   ├─ 0-2 levels: Good performance
   ├─ 3-4 levels: Consider refactoring
   └─ 5+ levels: Definitely refactor
```

---

## Performance Budget Templates

### Budget 1: Small Marketing Site

```yaml
# Target: < 1s LCP, < 0.05 CLS, < 100ms FID
assets:
  css:
    critical_inline: 14kb    # Inline in HTML
    total_css: 50kb          # All CSS compressed
    files: 2                 # Maximum number of CSS files

  fonts:
    total_size: 100kb        # All font files
    families: 2              # Maximum font families
    weights: 4               # Maximum font weights

  images:
    hero: 150kb              # Largest image
    total: 500kb             # All images

metrics:
  lcp: 1500ms
  fcp: 800ms
  cls: 0.05
  tbt: 150ms
```

### Budget 2: E-commerce Site

```yaml
# Target: < 2.5s LCP, < 0.1 CLS, < 100ms FID
assets:
  css:
    critical_inline: 14kb
    page_css: 80kb           # Per-page CSS
    shared_css: 120kb        # Shared across site
    files: 4

  fonts:
    total_size: 200kb
    families: 3
    weights: 6

  images:
    product: 100kb           # Per product image
    hero: 200kb
    total_above_fold: 400kb

metrics:
  lcp: 2500ms
  fcp: 1200ms
  cls: 0.1
  tbt: 300ms
  tti: 3500ms
```

### Budget 3: Web Application

```yaml
# Target: < 2s LCP, < 0.1 CLS, < 50ms INP
assets:
  css:
    critical_inline: 14kb
    app_css: 150kb           # Application CSS
    vendor_css: 100kb        # Third-party CSS
    files: 5

  fonts:
    total_size: 150kb
    families: 2
    weights: 4

  runtime:
    max_bundle: 300kb        # Max JS bundle size
    css_in_js: 50kb          # CSS-in-JS runtime cost

metrics:
  lcp: 2000ms
  fcp: 1000ms
  cls: 0.1
  inp: 200ms
  tbt: 200ms
```

---

## Advanced Performance Patterns

### Pattern 31: CSS Grid Performance Optimization

```css
/**
 * Description: Optimize CSS Grid for performance
 * Impact: 30-50% faster layout calculations
 */

/* BAD: Complex auto-placement */
.grid-container {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(250px, 1fr));
  gap: 1rem;
}

/* GOOD: Explicit grid with containment */
.grid-container {
  display: grid;
  grid-template-columns: repeat(3, 1fr);
  gap: 1rem;
  contain: layout style;
}

.grid-item {
  contain: layout paint;
}
```

### Pattern 32: Responsive Images with CSS

```css
/**
 * Description: Performance-optimized responsive images
 * Impact: 40-70% faster image loading
 */

.responsive-img {
  width: 100%;
  height: auto;
  aspect-ratio: 16 / 9;
  object-fit: cover;
  content-visibility: auto;

  /* Progressive enhancement */
  background: linear-gradient(to bottom, #f0f0f0, #e0e0e0);
}

/* Use with <picture> element for art direction */
```

### Pattern 33: Dark Mode Performance

```css
/**
 * Description: Efficient dark mode implementation
 * Impact: No performance penalty, better UX
 */

:root {
  --bg: #ffffff;
  --text: #000000;
  color-scheme: light;
}

@media (prefers-color-scheme: dark) {
  :root {
    --bg: #000000;
    --text: #ffffff;
    color-scheme: dark;
  }
}

/* Use custom properties for theme */
body {
  background: var(--bg);
  color: var(--text);
  transition: none; /* Avoid flash on load */
}
```

### Pattern 34: Virtual Scrolling with CSS

```css
/**
 * Description: Optimize long lists with content-visibility
 * Impact: 5-10x faster rendering for long lists
 */

.virtual-scroll-container {
  overflow-y: auto;
  height: 600px;
  contain: strict;
}

.virtual-scroll-item {
  content-visibility: auto;
  contain-intrinsic-size: 0 100px;
}
```

### Pattern 35: Performance Monitoring CSS

```css
/**
 * Description: Add performance hints to CSS
 * Impact: Better browser optimization
 */

/* High-priority resources */
.critical-image {
  /* Browser hint for importance */
  content: url('/hero.jpg') / 'high';
}

/* Low-priority resources */
.lazy-background {
  /* Defer loading */
  background: url('/pattern.jpg') / 'low';
}
```

---

## Performance Metrics Glossary

### Core Web Vitals

- **LCP (Largest Contentful Paint)**: Time to render largest content element
  - Good: < 2.5s
  - Needs Improvement: 2.5s - 4.0s
  - Poor: > 4.0s

- **FID (First Input Delay)**: Time from first interaction to browser response
  - Good: < 100ms
  - Needs Improvement: 100ms - 300ms
  - Poor: > 300ms

- **INP (Interaction to Next Paint)**: Responsiveness throughout page lifecycle
  - Good: < 200ms
  - Needs Improvement: 200ms - 500ms
  - Poor: > 500ms

- **CLS (Cumulative Layout Shift)**: Visual stability metric
  - Good: < 0.1
  - Needs Improvement: 0.1 - 0.25
  - Poor: > 0.25

### Additional Metrics

- **FCP (First Contentful Paint)**: Time to first text/image render
- **TTI (Time to Interactive)**: Time until page is fully interactive
- **TBT (Total Blocking Time)**: Total time main thread is blocked
- **SI (Speed Index)**: How quickly content is visually displayed

---

## CSS Performance Checklist

### Pre-Development

- [ ] Define performance budget
- [ ] Identify critical rendering path
- [ ] Plan CSS architecture (modular, component-based)
- [ ] Choose CSS methodology (BEM, SMACSS, etc.)
- [ ] Set up performance monitoring

### Development

- [ ] Write mobile-first CSS
- [ ] Use efficient selectors (max 3 levels deep)
- [ ] Avoid expensive properties in animations
- [ ] Use CSS containment where applicable
- [ ] Optimize font loading
- [ ] Implement critical CSS strategy
- [ ] Use CSS custom properties for theming
- [ ] Add proper image dimensions
- [ ] Use modern layout methods (Grid, Flexbox)

### Build Process

- [ ] Minify CSS files
- [ ] Remove unused CSS (PurgeCSS, etc.)
- [ ] Concatenate CSS files (< 3 files)
- [ ] Compress with gzip/brotli
- [ ] Generate critical CSS
- [ ] Optimize font files (subset, WOFF2)
- [ ] Set up proper caching headers

### Deployment

- [ ] Inline critical CSS (< 14KB)
- [ ] Async load non-critical CSS
- [ ] Preload key resources
- [ ] Use CDN for static assets
- [ ] Enable HTTP/2 or HTTP/3
- [ ] Monitor Core Web Vitals
- [ ] Set up performance alerts

### Post-Launch

- [ ] Monitor real-user metrics (RUM)
- [ ] Analyze CSS coverage reports
- [ ] A/B test performance improvements
- [ ] Regular performance audits
- [ ] Update performance budget

---

## Tools and Resources

### Build Tools

- **PurgeCSS**: Remove unused CSS
- **Critical**: Extract critical CSS
- **cssnano**: CSS minification
- **PostCSS**: CSS transformations
- **Autoprefixer**: Vendor prefixes

### Analysis Tools

- **Chrome DevTools**: Performance profiling
- **Lighthouse**: Comprehensive audits
- **WebPageTest**: Real-world testing
- **Chrome UX Report**: Field data
- **web-vitals**: Core Web Vitals library

### Monitoring Services

- **Google Analytics**: Custom metrics
- **Sentry**: Performance monitoring
- **New Relic**: Application performance
- **Datadog**: Real-user monitoring
- **SpeedCurve**: Performance tracking

---

## Quick Reference Tables

### CSS Property Performance Impact

| Property | Layout | Paint | Composite | Performance |
|----------|--------|-------|-----------|-------------|
| transform | No | No | Yes | Excellent |
| opacity | No | No | Yes | Excellent |
| color | No | Yes | No | Good |
| background | No | Yes | No | Good |
| box-shadow | No | Yes | No | Moderate |
| width/height | Yes | Yes | Yes | Poor |
| top/left | Yes | Yes | Yes | Poor |
| margin/padding | Yes | Yes | Yes | Poor |

### File Size Targets

| Asset Type | Target Size | Maximum Size |
|------------|-------------|--------------|
| Critical CSS | < 14 KB | 20 KB |
| Page CSS | < 50 KB | 100 KB |
| Total CSS | < 100 KB | 200 KB |
| Web Font | < 50 KB | 100 KB |
| Font Family | < 150 KB | 300 KB |

### Loading Priority

| Priority | Strategy | Use Case |
|----------|----------|----------|
| Critical | Inline | Above-fold styles |
| High | Preload | LCP elements |
| Medium | Normal link | Below-fold styles |
| Low | Async load | Print, themes |
| Defer | Prefetch | Next-page styles |

---

This comprehensive CSS performance guide provides 35+ optimization patterns, measurement strategies, and decision-making frameworks to achieve excellent Core Web Vitals scores and deliver fast, efficient web experiences.
