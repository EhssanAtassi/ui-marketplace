---
name: sass-patterns-library
description: Comprehensive SASS/SCSS patterns library with mixins, functions, and modern module system. Use when searching for SASS utilities, @use/@forward patterns, or advanced preprocessing techniques.
---

# SASS Patterns Library

A comprehensive searchable reference for modern SASS/SCSS with @use/@forward module system, advanced mixins, functions, and best practices.

## Table of Contents

1. [Modern Module System (@use/@forward)](#modern-module-system)
2. [Mixins Library](#mixins-library)
3. [Functions Library](#functions-library)
4. [Color Manipulation](#color-manipulation)
5. [Typography Patterns](#typography-patterns)
6. [Layout Utilities](#layout-utilities)
7. [Responsive Patterns](#responsive-patterns)
8. [Animation Helpers](#animation-helpers)
9. [Component Generators](#component-generators)
10. [Performance Patterns](#performance-patterns)
11. [Best Practices](#best-practices)
12. [Migration from @import](#migration-from-import)

---

## Modern Module System (@use/@forward)

### Module Structure Pattern

```scss
// styles/
// ├── _config.scss          (Barrel file)
// ├── config/
// │   ├── _colors.scss
// │   ├── _typography.scss
// │   └── _spacing.scss
// ├── tools/
// │   ├── _mixins.scss
// │   └── _functions.scss
// └── main.scss             (Entry point)
```

### Pattern 1: Basic @use

```scss
// _colors.scss
$primary: #3b82f6;
$secondary: #8b5cf6;

// main.scss
@use 'colors'; // Namespace: colors

.button {
  background: colors.$primary;
  border-color: colors.$secondary;
}
```

### Pattern 2: @use with Alias

```scss
@use 'colors' as c;
@use 'typography' as t;

.heading {
  color: c.$primary;
  font-family: t.$font-family-heading;
}
```

### Pattern 3: @use with Wildcard (*)

```scss
// Use sparingly - imports without namespace
@use 'colors' as *;

.button {
  background: $primary; // No namespace needed
}
```

### Pattern 4: @forward for Barrel Files

```scss
// _config.scss - Barrel file
@forward 'config/colors';
@forward 'config/typography';
@forward 'config/spacing';

// main.scss
@use 'config' as *; // All config modules available
```

### Pattern 5: @forward with Prefix

```scss
// _theme.scss
@forward 'colors' as color-*;
@forward 'spacing' as space-*;

// main.scss
@use 'theme';

.element {
  background: theme.$color-primary;
  padding: theme.$space-medium;
}
```

### Pattern 6: @forward with show/hide

```scss
// _public-api.scss
@forward 'internal' hide $private-var, private-mixin;
@forward 'config' show $primary, $secondary;

// Or show only specific members
@forward 'utilities' show rem, em, px-to-rem;
```

### Pattern 7: Private Variables

```scss
// _colors.scss
@use 'sass:color';
@use 'sass:map';

// Private - not exported
$_base-colors: (
  'primary': #3b82f6,
  'secondary': #8b5cf6
);

// Public function
@function get($name) {
  @return map.get($_base-colors, $name);
}

// Public variable
$primary: get('primary');
```

---

## Mixins Library

### Category 1: Responsive Mixins

#### Pattern 1: Breakpoint Mixin

```scss
@use 'sass:map';

$breakpoints: (
  'xs': 0,
  'sm': 576px,
  'md': 768px,
  'lg': 992px,
  'xl': 1200px,
  'xxl': 1400px
);

@mixin breakpoint($size, $type: 'min') {
  @if map.has-key($breakpoints, $size) {
    $breakpoint: map.get($breakpoints, $size);

    @if $type == 'min' {
      @media (min-width: $breakpoint) { @content; }
    } @else if $type == 'max' {
      @media (max-width: $breakpoint - 1px) { @content; }
    } @else if $type == 'only' {
      $keys: map.keys($breakpoints);
      $index: list.index($keys, $size);

      @if $index < length($keys) {
        $next: list.nth($keys, $index + 1);
        $next-bp: map.get($breakpoints, $next);
        @media (min-width: $breakpoint) and (max-width: $next-bp - 1px) {
          @content;
        }
      }
    }
  }
}

// Usage
.element {
  width: 100%;

  @include breakpoint('md') {
    width: 50%;
  }

  @include breakpoint('lg') {
    width: 33.333%;
  }
}
```

#### Pattern 2: Container Query Mixin

```scss
@mixin container($size) {
  @container (min-width: $size) {
    @content;
  }
}

// Usage
.card-wrapper {
  container-type: inline-size;
}

.card {
  @include container(400px) {
    display: grid;
    grid-template-columns: 200px 1fr;
  }
}
```

### Category 2: Layout Mixins

#### Pattern 1: Flexbox Center

```scss
@mixin flex-center($direction: row) {
  display: flex;
  align-items: center;
  justify-content: center;
  flex-direction: $direction;
}

// Usage
.centered {
  @include flex-center;
}

.centered-column {
  @include flex-center(column);
}
```

#### Pattern 2: Grid System Generator

```scss
@mixin grid-system($columns: 12, $gap: 1rem) {
  display: grid;
  gap: $gap;

  @for $i from 1 through $columns {
    &.cols-#{$i} {
      grid-template-columns: repeat($i, 1fr);
    }

    .col-span-#{$i} {
      grid-column: span $i;
    }
  }
}

// Usage
.grid {
  @include grid-system(12, 1.5rem);
}
```

#### Pattern 3: Aspect Ratio

```scss
@mixin aspect-ratio($width, $height) {
  position: relative;

  &::before {
    content: '';
    display: block;
    padding-top: calc($height / $width * 100%);
  }

  > * {
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
  }
}

// Modern version
@mixin aspect-ratio-modern($ratio) {
  aspect-ratio: $ratio;
}

// Usage
.video {
  @include aspect-ratio(16, 9);
}

.square {
  @include aspect-ratio-modern(1);
}
```

### Category 3: Typography Mixins

#### Pattern 1: Fluid Typography

```scss
@use 'sass:math';

@mixin fluid-type($min-vw, $max-vw, $min-size, $max-size) {
  font-size: $min-size;

  @media (min-width: $min-vw) {
    font-size: calc(
      #{$min-size} +
      #{math.div($max-size - $min-size, 1)} *
      ((100vw - #{$min-vw}) / #{math.div($max-vw - $min-vw, 1)})
    );
  }

  @media (min-width: $max-vw) {
    font-size: $max-size;
  }
}

// Usage
h1 {
  @include fluid-type(320px, 1200px, 1.5rem, 3rem);
}
```

#### Pattern 2: Text Truncation

```scss
@mixin truncate($lines: 1) {
  @if $lines == 1 {
    overflow: hidden;
    text-overflow: ellipsis;
    white-space: nowrap;
  } @else {
    display: -webkit-box;
    -webkit-line-clamp: $lines;
    -webkit-box-orient: vertical;
    overflow: hidden;
  }
}

// Usage
.single-line {
  @include truncate;
}

.three-lines {
  @include truncate(3);
}
```

### Category 4: Visual Effects

#### Pattern 1: Box Shadow Generator

```scss
@mixin box-shadow($level) {
  @if $level == 1 {
    box-shadow: 0 1px 3px rgba(0, 0, 0, 0.12), 0 1px 2px rgba(0, 0, 0, 0.24);
  } @else if $level == 2 {
    box-shadow: 0 3px 6px rgba(0, 0, 0, 0.16), 0 3px 6px rgba(0, 0, 0, 0.23);
  } @else if $level == 3 {
    box-shadow: 0 10px 20px rgba(0, 0, 0, 0.19), 0 6px 6px rgba(0, 0, 0, 0.23);
  } @else if $level == 4 {
    box-shadow: 0 14px 28px rgba(0, 0, 0, 0.25), 0 10px 10px rgba(0, 0, 0, 0.22);
  } @else if $level == 5 {
    box-shadow: 0 19px 38px rgba(0, 0, 0, 0.30), 0 15px 12px rgba(0, 0, 0, 0.22);
  }
}

// Usage
.card {
  @include box-shadow(2);

  &:hover {
    @include box-shadow(4);
  }
}
```

#### Pattern 2: Glassmorphism

```scss
@mixin glass($blur: 10px, $opacity: 0.1) {
  background: rgba(255, 255, 255, $opacity);
  backdrop-filter: blur($blur);
  -webkit-backdrop-filter: blur($blur);
  border: 1px solid rgba(255, 255, 255, 0.2);
}

// Usage
.glass-card {
  @include glass(15px, 0.15);
}
```

---

## Functions Library

### Category 1: Unit Conversion

#### Pattern 1: px to rem

```scss
@use 'sass:math';

$base-font-size: 16px !default;

@function rem($px) {
  @return math.div($px, $base-font-size) * 1rem;
}

// Usage
.element {
  font-size: rem(18px); // 1.125rem
  padding: rem(24px);   // 1.5rem
}
```

#### Pattern 2: px to em

```scss
@function em($px, $context: $base-font-size) {
  @return math.div($px, $context) * 1em;
}

// Usage
.element {
  padding: em(16px); // 1em
  margin: em(20px, 18px); // 1.111em
}
```

### Category 2: Color Functions

#### Pattern 1: Tint and Shade

```scss
@use 'sass:color';

@function tint($color, $percentage) {
  @return color.mix(white, $color, $percentage);
}

@function shade($color, $percentage) {
  @return color.mix(black, $color, $percentage);
}

// Usage
$primary: #3b82f6;

.light {
  background: tint($primary, 20%); // Lighter
}

.dark {
  background: shade($primary, 20%); // Darker
}
```

#### Pattern 2: Color Scale Generator

```scss
@use 'sass:color';
@use 'sass:map';

@function generate-scale($color, $name: 'color') {
  $scale: ();

  // Lighter shades
  $scale: map.merge($scale, (
    '#{$name}-50': tint($color, 95%),
    '#{$name}-100': tint($color, 80%),
    '#{$name}-200': tint($color, 60%),
    '#{$name}-300': tint($color, 40%),
    '#{$name}-400': tint($color, 20%),
  ));

  // Base
  $scale: map.merge($scale, (
    '#{$name}-500': $color,
  ));

  // Darker shades
  $scale: map.merge($scale, (
    '#{$name}-600': shade($color, 20%),
    '#{$name}-700': shade($color, 40%),
    '#{$name}-800': shade($color, 60%),
    '#{$name}-900': shade($color, 80%),
  ));

  @return $scale;
}

// Usage
$blue-scale: generate-scale(#3b82f6, 'blue');
```

### Category 3: Math Functions

#### Pattern 1: Modular Scale

```scss
@use 'sass:math';

$modular-scale-ratio: 1.25 !default;
$modular-scale-base: 1rem !default;

@function modular-scale($step) {
  @return $modular-scale-base * math.pow($modular-scale-ratio, $step);
}

// Usage
h1 { font-size: modular-scale(4);  } // 2.441rem
h2 { font-size: modular-scale(3);  } // 1.953rem
h3 { font-size: modular-scale(2);  } // 1.563rem
h4 { font-size: modular-scale(1);  } // 1.25rem
p  { font-size: modular-scale(0);  } // 1rem
```

#### Pattern 2: Strip Unit

```scss
@use 'sass:math';

@function strip-unit($value) {
  @return math.div($value, $value * 0 + 1);
}

// Usage
$value: strip-unit(16px); // 16
```

---

## Color Manipulation

### Pattern 1: Dynamic Theme Colors

```scss
@use 'sass:color';
@use 'sass:map';

@function theme-color($base-color, $variant: 'base') {
  $variants: (
    'lightest': color.scale($base-color, $lightness: 80%),
    'lighter': color.scale($base-color, $lightness: 40%),
    'light': color.scale($base-color, $lightness: 20%),
    'base': $base-color,
    'dark': color.scale($base-color, $lightness: -20%),
    'darker': color.scale($base-color, $lightness: -40%),
    'darkest': color.scale($base-color, $lightness: -60%)
  );

  @return map.get($variants, $variant);
}

// Usage
$primary: #3b82f6;

.button {
  background: theme-color($primary);

  &:hover {
    background: theme-color($primary, 'dark');
  }

  &:active {
    background: theme-color($primary, 'darker');
  }
}
```

### Pattern 2: Accessible Color Contrast

```scss
@use 'sass:color';

@function contrast-color($color, $light: white, $dark: black) {
  $lightness: color.lightness($color);

  @if $lightness > 50% {
    @return $dark;
  } @else {
    @return $light;
  }
}

// Usage
.badge {
  $bg: #3b82f6;
  background: $bg;
  color: contrast-color($bg); // Auto white or black
}
```

---

## Typography Patterns

### Pattern 1: Type Scale System

```scss
@use 'sass:map';

$type-scale: (
  'xs': 0.75rem,
  'sm': 0.875rem,
  'base': 1rem,
  'lg': 1.125rem,
  'xl': 1.25rem,
  '2xl': 1.5rem,
  '3xl': 1.875rem,
  '4xl': 2.25rem,
  '5xl': 3rem,
  '6xl': 3.75rem
);

@function font-size($size) {
  @return map.get($type-scale, $size);
}

// Generate utility classes
@each $name, $size in $type-scale {
  .text-#{$name} {
    font-size: $size;
  }
}
```

### Pattern 2: Font Family Stack

```scss
$font-family-sans: (
  'Inter',
  'system-ui',
  '-apple-system',
  'BlinkMacSystemFont',
  'Segoe UI',
  'Roboto',
  'Helvetica Neue',
  'Arial',
  'sans-serif'
);

$font-family-serif: (
  'Georgia',
  'Cambria',
  'Times New Roman',
  'Times',
  'serif'
);

$font-family-mono: (
  'JetBrains Mono',
  'Menlo',
  'Monaco',
  'Consolas',
  'Courier New',
  'monospace'
);

// Convert list to string
@function font-stack($stack) {
  $result: '';
  @each $font in $stack {
    @if $result != '' {
      $result: $result + ', ';
    }
    @if str-index($font, ' ') {
      $result: $result + '"' + $font + '"';
    } @else {
      $result: $result + $font;
    }
  }
  @return unquote($result);
}

// Usage
body {
  font-family: $font-family-sans;
}
```

---

## Layout Utilities

### Pattern 1: Spacing System Generator

```scss
@use 'sass:map';

$spacing-base: 8px;
$spacing-scale: (
  '0': 0,
  '1': $spacing-base * 0.5,    // 4px
  '2': $spacing-base,            // 8px
  '3': $spacing-base * 1.5,      // 12px
  '4': $spacing-base * 2,        // 16px
  '5': $spacing-base * 2.5,      // 20px
  '6': $spacing-base * 3,        // 24px
  '8': $spacing-base * 4,        // 32px
  '10': $spacing-base * 5,       // 40px
  '12': $spacing-base * 6,       // 48px
  '16': $spacing-base * 8,       // 64px
  '20': $spacing-base * 10,      // 80px
  '24': $spacing-base * 12       // 96px
);

@each $name, $value in $spacing-scale {
  // Margin utilities
  .m-#{$name} { margin: $value; }
  .mt-#{$name} { margin-top: $value; }
  .mr-#{$name} { margin-right: $value; }
  .mb-#{$name} { margin-bottom: $value; }
  .ml-#{$name} { margin-left: $value; }
  .mx-#{$name} { margin-left: $value; margin-right: $value; }
  .my-#{$name} { margin-top: $value; margin-bottom: $value; }

  // Padding utilities
  .p-#{$name} { padding: $value; }
  .pt-#{$name} { padding-top: $value; }
  .pr-#{$name} { padding-right: $value; }
  .pb-#{$name} { padding-bottom: $value; }
  .pl-#{$name} { padding-left: $value; }
  .px-#{$name} { padding-left: $value; padding-right: $value; }
  .py-#{$name} { padding-top: $value; padding-bottom: $value; }
}
```

### Pattern 2: Z-Index Management

```scss
$z-index: (
  'modal': 1000,
  'overlay': 900,
  'dropdown': 800,
  'header': 700,
  'sidebar': 600,
  'default': 1,
  'below': -1
);

@function z($layer) {
  @return map.get($z-index, $layer);
}

// Usage
.modal {
  z-index: z('modal');
}

.header {
  z-index: z('header');
}
```

---

## Responsive Patterns

### Pattern 1: Container Width System

```scss
$containers: (
  'sm': 640px,
  'md': 768px,
  'lg': 1024px,
  'xl': 1280px,
  '2xl': 1536px
);

@each $name, $width in $containers {
  .container-#{$name} {
    max-width: $width;
    margin-left: auto;
    margin-right: auto;
    padding-left: 1rem;
    padding-right: 1rem;
  }
}
```

### Pattern 2: Responsive Utilities Generator

```scss
@mixin generate-responsive-utilities($property, $prefix, $values) {
  // Base utilities
  @each $key, $value in $values {
    .#{$prefix}-#{$key} {
      #{$property}: $value;
    }
  }

  // Responsive variants
  @each $breakpoint-name, $breakpoint-value in $breakpoints {
    @if $breakpoint-name != 'xs' {
      @include breakpoint($breakpoint-name) {
        @each $key, $value in $values {
          .#{$breakpoint-name}\:#{$prefix}-#{$key} {
            #{$property}: $value;
          }
        }
      }
    }
  }
}

// Usage
@include generate-responsive-utilities(
  'display',
  'd',
  (
    'none': none,
    'block': block,
    'flex': flex,
    'grid': grid,
    'inline': inline,
    'inline-block': inline-block
  )
);
```

---

## Animation Helpers

### Pattern 1: Transition Mixin

```scss
@mixin transition($properties...) {
  $transitions: ();

  @each $property in $properties {
    $transitions: append($transitions, $property 0.3s ease, comma);
  }

  transition: $transitions;

  @media (prefers-reduced-motion: reduce) {
    transition: none;
  }
}

// Usage
.button {
  @include transition(background-color, transform, box-shadow);
}
```

### Pattern 2: Animation Generator

```scss
@mixin keyframes($name) {
  @keyframes #{$name} {
    @content;
  }
}

@mixin animation($name, $duration: 1s, $timing: ease, $delay: 0s, $iteration: 1, $direction: normal, $fill-mode: both) {
  animation: $name $duration $timing $delay $iteration $direction $fill-mode;

  @media (prefers-reduced-motion: reduce) {
    animation: none;
  }
}

// Usage
@include keyframes(fadeIn) {
  from { opacity: 0; }
  to { opacity: 1; }
}

.element {
  @include animation(fadeIn, 0.5s);
}
```

---

## Component Generators

### Pattern 1: Button Generator

```scss
@mixin button-variant($bg-color, $text-color: white) {
  background-color: $bg-color;
  color: $text-color;
  border: 2px solid $bg-color;

  &:hover {
    background-color: shade($bg-color, 10%);
    border-color: shade($bg-color, 10%);
  }

  &:active {
    background-color: shade($bg-color, 20%);
    border-color: shade($bg-color, 20%);
  }

  &:disabled {
    background-color: tint($bg-color, 50%);
    border-color: tint($bg-color, 50%);
    cursor: not-allowed;
  }
}

// Generate button variants
$button-colors: (
  'primary': #3b82f6,
  'secondary': #8b5cf6,
  'success': #10b981,
  'danger': #ef4444,
  'warning': #f59e0b
);

@each $name, $color in $button-colors {
  .btn-#{$name} {
    @include button-variant($color);
  }
}
```

### Pattern 2: Card Generator

```scss
@mixin card($padding: 1.5rem, $radius: 0.5rem, $shadow-level: 2) {
  padding: $padding;
  border-radius: $radius;
  background: white;
  @include box-shadow($shadow-level);

  &__header {
    margin-bottom: 1rem;
    padding-bottom: 1rem;
    border-bottom: 1px solid #e5e7eb;
  }

  &__title {
    font-size: 1.25rem;
    font-weight: 600;
    margin: 0;
  }

  &__body {
    margin-bottom: 1rem;
  }

  &__footer {
    margin-top: 1rem;
    padding-top: 1rem;
    border-top: 1px solid #e5e7eb;
  }
}

// Usage
.card {
  @include card;
}

.card-compact {
  @include card(1rem, 0.25rem, 1);
}
```

---

## Performance Patterns

### Pattern 1: Placeholder Selectors

```scss
// Reusable styles
%clearfix {
  &::after {
    content: '';
    display: table;
    clear: both;
  }
}

%ellipsis {
  overflow: hidden;
  text-overflow: ellipsis;
  white-space: nowrap;
}

%visually-hidden {
  position: absolute;
  width: 1px;
  height: 1px;
  padding: 0;
  margin: -1px;
  overflow: hidden;
  clip: rect(0, 0, 0, 0);
  white-space: nowrap;
  border: 0;
}

// Usage
.container {
  @extend %clearfix;
}

.truncated-text {
  @extend %ellipsis;
}

.sr-only {
  @extend %visually-hidden;
}
```

### Pattern 2: Conditional Compilation

```scss
$env: 'production' !default;

@mixin debug-only {
  @if $env == 'development' {
    @content;
  }
}

// Usage
.element {
  @include debug-only {
    outline: 2px solid red;
    background: rgba(255, 0, 0, 0.1);
  }
}
```

---

## Best Practices

### DO's ✅

1. **Use @use instead of @import**
```scss
// ✅ Good
@use 'colors';
@use 'typography' as t;

// ❌ Bad
@import 'colors';
@import 'typography';
```

2. **Keep variables private with $_**
```scss
// ✅ Good
$_private-var: value;
$public-var: value;

// Expose through function
@function get-private() {
  @return $_private-var;
}
```

3. **Use placeholder selectors for repeated patterns**
```scss
// ✅ Good
%button-base {
  padding: 0.5rem 1rem;
  border-radius: 0.25rem;
}

.button-primary {
  @extend %button-base;
  background: blue;
}
```

4. **Namespace your modules**
```scss
// ✅ Good
@use 'colors' as c;
.element { color: c.$primary; }

// ❌ Avoid wildcard unless necessary
@use 'colors' as *;
```

### DON'Ts ❌

1. **Don't nest deeper than 3 levels**
```scss
// ❌ Bad - too deep
.nav {
  .list {
    .item {
      .link {
        .icon { }
      }
    }
  }
}

// ✅ Good - flat BEM
.nav { }
.nav__list { }
.nav__item { }
.nav__link { }
.nav__icon { }
```

2. **Don't use color keywords**
```scss
// ❌ Bad
$primary: blue;

// ✅ Good
$primary: #3b82f6;
```

3. **Don't over-engineer with @extend**
```scss
// ❌ Can cause bloat
.button {
  @extend .base;
  @extend .rounded;
  @extend .shadowed;
}

// ✅ Better - use mixins
.button {
  @include base-styles;
  @include rounded;
  @include shadowed;
}
```

---

## Migration from @import

### Step 1: Replace @import with @use

```scss
// Before
@import 'colors';
@import 'typography';

$primary: red; // Global

// After
@use 'colors';
@use 'typography' as t;

// Namespaced
.element {
  color: colors.$primary;
  font: t.$body-font;
}
```

### Step 2: Update Variable Access

```scss
// Before
@import 'config';
.button { color: $primary; }

// After
@use 'config';
.button { color: config.$primary; }

// Or with wildcard
@use 'config' as *;
.button { color: $primary; }
```

### Step 3: Refactor Global Scope

```scss
// Before - Everything global
// _config.scss
$primary: blue;
$secondary: green;

// After - Explicit exports
// _config.scss
@use 'sass:map';

$_colors: (
  'primary': blue,
  'secondary': green
);

@function color($name) {
  @return map.get($_colors, $name);
}

// Export specific colors
$primary: color('primary');
$secondary: color('secondary');
```

---

## Quick Reference

### Essential Mixins
- `breakpoint($size)` - Responsive breakpoints
- `flex-center()` - Flexbox centering
- `truncate($lines)` - Text ellipsis
- `transition($props...)` - Smooth transitions

### Essential Functions
- `rem($px)` - px to rem conversion
- `tint($color, $%)` - Lighten color
- `shade($color, $%)` - Darken color
- `modular-scale($step)` - Typography scale

### Essential Patterns
- Module system with @use/@forward
- Private variables with $_
- Placeholder selectors with %
- Responsive utility generators

---

This library provides production-ready SASS patterns. Use @use for modern module system, keep nesting under 3 levels, and leverage placeholders for reusable styles.
