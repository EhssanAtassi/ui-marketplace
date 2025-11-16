---
name: generate-sass-architecture
description: Generate advanced SASS/SCSS architecture with modules, mixins, and functions using modern @use/@forward syntax
---

You are tasked with generating a modern SASS/SCSS architecture for the user's project.

## Instructions

1. **Ask the user about their needs**:
   - Project type (component library, design system, application)
   - Features needed (theming, responsive utilities, animations)
   - Naming convention preference (BEM, custom)
   - Module organization preference

2. **Generate modern SASS architecture** using:
   - @use and @forward (NOT @import)
   - Private variables with $_prefix
   - Modular file structure
   - Clear public APIs

3. **Create the following modules**:

   **Config Module** (_config/):
   - Color system with primitives and semantic tokens
   - Typography scale
   - Spacing system
   - Breakpoints
   - Z-index layers

   **Tools Module** (_tools/):
   - Responsive mixins
   - Typography mixins
   - Animation helpers
   - Utility generators
   - Advanced functions

   **Base Module** (_base/):
   - Reset/normalize
   - Typography defaults
   - Element styles

   **Components Module** (_components/):
   - Example components with BEM
   - State management
   - Variants

   **Utilities Module** (_utilities/):
   - Spacing utilities
   - Display utilities
   - Text utilities

4. **Include**:
   - Main entry point with proper @use syntax
   - Barrel files with @forward
   - Configuration with !default
   - Full documentation comments
   - Usage examples

5. **Add build configuration**:
   - sass.config.js or equivalent
   - Package.json scripts
   - PostCSS configuration

## Example Module Structure

```scss
// _config.scss - Barrel file
@forward 'config/colors';
@forward 'config/typography';
@forward 'config/spacing';

// _colors.scss - Color module
@use 'sass:color';
@use 'sass:map';

$_base-colors: (
  'primary': #3b82f6,
  'secondary': #8b5cf6
) !default;

@function get-color($name) {
  @return map.get($_base-colors, $name);
}

// Export public API
$colors: $_base-colors;
```

Generate the complete architecture with all files and proper modern SASS patterns.
