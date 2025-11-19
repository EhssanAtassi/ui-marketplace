---
description: Analyze and optimize your PostCSS configuration for better performance and smaller bundle sizes
---

I'll analyze your PostCSS config and provide optimization recommendations.

## Quick Optimization

Share your `postcss.config.js` and I'll:
1. Identify performance bottlenecks
2. Suggest plugin additions/removals
3. Optimize plugin order
4. Add production optimizations
5. Configure browser targets

## Optimized Production Config

```javascript
/**
 * Optimized PostCSS Configuration
 * - Fast development builds
 * - Optimized production builds
 * - Browser compatibility
 */
module.exports = {
  plugins: [
    // 1. Import resolution (run first)
    require('postcss-import')({
      path: ['src/styles', 'node_modules'],
    }),

    // 2. Modern CSS features
    require('postcss-preset-env')({
      stage: 2,
      features: {
        'nesting-rules': true,
        'custom-properties': true,
        'custom-media-queries': true,
      },
      autoprefixer: {
        grid: 'autoplace',
      },
      browsers: 'last 2 versions, > 1%, not dead',
    }),

    // 3. Production optimizations
    process.env.NODE_ENV === 'production' && require('@fullhuman/postcss-purgecss')({
      content: ['./src/**/*.{html,ts,tsx,jsx}'],
      safelist: {
        standard: [/^mat-/, /^cdk-/, /^ng-/],
        deep: [/data-theme/],
      },
      defaultExtractor: content => content.match(/[\w-/:]+(?<!:)/g) || [],
    }),

    process.env.NODE_ENV === 'production' && require('cssnano')({
      preset: ['advanced', {
        discardComments: { removeAll: true },
        reduceIdents: true,
        zindex: false,
        autoprefixer: false,
      }],
    }),

    // 4. Development helpers
    process.env.NODE_ENV === 'development' && require('postcss-reporter')({
      clearReportedMessages: true,
    }),
  ].filter(Boolean),
};
```

## Performance Tips

### 1. Plugin Order
```javascript
// Correct order for best performance
[
  'postcss-import',      // First - resolve imports
  'postcss-preset-env',  // Second - transform CSS
  'purgecss',           // Third - remove unused
  'cssnano',            // Last - minify
]
```

### 2. Conditional Loading
```javascript
// Only run heavy plugins in production
process.env.NODE_ENV === 'production' && require('cssnano')()
```

### 3. Browser Targets
```javascript
// .browserslistrc
last 2 versions
> 1%
not dead
not IE 11
```

## Bundle Size Optimization

### Before
```
main.css: 450 KB
```

### After (with PurgeCSS + cssnano)
```
main.css: 45 KB (90% reduction)
```

**Share your config for personalized optimization!**
