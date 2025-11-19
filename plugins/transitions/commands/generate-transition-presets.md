---
description: Generate complete transition preset library with Material Design, iOS, and custom timing curves
---

I'll generate a complete transition presets library with production-ready timing functions and durations.

## What This Generates

Complete CSS transition presets:
- **Material Design Curves** - Standard, decelerate, accelerate, sharp
- **iOS-Style Curves** - Smooth, bounce, elastic
- **Custom Curves** - Anticipation, overshoot, elastic
- **Duration Presets** - Fast, normal, slow
- **Utility Classes** - Ready-to-use transition classes

## Preset Options

### Style Guide
1. **Material Design** - Google's motion system
2. **iOS/Apple** - Apple's smooth animations
3. **Custom** - Unique timing curves
4. **All** - Complete library (recommended)

## Generated Preset Library

### CSS Output

```css
/**
 * Transition Presets Library
 * Production-ready timing functions and durations
 */

/* ========================================
   DURATION VARIABLES
   ======================================== */

:root {
  --duration-fast: 150ms;
  --duration-normal: 250ms;
  --duration-slow: 350ms;
  --duration-slower: 500ms;
}

/* ========================================
   MATERIAL DESIGN CURVES
   ======================================== */

:root {
  --ease-standard: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-decelerate: cubic-bezier(0, 0, 0.2, 1);
  --ease-accelerate: cubic-bezier(0.4, 0, 1, 1);
  --ease-sharp: cubic-bezier(0.4, 0, 0.6, 1);
}

.transition-standard {
  transition: all var(--duration-normal) var(--ease-standard);
}

.transition-decelerate {
  transition: all var(--duration-normal) var(--ease-decelerate);
}

.transition-accelerate {
  transition: all var(--duration-normal) var(--ease-accelerate);
}

/* ========================================
   iOS-STYLE CURVES
   ======================================== */

:root {
  --ease-ios-smooth: cubic-bezier(0.25, 0.46, 0.45, 0.94);
  --ease-ios-bounce: cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

.transition-ios-smooth {
  transition: all var(--duration-normal) var(--ease-ios-smooth);
}

.transition-ios-bounce {
  transition: all 400ms var(--ease-ios-bounce);
}

/* ========================================
   CUSTOM CURVES
   ======================================== */

:root {
  --ease-anticipation: cubic-bezier(0.68, -0.25, 0.265, 1.25);
  --ease-overshoot: cubic-bezier(0.175, 0.885, 0.32, 1.275);
  --ease-elastic: cubic-bezier(0.68, -0.6, 0.32, 1.6);
}

.transition-anticipation {
  transition: all var(--duration-slower) var(--ease-anticipation);
}

.transition-overshoot {
  transition: all 400ms var(--ease-overshoot);
}

.transition-elastic {
  transition: all 600ms var(--ease-elastic);
}

/* ========================================
   PERFORMANCE-OPTIMIZED PRESETS
   ======================================== */

.transition-transform {
  transition: transform var(--duration-normal) var(--ease-standard);
}

.transition-opacity {
  transition: opacity var(--duration-normal) var(--ease-standard);
}

.transition-all-fast {
  transition: transform var(--duration-fast) var(--ease-standard),
              opacity var(--duration-fast) var(--ease-standard);
}

.transition-all-normal {
  transition: transform var(--duration-normal) var(--ease-standard),
              opacity var(--duration-normal) var(--ease-standard);
}

/* ========================================
   COMPONENT-SPECIFIC PRESETS
   ======================================== */

.transition-button {
  transition: transform 200ms ease-out, box-shadow 200ms ease-out;
}

.transition-card {
  transition: transform 250ms ease-out, box-shadow 250ms ease-out;
}

.transition-modal {
  transition: opacity 300ms ease, transform 300ms ease;
}

.transition-sidebar {
  transition: transform 300ms var(--ease-standard);
}

.transition-dropdown {
  transition: max-height 300ms ease, opacity 200ms ease, transform 200ms ease;
}

/* ========================================
   ACCESSIBILITY
   ======================================== */

@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}
```

### TypeScript/SCSS Variables

```typescript
// transition-presets.ts
export const transitions = {
  duration: {
    fast: '150ms',
    normal: '250ms',
    slow: '350ms',
    slower: '500ms',
  },

  easing: {
    standard: 'cubic-bezier(0.4, 0, 0.2, 1)',
    decelerate: 'cubic-bezier(0, 0, 0.2, 1)',
    accelerate: 'cubic-bezier(0.4, 0, 1, 1)',
    sharp: 'cubic-bezier(0.4, 0, 0.6, 1)',
    iosSmooth: 'cubic-bezier(0.25, 0.46, 0.45, 0.94)',
    iosBounce: 'cubic-bezier(0.68, -0.55, 0.265, 1.55)',
  },

  presets: {
    button: 'transform 200ms ease-out, box-shadow 200ms ease-out',
    card: 'transform 250ms ease-out, box-shadow 250ms ease-out',
    modal: 'opacity 300ms ease, transform 300ms ease',
  },
};
```

### Tailwind CSS Plugin

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      transitionDuration: {
        fast: '150ms',
        normal: '250ms',
        slow: '350ms',
      },
      transitionTimingFunction: {
        'material-standard': 'cubic-bezier(0.4, 0, 0.2, 1)',
        'material-decelerate': 'cubic-bezier(0, 0, 0.2, 1)',
        'material-accelerate': 'cubic-bezier(0.4, 0, 1, 1)',
        'ios-smooth': 'cubic-bezier(0.25, 0.46, 0.45, 0.94)',
      },
    },
  },
};
```

**I'll generate the complete preset library in your preferred format!**
