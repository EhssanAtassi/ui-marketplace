---
description: Interactive Material theme generator with custom palettes, typography, and light/dark modes
---

I'll help you create a complete Angular Material theme with custom colors, typography, and dark mode support.

## What This Generates

A complete Material theming system:
- Custom color palettes
- Typography configuration
- Light and dark themes
- Component-specific styles
- Theme toggle service
- CSS custom properties
- Theme preview component

## Theme Types

### 1. Brand-Based Theme
Match your existing brand identity.

**What I'll need:**
- Primary brand color (hex)
- Secondary/accent color
- Logo colors
- Typography preferences
- Existing style guide

**What you'll get:**
- Complete Material palette
- Matching light/dark variants
- Brand-aligned typography
- CSS custom properties
- Theme documentation

### 2. Pre-Built Theme
Start with Material Design 3 palettes.

**Available Themes:**
- **Indigo & Pink** (Material default)
- **Blue & Amber** (Corporate)
- **Purple & Green** (Creative)
- **Teal & Orange** (Modern)
- **Deep Purple & Lime** (Vibrant)
- **Red & Gray** (Bold)

### 3. Accessibility-First Theme
High contrast and WCAG AAA compliant.

**Features:**
- Enhanced contrast ratios
- Larger typography
- Clear focus indicators
- Reduced motion support
- Color-blind friendly palettes

### 4. Custom Palette Theme
Full control over every color.

**Customize:**
- Primary palette (50-900 shades)
- Accent palette
- Warn palette
- Background colors
- Surface colors
- Text colors

## Generated Files

### Theme SCSS File

**styles/theme.scss:**
```scss
/**
 * Custom Material Theme Configuration
 * @description Complete theme with custom palettes and typography
 * @version 1.0.0
 */

@use '@angular/material' as mat;
@use 'sass:map';

// Include Material core
@include mat.core();

// ===== Custom Color Palettes =====

/**
 * Primary Palette
 * @description Main brand color palette
 */
$custom-primary-palette: (
  50: #e3f2fd,
  100: #bbdefb,
  200: #90caf9,
  300: #64b5f6,
  400: #42a5f5,
  500: #2196f3,
  600: #1e88e5,
  700: #1976d2,
  800: #1565c0,
  900: #0d47a1,
  A100: #82b1ff,
  A200: #448aff,
  A400: #2979ff,
  A700: #2962ff,
  contrast: (
    50: rgba(black, 0.87),
    100: rgba(black, 0.87),
    200: rgba(black, 0.87),
    300: rgba(black, 0.87),
    400: rgba(black, 0.87),
    500: white,
    600: white,
    700: white,
    800: white,
    900: white,
    A100: rgba(black, 0.87),
    A200: white,
    A400: white,
    A700: white,
  )
);

/**
 * Define Material palettes
 */
$app-primary: mat.define-palette($custom-primary-palette);
$app-accent: mat.define-palette(mat.$pink-palette, A200, A100, A400);
$app-warn: mat.define-palette(mat.$red-palette);

// ===== Custom Typography =====

/**
 * Typography Configuration
 * @description Custom font families and scales
 */
$custom-typography: mat.define-typography-config(
  $font-family: '"Roboto", "Helvetica Neue", sans-serif',
  $headline-1: mat.define-typography-level(96px, 96px, 300, $letter-spacing: -1.5px),
  $headline-2: mat.define-typography-level(60px, 60px, 300, $letter-spacing: -0.5px),
  $headline-3: mat.define-typography-level(48px, 50px, 400),
  $headline-4: mat.define-typography-level(34px, 40px, 400),
  $headline-5: mat.define-typography-level(24px, 32px, 400),
  $headline-6: mat.define-typography-level(20px, 32px, 500),
  $subtitle-1: mat.define-typography-level(16px, 28px, 400),
  $subtitle-2: mat.define-typography-level(14px, 24px, 500),
  $body-1: mat.define-typography-level(16px, 24px, 400),
  $body-2: mat.define-typography-level(14px, 20px, 400),
  $caption: mat.define-typography-level(12px, 20px, 400),
  $button: mat.define-typography-level(14px, 14px, 500),
  $overline: mat.define-typography-level(10px, 16px, 400, $letter-spacing: 1.5px),
);

// ===== Light Theme =====

/**
 * Light Theme Definition
 * @description Default light theme
 */
$light-theme: mat.define-light-theme((
  color: (
    primary: $app-primary,
    accent: $app-accent,
    warn: $app-warn,
  ),
  typography: $custom-typography,
  density: 0,
));

// Apply light theme
@include mat.all-component-themes($light-theme);

// ===== Dark Theme =====

/**
 * Dark Theme Definition
 * @description Dark mode variant
 */
$dark-theme: mat.define-dark-theme((
  color: (
    primary: $app-primary,
    accent: $app-accent,
    warn: $app-warn,
  ),
  typography: $custom-typography,
  density: 0,
));

// Apply dark theme when class is present
.dark-theme {
  @include mat.all-component-colors($dark-theme);
}

// ===== CSS Custom Properties =====

/**
 * Export theme colors as CSS variables
 * @description Runtime-accessible theme colors
 */
:root {
  // Primary colors
  --mat-primary-50: #e3f2fd;
  --mat-primary-100: #bbdefb;
  --mat-primary-500: #2196f3;
  --mat-primary-700: #1976d2;

  // Accent colors
  --mat-accent-500: #ff4081;
  --mat-accent-700: #c51162;

  // Warn colors
  --mat-warn-500: #f44336;
  --mat-warn-700: #d32f2f;

  // Surface colors
  --mat-surface: #ffffff;
  --mat-background: #fafafa;

  // Text colors
  --mat-text-primary: rgba(0, 0, 0, 0.87);
  --mat-text-secondary: rgba(0, 0, 0, 0.6);
  --mat-text-disabled: rgba(0, 0, 0, 0.38);
}

.dark-theme {
  // Dark mode variables
  --mat-surface: #303030;
  --mat-background: #212121;

  --mat-text-primary: rgba(255, 255, 255, 0.87);
  --mat-text-secondary: rgba(255, 255, 255, 0.6);
  --mat-text-disabled: rgba(255, 255, 255, 0.38);
}

// ===== Component-Specific Customization =====

/**
 * Custom component theming
 * @description Override specific component styles
 */
@mixin custom-component-theme($theme) {
  $color-config: mat.get-color-config($theme);
  $primary-palette: map.get($color-config, 'primary');
  $accent-palette: map.get($color-config, 'accent');

  // Custom card styling
  .mat-mdc-card {
    border-radius: 12px;
    box-shadow: 0 2px 8px rgba(0, 0, 0, 0.1);

    &:hover {
      box-shadow: 0 4px 16px rgba(0, 0, 0, 0.15);
    }
  }

  // Custom button styling
  .mat-mdc-raised-button {
    border-radius: 8px;
    font-weight: 500;
  }

  // Custom form field styling
  .mat-mdc-form-field {
    .mat-mdc-text-field-wrapper {
      border-radius: 8px;
    }
  }
}

@include custom-component-theme($light-theme);

.dark-theme {
  @include custom-component-theme($dark-theme);
}
```

### Theme Service

**services/theme.service.ts:**
```typescript
/**
 * Theme Service
 * @description Manages theme switching and persistence
 */
import { Injectable, signal, effect } from '@angular/core';

export type Theme = 'light' | 'dark' | 'auto';

@Injectable({
  providedIn: 'root'
})
export class ThemeService {
  /** Current theme signal */
  private themeSignal = signal<Theme>('light');

  /** System prefers dark mode */
  private prefersDark = window.matchMedia('(prefers-color-scheme: dark)');

  /** Public readonly theme */
  theme = this.themeSignal.asReadonly();

  constructor() {
    // Load saved theme
    const saved = localStorage.getItem('theme') as Theme;
    if (saved) {
      this.setTheme(saved);
    } else {
      // Auto-detect system preference
      this.setTheme(this.prefersDark.matches ? 'dark' : 'light');
    }

    // Listen for system theme changes
    this.prefersDark.addEventListener('change', (e) => {
      if (this.themeSignal() === 'auto') {
        this.applyTheme(e.matches ? 'dark' : 'light');
      }
    });

    // Apply theme when it changes
    effect(() => {
      const theme = this.themeSignal();
      this.applyTheme(theme === 'auto'
        ? (this.prefersDark.matches ? 'dark' : 'light')
        : theme
      );
    });
  }

  /**
   * Sets the theme
   * @param theme - Theme to apply
   */
  setTheme(theme: Theme): void {
    this.themeSignal.set(theme);
    localStorage.setItem('theme', theme);
  }

  /**
   * Toggles between light and dark
   */
  toggleTheme(): void {
    const current = this.themeSignal();
    this.setTheme(current === 'light' ? 'dark' : 'light');
  }

  /**
   * Applies theme to document
   * @param theme - Theme to apply
   */
  private applyTheme(theme: Theme): void {
    const actualTheme = theme === 'auto'
      ? (this.prefersDark.matches ? 'dark' : 'light')
      : theme;

    if (actualTheme === 'dark') {
      document.body.classList.add('dark-theme');
    } else {
      document.body.classList.remove('dark-theme');
    }
  }

  /**
   * Checks if dark mode is active
   * @returns True if dark mode
   */
  isDark(): boolean {
    const theme = this.themeSignal();
    return theme === 'dark' ||
           (theme === 'auto' && this.prefersDark.matches);
  }
}
```

### Theme Toggle Component

**components/theme-toggle/theme-toggle.component.ts:**
```typescript
/**
 * Theme Toggle Component
 * @description UI control for switching themes
 */
import { Component, inject } from '@angular/core';
import { MatButtonModule } from '@angular/material/button';
import { MatIconModule } from '@angular/material/icon';
import { MatMenuModule } from '@angular/material/menu';
import { ThemeService, Theme } from '../../services/theme.service';

@Component({
  selector: 'app-theme-toggle',
  standalone: true,
  imports: [MatButtonModule, MatIconModule, MatMenuModule],
  templateUrl: './theme-toggle.component.html',
  styleUrls: ['./theme-toggle.component.scss']
})
export class ThemeToggleComponent {
  themeService = inject(ThemeService);

  /** Available themes */
  themes: { value: Theme; label: string; icon: string }[] = [
    { value: 'light', label: 'Light', icon: 'light_mode' },
    { value: 'dark', label: 'Dark', icon: 'dark_mode' },
    { value: 'auto', label: 'Auto', icon: 'brightness_auto' }
  ];

  /**
   * Sets theme
   * @param theme - Theme to set
   */
  setTheme(theme: Theme): void {
    this.themeService.setTheme(theme);
  }

  /**
   * Gets current theme icon
   * @returns Icon name
   */
  getCurrentIcon(): string {
    const theme = this.themeService.theme();
    return this.themes.find(t => t.value === theme)?.icon || 'brightness_auto';
  }
}
```

**theme-toggle.component.html:**
```html
<button
  mat-icon-button
  [matMenuTriggerFor]="themeMenu"
  [attr.aria-label]="'Change theme'"
>
  <mat-icon>{{ getCurrentIcon() }}</mat-icon>
</button>

<mat-menu #themeMenu="matMenu">
  @for (theme of themes; track theme.value) {
    <button
      mat-menu-item
      (click)="setTheme(theme.value)"
      [class.active]="themeService.theme() === theme.value"
    >
      <mat-icon>{{ theme.icon }}</mat-icon>
      <span>{{ theme.label }}</span>
    </button>
  }
</mat-menu>
```

## Quick Generation

Just tell me:
"Generate a Material theme with [colors]"

**Examples:**
- "Generate a Material theme with blue and orange"
- "Generate a corporate theme with navy and gold"
- "Generate a high-contrast accessible theme"
- "Generate a dark theme matching my brand colors"

## Custom Generation

Provide details:

**Colors:**
- **Primary**: #2196f3 (blue)
- **Accent**: #ff4081 (pink)
- **Warn**: #f44336 (red)
- **Background**: #fafafa
- **Surface**: #ffffff

**Typography:**
- **Font family**: "Inter", "Roboto", sans-serif
- **Base size**: 16px
- **Scale**: 1.25 (modular scale)
- **Line height**: 1.5

**Features:**
- Light and dark modes
- Automatic system detection
- Persistent theme preference
- Smooth transitions
- Component overrides
- Custom density

## Generated Assets

### 1. Theme Configuration
- Complete SCSS theme file
- Custom palette definitions
- Typography configuration
- Light/dark variants

### 2. Theme Service
- Angular service for theme management
- LocalStorage persistence
- System preference detection
- Theme toggle functionality

### 3. Theme Toggle Component
- Material button with menu
- Theme selection UI
- Current theme indicator
- Accessibility labels

### 4. CSS Custom Properties
- Runtime theme variables
- Component-specific overrides
- Easy customization
- Dynamic updates

### 5. Documentation
- Setup instructions
- Usage examples
- Customization guide
- Migration from default theme

## Features Included

### Multiple Theme Modes
- **Light mode**: Default bright theme
- **Dark mode**: Eye-friendly dark variant
- **Auto mode**: Follows system preference
- **Custom modes**: Brand-specific themes

### Typography System
- Consistent font hierarchy
- Responsive font sizes
- Line height optimization
- Letter spacing
- Font weight scale

### Color System
- Material Design 3 palettes
- 50-900 shade scales
- Contrast calculations
- Accessibility compliance
- Custom color generation

### Component Overrides
- Card styling
- Button variants
- Form fields
- Tables
- Dialogs
- Toolbars

### Accessibility
- WCAG 2.1 AA compliance
- High contrast options
- Reduced motion support
- Focus indicators
- Color-blind friendly

### Performance
- CSS-only theme switching
- No JavaScript overhead
- Minimal bundle size
- Tree-shakable components
- Optimized selectors

## Theme Testing

I'll also generate a theme preview component:

**theme-preview.component.ts:**
```typescript
/**
 * Theme Preview Component
 * @description Visual preview of all theme colors and components
 */
@Component({
  selector: 'app-theme-preview',
  standalone: true,
  imports: [/* Material modules */],
  templateUrl: './theme-preview.component.html',
  styleUrls: ['./theme-preview.component.scss']
})
export class ThemePreviewComponent {
  // Preview all Material components with current theme
}
```

Shows preview of:
- Color palettes (primary, accent, warn)
- Typography scale
- All Material components
- Light/dark variants
- Accessibility features

## Integration Guide

After generation, I'll provide:

1. **Import Instructions**
   - Where to add theme SCSS
   - How to configure angular.json
   - Font loading (if custom)

2. **Service Setup**
   - How to provide ThemeService
   - Initial theme detection
   - Persistence configuration

3. **Component Usage**
   - Adding theme toggle to toolbar
   - Accessing theme in components
   - Custom component theming

4. **Testing**
   - Visual regression tests
   - Accessibility audits
   - Cross-browser verification

## What Happens Next

1. I'll analyze your color preferences
2. Generate complete theme SCSS file
3. Create theme service with signals
4. Build theme toggle component
5. Export CSS custom properties
6. Provide integration instructions
7. Generate theme preview
8. Add accessibility notes

Let me know what kind of theme you'd like to create!
