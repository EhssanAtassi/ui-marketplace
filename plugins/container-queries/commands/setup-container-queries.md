---
name: setup-container-queries
description: Set up CSS Container Queries for responsive components with examples and patterns
---

You are tasked with setting up CSS Container Queries for responsive component design.

## Instructions

1. **Ask the user about their project**:
   - Framework (React, Angular, Vue, vanilla CSS)
   - Component type (cards, navigation, grid, sidebar, custom)
   - Browser support requirements
   - Fallback strategy needed (progressive enhancement, polyfill)
   - Breakpoint preferences

2. **Set up container infrastructure**:
   - Create base container styles
   - Set up container types (`inline-size`, `size`)
   - Configure container names (if needed)
   - Add browser support detection

3. **Generate responsive component patterns**:
   - Container wrapper setup
   - Container query breakpoints
   - Container unit usage
   - Fallback media queries (if needed)

4. **Create examples**:
   - Basic container query setup
   - Container units for responsive typography/spacing
   - Real component examples
   - Nested container patterns

5. **Add testing utilities**:
   - Browser feature detection
   - Container resize testing
   - Performance monitoring

6. **Include documentation**:
   - Usage examples
   - Browser compatibility notes
   - Performance best practices
   - Troubleshooting guide

## Example Implementation

### Basic Setup

```css
/**
 * Container Queries Setup
 * @description Modern component-based responsive design
 */

/* Container wrapper */
.container {
  container-type: inline-size;
  container-name: main;
}

/* Container query */
@container main (min-width: 400px) {
  .content {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
}

/* Container units */
.responsive-text {
  font-size: clamp(1rem, 5cqi, 2rem);
  padding: max(1rem, 3cqi);
}

/* Fallback with @supports */
@supports (container-type: inline-size) {
  .modern-container {
    container-type: inline-size;
  }

  @container (min-width: 500px) {
    .modern-content {
      display: flex;
      gap: 2rem;
    }
  }
}

/* Fallback for older browsers */
@media (min-width: 768px) {
  .content {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
}
```

### Component Pattern

```css
/**
 * Responsive Card Component
 * Adapts based on container width, not viewport
 */
.card-container {
  container-type: inline-size;
  container-name: card;
}

.card {
  background: white;
  border-radius: 0.5rem;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

/* Mobile layout (< 400px) */
@container card (max-width: 399px) {
  .card {
    display: flex;
    flex-direction: column;
  }

  .card__image {
    width: 100%;
    aspect-ratio: 16/9;
  }

  .card__content {
    padding: 1rem;
  }

  .card__title {
    font-size: 1.125rem;
  }
}

/* Tablet layout (400px - 699px) */
@container card (min-width: 400px) and (max-width: 699px) {
  .card {
    display: grid;
    grid-template-columns: 200px 1fr;
  }

  .card__image {
    height: 100%;
    object-fit: cover;
  }

  .card__content {
    padding: 1.5rem;
  }

  .card__title {
    font-size: 1.25rem;
  }
}

/* Desktop layout (>= 700px) */
@container card (min-width: 700px) {
  .card {
    position: relative;
    min-height: 400px;
  }

  .card__image {
    position: absolute;
    inset: 0;
    object-fit: cover;
  }

  .card__content {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    padding: 2rem;
    background: linear-gradient(to top, rgba(0,0,0,0.9), transparent);
    color: white;
  }

  .card__title {
    font-size: 1.75rem;
  }
}
```

### Framework Integration

#### React Example

```typescript
/**
 * React Container Query Component
 * @description Card component using container queries
 */
import React from 'react';
import styles from './Card.module.css';

interface CardProps {
  title: string;
  description: string;
  image: string;
}

export const Card: React.FC<CardProps> = ({ title, description, image }) => {
  return (
    <div className={styles.cardContainer}>
      <div className={styles.card}>
        <img src={image} alt={title} className={styles.card__image} />
        <div className={styles.card__content}>
          <h3 className={styles.card__title}>{title}</h3>
          <p className={styles.card__description}>{description}</p>
        </div>
      </div>
    </div>
  );
};
```

```css
/* Card.module.css */
.cardContainer {
  container-type: inline-size;
  container-name: card;
}

/* Container queries from above */
@container card (min-width: 400px) {
  .card {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
}
```

#### Angular Example

```typescript
/**
 * Angular Container Query Component
 * @component CardComponent
 * @description Responsive card using container queries
 */
import { Component, Input } from '@angular/core';

@Component({
  selector: 'app-card',
  templateUrl: './card.component.html',
  styleUrls: ['./card.component.scss'],
  standalone: true
})
export class CardComponent {
  @Input() title: string = '';
  @Input() description: string = '';
  @Input() image: string = '';
}
```

```html
<!-- card.component.html -->
<div class="card-container">
  <div class="card">
    <img [src]="image" [alt]="title" class="card__image" />
    <div class="card__content">
      <h3 class="card__title">{{ title }}</h3>
      <p class="card__description">{{ description }}</p>
    </div>
  </div>
</div>
```

```scss
// card.component.scss
.card-container {
  container-type: inline-size;
  container-name: card;
}

@container card (min-width: 400px) {
  .card {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
}
```

### Browser Support Detection

```javascript
/**
 * Container Query Support Detection
 * @returns {boolean} True if container queries are supported
 */
function supportsContainerQueries() {
  return CSS.supports('container-type: inline-size');
}

// Add class to HTML element
if (supportsContainerQueries()) {
  document.documentElement.classList.add('container-queries-supported');
} else {
  document.documentElement.classList.add('no-container-queries');
  // Load polyfill if needed
  import('container-query-polyfill');
}
```

## Component Types to Generate

Based on user selection:

1. **Card Component**: Vertical → Horizontal → Overlay layouts
2. **Navigation**: Hamburger → Horizontal → Mega menu
3. **Grid Layout**: 1 → 2 → 3 → 4 columns based on container
4. **Sidebar**: Collapsed → Partial → Full expansion
5. **Form**: Stacked → Inline → Multi-column
6. **Table**: Cards → Horizontal scroll → Full table
7. **Feature List**: Vertical → Grid → Horizontal
8. **Product Gallery**: Masonry → Grid → Carousel

## Performance Checklist

- [ ] Use `inline-size` instead of `size` when possible
- [ ] Add `contain: layout style` for optimization
- [ ] Batch container query styles together
- [ ] Cache container unit calculations in CSS variables
- [ ] Test on various container sizes
- [ ] Monitor reflow/repaint performance
- [ ] Implement progressive enhancement
- [ ] Provide media query fallbacks

## Browser Compatibility

- Chrome/Edge 105+
- Safari 16+
- Firefox 110+
- Opera 91+

**Fallback**: Use `@supports` with media query fallbacks for older browsers.

Generate the complete container query setup with examples, documentation, and testing utilities based on the user's requirements.
