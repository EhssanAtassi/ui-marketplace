---
description: Configure multi-brand theme system with brand switching, shared components, and isolated brand identities
---

I'll help you set up a complete multi-brand theme system that allows multiple brands to share components while maintaining unique visual identities.

## What This Configures

Complete multi-brand system with:
- **Brand Manager**: Switch between brands at runtime
- **Shared Components**: Brand-agnostic UI components
- **Brand Configurations**: Colors, typography, assets per brand
- **Theme Inheritance**: Share common tokens across brands
- **Brand Detection**: Subdomain or path-based brand routing
- **Asset Management**: Brand-specific logos, favicons, icons
- **TypeScript Support**: Full type safety for all brands

## Quick Setup

Just tell me:
1. **Number of brands**: 2, 3, or more
2. **Brand names**: Company names or product names
3. **Routing strategy**: Subdomain, path-based, or manual

**Examples:**
- "Setup 3 brands: Acme, GlobalCorp, TechStart with subdomain routing"
- "Create 2-brand system for ProductA and ProductB with path routing"
- "Configure multi-brand for white-label SaaS"

## Custom Configuration

Answer these questions for a tailored setup:

### 1. Brand Configuration

How many brands do you need?
- **2 brands** - Simple dual-brand setup
- **3-5 brands** - Multiple product brands
- **6+ brands** - Enterprise white-label system
- **Dynamic** - Brands loaded from API/config

For each brand, I'll need:

**Brand 1 (Primary):**
```
Name: Acme Corp
ID: acme
Primary Color: #3b82f6
Logo URL: /logos/acme-logo.svg
Domain: acme.example.com (or /brands/acme)
```

**Brand 2:**
```
Name: GlobalCorp
ID: globalcorp
Primary Color: #8b5cf6
Logo URL: /logos/globalcorp-logo.svg
Domain: globalcorp.example.com (or /brands/globalcorp)
```

### 2. Brand Routing Strategy

How should brands be detected?

**Subdomain-Based** (recommended for production)
```
acme.example.com → Acme brand
globalcorp.example.com → GlobalCorp brand
```

**Path-Based** (good for development)
```
example.com/brands/acme → Acme brand
example.com/brands/globalcorp → GlobalCorp brand
```

**Manual Selection** (user chooses brand)
```
Dropdown or switcher component
Persisted in localStorage
```

**API-Based** (loaded from backend)
```
Fetch brand based on user account
Multi-tenancy setup
```

### 3. Brand Customization Levels

What should be brand-specific?

**Level 1: Colors Only**
- [x] Primary color
- [x] Secondary color
- [ ] Complete color palette
- [ ] Typography
- [ ] Spacing

**Level 2: Visual Identity**
- [x] Colors (all tokens)
- [x] Logo and favicon
- [x] Typography
- [ ] Spacing and layout
- [ ] Component styles

**Level 3: Complete Theming**
- [x] All colors
- [x] Typography system
- [x] Spacing scale
- [x] Component overrides
- [x] Custom assets
- [x] Animations

### 4. Shared vs Brand-Specific

What should be shared across brands?

**Shared (Common Base):**
- [ ] Spacing scale
- [ ] Typography scale
- [ ] Component structure
- [ ] Layout grid
- [ ] Breakpoints
- [ ] Shadow system

**Brand-Specific:**
- [x] Brand colors
- [x] Logos and assets
- [x] Font families
- [ ] Component colors
- [ ] Custom components
- [ ] Animations

### 5. Framework Integration

Choose your setup:
- **React SPA** - Client-side brand switching
- **Next.js** - Server-side brand detection
- **Multi-tenant App** - User-based brands
- **White-label SaaS** - Customer-specific brands

## Generated Multi-Brand Architecture

### Brand Configuration System

```typescript
/**
 * Brand Configuration
 * @description Complete brand identity and theme
 */
export interface BrandConfig {
  id: string;
  name: string;
  displayName: string;
  domain?: string;
  path?: string;
  theme: BrandTheme;
  assets: BrandAssets;
  metadata: BrandMetadata;
}

export interface BrandTheme {
  colors: {
    primary: ColorScale;
    secondary: ColorScale;
    accent: ColorScale;
    // Inherits neutral, semantic from base theme
  };
  typography?: {
    fontFamilies?: {
      heading?: string;
      body?: string;
    };
  };
  // Other overrides...
}

export interface BrandAssets {
  logo: {
    light: string;
    dark: string;
    mark: string;
    wordmark: string;
  };
  favicon: string;
  icons?: Record<string, string>;
  images?: Record<string, string>;
}

export interface BrandMetadata {
  title: string;
  description: string;
  themeColor: string;
  socialPreview?: string;
}
```

### Brand Definitions

```typescript
/**
 * Brand: Acme Corp
 */
export const acmeBrand: BrandConfig = {
  id: 'acme',
  name: 'acme',
  displayName: 'Acme Corp',
  domain: 'acme.example.com',
  theme: {
    colors: {
      primary: {
        50: '#eff6ff',
        100: '#dbeafe',
        200: '#bfdbfe',
        300: '#93c5fd',
        400: '#60a5fa',
        500: '#3b82f6',  // Brand blue
        600: '#2563eb',
        700: '#1d4ed8',
        800: '#1e40af',
        900: '#1e3a8a',
        950: '#172554',
      },
      secondary: {
        // Similar structure...
        500: '#8b5cf6',
      },
    },
    typography: {
      fontFamilies: {
        heading: 'Inter, sans-serif',
        body: 'Inter, sans-serif',
      },
    },
  },
  assets: {
    logo: {
      light: '/logos/acme-light.svg',
      dark: '/logos/acme-dark.svg',
      mark: '/logos/acme-mark.svg',
      wordmark: '/logos/acme-wordmark.svg',
    },
    favicon: '/favicons/acme.ico',
  },
  metadata: {
    title: 'Acme Corp - Innovation First',
    description: 'Leading provider of innovative solutions',
    themeColor: '#3b82f6',
  },
};

/**
 * Brand: GlobalCorp
 */
export const globalCorpBrand: BrandConfig = {
  id: 'globalcorp',
  name: 'globalcorp',
  displayName: 'GlobalCorp',
  domain: 'globalcorp.example.com',
  theme: {
    colors: {
      primary: {
        // Purple palette
        500: '#8b5cf6',
      },
      secondary: {
        // Cyan palette
        500: '#06b6d4',
      },
    },
    typography: {
      fontFamilies: {
        heading: 'Montserrat, sans-serif',
        body: 'Open Sans, sans-serif',
      },
    },
  },
  assets: {
    logo: {
      light: '/logos/globalcorp-light.svg',
      dark: '/logos/globalcorp-dark.svg',
      mark: '/logos/globalcorp-mark.svg',
      wordmark: '/logos/globalcorp-wordmark.svg',
    },
    favicon: '/favicons/globalcorp.ico',
  },
  metadata: {
    title: 'GlobalCorp - Worldwide Excellence',
    description: 'Global solutions for global challenges',
    themeColor: '#8b5cf6',
  },
};

/**
 * All Brands Registry
 */
export const brands: Record<string, BrandConfig> = {
  acme: acmeBrand,
  globalcorp: globalCorpBrand,
};
```

### Brand Manager Service

```typescript
/**
 * Brand Manager
 * @description Manages brand detection and switching
 */
export class BrandManager {
  private static instance: BrandManager;
  private currentBrand: BrandConfig | null = null;
  private listeners: Set<(brand: BrandConfig) => void> = new Set();

  static getInstance(): BrandManager {
    if (!this.instance) {
      this.instance = new BrandManager();
    }
    return this.instance;
  }

  /**
   * Detect Brand from URL
   * @description Auto-detect brand based on subdomain or path
   */
  detectBrand(): BrandConfig {
    const hostname = window.location.hostname;
    const pathname = window.location.pathname;

    // Try subdomain detection
    const subdomain = hostname.split('.')[0];
    if (brands[subdomain]) {
      return brands[subdomain];
    }

    // Try path detection
    const pathMatch = pathname.match(/^\/brands\/([^\/]+)/);
    if (pathMatch && brands[pathMatch[1]]) {
      return brands[pathMatch[1]];
    }

    // Try localStorage
    const saved = localStorage.getItem('selected-brand');
    if (saved && brands[saved]) {
      return brands[saved];
    }

    // Default to first brand
    return Object.values(brands)[0];
  }

  /**
   * Activate Brand
   * @description Apply brand theme and assets
   */
  activateBrand(brandId: string): void {
    const brand = brands[brandId];
    if (!brand) throw new Error(`Brand "${brandId}" not found`);

    this.currentBrand = brand;
    this.applyBrandTheme(brand);
    this.notifyListeners(brand);

    // Persist selection
    localStorage.setItem('selected-brand', brandId);
  }

  /**
   * Apply Brand Theme
   * @description Update DOM with brand-specific styles
   */
  private applyBrandTheme(brand: BrandConfig): void {
    // 1. Apply CSS variables
    const theme = this.generateThemeFromBrand(brand);
    const cssVars = this.flattenTheme(theme);
    const root = document.documentElement;

    Object.entries(cssVars).forEach(([key, value]) => {
      root.style.setProperty(`--${key}`, value);
    });

    // 2. Apply brand class
    document.body.className = document.body.className
      .replace(/brand-[\w-]+/g, '')
      .concat(` brand-${brand.id}`);

    // 3. Update meta tags
    this.updateMetaTags(brand);

    // 4. Update favicon
    this.updateFavicon(brand.assets.favicon);

    // 5. Preload brand assets
    this.preloadAssets(brand.assets);
  }

  /**
   * Generate Theme from Brand Config
   */
  private generateThemeFromBrand(brand: BrandConfig): Theme {
    // Merge base theme with brand overrides
    return {
      ...baseTheme,
      colors: {
        ...baseTheme.colors,
        primary: brand.theme.colors.primary,
        secondary: brand.theme.colors.secondary,
        brand: {
          primary: brand.theme.colors.primary[500],
          secondary: brand.theme.colors.secondary[500],
        },
      },
      typography: {
        ...baseTheme.typography,
        ...brand.theme.typography,
      },
    };
  }

  /**
   * Update Meta Tags
   */
  private updateMetaTags(brand: BrandConfig): void {
    document.title = brand.metadata.title;

    const updateMeta = (name: string, content: string) => {
      let meta = document.querySelector(`meta[name="${name}"]`);
      if (!meta) {
        meta = document.createElement('meta');
        meta.setAttribute('name', name);
        document.head.appendChild(meta);
      }
      meta.setAttribute('content', content);
    };

    updateMeta('description', brand.metadata.description);
    updateMeta('theme-color', brand.metadata.themeColor);
  }

  /**
   * Update Favicon
   */
  private updateFavicon(faviconUrl: string): void {
    let link = document.querySelector<HTMLLinkElement>('link[rel="icon"]');
    if (!link) {
      link = document.createElement('link');
      link.rel = 'icon';
      document.head.appendChild(link);
    }
    link.href = faviconUrl;
  }

  /**
   * Preload Assets
   */
  private async preloadAssets(assets: BrandAssets): Promise<void> {
    const urls = [
      assets.logo.light,
      assets.logo.dark,
      ...Object.values(assets.icons || {}),
    ];

    await Promise.all(
      urls.map(url => {
        return new Promise((resolve, reject) => {
          const img = new Image();
          img.onload = resolve;
          img.onerror = reject;
          img.src = url;
        });
      })
    );
  }

  /**
   * Subscribe to Brand Changes
   */
  subscribe(callback: (brand: BrandConfig) => void): () => void {
    this.listeners.add(callback);
    return () => this.listeners.delete(callback);
  }

  private notifyListeners(brand: BrandConfig): void {
    this.listeners.forEach(callback => callback(brand));
  }

  /**
   * Get Current Brand
   */
  getCurrentBrand(): BrandConfig | null {
    return this.currentBrand;
  }

  /**
   * Get All Brands
   */
  getAllBrands(): BrandConfig[] {
    return Object.values(brands);
  }
}
```

### React Hook for Multi-Brand

```typescript
/**
 * useBrand Hook
 * @description Access and manage brand context in React
 */
export const useBrand = () => {
  const [brand, setBrand] = useState<BrandConfig | null>(null);
  const manager = useMemo(() => BrandManager.getInstance(), []);

  useEffect(() => {
    // Auto-detect and activate brand on mount
    const detected = manager.detectBrand();
    manager.activateBrand(detected.id);
    setBrand(detected);

    // Subscribe to brand changes
    const unsubscribe = manager.subscribe(setBrand);
    return unsubscribe;
  }, [manager]);

  return {
    brand,
    activateBrand: (brandId: string) => manager.activateBrand(brandId),
    getAllBrands: () => manager.getAllBrands(),
    isActive: (brandId: string) => brand?.id === brandId,
  };
};
```

### Brand Provider Component

```typescript
/**
 * Brand Provider
 * @description Provides brand context to app
 */
import React, { createContext, useContext } from 'react';

interface BrandContextValue {
  brand: BrandConfig | null;
  activateBrand: (brandId: string) => void;
  getAllBrands: () => BrandConfig[];
  isActive: (brandId: string) => boolean;
}

const BrandContext = createContext<BrandContextValue | undefined>(undefined);

export const BrandProvider: React.FC<{ children: React.ReactNode }> = ({ children }) => {
  const value = useBrand();

  return <BrandContext.Provider value={value}>{children}</BrandContext.Provider>;
};

export const useBrandContext = () => {
  const context = useContext(BrandContext);
  if (!context) throw new Error('useBrandContext must be used within BrandProvider');
  return context;
};
```

### Brand Switcher Component

```typescript
/**
 * Brand Switcher Component
 * @description UI for switching between brands
 */
export const BrandSwitcher: React.FC = () => {
  const { brand, getAllBrands, activateBrand, isActive } = useBrandContext();

  return (
    <div style={{ display: 'flex', gap: '1rem' }}>
      {getAllBrands().map(b => (
        <button
          key={b.id}
          onClick={() => activateBrand(b.id)}
          style={{
            padding: '0.5rem 1rem',
            backgroundColor: isActive(b.id)
              ? 'var(--interactive-primary-default)'
              : 'var(--background-secondary)',
            color: isActive(b.id)
              ? 'var(--foreground-inverse)'
              : 'var(--foreground-primary)',
            border: '1px solid var(--border-default)',
            borderRadius: 'var(--radii-base)',
            cursor: 'pointer',
          }}
        >
          {b.displayName}
        </button>
      ))}
    </div>
  );
};
```

### Brand-Aware Logo Component

```typescript
/**
 * Brand Logo Component
 * @description Automatically uses current brand's logo
 */
export const BrandLogo: React.FC<{
  variant?: 'full' | 'mark' | 'wordmark';
  theme?: 'light' | 'dark';
}> = ({ variant = 'full', theme = 'light' }) => {
  const { brand } = useBrandContext();

  if (!brand) return null;

  const logoSrc = variant === 'mark'
    ? brand.assets.logo.mark
    : variant === 'wordmark'
    ? brand.assets.logo.wordmark
    : brand.assets.logo[theme];

  return (
    <img
      src={logoSrc}
      alt={`${brand.displayName} logo`}
      style={{ height: '2rem' }}
    />
  );
};
```

## Next.js Server-Side Brand Detection

```typescript
/**
 * middleware.ts
 * @description Detect brand on server-side
 */
import { NextRequest, NextResponse } from 'next/server';

export function middleware(request: NextRequest) {
  const hostname = request.headers.get('host') || '';
  const subdomain = hostname.split('.')[0];

  // Set brand cookie based on subdomain
  if (brands[subdomain]) {
    const response = NextResponse.next();
    response.cookies.set('brand', subdomain);
    return response;
  }

  return NextResponse.next();
}
```

## Usage Example

```typescript
/**
 * App Component
 */
import { BrandProvider, BrandSwitcher, BrandLogo } from './brand';

function App() {
  return (
    <BrandProvider>
      <div style={{
        padding: '2rem',
        backgroundColor: 'var(--background-primary)',
        minHeight: '100vh',
      }}>
        <header style={{ marginBottom: '2rem' }}>
          <BrandLogo variant="full" />
          <BrandSwitcher />
        </header>

        <main>
          <h1 style={{ color: 'var(--foreground-primary)' }}>
            Multi-Brand Application
          </h1>
          <p style={{ color: 'var(--foreground-secondary)' }}>
            The interface automatically adapts to the selected brand.
          </p>
        </main>
      </div>
    </BrandProvider>
  );
}
```

## What Happens Next

1. I'll gather your brand configurations
2. Generate complete multi-brand system:
   - `brands/` - Brand configuration files
   - `BrandManager.ts` - Brand management service
   - `BrandProvider.tsx` - React provider
   - `useBrand.ts` - React hook
   - `BrandSwitcher.tsx` - UI component
   - `types.ts` - TypeScript definitions
3. Set up brand detection (subdomain/path/manual)
4. Configure asset management
5. Provide integration instructions
6. Include testing examples

**Tell me about your brands, and I'll set up your complete multi-brand system!**
