---
name: create-animation
description: Create custom CSS animations with keyframes, timing functions, and performance optimization
---

You are tasked with creating custom CSS animations for the user.

## Instructions

1. **Ask the user what they want to animate**:
   - Animation type (entrance, exit, attention, loading, transition)
   - Element type (button, modal, card, page, icon, etc.)
   - Animation style (fade, slide, bounce, rotate, scale, flip, etc.)
   - Duration and easing preference
   - Trigger (on load, on hover, on click, on scroll, automatic)

2. **Create the animation** with:
   - @keyframes definition
   - Animation properties (duration, timing-function, delay, iteration)
   - Multiple animation variants (if applicable)
   - State management classes

3. **Include performance optimizations**:
   - Use transform and opacity (GPU-accelerated)
   - Add will-change for complex animations
   - Include backface-visibility
   - Add hardware acceleration hints

4. **Add accessibility**:
   - Respect prefers-reduced-motion
   - Provide reduced motion alternative
   - Ensure focus states are animated

5. **Create usage classes**:
   - Base animation class
   - Modifier classes (speed, delay, direction)
   - Utility classes for common needs

6. **Provide examples**:
   - HTML structure
   - JavaScript triggers (if needed)
   - Multiple use cases
   - Responsive considerations

7. **Include**:
   - Full documentation
   - Browser compatibility notes
   - Performance impact notes
   - Testing suggestions

## Example Animation

```css
/**
 * Modal Animation
 * @description Smooth modal entrance with backdrop fade
 * @performance GPU-accelerated using transform and opacity
 */

/* Backdrop fade in */
@keyframes backdrop-fade-in {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

/* Modal slide up with scale */
@keyframes modal-enter {
  from {
    opacity: 0;
    transform: translateY(20px) scale(0.95);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

/* Usage */
.modal-backdrop {
  animation: backdrop-fade-in 0.2s ease-out;
  background: rgba(0, 0, 0, 0.5);
}

.modal {
  animation: modal-enter 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  will-change: transform, opacity;
}

/* Exit animation */
.modal-exit {
  animation: modal-enter 0.2s ease-in reverse;
}

/* Reduced motion alternative */
@media (prefers-reduced-motion: reduce) {
  .modal,
  .modal-backdrop {
    animation: none;
    transition: opacity 0.1s ease;
  }
}
```

## Animation Types to Offer

- **Entrance**: fadeIn, slideIn, bounceIn, scaleIn, rotateIn
- **Exit**: fadeOut, slideOut, bounceOut, scaleOut, rotateOut
- **Attention**: bounce, pulse, shake, wobble, flash
- **Loading**: spinner, dots, bars, skeleton
- **Transition**: crossfade, slide, flip, zoom

Generate the animation with full code, documentation, and usage examples.
