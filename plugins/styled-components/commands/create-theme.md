---
description: Generate custom styled-components themes with color palettes, typography, and complete TypeScript definitions
---

I'll help you create a complete custom theme for styled-components with colors, typography, spacing, and all design tokens.

## What This Generates

A complete theming system:
- Theme interface with TypeScript
- Light and dark theme variants
- Color palettes (primary, secondary, success, warning, danger, info)
- Typography scale
- Spacing system
- Breakpoints for responsive design
- Shadow system
- Animation timings
- Border radius values
- Z-index scale
- Theme provider setup
- TypeScript declarations

## Theme Types

### 1. Brand-Based Theme
Match your existing brand colors.

**What I'll need:**
- Primary brand color (hex)
- Secondary color
- Logo colors
- Font families (if custom)
- Existing design system reference

**What you'll get:**
- Complete color palette with shades
- Matching light/dark variants
- Typography configuration
- All design tokens

### 2. Pre-Built Theme
Start with a ready-made color scheme.

**Available Themes:**
- **Blue & Pink** (Modern, friendly)
- **Purple & Orange** (Creative, vibrant)
- **Teal & Coral** (Fresh, contemporary)
- **Indigo & Amber** (Professional, warm)
- **Green & Blue** (Natural, calm)
- **Red & Gray** (Bold, sophisticated)

### 3. Accessibility-First Theme
High contrast and WCAG AAA compliant.

**Features:**
- Enhanced contrast ratios (7:1 minimum)
- Larger font sizes
- Clear focus indicators
- Color-blind friendly palettes
- Reduced motion support

### 4. Custom Palette Theme
Full control over every color.

**Customize:**
- All color values
- Typography scale
- Spacing multipliers
- Custom breakpoints
- Shadow depths
- Animation timings

## Quick Generation

Just tell me:
"Generate a [theme type] theme with [colors]"

**Examples:**
- "Generate a brand theme with #007bff blue and #ff6b6b red"
- "Generate the Purple & Orange pre-built theme"
- "Generate an accessible high-contrast theme"
- "Generate a custom theme with navy and gold"

## Custom Generation

Provide your preferences:

### Colors
```
Primary: #007bff (blue)
Secondary: #6c757d (gray)
Success: #28a745 (green)
Warning: #ffc107 (yellow)
Danger: #dc3545 (red)
Info: #17a2b8 (cyan)
```

### Typography
```
Font Family: "Inter", "Roboto", sans-serif
Base Size: 16px
Scale: 1.25 (minor third)
Line Height: 1.5
```

### Spacing
```
Base Unit: 8px (0.5rem)
Scale: 4px, 8px, 16px, 24px, 32px, 48px, 64px, 96px
```

### Breakpoints
```
Mobile: 640px
Tablet: 768px
Desktop: 1024px
Large: 1280px
XL: 1536px
```

## Generated Files

### theme.ts

```typescript
/**
 * Theme Configuration
 * @description Complete theme system with light and dark variants
 * @version 1.0.0
 */

/**
 * Theme interface
 * Defines the structure for all theme objects
 */
export interface Theme {
  colors: {
    // Primary colors
    primary: string;
    primaryHover: string;
    primaryActive: string;
    primaryLight: string;
    primaryDark: string;

    // Secondary colors
    secondary: string;
    secondaryHover: string;
    secondaryActive: string;
    secondaryLight: string;
    secondaryDark: string;

    // Semantic colors
    success: string;
    successLight: string;
    successDark: string;
    warning: string;
    warningLight: string;
    warningDark: string;
    danger: string;
    dangerLight: string;
    dangerDark: string;
    info: string;
    infoLight: string;
    infoDark: string;

    // Neutral colors
    background: string;
    surface: string;
    surfaceAlt: string;
    text: string;
    textSecondary: string;
    textDisabled: string;
    border: string;
    borderLight: string;
    borderDark: string;
    divider: string;
    overlay: string;
  };

  typography: {
    fontFamily: {
      primary: string;
      secondary: string;
      monospace: string;
    };
    fontSize: {
      xs: string;
      sm: string;
      base: string;
      lg: string;
      xl: string;
      '2xl': string;
      '3xl': string;
      '4xl': string;
      '5xl': string;
      '6xl': string;
    };
    fontWeight: {
      light: number;
      normal: number;
      medium: number;
      semibold: number;
      bold: number;
      extrabold: number;
    };
    lineHeight: {
      none: number;
      tight: number;
      snug: number;
      normal: number;
      relaxed: number;
      loose: number;
    };
    letterSpacing: {
      tighter: string;
      tight: string;
      normal: string;
      wide: string;
      wider: string;
      widest: string;
    };
  };

  spacing: {
    xs: string;
    sm: string;
    md: string;
    lg: string;
    xl: string;
    '2xl': string;
    '3xl': string;
    '4xl': string;
    '5xl': string;
    '6xl': string;
  };

  breakpoints: {
    xs: string;
    sm: string;
    md: string;
    lg: string;
    xl: string;
    '2xl': string;
  };

  shadows: {
    none: string;
    sm: string;
    md: string;
    lg: string;
    xl: string;
    '2xl': string;
    inner: string;
  };

  animations: {
    duration: {
      instant: string;
      fast: string;
      normal: string;
      slow: string;
      slower: string;
    };
    easing: {
      linear: string;
      easeIn: string;
      easeOut: string;
      easeInOut: string;
      sharp: string;
      bounce: string;
    };
  };

  borderRadius: {
    none: string;
    sm: string;
    md: string;
    lg: string;
    xl: string;
    '2xl': string;
    '3xl': string;
    full: string;
  };

  zIndex: {
    base: number;
    dropdown: number;
    sticky: number;
    fixed: number;
    modalBackdrop: number;
    modal: number;
    popover: number;
    tooltip: number;
  };

  // Utility properties
  transitions: {
    default: string;
    fast: string;
    slow: string;
  };

  // Media query helpers
  media: {
    xs: string;
    sm: string;
    md: string;
    lg: string;
    xl: string;
    '2xl': string;
  };
}

/**
 * Light theme
 * Default theme with light background
 */
export const lightTheme: Theme = {
  colors: {
    // Primary colors
    primary: '#007bff',
    primaryHover: '#0056b3',
    primaryActive: '#004085',
    primaryLight: '#cce5ff',
    primaryDark: '#003d7a',

    // Secondary colors
    secondary: '#6c757d',
    secondaryHover: '#5a6268',
    secondaryActive: '#545b62',
    secondaryLight: '#d6d8db',
    secondaryDark: '#343a40',

    // Semantic colors
    success: '#28a745',
    successLight: '#d4edda',
    successDark: '#1e7e34',
    warning: '#ffc107',
    warningLight: '#fff3cd',
    warningDark: '#d39e00',
    danger: '#dc3545',
    dangerLight: '#f8d7da',
    dangerDark: '#bd2130',
    info: '#17a2b8',
    infoLight: '#d1ecf1',
    infoDark: '#117a8b',

    // Neutral colors
    background: '#ffffff',
    surface: '#f8f9fa',
    surfaceAlt: '#e9ecef',
    text: '#212529',
    textSecondary: '#6c757d',
    textDisabled: '#adb5bd',
    border: '#dee2e6',
    borderLight: '#e9ecef',
    borderDark: '#ced4da',
    divider: '#e9ecef',
    overlay: 'rgba(0, 0, 0, 0.5)',
  },

  typography: {
    fontFamily: {
      primary:
        '-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif',
      secondary: 'Georgia, "Times New Roman", Times, serif',
      monospace: '"Fira Code", "SF Mono", Monaco, Consolas, "Courier New", monospace',
    },
    fontSize: {
      xs: '0.75rem',
      sm: '0.875rem',
      base: '1rem',
      lg: '1.125rem',
      xl: '1.25rem',
      '2xl': '1.5rem',
      '3xl': '1.875rem',
      '4xl': '2.25rem',
      '5xl': '3rem',
      '6xl': '3.75rem',
    },
    fontWeight: {
      light: 300,
      normal: 400,
      medium: 500,
      semibold: 600,
      bold: 700,
      extrabold: 800,
    },
    lineHeight: {
      none: 1,
      tight: 1.25,
      snug: 1.375,
      normal: 1.5,
      relaxed: 1.75,
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
  },

  spacing: {
    xs: '0.25rem',
    sm: '0.5rem',
    md: '1rem',
    lg: '1.5rem',
    xl: '2rem',
    '2xl': '3rem',
    '3xl': '4rem',
    '4xl': '6rem',
    '5xl': '8rem',
    '6xl': '12rem',
  },

  breakpoints: {
    xs: '320px',
    sm: '640px',
    md: '768px',
    lg: '1024px',
    xl: '1280px',
    '2xl': '1536px',
  },

  shadows: {
    none: 'none',
    sm: '0 1px 2px 0 rgba(0, 0, 0, 0.05)',
    md: '0 4px 6px -1px rgba(0, 0, 0, 0.1), 0 2px 4px -1px rgba(0, 0, 0, 0.06)',
    lg: '0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05)',
    xl: '0 20px 25px -5px rgba(0, 0, 0, 0.1), 0 10px 10px -5px rgba(0, 0, 0, 0.04)',
    '2xl': '0 25px 50px -12px rgba(0, 0, 0, 0.25)',
    inner: 'inset 0 2px 4px 0 rgba(0, 0, 0, 0.06)',
  },

  animations: {
    duration: {
      instant: '75ms',
      fast: '150ms',
      normal: '300ms',
      slow: '500ms',
      slower: '1000ms',
    },
    easing: {
      linear: 'linear',
      easeIn: 'cubic-bezier(0.4, 0, 1, 1)',
      easeOut: 'cubic-bezier(0, 0, 0.2, 1)',
      easeInOut: 'cubic-bezier(0.4, 0, 0.2, 1)',
      sharp: 'cubic-bezier(0.4, 0, 0.6, 1)',
      bounce: 'cubic-bezier(0.68, -0.55, 0.265, 1.55)',
    },
  },

  borderRadius: {
    none: '0',
    sm: '0.25rem',
    md: '0.5rem',
    lg: '0.75rem',
    xl: '1rem',
    '2xl': '1.5rem',
    '3xl': '2rem',
    full: '9999px',
  },

  zIndex: {
    base: 0,
    dropdown: 1000,
    sticky: 1020,
    fixed: 1030,
    modalBackdrop: 1040,
    modal: 1050,
    popover: 1060,
    tooltip: 1070,
  },

  transitions: {
    default: 'all 0.3s cubic-bezier(0.4, 0, 0.2, 1)',
    fast: 'all 0.15s cubic-bezier(0, 0, 0.2, 1)',
    slow: 'all 0.5s cubic-bezier(0.4, 0, 0.2, 1)',
  },

  media: {
    xs: '@media (min-width: 320px)',
    sm: '@media (min-width: 640px)',
    md: '@media (min-width: 768px)',
    lg: '@media (min-width: 1024px)',
    xl: '@media (min-width: 1280px)',
    '2xl': '@media (min-width: 1536px)',
  },
};

/**
 * Dark theme
 * Dark mode variant
 */
export const darkTheme: Theme = {
  ...lightTheme,
  colors: {
    ...lightTheme.colors,

    // Primary colors (adjusted for dark mode)
    primary: '#0d6efd',
    primaryHover: '#0a58ca',
    primaryActive: '#084298',
    primaryLight: '#1a2942',
    primaryDark: '#0d3b7f',

    // Secondary colors (adjusted for dark mode)
    secondary: '#adb5bd',
    secondaryHover: '#8a9199',
    secondaryActive: '#6c757d',
    secondaryLight: '#495057',
    secondaryDark: '#343a40',

    // Semantic colors (adjusted for dark mode)
    success: '#198754',
    successLight: '#0f3d2d',
    successDark: '#0d502d',
    warning: '#ffc107',
    warningLight: '#4a3b1e',
    warningDark: '#d39e00',
    danger: '#dc3545',
    dangerLight: '#4a1d24',
    dangerDark: '#b02a37',
    info: '#0dcaf0',
    infoLight: '#1a3d47',
    infoDark: '#0891ad',

    // Neutral colors (dark mode)
    background: '#0d1117',
    surface: '#161b22',
    surfaceAlt: '#1c2128',
    text: '#e6edf3',
    textSecondary: '#8b949e',
    textDisabled: '#6e7681',
    border: '#30363d',
    borderLight: '#21262d',
    borderDark: '#3d444d',
    divider: '#21262d',
    overlay: 'rgba(0, 0, 0, 0.7)',
  },
};
```

### styled.d.ts

```typescript
/**
 * TypeScript declarations
 * Extends styled-components DefaultTheme
 */
import 'styled-components';
import { Theme } from './theme';

declare module 'styled-components' {
  export interface DefaultTheme extends Theme {}
}
```

### Theme Utilities

I'll also generate utility functions:

**themeUtils.ts:**
```typescript
/**
 * Theme Utility Functions
 * @description Helper functions for working with themes
 */
import { DefaultTheme } from 'styled-components';

/**
 * Get spacing value
 */
export const spacing = (key: keyof DefaultTheme['spacing']) => {
  return ({ theme }: { theme: DefaultTheme }) => theme.spacing[key];
};

/**
 * Get color value
 */
export const color = (key: keyof DefaultTheme['colors']) => {
  return ({ theme }: { theme: DefaultTheme }) => theme.colors[key];
};

/**
 * Get typography value
 */
export const fontSize = (key: keyof DefaultTheme['typography']['fontSize']) => {
  return ({ theme }: { theme: DefaultTheme }) => theme.typography.fontSize[key];
};

/**
 * Get shadow value
 */
export const shadow = (key: keyof DefaultTheme['shadows']) => {
  return ({ theme }: { theme: DefaultTheme }) => theme.shadows[key];
};

/**
 * Get border radius value
 */
export const borderRadius = (key: keyof DefaultTheme['borderRadius']) => {
  return ({ theme }: { theme: DefaultTheme }) => theme.borderRadius[key];
};

/**
 * Create media query
 */
export const mediaQuery = (breakpoint: keyof DefaultTheme['breakpoints']) => {
  return ({ theme }: { theme: DefaultTheme }) =>
    `@media (min-width: ${theme.breakpoints[breakpoint]})`;
};
```

## Color Palette Generation

I'll generate complete color palettes from your primary color:

- 50-900 shades (like Tailwind)
- Hover/active states
- Light/dark variants
- Accessible contrast ratios

## Typography Scale

Based on your preferences:

- Modular scale calculation
- Line height optimization
- Font weight variants
- Letter spacing adjustments

## What Happens Next

1. I'll analyze your color inputs
2. Generate complete theme files
3. Calculate all color variants
4. Create TypeScript declarations
5. Add utility functions
6. Provide usage examples
7. Include migration guide (if updating)

## Usage Examples

After generation, you can use your theme:

```typescript
import styled from 'styled-components';

const Button = styled.button`
  background-color: ${({ theme }) => theme.colors.primary};
  color: white;
  padding: ${({ theme }) => theme.spacing.md};
  border-radius: ${({ theme }) => theme.borderRadius.lg};
  font-size: ${({ theme }) => theme.typography.fontSize.base};
  box-shadow: ${({ theme }) => theme.shadows.md};
  transition: ${({ theme }) => theme.transitions.default};

  &:hover {
    background-color: ${({ theme }) => theme.colors.primaryHover};
    box-shadow: ${({ theme }) => theme.shadows.lg};
  }
`;
```

## Verification

I'll provide verification steps:
1. Theme is properly typed
2. Autocompletion works
3. All color combinations have sufficient contrast
4. Dark mode variants look correct
5. Theme toggle works smoothly

Let me know what kind of theme you'd like to create!
