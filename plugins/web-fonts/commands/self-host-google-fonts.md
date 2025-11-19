---
description: Generate self-hosted Google Fonts setup with @font-face declarations and optimized file downloads
---

I'll help you self-host Google Fonts for better performance and privacy.

## Quick Setup

Tell me:
1. **Font family**: e.g., "Inter", "Roboto"
2. **Weights**: e.g., 400, 700
3. **Styles**: normal, italic, or both

## Why Self-Host?

✅ **Better Performance** - No external requests
✅ **Privacy** - No Google tracking
✅ **Reliability** - No CDN dependency
✅ **Control** - Custom subsetting

## Generated Setup

### Step 1: Download Fonts

```bash
# Using google-webfonts-helper
# Visit: https://gwfh.mranftl.com/fonts

# Download WOFF2 files:
# - inter-v12-latin-regular.woff2
# - inter-v12-latin-700.woff2

# Place in: public/fonts/
```

### Step 2: @font-face Declarations

```css
/**
 * Self-Hosted Google Fonts
 * Font: Inter
 * Weights: 400, 700
 * Subset: Latin
 */

/* Regular */
@font-face {
  font-display: swap;
  font-family: 'Inter';
  font-style: normal;
  font-weight: 400;
  src: url('/fonts/inter-v12-latin-regular.woff2') format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+0304, U+0308, U+0329, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}

/* Bold */
@font-face {
  font-display: swap;
  font-family: 'Inter';
  font-style: normal;
  font-weight: 700;
  src: url('/fonts/inter-v12-latin-700.woff2') format('woff2');
  unicode-range: U+0000-00FF, U+0131, U+0152-0153, U+02BB-02BC, U+02C6, U+02DA, U+02DC, U+0304, U+0308, U+0329, U+2000-206F, U+2074, U+20AC, U+2122, U+2191, U+2193, U+2212, U+2215, U+FEFF, U+FFFD;
}
```

### Step 3: Preload Critical Fonts

```html
<head>
  <!-- Preload regular weight -->
  <link
    rel="preload"
    href="/fonts/inter-v12-latin-regular.woff2"
    as="font"
    type="font/woff2"
    crossorigin
  />
</head>
```

### Step 4: Use Font

```css
body {
  font-family: 'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  font-weight: 400;
}

h1, h2, h3 {
  font-weight: 700;
}
```

## Complete Example

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Self-Hosted Google Fonts</title>

  <!-- Preload critical font -->
  <link rel="preload" href="/fonts/inter-v12-latin-regular.woff2" as="font" type="font/woff2" crossorigin>

  <style>
    /* @font-face declarations */
    @font-face {
      font-display: swap;
      font-family: 'Inter';
      font-style: normal;
      font-weight: 400;
      src: url('/fonts/inter-v12-latin-regular.woff2') format('woff2');
    }

    @font-face {
      font-display: swap;
      font-family: 'Inter';
      font-style: normal;
      font-weight: 700;
      src: url('/fonts/inter-v12-latin-700.woff2') format('woff2');
    }

    /* Usage */
    body {
      font-family: 'Inter', system-ui, sans-serif;
    }
  </style>
</head>
<body>
  <h1>Self-Hosted Font</h1>
  <p>Faster loading, better privacy!</p>
</body>
</html>
```

**Tell me which Google Font you want to self-host!**
