---
name: animation-library
description: CSS animation patterns library. Use when searching for keyframes, timing functions, or animation recipes for common UI patterns.
---

# Animation Library - Complete CSS Animation Patterns Reference

A comprehensive library of pre-built CSS animations, timing functions, and animation recipes for common UI patterns. This library includes 50+ animation patterns ready to use in your projects.

## Table of Contents

1. [Fade Animations](#fade-animations)
2. [Slide Animations](#slide-animations)
3. [Scale Animations](#scale-animations)
4. [Rotate Animations](#rotate-animations)
5. [Bounce Animations](#bounce-animations)
6. [Flip Animations](#flip-animations)
7. [Shake & Wobble Animations](#shake--wobble-animations)
8. [Blur & Focus Animations](#blur--focus-animations)
9. [Glow & Pulse Animations](#glow--pulse-animations)
10. [Swing & Pendulum Animations](#swing--pendulum-animations)
11. [Timing Functions Reference](#timing-functions-reference)
12. [Common UI Animation Recipes](#common-ui-animation-recipes)
13. [Scroll-Driven Animation Patterns](#scroll-driven-animation-patterns)
14. [Performance Patterns](#performance-patterns)
15. [Accessibility Considerations](#accessibility-considerations)
16. [Browser Compatibility Notes](#browser-compatibility-notes)
17. [Troubleshooting Guide](#troubleshooting-guide)

---

## Fade Animations

### 1. Fade In
```css
/**
 * Fade In Animation
 * Description: Smoothly fades element from transparent to visible
 * Use case: Page loads, content reveals, modal appearances
 * Performance: GPU-accelerated (opacity)
 */
@keyframes fadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

.fade-in {
  animation: fadeIn 0.3s ease-in;
}
```

### 2. Fade Out
```css
/**
 * Fade Out Animation
 * Description: Smoothly fades element from visible to transparent
 * Use case: Dismissing modals, hiding content, exit animations
 * Performance: GPU-accelerated (opacity)
 */
@keyframes fadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}

.fade-out {
  animation: fadeOut 0.3s ease-out;
  animation-fill-mode: forwards;
}
```

### 3. Fade In Up
```css
/**
 * Fade In Up Animation
 * Description: Fades in while moving upward
 * Use case: List items, cards, content blocks
 * Performance: Uses transform for movement (GPU-accelerated)
 */
@keyframes fadeInUp {
  from {
    opacity: 0;
    transform: translateY(20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in-up {
  animation: fadeInUp 0.5s ease-out;
}
```

### 4. Fade In Down
```css
/**
 * Fade In Down Animation
 * Description: Fades in while moving downward
 * Use case: Dropdown menus, notifications, alerts
 * Performance: GPU-accelerated
 */
@keyframes fadeInDown {
  from {
    opacity: 0;
    transform: translateY(-20px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.fade-in-down {
  animation: fadeInDown 0.5s ease-out;
}
```

### 5. Fade In Left
```css
/**
 * Fade In Left Animation
 * Description: Fades in while moving from left
 * Use case: Sidebar panels, side navigation
 * Performance: GPU-accelerated
 */
@keyframes fadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.fade-in-left {
  animation: fadeInLeft 0.5s ease-out;
}
```

### 6. Fade In Right
```css
/**
 * Fade In Right Animation
 * Description: Fades in while moving from right
 * Use case: Side panels, shopping cart drawers
 * Performance: GPU-accelerated
 */
@keyframes fadeInRight {
  from {
    opacity: 0;
    transform: translateX(20px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

.fade-in-right {
  animation: fadeInRight 0.5s ease-out;
}
```

---

## Slide Animations

### 7. Slide In Left
```css
/**
 * Slide In Left Animation
 * Description: Slides element in from the left edge
 * Use case: Mobile menus, drawer navigation
 * Performance: GPU-accelerated transform
 */
@keyframes slideInLeft {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}

.slide-in-left {
  animation: slideInLeft 0.3s ease-out;
}
```

### 8. Slide In Right
```css
/**
 * Slide In Right Animation
 * Description: Slides element in from the right edge
 * Use case: Shopping carts, filter panels
 * Performance: GPU-accelerated transform
 */
@keyframes slideInRight {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0);
  }
}

.slide-in-right {
  animation: slideInRight 0.3s ease-out;
}
```

### 9. Slide In Up
```css
/**
 * Slide In Up Animation
 * Description: Slides element upward from bottom
 * Use case: Bottom sheets, mobile modals
 * Performance: GPU-accelerated transform
 */
@keyframes slideInUp {
  from {
    transform: translateY(100%);
  }
  to {
    transform: translateY(0);
  }
}

.slide-in-up {
  animation: slideInUp 0.3s ease-out;
}
```

### 10. Slide In Down
```css
/**
 * Slide In Down Animation
 * Description: Slides element downward from top
 * Use case: Top notification bars, banners
 * Performance: GPU-accelerated transform
 */
@keyframes slideInDown {
  from {
    transform: translateY(-100%);
  }
  to {
    transform: translateY(0);
  }
}

.slide-in-down {
  animation: slideInDown 0.3s ease-out;
}
```

### 11. Slide Out Left
```css
/**
 * Slide Out Left Animation
 * Description: Slides element out to the left
 * Use case: Dismissing panels, swipe actions
 * Performance: GPU-accelerated transform
 */
@keyframes slideOutLeft {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}

.slide-out-left {
  animation: slideOutLeft 0.3s ease-in;
  animation-fill-mode: forwards;
}
```

---

## Scale Animations

### 12. Scale In
```css
/**
 * Scale In Animation
 * Description: Grows element from small to full size
 * Use case: Modals, pop-ups, button interactions
 * Performance: GPU-accelerated scale transform
 */
@keyframes scaleIn {
  from {
    opacity: 0;
    transform: scale(0.8);
  }
  to {
    opacity: 1;
    transform: scale(1);
  }
}

.scale-in {
  animation: scaleIn 0.3s ease-out;
}
```

### 13. Scale Out
```css
/**
 * Scale Out Animation
 * Description: Shrinks element from full size to small
 * Use case: Dismissing modals, closing pop-ups
 * Performance: GPU-accelerated scale transform
 */
@keyframes scaleOut {
  from {
    opacity: 1;
    transform: scale(1);
  }
  to {
    opacity: 0;
    transform: scale(0.8);
  }
}

.scale-out {
  animation: scaleOut 0.3s ease-in;
  animation-fill-mode: forwards;
}
```

### 14. Scale Up
```css
/**
 * Scale Up Animation
 * Description: Scales element to larger size
 * Use case: Hover effects, focus states, emphasis
 * Performance: GPU-accelerated
 */
@keyframes scaleUp {
  from {
    transform: scale(1);
  }
  to {
    transform: scale(1.1);
  }
}

.scale-up {
  animation: scaleUp 0.2s ease-out;
  animation-fill-mode: forwards;
}
```

### 15. Scale Down
```css
/**
 * Scale Down Animation
 * Description: Scales element to smaller size
 * Use case: Click effects, pressed states
 * Performance: GPU-accelerated
 */
@keyframes scaleDown {
  from {
    transform: scale(1);
  }
  to {
    transform: scale(0.95);
  }
}

.scale-down {
  animation: scaleDown 0.2s ease-out;
  animation-fill-mode: forwards;
}
```

### 16. Scale Bounce
```css
/**
 * Scale Bounce Animation
 * Description: Scales with elastic bounce effect
 * Use case: Success states, confirmations, playful interactions
 * Performance: GPU-accelerated
 */
@keyframes scaleBounce {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.15);
  }
  70% {
    transform: scale(0.9);
  }
  100% {
    transform: scale(1);
  }
}

.scale-bounce {
  animation: scaleBounce 0.5s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

---

## Rotate Animations

### 17. Rotate In
```css
/**
 * Rotate In Animation
 * Description: Rotates and fades in element
 * Use case: Card flips, revealing content
 * Performance: GPU-accelerated rotate
 */
@keyframes rotateIn {
  from {
    opacity: 0;
    transform: rotate(-180deg);
  }
  to {
    opacity: 1;
    transform: rotate(0deg);
  }
}

.rotate-in {
  animation: rotateIn 0.5s ease-out;
}
```

### 18. Rotate 360
```css
/**
 * Rotate 360 Animation
 * Description: Full 360-degree rotation
 * Use case: Loading spinners, refresh icons
 * Performance: GPU-accelerated
 */
@keyframes rotate360 {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.rotate-360 {
  animation: rotate360 1s linear infinite;
}
```

### 19. Rotate Scale In
```css
/**
 * Rotate Scale In Animation
 * Description: Combines rotation with scaling
 * Use case: Dynamic entrances, attention grabbers
 * Performance: GPU-accelerated
 */
@keyframes rotateScaleIn {
  from {
    opacity: 0;
    transform: rotate(-180deg) scale(0);
  }
  to {
    opacity: 1;
    transform: rotate(0deg) scale(1);
  }
}

.rotate-scale-in {
  animation: rotateScaleIn 0.5s ease-out;
}
```

### 20. Rotate Y (3D Flip)
```css
/**
 * Rotate Y 3D Flip Animation
 * Description: 3D rotation along Y-axis
 * Use case: Card flips, pricing tables, before/after
 * Performance: Uses 3D transforms
 */
@keyframes rotateY {
  from {
    transform: perspective(1000px) rotateY(0deg);
  }
  to {
    transform: perspective(1000px) rotateY(360deg);
  }
}

.rotate-y {
  animation: rotateY 0.8s ease-in-out;
}
```

### 21. Rotate X (3D Flip)
```css
/**
 * Rotate X 3D Flip Animation
 * Description: 3D rotation along X-axis
 * Use case: Dropdown reveals, flip cards
 * Performance: Uses 3D transforms
 */
@keyframes rotateX {
  from {
    transform: perspective(1000px) rotateX(0deg);
  }
  to {
    transform: perspective(1000px) rotateX(360deg);
  }
}

.rotate-x {
  animation: rotateX 0.8s ease-in-out;
}
```

---

## Bounce Animations

### 22. Bounce In
```css
/**
 * Bounce In Animation
 * Description: Bouncy entrance animation
 * Use case: Playful UI elements, notifications
 * Performance: GPU-accelerated scale
 */
@keyframes bounceIn {
  0% {
    opacity: 0;
    transform: scale(0.3);
  }
  50% {
    opacity: 1;
    transform: scale(1.05);
  }
  70% {
    transform: scale(0.9);
  }
  100% {
    transform: scale(1);
  }
}

.bounce-in {
  animation: bounceIn 0.6s cubic-bezier(0.68, -0.55, 0.265, 1.55);
}
```

### 23. Bounce
```css
/**
 * Bounce Animation
 * Description: Continuous bouncing effect
 * Use case: Scroll indicators, call-to-action buttons
 * Performance: GPU-accelerated translateY
 */
@keyframes bounce {
  0%, 20%, 50%, 80%, 100% {
    transform: translateY(0);
  }
  40% {
    transform: translateY(-20px);
  }
  60% {
    transform: translateY(-10px);
  }
}

.bounce {
  animation: bounce 2s infinite;
}
```

### 24. Bounce In Up
```css
/**
 * Bounce In Up Animation
 * Description: Bounces in from below
 * Use case: Toast notifications, bottom sheets
 * Performance: GPU-accelerated
 */
@keyframes bounceInUp {
  0% {
    opacity: 0;
    transform: translateY(100px);
  }
  60% {
    opacity: 1;
    transform: translateY(-10px);
  }
  80% {
    transform: translateY(5px);
  }
  100% {
    transform: translateY(0);
  }
}

.bounce-in-up {
  animation: bounceInUp 0.8s ease-out;
}
```

### 25. Bounce In Down
```css
/**
 * Bounce In Down Animation
 * Description: Bounces in from above
 * Use case: Top notifications, header alerts
 * Performance: GPU-accelerated
 */
@keyframes bounceInDown {
  0% {
    opacity: 0;
    transform: translateY(-100px);
  }
  60% {
    opacity: 1;
    transform: translateY(10px);
  }
  80% {
    transform: translateY(-5px);
  }
  100% {
    transform: translateY(0);
  }
}

.bounce-in-down {
  animation: bounceInDown 0.8s ease-out;
}
```

---

## Flip Animations

### 26. Flip In X
```css
/**
 * Flip In X Animation
 * Description: 3D flip along X-axis entrance
 * Use case: Card reveals, content transitions
 * Performance: 3D transforms with backface-visibility
 */
@keyframes flipInX {
  from {
    transform: perspective(400px) rotateX(90deg);
    opacity: 0;
  }
  40% {
    transform: perspective(400px) rotateX(-10deg);
  }
  70% {
    transform: perspective(400px) rotateX(10deg);
  }
  100% {
    transform: perspective(400px) rotateX(0deg);
    opacity: 1;
  }
}

.flip-in-x {
  animation: flipInX 0.75s ease-out;
  backface-visibility: visible;
}
```

### 27. Flip In Y
```css
/**
 * Flip In Y Animation
 * Description: 3D flip along Y-axis entrance
 * Use case: Card reveals, pricing toggles
 * Performance: 3D transforms with backface-visibility
 */
@keyframes flipInY {
  from {
    transform: perspective(400px) rotateY(90deg);
    opacity: 0;
  }
  40% {
    transform: perspective(400px) rotateY(-10deg);
  }
  70% {
    transform: perspective(400px) rotateY(10deg);
  }
  100% {
    transform: perspective(400px) rotateY(0deg);
    opacity: 1;
  }
}

.flip-in-y {
  animation: flipInY 0.75s ease-out;
  backface-visibility: visible;
}
```

### 28. Flip
```css
/**
 * Flip Animation
 * Description: Simple 180-degree flip
 * Use case: Card flips, reveal animations
 * Performance: 3D transforms
 */
@keyframes flip {
  from {
    transform: perspective(400px) rotateY(0);
  }
  to {
    transform: perspective(400px) rotateY(180deg);
  }
}

.flip {
  animation: flip 0.6s ease-in-out;
}
```

---

## Shake & Wobble Animations

### 29. Shake
```css
/**
 * Shake Animation
 * Description: Horizontal shaking effect
 * Use case: Error states, invalid inputs, attention
 * Performance: GPU-accelerated translateX
 */
@keyframes shake {
  0%, 100% {
    transform: translateX(0);
  }
  10%, 30%, 50%, 70%, 90% {
    transform: translateX(-10px);
  }
  20%, 40%, 60%, 80% {
    transform: translateX(10px);
  }
}

.shake {
  animation: shake 0.6s ease-in-out;
}
```

### 30. Shake Vertical
```css
/**
 * Shake Vertical Animation
 * Description: Vertical shaking effect
 * Use case: Error emphasis, form validation
 * Performance: GPU-accelerated translateY
 */
@keyframes shakeVertical {
  0%, 100% {
    transform: translateY(0);
  }
  10%, 30%, 50%, 70%, 90% {
    transform: translateY(-8px);
  }
  20%, 40%, 60%, 80% {
    transform: translateY(8px);
  }
}

.shake-vertical {
  animation: shakeVertical 0.6s ease-in-out;
}
```

### 31. Wobble
```css
/**
 * Wobble Animation
 * Description: Wobbling rotation effect
 * Use case: Playful interactions, notifications
 * Performance: GPU-accelerated rotate and translateX
 */
@keyframes wobble {
  0% {
    transform: translateX(0) rotate(0deg);
  }
  15% {
    transform: translateX(-25%) rotate(-5deg);
  }
  30% {
    transform: translateX(20%) rotate(3deg);
  }
  45% {
    transform: translateX(-15%) rotate(-3deg);
  }
  60% {
    transform: translateX(10%) rotate(2deg);
  }
  75% {
    transform: translateX(-5%) rotate(-1deg);
  }
  100% {
    transform: translateX(0) rotate(0deg);
  }
}

.wobble {
  animation: wobble 0.8s ease-in-out;
}
```

### 32. Jello
```css
/**
 * Jello Animation
 * Description: Jelly-like wobble effect
 * Use case: Playful interactions, button presses
 * Performance: GPU-accelerated skew
 */
@keyframes jello {
  0%, 100% {
    transform: skewX(0deg) skewY(0deg);
  }
  30% {
    transform: skewX(25deg) skewY(25deg);
  }
  40% {
    transform: skewX(-15deg) skewY(-15deg);
  }
  50% {
    transform: skewX(15deg) skewY(15deg);
  }
  65% {
    transform: skewX(-5deg) skewY(-5deg);
  }
  75% {
    transform: skewX(5deg) skewY(5deg);
  }
}

.jello {
  animation: jello 0.9s ease-in-out;
}
```

### 33. Rubber Band
```css
/**
 * Rubber Band Animation
 * Description: Elastic stretching effect
 * Use case: Emphasis, playful interactions
 * Performance: GPU-accelerated scale
 */
@keyframes rubberBand {
  0% {
    transform: scaleX(1);
  }
  30% {
    transform: scaleX(1.25) scaleY(0.75);
  }
  40% {
    transform: scaleX(0.75) scaleY(1.25);
  }
  50% {
    transform: scaleX(1.15) scaleY(0.85);
  }
  65% {
    transform: scaleX(0.95) scaleY(1.05);
  }
  75% {
    transform: scaleX(1.05) scaleY(0.95);
  }
  100% {
    transform: scaleX(1) scaleY(1);
  }
}

.rubber-band {
  animation: rubberBand 1s ease-in-out;
}
```

---

## Blur & Focus Animations

### 34. Blur In
```css
/**
 * Blur In Animation
 * Description: Transitions from blurred to sharp
 * Use case: Image loading, content reveals
 * Performance: Filter property (may be CPU-intensive)
 */
@keyframes blurIn {
  from {
    filter: blur(10px);
    opacity: 0;
  }
  to {
    filter: blur(0);
    opacity: 1;
  }
}

.blur-in {
  animation: blurIn 0.6s ease-out;
}
```

### 35. Blur Out
```css
/**
 * Blur Out Animation
 * Description: Transitions from sharp to blurred
 * Use case: Exit animations, background transitions
 * Performance: Filter property (may be CPU-intensive)
 */
@keyframes blurOut {
  from {
    filter: blur(0);
    opacity: 1;
  }
  to {
    filter: blur(10px);
    opacity: 0;
  }
}

.blur-out {
  animation: blurOut 0.6s ease-out;
  animation-fill-mode: forwards;
}
```

### 36. Focus In
```css
/**
 * Focus In Animation
 * Description: Zooms in with blur to focus effect
 * Use case: Hero images, spotlight effects
 * Performance: Combines transform and filter
 */
@keyframes focusIn {
  from {
    filter: blur(12px);
    opacity: 0;
    transform: scale(0.95);
  }
  to {
    filter: blur(0);
    opacity: 1;
    transform: scale(1);
  }
}

.focus-in {
  animation: focusIn 0.8s ease-out;
}
```

---

## Glow & Pulse Animations

### 37. Pulse
```css
/**
 * Pulse Animation
 * Description: Subtle pulsing scale effect
 * Use case: Live indicators, breathing buttons
 * Performance: GPU-accelerated scale
 */
@keyframes pulse {
  0% {
    transform: scale(1);
  }
  50% {
    transform: scale(1.05);
  }
  100% {
    transform: scale(1);
  }
}

.pulse {
  animation: pulse 2s ease-in-out infinite;
}
```

### 38. Pulse Glow
```css
/**
 * Pulse Glow Animation
 * Description: Pulsing glow effect with box-shadow
 * Use case: Notifications, alerts, live status
 * Performance: Box-shadow (may affect performance)
 */
@keyframes pulseGlow {
  0% {
    box-shadow: 0 0 0 0 rgba(59, 130, 246, 0.7);
  }
  70% {
    box-shadow: 0 0 0 10px rgba(59, 130, 246, 0);
  }
  100% {
    box-shadow: 0 0 0 0 rgba(59, 130, 246, 0);
  }
}

.pulse-glow {
  animation: pulseGlow 2s infinite;
}
```

### 39. Glow
```css
/**
 * Glow Animation
 * Description: Continuous glowing effect
 * Use case: Highlighting, emphasis, hover states
 * Performance: Filter and opacity changes
 */
@keyframes glow {
  0%, 100% {
    filter: drop-shadow(0 0 2px currentColor);
  }
  50% {
    filter: drop-shadow(0 0 20px currentColor);
  }
}

.glow {
  animation: glow 2s ease-in-out infinite;
}
```

### 40. Heartbeat
```css
/**
 * Heartbeat Animation
 * Description: Two-beat pulse pattern
 * Use case: Like buttons, favorite icons
 * Performance: GPU-accelerated scale
 */
@keyframes heartbeat {
  0% {
    transform: scale(1);
  }
  14% {
    transform: scale(1.3);
  }
  28% {
    transform: scale(1);
  }
  42% {
    transform: scale(1.3);
  }
  70% {
    transform: scale(1);
  }
}

.heartbeat {
  animation: heartbeat 1.3s ease-in-out infinite;
}
```

---

## Swing & Pendulum Animations

### 41. Swing
```css
/**
 * Swing Animation
 * Description: Pendulum swinging effect
 * Use case: Hanging elements, playful interactions
 * Performance: GPU-accelerated rotate
 */
@keyframes swing {
  20% {
    transform: rotate(15deg);
  }
  40% {
    transform: rotate(-10deg);
  }
  60% {
    transform: rotate(5deg);
  }
  80% {
    transform: rotate(-5deg);
  }
  100% {
    transform: rotate(0deg);
  }
}

.swing {
  transform-origin: top center;
  animation: swing 1s ease-in-out;
}
```

### 42. Tada
```css
/**
 * Tada Animation
 * Description: Attention-grabbing scale and rotation
 * Use case: Success messages, achievements, celebrations
 * Performance: GPU-accelerated
 */
@keyframes tada {
  0% {
    transform: scale(1) rotate(0deg);
  }
  10%, 20% {
    transform: scale(0.9) rotate(-3deg);
  }
  30%, 50%, 70%, 90% {
    transform: scale(1.1) rotate(3deg);
  }
  40%, 60%, 80% {
    transform: scale(1.1) rotate(-3deg);
  }
  100% {
    transform: scale(1) rotate(0deg);
  }
}

.tada {
  animation: tada 1s ease-in-out;
}
```

---

## Advanced Animations

### 43. Zoom In
```css
/**
 * Zoom In Animation
 * Description: Zooms in from center with opacity
 * Use case: Image galleries, modals, lightboxes
 * Performance: GPU-accelerated
 */
@keyframes zoomIn {
  from {
    opacity: 0;
    transform: scale(0.3);
  }
  50% {
    opacity: 1;
  }
  to {
    transform: scale(1);
  }
}

.zoom-in {
  animation: zoomIn 0.5s ease-out;
}
```

### 44. Zoom Out
```css
/**
 * Zoom Out Animation
 * Description: Zooms out from center with opacity
 * Use case: Closing modals, dismissing overlays
 * Performance: GPU-accelerated
 */
@keyframes zoomOut {
  from {
    opacity: 1;
    transform: scale(1);
  }
  50% {
    opacity: 0;
    transform: scale(0.3);
  }
  to {
    opacity: 0;
  }
}

.zoom-out {
  animation: zoomOut 0.5s ease-in;
  animation-fill-mode: forwards;
}
```

### 45. Roll In
```css
/**
 * Roll In Animation
 * Description: Rolls in from left with rotation
 * Use case: Playful entrances, game elements
 * Performance: GPU-accelerated
 */
@keyframes rollIn {
  from {
    opacity: 0;
    transform: translateX(-100%) rotate(-120deg);
  }
  to {
    opacity: 1;
    transform: translateX(0) rotate(0deg);
  }
}

.roll-in {
  animation: rollIn 0.6s ease-out;
}
```

### 46. Roll Out
```css
/**
 * Roll Out Animation
 * Description: Rolls out to right with rotation
 * Use case: Playful exits, dismissing elements
 * Performance: GPU-accelerated
 */
@keyframes rollOut {
  from {
    opacity: 1;
    transform: translateX(0) rotate(0deg);
  }
  to {
    opacity: 0;
    transform: translateX(100%) rotate(120deg);
  }
}

.roll-out {
  animation: rollOut 0.6s ease-in;
  animation-fill-mode: forwards;
}
```

### 47. Light Speed In Right
```css
/**
 * Light Speed In Right Animation
 * Description: Fast entrance from right with skew
 * Use case: Fast reveals, speed emphasis
 * Performance: GPU-accelerated
 */
@keyframes lightSpeedInRight {
  from {
    transform: translateX(100%) skewX(-30deg);
    opacity: 0;
  }
  60% {
    transform: skewX(20deg);
    opacity: 1;
  }
  80% {
    transform: skewX(-5deg);
  }
  100% {
    transform: translateX(0) skewX(0deg);
  }
}

.light-speed-in-right {
  animation: lightSpeedInRight 0.6s ease-out;
}
```

### 48. Hinge
```css
/**
 * Hinge Animation
 * Description: Falls and rotates like a door hinge
 * Use case: Dramatic exits, error states
 * Performance: GPU-accelerated
 */
@keyframes hinge {
  0% {
    transform-origin: top left;
    animation-timing-function: ease-in-out;
  }
  20%, 60% {
    transform: rotate(80deg);
    transform-origin: top left;
    animation-timing-function: ease-in-out;
  }
  40%, 80% {
    transform: rotate(60deg);
    transform-origin: top left;
    animation-timing-function: ease-in-out;
    opacity: 1;
  }
  100% {
    transform: translateY(700px);
    opacity: 0;
  }
}

.hinge {
  animation: hinge 2s ease-in-out;
  animation-fill-mode: forwards;
}
```

### 49. Jack In The Box
```css
/**
 * Jack In The Box Animation
 * Description: Pops up with rotation and scale
 * Use case: Surprise elements, playful reveals
 * Performance: GPU-accelerated
 */
@keyframes jackInTheBox {
  from {
    opacity: 0;
    transform: scale(0.1) rotate(30deg);
    transform-origin: center bottom;
  }
  50% {
    transform: rotate(-10deg);
  }
  70% {
    transform: rotate(3deg);
  }
  to {
    opacity: 1;
    transform: scale(1) rotate(0deg);
  }
}

.jack-in-the-box {
  animation: jackInTheBox 0.8s ease-out;
}
```

### 50. Flash
```css
/**
 * Flash Animation
 * Description: Rapid opacity flashing
 * Use case: Alerts, attention grabbers, notifications
 * Performance: GPU-accelerated opacity
 */
@keyframes flash {
  0%, 50%, 100% {
    opacity: 1;
  }
  25%, 75% {
    opacity: 0;
  }
}

.flash {
  animation: flash 1s ease-in-out;
}
```

---

## Timing Functions Reference

### CSS Timing Function Presets

```css
/**
 * Timing Functions Guide
 * Description: Comprehensive reference for animation timing
 * Use case: Fine-tuning animation feel and responsiveness
 */

/* Linear - Constant speed throughout */
.timing-linear {
  animation-timing-function: linear;
}

/* Ease (default) - Slow start, fast middle, slow end */
.timing-ease {
  animation-timing-function: ease;
}

/* Ease-In - Slow start, fast end */
.timing-ease-in {
  animation-timing-function: ease-in;
}

/* Ease-Out - Fast start, slow end */
.timing-ease-out {
  animation-timing-function: ease-out;
}

/* Ease-In-Out - Slow start and end, fast middle */
.timing-ease-in-out {
  animation-timing-function: ease-in-out;
}
```

### Custom Cubic Bezier Functions

```css
/**
 * Custom Timing Functions
 * Description: Advanced easing for specific effects
 * Tool: https://cubic-bezier.com for visualization
 */

/* Elastic - Bouncy overshoot */
.timing-elastic {
  animation-timing-function: cubic-bezier(0.68, -0.55, 0.265, 1.55);
}

/* Fast Out Slow In (Material Design) */
.timing-fast-out-slow-in {
  animation-timing-function: cubic-bezier(0.4, 0, 0.2, 1);
}

/* Linear Out Slow In (Material Design) */
.timing-linear-out-slow-in {
  animation-timing-function: cubic-bezier(0, 0, 0.2, 1);
}

/* Fast Out Linear In (Material Design) */
.timing-fast-out-linear-in {
  animation-timing-function: cubic-bezier(0.4, 0, 1, 1);
}

/* Smooth - Very smooth acceleration/deceleration */
.timing-smooth {
  animation-timing-function: cubic-bezier(0.25, 0.46, 0.45, 0.94);
}

/* Snap - Quick snap effect */
.timing-snap {
  animation-timing-function: cubic-bezier(0, 1.5, 1, 1.5);
}

/* Anticipate - Pulls back before moving forward */
.timing-anticipate {
  animation-timing-function: cubic-bezier(0.36, 0, 0.66, -0.56);
}

/* Overshoot - Goes beyond target then settles */
.timing-overshoot {
  animation-timing-function: cubic-bezier(0.34, 1.56, 0.64, 1);
}
```

### Steps Timing Function

```css
/**
 * Steps Timing Function
 * Description: Creates discrete animation steps
 * Use case: Sprite animations, typewriter effects
 */

/* Jump at start of each step */
.timing-steps-start {
  animation-timing-function: steps(4, jump-start);
}

/* Jump at end of each step */
.timing-steps-end {
  animation-timing-function: steps(4, jump-end);
}

/* Jump at both start and end */
.timing-steps-both {
  animation-timing-function: steps(4, jump-both);
}

/* No jump at start or end */
.timing-steps-none {
  animation-timing-function: steps(4, jump-none);
}
```

---

## Common UI Animation Recipes

### Modal/Dialog Animations

```css
/**
 * Modal Fade Scale Animation
 * Description: Modern modal entrance with backdrop
 * Use case: Modal dialogs, pop-ups
 * Performance: GPU-accelerated
 */

/* Backdrop fade in */
@keyframes modalBackdropFadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

/* Modal content scale in */
@keyframes modalContentScaleIn {
  from {
    opacity: 0;
    transform: scale(0.9) translateY(-20px);
  }
  to {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
}

.modal-backdrop {
  animation: modalBackdropFadeIn 0.2s ease-out;
}

.modal-content {
  animation: modalContentScaleIn 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

/* Modal exit animations */
@keyframes modalBackdropFadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}

@keyframes modalContentScaleOut {
  from {
    opacity: 1;
    transform: scale(1) translateY(0);
  }
  to {
    opacity: 0;
    transform: scale(0.9) translateY(-20px);
  }
}

.modal-backdrop-exit {
  animation: modalBackdropFadeOut 0.2s ease-in;
  animation-fill-mode: forwards;
}

.modal-content-exit {
  animation: modalContentScaleOut 0.2s ease-in;
  animation-fill-mode: forwards;
}
```

### Toast/Notification Animations

```css
/**
 * Toast Notification Animation
 * Description: Slide in from top with bounce
 * Use case: Toast notifications, alerts
 * Performance: GPU-accelerated
 */
@keyframes toastSlideIn {
  from {
    transform: translateY(-100%) translateX(-50%);
    opacity: 0;
  }
  to {
    transform: translateY(0) translateX(-50%);
    opacity: 1;
  }
}

@keyframes toastSlideOut {
  from {
    transform: translateY(0) translateX(-50%);
    opacity: 1;
  }
  to {
    transform: translateY(-100%) translateX(-50%);
    opacity: 0;
  }
}

.toast-enter {
  animation: toastSlideIn 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.toast-exit {
  animation: toastSlideOut 0.2s ease-in;
  animation-fill-mode: forwards;
}

/* Toast from bottom */
@keyframes toastSlideInBottom {
  from {
    transform: translateY(100%);
    opacity: 0;
  }
  to {
    transform: translateY(0);
    opacity: 1;
  }
}

.toast-bottom {
  animation: toastSlideInBottom 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}
```

### Dropdown Menu Animations

```css
/**
 * Dropdown Menu Animation
 * Description: Smooth dropdown reveal with origin
 * Use case: Navigation menus, select dropdowns
 * Performance: GPU-accelerated with proper origin
 */
@keyframes dropdownFadeIn {
  from {
    opacity: 0;
    transform: scaleY(0.95) translateY(-10px);
    transform-origin: top;
  }
  to {
    opacity: 1;
    transform: scaleY(1) translateY(0);
    transform-origin: top;
  }
}

@keyframes dropdownFadeOut {
  from {
    opacity: 1;
    transform: scaleY(1) translateY(0);
    transform-origin: top;
  }
  to {
    opacity: 0;
    transform: scaleY(0.95) translateY(-10px);
    transform-origin: top;
  }
}

.dropdown-enter {
  animation: dropdownFadeIn 0.15s cubic-bezier(0.16, 1, 0.3, 1);
}

.dropdown-exit {
  animation: dropdownFadeOut 0.1s ease-in;
  animation-fill-mode: forwards;
}
```

### Accordion/Collapse Animations

```css
/**
 * Accordion Animation
 * Description: Smooth height transitions for accordions
 * Use case: FAQ sections, collapsible panels
 * Performance: Uses max-height with overflow
 * Note: For better performance with dynamic heights, use JavaScript
 */
@keyframes accordionExpand {
  from {
    max-height: 0;
    opacity: 0;
  }
  to {
    max-height: 1000px; /* Adjust based on content */
    opacity: 1;
  }
}

@keyframes accordionCollapse {
  from {
    max-height: 1000px;
    opacity: 1;
  }
  to {
    max-height: 0;
    opacity: 0;
  }
}

.accordion-expand {
  animation: accordionExpand 0.3s ease-out;
  overflow: hidden;
}

.accordion-collapse {
  animation: accordionCollapse 0.3s ease-in;
  animation-fill-mode: forwards;
  overflow: hidden;
}
```

### Skeleton Loading Animation

```css
/**
 * Skeleton Shimmer Animation
 * Description: Loading placeholder shimmer effect
 * Use case: Content loading states, skeleton screens
 * Performance: GPU-accelerated gradient animation
 */
@keyframes shimmer {
  0% {
    background-position: -1000px 0;
  }
  100% {
    background-position: 1000px 0;
  }
}

.skeleton {
  background: linear-gradient(
    90deg,
    #f0f0f0 0%,
    #f8f8f8 50%,
    #f0f0f0 100%
  );
  background-size: 1000px 100%;
  animation: shimmer 2s infinite linear;
}

/* Alternative pulse skeleton */
@keyframes skeletonPulse {
  0%, 100% {
    opacity: 1;
  }
  50% {
    opacity: 0.5;
  }
}

.skeleton-pulse {
  background: #f0f0f0;
  animation: skeletonPulse 1.5s ease-in-out infinite;
}
```

### Tooltip Animations

```css
/**
 * Tooltip Animation
 * Description: Subtle tooltip appearance
 * Use case: Hover tooltips, help text
 * Performance: GPU-accelerated
 */
@keyframes tooltipFadeIn {
  from {
    opacity: 0;
    transform: translateY(5px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

.tooltip-enter {
  animation: tooltipFadeIn 0.2s cubic-bezier(0.16, 1, 0.3, 1);
}

/* Tooltip with different directions */
@keyframes tooltipFadeInTop {
  from {
    opacity: 0;
    transform: translateY(-5px);
  }
  to {
    opacity: 1;
    transform: translateY(0);
  }
}

@keyframes tooltipFadeInLeft {
  from {
    opacity: 0;
    transform: translateX(-5px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}

@keyframes tooltipFadeInRight {
  from {
    opacity: 0;
    transform: translateX(5px);
  }
  to {
    opacity: 1;
    transform: translateX(0);
  }
}
```

### Card Hover Effects

```css
/**
 * Card Lift Animation
 * Description: Elevates card on hover
 * Use case: Product cards, article previews
 * Performance: GPU-accelerated transform and shadow
 */
.card {
  transition: transform 0.3s cubic-bezier(0.16, 1, 0.3, 1),
              box-shadow 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.card:hover {
  transform: translateY(-8px);
  box-shadow: 0 20px 40px rgba(0, 0, 0, 0.15);
}

/* Card flip effect */
.card-flip-container {
  perspective: 1000px;
}

@keyframes cardFlip {
  from {
    transform: rotateY(0deg);
  }
  to {
    transform: rotateY(180deg);
  }
}

.card-flip {
  transition: transform 0.6s;
  transform-style: preserve-3d;
}

.card-flip:hover {
  transform: rotateY(180deg);
}

.card-front,
.card-back {
  backface-visibility: hidden;
}

.card-back {
  transform: rotateY(180deg);
}
```

### Button Press Animation

```css
/**
 * Button Press Animation
 * Description: Tactile button feedback
 * Use case: All interactive buttons
 * Performance: GPU-accelerated scale
 */
.button {
  transition: transform 0.1s cubic-bezier(0.16, 1, 0.3, 1),
              box-shadow 0.1s cubic-bezier(0.16, 1, 0.3, 1);
}

.button:active {
  transform: scale(0.96);
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.2);
}

/* Button ripple effect */
@keyframes ripple {
  to {
    transform: scale(4);
    opacity: 0;
  }
}

.button-ripple {
  position: relative;
  overflow: hidden;
}

.button-ripple::after {
  content: '';
  position: absolute;
  top: 50%;
  left: 50%;
  width: 100px;
  height: 100px;
  background: rgba(255, 255, 255, 0.5);
  border-radius: 50%;
  transform: translate(-50%, -50%) scale(0);
  opacity: 0;
  pointer-events: none;
}

.button-ripple:active::after {
  animation: ripple 0.6s ease-out;
}
```

### Page Transition Animations

```css
/**
 * Page Transition Animations
 * Description: Smooth page changes for SPAs
 * Use case: Route changes, view transitions
 * Performance: GPU-accelerated
 */

/* Fade transition */
@keyframes pageFadeIn {
  from {
    opacity: 0;
  }
  to {
    opacity: 1;
  }
}

@keyframes pageFadeOut {
  from {
    opacity: 1;
  }
  to {
    opacity: 0;
  }
}

.page-enter {
  animation: pageFadeIn 0.3s ease-out;
}

.page-exit {
  animation: pageFadeOut 0.3s ease-in;
}

/* Slide transition */
@keyframes pageSlideInRight {
  from {
    transform: translateX(100%);
  }
  to {
    transform: translateX(0);
  }
}

@keyframes pageSlideOutLeft {
  from {
    transform: translateX(0);
  }
  to {
    transform: translateX(-100%);
  }
}

.page-slide-enter {
  animation: pageSlideInRight 0.4s cubic-bezier(0.16, 1, 0.3, 1);
}

.page-slide-exit {
  animation: pageSlideOutLeft 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  animation-fill-mode: forwards;
}
```

### Loading Spinner Animations

```css
/**
 * Loading Spinner Animations
 * Description: Various loading indicators
 * Use case: Content loading, async operations
 * Performance: GPU-accelerated rotations
 */

/* Standard spinner */
@keyframes spin {
  from {
    transform: rotate(0deg);
  }
  to {
    transform: rotate(360deg);
  }
}

.spinner {
  animation: spin 1s linear infinite;
}

/* Dots loader */
@keyframes dotPulse {
  0%, 80%, 100% {
    opacity: 0.3;
    transform: scale(0.8);
  }
  40% {
    opacity: 1;
    transform: scale(1);
  }
}

.dot-loader .dot:nth-child(1) {
  animation: dotPulse 1.4s ease-in-out infinite;
}

.dot-loader .dot:nth-child(2) {
  animation: dotPulse 1.4s ease-in-out 0.2s infinite;
}

.dot-loader .dot:nth-child(3) {
  animation: dotPulse 1.4s ease-in-out 0.4s infinite;
}

/* Progress bar */
@keyframes progressIndeterminate {
  0% {
    transform: translateX(-100%);
  }
  100% {
    transform: translateX(400%);
  }
}

.progress-indeterminate {
  animation: progressIndeterminate 1.5s cubic-bezier(0.65, 0.815, 0.735, 0.395) infinite;
}
```

---

## Scroll-Driven Animation Patterns

### Scroll-Triggered Fade In

```css
/**
 * Scroll Fade In Animation
 * Description: Elements fade in as they enter viewport
 * Use case: Landing pages, content reveals
 * Implementation: Requires Intersection Observer API or scroll-timeline
 */

/* Using Intersection Observer approach */
.scroll-fade {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.6s ease-out,
              transform 0.6s ease-out;
}

.scroll-fade.in-view {
  opacity: 1;
  transform: translateY(0);
}

/* Staggered children */
.scroll-fade.in-view .stagger-item {
  animation: fadeInUp 0.6s ease-out backwards;
}

.scroll-fade.in-view .stagger-item:nth-child(1) { animation-delay: 0.1s; }
.scroll-fade.in-view .stagger-item:nth-child(2) { animation-delay: 0.2s; }
.scroll-fade.in-view .stagger-item:nth-child(3) { animation-delay: 0.3s; }
.scroll-fade.in-view .stagger-item:nth-child(4) { animation-delay: 0.4s; }
```

### Parallax Scroll Effect

```css
/**
 * Parallax Scroll Animation
 * Description: Elements move at different speeds
 * Use case: Hero sections, visual depth
 * Implementation: Requires JavaScript for scroll position
 */
.parallax-slow {
  transition: transform 0.5s cubic-bezier(0.16, 1, 0.3, 1);
  will-change: transform;
}

/* Applied via JS: transform: translateY(scrollY * 0.5) */

.parallax-fast {
  transition: transform 0.3s cubic-bezier(0.16, 1, 0.3, 1);
  will-change: transform;
}

/* Applied via JS: transform: translateY(scrollY * -0.3) */
```

### Scroll Progress Indicator

```css
/**
 * Scroll Progress Animation
 * Description: Shows reading progress
 * Use case: Articles, long-form content
 * Implementation: JavaScript to update width
 */
@keyframes progressGrow {
  from {
    transform: scaleX(0);
  }
  to {
    transform: scaleX(1);
  }
}

.scroll-progress {
  transform-origin: left;
  transition: transform 0.2s ease-out;
  will-change: transform;
}

/* Applied via JS: transform: scaleX(scrollPercent) */
```

### Sticky Header with Animation

```css
/**
 * Sticky Header Animation
 * Description: Header shrinks/changes on scroll
 * Use case: Navigation headers
 * Performance: GPU-accelerated transform
 */
.header {
  position: sticky;
  top: 0;
  transition: transform 0.3s cubic-bezier(0.16, 1, 0.3, 1),
              background 0.3s ease,
              padding 0.3s ease,
              box-shadow 0.3s ease;
}

.header.scrolled {
  padding: 0.5rem 1rem;
  background: rgba(255, 255, 255, 0.95);
  backdrop-filter: blur(10px);
  box-shadow: 0 2px 10px rgba(0, 0, 0, 0.1);
}

/* Hide on scroll down, show on scroll up */
.header.hide {
  transform: translateY(-100%);
}

.header.show {
  transform: translateY(0);
}
```

### Scroll-Snap Animations

```css
/**
 * Scroll Snap Animation
 * Description: Smooth snapping between sections
 * Use case: Full-page scrolling, carousels
 * Performance: Native CSS scroll-snap
 */
.scroll-container {
  scroll-snap-type: y mandatory;
  scroll-behavior: smooth;
  overflow-y: scroll;
  height: 100vh;
}

.scroll-section {
  scroll-snap-align: start;
  height: 100vh;
}

/* Fade in sections as they snap */
.scroll-section {
  opacity: 0.5;
  transform: scale(0.95);
  transition: opacity 0.6s ease,
              transform 0.6s ease;
}

.scroll-section.active {
  opacity: 1;
  transform: scale(1);
}
```

---

## Performance Patterns

### GPU Acceleration Best Practices

```css
/**
 * GPU Acceleration Guide
 * Description: Patterns for hardware-accelerated animations
 * Performance: Forces GPU compositing for smooth 60fps
 */

/* Properties that trigger GPU acceleration: */
/* - transform (translate, scale, rotate)
   - opacity
   - filter
   - will-change */

/* GOOD - GPU accelerated */
.gpu-optimized {
  transform: translateZ(0); /* Force GPU layer */
  will-change: transform, opacity; /* Hint to browser */
}

/* Animate these properties freely */
@keyframes optimized {
  from {
    transform: translateX(0) scale(1);
    opacity: 0;
  }
  to {
    transform: translateX(100px) scale(1.2);
    opacity: 1;
  }
}

/* AVOID - CPU intensive */
.cpu-intensive {
  /* These trigger layout/paint on every frame */
  /* - width/height
     - top/left/right/bottom (without position: absolute)
     - margin/padding
     - border */
}

/* BAD - causes reflow */
@keyframes reflow-trigger {
  from { width: 100px; }
  to { width: 200px; }
}

/* GOOD - use transform instead */
@keyframes transform-alternative {
  from { transform: scaleX(1); }
  to { transform: scaleX(2); }
}
```

### Will-Change Optimization

```css
/**
 * Will-Change Property Guide
 * Description: Optimize specific animations
 * Warning: Use sparingly, only when needed
 */

/* Use will-change for animations you know will happen */
.animated-element {
  will-change: transform, opacity;
}

/* Remove will-change after animation completes */
.animated-element.animation-done {
  will-change: auto;
}

/* AVOID - Too broad, wastes memory */
.bad-will-change {
  will-change: transform, opacity, filter, background, color, width, height;
}

/* AVOID - On too many elements */
* {
  will-change: transform; /* Don't do this! */
}

/* GOOD - Targeted usage */
.modal-content {
  will-change: transform, opacity;
}

.modal-content.closed {
  will-change: auto;
}
```

### Animation Performance Checklist

```css
/**
 * Performance Optimization Checklist
 *
 * ✅ DO:
 * - Use transform and opacity for animations
 * - Enable GPU acceleration with translateZ(0)
 * - Use will-change for known animations
 * - Keep animations under 300ms for perceived instant
 * - Use requestAnimationFrame for JS animations
 * - Debounce scroll/resize listeners
 * - Use CSS containment when possible
 *
 * ❌ AVOID:
 * - Animating width, height, top, left
 * - Animating box-shadow (use opacity on pseudo-element)
 * - Animating many elements simultaneously
 * - Long-running will-change declarations
 * - Synchronous layouts (forced reflow)
 * - Complex box-shadow or filter animations
 */

/* CSS Containment for performance */
.contained-element {
  contain: layout style paint;
}

/* Optimize box-shadow animations */
.shadow-animation {
  position: relative;
}

.shadow-animation::before {
  content: '';
  position: absolute;
  inset: 0;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.3);
  opacity: 0;
  transition: opacity 0.3s ease;
  z-index: -1;
}

.shadow-animation:hover::before {
  opacity: 1;
}
```

### Reduce Motion Preference

```css
/**
 * Respect Prefers-Reduced-Motion
 * Description: Accessibility for motion-sensitive users
 * Requirement: WCAG 2.1 Level AA compliance
 */

/* Default animations */
.animated {
  animation: fadeInUp 0.6s ease-out;
}

/* Disable or reduce animations for users who prefer reduced motion */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
    scroll-behavior: auto !important;
  }

  /* Or provide gentler alternatives */
  .animated {
    animation: fadeIn 0.2s ease-out;
  }
}

/* Provide no-motion alternatives */
@media (prefers-reduced-motion: reduce) {
  .slide-in {
    animation: fadeIn 0.2s ease;
  }

  .bounce {
    animation: none;
  }

  .parallax {
    transform: none !important;
  }
}
```

---

## Accessibility Considerations

### Focus Animations

```css
/**
 * Accessible Focus Indicators
 * Description: Clear focus states for keyboard navigation
 * Requirement: WCAG 2.1 Level AA - 2.4.7 Focus Visible
 */

/* Enhanced focus indicator */
.button,
.link,
.input {
  outline: 2px solid transparent;
  outline-offset: 2px;
  transition: outline-color 0.2s ease,
              outline-offset 0.2s ease;
}

.button:focus-visible,
.link:focus-visible,
.input:focus-visible {
  outline-color: #3b82f6;
  outline-offset: 4px;
}

/* Animated focus ring */
@keyframes focusRing {
  0% {
    outline-width: 2px;
    outline-offset: 2px;
  }
  50% {
    outline-width: 3px;
    outline-offset: 4px;
  }
  100% {
    outline-width: 2px;
    outline-offset: 2px;
  }
}

.interactive:focus-visible {
  animation: focusRing 0.6s ease-out;
  outline: 2px solid #3b82f6;
}
```

### Screen Reader Considerations

```css
/**
 * Screen Reader Announcements
 * Description: Handle animations for assistive tech
 * Best Practice: Use aria-live regions for dynamic content
 */

/* Hide animation from screen readers during transition */
.animating[aria-hidden="true"] {
  animation: fadeIn 0.3s ease;
}

/* Visually hidden but available to screen readers */
.sr-only {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border-width: 0;
}

/* Loading state announcement */
.loading[aria-busy="true"] {
  animation: pulse 1.5s ease-in-out infinite;
}

/* Add visually hidden loading text for screen readers */
.loading::after {
  content: 'Loading...';
  /* Apply .sr-only styles */
}
```

### Animation Duration Guidelines

```css
/**
 * Timing Guidelines for Accessibility
 *
 * Quick (100-200ms):
 * - Hover effects
 * - Focus indicators
 * - Button presses
 *
 * Medium (200-400ms):
 * - Dropdowns
 * - Tooltips
 * - Small modals
 *
 * Slow (400-600ms):
 * - Page transitions
 * - Large modals
 * - Complex reveals
 *
 * Very Slow (600ms+):
 * - Decorative animations
 * - Loading indicators
 * - Background effects
 */

/* Instant feedback - hover/focus */
.instant {
  transition-duration: 0.15s;
}

/* Quick interactions - clicks/taps */
.quick {
  transition-duration: 0.2s;
}

/* Standard UI animations */
.standard {
  transition-duration: 0.3s;
}

/* Emphasized transitions */
.emphasized {
  transition-duration: 0.5s;
}
```

### Color Contrast with Animations

```css
/**
 * Maintain Color Contrast During Animations
 * Description: Ensure WCAG AA compliance (4.5:1 ratio)
 * Requirement: WCAG 2.1 Level AA - 1.4.3 Contrast
 */

/* Ensure contrast is maintained throughout animation */
@keyframes colorFade {
  from {
    color: #000000; /* 21:1 ratio on white */
    background: #ffffff;
  }
  to {
    color: #ffffff; /* 21:1 ratio on black */
    background: #000000;
  }
}

/* AVOID - intermediate frames may fail contrast */
@keyframes badColorFade {
  from {
    color: #333333;
  }
  50% {
    color: #888888; /* May not meet 4.5:1 */
  }
  to {
    color: #ffffff;
  }
}
```

---

## Browser Compatibility Notes

### Modern Features Support

```css
/**
 * Browser Support Matrix
 *
 * ✅ Widely Supported (95%+):
 * - Basic CSS animations (@keyframes, animation)
 * - 2D transforms (translate, rotate, scale)
 * - Opacity transitions
 * - Transform-origin
 *
 * ⚠️ Modern Browsers (85%+):
 * - 3D transforms (perspective, rotateX/Y/Z)
 * - backdrop-filter
 * - will-change
 * - prefers-reduced-motion
 *
 * ⚠️ Cutting Edge (<70%):
 * - @scroll-timeline
 * - animation-timeline
 * - View Transitions API
 * - Individual transform properties
 */

/* Safe cross-browser animation */
.cross-browser-safe {
  animation: fadeIn 0.3s ease;
  transform: translateX(20px);
}

/* With fallback for older browsers */
.modern-with-fallback {
  /* Fallback for no backdrop-filter support */
  background: rgba(255, 255, 255, 0.9);
}

@supports (backdrop-filter: blur(10px)) {
  .modern-with-fallback {
    background: rgba(255, 255, 255, 0.7);
    backdrop-filter: blur(10px);
  }
}

/* Feature detection for 3D transforms */
@supports (transform: perspective(1000px)) {
  .flip-card {
    transform: perspective(1000px) rotateY(0deg);
    transition: transform 0.6s;
  }

  .flip-card:hover {
    transform: perspective(1000px) rotateY(180deg);
  }
}
```

### Vendor Prefixes

```css
/**
 * Vendor Prefix Guide
 * Note: Most modern build tools (PostCSS/Autoprefixer) handle this
 * Listed for reference and manual fallbacks
 */

/* Animation (rarely needed now) */
.with-prefix {
  -webkit-animation: slideIn 0.3s ease;
  animation: slideIn 0.3s ease;
}

@-webkit-keyframes slideIn {
  from { -webkit-transform: translateX(-100%); }
  to { -webkit-transform: translateX(0); }
}

@keyframes slideIn {
  from { transform: translateX(-100%); }
  to { transform: translateX(0); }
}

/* Transform (rarely needed now) */
.transform-prefix {
  -webkit-transform: translate3d(0, 0, 0);
  transform: translate3d(0, 0, 0);
}

/* Backdrop filter (still recommended) */
.backdrop-prefix {
  -webkit-backdrop-filter: blur(10px);
  backdrop-filter: blur(10px);
}

/* Filter (rarely needed now) */
.filter-prefix {
  -webkit-filter: blur(5px);
  filter: blur(5px);
}
```

### Mobile Browser Considerations

```css
/**
 * Mobile-Specific Optimization
 * Description: Handle iOS/Android quirks
 */

/* iOS Safari - prevent tap highlight */
.tap-target {
  -webkit-tap-highlight-color: transparent;
  tap-highlight-color: transparent;
}

/* iOS Safari - force GPU acceleration */
.ios-smooth {
  -webkit-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-perspective: 1000;
  perspective: 1000;
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}

/* Prevent animation during orientation change */
.no-orientation-animation {
  transition: none;
}

@media (orientation: landscape) {
  .no-orientation-animation {
    transition: all 0.3s ease;
  }
}

/* Android - fix flickering */
.android-fix {
  -webkit-transform: translateZ(0);
  transform: translateZ(0);
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
}
```

---

## Troubleshooting Guide

### Common Issues and Solutions

#### Issue 1: Janky/Stuttering Animations

```css
/**
 * Problem: Animation is not smooth, stutters at 30fps or less
 * Solutions:
 */

/* ❌ BAD - Animating layout properties */
@keyframes janky {
  from { width: 100px; }
  to { width: 200px; }
}

/* ✅ GOOD - Use transform instead */
@keyframes smooth {
  from { transform: scaleX(1); }
  to { transform: scaleX(2); }
}

/* Force GPU acceleration */
.smooth-animation {
  transform: translateZ(0);
  will-change: transform;
}

/* Check for too many simultaneous animations */
/* Limit to 10-15 active animations at once */
```

#### Issue 2: Animation Not Starting

```css
/**
 * Problem: Animation defined but not playing
 * Solutions:
 */

/* Check 1: Ensure animation is applied */
.element {
  animation-name: fadeIn;
  animation-duration: 0.3s; /* Must have duration! */
}

/* Check 2: Verify keyframes are defined */
@keyframes fadeIn {
  from { opacity: 0; }
  to { opacity: 1; }
}

/* Check 3: Check for conflicts */
.element {
  /* These can override animation */
  /* display: none; */
  /* opacity: 1 !important; */
}

/* Check 4: Use shorthand correctly */
.element {
  /* name | duration | timing | delay | iteration | direction | fill | play-state */
  animation: fadeIn 0.3s ease 0s 1 normal forwards running;
}
```

#### Issue 3: Animation Flashing/Flickering

```css
/**
 * Problem: Elements flash or flicker during animation
 * Solutions:
 */

/* Add backface-visibility */
.no-flicker {
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden;
  -webkit-perspective: 1000;
  perspective: 1000;
}

/* Force GPU layer */
.no-flicker-2 {
  transform: translateZ(0);
  transform: translate3d(0, 0, 0);
}

/* For 3D transforms */
.no-flicker-3d {
  transform-style: preserve-3d;
  -webkit-transform-style: preserve-3d;
}
```

#### Issue 4: Animation Ends Then Jumps

```css
/**
 * Problem: Animation plays correctly but jumps at the end
 * Solutions:
 */

/* ❌ BAD - No fill mode */
.jumpy {
  animation: slideIn 0.3s ease;
}

/* ✅ GOOD - Use animation-fill-mode */
.no-jump {
  animation: slideIn 0.3s ease forwards;
  /* forwards = maintain final state */
  /* backwards = apply first frame before animation */
  /* both = apply both forwards and backwards */
}

/* Ensure end state matches animation */
@keyframes slideIn {
  from {
    transform: translateX(-100%);
  }
  to {
    transform: translateX(0);
  }
}

.no-jump {
  /* End state should match 'to' frame */
  transform: translateX(0);
  animation: slideIn 0.3s ease;
}
```

#### Issue 5: Hover Animation Reverses Too Quickly

```css
/**
 * Problem: Reverse animation on mouse out is too fast
 * Solutions:
 */

/* ❌ BAD - Same duration for in/out */
.quick-reverse {
  transition: transform 0.3s ease;
}

.quick-reverse:hover {
  transform: scale(1.2);
}

/* ✅ GOOD - Different timing for reverse */
.smooth-reverse {
  transition: transform 0.6s cubic-bezier(0.16, 1, 0.3, 1);
}

.smooth-reverse:hover {
  transition-duration: 0.3s;
  transform: scale(1.2);
}
```

#### Issue 6: Animation Delays Page Load

```css
/**
 * Problem: Animations slow down initial page render
 * Solutions:
 */

/* Defer non-critical animations */
.defer-animation {
  animation: fadeIn 0.3s ease;
  /* Add this via JS after page load */
  animation-play-state: paused;
}

/* Use will-change only when needed */
.optimize-load {
  /* Don't set will-change on load */
}

.optimize-load.ready {
  /* Add when animation is about to start */
  will-change: transform, opacity;
}

.optimize-load.done {
  /* Remove when complete */
  will-change: auto;
}

/* Load animations progressively */
@keyframes lazy-loaded {
  /* Simple animations first */
  0% { opacity: 0; }
  100% { opacity: 1; }
}
```

#### Issue 7: 3D Transform Not Working

```css
/**
 * Problem: 3D rotations appear flat or don't work
 * Solutions:
 */

/* ❌ BAD - Missing perspective */
.flat-3d {
  transform: rotateY(45deg);
}

/* ✅ GOOD - Add perspective to parent */
.parent-perspective {
  perspective: 1000px;
  perspective-origin: center;
}

.parent-perspective .child-3d {
  transform: rotateY(45deg);
  transform-style: preserve-3d;
}

/* Or add perspective to element */
.self-perspective {
  transform: perspective(1000px) rotateY(45deg);
}

/* For card flips, preserve 3D on children */
.flip-container {
  perspective: 1000px;
}

.flip-card {
  transform-style: preserve-3d;
  transition: transform 0.6s;
}

.flip-card-face {
  backface-visibility: hidden;
}
```

#### Issue 8: Animation Performance on Mobile

```css
/**
 * Problem: Animations lag or stutter on mobile devices
 * Solutions:
 */

/* Reduce animation complexity on mobile */
@media (max-width: 768px) {
  .complex-animation {
    /* Simpler animation for mobile */
    animation: fadeIn 0.3s ease;
  }
}

/* Use transform instead of position */
/* ❌ BAD */
@media (max-width: 768px) {
  @keyframes mobile-bad {
    from { left: 0; }
    to { left: 100px; }
  }
}

/* ✅ GOOD */
@media (max-width: 768px) {
  @keyframes mobile-good {
    from { transform: translateX(0); }
    to { transform: translateX(100px); }
  }
}

/* Reduce number of animated elements */
@media (max-width: 768px) {
  .mobile-optimize .item {
    /* Disable stagger on mobile */
    animation-delay: 0s !important;
  }
}
```

### Debug Checklist

```
Animation Not Working? Check:

1. ☐ Is animation-duration set? (defaults to 0)
2. ☐ Are keyframes defined correctly?
3. ☐ Is element visible? (display: none prevents animation)
4. ☐ Check browser DevTools > Animations panel
5. ☐ Is animation-play-state set to running?
6. ☐ Are there conflicting !important styles?
7. ☐ Check z-index stacking issues
8. ☐ Verify browser support (@supports)
9. ☐ Check for typos in animation-name
10. ☐ Is the element in the DOM when animation triggers?

Performance Issues? Check:

1. ☐ Using transform/opacity instead of layout properties?
2. ☐ Too many simultaneous animations?
3. ☐ Is will-change causing memory issues?
4. ☐ Complex box-shadow/filter animations?
5. ☐ Check with DevTools Performance tab
6. ☐ Mobile device testing
7. ☐ Forced reflows in JavaScript?
8. ☐ Large images or backgrounds being animated?
9. ☐ Missing GPU acceleration hints?
10. ☐ Browser extensions interfering?
```

---

## Animation Utilities

### Stagger Animations

```css
/**
 * Stagger Animation Utilities
 * Description: Delay animations for multiple items
 * Use case: Lists, grids, sequential reveals
 */

/* Method 1: nth-child selectors */
.stagger-item:nth-child(1) { animation-delay: 0.1s; }
.stagger-item:nth-child(2) { animation-delay: 0.2s; }
.stagger-item:nth-child(3) { animation-delay: 0.3s; }
.stagger-item:nth-child(4) { animation-delay: 0.4s; }
.stagger-item:nth-child(5) { animation-delay: 0.5s; }

/* Method 2: CSS custom properties (more flexible) */
.stagger-container {
  --stagger-delay: 0.1s;
}

.stagger-item {
  animation: fadeInUp 0.5s ease both;
  animation-delay: calc(var(--item-index, 0) * var(--stagger-delay));
}

/* Set via inline style: style="--item-index: 1" */

/* Method 3: Generate with SCSS/SASS */
/* @for $i from 1 through 20 {
  .stagger-item:nth-child(#{$i}) {
    animation-delay: #{$i * 0.1}s;
  }
} */
```

### Animation Presets

```css
/**
 * Quick Animation Preset Classes
 * Description: Drop-in animation utilities
 * Use case: Rapid prototyping, common animations
 */

/* Duration presets */
.duration-fast { animation-duration: 0.15s; }
.duration-normal { animation-duration: 0.3s; }
.duration-slow { animation-duration: 0.5s; }
.duration-slower { animation-duration: 0.8s; }

/* Delay presets */
.delay-0 { animation-delay: 0s; }
.delay-1 { animation-delay: 0.1s; }
.delay-2 { animation-delay: 0.2s; }
.delay-3 { animation-delay: 0.3s; }
.delay-5 { animation-delay: 0.5s; }

/* Iteration presets */
.once { animation-iteration-count: 1; }
.twice { animation-iteration-count: 2; }
.infinite { animation-iteration-count: infinite; }

/* Fill mode presets */
.fill-none { animation-fill-mode: none; }
.fill-forwards { animation-fill-mode: forwards; }
.fill-backwards { animation-fill-mode: backwards; }
.fill-both { animation-fill-mode: both; }

/* Play state */
.paused { animation-play-state: paused; }
.playing { animation-play-state: running; }
```

---

## Usage Examples

### Complete Modal Implementation

```html
<!-- HTML -->
<div class="modal-backdrop" id="modal">
  <div class="modal-content">
    <h2>Modal Title</h2>
    <p>Modal content goes here</p>
    <button onclick="closeModal()">Close</button>
  </div>
</div>
```

```css
/* CSS */
.modal-backdrop {
  position: fixed;
  inset: 0;
  background: rgba(0, 0, 0, 0.5);
  display: flex;
  align-items: center;
  justify-content: center;
  animation: modalBackdropFadeIn 0.2s ease-out;
}

.modal-backdrop.closing {
  animation: modalBackdropFadeOut 0.2s ease-in;
}

.modal-content {
  background: white;
  padding: 2rem;
  border-radius: 8px;
  max-width: 500px;
  width: 90%;
  animation: modalContentScaleIn 0.3s cubic-bezier(0.16, 1, 0.3, 1);
}

.modal-backdrop.closing .modal-content {
  animation: modalContentScaleOut 0.2s ease-in;
}
```

```javascript
/* JavaScript */
function closeModal() {
  const modal = document.getElementById('modal');
  modal.classList.add('closing');

  // Wait for animation to complete
  setTimeout(() => {
    modal.remove(); // or modal.style.display = 'none';
  }, 200);
}
```

---

## Quick Reference

### Most Common Animations

```css
/* Top 10 Most Used Animations */

/* 1. Fade In */
.fade-in { animation: fadeIn 0.3s ease; }

/* 2. Fade Out */
.fade-out { animation: fadeOut 0.3s ease forwards; }

/* 3. Slide In */
.slide-in { animation: slideInUp 0.4s ease; }

/* 4. Scale In */
.scale-in { animation: scaleIn 0.3s ease; }

/* 5. Bounce */
.bounce { animation: bounce 2s infinite; }

/* 6. Pulse */
.pulse { animation: pulse 2s infinite; }

/* 7. Shake */
.shake { animation: shake 0.6s ease; }

/* 8. Rotate */
.rotate { animation: rotate360 1s linear infinite; }

/* 9. Glow */
.glow { animation: pulseGlow 2s infinite; }

/* 10. Wobble */
.wobble { animation: wobble 0.8s ease; }
```

### Speed Reference

```
Animation Timing Quick Guide:

Ultra Fast:    100ms  - Instant feedback
Fast:          200ms  - Quick transitions
Normal:        300ms  - Standard UI (recommended default)
Medium:        500ms  - Emphasized transitions
Slow:          800ms  - Dramatic effects
Very Slow:     1000ms+ - Decorative/background
```

### Property Performance

```
Performance Impact (Best to Worst):

⚡ Fastest (GPU-accelerated):
- transform (translate, scale, rotate)
- opacity

⚡ Fast (GPU-accelerated with caution):
- filter (blur, brightness, etc.)
- backdrop-filter

⚠️ Moderate (may cause repaint):
- color
- background-color
- box-shadow (use opacity on pseudo-element instead)

❌ Slow (causes layout recalculation):
- width, height
- top, left, right, bottom (on non-positioned elements)
- margin, padding
- border
- font-size
```

---

## Resources

### External Tools

- **Cubic Bezier Generator**: https://cubic-bezier.com
- **Animista**: https://animista.net (animation library)
- **Keyframes.app**: https://keyframes.app (animation builder)
- **CSS Animation Performance**: https://web.dev/animations

### Testing Tools

- Chrome DevTools > Animations Panel
- Chrome DevTools > Performance Panel
- Firefox DevTools > Performance
- Lighthouse Performance Audit

### Browser Support

- Can I Use: https://caniuse.com
- MDN Web Docs: https://developer.mozilla.org

---

## Conclusion

This animation library provides 50+ ready-to-use CSS animations covering:
- ✅ Fade, slide, scale, rotate, bounce, flip animations
- ✅ Shake, wobble, blur, glow, swing effects
- ✅ Complete UI animation recipes (modals, toasts, dropdowns, etc.)
- ✅ Scroll-driven animation patterns
- ✅ Performance optimization techniques
- ✅ Accessibility best practices
- ✅ Browser compatibility guidance
- ✅ Comprehensive troubleshooting guide

All animations are GPU-accelerated where possible and include accessibility considerations. Use this library as a reference for implementing smooth, performant, and accessible animations in your projects.

**Remember**: Always test animations on target devices, respect user preferences (prefers-reduced-motion), and prioritize performance for the best user experience.
