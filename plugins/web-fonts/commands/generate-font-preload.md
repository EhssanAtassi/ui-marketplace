---
description: Generate font preload snippets with correct crossorigin and type attributes
---

I'll generate optimized font preload snippets for your critical fonts.

## Quick Generation

Tell me:
1. **Font file path**: e.g., `/fonts/inter-regular.woff2`
2. **How many fonts**: Limit to 1-2 for best performance

⚠️ **Important**: Only preload fonts that are immediately visible above the fold.

## Generated Preload Snippets

### Single Font (Recommended)

```html
<link
  rel="preload"
  href="/fonts/inter-regular.woff2"
  as="font"
  type="font/woff2"
  crossorigin
/>
```

### Multiple Weights

```html
<!-- Regular weight (most critical) -->
<link rel="preload" href="/fonts/inter-400.woff2" as="font" type="font/woff2" crossorigin>

<!-- Bold weight (if critical) -->
<link rel="preload" href="/fonts/inter-700.woff2" as="font" type="font/woff2" crossorigin>
```

### Variable Font

```html
<link
  rel="preload"
  href="/fonts/inter-variable.woff2"
  as="font"
  type="font/woff2"
  crossorigin
/>
```

## Complete Example

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">

  <!-- DNS prefetch for Google Fonts (if using) -->
  <link rel="dns-prefetch" href="https://fonts.googleapis.com">

  <!-- Preconnect for Google Fonts (if using) -->
  <link rel="preconnect" href="https://fonts.googleapis.com">
  <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>

  <!-- Preload critical self-hosted fonts -->
  <link
    rel="preload"
    href="/fonts/inter-regular.woff2"
    as="font"
    type="font/woff2"
    crossorigin
  />

  <!-- Font declarations -->
  <style>
    @font-face {
      font-family: 'Inter';
      src: url('/fonts/inter-regular.woff2') format('woff2');
      font-display: swap;
      font-weight: 400;
    }

    body {
      font-family: 'Inter', system-ui, sans-serif;
    }
  </style>
</head>
<body>
  <h1>Optimized Font Loading</h1>
</body>
</html>
```

## Best Practices

✅ **DO:**
- Preload 1-2 critical fonts only
- Include `crossorigin` attribute
- Specify `type="font/woff2"`
- Place in `<head>` before stylesheets

❌ **DON'T:**
- Preload all font weights
- Forget `crossorigin` (will load twice!)
- Preload fonts not used above fold
- Preload before critical CSS

## Framework Integration

### Next.js

```tsx
// app/layout.tsx or pages/_document.tsx
<Head>
  <link
    rel="preload"
    href="/fonts/inter-regular.woff2"
    as="font"
    type="font/woff2"
    crossorigin="anonymous"
  />
</Head>
```

### React Helmet

```jsx
<Helmet>
  <link
    rel="preload"
    href="/fonts/inter-regular.woff2"
    as="font"
    type="font/woff2"
    crossOrigin="anonymous"
  />
</Helmet>
```

### Angular

```html
<!-- index.html -->
<link rel="preload" href="/assets/fonts/inter-regular.woff2" as="font" type="font/woff2" crossorigin>
```

**Tell me which fonts to preload!**
