---
description: Generate complete map themes with dark mode, custom colors, and design token integration
---

I'll help you generate a complete map theme system with light/dark modes and custom branding.

## What This Generates

A complete map theming system including:
- Light and dark mode map styles
- Custom color schemes
- Marker icon variants
- Popup themes
- Control styling
- Design token integration
- Theme switcher component

## Theme Types

### 1. Brand-Based Theme
Match your existing brand colors and design system.

**What I'll need:**
- Primary brand color(s)
- Logo or brand assets
- Existing design tokens (if any)
- Typography preferences

**What you'll get:**
- Map tiles styled with your brand colors
- Markers using brand palette
- UI controls matching your design system
- CSS variables for easy customization

### 2. Industry-Specific Theme
Pre-designed themes for common use cases.

**Available themes:**
- **Corporate**: Professional, clean, business-focused
- **E-Commerce**: Bright, engaging, conversion-optimized
- **Real Estate**: Elegant, trustworthy, detail-oriented
- **Travel**: Vibrant, exploratory, image-rich
- **Logistics**: Functional, data-dense, efficient
- **Healthcare**: Calming, accessible, clear
- **Finance**: Trustworthy, professional, secure
- **Education**: Friendly, accessible, informative

### 3. Mood-Based Theme
Themes based on visual mood and atmosphere.

**Moods:**
- **Minimalist**: Clean, simple, distraction-free
- **Modern**: Bold, contemporary, trendy
- **Classic**: Timeless, traditional, refined
- **Playful**: Fun, colorful, energetic
- **Sophisticated**: Elegant, premium, luxurious
- **Technical**: Data-focused, precise, functional

### 4. Color Scheme Theme
Start with a color palette.

**Provide:**
- 2-5 colors for your palette
- Or choose from preset palettes:
  - Monochromatic
  - Complementary
  - Analogous
  - Triadic
  - Split-complementary

## What Gets Generated

### 1. Map Style Configuration

**For Mapbox:**
```typescript
/**
 * Custom Mapbox Style
 *
 * @swagger
 * @description Complete Mapbox style definition with your brand colors
 */
export const customMapStyle = {
  version: 8,
  name: 'Your Brand Theme',
  metadata: {
    'mapbox:autocomposite': true
  },
  sources: {
    // Optimized sources
  },
  layers: [
    // Custom styled layers
    {
      id: 'background',
      type: 'background',
      paint: {
        'background-color': 'var(--color-map-background)'
      }
    },
    // ... more layers
  ]
};
```

**For Leaflet:**
```typescript
/**
 * Leaflet Tile Layer Configuration
 *
 * @swagger
 * @description Themed tile layers with light/dark variants
 */
export const mapThemes = {
  light: {
    tileUrl: 'https://...',
    attribution: '...',
    filter: 'none'
  },
  dark: {
    tileUrl: 'https://...',
    attribution: '...',
    filter: 'invert(1) hue-rotate(180deg) brightness(0.9)'
  }
};
```

### 2. Marker Theme System

```typescript
/**
 * Themed Marker Factory
 *
 * @swagger
 * @description Creates markers that automatically match the current theme
 */
export function createThemedMarker(
  category: string,
  theme: 'light' | 'dark' = 'light'
): L.DivIcon {
  const colors = themeConfig[theme].markers[category];

  return L.divIcon({
    html: `
      <svg ...>
        <path fill="${colors.primary}" stroke="${colors.accent}"/>
      </svg>
    `,
    className: `themed-marker themed-marker-${theme}`
  });
}
```

### 3. Popup Theme

```css
/**
 * Popup Theme Styles
 *
 * @description Styled popups with theme variables
 */
.map-popup {
  --popup-bg: var(--color-surface);
  --popup-text: var(--color-text-primary);
  --popup-accent: var(--color-primary);

  background: var(--popup-bg);
  color: var(--popup-text);
  border-radius: var(--radius-lg);
  box-shadow: var(--shadow-xl);
}

.map-popup-dark {
  --popup-bg: var(--color-surface-dark);
  --popup-text: var(--color-text-dark);
  --popup-accent: var(--color-primary-light);
}
```

### 4. Theme Switcher Component

```typescript
/**
 * Theme Switcher Component
 *
 * @swagger
 * @component ThemeSwitcher
 * @description Toggle between light and dark map themes
 *
 * @example
 * <app-map-theme-switcher
 *   [(theme)]="currentTheme"
 *   (themeChange)="onThemeChange($event)">
 * </app-map-theme-switcher>
 */
@Component({
  selector: 'app-map-theme-switcher',
  template: `
    <button
      class="theme-toggle"
      (click)="toggleTheme()"
      [attr.aria-label]="
        currentTheme === 'light'
          ? 'Switch to dark mode'
          : 'Switch to light mode'
      ">
      <svg *ngIf="currentTheme === 'light'"><!-- moon icon --></svg>
      <svg *ngIf="currentTheme === 'dark'"><!-- sun icon --></svg>
    </button>
  `,
  styleUrls: ['./map-theme-switcher.component.css'],
  standalone: true
})
export class MapThemeSwitcherComponent {
  @Input() theme: 'light' | 'dark' = 'light';
  @Output() themeChange = new EventEmitter<'light' | 'dark'>();

  currentTheme: 'light' | 'dark' = 'light';

  ngOnInit(): void {
    this.currentTheme = this.theme;
    this.applyTheme(this.currentTheme);
  }

  toggleTheme(): void {
    this.currentTheme = this.currentTheme === 'light' ? 'dark' : 'light';
    this.applyTheme(this.currentTheme);
    this.themeChange.emit(this.currentTheme);
  }

  private applyTheme(theme: 'light' | 'dark'): void {
    document.body.setAttribute('data-map-theme', theme);
    localStorage.setItem('mapTheme', theme);
  }
}
```

### 5. Design Tokens File

```typescript
/**
 * Map Theme Design Tokens
 *
 * @description Centralized theme variables for all map components
 */
export const mapThemeTokens = {
  light: {
    // Background colors
    background: {
      map: '#f5f5f5',
      popup: '#ffffff',
      control: '#ffffff',
      overlay: 'rgba(0, 0, 0, 0.5)'
    },

    // Text colors
    text: {
      primary: '#1f2937',
      secondary: '#6b7280',
      tertiary: '#9ca3af',
      inverse: '#ffffff'
    },

    // Brand colors
    brand: {
      primary: '#3b82f6',
      secondary: '#10b981',
      accent: '#f59e0b',
      error: '#ef4444'
    },

    // Map-specific
    map: {
      water: '#a5c9e3',
      land: '#e8e8e8',
      roads: '#ffffff',
      borders: '#b0b0b0',
      labels: '#4a4a4a'
    },

    // Markers
    markers: {
      default: '#3b82f6',
      selected: '#1d4ed8',
      hover: '#60a5fa',
      cluster: {
        small: '#3b82f6',
        medium: '#f59e0b',
        large: '#ef4444'
      }
    },

    // Effects
    shadows: {
      popup: '0 10px 40px rgba(0, 0, 0, 0.15)',
      marker: '0 4px 12px rgba(0, 0, 0, 0.2)',
      control: '0 2px 8px rgba(0, 0, 0, 0.1)'
    }
  },

  dark: {
    // Dark mode variants
    background: {
      map: '#1a1a1a',
      popup: '#2d3748',
      control: '#374151',
      overlay: 'rgba(0, 0, 0, 0.7)'
    },

    text: {
      primary: '#f3f4f6',
      secondary: '#d1d5db',
      tertiary: '#9ca3af',
      inverse: '#1f2937'
    },

    brand: {
      primary: '#60a5fa',
      secondary: '#34d399',
      accent: '#fbbf24',
      error: '#f87171'
    },

    map: {
      water: '#1e3a5f',
      land: '#2a2a2a',
      roads: '#3a3a3a',
      borders: '#4a4a4a',
      labels: '#d1d5db'
    },

    markers: {
      default: '#60a5fa',
      selected: '#93c5fd',
      hover: '#3b82f6',
      cluster: {
        small: '#60a5fa',
        medium: '#fbbf24',
        large: '#f87171'
      }
    },

    shadows: {
      popup: '0 10px 40px rgba(0, 0, 0, 0.5)',
      marker: '0 4px 12px rgba(0, 0, 0, 0.4)',
      control: '0 2px 8px rgba(0, 0, 0, 0.3)'
    }
  }
};
```

### 6. CSS Variables Export

```css
/**
 * CSS Custom Properties for Map Themes
 *
 * @description Import this file to use map theme variables
 */

:root {
  /* Light theme (default) */
  --map-bg: #f5f5f5;
  --map-popup-bg: #ffffff;
  --map-text: #1f2937;
  --map-primary: #3b82f6;
  --map-shadow: 0 10px 40px rgba(0, 0, 0, 0.15);
}

[data-map-theme='dark'] {
  /* Dark theme overrides */
  --map-bg: #1a1a1a;
  --map-popup-bg: #2d3748;
  --map-text: #f3f4f6;
  --map-primary: #60a5fa;
  --map-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
}

@media (prefers-color-scheme: dark) {
  :root:not([data-map-theme]) {
    /* Auto dark mode */
    --map-bg: #1a1a1a;
    --map-popup-bg: #2d3748;
    --map-text: #f3f4f6;
    --map-primary: #60a5fa;
    --map-shadow: 0 10px 40px rgba(0, 0, 0, 0.5);
  }
}
```

### 7. Documentation

Complete documentation including:
- Installation instructions
- Usage examples
- Customization guide
- Color palette reference
- Accessibility notes
- Browser compatibility
- Performance tips

## How to Request a Theme

### Quick Generation
Simply tell me:
"Generate a [theme type] map theme"

**Examples:**
- "Generate a corporate map theme with blue and gray"
- "Generate a travel industry theme with bright colors"
- "Generate a minimalist dark mode map theme"

### Custom Generation
Provide details:
- **Theme name**: "MyApp Map Theme"
- **Colors**: Primary: #3b82f6, Secondary: #10b981
- **Mood**: Modern, clean, professional
- **Features**: Light and dark modes, smooth transitions
- **Integration**: Use existing design tokens from our Angular Material theme

### From Existing Design System
Share your design tokens or brand guidelines, and I'll generate matching map styles:
"Use our existing design system from [file path or description]"

## What Happens Next

1. I'll analyze your requirements
2. Generate the theme configuration
3. Create all necessary files (TypeScript, CSS, HTML)
4. Provide usage documentation
5. Include customization examples
6. Add accessibility and performance notes

Let me know what kind of theme you'd like to generate!
