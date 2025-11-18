---
description: Generate complete enterprise CSS architecture with ITCSS layers, design tokens, and governance framework
---

I'll help you set up a production-ready enterprise CSS architecture for large-scale applications.

## What This Generates

A complete CSS architecture including:
- ITCSS 7-layer structure
- Design token system (3-tier)
- Component library foundation
- Governance framework
- Build pipeline configuration
- Documentation templates
- Stylelint configuration

## Architecture Types

### 1. Monorepo Architecture
Multi-application environment with shared design system.

**What I'll need:**
- Number of applications
- Shared component requirements
- Build tool preference (Webpack, Vite, etc.)
- Package manager (npm, yarn, pnpm)

**What you'll get:**
- Shared design system package
- Application-specific overrides
- Build configuration
- Lerna/Nx monorepo setup

### 2. Standalone Design System
Independent design system package.

**What I'll need:**
- Target frameworks (React, Vue, Angular, etc.)
- Distribution format (CSS, SCSS, JS)
- Documentation platform (Storybook, Docusaurus)

**What you'll get:**
- Complete design system package
- Component documentation
- Usage examples
- npm publishing configuration

### 3. Enterprise Application
Single large application with internal design system.

**What I'll need:**
- Application framework
- Theming requirements
- Browser support matrix
- Performance budgets

**What you'll get:**
- ITCSS folder structure
- Design token files
- Component scaffolds
- Build configuration

### 4. Migration Architecture
Gradual migration from legacy CSS.

**What I'll need:**
- Current CSS methodology
- Migration timeline
- Breaking change tolerance
- Team size

**What you'll get:**
- Compatibility layer
- Migration scripts (codemods)
- Deprecation strategy
- Rollout plan

## Generated Structure

### ITCSS Layer Structure

```
src/
├── settings/           # Layer 1: Variables & config
│   ├── _colors.scss
│   ├── _typography.scss
│   ├── _spacing.scss
│   ├── _breakpoints.scss
│   └── _tokens.scss
│
├── tools/              # Layer 2: Mixins & functions
│   ├── _mixins.scss
│   ├── _functions.scss
│   └── _placeholders.scss
│
├── generic/            # Layer 3: Reset & normalize
│   ├── _reset.scss
│   └── _box-sizing.scss
│
├── elements/           # Layer 4: Base HTML elements
│   ├── _headings.scss
│   ├── _links.scss
│   ├── _forms.scss
│   └── _tables.scss
│
├── objects/            # Layer 5: Layout patterns
│   ├── _container.scss
│   ├── _grid.scss
│   ├── _media.scss
│   └── _stack.scss
│
├── components/         # Layer 6: UI components
│   ├── core/
│   │   ├── _button.scss
│   │   ├── _input.scss
│   │   └── _card.scss
│   ├── layout/
│   │   ├── _header.scss
│   │   └── _sidebar.scss
│   └── navigation/
│       ├── _nav.scss
│       └── _tabs.scss
│
├── utilities/          # Layer 7: Helper classes
│   ├── _spacing.scss
│   ├── _typography.scss
│   └── _visibility.scss
│
└── main.scss           # Main entry point
```

### Design Token Files

**tokens/_colors.scss**
```scss
/**
 * Color Design Tokens
 * @tier-1 Primitive colors (raw values)
 * @tier-2 Semantic colors (purpose-driven)
 * @tier-3 Component tokens (specific use)
 */

// Tier 1: Primitive Colors
$primitive-colors: (
  'blue-500': #3b82f6,
  'blue-600': #2563eb,
  'gray-100': #f3f4f6,
  'gray-500': #6b7280,
  'gray-900': #111827
);

// Tier 2: Semantic Colors
$semantic-colors: (
  'primary': map-get($primitive-colors, 'blue-600'),
  'text-primary': map-get($primitive-colors, 'gray-900'),
  'surface': #ffffff
);

// Tier 3: Component Tokens
$component-tokens: (
  'button-primary-bg': map-get($semantic-colors, 'primary'),
  'card-background': map-get($semantic-colors, 'surface')
);

// CSS Custom Properties Export
:root {
  @each $name, $value in $semantic-colors {
    --color-#{$name}: #{$value};
  }
}
```

### Governance Files

**CSS_GOVERNANCE.md**
```markdown
# CSS Governance Framework

## Decision Making
- RFC process for major changes
- Design System Council approval
- 2-week review period

## Code Standards
- Stylelint compliance required
- WCAG 2.1 AA minimum
- Performance budgets enforced
- Browser support matrix

## Review Process
- 2 peer approvals required
- Design review for new components
- Accessibility audit for interactive elements
```

**.stylelintrc.json**
```json
{
  "extends": "stylelint-config-standard-scss",
  "plugins": [
    "stylelint-selector-bem-pattern"
  ],
  "rules": {
    "selector-max-id": 0,
    "selector-max-specificity": "0,3,0",
    "max-nesting-depth": 3,
    "selector-class-pattern": "^[a-z]([a-z0-9-]+)?(__([a-z0-9]+-?)+)?(--([a-z0-9]+-?)+){0,2}$"
  }
}
```

### Build Configuration

**webpack.config.js** (Webpack example)
```javascript
/**
 * Enterprise CSS Build Configuration
 */
const MiniCssExtractPlugin = require('mini-css-extract-plugin');
const CssMinimizerPlugin = require('css-minimizer-webpack-plugin');

module.exports = {
  module: {
    rules: [
      {
        test: /\.scss$/,
        use: [
          MiniCssExtractPlugin.loader,
          'css-loader',
          'postcss-loader',
          'sass-loader'
        ]
      }
    ]
  },
  plugins: [
    new MiniCssExtractPlugin({
      filename: '[name].[contenthash].css'
    })
  ],
  optimization: {
    minimizer: [new CssMinimizerPlugin()]
  }
};
```

### Documentation Templates

**Component Documentation Template:**
```markdown
# Component Name

## Description
Brief component description

## Usage
\`\`\`html
<button class="c-button c-button--primary">
  Click me
</button>
\`\`\`

## API
- **Variants**: primary, secondary, outlined
- **Sizes**: small, medium, large
- **States**: disabled, loading

## Accessibility
- WCAG 2.1 AA compliant
- Keyboard navigable
- Screen reader friendly

## Browser Support
- Chrome 90+
- Firefox 88+
- Safari 14+
- Edge 90+
```

## Quick Generation

Just tell me:
"Generate a [architecture type] CSS architecture for [framework/use case]"

**Examples:**
- "Generate a monorepo architecture for 3 Angular applications"
- "Generate a standalone design system for React with Storybook"
- "Generate an enterprise application architecture with dark mode support"
- "Generate a migration architecture from Bootstrap to custom CSS"

## Custom Generation

Provide details:
- **Project type**: Monorepo / Standalone / Enterprise / Migration
- **Framework**: React / Vue / Angular / Vanilla
- **Team size**: 1-5 / 5-20 / 20+
- **Requirements**: Theming, i18n, accessibility level
- **Build tool**: Webpack / Vite / Rollup / Parcel
- **Documentation**: Storybook / Docusaurus / Custom

## What Happens Next

1. I'll analyze your requirements
2. Generate the complete file structure
3. Create all configuration files
4. Provide setup instructions
5. Include best practices guide
6. Add migration path (if applicable)

Let me know what kind of architecture you'd like to generate!
