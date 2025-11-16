---
name: token-patterns
description: Design token patterns and naming conventions. Use when searching for token architecture, naming strategies, or design system patterns.
---

# Design Token Patterns & Naming Conventions

A comprehensive reference guide for design token patterns, naming conventions, transformation strategies, and platform-specific formats. This skill provides architecture guidance for building scalable, maintainable design systems with 30+ searchable token patterns and real-world examples.

## Table of Contents

1. [Token Naming Conventions](#token-naming-conventions)
2. [CTI Pattern (Category-Type-Item)](#cti-pattern-category-type-item)
3. [Semantic Naming Strategy](#semantic-naming-strategy)
4. [Token Categories Reference](#token-categories-reference)
5. [Token Transformation Patterns](#token-transformation-patterns)
6. [Platform-Specific Formats](#platform-specific-formats)
7. [Token Inheritance Patterns](#token-inheritance-patterns)
8. [Common Token Structures](#common-token-structures)
9. [Token Composition Patterns](#token-composition-patterns)
10. [Theme Variants & Scales](#theme-variants--scales)
11. [Token Math & Calculations](#token-math--calculations)
12. [Documentation & Comments](#documentation--comments)
13. [Advanced Patterns](#advanced-patterns)
14. [Quick Reference Tables](#quick-reference-tables)
15. [Searchable Token Index](#searchable-token-index)

---

## Token Naming Conventions

### 1. BEM-Inspired Token Names

**Pattern**: `[block]__[element]--[modifier]`

```json
{
  "color__button--primary": "#0070F3",
  "color__button--secondary": "#666666",
  "spacing__button--large": "16px",
  "spacing__button--small": "8px"
}
```

**Use Cases**:
- Component-specific tokens
- Variant management
- State-based overrides

---

## CTI Pattern (Category-Type-Item)

The CTI (Category-Type-Item) pattern is the industry-standard approach for token naming. It provides hierarchical, searchable, and maintainable naming across all platforms.

### 2. Basic CTI Structure

**Pattern**: `{category}-{type}-{item}`

```json
{
  "color-background-primary": "#FFFFFF",
  "color-background-secondary": "#F5F5F5",
  "color-text-primary": "#000000",
  "color-text-secondary": "#666666",
  "color-border-light": "#EEEEEE",
  "color-border-dark": "#CCCCCC"
}
```

**Components**:
- **Category**: Defines the design aspect (color, spacing, typography, etc.)
- **Type**: Specifies the purpose or usage (background, text, border, etc.)
- **Item**: Identifies the specific variant or scale (primary, secondary, small, large, etc.)

### 3. Extended CTI with Multiple Levels

**Pattern**: `{category}-{type}-{subtype}-{item}`

```json
{
  "color-text-interactive-primary": "#0070F3",
  "color-text-interactive-hover": "#005BCB",
  "color-text-interactive-disabled": "#CCCCCC",
  "color-background-surface-elevated": "#FAFAFA",
  "color-background-surface-overlay": "rgba(0, 0, 0, 0.5)"
}
```

### 4. Numbered Scale Variation

**Pattern**: `{category}-{type}-{item}-{number}`

```json
{
  "color-gray-50": "#FAFAFA",
  "color-gray-100": "#F5F5F5",
  "color-gray-200": "#EEEEEE",
  "color-gray-300": "#E0E0E0",
  "color-gray-400": "#BDBDBD",
  "color-gray-500": "#9E9E9E",
  "color-gray-600": "#757575",
  "color-gray-700": "#616161",
  "color-gray-800": "#424242",
  "color-gray-900": "#212121"
}
```

---

## Semantic Naming Strategy

Semantic naming focuses on the *purpose* rather than the *appearance* of tokens, making designs more flexible and maintainable.

### 5. Purpose-Based Semantic Names

**Pattern**: Describe *what* the token is used for, not *what* it looks like

```json
{
  "color-action-primary": "#0070F3",
  "color-action-secondary": "#CCCCCC",
  "color-feedback-success": "#00B341",
  "color-feedback-warning": "#FFA500",
  "color-feedback-error": "#FF4444",
  "color-feedback-info": "#0099FF",
  "color-border-subtle": "#E0E0E0",
  "color-border-prominent": "#999999"
}
```

**Benefits**:
- Easier to update themes (change once, propagate everywhere)
- Better for accessibility and WCAG compliance
- Scales well across light/dark modes

### 6. State-Based Semantic Naming

```json
{
  "color-button-default-foreground": "#FFFFFF",
  "color-button-default-background": "#0070F3",
  "color-button-hover-background": "#0061E8",
  "color-button-active-background": "#0051CC",
  "color-button-disabled-foreground": "#CCCCCC",
  "color-button-disabled-background": "#F5F5F5"
}
```

### 7. Role-Based Semantic Naming

```json
{
  "color-accent": "#0070F3",
  "color-accent-hover": "#005BCB",
  "color-neutral-primary": "#000000",
  "color-neutral-secondary": "#666666",
  "color-neutral-tertiary": "#AAAAAA",
  "color-positive": "#00B341",
  "color-negative": "#FF4444"
}
```

---

## Token Categories Reference

### 8. Color Tokens - Comprehensive Structure

```json
{
  "color-brand-primary": "#0070F3",
  "color-brand-secondary": "#FF6B35",
  "color-status-success": "#00B341",
  "color-status-warning": "#FFA500",
  "color-status-error": "#FF4444",
  "color-status-info": "#0099FF",
  "color-surface-primary": "#FFFFFF",
  "color-surface-secondary": "#F5F5F5",
  "color-surface-tertiary": "#EEEEEE",
  "color-surface-inverse": "#1F1F1F",
  "color-text-primary": "#000000",
  "color-text-secondary": "#666666",
  "color-text-tertiary": "#999999",
  "color-text-inverse": "#FFFFFF",
  "color-border-subtle": "#E0E0E0",
  "color-border-medium": "#BDBDBD",
  "color-border-strong": "#666666",
  "color-overlay-light": "rgba(255, 255, 255, 0.8)",
  "color-overlay-dark": "rgba(0, 0, 0, 0.5)"
}
```

### 9. Typography Tokens

```json
{
  "typography-font-family-base": "system-ui, -apple-system, sans-serif",
  "typography-font-family-heading": "Georgia, serif",
  "typography-font-family-mono": "Menlo, monospace",
  "typography-font-size-xs": "12px",
  "typography-font-size-sm": "14px",
  "typography-font-size-base": "16px",
  "typography-font-size-lg": "18px",
  "typography-font-size-xl": "20px",
  "typography-font-size-2xl": "24px",
  "typography-font-size-3xl": "32px",
  "typography-font-weight-light": "300",
  "typography-font-weight-regular": "400",
  "typography-font-weight-medium": "500",
  "typography-font-weight-semibold": "600",
  "typography-font-weight-bold": "700",
  "typography-line-height-tight": "1.2",
  "typography-line-height-normal": "1.5",
  "typography-line-height-relaxed": "1.8",
  "typography-letter-spacing-tight": "-0.02em",
  "typography-letter-spacing-normal": "0em",
  "typography-letter-spacing-wide": "0.05em"
}
```

### 10. Spacing Tokens

```json
{
  "spacing-0": "0",
  "spacing-xs": "4px",
  "spacing-sm": "8px",
  "spacing-md": "16px",
  "spacing-lg": "24px",
  "spacing-xl": "32px",
  "spacing-2xl": "48px",
  "spacing-3xl": "64px",
  "spacing-4xl": "96px",
  "spacing-gutter-sm": "8px",
  "spacing-gutter-md": "16px",
  "spacing-gutter-lg": "24px",
  "spacing-inset-xs": "4px",
  "spacing-inset-sm": "8px",
  "spacing-inset-md": "16px",
  "spacing-inset-lg": "24px",
  "spacing-stack-xs": "4px",
  "spacing-stack-sm": "8px",
  "spacing-stack-md": "16px"
}
```

### 11. Sizing Tokens

```json
{
  "sizing-xs": "64px",
  "sizing-sm": "128px",
  "sizing-md": "256px",
  "sizing-lg": "512px",
  "sizing-xl": "1024px",
  "sizing-auto": "auto",
  "sizing-full": "100%",
  "sizing-min": "min-content",
  "sizing-max": "max-content",
  "sizing-fit": "fit-content"
}
```

### 12. Border Tokens

```json
{
  "border-radius-0": "0",
  "border-radius-sm": "2px",
  "border-radius-md": "4px",
  "border-radius-lg": "8px",
  "border-radius-xl": "12px",
  "border-radius-2xl": "16px",
  "border-radius-full": "9999px",
  "border-width-thin": "1px",
  "border-width-medium": "2px",
  "border-width-thick": "4px",
  "border-style-solid": "solid",
  "border-style-dashed": "dashed",
  "border-style-dotted": "dotted"
}
```

### 13. Elevation/Shadow Tokens

```json
{
  "elevation-shadow-xs": "0 1px 2px rgba(0, 0, 0, 0.05)",
  "elevation-shadow-sm": "0 1px 3px rgba(0, 0, 0, 0.1)",
  "elevation-shadow-md": "0 4px 6px rgba(0, 0, 0, 0.1)",
  "elevation-shadow-lg": "0 10px 15px rgba(0, 0, 0, 0.1)",
  "elevation-shadow-xl": "0 20px 25px rgba(0, 0, 0, 0.1)",
  "elevation-shadow-2xl": "0 25px 50px rgba(0, 0, 0, 0.15)",
  "elevation-z-index-dropdown": "1000",
  "elevation-z-index-sticky": "500",
  "elevation-z-index-fixed": "1000",
  "elevation-z-index-modal": "1100"
}
```

### 14. Animation/Motion Tokens

```json
{
  "motion-duration-fast": "100ms",
  "motion-duration-base": "200ms",
  "motion-duration-slow": "300ms",
  "motion-easing-linear": "linear",
  "motion-easing-ease-in": "cubic-bezier(0.4, 0, 1, 1)",
  "motion-easing-ease-out": "cubic-bezier(0, 0, 0.2, 1)",
  "motion-easing-ease-in-out": "cubic-bezier(0.4, 0, 0.2, 1)",
  "motion-transition-fast": "all 100ms ease-in-out",
  "motion-transition-base": "all 200ms ease-in-out",
  "motion-transition-slow": "all 300ms ease-in-out"
}
```

### 15. Opacity Tokens

```json
{
  "opacity-0": "0",
  "opacity-10": "0.1",
  "opacity-20": "0.2",
  "opacity-30": "0.3",
  "opacity-40": "0.4",
  "opacity-50": "0.5",
  "opacity-60": "0.6",
  "opacity-70": "0.7",
  "opacity-80": "0.8",
  "opacity-90": "0.9",
  "opacity-100": "1"
}
```

---

## Token Transformation Patterns

Token transformations convert design tokens into platform-specific outputs. This is critical for supporting web, mobile, and other platforms.

### 16. Token Transform to CSS Custom Properties

**Input** (JSON):
```json
{
  "color-primary": "#0070F3",
  "spacing-md": "16px"
}
```

**Output** (CSS):
```css
:root {
  --color-primary: #0070F3;
  --spacing-md: 16px;
}

.component {
  background-color: var(--color-primary);
  padding: var(--spacing-md);
}
```

### 17. Token Transform to SCSS Variables

**Input** (JSON):
```json
{
  "color-primary": "#0070F3",
  "spacing-md": "16px"
}
```

**Output** (SCSS):
```scss
$color-primary: #0070F3;
$spacing-md: 16px;

.component {
  background-color: $color-primary;
  padding: $spacing-md;
}
```

### 18. Token Transform to TypeScript Types

**Input** (JSON):
```json
{
  "color-primary": "#0070F3",
  "spacing-md": "16px"
}
```

**Output** (TypeScript):
```typescript
export const tokens = {
  color: {
    primary: '#0070F3'
  },
  spacing: {
    md: '16px'
  }
} as const;

export type Tokens = typeof tokens;

// Usage
const bgColor: string = tokens.color.primary;
const padding: string = tokens.spacing.md;
```

### 19. Token Transform to JavaScript Objects

```javascript
// Tokens object structure
export const tokens = {
  color: {
    brand: {
      primary: '#0070F3',
      secondary: '#FF6B35'
    },
    status: {
      success: '#00B341',
      error: '#FF4444'
    }
  },
  spacing: {
    xs: '4px',
    sm: '8px',
    md: '16px'
  }
};

// Access
tokens.color.brand.primary // '#0070F3'
tokens.spacing.md // '16px'
```

### 20. Token Transform to Swift (iOS)

```swift
struct DesignTokens {
    struct Colors {
        static let primary = UIColor(hex: "#0070F3")
        static let secondary = UIColor(hex: "#FF6B35")
    }

    struct Spacing {
        static let xs: CGFloat = 4
        static let sm: CGFloat = 8
        static let md: CGFloat = 16
    }
}

// Usage
let primaryColor = DesignTokens.Colors.primary
let padding = DesignTokens.Spacing.md
```

### 21. Token Transform to Kotlin (Android)

```kotlin
object DesignTokens {
    object Colors {
        const val Primary = "#0070F3"
        const val Secondary = "#FF6B35"
    }

    object Spacing {
        const val Xs = 4
        const val Sm = 8
        const val Md = 16
    }
}

// Usage
val primaryColor = DesignTokens.Colors.Primary
val padding = DesignTokens.Spacing.Md
```

### 22. Token Transform to JSON Schema

```json
{
  "$schema": "http://json-schema.org/draft-07/schema#",
  "type": "object",
  "properties": {
    "color": {
      "type": "object",
      "properties": {
        "primary": {
          "type": "string",
          "pattern": "^#[0-9A-F]{6}$"
        }
      }
    },
    "spacing": {
      "type": "object",
      "properties": {
        "md": {
          "type": "string",
          "pattern": "^[0-9]+(px|rem|em)$"
        }
      }
    }
  }
}
```

---

## Platform-Specific Formats

### 23. Web CSS Custom Properties Format

```css
/* Light Mode */
:root {
  --color-primary: #0070F3;
  --color-text: #000000;
  --spacing-md: 16px;
  --border-radius-md: 4px;
}

/* Dark Mode */
@media (prefers-color-scheme: dark) {
  :root {
    --color-primary: #0088FF;
    --color-text: #FFFFFF;
  }
}

/* Usage */
.button {
  background-color: var(--color-primary);
  color: var(--color-text);
  padding: var(--spacing-md);
  border-radius: var(--border-radius-md);
}
```

### 24. Tailwind Configuration Format

```javascript
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: '#0070F3',
        secondary: '#FF6B35',
        gray: {
          50: '#FAFAFA',
          900: '#212121'
        }
      },
      spacing: {
        xs: '4px',
        sm: '8px',
        md: '16px'
      },
      fontSize: {
        xs: '12px',
        sm: '14px',
        base: '16px'
      },
      borderRadius: {
        sm: '2px',
        md: '4px',
        lg: '8px'
      }
    }
  }
};
```

### 25. Material Design Format

```typescript
import { createMuiTheme } from '@mui/material/styles';

const theme = createMuiTheme({
  palette: {
    primary: {
      main: '#0070F3',
      light: '#0088FF',
      dark: '#0051CC'
    },
    secondary: {
      main: '#FF6B35'
    },
    success: {
      main: '#00B341'
    }
  },
  spacing: 8,
  typography: {
    fontFamily: 'system-ui',
    fontSize: 16
  }
});
```

### 26. Figma Design Tokens Format

```json
{
  "colors": {
    "brand": {
      "primary": {
        "value": "#0070F3",
        "type": "color",
        "description": "Primary brand color"
      }
    }
  },
  "spacing": {
    "md": {
      "value": "16px",
      "type": "dimension",
      "description": "Medium spacing scale"
    }
  }
}
```

---

## Token Inheritance Patterns

### 27. Single-Level Inheritance

```json
{
  "base-color-primary": "#0070F3",
  "color-primary": "{base-color-primary}",
  "color-button-primary": "{color-primary}"
}
```

### 28. Multi-Level Semantic Inheritance

```json
{
  "base-blue-500": "#0070F3",
  "color-action-primary": "{base-blue-500}",
  "color-button-primary": "{color-action-primary}",
  "color-button-hover": "color-action-primary-hover"
}
```

### 29. Contextual Inheritance

```json
{
  "base-neutral": "#000000",
  "color-text": "{base-neutral}",
  "color-text-button": "{color-text}",
  "color-text-button-disabled": "opacity({color-text-button}, 0.5)"
}
```

### 30. Theme-Based Inheritance

```json
{
  "light": {
    "base-bg": "#FFFFFF",
    "color-bg-primary": "{base-bg}",
    "color-text-primary": "#000000"
  },
  "dark": {
    "base-bg": "#1F1F1F",
    "color-bg-primary": "{base-bg}",
    "color-text-primary": "#FFFFFF"
  }
}
```

---

## Common Token Structures

### 31. Flat Token Structure

**Best for**: Simple applications, direct CSS variable mapping

```json
{
  "color-primary": "#0070F3",
  "color-secondary": "#FF6B35",
  "spacing-sm": "8px",
  "spacing-md": "16px"
}
```

### 32. Nested/Hierarchical Token Structure

**Best for**: Complex design systems, component-based architectures

```json
{
  "color": {
    "brand": {
      "primary": "#0070F3",
      "secondary": "#FF6B35"
    },
    "status": {
      "success": "#00B341",
      "error": "#FF4444"
    }
  },
  "spacing": {
    "scale": {
      "xs": "4px",
      "sm": "8px"
    }
  }
}
```

### 33. Component Token Structure

**Best for**: Component libraries, design systems

```json
{
  "button": {
    "primary": {
      "background": "#0070F3",
      "foreground": "#FFFFFF",
      "hover-background": "#005BCB",
      "padding": "16px"
    },
    "secondary": {
      "background": "#F5F5F5",
      "foreground": "#000000"
    }
  },
  "input": {
    "background": "#FFFFFF",
    "border": "#CCCCCC",
    "padding": "12px"
  }
}
```

---

## Token Composition Patterns

### 34. Shadow Composition

```json
{
  "shadow-sm": {
    "x": "0",
    "y": "1px",
    "blur": "3px",
    "spread": "0",
    "color": "rgba(0, 0, 0, 0.1)"
  },
  "shadow-md": {
    "x": "0",
    "y": "4px",
    "blur": "6px",
    "spread": "0",
    "color": "rgba(0, 0, 0, 0.1)"
  }
}
```

### 35. Typography Composition

```json
{
  "typography-heading-1": {
    "font-family": "{typography-font-family-heading}",
    "font-size": "32px",
    "font-weight": "700",
    "line-height": "1.2",
    "letter-spacing": "-0.02em"
  },
  "typography-body": {
    "font-family": "{typography-font-family-base}",
    "font-size": "16px",
    "font-weight": "400",
    "line-height": "1.5"
  }
}
```

### 36. Border Composition

```json
{
  "border-subtle": {
    "width": "1px",
    "style": "solid",
    "color": "#E0E0E0"
  },
  "border-strong": {
    "width": "2px",
    "style": "solid",
    "color": "#666666"
  }
}
```

---

## Theme Variants & Scales

### 37. Color Scale Variants

```json
{
  "color-gray": {
    "50": "#FAFAFA",
    "100": "#F5F5F5",
    "200": "#EEEEEE",
    "300": "#E0E0E0",
    "400": "#BDBDBD",
    "500": "#9E9E9E",
    "600": "#757575",
    "700": "#616161",
    "800": "#424242",
    "900": "#212121"
  }
}
```

### 38. Spacing Scale Variants

```json
{
  "spacing-scale": {
    "2xs": "2px",
    "xs": "4px",
    "sm": "8px",
    "md": "16px",
    "lg": "24px",
    "xl": "32px",
    "2xl": "48px",
    "3xl": "64px"
  }
}
```

### 39. Responsive Variants

```json
{
  "spacing-gutter": {
    "mobile": "12px",
    "tablet": "16px",
    "desktop": "24px"
  },
  "font-size-body": {
    "mobile": "14px",
    "tablet": "16px",
    "desktop": "16px"
  }
}
```

---

## Token Math & Calculations

### 40. Calculated Token Values

```json
{
  "spacing-base": "4px",
  "spacing-sm": "calc({spacing-base} * 2)",
  "spacing-md": "calc({spacing-base} * 4)",
  "spacing-lg": "calc({spacing-base} * 6)",
  "color-opacity-50": "rgba({color-primary}, 0.5)"
}
```

### 41. Relative Sizing

```json
{
  "font-size-base": "16px",
  "font-size-sm": "calc({font-size-base} * 0.875)",
  "font-size-lg": "calc({font-size-base} * 1.125)",
  "line-height-relaxed": "calc({font-size-base} * 1.8)"
}
```

---

## Documentation & Comments

### 42. Documented Token Structure

```json
{
  "color-primary": {
    "value": "#0070F3",
    "type": "color",
    "category": "Brand Colors",
    "description": "Primary action color for buttons, links, and interactive elements",
    "usage": ["buttons", "links", "focus-states"],
    "deprecated": false,
    "aliases": ["color-action", "color-interactive"]
  },
  "spacing-md": {
    "value": "16px",
    "type": "dimension",
    "category": "Spacing Scale",
    "description": "Medium spacing unit - standard padding for components",
    "usage": ["padding", "margin", "gap"],
    "deprecated": false,
    "relatedTokens": ["spacing-sm", "spacing-lg"]
  }
}
```

---

## Advanced Patterns

### 43. Conditional Token Application

```json
{
  "tokens": {
    "light": {
      "color-bg": "#FFFFFF",
      "color-text": "#000000"
    },
    "dark": {
      "color-bg": "#1F1F1F",
      "color-text": "#FFFFFF"
    },
    "highContrast": {
      "color-bg": "#000000",
      "color-text": "#FFFF00"
    }
  }
}
```

### 44. Token Aliases & References

```json
{
  "color-primary": "#0070F3",
  "color-brand": "{color-primary}",
  "color-interactive": "{color-primary}",
  "color-link": "{color-primary}",
  "color-focus": "{color-primary}"
}
```

### 45. Platform-Specific Token Overrides

```json
{
  "tokens": {
    "base": {
      "font-size-body": "16px"
    },
    "web": {
      "font-size-body": "16px"
    },
    "ios": {
      "font-size-body": "17px"
    },
    "android": {
      "font-size-body": "18px"
    }
  }
}
```

---

## Quick Reference Tables

### Token Category Quick Reference

| Category | Type | Examples | Purpose |
|----------|------|----------|---------|
| **Color** | Semantic | primary, secondary, success, error | Brand identity, status, feedback |
| **Spacing** | Scale | xs, sm, md, lg, xl | Padding, margin, gaps |
| **Typography** | Font/Scale | font-family, font-size, font-weight | Text styling, hierarchy |
| **Border** | Radius/Style | radius, width, style | Component corners, dividers |
| **Elevation** | Shadow/Z-index | shadow-sm, z-index-modal | Depth, layering |
| **Motion** | Duration/Easing | duration-fast, easing-ease-out | Transitions, animations |
| **Opacity** | Alpha | 0-100 | Transparency, visibility |

### Common Token Scales

| Scale | Values | Use Case |
|-------|--------|----------|
| **Color** | 50-900 (step 50) | Grayscale, brand colors |
| **Spacing** | xs, sm, md, lg, xl, 2xl | Padding, margin, gaps |
| **Font Size** | xs, sm, base, lg, xl, 2xl, 3xl | Typography hierarchy |
| **Border Radius** | 0, sm, md, lg, xl, 2xl, full | Component corners |
| **Shadow** | xs, sm, md, lg, xl, 2xl | Depth levels |
| **Z-index** | 1-1100 | Layer management |

### State Variants

| State | Token Suffix | Common Values |
|-------|--------------|----------------|
| Default | `-default` | Primary color, standard spacing |
| Hover | `-hover` | Darker shade, lighter background |
| Active | `-active` | Darker background, pressed effect |
| Disabled | `-disabled` | Reduced opacity, gray color |
| Focus | `-focus` | Outline style, bright color |

---

## Searchable Token Index

### A - Accessibility, Animation
- `color-focus` - Focus indicator color
- `color-focus-visible` - Keyboard focus color
- `motion-duration-fast` - Quick animation duration
- `motion-duration-base` - Standard animation duration
- `motion-easing-ease-in-out` - Smooth easing function

### B - Background, Border, Brand
- `color-background-primary` - Primary background
- `color-background-secondary` - Secondary background
- `color-border-light` - Light border color
- `color-border-dark` - Dark border color
- `color-brand-primary` - Primary brand color

### C - Color, Contrast, Component
- `color-text-primary` - Primary text color
- `color-text-secondary` - Secondary text color
- `color-status-success` - Success status color
- `color-status-error` - Error status color
- `color-status-warning` - Warning status color

### D - Disabled, Depth, Display
- `color-disabled-foreground` - Disabled text color
- `color-disabled-background` - Disabled background
- `elevation-shadow-sm` - Small shadow
- `elevation-shadow-md` - Medium shadow

### E - Elevation, Error, Emphasis
- `elevation-z-index-dropdown` - Dropdown z-index
- `elevation-z-index-modal` - Modal z-index
- `color-feedback-error` - Error feedback color

### F - Focus, Font, Foreground
- `typography-font-size-base` - Base font size
- `typography-font-family-base` - Base font family
- `typography-font-weight-bold` - Bold weight

### G - Grayscale, Gutter, Gradient
- `color-gray-50` - Lightest gray
- `color-gray-900` - Darkest gray
- `spacing-gutter-md` - Medium gutter spacing

### H - Heading, Hover, Height
- `typography-font-size-heading` - Heading font size
- `color-hover-background` - Hover background

### I - Info, Input, Inset
- `color-status-info` - Info status color
- `spacing-inset-md` - Inset padding

### L - Line, Letter, Light
- `typography-line-height-normal` - Normal line height
- `typography-letter-spacing-normal` - Normal letter spacing

### M - Margin, Motion, Medium
- `spacing-md` - Medium spacing
- `motion-transition-base` - Base transition

### N - Neutral, Notification
- `color-neutral-primary` - Primary neutral color

### O - Opacity, Overlay, Outline
- `opacity-50` - 50% opacity
- `color-overlay-dark` - Dark overlay color

### P - Padding, Primary, Positive
- `spacing-padding-md` - Medium padding
- `color-positive` - Positive/success color

### R - Radius, Role
- `border-radius-md` - Medium border radius

### S - Spacing, Shadow, Surface, Status
- `spacing-sm` - Small spacing
- `elevation-shadow-lg` - Large shadow
- `color-surface-primary` - Primary surface
- `color-status-success` - Success status

### T - Text, Typography, Transition
- `color-text-primary` - Primary text
- `typography-font-size-lg` - Large font size
- `motion-transition-slow` - Slow transition

### U - UI, Utility
- UI token patterns vary by system

### V - Variant
- Variant tokens vary by component

### W - Warning, Weight
- `color-status-warning` - Warning status color
- `typography-font-weight-semibold` - Semibold weight

### Z - Z-index
- `elevation-z-index-sticky` - Sticky z-index
- `elevation-z-index-modal` - Modal z-index

---

## Best Practices & Recommendations

### Naming Guidelines

1. **Use lowercase with hyphens**: `color-primary-hover`
2. **Be specific**: `color-button-primary` better than `color-blue`
3. **Avoid color names**: Use semantic names instead
4. **Consistent depth**: Limit nesting levels (3-4 recommended)
5. **Group by purpose**: Category > Type > Item pattern
6. **Use scales**: 50, 100, 200... or xs, sm, md, lg, xl
7. **Include state variants**: `-default`, `-hover`, `-active`, `-disabled`

### Organization Guidelines

1. **Group by category**: Colors together, spacing together
2. **Create base tokens**: Foundation for semantic tokens
3. **Use aliases**: Link common tokens to single source
4. **Document usage**: Add descriptions and examples
5. **Version tokens**: Track changes across design iterations
6. **Test coverage**: Ensure all tokens are used

### Maintenance Guidelines

1. **Keep tokens DRY**: No duplicate values
2. **Regular audits**: Remove unused tokens
3. **Version control**: Track all changes
4. **Testing**: Validate transformations
5. **Documentation**: Keep docs up-to-date
6. **Team alignment**: Use consistent naming

---

## Related Resources

- Token.studio (https://token.studio/) - Token management platform
- Style Dictionary (https://amzn.github.io/style-dictionary/) - Token transformation tool
- Tokens.json Specification - JSON schema for design tokens
- W3C Design Tokens Community Group - Industry standards
- Design System Handbook - Token fundamentals

---

*Last Updated: 2024 | For design system architects, token managers, and design ops professionals*
