---
description: Generate complete design token system with primitive, semantic, and component tokens following industry standards
---

I'll help you create a comprehensive design token system following the three-tier architecture: **Primitives** → **Semantic** → **Component** tokens.

## What This Generates

Complete design token system with:
- **Primitive Tokens**: Base values (colors, spacing, typography)
- **Semantic Tokens**: Purpose-driven mappings
- **Component Tokens**: Component-specific values
- **TypeScript Definitions**: Full type safety
- **JSON/YAML Export**: Platform-agnostic tokens
- **CSS Variables**: Runtime-ready output
- **Documentation**: Token usage guide

## Quick Start

Just tell me:
1. **Base color**: Your primary brand color
2. **Scale type**: 5-step, 9-step, or 11-step
3. **Output format**: TypeScript, JSON, CSS, or all

**Examples:**
- "Generate tokens with #3b82f6 as primary, 11-step scale, TypeScript output"
- "Create design tokens for #8b5cf6, export as JSON and CSS variables"
- "Generate complete token system with Tailwind-style scales"

## Custom Configuration

Answer these questions for tailored tokens:

### 1. Color Token Strategy

Choose your color scale:

**11-Step Scale** (Tailwind-style, recommended)
```
50  - Lightest tint
100, 200, 300, 400 - Light variations
500 - Base color (your brand color)
600, 700, 800, 900 - Dark variations
950 - Darkest shade
```

**9-Step Scale** (Material Design)
```
100, 200, 300, 400 - Light
500 - Base
600, 700, 800, 900 - Dark
```

**5-Step Scale** (Minimal)
```
100 - Light
300 - Medium light
500 - Base
700 - Medium dark
900 - Dark
```

### 2. Base Color Input

How do you want to define colors?

**Option 1: Single Base Color** (I'll generate complete palette)
```
Primary: #3b82f6
```

**Option 2: Multiple Brand Colors**
```
Primary: #3b82f6
Secondary: #8b5cf6
Accent: #06b6d4
```

**Option 3: Complete Primitive Palette**
```
Primary: [Your 11-step scale]
Secondary: [Your 11-step scale]
Neutral: [Your 11-step scale]
Success: #10b981
Warning: #f59e0b
Error: #ef4444
Info: #3b82f6
```

### 3. Typography Tokens

Choose typography system:

**Option 1: Modular Scale** (recommended)
- Base size: 16px
- Scale ratio: 1.25 (Major Third)
- Generates: 12, 14, 16, 20, 25, 31, 39, 49px

**Option 2: Tailwind Scale**
- xs, sm, base, lg, xl, 2xl, 3xl, 4xl, 5xl, 6xl

**Option 3: Custom Scale**
- Define your own sizes

**Font Stack:**
- System fonts (default)
- Google Fonts (specify names)
- Custom fonts (provide URLs)

### 4. Spacing Tokens

Choose spacing system:

**8px Grid** (recommended)
```
0, 4, 8, 12, 16, 20, 24, 32, 40, 48, 64, 80, 96px
```

**4px Grid** (Fine control)
```
0, 4, 8, 12, 16, 20, 24, 28, 32, 36, 40...
```

**Tailwind Scale**
```
0, 0.25rem, 0.5rem, 0.75rem, 1rem, 1.25rem...
```

### 5. Token Output Formats

Which formats do you need?

- [x] **TypeScript** - Type-safe tokens
- [ ] **JSON** - Platform-agnostic
- [ ] **CSS Variables** - Runtime theming
- [ ] **SCSS Variables** - Sass compilation
- [ ] **Figma Tokens** - Design tool sync
- [ ] **Style Dictionary** - Build system

### 6. Semantic Mapping

How should semantic tokens be mapped?

**Auto-mapping** (I'll create sensible defaults)
- background.primary → neutral.0
- foreground.primary → neutral.900
- border.default → neutral.200
- interactive.primary.default → primary.500

**Custom mapping** (You define mappings)
- Provide your semantic → primitive mappings

## Generated Token Structure

### Primitive Tokens

```typescript
/**
 * Primitive Color Tokens
 * @description Base color palette - context-free values
 */
export const primitiveColors = {
  // Primary brand color (Blue)
  primary: {
    50: '#eff6ff',
    100: '#dbeafe',
    200: '#bfdbfe',
    300: '#93c5fd',
    400: '#60a5fa',
    500: '#3b82f6',  // Base
    600: '#2563eb',
    700: '#1d4ed8',
    800: '#1e40af',
    900: '#1e3a8a',
    950: '#172554',
  },

  // Secondary brand color (Purple)
  secondary: {
    50: '#faf5ff',
    100: '#f3e8ff',
    200: '#e9d5ff',
    300: '#d8b4fe',
    400: '#c084fc',
    500: '#a855f7',  // Base
    600: '#9333ea',
    700: '#7e22ce',
    800: '#6b21a8',
    900: '#581c87',
    950: '#3b0764',
  },

  // Neutral colors (Gray)
  neutral: {
    0: '#ffffff',
    50: '#f9fafb',
    100: '#f3f4f6',
    200: '#e5e7eb',
    300: '#d1d5db',
    400: '#9ca3af',
    500: '#6b7280',
    600: '#4b5563',
    700: '#374151',
    800: '#1f2937',
    900: '#111827',
    950: '#030712',
    1000: '#000000',
  },

  // Feedback colors
  success: {
    500: '#10b981',
    600: '#059669',
    700: '#047857',
  },

  warning: {
    500: '#f59e0b',
    600: '#d97706',
    700: '#b45309',
  },

  error: {
    500: '#ef4444',
    600: '#dc2626',
    700: '#b91c1c',
  },

  info: {
    500: '#3b82f6',
    600: '#2563eb',
    700: '#1d4ed8',
  },
} as const;

/**
 * Primitive Typography Tokens
 */
export const primitiveTypography = {
  fontFamily: {
    sans: "'Inter', -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif",
    serif: "'Georgia', serif",
    mono: "'Fira Code', 'Consolas', 'Monaco', monospace",
    display: "'Poppins', sans-serif",
  },

  fontSize: {
    xs: '0.75rem',    // 12px
    sm: '0.875rem',   // 14px
    base: '1rem',     // 16px
    lg: '1.125rem',   // 18px
    xl: '1.25rem',    // 20px
    '2xl': '1.5rem',  // 24px
    '3xl': '1.875rem', // 30px
    '4xl': '2.25rem', // 36px
    '5xl': '3rem',    // 48px
    '6xl': '3.75rem', // 60px
  },

  fontWeight: {
    thin: 100,
    extralight: 200,
    light: 300,
    normal: 400,
    medium: 500,
    semibold: 600,
    bold: 700,
    extrabold: 800,
    black: 900,
  },

  lineHeight: {
    none: 1,
    tight: 1.25,
    snug: 1.375,
    normal: 1.5,
    relaxed: 1.625,
    loose: 2,
  },

  letterSpacing: {
    tighter: '-0.05em',
    tight: '-0.025em',
    normal: '0',
    wide: '0.025em',
    wider: '0.05em',
    widest: '0.1em',
  },
} as const;

/**
 * Primitive Spacing Tokens
 * @description 8px grid system
 */
export const primitiveSpacing = {
  0: '0',
  1: '0.25rem',   // 4px
  2: '0.5rem',    // 8px
  3: '0.75rem',   // 12px
  4: '1rem',      // 16px
  5: '1.25rem',   // 20px
  6: '1.5rem',    // 24px
  7: '1.75rem',   // 28px
  8: '2rem',      // 32px
  9: '2.25rem',   // 36px
  10: '2.5rem',   // 40px
  12: '3rem',     // 48px
  14: '3.5rem',   // 56px
  16: '4rem',     // 64px
  20: '5rem',     // 80px
  24: '6rem',     // 96px
  28: '7rem',     // 112px
  32: '8rem',     // 128px
} as const;

/**
 * Primitive Shadow Tokens
 */
export const primitiveShadows = {
  none: 'none',
  xs: '0 1px 2px 0 rgba(0, 0, 0, 0.05)',
  sm: '0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px -1px rgba(0, 0, 0, 0.1)',
  md: '0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -2px rgba(0, 0, 0, 0.1)',
  lg: '0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -4px rgba(0, 0, 0, 0.1)',
  xl: '0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 8px 10px -6px rgba(0, 0, 0, 0.1)',
  '2xl': '0 25px 50px -12px rgba(0, 0, 0, 0.25)',
  inner: 'inset 0 2px 4px 0 rgba(0, 0, 0, 0.05)',
} as const;

/**
 * Primitive Border Radius Tokens
 */
export const primitiveRadii = {
  none: '0',
  xs: '0.125rem',  // 2px
  sm: '0.25rem',   // 4px
  base: '0.375rem', // 6px
  md: '0.5rem',    // 8px
  lg: '0.75rem',   // 12px
  xl: '1rem',      // 16px
  '2xl': '1.5rem', // 24px
  '3xl': '2rem',   // 32px
  full: '9999px',
} as const;
```

### Semantic Tokens

```typescript
/**
 * Semantic Color Tokens
 * @description Purpose-driven color mappings
 */
export const semanticColors = {
  // Background tokens
  background: {
    primary: primitiveColors.neutral[0],      // #ffffff
    secondary: primitiveColors.neutral[50],   // #f9fafb
    tertiary: primitiveColors.neutral[100],   // #f3f4f6
    inverse: primitiveColors.neutral[900],    // #111827
    overlay: 'rgba(0, 0, 0, 0.5)',
    elevated: primitiveColors.neutral[0],     // Cards, modals
    sunken: primitiveColors.neutral[50],      // Input backgrounds
  },

  // Foreground tokens
  foreground: {
    primary: primitiveColors.neutral[900],    // Main text
    secondary: primitiveColors.neutral[600],  // Secondary text
    tertiary: primitiveColors.neutral[400],   // Tertiary text
    disabled: primitiveColors.neutral[300],   // Disabled state
    inverse: primitiveColors.neutral[0],      // Text on dark
    brand: primitiveColors.primary[600],      // Brand-colored text
    link: primitiveColors.primary[600],       // Links
    linkHover: primitiveColors.primary[700],
  },

  // Border tokens
  border: {
    default: primitiveColors.neutral[200],
    subtle: primitiveColors.neutral[100],
    strong: primitiveColors.neutral[300],
    focus: primitiveColors.primary[500],
    error: primitiveColors.error[500],
    success: primitiveColors.success[500],
    warning: primitiveColors.warning[500],
  },

  // Interactive tokens
  interactive: {
    primary: {
      default: primitiveColors.primary[500],
      hover: primitiveColors.primary[600],
      active: primitiveColors.primary[700],
      disabled: primitiveColors.neutral[300],
      focus: primitiveColors.primary[500],
      loading: primitiveColors.neutral[400],
    },
    secondary: {
      default: primitiveColors.neutral[600],
      hover: primitiveColors.neutral[700],
      active: primitiveColors.neutral[800],
      disabled: primitiveColors.neutral[200],
      focus: primitiveColors.neutral[600],
      loading: primitiveColors.neutral[300],
    },
    danger: {
      default: primitiveColors.error[500],
      hover: primitiveColors.error[600],
      active: primitiveColors.error[700],
      disabled: primitiveColors.neutral[300],
      focus: primitiveColors.error[500],
    },
  },

  // Feedback tokens
  feedback: {
    success: {
      background: primitiveColors.success[50],
      foreground: primitiveColors.success[700],
      border: primitiveColors.success[500],
    },
    warning: {
      background: primitiveColors.warning[50],
      foreground: primitiveColors.warning[700],
      border: primitiveColors.warning[500],
    },
    error: {
      background: primitiveColors.error[50],
      foreground: primitiveColors.error[700],
      border: primitiveColors.error[500],
    },
    info: {
      background: primitiveColors.info[50],
      foreground: primitiveColors.info[700],
      border: primitiveColors.info[500],
    },
  },
} as const;

/**
 * Semantic Typography Tokens
 */
export const semanticTypography = {
  // Display (Hero headings)
  display: {
    fontFamily: primitiveTypography.fontFamily.display,
    fontSize: primitiveTypography.fontSize['5xl'],
    fontWeight: primitiveTypography.fontWeight.bold,
    lineHeight: primitiveTypography.lineHeight.tight,
    letterSpacing: primitiveTypography.letterSpacing.tight,
  },

  // Headings
  h1: {
    fontFamily: primitiveTypography.fontFamily.sans,
    fontSize: primitiveTypography.fontSize['4xl'],
    fontWeight: primitiveTypography.fontWeight.bold,
    lineHeight: primitiveTypography.lineHeight.tight,
  },
  h2: {
    fontSize: primitiveTypography.fontSize['3xl'],
    fontWeight: primitiveTypography.fontWeight.semibold,
  },
  h3: {
    fontSize: primitiveTypography.fontSize['2xl'],
    fontWeight: primitiveTypography.fontWeight.semibold,
  },
  h4: {
    fontSize: primitiveTypography.fontSize.xl,
    fontWeight: primitiveTypography.fontWeight.medium,
  },

  // Body text
  bodyLarge: {
    fontSize: primitiveTypography.fontSize.lg,
    lineHeight: primitiveTypography.lineHeight.relaxed,
  },
  body: {
    fontSize: primitiveTypography.fontSize.base,
    lineHeight: primitiveTypography.lineHeight.normal,
  },
  bodySmall: {
    fontSize: primitiveTypography.fontSize.sm,
    lineHeight: primitiveTypography.lineHeight.normal,
  },

  // Labels
  label: {
    fontSize: primitiveTypography.fontSize.sm,
    fontWeight: primitiveTypography.fontWeight.medium,
    letterSpacing: primitiveTypography.letterSpacing.wide,
  },

  // Code
  code: {
    fontFamily: primitiveTypography.fontFamily.mono,
    fontSize: primitiveTypography.fontSize.sm,
  },
} as const;
```

### Component Tokens

```typescript
/**
 * Component Tokens
 * @description Component-specific token overrides
 */
export const componentTokens = {
  // Button tokens
  button: {
    primary: {
      background: semanticColors.interactive.primary.default,
      backgroundHover: semanticColors.interactive.primary.hover,
      backgroundActive: semanticColors.interactive.primary.active,
      backgroundDisabled: semanticColors.interactive.primary.disabled,
      foreground: semanticColors.foreground.inverse,
      foregroundDisabled: semanticColors.foreground.disabled,
      border: 'none',
      borderRadius: primitiveRadii.base,
      paddingX: primitiveSpacing[4],
      paddingY: primitiveSpacing[2],
      fontSize: primitiveTypography.fontSize.base,
      fontWeight: primitiveTypography.fontWeight.medium,
      shadow: primitiveShadows.sm,
      shadowHover: primitiveShadows.md,
    },
    secondary: {
      background: semanticColors.background.secondary,
      backgroundHover: semanticColors.background.tertiary,
      foreground: semanticColors.foreground.primary,
      border: `1px solid ${semanticColors.border.default}`,
    },
    // ... other button variants
  },

  // Input tokens
  input: {
    background: semanticColors.background.primary,
    backgroundDisabled: semanticColors.background.sunken,
    foreground: semanticColors.foreground.primary,
    placeholder: semanticColors.foreground.tertiary,
    border: `1px solid ${semanticColors.border.default}`,
    borderHover: `1px solid ${semanticColors.border.strong}`,
    borderFocus: `2px solid ${semanticColors.border.focus}`,
    borderError: `2px solid ${semanticColors.border.error}`,
    borderRadius: primitiveRadii.sm,
    paddingX: primitiveSpacing[3],
    paddingY: primitiveSpacing[2],
    fontSize: primitiveTypography.fontSize.base,
    shadow: primitiveShadows.inner,
    shadowFocus: primitiveShadows.md,
  },

  // Card tokens
  card: {
    background: semanticColors.background.elevated,
    foreground: semanticColors.foreground.primary,
    border: `1px solid ${semanticColors.border.subtle}`,
    borderRadius: primitiveRadii.lg,
    padding: primitiveSpacing[6],
    shadow: primitiveShadows.md,
    shadowHover: primitiveShadows.lg,
  },

  // Modal tokens
  modal: {
    background: semanticColors.background.primary,
    overlay: semanticColors.background.overlay,
    borderRadius: primitiveRadii.xl,
    padding: primitiveSpacing[8],
    shadow: primitiveShadows['2xl'],
    maxWidth: '32rem',
  },
} as const;
```

## Export Formats

### TypeScript (Complete Type Safety)

```typescript
/**
 * Token Types
 */
export type ColorScale = typeof primitiveColors.primary;
export type Spacing = typeof primitiveSpacing;
export type Typography = typeof primitiveTypography;

export interface DesignTokens {
  primitive: {
    colors: typeof primitiveColors;
    typography: typeof primitiveTypography;
    spacing: typeof primitiveSpacing;
    shadows: typeof primitiveShadows;
    radii: typeof primitiveRadii;
  };
  semantic: {
    colors: typeof semanticColors;
    typography: typeof semanticTypography;
  };
  component: typeof componentTokens;
}
```

### JSON Output

```json
{
  "primitive": {
    "colors": {
      "primary": {
        "50": "#eff6ff",
        "500": "#3b82f6",
        "900": "#1e3a8a"
      }
    },
    "spacing": {
      "2": "0.5rem",
      "4": "1rem"
    }
  },
  "semantic": {
    "colors": {
      "background": {
        "primary": "#ffffff"
      }
    }
  }
}
```

### CSS Variables Output

```css
:root {
  /* Primitive Colors */
  --color-primary-50: #eff6ff;
  --color-primary-500: #3b82f6;
  --color-primary-900: #1e3a8a;

  /* Semantic Colors */
  --background-primary: var(--color-neutral-0);
  --foreground-primary: var(--color-neutral-900);
  --border-default: var(--color-neutral-200);

  /* Spacing */
  --spacing-2: 0.5rem;
  --spacing-4: 1rem;

  /* Typography */
  --font-sans: 'Inter', sans-serif;
  --fontSize-base: 1rem;
}
```

## What Happens Next

1. I'll gather your preferences (or use sensible defaults)
2. Generate color scales from your base colors
3. Create complete token system:
   - `tokens/primitive.ts` - Primitive tokens
   - `tokens/semantic.ts` - Semantic mappings
   - `tokens/component.ts` - Component tokens
   - `tokens/index.ts` - Unified export
   - `tokens/types.ts` - TypeScript definitions
4. Export in requested formats (TS, JSON, CSS, etc.)
5. Generate token documentation
6. Provide usage examples

**Tell me your base color and preferences, and I'll generate your complete design token system!**
