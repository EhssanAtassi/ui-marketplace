---
description: Generate complete theme system with light/dark modes, density variants, and design tokens
---

I'll help you generate a complete theme system with light/dark modes, optional density variants, and comprehensive design tokens.

## What This Generates

Complete theme system with:
- **Design Token Architecture**: Primitive → Semantic → Component tokens
- **Light & Dark Themes**: Full light and dark mode implementations
- **Density Variants** (optional): Comfortable, default, compact, dense
- **TypeScript Definitions**: Full type safety
- **CSS Custom Properties**: Runtime theming support
- **Theme Provider**: React context implementation
- **Theme Switcher**: UI component for theme selection

## Quick Start

Just tell me:
1. **Project type**: React, Next.js, or Vue
2. **Styling approach**: CSS Variables, Styled Components, or Tailwind
3. **Features**: Which variants you want

**Examples:**
- "Generate theme for Next.js with styled-components"
- "Create React theme with CSS variables and density variants"
- "Generate Vue theme with Tailwind integration"

## Custom Configuration

Answer these questions for a tailored theme:

### 1. Brand Colors

What are your primary brand colors?

**Option 1: Single Color** (I'll generate complete scale)
```
Primary color: #3b82f6
```

**Option 2: Complete Palette**
```
Primary: #3b82f6
Secondary: #8b5cf6
Accent: #06b6d4
```

**Option 3: Use Preset**
- Blue (default)
- Purple
- Green
- Red
- Orange
- Neutral

### 2. Typography

Choose your font stack:

**Option 1: System Fonts** (recommended)
```
Headings: System UI
Body: System UI
Mono: Monospace
```

**Option 2: Custom Fonts**
```
Headings: Inter
Body: Inter
Mono: Fira Code
```

**Option 3: Presets**
- Modern (Inter, SF Pro)
- Classic (Georgia, Times)
- Elegant (Playfair, Lora)
- Technical (IBM Plex, JetBrains Mono)

### 3. Spacing Scale

Choose spacing system:
- **8px Grid** (default) - 4, 8, 16, 24, 32, 48, 64px
- **4px Grid** - 4, 8, 12, 16, 20, 24, 28, 32px
- **Tailwind** - 0.25rem increments
- **Custom** - Define your own scale

### 4. Theme Variants

Select which variants to generate:

**Color Modes:**
- [x] Light mode
- [x] Dark mode
- [ ] Auto (follows system preference)
- [ ] High contrast mode

**Density Variants:**
- [ ] Comfortable (1.25x spacing)
- [ ] Default (1x spacing)
- [ ] Compact (0.875x spacing)
- [ ] Dense (0.75x spacing)

### 5. Framework Integration

Choose your framework:
- **React** - Context provider with hooks
- **Next.js** - App Router or Pages Router
- **Vue** - Composition API
- **Angular** - Service-based theming
- **Vanilla JS** - Pure JavaScript implementation

### 6. Styling Approach

How do you want to apply styles?
- **CSS Variables** - Runtime theming with custom properties
- **Styled Components** - CSS-in-JS with full TypeScript
- **Tailwind CSS** - Extend Tailwind config
- **CSS Modules** - Scoped CSS with theme classes
- **SCSS** - Sass variables and mixins

## Generated Theme Structure

### Light Theme Example

```typescript
/**
 * Light Theme
 * @description Default light mode theme
 */
export const lightTheme: Theme = {
  colors: {
    // Background tokens
    background: {
      primary: '#ffffff',
      secondary: '#f9fafb',
      tertiary: '#f3f4f6',
      inverse: '#111827',
      elevated: '#ffffff',
    },

    // Foreground tokens
    foreground: {
      primary: '#111827',
      secondary: '#4b5563',
      tertiary: '#9ca3af',
      disabled: '#d1d5db',
      inverse: '#ffffff',
      brand: '#3b82f6',
    },

    // Border tokens
    border: {
      default: '#e5e7eb',
      subtle: '#f3f4f6',
      strong: '#d1d5db',
      focus: '#3b82f6',
      error: '#ef4444',
    },

    // Interactive tokens
    interactive: {
      primary: {
        default: '#3b82f6',
        hover: '#2563eb',
        active: '#1d4ed8',
        disabled: '#d1d5db',
        focus: '#3b82f6',
      },
      secondary: {
        default: '#6b7280',
        hover: '#4b5563',
        active: '#374151',
        disabled: '#e5e7eb',
        focus: '#6b7280',
      },
    },

    // Semantic colors
    semantic: {
      success: '#10b981',
      warning: '#f59e0b',
      error: '#ef4444',
      info: '#3b82f6',
    },
  },

  typography: {
    fonts: {
      heading: 'Inter, system-ui, sans-serif',
      body: 'Inter, system-ui, sans-serif',
      mono: 'Fira Code, Consolas, monospace',
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
    },
    fontWeight: {
      light: 300,
      normal: 400,
      medium: 500,
      semibold: 600,
      bold: 700,
    },
    lineHeight: {
      tight: 1.25,
      normal: 1.5,
      relaxed: 1.75,
    },
  },

  spacing: {
    0: '0',
    1: '0.25rem',   // 4px
    2: '0.5rem',    // 8px
    3: '0.75rem',   // 12px
    4: '1rem',      // 16px
    6: '1.5rem',    // 24px
    8: '2rem',      // 32px
    12: '3rem',     // 48px
    16: '4rem',     // 64px
  },

  shadows: {
    none: 'none',
    sm: '0 1px 2px 0 rgba(0, 0, 0, 0.05)',
    md: '0 4px 6px -1px rgba(0, 0, 0, 0.1)',
    lg: '0 10px 15px -3px rgba(0, 0, 0, 0.1)',
    xl: '0 20px 25px -5px rgba(0, 0, 0, 0.1)',
  },

  radii: {
    none: '0',
    sm: '0.25rem',
    base: '0.375rem',
    md: '0.5rem',
    lg: '0.75rem',
    full: '9999px',
  },

  transitions: {
    fast: 'all 150ms cubic-bezier(0.4, 0, 0.2, 1)',
    default: 'all 250ms cubic-bezier(0.4, 0, 0.2, 1)',
    slow: 'all 350ms cubic-bezier(0.4, 0, 0.2, 1)',
  },
};
```

### Dark Theme Example

```typescript
/**
 * Dark Theme
 * @description Dark mode theme with inverted colors
 */
export const darkTheme: Theme = {
  ...lightTheme,
  colors: {
    // Background tokens (inverted)
    background: {
      primary: '#0a0a0a',
      secondary: '#1a1a1a',
      tertiary: '#2a2a2a',
      inverse: '#ffffff',
      elevated: '#1a1a1a',
    },

    // Foreground tokens (inverted)
    foreground: {
      primary: '#ffffff',
      secondary: '#e5e7eb',
      tertiary: '#9ca3af',
      disabled: '#4b5563',
      inverse: '#111827',
      brand: '#60a5fa',
    },

    // Border tokens (adjusted)
    border: {
      default: '#374151',
      subtle: '#1f2937',
      strong: '#4b5563',
      focus: '#60a5fa',
      error: '#f87171',
    },

    // Interactive tokens (adjusted)
    interactive: {
      primary: {
        default: '#3b82f6',
        hover: '#60a5fa',
        active: '#93c5fd',
        disabled: '#374151',
        focus: '#60a5fa',
      },
      secondary: {
        default: '#6b7280',
        hover: '#9ca3af',
        active: '#d1d5db',
        disabled: '#374151',
        focus: '#9ca3af',
      },
    },

    // Semantic colors (brighter for dark mode)
    semantic: {
      success: '#34d399',
      warning: '#fbbf24',
      error: '#f87171',
      info: '#60a5fa',
    },
  },
};
```

## React Theme Provider

```typescript
/**
 * Theme Provider Component
 * @description Manages theme state and CSS variables
 */
import React, { createContext, useContext, useState, useEffect } from 'react';

interface ThemeContextValue {
  theme: Theme;
  themeName: 'light' | 'dark';
  setTheme: (name: 'light' | 'dark') => void;
  toggleTheme: () => void;
}

const ThemeContext = createContext<ThemeContextValue | undefined>(undefined);

export const ThemeProvider: React.FC<{ children: React.ReactNode }> = ({ children }) => {
  const [themeName, setThemeName] = useState<'light' | 'dark'>('light');

  // Detect system preference
  useEffect(() => {
    const prefersDark = window.matchMedia('(prefers-color-scheme: dark)').matches;
    const saved = localStorage.getItem('theme') as 'light' | 'dark' | null;
    setThemeName(saved || (prefersDark ? 'dark' : 'light'));
  }, []);

  // Apply theme to DOM
  useEffect(() => {
    const theme = themeName === 'dark' ? darkTheme : lightTheme;

    // Apply CSS variables
    const root = document.documentElement;
    Object.entries(flattenTheme(theme)).forEach(([key, value]) => {
      root.style.setProperty(`--${key}`, value);
    });

    // Apply class
    document.body.className = `theme-${themeName}`;
    localStorage.setItem('theme', themeName);
  }, [themeName]);

  const value = {
    theme: themeName === 'dark' ? darkTheme : lightTheme,
    themeName,
    setTheme: setThemeName,
    toggleTheme: () => setThemeName(prev => prev === 'dark' ? 'light' : 'dark'),
  };

  return <ThemeContext.Provider value={value}>{children}</ThemeContext.Provider>;
};

export const useTheme = () => {
  const context = useContext(ThemeContext);
  if (!context) throw new Error('useTheme must be used within ThemeProvider');
  return context;
};
```

## Theme Switcher Component

```typescript
/**
 * Theme Switcher Component
 * @description UI component for switching themes
 */
export const ThemeSwitcher: React.FC = () => {
  const { themeName, toggleTheme } = useTheme();

  return (
    <button
      onClick={toggleTheme}
      aria-label="Toggle theme"
      style={{
        padding: '0.5rem 1rem',
        borderRadius: 'var(--radii-base)',
        border: '1px solid var(--border-default)',
        backgroundColor: 'var(--background-secondary)',
        color: 'var(--foreground-primary)',
        cursor: 'pointer',
      }}
    >
      {themeName === 'dark' ? '🌙 Dark' : '☀️ Light'}
    </button>
  );
};
```

## Usage Example

```typescript
/**
 * App Component
 */
import { ThemeProvider, ThemeSwitcher } from './theme';

function App() {
  return (
    <ThemeProvider>
      <div style={{
        padding: '2rem',
        backgroundColor: 'var(--background-primary)',
        color: 'var(--foreground-primary)',
        minHeight: '100vh',
      }}>
        <ThemeSwitcher />
        <h1>Themed Application</h1>
        {/* Your app content */}
      </div>
    </ThemeProvider>
  );
}
```

## Next.js Integration

### App Router (Next.js 13+)

```typescript
// app/providers.tsx
'use client';

import { ThemeProvider } from './theme/ThemeProvider';

export function Providers({ children }: { children: React.ReactNode }) {
  return <ThemeProvider>{children}</ThemeProvider>;
}

// app/layout.tsx
import { Providers } from './providers';

export default function RootLayout({ children }: { children: React.ReactNode }) {
  return (
    <html lang="en">
      <body>
        <Providers>{children}</Providers>
      </body>
    </html>
  );
}
```

## CSS Variables Output

When theme is applied, these CSS variables are generated:

```css
:root {
  /* Colors */
  --background-primary: #ffffff;
  --background-secondary: #f9fafb;
  --foreground-primary: #111827;
  --foreground-secondary: #4b5563;
  --border-default: #e5e7eb;
  --interactive-primary-default: #3b82f6;
  --interactive-primary-hover: #2563eb;

  /* Typography */
  --font-heading: Inter, system-ui, sans-serif;
  --font-body: Inter, system-ui, sans-serif;
  --fontSize-base: 1rem;
  --fontSize-lg: 1.125rem;
  --fontWeight-normal: 400;
  --fontWeight-bold: 700;

  /* Spacing */
  --spacing-2: 0.5rem;
  --spacing-4: 1rem;
  --spacing-6: 1.5rem;
  --spacing-8: 2rem;

  /* Shadows */
  --shadow-sm: 0 1px 2px 0 rgba(0, 0, 0, 0.05);
  --shadow-md: 0 4px 6px -1px rgba(0, 0, 0, 0.1);

  /* Radii */
  --radii-sm: 0.25rem;
  --radii-base: 0.375rem;
  --radii-lg: 0.75rem;
}
```

## What Happens Next

1. I'll ask about your preferences (or use defaults)
2. Generate complete theme files:
   - `theme/tokens.ts` - Design tokens
   - `theme/lightTheme.ts` - Light mode theme
   - `theme/darkTheme.ts` - Dark mode theme
   - `theme/ThemeProvider.tsx` - React provider
   - `theme/useTheme.ts` - Theme hook
   - `theme/types.ts` - TypeScript definitions
3. Create theme switcher component
4. Provide integration instructions
5. Include usage examples

**Tell me what you need, and I'll generate your complete theme system!**
