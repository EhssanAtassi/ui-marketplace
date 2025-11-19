---
description: Generate CSS transition snippets for common UI patterns with optimal timing and performance
---

I'll help you generate optimized CSS transitions for your UI components.

## Quick Generation

Tell me what you're transitioning:
- **Button hover** - "Generate button hover transition"
- **Modal appearance** - "Create modal fade-in transition"
- **Sidebar slide** - "Generate sidebar slide transition"
- **Dropdown menu** - "Create dropdown transition"
- **Card hover** - "Generate card elevation transition"

## Custom Transition

Answer these questions:

### 1. What are you transitioning?
- Button/Link
- Modal/Dialog
- Sidebar/Drawer
- Dropdown/Menu
- Card/Panel
- Form Input
- Tab Content
- List Items
- Custom

### 2. Transition Type
- **Fade** - Opacity change
- **Slide** - Position change
- **Scale** - Size change
- **Elevation** - Shadow/depth change
- **Combined** - Multiple properties

### 3. Direction (if applicable)
- Up/Down
- Left/Right
- In/Out
- Custom

### 4. Duration
- **Fast** (150-200ms) - Micro-interactions
- **Normal** (250-300ms) - Standard UI
- **Slow** (350-500ms) - Emphasis
- Custom (specify ms)

### 5. Timing Function
- **ease-out** - Entering elements (recommended)
- **ease-in** - Exiting elements
- **ease-in-out** - Balanced
- **Material Design** - Standard curves
- **Custom** - Specify cubic-bezier

## Generated Examples

### Button Hover
```css
.button {
  background: #3b82f6;
  color: white;
  padding: 12px 24px;
  border: none;
  border-radius: 6px;
  cursor: pointer;
  box-shadow: 0 4px 12px rgba(59, 130, 246, 0.4);
  transition: transform 200ms ease-out, box-shadow 200ms ease-out;
}

.button:hover {
  transform: translateY(-2px);
  box-shadow: 0 6px 20px rgba(59, 130, 246, 0.6);
}

.button:active {
  transform: translateY(0);
  transition-duration: 100ms;
}

/* Accessibility */
@media (prefers-reduced-motion: reduce) {
  .button {
    transition: none;
  }
}
```

### Modal Fade + Scale
```css
.modal {
  position: fixed;
  inset: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  background: rgba(0, 0, 0, 0.5);
  opacity: 0;
  transform: scale(0.95);
  pointer-events: none;
  transition: opacity 300ms ease, transform 300ms ease;
}

.modal.open {
  opacity: 1;
  transform: scale(1);
  pointer-events: all;
}

.modal-content {
  background: white;
  border-radius: 8px;
  padding: 2rem;
  max-width: 500px;
}
```

### Sidebar Slide
```css
.sidebar {
  position: fixed;
  left: 0;
  top: 0;
  width: 300px;
  height: 100vh;
  background: white;
  box-shadow: 2px 0 10px rgba(0, 0, 0, 0.1);
  transform: translateX(-100%);
  transition: transform 300ms cubic-bezier(0.4, 0, 0.2, 1);
}

.sidebar.open {
  transform: translateX(0);
}

/* Overlay */
.sidebar-overlay {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.5);
  opacity: 0;
  pointer-events: none;
  transition: opacity 200ms ease;
}

.sidebar.open ~ .sidebar-overlay {
  opacity: 1;
  pointer-events: all;
}
```

### Dropdown Menu
```css
.dropdown {
  position: relative;
}

.dropdown-menu {
  position: absolute;
  top: 100%;
  left: 0;
  min-width: 200px;
  background: white;
  border-radius: 4px;
  box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
  max-height: 0;
  overflow: hidden;
  opacity: 0;
  transform: translateY(-10px);
  transition: max-height 300ms ease, opacity 200ms ease, transform 200ms ease;
}

.dropdown.open .dropdown-menu {
  max-height: 400px;
  opacity: 1;
  transform: translateY(0);
}
```

### Card Elevation
```css
.card {
  background: white;
  border-radius: 8px;
  padding: 1.5rem;
  box-shadow: 0 1px 3px rgba(0, 0, 0, 0.1);
  transition: transform 250ms ease-out, box-shadow 250ms ease-out;
}

.card:hover {
  transform: translateY(-4px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}
```

**Tell me what you need, and I'll generate the perfect transition!**
