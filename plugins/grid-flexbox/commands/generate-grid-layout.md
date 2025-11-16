---
name: generate-grid-layout
description: Generate a responsive grid layout system using CSS Grid and/or Flexbox
---

You are tasked with generating a responsive grid layout system for the user.

## Instructions

1. **Ask the user**:
   - Layout type preference (CSS Grid, Flexbox, or hybrid)
   - Grid columns (12-column, 16-column, custom)
   - Breakpoints (mobile, tablet, desktop, custom)
   - Features needed:
     - Responsive columns
     - Gap/gutter system
     - Nested grids
     - Grid areas for complex layouts
     - Alignment utilities
     - Order utilities
   - Naming convention (BEM, utility classes, custom)

2. **Generate the grid system** with:
   - Base grid container
   - Column/item classes
   - Responsive modifiers
   - Gap/spacing utilities
   - Alignment utilities

3. **Create responsive patterns**:
   - Mobile-first approach
   - Breakpoint-specific classes
   - Auto-fit/auto-fill patterns (for CSS Grid)
   - Flexbox wrapping patterns

4. **Include advanced features** (if requested):
   - Grid template areas for named layouts
   - Subgrid support
   - Container queries
   - Aspect ratio utilities
   - Order/flex-order utilities

5. **Generate utilities** for:
   - Gap spacing (consistent with design system)
   - Alignment (align-items, justify-content)
   - Column spans
   - Row spans
   - Auto-flow patterns

6. **Provide examples**:
   - Common layouts (2-column, 3-column, sidebar, holy grail)
   - Responsive gallery
   - Dashboard layout
   - Card grid
   - Complex nested grids

## Example CSS Grid System

```scss
/**
 * Responsive CSS Grid System
 * @description Mobile-first 12-column grid with flexible gaps
 */

// Grid container
.grid {
  display: grid;
  grid-template-columns: repeat(12, 1fr);
  gap: var(--grid-gap, 1rem);
  width: 100%;
}

// Auto-responsive grid (no media queries needed)
.grid-auto {
  display: grid;
  grid-template-columns: repeat(auto-fit, minmax(min(300px, 100%), 1fr));
  gap: var(--grid-gap, 1rem);
}

// Column spans (1-12)
@for $i from 1 through 12 {
  .col-#{$i} {
    grid-column: span $i;
  }
}

// Responsive column spans
@media (min-width: 768px) {
  @for $i from 1 through 12 {
    .md\\:col-#{$i} {
      grid-column: span $i;
    }
  }
}

// Grid gaps
.gap-sm { gap: 0.5rem; }
.gap-md { gap: 1rem; }
.gap-lg { gap: 2rem; }

// Alignment
.items-start { align-items: start; }
.items-center { align-items: center; }
.items-end { align-items: end; }

.justify-start { justify-content: start; }
.justify-center { justify-content: center; }
.justify-between { justify-content: space-between; }
```

Generate the complete grid system with documentation and usage examples.
