---
name: setup-postcss
description: Set up PostCSS with modern plugins and build optimization for CSS processing
---

You are tasked with setting up PostCSS with an optimized plugin pipeline.

## Instructions

1. **Ask the user**:
   - Build tool (Webpack, Vite, Parcel, Gulp, standalone)
   - Desired features:
     - Autoprefixer
     - CSS nesting
     - Future CSS features (preset-env)
     - Minification (cssnano)
     - PurgeCSS for production
     - Critical CSS extraction
   - Environment (development, production, both)
   - Framework integration needed

2. **Install PostCSS packages**:
   - Core PostCSS
   - Selected plugins
   - Build tool integration packages

3. **Generate postcss.config.js** with:
   - Plugin order (IMPORTANT: order matters!)
   - Environment-specific plugins
   - Plugin configuration options
   - Comments explaining each plugin

4. **Set up for different environments**:
   - Development: Fast rebuilds, source maps, helpful warnings
   - Production: Minification, purging, optimization

5. **Configure plugins**:
   - **postcss-preset-env**: Stage 2+ features, autoprefixer settings
   - **postcss-import**: Path resolution
   - **postcss-nesting**: CSS nesting support
   - **cssnano**: Advanced minification settings
   - **@fullhuman/postcss-purgecss**: Content paths and safelist
   - **postcss-custom-properties**: Fallbacks
   - **postcss-reporter**: Error reporting

6. **Integrate with build tool**:
   - Webpack: css-loader and postcss-loader config
   - Vite: vite.config.js CSS options
   - Gulp: gulp-postcss task
   - Package.json scripts

7. **Add**:
   - Example CSS files demonstrating features
   - Build scripts
   - Documentation
   - Performance tips

## Example postcss.config.js

```javascript
/**
 * PostCSS Configuration
 * @description Modern CSS processing pipeline with optimization
 */
module.exports = {
  plugins: [
    // 1. Import resolution
    require('postcss-import')({
      path: ['src/styles', 'node_modules']
    }),

    // 2. CSS Nesting
    require('postcss-nesting'),

    // 3. Future CSS features + Autoprefixer
    require('postcss-preset-env')({
      stage: 2,
      features: {
        'nesting-rules': true,
        'custom-properties': true,
        'custom-media-queries': true,
      },
      autoprefixer: {
        grid: 'autoplace',
        flexbox: 'no-2009',
      },
      browsers: 'last 2 versions, > 1%, not dead',
    }),

    // 4. Production optimization
    process.env.NODE_ENV === 'production' && require('cssnano')({
      preset: ['advanced', {
        discardComments: { removeAll: true },
        reduceIdents: false,
        zindex: false,
      }]
    }),

    // 5. Remove unused CSS (production)
    process.env.NODE_ENV === 'production' && require('@fullhuman/postcss-purgecss')({
      content: ['./src/**/*.{html,ts,tsx,jsx,vue}'],
      safelist: {
        standard: [/^mat-/, /^cdk-/],
        deep: [/data-theme/],
      },
    }),

  ].filter(Boolean) // Remove falsy values
};
```

Generate the complete PostCSS setup with optimized configuration and build integration.
