---
description: Analyze and optimize web fonts with recommendations for font-display, preloading, and performance
---

I'll analyze your fonts and provide optimization recommendations.

## Quick Optimization

Tell me:
1. **Font source**: Google Fonts, self-hosted, or Adobe Fonts
2. **Font families**: Which fonts you're using
3. **Weights needed**: 400, 700, etc.

## Optimization Checklist

### ✅ Use WOFF2
```css
@font-face {
  font-family: 'Inter';
  src: url('inter.woff2') format('woff2'); /* 30% smaller than WOFF */
  font-display: swap;
}
```

### ✅ Add font-display

```css
/* Body text - swap for instant render */
font-display: swap;

/* Icons - block to prevent missing icons */
font-display: block;

/* Performance-first - optional */
font-display: optional;
```

### ✅ Preload Critical Fonts

```html
<!-- Only 1-2 most critical fonts -->
<link rel="preload" href="/fonts/inter-regular.woff2" as="font" type="font/woff2" crossorigin>
```

### ✅ Subset Fonts

```css
/* Latin only (80% smaller) */
@font-face {
  font-family: 'Inter';
  src: url('inter-latin.woff2') format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153;
}
```

### ✅ Limit Weights

```html
<!-- Before: All weights (600KB) -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@100;200;300;400;500;600;700;800;900">

<!-- After: Only needed (120KB) -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap">
```

## Optimized Patterns

### Google Fonts (Optimized)

```html
<!-- Preconnect -->
<link rel="preconnect" href="https://fonts.googleapis.com">
<link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

<!-- Load with display=swap -->
<link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;700&display=swap" rel="stylesheet">
```

### Self-Hosted (Best Performance)

```html
<link rel="preload" href="/fonts/inter-400.woff2" as="font" type="font/woff2" crossorigin>

<style>
  @font-face {
    font-family: 'Inter';
    src: url('/fonts/inter-400.woff2') format('woff2');
    font-display: swap;
    font-weight: 400;
  }
</style>
```

### Variable Font (Multi-Weight)

```html
<link rel="preload" href="/fonts/inter-variable.woff2" as="font" type="font/woff2" crossorigin>

<style>
  @font-face {
    font-family: 'Inter Variable';
    src: url('/fonts/inter-variable.woff2') format('woff2-variations');
    font-display: swap;
    font-weight: 100 900;
  }
</style>
```

**Share your current setup for personalized optimization!**
