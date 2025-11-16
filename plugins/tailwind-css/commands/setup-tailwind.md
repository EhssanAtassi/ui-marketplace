---
name: setup-tailwind
description: Set up Tailwind CSS with custom configuration, plugins, and build optimization for your project
---

You are tasked with setting up Tailwind CSS for the user's project.

## Instructions

1. **Ask the user**:
   - Framework (React, Angular, Vue, Next.js, vanilla)
   - Project type (new or existing)
   - Features needed (forms plugin, typography, aspect-ratio, etc.)
   - Custom design requirements (colors, fonts, spacing)
   - Build tool (Vite, Webpack, Parcel, PostCSS)

2. **Install and configure Tailwind**:
   - Install packages (tailwindcss, autoprefixer, postcss)
   - Generate tailwind.config.js
   - Generate postcss.config.js
   - Set up content paths

3. **Create custom configuration** including:
   - Custom color palette
   - Typography scale
   - Spacing system
   - Breakpoints (if custom)
   - Plugins configuration
   - JIT mode settings
   - Theme extension

4. **Set up the CSS entry point**:
   - Create main CSS file with @tailwind directives
   - Add @layer for custom utilities
   - Include custom base styles
   - Add component classes with @apply

5. **Configure for production**:
   - PurgeCSS/content configuration
   - Minification settings
   - Source maps
   - Build scripts

6. **Add framework-specific integration**:
   - React: className management (clsx, classnames)
   - Angular: styles configuration in angular.json
   - Vue: PostCSS integration
   - Next.js: App/Pages router setup

7. **Include**:
   - Example components using Tailwind
   - Custom plugin if needed
   - Dark mode setup
   - Responsive patterns
   - Full documentation

## Example tailwind.config.js

```javascript
/**
 * Tailwind CSS Configuration
 * @description Custom Tailwind configuration with extended theme
 */
module.exports = {
  content: [
    './src/**/*.{html,ts,tsx,jsx,vue}',
    './pages/**/*.{js,ts,jsx,tsx}',
  ],
  darkMode: 'class',
  theme: {
    extend: {
      colors: {
        primary: {
          50: '#eff6ff',
          500: '#3b82f6',
          900: '#1e3a8a',
        },
      },
      fontFamily: {
        sans: ['Inter', 'sans-serif'],
      },
      spacing: {
        '18': '4.5rem',
        '88': '22rem',
      },
    },
  },
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
  ],
};
```

Generate the complete Tailwind setup with all necessary files and configurations.
