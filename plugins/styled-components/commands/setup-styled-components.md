---
description: Interactive wizard to set up styled-components in your React/Next.js project with TypeScript, theming, and SSR
---

I'll help you set up styled-components in your project with a complete configuration including TypeScript, theming, global styles, and optional SSR support.

## What This Sets Up

A complete styled-components installation:
- Package installation
- TypeScript configuration
- Theme system (light/dark modes)
- Global styles
- Theme provider setup
- SSR configuration (optional)
- Example components

## Project Types

### 1. Create React App / Vite
Standard React application without SSR.

**What I'll generate:**
- Theme files (light/dark)
- TypeScript declarations
- GlobalStyles component
- App wrapper with ThemeProvider
- Example themed components
- Theme toggle hook

### 2. Next.js App Router (13+)
Next.js with App Router and SSR.

**What I'll generate:**
- Theme files
- SSR registry component
- Root layout configuration
- TypeScript declarations
- GlobalStyles component
- Babel configuration
- Example components

### 3. Next.js Pages Router
Next.js with Pages Router and SSR.

**What I'll generate:**
- Theme files
- _document.tsx with SSR
- _app.tsx with ThemeProvider
- TypeScript declarations
- GlobalStyles component
- Babel configuration
- Example components

### 4. Existing Project
Add styled-components to an existing setup.

**What I'll need:**
- Current build tool
- Framework version
- Existing styling approach
- Migration requirements

## Quick Setup

Just tell me:
"Set up styled-components for [project type]"

**Examples:**
- "Set up styled-components for a new Vite React app"
- "Set up styled-components for Next.js 14 with App Router"
- "Set up styled-components for an existing CRA project"

## Custom Setup

Answer these questions:

### 1. Project Type
- **Create React App**: Standard React app
- **Vite**: Modern build tool
- **Next.js App Router**: Next.js 13+ with app directory
- **Next.js Pages Router**: Next.js with pages directory
- **Other**: Custom React setup

### 2. TypeScript
Do you want full TypeScript support?
- **Yes**: Complete type definitions and theme typing
- **No**: JavaScript only (not recommended)

### 3. Theme Configuration
What theme setup do you need?
- **Basic**: Light theme only
- **Light/Dark**: Both themes with toggle
- **Custom**: Multiple theme variants
- **Brand-based**: Match existing brand colors

### 4. SSR Requirements
(Only for Next.js or custom SSR setups)
- **Yes**: Full SSR support with hydration
- **No**: Client-side only

### 5. Additional Features
Select all that apply:
- [ ] Global styles (recommended)
- [ ] Animations library
- [ ] Responsive utilities
- [ ] Component examples
- [ ] Dark mode toggle component
- [ ] Theme persistence (localStorage)

## Generated Files

### For CRA/Vite Projects

**Directory structure:**
```
src/
├── styles/
│   ├── theme.ts              # Theme definitions
│   ├── GlobalStyles.tsx      # Global styles
│   └── styled.d.ts           # TypeScript declarations
├── hooks/
│   └── useTheme.ts           # Theme management hook
├── components/
│   └── ThemeToggle.tsx       # Dark mode toggle
└── App.tsx                   # Updated with providers
```

**theme.ts:**
```typescript
/**
 * Theme Configuration
 * @description Complete theme system with light and dark variants
 */

export interface Theme {
  colors: {
    primary: string;
    primaryHover: string;
    primaryActive: string;
    secondary: string;
    secondaryHover: string;
    secondaryActive: string;
    success: string;
    warning: string;
    danger: string;
    info: string;
    background: string;
    surface: string;
    text: string;
    textSecondary: string;
    border: string;
    divider: string;
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
    };
    fontWeight: {
      light: number;
      normal: number;
      medium: number;
      semibold: number;
      bold: number;
    };
    lineHeight: {
      tight: number;
      normal: number;
      relaxed: number;
      loose: number;
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
  };
  animations: {
    duration: {
      fast: string;
      normal: string;
      slow: string;
    };
    easing: {
      easeIn: string;
      easeOut: string;
      easeInOut: string;
      linear: string;
    };
  };
  borderRadius: {
    none: string;
    sm: string;
    md: string;
    lg: string;
    xl: string;
    full: string;
  };
  zIndex: {
    dropdown: number;
    sticky: number;
    fixed: number;
    modal: number;
    popover: number;
    tooltip: number;
  };
}

/**
 * Light theme
 */
export const lightTheme: Theme = {
  colors: {
    primary: '#007bff',
    primaryHover: '#0056b3',
    primaryActive: '#004085',
    secondary: '#6c757d',
    secondaryHover: '#5a6268',
    secondaryActive: '#545b62',
    success: '#28a745',
    warning: '#ffc107',
    danger: '#dc3545',
    info: '#17a2b8',
    background: '#ffffff',
    surface: '#f8f9fa',
    text: '#212529',
    textSecondary: '#6c757d',
    border: '#dee2e6',
    divider: '#e9ecef',
  },
  typography: {
    fontFamily: {
      primary: '-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, "Helvetica Neue", Arial, sans-serif',
      secondary: 'Georgia, "Times New Roman", Times, serif',
      monospace: '"Fira Code", "Courier New", Courier, monospace',
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
      loose: 2,
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
  },
  animations: {
    duration: {
      fast: '150ms',
      normal: '300ms',
      slow: '500ms',
    },
    easing: {
      easeIn: 'cubic-bezier(0.4, 0, 1, 1)',
      easeOut: 'cubic-bezier(0, 0, 0.2, 1)',
      easeInOut: 'cubic-bezier(0.4, 0, 0.2, 1)',
      linear: 'linear',
    },
  },
  borderRadius: {
    none: '0',
    sm: '0.25rem',
    md: '0.5rem',
    lg: '0.75rem',
    xl: '1rem',
    full: '9999px',
  },
  zIndex: {
    dropdown: 1000,
    sticky: 1020,
    fixed: 1030,
    modal: 1040,
    popover: 1050,
    tooltip: 1060,
  },
};

/**
 * Dark theme
 */
export const darkTheme: Theme = {
  ...lightTheme,
  colors: {
    primary: '#0d6efd',
    primaryHover: '#0a58ca',
    primaryActive: '#084298',
    secondary: '#adb5bd',
    secondaryHover: '#8a9199',
    secondaryActive: '#6c757d',
    success: '#198754',
    warning: '#ffc107',
    danger: '#dc3545',
    info: '#0dcaf0',
    background: '#0d1117',
    surface: '#161b22',
    text: '#e6edf3',
    textSecondary: '#8b949e',
    border: '#30363d',
    divider: '#21262d',
  },
};
```

**styled.d.ts:**
```typescript
/**
 * TypeScript declarations for styled-components
 * Extends DefaultTheme with custom theme interface
 */
import 'styled-components';
import { Theme } from './theme';

declare module 'styled-components' {
  export interface DefaultTheme extends Theme {}
}
```

**GlobalStyles.tsx:**
```typescript
/**
 * Global Styles
 * @description Application-wide styles using createGlobalStyle
 */
import { createGlobalStyle } from 'styled-components';

const GlobalStyles = createGlobalStyle`
  /* CSS Reset */
  *, *::before, *::after {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }

  html {
    font-size: 16px;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-rendering: optimizeLegibility;
  }

  /* Body */
  body {
    font-family: ${({ theme }) => theme.typography.fontFamily.primary};
    font-size: ${({ theme }) => theme.typography.fontSize.base};
    line-height: ${({ theme }) => theme.typography.lineHeight.normal};
    color: ${({ theme }) => theme.colors.text};
    background-color: ${({ theme }) => theme.colors.background};
    transition: background-color ${({ theme }) => theme.animations.duration.normal} ease,
                color ${({ theme }) => theme.animations.duration.normal} ease;
  }

  /* Typography */
  h1, h2, h3, h4, h5, h6 {
    font-weight: ${({ theme }) => theme.typography.fontWeight.bold};
    line-height: ${({ theme }) => theme.typography.lineHeight.tight};
    color: ${({ theme }) => theme.colors.text};
  }

  h1 { font-size: ${({ theme }) => theme.typography.fontSize['4xl']}; }
  h2 { font-size: ${({ theme }) => theme.typography.fontSize['3xl']}; }
  h3 { font-size: ${({ theme }) => theme.typography.fontSize['2xl']}; }
  h4 { font-size: ${({ theme }) => theme.typography.fontSize.xl}; }
  h5 { font-size: ${({ theme }) => theme.typography.fontSize.lg}; }
  h6 { font-size: ${({ theme }) => theme.typography.fontSize.base}; }

  p {
    margin-bottom: ${({ theme }) => theme.spacing.md};
  }

  /* Links */
  a {
    color: ${({ theme }) => theme.colors.primary};
    text-decoration: none;
    transition: color ${({ theme }) => theme.animations.duration.fast} ease;

    &:hover {
      color: ${({ theme }) => theme.colors.primaryHover};
      text-decoration: underline;
    }

    &:focus-visible {
      outline: 2px solid ${({ theme }) => theme.colors.primary};
      outline-offset: 2px;
      border-radius: ${({ theme }) => theme.borderRadius.sm};
    }
  }

  /* Code */
  code, pre {
    font-family: ${({ theme }) => theme.typography.fontFamily.monospace};
  }

  code {
    background-color: ${({ theme }) => theme.colors.surface};
    padding: 2px 6px;
    border-radius: ${({ theme }) => theme.borderRadius.sm};
    font-size: ${({ theme }) => theme.typography.fontSize.sm};
    color: ${({ theme }) => theme.colors.primary};
  }

  pre {
    background-color: ${({ theme }) => theme.colors.surface};
    padding: ${({ theme }) => theme.spacing.md};
    border-radius: ${({ theme }) => theme.borderRadius.md};
    overflow-x: auto;

    code {
      background-color: transparent;
      padding: 0;
      color: ${({ theme }) => theme.colors.text};
    }
  }

  /* Selection */
  ::selection {
    background-color: ${({ theme }) => theme.colors.primary};
    color: white;
  }

  /* Scrollbar */
  ::-webkit-scrollbar {
    width: 12px;
    height: 12px;
  }

  ::-webkit-scrollbar-track {
    background: ${({ theme }) => theme.colors.surface};
  }

  ::-webkit-scrollbar-thumb {
    background: ${({ theme }) => theme.colors.border};
    border-radius: ${({ theme }) => theme.borderRadius.full};

    &:hover {
      background: ${({ theme }) => theme.colors.textSecondary};
    }
  }

  /* Focus visible for accessibility */
  :focus-visible {
    outline: 2px solid ${({ theme }) => theme.colors.primary};
    outline-offset: 2px;
  }
`;

export default GlobalStyles;
```

**useTheme.ts:**
```typescript
/**
 * Theme Hook
 * @description Manages theme state and persistence
 */
import { useState, useEffect } from 'react';
import { lightTheme, darkTheme, Theme } from '../styles/theme';

export type ThemeMode = 'light' | 'dark' | 'system';

export const useTheme = () => {
  const [mode, setMode] = useState<ThemeMode>(() => {
    // Load from localStorage or default to system
    const saved = localStorage.getItem('theme-mode') as ThemeMode;
    return saved || 'system';
  });

  const [theme, setTheme] = useState<Theme>(() => {
    if (mode === 'system') {
      return window.matchMedia('(prefers-color-scheme: dark)').matches
        ? darkTheme
        : lightTheme;
    }
    return mode === 'dark' ? darkTheme : lightTheme;
  });

  useEffect(() => {
    localStorage.setItem('theme-mode', mode);

    if (mode === 'system') {
      const mediaQuery = window.matchMedia('(prefers-color-scheme: dark)');
      const handleChange = (e: MediaQueryListEvent) => {
        setTheme(e.matches ? darkTheme : lightTheme);
      };

      setTheme(mediaQuery.matches ? darkTheme : lightTheme);
      mediaQuery.addEventListener('change', handleChange);

      return () => mediaQuery.removeEventListener('change', handleChange);
    } else {
      setTheme(mode === 'dark' ? darkTheme : lightTheme);
    }
  }, [mode]);

  const toggleTheme = () => {
    setMode((prev) => {
      if (prev === 'light') return 'dark';
      if (prev === 'dark') return 'system';
      return 'light';
    });
  };

  const setThemeMode = (newMode: ThemeMode) => {
    setMode(newMode);
  };

  return {
    theme,
    mode,
    setThemeMode,
    toggleTheme,
    isDark: theme === darkTheme,
  };
};
```

**App.tsx:**
```typescript
/**
 * App Component
 * @description Root component with ThemeProvider
 */
import { ThemeProvider } from 'styled-components';
import GlobalStyles from './styles/GlobalStyles';
import { useTheme } from './hooks/useTheme';
import ThemeToggle from './components/ThemeToggle';

function App() {
  const { theme } = useTheme();

  return (
    <ThemeProvider theme={theme}>
      <GlobalStyles />
      <ThemeToggle />
      {/* Your app components */}
    </ThemeProvider>
  );
}

export default App;
```

### For Next.js App Router

Additional files for SSR support:

**app/registry.tsx:**
```typescript
'use client';

import React, { useState } from 'react';
import { useServerInsertedHTML } from 'next/navigation';
import { ServerStyleSheet, StyleSheetManager } from 'styled-components';

/**
 * Styled Components Registry
 * @description Handles SSR style injection for Next.js App Router
 */
export default function StyledComponentsRegistry({
  children,
}: {
  children: React.ReactNode;
}) {
  const [styledComponentsStyleSheet] = useState(() => new ServerStyleSheet());

  useServerInsertedHTML(() => {
    const styles = styledComponentsStyleSheet.getStyleElement();
    styledComponentsStyleSheet.instance.clearTag();
    return <>{styles}</>;
  });

  if (typeof window !== 'undefined') return <>{children}</>;

  return (
    <StyleSheetManager sheet={styledComponentsStyleSheet.instance}>
      {children}
    </StyleSheetManager>
  );
}
```

**app/layout.tsx:**
```typescript
import StyledComponentsRegistry from './registry';
import { ThemeProvider } from 'styled-components';
import { lightTheme } from '../styles/theme';
import GlobalStyles from '../styles/GlobalStyles';

export default function RootLayout({
  children,
}: {
  children: React.ReactNode;
}) {
  return (
    <html lang="en">
      <body>
        <StyledComponentsRegistry>
          <ThemeProvider theme={lightTheme}>
            <GlobalStyles />
            {children}
          </ThemeProvider>
        </StyledComponentsRegistry>
      </body>
    </html>
  );
}
```

**.babelrc:**
```json
{
  "presets": ["next/babel"],
  "plugins": [
    [
      "babel-plugin-styled-components",
      {
        "ssr": true,
        "displayName": true,
        "fileName": true,
        "minify": true,
        "transpileTemplateLiterals": true,
        "pure": true
      }
    ]
  ]
}
```

## Installation Commands

I'll provide the exact commands to run:

### CRA/Vite
```bash
npm install styled-components
npm install -D @types/styled-components
```

### Next.js
```bash
npm install styled-components
npm install -D @types/styled-components babel-plugin-styled-components
```

## What Happens Next

1. I'll detect your project type (or you tell me)
2. Generate all necessary files
3. Create directory structure
4. Install packages (or provide commands)
5. Update configuration files
6. Provide setup verification steps
7. Include example components
8. Add documentation comments

## Verification Steps

After setup, I'll provide steps to verify:
1. Theme provider is working
2. Global styles are applied
3. TypeScript autocompletion works
4. SSR is configured (if applicable)
5. Theme toggle works
6. Dark mode persists

Let me know your project type, and I'll set up everything for you!
