---
name: tailwind-utilities-reference
description: Complete Tailwind CSS utilities reference. Use when searching for utility classes, responsive variants, or Tailwind configuration patterns.
---

# Tailwind CSS Utilities Reference

A comprehensive reference guide for Tailwind CSS utility classes, patterns, and configurations. This skill provides quick access to all Tailwind utilities, responsive design patterns, custom configurations, and best practices.

## Table of Contents

1. [Layout Utilities](#layout-utilities)
2. [Flexbox & Grid](#flexbox--grid)
3. [Spacing (Padding & Margin)](#spacing-padding--margin)
4. [Sizing](#sizing)
5. [Typography](#typography)
6. [Backgrounds](#backgrounds)
7. [Borders](#borders)
8. [Effects & Filters](#effects--filters)
9. [Transitions & Animations](#transitions--animations)
10. [Transforms](#transforms)
11. [Interactivity](#interactivity)
12. [Responsive Design Patterns](#responsive-design-patterns)
13. [Custom Configuration](#custom-configuration)
14. [Plugin Development](#plugin-development)
15. [Component Recipes](#component-recipes)
16. [JIT Mode Patterns](#jit-mode-patterns)
17. [Performance Optimization](#performance-optimization)
18. [Searchable Class Index](#searchable-class-index)

---

## Layout Utilities

### Container
```html
<!-- Container with responsive max-width -->
<div class="container mx-auto">
  <!-- Centers and constrains content -->
</div>

<!-- Full width container -->
<div class="container-fluid">
  <!-- Spans full viewport width -->
</div>
```

### Display
```html
<!-- Display types -->
<div class="block">Block</div>
<div class="inline-block">Inline Block</div>
<div class="inline">Inline</div>
<div class="flex">Flex</div>
<div class="inline-flex">Inline Flex</div>
<div class="grid">Grid</div>
<div class="inline-grid">Inline Grid</div>
<div class="table">Table</div>
<div class="hidden">Hidden</div>

<!-- Responsive display -->
<div class="hidden md:block lg:flex">
  Responsive display changes
</div>
```

### Position
```html
<!-- Static (default) -->
<div class="static">Static</div>

<!-- Relative -->
<div class="relative">Relative</div>

<!-- Absolute -->
<div class="absolute top-0 right-0">Absolute</div>

<!-- Fixed -->
<div class="fixed bottom-4 right-4">Fixed</div>

<!-- Sticky -->
<div class="sticky top-0">Sticky Header</div>

<!-- Position values -->
<div class="absolute inset-0">All sides 0</div>
<div class="absolute inset-x-0">Left and right 0</div>
<div class="absolute inset-y-0">Top and bottom 0</div>
<div class="absolute top-4 left-4">Specific positioning</div>
<div class="absolute -top-2 -left-2">Negative positioning</div>
```

### Overflow
```html
<!-- Overflow control -->
<div class="overflow-auto">Auto scrollbars</div>
<div class="overflow-hidden">Hidden overflow</div>
<div class="overflow-visible">Visible overflow</div>
<div class="overflow-scroll">Always scrollbars</div>

<!-- Directional overflow -->
<div class="overflow-x-auto overflow-y-hidden">
  Horizontal scroll only
</div>

<!-- Text overflow -->
<div class="truncate">Truncated text with ellipsis</div>
<div class="text-ellipsis overflow-hidden">Ellipsis</div>
<div class="text-clip overflow-hidden">Clipped</div>
```

### Z-Index
```html
<!-- Z-index layering -->
<div class="z-0">Base layer</div>
<div class="z-10">Layer 10</div>
<div class="z-20">Layer 20</div>
<div class="z-30">Layer 30</div>
<div class="z-40">Layer 40</div>
<div class="z-50">Layer 50</div>
<div class="z-auto">Auto</div>
<div class="-z-10">Negative layer</div>

<!-- Custom z-index with JIT -->
<div class="z-[100]">Custom z-index 100</div>
<div class="z-[999]">Custom z-index 999</div>
```

### Object Fit & Position
```html
<!-- Object fit for images/video -->
<img class="object-contain" src="..." alt="...">
<img class="object-cover" src="..." alt="...">
<img class="object-fill" src="..." alt="...">
<img class="object-none" src="..." alt="...">
<img class="object-scale-down" src="..." alt="...">

<!-- Object position -->
<img class="object-center" src="..." alt="...">
<img class="object-top" src="..." alt="...">
<img class="object-bottom" src="..." alt="...">
<img class="object-left" src="..." alt="...">
<img class="object-right" src="..." alt="...">
<img class="object-left-top" src="..." alt="...">
```

---

## Flexbox & Grid

### Flexbox Container
```html
<!-- Basic flex container -->
<div class="flex">
  <div>Item 1</div>
  <div>Item 2</div>
</div>

<!-- Flex direction -->
<div class="flex flex-row">Row (default)</div>
<div class="flex flex-row-reverse">Row reverse</div>
<div class="flex flex-col">Column</div>
<div class="flex flex-col-reverse">Column reverse</div>

<!-- Flex wrap -->
<div class="flex flex-wrap">Wrap</div>
<div class="flex flex-wrap-reverse">Wrap reverse</div>
<div class="flex flex-nowrap">No wrap</div>

<!-- Justify content (main axis) -->
<div class="flex justify-start">Start</div>
<div class="flex justify-end">End</div>
<div class="flex justify-center">Center</div>
<div class="flex justify-between">Space between</div>
<div class="flex justify-around">Space around</div>
<div class="flex justify-evenly">Space evenly</div>

<!-- Align items (cross axis) -->
<div class="flex items-start">Start</div>
<div class="flex items-end">End</div>
<div class="flex items-center">Center</div>
<div class="flex items-baseline">Baseline</div>
<div class="flex items-stretch">Stretch</div>

<!-- Align content (multi-line) -->
<div class="flex flex-wrap content-start">Start</div>
<div class="flex flex-wrap content-end">End</div>
<div class="flex flex-wrap content-center">Center</div>
<div class="flex flex-wrap content-between">Between</div>
<div class="flex flex-wrap content-around">Around</div>
<div class="flex flex-wrap content-evenly">Evenly</div>
```

### Flexbox Items
```html
<!-- Flex grow/shrink/basis -->
<div class="flex-1">Grow and shrink</div>
<div class="flex-auto">Auto</div>
<div class="flex-initial">Initial</div>
<div class="flex-none">No grow/shrink</div>

<!-- Flex grow -->
<div class="flex-grow">Grow</div>
<div class="flex-grow-0">No grow</div>

<!-- Flex shrink -->
<div class="flex-shrink">Shrink</div>
<div class="flex-shrink-0">No shrink</div>

<!-- Order -->
<div class="order-1">Order 1</div>
<div class="order-2">Order 2</div>
<div class="order-first">First (-9999)</div>
<div class="order-last">Last (9999)</div>

<!-- Self alignment -->
<div class="self-auto">Auto</div>
<div class="self-start">Start</div>
<div class="self-end">End</div>
<div class="self-center">Center</div>
<div class="self-stretch">Stretch</div>
<div class="self-baseline">Baseline</div>
```

### Grid Container
```html
<!-- Grid template columns -->
<div class="grid grid-cols-1">1 column</div>
<div class="grid grid-cols-2">2 columns</div>
<div class="grid grid-cols-3">3 columns</div>
<div class="grid grid-cols-4">4 columns</div>
<div class="grid grid-cols-5">5 columns</div>
<div class="grid grid-cols-6">6 columns</div>
<div class="grid grid-cols-12">12 columns</div>
<div class="grid grid-cols-none">None</div>

<!-- Custom grid columns with JIT -->
<div class="grid grid-cols-[200px_1fr_1fr]">Custom columns</div>
<div class="grid grid-cols-[repeat(auto-fit,minmax(250px,1fr))]">
  Responsive auto-fit grid
</div>

<!-- Grid template rows -->
<div class="grid grid-rows-1">1 row</div>
<div class="grid grid-rows-2">2 rows</div>
<div class="grid grid-rows-3">3 rows</div>
<div class="grid grid-rows-none">None</div>

<!-- Grid gap -->
<div class="grid gap-0">No gap</div>
<div class="grid gap-1">0.25rem gap</div>
<div class="grid gap-2">0.5rem gap</div>
<div class="grid gap-4">1rem gap</div>
<div class="grid gap-8">2rem gap</div>
<div class="grid gap-x-4 gap-y-8">Different x/y gaps</div>

<!-- Grid auto flow -->
<div class="grid grid-flow-row">Row flow</div>
<div class="grid grid-flow-col">Column flow</div>
<div class="grid grid-flow-row-dense">Row dense</div>
<div class="grid grid-flow-col-dense">Column dense</div>

<!-- Grid auto columns/rows -->
<div class="grid auto-cols-auto">Auto</div>
<div class="grid auto-cols-min">Min</div>
<div class="grid auto-cols-max">Max</div>
<div class="grid auto-cols-fr">Fr</div>
```

### Grid Items
```html
<!-- Column span -->
<div class="col-span-1">Span 1 column</div>
<div class="col-span-2">Span 2 columns</div>
<div class="col-span-full">Span all columns</div>
<div class="col-auto">Auto</div>

<!-- Column start/end -->
<div class="col-start-1">Start at column 1</div>
<div class="col-start-2 col-end-4">Column 2 to 4</div>
<div class="col-end-3">End at column 3</div>

<!-- Row span -->
<div class="row-span-1">Span 1 row</div>
<div class="row-span-2">Span 2 rows</div>
<div class="row-span-full">Span all rows</div>

<!-- Row start/end -->
<div class="row-start-1">Start at row 1</div>
<div class="row-start-2 row-end-4">Row 2 to 4</div>

<!-- Grid item placement -->
<div class="place-self-auto">Auto</div>
<div class="place-self-start">Start</div>
<div class="place-self-end">End</div>
<div class="place-self-center">Center</div>
<div class="place-self-stretch">Stretch</div>

<!-- Justify/align self -->
<div class="justify-self-center">Justify center</div>
<div class="align-self-center">Align center</div>
```

---

## Spacing (Padding & Margin)

### Spacing Scale
```
0    = 0px
px   = 1px
0.5  = 0.125rem (2px)
1    = 0.25rem  (4px)
1.5  = 0.375rem (6px)
2    = 0.5rem   (8px)
2.5  = 0.625rem (10px)
3    = 0.75rem  (12px)
3.5  = 0.875rem (14px)
4    = 1rem     (16px)
5    = 1.25rem  (20px)
6    = 1.5rem   (24px)
7    = 1.75rem  (28px)
8    = 2rem     (32px)
9    = 2.25rem  (36px)
10   = 2.5rem   (40px)
11   = 2.75rem  (44px)
12   = 3rem     (48px)
14   = 3.5rem   (56px)
16   = 4rem     (64px)
20   = 5rem     (80px)
24   = 6rem     (96px)
28   = 7rem     (112px)
32   = 8rem     (128px)
36   = 9rem     (144px)
40   = 10rem    (160px)
44   = 11rem    (176px)
48   = 12rem    (192px)
52   = 13rem    (208px)
56   = 14rem    (224px)
60   = 15rem    (240px)
64   = 16rem    (256px)
72   = 18rem    (288px)
80   = 20rem    (320px)
96   = 24rem    (384px)
```

### Padding
```html
<!-- All sides -->
<div class="p-0">No padding</div>
<div class="p-4">1rem padding all sides</div>
<div class="p-8">2rem padding all sides</div>

<!-- Horizontal (left + right) -->
<div class="px-4">1rem horizontal padding</div>

<!-- Vertical (top + bottom) -->
<div class="py-4">1rem vertical padding</div>

<!-- Individual sides -->
<div class="pt-4">Padding top</div>
<div class="pr-4">Padding right</div>
<div class="pb-4">Padding bottom</div>
<div class="pl-4">Padding left</div>

<!-- Combinations -->
<div class="px-4 py-8">Different horizontal/vertical</div>
<div class="pt-2 px-4 pb-6">Custom each side</div>

<!-- Arbitrary values with JIT -->
<div class="p-[17px]">Custom padding 17px</div>
<div class="px-[2.5rem] py-[1.25rem]">Custom values</div>
```

### Margin
```html
<!-- All sides -->
<div class="m-0">No margin</div>
<div class="m-4">1rem margin all sides</div>
<div class="m-auto">Auto margin (centering)</div>

<!-- Horizontal (left + right) -->
<div class="mx-4">1rem horizontal margin</div>
<div class="mx-auto">Center horizontally</div>

<!-- Vertical (top + bottom) -->
<div class="my-4">1rem vertical margin</div>

<!-- Individual sides -->
<div class="mt-4">Margin top</div>
<div class="mr-4">Margin right</div>
<div class="mb-4">Margin bottom</div>
<div class="ml-4">Margin left</div>

<!-- Negative margins -->
<div class="-m-4">Negative margin all sides</div>
<div class="-mt-8">Negative margin top</div>
<div class="-mx-4">Negative horizontal margin</div>

<!-- Arbitrary values with JIT -->
<div class="m-[13px]">Custom margin 13px</div>
<div class="mt-[2.5rem]">Custom margin top</div>
```

### Space Between
```html
<!-- Space between children (flex/grid) -->
<div class="flex space-x-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<div class="flex flex-col space-y-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<!-- Negative space between -->
<div class="flex -space-x-2">
  <!-- Overlapping items -->
</div>

<!-- Space between reverse -->
<div class="flex flex-row-reverse space-x-4 space-x-reverse">
  Reversed direction
</div>
```

---

## Sizing

### Width
```html
<!-- Fixed widths -->
<div class="w-0">0</div>
<div class="w-px">1px</div>
<div class="w-0.5">0.125rem</div>
<div class="w-1">0.25rem</div>
<div class="w-full">100%</div>
<div class="w-screen">100vw</div>

<!-- Fractional widths -->
<div class="w-1/2">50%</div>
<div class="w-1/3">33.333%</div>
<div class="w-2/3">66.667%</div>
<div class="w-1/4">25%</div>
<div class="w-3/4">75%</div>
<div class="w-1/5">20%</div>
<div class="w-1/6">16.667%</div>
<div class="w-1/12">8.333%</div>

<!-- Auto and fit-content -->
<div class="w-auto">Auto</div>
<div class="w-fit">Fit content</div>

<!-- Min/max content -->
<div class="w-min">Min content</div>
<div class="w-max">Max content</div>

<!-- Arbitrary values with JIT -->
<div class="w-[350px]">350px width</div>
<div class="w-[calc(100%-2rem)]">Calculated width</div>
```

### Min-Width
```html
<div class="min-w-0">0</div>
<div class="min-w-full">100%</div>
<div class="min-w-min">Min content</div>
<div class="min-w-max">Max content</div>
<div class="min-w-fit">Fit content</div>
<div class="min-w-[200px]">Custom min-width</div>
```

### Max-Width
```html
<!-- Responsive max-widths -->
<div class="max-w-xs">20rem (320px)</div>
<div class="max-w-sm">24rem (384px)</div>
<div class="max-w-md">28rem (448px)</div>
<div class="max-w-lg">32rem (512px)</div>
<div class="max-w-xl">36rem (576px)</div>
<div class="max-w-2xl">42rem (672px)</div>
<div class="max-w-3xl">48rem (768px)</div>
<div class="max-w-4xl">56rem (896px)</div>
<div class="max-w-5xl">64rem (1024px)</div>
<div class="max-w-6xl">72rem (1152px)</div>
<div class="max-w-7xl">80rem (1280px)</div>

<!-- Special max-widths -->
<div class="max-w-none">None</div>
<div class="max-w-full">100%</div>
<div class="max-w-screen-sm">640px</div>
<div class="max-w-screen-md">768px</div>
<div class="max-w-screen-lg">1024px</div>
<div class="max-w-screen-xl">1280px</div>
<div class="max-w-screen-2xl">1536px</div>

<!-- Prose widths -->
<div class="max-w-prose">65ch</div>
```

### Height
```html
<!-- Fixed heights (same scale as width) -->
<div class="h-0">0</div>
<div class="h-full">100%</div>
<div class="h-screen">100vh</div>
<div class="h-auto">Auto</div>

<!-- Fractional heights -->
<div class="h-1/2">50%</div>
<div class="h-1/3">33.333%</div>
<div class="h-2/3">66.667%</div>

<!-- Viewport heights -->
<div class="h-screen">100vh</div>
<div class="h-[50vh]">50vh</div>
<div class="h-[100dvh]">Dynamic viewport height</div>
```

### Min-Height
```html
<div class="min-h-0">0</div>
<div class="min-h-full">100%</div>
<div class="min-h-screen">100vh</div>
<div class="min-h-fit">Fit content</div>
<div class="min-h-[400px]">Custom min-height</div>
```

### Max-Height
```html
<div class="max-h-0">0</div>
<div class="max-h-full">100%</div>
<div class="max-h-screen">100vh</div>
<div class="max-h-none">None</div>
<div class="max-h-[600px]">Custom max-height</div>
```

---

## Typography

### Font Family
```html
<p class="font-sans">Sans-serif font</p>
<p class="font-serif">Serif font</p>
<p class="font-mono">Monospace font</p>

<!-- Custom font families (configured in tailwind.config.js) -->
<p class="font-heading">Custom heading font</p>
<p class="font-body">Custom body font</p>
```

### Font Size
```html
<p class="text-xs">0.75rem (12px)</p>
<p class="text-sm">0.875rem (14px)</p>
<p class="text-base">1rem (16px)</p>
<p class="text-lg">1.125rem (18px)</p>
<p class="text-xl">1.25rem (20px)</p>
<p class="text-2xl">1.5rem (24px)</p>
<p class="text-3xl">1.875rem (30px)</p>
<p class="text-4xl">2.25rem (36px)</p>
<p class="text-5xl">3rem (48px)</p>
<p class="text-6xl">3.75rem (60px)</p>
<p class="text-7xl">4.5rem (72px)</p>
<p class="text-8xl">6rem (96px)</p>
<p class="text-9xl">8rem (128px)</p>

<!-- Arbitrary values -->
<p class="text-[17px]">Custom 17px</p>
<p class="text-[clamp(1rem,2vw,1.5rem)]">Fluid typography</p>
```

### Font Weight
```html
<p class="font-thin">100</p>
<p class="font-extralight">200</p>
<p class="font-light">300</p>
<p class="font-normal">400</p>
<p class="font-medium">500</p>
<p class="font-semibold">600</p>
<p class="font-bold">700</p>
<p class="font-extrabold">800</p>
<p class="font-black">900</p>
```

### Font Style
```html
<p class="italic">Italic text</p>
<p class="not-italic">Not italic</p>
```

### Font Variant Numeric
```html
<p class="normal-nums">Normal numbers</p>
<p class="ordinal">Ordinal numbers</p>
<p class="slashed-zero">Slashed zero</p>
<p class="lining-nums">Lining numbers</p>
<p class="oldstyle-nums">Oldstyle numbers</p>
<p class="proportional-nums">Proportional</p>
<p class="tabular-nums">Tabular numbers</p>
<p class="diagonal-fractions">Diagonal fractions</p>
<p class="stacked-fractions">Stacked fractions</p>
```

### Line Height
```html
<p class="leading-none">1</p>
<p class="leading-tight">1.25</p>
<p class="leading-snug">1.375</p>
<p class="leading-normal">1.5</p>
<p class="leading-relaxed">1.625</p>
<p class="leading-loose">2</p>
<p class="leading-3">0.75rem</p>
<p class="leading-4">1rem</p>
<p class="leading-5">1.25rem</p>
<p class="leading-10">2.5rem</p>
```

### Letter Spacing
```html
<p class="tracking-tighter">-0.05em</p>
<p class="tracking-tight">-0.025em</p>
<p class="tracking-normal">0em</p>
<p class="tracking-wide">0.025em</p>
<p class="tracking-wider">0.05em</p>
<p class="tracking-widest">0.1em</p>
```

### Text Alignment
```html
<p class="text-left">Left aligned</p>
<p class="text-center">Center aligned</p>
<p class="text-right">Right aligned</p>
<p class="text-justify">Justified</p>
<p class="text-start">Start (LTR: left, RTL: right)</p>
<p class="text-end">End (LTR: right, RTL: left)</p>
```

### Text Color
```html
<!-- Color palette (slate, gray, zinc, neutral, stone, red, orange, amber, yellow, lime, green, emerald, teal, cyan, sky, blue, indigo, violet, purple, fuchsia, pink, rose) -->
<p class="text-slate-50">Lightest</p>
<p class="text-slate-100">...</p>
<p class="text-slate-500">Medium</p>
<p class="text-slate-900">Darkest</p>
<p class="text-slate-950">Extra dark</p>

<!-- Special colors -->
<p class="text-black">Black</p>
<p class="text-white">White</p>
<p class="text-transparent">Transparent</p>
<p class="text-current">Current color</p>
<p class="text-inherit">Inherit</p>

<!-- Arbitrary colors -->
<p class="text-[#1a1a1a]">Custom hex</p>
<p class="text-[rgb(255,0,0)]">RGB</p>
```

### Text Decoration
```html
<p class="underline">Underlined</p>
<p class="overline">Overlined</p>
<p class="line-through">Strike through</p>
<p class="no-underline">No decoration</p>

<!-- Decoration style -->
<p class="decoration-solid">Solid line</p>
<p class="decoration-double">Double line</p>
<p class="decoration-dotted">Dotted line</p>
<p class="decoration-dashed">Dashed line</p>
<p class="decoration-wavy">Wavy line</p>

<!-- Decoration color -->
<p class="underline decoration-blue-500">Blue underline</p>

<!-- Decoration thickness -->
<p class="underline decoration-1">1px thick</p>
<p class="underline decoration-2">2px thick</p>
<p class="underline decoration-4">4px thick</p>
<p class="underline decoration-8">8px thick</p>

<!-- Decoration offset -->
<p class="underline underline-offset-1">Offset 1px</p>
<p class="underline underline-offset-4">Offset 4px</p>
<p class="underline underline-offset-8">Offset 8px</p>
```

### Text Transform
```html
<p class="uppercase">UPPERCASE TEXT</p>
<p class="lowercase">lowercase text</p>
<p class="capitalize">Capitalize Each Word</p>
<p class="normal-case">Normal case</p>
```

### Text Overflow
```html
<p class="truncate">Truncate with ellipsis...</p>
<p class="text-ellipsis overflow-hidden">Ellipsis</p>
<p class="text-clip overflow-hidden">Clip</p>
```

### Vertical Alignment
```html
<span class="align-baseline">Baseline</span>
<span class="align-top">Top</span>
<span class="align-middle">Middle</span>
<span class="align-bottom">Bottom</span>
<span class="align-text-top">Text top</span>
<span class="align-text-bottom">Text bottom</span>
<span class="align-sub">Subscript</span>
<span class="align-super">Superscript</span>
```

### Whitespace & Word Break
```html
<!-- Whitespace -->
<p class="whitespace-normal">Normal</p>
<p class="whitespace-nowrap">No wrap</p>
<p class="whitespace-pre">Preserve whitespace</p>
<p class="whitespace-pre-line">Preserve line breaks</p>
<p class="whitespace-pre-wrap">Preserve and wrap</p>

<!-- Word break -->
<p class="break-normal">Normal break</p>
<p class="break-words">Break words</p>
<p class="break-all">Break all</p>

<!-- Hyphens -->
<p class="hyphens-none">No hyphens</p>
<p class="hyphens-manual">Manual hyphens</p>
<p class="hyphens-auto">Auto hyphens</p>
```

### Text Indent
```html
<p class="indent-0">No indent</p>
<p class="indent-4">1rem indent</p>
<p class="indent-8">2rem indent</p>
<p class="-indent-4">Hanging indent</p>
```

---

## Backgrounds

### Background Color
```html
<!-- All color palettes available -->
<div class="bg-slate-50">Lightest</div>
<div class="bg-slate-500">Medium</div>
<div class="bg-slate-900">Darkest</div>

<!-- Special backgrounds -->
<div class="bg-transparent">Transparent</div>
<div class="bg-current">Current color</div>
<div class="bg-inherit">Inherit</div>

<!-- Arbitrary colors -->
<div class="bg-[#f0f0f0]">Custom hex</div>
<div class="bg-[rgb(240,240,240)]">RGB</div>
<div class="bg-[hsl(0,0%,94%)]">HSL</div>
```

### Background Opacity
```html
<div class="bg-blue-500 bg-opacity-0">0%</div>
<div class="bg-blue-500 bg-opacity-25">25%</div>
<div class="bg-blue-500 bg-opacity-50">50%</div>
<div class="bg-blue-500 bg-opacity-75">75%</div>
<div class="bg-blue-500 bg-opacity-100">100%</div>

<!-- Using opacity utilities -->
<div class="bg-blue-500 opacity-50">50% opacity on entire element</div>

<!-- Modern approach with color opacity -->
<div class="bg-blue-500/50">50% opacity (Tailwind 3+)</div>
<div class="bg-blue-500/[0.37]">37% opacity</div>
```

### Background Image
```html
<!-- Gradient directions -->
<div class="bg-gradient-to-t">To top</div>
<div class="bg-gradient-to-tr">To top right</div>
<div class="bg-gradient-to-r">To right</div>
<div class="bg-gradient-to-br">To bottom right</div>
<div class="bg-gradient-to-b">To bottom</div>
<div class="bg-gradient-to-bl">To bottom left</div>
<div class="bg-gradient-to-l">To left</div>
<div class="bg-gradient-to-tl">To top left</div>

<!-- Gradient colors -->
<div class="bg-gradient-to-r from-purple-400 via-pink-500 to-red-500">
  Three color gradient
</div>

<div class="bg-gradient-to-br from-blue-400 to-blue-600">
  Two color gradient
</div>

<!-- Gradient color stops -->
<div class="bg-gradient-to-r from-blue-500 from-10% via-purple-500 via-50% to-pink-500 to-90%">
  Custom color stops
</div>

<!-- None -->
<div class="bg-none">No background image</div>

<!-- Custom images with JIT -->
<div class="bg-[url('/img/hero.jpg')]">Background image</div>
```

### Background Position
```html
<div class="bg-bottom">Bottom</div>
<div class="bg-center">Center</div>
<div class="bg-left">Left</div>
<div class="bg-left-bottom">Left bottom</div>
<div class="bg-left-top">Left top</div>
<div class="bg-right">Right</div>
<div class="bg-right-bottom">Right bottom</div>
<div class="bg-right-top">Right top</div>
<div class="bg-top">Top</div>
```

### Background Size
```html
<div class="bg-auto">Auto</div>
<div class="bg-cover">Cover</div>
<div class="bg-contain">Contain</div>
<div class="bg-[length:200px_100px]">Custom size</div>
```

### Background Repeat
```html
<div class="bg-repeat">Repeat</div>
<div class="bg-no-repeat">No repeat</div>
<div class="bg-repeat-x">Repeat horizontally</div>
<div class="bg-repeat-y">Repeat vertically</div>
<div class="bg-repeat-round">Round</div>
<div class="bg-repeat-space">Space</div>
```

### Background Attachment
```html
<div class="bg-fixed">Fixed</div>
<div class="bg-local">Local</div>
<div class="bg-scroll">Scroll</div>
```

### Background Clip
```html
<div class="bg-clip-border">Clip to border</div>
<div class="bg-clip-padding">Clip to padding</div>
<div class="bg-clip-content">Clip to content</div>
<div class="bg-clip-text">Clip to text</div>

<!-- Text gradient effect -->
<h1 class="text-6xl font-bold bg-gradient-to-r from-blue-500 to-purple-600 bg-clip-text text-transparent">
  Gradient Text
</h1>
```

### Background Origin
```html
<div class="bg-origin-border">Border box</div>
<div class="bg-origin-padding">Padding box</div>
<div class="bg-origin-content">Content box</div>
```

---

## Borders

### Border Width
```html
<!-- All sides -->
<div class="border">1px all sides</div>
<div class="border-0">No border</div>
<div class="border-2">2px all sides</div>
<div class="border-4">4px all sides</div>
<div class="border-8">8px all sides</div>

<!-- Individual sides -->
<div class="border-t">Top</div>
<div class="border-r">Right</div>
<div class="border-b">Bottom</div>
<div class="border-l">Left</div>

<!-- Combinations -->
<div class="border-x">Horizontal</div>
<div class="border-y">Vertical</div>

<!-- Custom widths -->
<div class="border-t-2 border-r-4 border-b-2 border-l-0">
  Different widths each side
</div>
```

### Border Color
```html
<!-- All color palettes -->
<div class="border border-slate-300">Border color</div>
<div class="border border-blue-500">Blue border</div>

<!-- Special colors -->
<div class="border border-transparent">Transparent</div>
<div class="border border-current">Current color</div>

<!-- Individual sides -->
<div class="border-t-blue-500 border-b-red-500">
  Different colors
</div>

<!-- With opacity -->
<div class="border border-blue-500/50">50% opacity</div>
```

### Border Style
```html
<div class="border border-solid">Solid</div>
<div class="border border-dashed">Dashed</div>
<div class="border border-dotted">Dotted</div>
<div class="border border-double">Double</div>
<div class="border border-hidden">Hidden</div>
<div class="border border-none">None</div>
```

### Border Radius
```html
<!-- All corners -->
<div class="rounded-none">0</div>
<div class="rounded-sm">0.125rem</div>
<div class="rounded">0.25rem</div>
<div class="rounded-md">0.375rem</div>
<div class="rounded-lg">0.5rem</div>
<div class="rounded-xl">0.75rem</div>
<div class="rounded-2xl">1rem</div>
<div class="rounded-3xl">1.5rem</div>
<div class="rounded-full">9999px (pill/circle)</div>

<!-- Individual corners -->
<div class="rounded-t">Top corners</div>
<div class="rounded-r">Right corners</div>
<div class="rounded-b">Bottom corners</div>
<div class="rounded-l">Left corners</div>
<div class="rounded-tl">Top left</div>
<div class="rounded-tr">Top right</div>
<div class="rounded-br">Bottom right</div>
<div class="rounded-bl">Bottom left</div>

<!-- Custom radius -->
<div class="rounded-[12px]">Custom 12px</div>
<div class="rounded-tl-2xl rounded-br-2xl">
  Diagonal rounded corners
</div>
```

### Divide (Between Elements)
```html
<!-- Divide width -->
<div class="divide-y">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>

<div class="divide-x">
  <div>Col 1</div>
  <div>Col 2</div>
  <div>Col 3</div>
</div>

<div class="divide-y-2">Thicker divider</div>

<!-- Divide color -->
<div class="divide-y divide-gray-200">
  Gray dividers
</div>

<!-- Divide style -->
<div class="divide-y divide-dashed">Dashed dividers</div>

<!-- Divide opacity -->
<div class="divide-y divide-gray-200 divide-opacity-50">
  50% opacity dividers
</div>

<!-- Divide reverse (for reversed flex) -->
<div class="flex flex-col-reverse divide-y divide-y-reverse">
  Reversed with dividers
</div>
```

### Outline
```html
<!-- Outline width -->
<button class="outline outline-1">1px outline</button>
<button class="outline outline-2">2px outline</button>
<button class="outline outline-4">4px outline</button>

<!-- Outline color -->
<button class="outline outline-blue-500">Blue outline</button>
<button class="outline outline-blue-500/50">50% opacity</button>

<!-- Outline style -->
<button class="outline outline-solid">Solid</button>
<button class="outline outline-dashed">Dashed</button>
<button class="outline outline-dotted">Dotted</button>
<button class="outline outline-double">Double</button>

<!-- Outline offset -->
<button class="outline outline-2 outline-offset-0">No offset</button>
<button class="outline outline-2 outline-offset-2">2px offset</button>
<button class="outline outline-2 outline-offset-4">4px offset</button>

<!-- Remove outline -->
<button class="outline-none">No outline</button>
```

### Ring (Focus Rings)
```html
<!-- Ring width -->
<input class="ring ring-2">Default ring</input>
<input class="ring-0">No ring</input>
<input class="ring-1">1px ring</input>
<input class="ring-2">2px ring</input>
<input class="ring-4">4px ring</input>

<!-- Ring color -->
<input class="ring-2 ring-blue-500">Blue ring</input>
<input class="ring-2 ring-blue-500/50">50% opacity</input>

<!-- Ring offset (gap between element and ring) -->
<input class="ring-2 ring-blue-500 ring-offset-0">No offset</input>
<input class="ring-2 ring-blue-500 ring-offset-2">2px offset</input>
<input class="ring-2 ring-blue-500 ring-offset-4">4px offset</input>

<!-- Ring offset color -->
<input class="ring-2 ring-blue-500 ring-offset-2 ring-offset-white">
  White offset
</input>

<!-- Inset ring -->
<input class="ring-2 ring-inset ring-blue-500">Inset ring</input>

<!-- Focus ring pattern -->
<input class="focus:ring-2 focus:ring-blue-500 focus:ring-offset-2">
  Focus ring on interaction
</input>
```

---

## Effects & Filters

### Box Shadow
```html
<div class="shadow-sm">Small shadow</div>
<div class="shadow">Default shadow</div>
<div class="shadow-md">Medium shadow</div>
<div class="shadow-lg">Large shadow</div>
<div class="shadow-xl">Extra large shadow</div>
<div class="shadow-2xl">2XL shadow</div>
<div class="shadow-inner">Inner shadow</div>
<div class="shadow-none">No shadow</div>

<!-- Custom shadows -->
<div class="shadow-[0_35px_60px_-15px_rgba(0,0,0,0.3)]">
  Custom shadow
</div>

<!-- Colored shadows -->
<div class="shadow-lg shadow-blue-500/50">Blue shadow</div>
```

### Drop Shadow (Filter)
```html
<div class="drop-shadow-sm">Small drop shadow</div>
<div class="drop-shadow">Default drop shadow</div>
<div class="drop-shadow-md">Medium drop shadow</div>
<div class="drop-shadow-lg">Large drop shadow</div>
<div class="drop-shadow-xl">XL drop shadow</div>
<div class="drop-shadow-2xl">2XL drop shadow</div>
<div class="drop-shadow-none">No drop shadow</div>

<!-- Custom drop shadow -->
<div class="drop-shadow-[0_35px_35px_rgba(0,0,0,0.25)]">
  Custom drop shadow
</div>
```

### Opacity
```html
<div class="opacity-0">0% (invisible)</div>
<div class="opacity-5">5%</div>
<div class="opacity-10">10%</div>
<div class="opacity-25">25%</div>
<div class="opacity-50">50%</div>
<div class="opacity-75">75%</div>
<div class="opacity-90">90%</div>
<div class="opacity-100">100% (opaque)</div>

<!-- Arbitrary opacity -->
<div class="opacity-[0.37]">37%</div>
```

### Mix Blend Mode
```html
<div class="mix-blend-normal">Normal</div>
<div class="mix-blend-multiply">Multiply</div>
<div class="mix-blend-screen">Screen</div>
<div class="mix-blend-overlay">Overlay</div>
<div class="mix-blend-darken">Darken</div>
<div class="mix-blend-lighten">Lighten</div>
<div class="mix-blend-color-dodge">Color dodge</div>
<div class="mix-blend-color-burn">Color burn</div>
<div class="mix-blend-hard-light">Hard light</div>
<div class="mix-blend-soft-light">Soft light</div>
<div class="mix-blend-difference">Difference</div>
<div class="mix-blend-exclusion">Exclusion</div>
<div class="mix-blend-hue">Hue</div>
<div class="mix-blend-saturation">Saturation</div>
<div class="mix-blend-color">Color</div>
<div class="mix-blend-luminosity">Luminosity</div>
```

### Background Blend Mode
```html
<div class="bg-blend-normal">Normal</div>
<div class="bg-blend-multiply">Multiply</div>
<div class="bg-blend-screen">Screen</div>
<div class="bg-blend-overlay">Overlay</div>
<!-- All same options as mix-blend-mode -->
```

### Filters
```html
<!-- Blur -->
<div class="blur-none">No blur</div>
<div class="blur-sm">Small blur (4px)</div>
<div class="blur">Default blur (8px)</div>
<div class="blur-md">Medium blur (12px)</div>
<div class="blur-lg">Large blur (16px)</div>
<div class="blur-xl">XL blur (24px)</div>
<div class="blur-2xl">2XL blur (40px)</div>
<div class="blur-3xl">3XL blur (64px)</div>

<!-- Brightness -->
<div class="brightness-0">0 (black)</div>
<div class="brightness-50">50%</div>
<div class="brightness-100">100% (normal)</div>
<div class="brightness-150">150%</div>
<div class="brightness-200">200%</div>

<!-- Contrast -->
<div class="contrast-0">0</div>
<div class="contrast-50">50%</div>
<div class="contrast-100">100% (normal)</div>
<div class="contrast-150">150%</div>
<div class="contrast-200">200%</div>

<!-- Grayscale -->
<div class="grayscale-0">No grayscale</div>
<div class="grayscale">Full grayscale</div>

<!-- Hue Rotate -->
<div class="hue-rotate-0">0deg</div>
<div class="hue-rotate-15">15deg</div>
<div class="hue-rotate-30">30deg</div>
<div class="hue-rotate-60">60deg</div>
<div class="hue-rotate-90">90deg</div>
<div class="hue-rotate-180">180deg</div>

<!-- Invert -->
<div class="invert-0">No invert</div>
<div class="invert">Full invert</div>

<!-- Saturate -->
<div class="saturate-0">0</div>
<div class="saturate-50">50%</div>
<div class="saturate-100">100% (normal)</div>
<div class="saturate-150">150%</div>
<div class="saturate-200">200%</div>

<!-- Sepia -->
<div class="sepia-0">No sepia</div>
<div class="sepia">Full sepia</div>

<!-- Combining filters -->
<img class="blur-sm brightness-110 contrast-125 saturate-150" src="..." alt="...">

<!-- Backdrop filters (for background) -->
<div class="backdrop-blur-sm">Backdrop blur</div>
<div class="backdrop-brightness-110">Backdrop brightness</div>
<div class="backdrop-contrast-125">Backdrop contrast</div>
<div class="backdrop-grayscale">Backdrop grayscale</div>
<div class="backdrop-hue-rotate-15">Backdrop hue rotate</div>
<div class="backdrop-invert">Backdrop invert</div>
<div class="backdrop-opacity-50">Backdrop opacity</div>
<div class="backdrop-saturate-150">Backdrop saturate</div>
<div class="backdrop-sepia">Backdrop sepia</div>
```

---

## Transitions & Animations

### Transition Property
```html
<div class="transition-none">No transition</div>
<div class="transition-all">All properties</div>
<div class="transition">Common properties</div>
<div class="transition-colors">Colors only</div>
<div class="transition-opacity">Opacity only</div>
<div class="transition-shadow">Shadow only</div>
<div class="transition-transform">Transform only</div>

<!-- Custom properties -->
<div class="transition-[width,height]">Custom properties</div>
```

### Transition Duration
```html
<div class="duration-75">75ms</div>
<div class="duration-100">100ms</div>
<div class="duration-150">150ms</div>
<div class="duration-200">200ms</div>
<div class="duration-300">300ms</div>
<div class="duration-500">500ms</div>
<div class="duration-700">700ms</div>
<div class="duration-1000">1000ms (1s)</div>

<!-- Custom duration -->
<div class="duration-[2s]">2 seconds</div>
```

### Transition Timing Function
```html
<div class="ease-linear">Linear</div>
<div class="ease-in">Ease in</div>
<div class="ease-out">Ease out</div>
<div class="ease-in-out">Ease in-out</div>

<!-- Custom easing -->
<div class="ease-[cubic-bezier(0.95,0.05,0.795,0.035)]">
  Custom cubic-bezier
</div>
```

### Transition Delay
```html
<div class="delay-75">75ms delay</div>
<div class="delay-100">100ms delay</div>
<div class="delay-150">150ms delay</div>
<div class="delay-200">200ms delay</div>
<div class="delay-300">300ms delay</div>
<div class="delay-500">500ms delay</div>
<div class="delay-700">700ms delay</div>
<div class="delay-1000">1000ms delay</div>
```

### Animation
```html
<!-- Built-in animations -->
<div class="animate-none">No animation</div>
<div class="animate-spin">Spinning (loading spinner)</div>
<div class="animate-ping">Pinging (notification dot)</div>
<div class="animate-pulse">Pulsing (skeleton loader)</div>
<div class="animate-bounce">Bouncing</div>

<!-- Complete transition example -->
<button class="
  transition-all
  duration-300
  ease-in-out
  hover:scale-110
  hover:shadow-lg
  active:scale-95
">
  Interactive Button
</button>
```

---

## Transforms

### Scale
```html
<!-- Uniform scale -->
<div class="scale-0">0%</div>
<div class="scale-50">50%</div>
<div class="scale-75">75%</div>
<div class="scale-90">90%</div>
<div class="scale-95">95%</div>
<div class="scale-100">100% (normal)</div>
<div class="scale-105">105%</div>
<div class="scale-110">110%</div>
<div class="scale-125">125%</div>
<div class="scale-150">150%</div>

<!-- X-axis scale -->
<div class="scale-x-50">50% width</div>
<div class="scale-x-150">150% width</div>

<!-- Y-axis scale -->
<div class="scale-y-50">50% height</div>
<div class="scale-y-150">150% height</div>

<!-- Custom scale -->
<div class="scale-[1.7]">170%</div>
```

### Rotate
```html
<div class="rotate-0">0deg</div>
<div class="rotate-1">1deg</div>
<div class="rotate-3">3deg</div>
<div class="rotate-6">6deg</div>
<div class="rotate-12">12deg</div>
<div class="rotate-45">45deg</div>
<div class="rotate-90">90deg</div>
<div class="rotate-180">180deg</div>

<!-- Negative rotation -->
<div class="-rotate-45">-45deg</div>
<div class="-rotate-90">-90deg</div>

<!-- Custom rotation -->
<div class="rotate-[17deg]">17deg</div>
```

### Translate
```html
<!-- X-axis translate (uses spacing scale) -->
<div class="translate-x-0">0</div>
<div class="translate-x-4">1rem right</div>
<div class="translate-x-1/2">50% right</div>
<div class="translate-x-full">100% right</div>
<div class="-translate-x-4">1rem left</div>
<div class="-translate-x-1/2">50% left</div>

<!-- Y-axis translate -->
<div class="translate-y-0">0</div>
<div class="translate-y-4">1rem down</div>
<div class="translate-y-1/2">50% down</div>
<div class="translate-y-full">100% down</div>
<div class="-translate-y-4">1rem up</div>
<div class="-translate-y-1/2">50% up</div>

<!-- Custom translate -->
<div class="translate-x-[13px]">13px right</div>

<!-- Centering with translate -->
<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
  Perfect center
</div>
```

### Skew
```html
<!-- X-axis skew -->
<div class="skew-x-0">0deg</div>
<div class="skew-x-3">3deg</div>
<div class="skew-x-6">6deg</div>
<div class="skew-x-12">12deg</div>
<div class="-skew-x-12">-12deg</div>

<!-- Y-axis skew -->
<div class="skew-y-0">0deg</div>
<div class="skew-y-3">3deg</div>
<div class="skew-y-6">6deg</div>
<div class="skew-y-12">12deg</div>
<div class="-skew-y-12">-12deg</div>
```

### Transform Origin
```html
<div class="origin-center">Center (default)</div>
<div class="origin-top">Top</div>
<div class="origin-top-right">Top right</div>
<div class="origin-right">Right</div>
<div class="origin-bottom-right">Bottom right</div>
<div class="origin-bottom">Bottom</div>
<div class="origin-bottom-left">Bottom left</div>
<div class="origin-left">Left</div>
<div class="origin-top-left">Top left</div>

<!-- Custom origin -->
<div class="origin-[33%_75%]">Custom origin</div>
```

### Combined Transforms
```html
<!-- Multiple transforms -->
<div class="transform rotate-45 scale-150 translate-x-4">
  Combined transforms
</div>

<!-- Interactive card example -->
<div class="
  transition-transform
  duration-300
  hover:scale-105
  hover:-rotate-2
  hover:translate-y-2
">
  Hover me
</div>
```

---

## Interactivity

### Cursor
```html
<div class="cursor-auto">Auto</div>
<div class="cursor-default">Default</div>
<div class="cursor-pointer">Pointer (hand)</div>
<div class="cursor-wait">Wait</div>
<div class="cursor-text">Text (I-beam)</div>
<div class="cursor-move">Move</div>
<div class="cursor-help">Help</div>
<div class="cursor-not-allowed">Not allowed</div>
<div class="cursor-none">None</div>
<div class="cursor-context-menu">Context menu</div>
<div class="cursor-progress">Progress</div>
<div class="cursor-cell">Cell</div>
<div class="cursor-crosshair">Crosshair</div>
<div class="cursor-vertical-text">Vertical text</div>
<div class="cursor-alias">Alias</div>
<div class="cursor-copy">Copy</div>
<div class="cursor-no-drop">No drop</div>
<div class="cursor-grab">Grab</div>
<div class="cursor-grabbing">Grabbing</div>

<!-- Resize cursors -->
<div class="cursor-col-resize">Column resize</div>
<div class="cursor-row-resize">Row resize</div>
<div class="cursor-n-resize">North resize</div>
<div class="cursor-e-resize">East resize</div>
<div class="cursor-s-resize">South resize</div>
<div class="cursor-w-resize">West resize</div>
<div class="cursor-ne-resize">NE resize</div>
<div class="cursor-nw-resize">NW resize</div>
<div class="cursor-se-resize">SE resize</div>
<div class="cursor-sw-resize">SW resize</div>
<div class="cursor-ew-resize">EW resize</div>
<div class="cursor-ns-resize">NS resize</div>

<!-- Custom cursor -->
<div class="cursor-[url(hand.cur),pointer]">Custom cursor</div>
```

### Pointer Events
```html
<div class="pointer-events-none">No pointer events</div>
<div class="pointer-events-auto">Auto pointer events</div>
```

### Resize
```html
<textarea class="resize-none">Not resizable</textarea>
<textarea class="resize">Resizable (both)</textarea>
<textarea class="resize-y">Vertically resizable</textarea>
<textarea class="resize-x">Horizontally resizable</textarea>
```

### Scroll Behavior
```html
<html class="scroll-smooth">
  <!-- Smooth scrolling for anchor links -->
</html>

<div class="scroll-auto">Auto scroll</div>
```

### Scroll Snap
```html
<!-- Container -->
<div class="snap-none">No snap</div>
<div class="snap-x">Snap horizontally</div>
<div class="snap-y">Snap vertically</div>
<div class="snap-both">Snap both</div>

<!-- Snap strictness -->
<div class="snap-mandatory">Mandatory snap</div>
<div class="snap-proximity">Proximity snap</div>

<!-- Children snap alignment -->
<div class="snap-start">Snap to start</div>
<div class="snap-end">Snap to end</div>
<div class="snap-center">Snap to center</div>
<div class="snap-align-none">No snap align</div>

<!-- Example carousel -->
<div class="flex overflow-x-auto snap-x snap-mandatory">
  <div class="snap-center flex-shrink-0 w-full">Slide 1</div>
  <div class="snap-center flex-shrink-0 w-full">Slide 2</div>
  <div class="snap-center flex-shrink-0 w-full">Slide 3</div>
</div>
```

### Touch Action
```html
<div class="touch-auto">Auto</div>
<div class="touch-none">None</div>
<div class="touch-pan-x">Pan X</div>
<div class="touch-pan-left">Pan left</div>
<div class="touch-pan-right">Pan right</div>
<div class="touch-pan-y">Pan Y</div>
<div class="touch-pan-up">Pan up</div>
<div class="touch-pan-down">Pan down</div>
<div class="touch-pinch-zoom">Pinch zoom</div>
<div class="touch-manipulation">Manipulation</div>
```

### User Select
```html
<div class="select-none">Not selectable</div>
<div class="select-text">Selectable text</div>
<div class="select-all">Select all on click</div>
<div class="select-auto">Auto</div>
```

### Will Change
```html
<div class="will-change-auto">Auto</div>
<div class="will-change-scroll">Scroll</div>
<div class="will-change-contents">Contents</div>
<div class="will-change-transform">Transform</div>
```

### Appearance
```html
<select class="appearance-none">No browser styling</select>
<select class="appearance-auto">Auto appearance</select>
```

### Accent Color
```html
<input type="checkbox" class="accent-blue-500">
<input type="radio" class="accent-green-500">
<input type="range" class="accent-purple-500">
```

### Caret Color
```html
<input class="caret-blue-500">
<textarea class="caret-red-500"></textarea>
```

---

## Responsive Design Patterns

### Breakpoints
```
sm   = 640px   (min-width)
md   = 768px   (min-width)
lg   = 1024px  (min-width)
xl   = 1280px  (min-width)
2xl  = 1536px  (min-width)
```

### Mobile-First Responsive Design
```html
<!-- Mobile first: base styles apply to all screens, then override for larger -->
<div class="text-sm md:text-base lg:text-lg xl:text-xl">
  Responsive text sizing
</div>

<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4">
  <!-- 1 column mobile, 2 on small, 3 on large, 4 on xl -->
</div>

<!-- Responsive padding -->
<div class="p-4 md:p-6 lg:p-8">
  Increasing padding on larger screens
</div>

<!-- Hide/show at breakpoints -->
<div class="block md:hidden">
  Only visible on mobile
</div>

<div class="hidden md:block">
  Hidden on mobile, visible on md+
</div>

<div class="hidden lg:block">
  Only visible on large screens
</div>
```

### Responsive Layout Patterns

#### Stack to Row
```html
<div class="flex flex-col md:flex-row gap-4">
  <div class="w-full md:w-1/2">Column 1</div>
  <div class="w-full md:w-1/2">Column 2</div>
</div>
```

#### Responsive Grid
```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
  <div>Item 4</div>
</div>
```

#### Sidebar Layout
```html
<div class="flex flex-col lg:flex-row gap-6">
  <!-- Sidebar -->
  <aside class="w-full lg:w-64 flex-shrink-0">
    Sidebar
  </aside>

  <!-- Main content -->
  <main class="flex-1">
    Main content
  </main>
</div>
```

#### Card Grid
```html
<div class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 gap-6">
  <div class="bg-white rounded-lg shadow p-6">Card 1</div>
  <div class="bg-white rounded-lg shadow p-6">Card 2</div>
  <div class="bg-white rounded-lg shadow p-6">Card 3</div>
</div>
```

#### Container with Max Width
```html
<div class="container mx-auto px-4 sm:px-6 lg:px-8">
  <div class="max-w-7xl mx-auto">
    Centered content with responsive padding
  </div>
</div>
```

### Responsive Typography
```html
<!-- Fluid headings -->
<h1 class="text-3xl sm:text-4xl md:text-5xl lg:text-6xl font-bold">
  Large Heading
</h1>

<h2 class="text-2xl sm:text-3xl md:text-4xl font-semibold">
  Medium Heading
</h2>

<!-- Responsive line height -->
<p class="text-base leading-relaxed md:text-lg md:leading-loose">
  Body text with responsive sizing and line height
</p>
```

### Responsive Images
```html
<!-- Responsive image -->
<img
  class="w-full h-auto"
  src="image.jpg"
  alt="Responsive image"
>

<!-- Different aspect ratios -->
<div class="aspect-square md:aspect-video lg:aspect-[16/10]">
  <img class="w-full h-full object-cover" src="..." alt="...">
</div>

<!-- Responsive object fit -->
<img
  class="object-cover md:object-contain lg:object-scale-down"
  src="..."
  alt="..."
>
```

### Advanced Responsive Patterns
```html
<!-- Max 2 columns, then 3, then 4 -->
<div class="grid grid-cols-2 md:grid-cols-3 lg:grid-cols-4 gap-4">
  Cards
</div>

<!-- Responsive flexbox alignment -->
<div class="flex flex-col items-start md:flex-row md:items-center md:justify-between">
  <div>Logo</div>
  <nav>Navigation</nav>
</div>

<!-- Conditional spacing -->
<div class="space-y-4 md:space-y-0 md:space-x-6 flex flex-col md:flex-row">
  Items with different spacing on mobile vs desktop
</div>

<!-- Responsive aspect ratio -->
<div class="aspect-[4/3] sm:aspect-video lg:aspect-[21/9]">
  Video or image container
</div>
```

---

## Custom Configuration

### Extending the Theme (tailwind.config.js)

```javascript
/** @type {import('tailwindcss').Config} */
module.exports = {
  theme: {
    extend: {
      // Custom colors
      colors: {
        primary: {
          50: '#f0f9ff',
          100: '#e0f2fe',
          200: '#bae6fd',
          300: '#7dd3fc',
          400: '#38bdf8',
          500: '#0ea5e9',
          600: '#0284c7',
          700: '#0369a1',
          800: '#075985',
          900: '#0c4a6e',
          950: '#082f49',
        },
        secondary: '#8b5cf6',
        accent: {
          light: '#fbbf24',
          DEFAULT: '#f59e0b',
          dark: '#d97706',
        },
      },

      // Custom spacing
      spacing: {
        '128': '32rem',
        '144': '36rem',
      },

      // Custom font families
      fontFamily: {
        sans: ['Inter', 'system-ui', 'sans-serif'],
        serif: ['Merriweather', 'Georgia', 'serif'],
        mono: ['Fira Code', 'monospace'],
        display: ['Poppins', 'sans-serif'],
        body: ['Open Sans', 'sans-serif'],
      },

      // Custom font sizes
      fontSize: {
        '2xs': '0.625rem',
        '3xl': '2rem',
        '4xl': '2.5rem',
        '5xl': '3rem',
      },

      // Custom breakpoints
      screens: {
        'xs': '475px',
        '3xl': '1920px',
      },

      // Custom border radius
      borderRadius: {
        '4xl': '2rem',
        '5xl': '3rem',
      },

      // Custom z-index
      zIndex: {
        '60': '60',
        '70': '70',
        '80': '80',
        '90': '90',
        '100': '100',
      },

      // Custom animations
      keyframes: {
        'fade-in': {
          '0%': { opacity: '0' },
          '100%': { opacity: '1' },
        },
        'fade-out': {
          '0%': { opacity: '1' },
          '100%': { opacity: '0' },
        },
        'slide-in': {
          '0%': { transform: 'translateX(-100%)' },
          '100%': { transform: 'translateX(0)' },
        },
        'slide-out': {
          '0%': { transform: 'translateX(0)' },
          '100%': { transform: 'translateX(100%)' },
        },
        'scale-in': {
          '0%': { transform: 'scale(0.9)', opacity: '0' },
          '100%': { transform: 'scale(1)', opacity: '1' },
        },
        wiggle: {
          '0%, 100%': { transform: 'rotate(-3deg)' },
          '50%': { transform: 'rotate(3deg)' },
        },
      },
      animation: {
        'fade-in': 'fade-in 0.3s ease-in-out',
        'fade-out': 'fade-out 0.3s ease-in-out',
        'slide-in': 'slide-in 0.3s ease-out',
        'slide-out': 'slide-out 0.3s ease-out',
        'scale-in': 'scale-in 0.2s ease-out',
        'wiggle': 'wiggle 1s ease-in-out infinite',
      },

      // Custom box shadows
      boxShadow: {
        'inner-lg': 'inset 0 2px 4px 0 rgb(0 0 0 / 0.1)',
        '3xl': '0 35px 60px -15px rgba(0, 0, 0, 0.3)',
        'glow': '0 0 20px rgba(59, 130, 246, 0.5)',
      },

      // Custom gradients (use with bg-gradient-to-*)
      backgroundImage: {
        'gradient-radial': 'radial-gradient(var(--tw-gradient-stops))',
        'gradient-conic': 'conic-gradient(from 180deg at 50% 50%, var(--tw-gradient-stops))',
        'hero-pattern': "url('/img/hero-pattern.svg')",
      },

      // Custom aspect ratios
      aspectRatio: {
        '4/3': '4 / 3',
        '21/9': '21 / 9',
      },

      // Custom transitions
      transitionProperty: {
        'height': 'height',
        'spacing': 'margin, padding',
      },

      // Custom min/max widths
      minWidth: {
        '1/2': '50%',
        '1/3': '33.333333%',
        '2/3': '66.666667%',
      },
      maxWidth: {
        '8xl': '88rem',
        '9xl': '96rem',
      },

      // Custom line heights
      lineHeight: {
        'extra-loose': '2.5',
        '12': '3rem',
      },

      // Custom letter spacing
      letterSpacing: {
        'extra-wide': '0.15em',
      },
    },
  },
  plugins: [],
}
```

### Using CSS Variables with Tailwind

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        primary: 'rgb(var(--color-primary) / <alpha-value>)',
        secondary: 'rgb(var(--color-secondary) / <alpha-value>)',
      },
    },
  },
}
```

```css
/* globals.css */
:root {
  --color-primary: 59 130 246; /* RGB values for blue-500 */
  --color-secondary: 139 92 246; /* RGB values for purple-500 */
}

[data-theme="dark"] {
  --color-primary: 96 165 250; /* RGB values for blue-400 */
  --color-secondary: 167 139 250; /* RGB values for purple-400 */
}
```

```html
<!-- Usage -->
<div class="bg-primary text-white">Primary background</div>
<div class="bg-primary/50">Primary with 50% opacity</div>
```

---

## Plugin Development

### Creating a Custom Plugin

```javascript
// tailwind.config.js
const plugin = require('tailwindcss/plugin')

module.exports = {
  plugins: [
    // Text shadow plugin
    plugin(function({ addUtilities, theme }) {
      const textShadows = {
        '.text-shadow-sm': {
          textShadow: '0 1px 2px rgba(0, 0, 0, 0.1)',
        },
        '.text-shadow': {
          textShadow: '0 2px 4px rgba(0, 0, 0, 0.1)',
        },
        '.text-shadow-lg': {
          textShadow: '0 8px 16px rgba(0, 0, 0, 0.1)',
        },
        '.text-shadow-none': {
          textShadow: 'none',
        },
      }

      addUtilities(textShadows)
    }),

    // Glass morphism plugin
    plugin(function({ addUtilities }) {
      addUtilities({
        '.glass': {
          background: 'rgba(255, 255, 255, 0.1)',
          backdropFilter: 'blur(10px)',
          borderRadius: '10px',
          border: '1px solid rgba(255, 255, 255, 0.2)',
        },
        '.glass-dark': {
          background: 'rgba(0, 0, 0, 0.1)',
          backdropFilter: 'blur(10px)',
          borderRadius: '10px',
          border: '1px solid rgba(0, 0, 0, 0.2)',
        },
      })
    }),

    // Custom component plugin
    plugin(function({ addComponents, theme }) {
      addComponents({
        '.btn': {
          padding: `${theme('spacing.2')} ${theme('spacing.4')}`,
          borderRadius: theme('borderRadius.md'),
          fontWeight: theme('fontWeight.semibold'),
          transition: 'all 0.3s',
          '&:hover': {
            transform: 'translateY(-2px)',
            boxShadow: theme('boxShadow.lg'),
          },
        },
        '.btn-primary': {
          backgroundColor: theme('colors.blue.500'),
          color: theme('colors.white'),
          '&:hover': {
            backgroundColor: theme('colors.blue.600'),
          },
        },
        '.card': {
          backgroundColor: theme('colors.white'),
          borderRadius: theme('borderRadius.lg'),
          padding: theme('spacing.6'),
          boxShadow: theme('boxShadow.md'),
        },
      })
    }),

    // Responsive utilities with variants
    plugin(function({ addUtilities, matchUtilities, theme }) {
      matchUtilities(
        {
          'grid-auto-fit': (value) => ({
            gridTemplateColumns: `repeat(auto-fit, minmax(${value}, 1fr))`,
          }),
          'grid-auto-fill': (value) => ({
            gridTemplateColumns: `repeat(auto-fill, minmax(${value}, 1fr))`,
          }),
        },
        { values: theme('spacing') }
      )
    }),
  ],
}
```

### Using the Custom Plugin

```html
<!-- Text shadow -->
<h1 class="text-shadow-lg">Heading with shadow</h1>

<!-- Glass morphism -->
<div class="glass p-6">
  Glass effect card
</div>

<!-- Custom button component -->
<button class="btn btn-primary">
  Click me
</button>

<!-- Custom card component -->
<div class="card">
  Card content
</div>

<!-- Auto-fit grid -->
<div class="grid grid-auto-fit-[250px] gap-4">
  <div>Item 1</div>
  <div>Item 2</div>
  <div>Item 3</div>
</div>
```

### Official Tailwind Plugins

```javascript
// tailwind.config.js
module.exports = {
  plugins: [
    require('@tailwindcss/forms'),
    require('@tailwindcss/typography'),
    require('@tailwindcss/aspect-ratio'),
    require('@tailwindcss/container-queries'),
  ],
}
```

---

## Component Recipes

### 1. Modern Card
```html
<div class="max-w-sm rounded-lg overflow-hidden shadow-lg hover:shadow-2xl transition-shadow duration-300 bg-white">
  <img class="w-full h-48 object-cover" src="/img/card-top.jpg" alt="Card image">
  <div class="p-6">
    <div class="font-bold text-xl mb-2">Card Title</div>
    <p class="text-gray-700 text-base">
      Some quick example text to build on the card title and make up the bulk of the card's content.
    </p>
  </div>
  <div class="px-6 pb-6">
    <button class="bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded transition-colors">
      Learn More
    </button>
  </div>
</div>
```

### 2. Navigation Bar
```html
<nav class="bg-white shadow-lg">
  <div class="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
    <div class="flex justify-between h-16">
      <div class="flex items-center">
        <a href="#" class="text-xl font-bold text-gray-800">Logo</a>
      </div>
      <div class="hidden md:flex items-center space-x-8">
        <a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Home</a>
        <a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">About</a>
        <a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Services</a>
        <a href="#" class="text-gray-600 hover:text-gray-900 transition-colors">Contact</a>
      </div>
      <div class="flex items-center">
        <button class="md:hidden p-2">
          <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
            <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M4 6h16M4 12h16M4 18h16"/>
          </svg>
        </button>
      </div>
    </div>
  </div>
</nav>
```

### 3. Hero Section
```html
<section class="relative bg-gradient-to-r from-purple-600 to-blue-600 h-screen flex items-center justify-center text-white">
  <div class="absolute inset-0 bg-black opacity-50"></div>
  <div class="container mx-auto px-6 relative z-10 text-center">
    <h1 class="text-5xl md:text-6xl lg:text-7xl font-bold mb-6 animate-fade-in">
      Welcome to Our Platform
    </h1>
    <p class="text-xl md:text-2xl mb-8 max-w-3xl mx-auto">
      Build amazing things with the power of modern web technologies
    </p>
    <div class="flex flex-col sm:flex-row gap-4 justify-center">
      <button class="bg-white text-purple-600 px-8 py-3 rounded-full font-semibold hover:bg-gray-100 transition-colors">
        Get Started
      </button>
      <button class="border-2 border-white px-8 py-3 rounded-full font-semibold hover:bg-white hover:text-purple-600 transition-colors">
        Learn More
      </button>
    </div>
  </div>
</section>
```

### 4. Form with Validation States
```html
<form class="max-w-md mx-auto p-6 bg-white rounded-lg shadow-md">
  <div class="mb-4">
    <label class="block text-gray-700 text-sm font-bold mb-2" for="email">
      Email
    </label>
    <input
      class="w-full px-3 py-2 border border-gray-300 rounded-md focus:outline-none focus:ring-2 focus:ring-blue-500 focus:border-transparent"
      id="email"
      type="email"
      placeholder="Enter your email"
    >
  </div>

  <!-- Error state -->
  <div class="mb-4">
    <label class="block text-gray-700 text-sm font-bold mb-2" for="password">
      Password
    </label>
    <input
      class="w-full px-3 py-2 border border-red-500 rounded-md focus:outline-none focus:ring-2 focus:ring-red-500"
      id="password"
      type="password"
    >
    <p class="text-red-500 text-xs italic mt-1">Please enter a valid password.</p>
  </div>

  <!-- Success state -->
  <div class="mb-6">
    <label class="block text-gray-700 text-sm font-bold mb-2" for="username">
      Username
    </label>
    <input
      class="w-full px-3 py-2 border border-green-500 rounded-md focus:outline-none focus:ring-2 focus:ring-green-500"
      id="username"
      type="text"
    >
    <p class="text-green-500 text-xs italic mt-1">Username is available!</p>
  </div>

  <button
    class="w-full bg-blue-500 hover:bg-blue-700 text-white font-bold py-2 px-4 rounded focus:outline-none focus:shadow-outline transition-colors"
    type="submit"
  >
    Sign Up
  </button>
</form>
```

### 5. Modal/Dialog
```html
<!-- Overlay -->
<div class="fixed inset-0 bg-black bg-opacity-50 flex items-center justify-center p-4 z-50">
  <!-- Modal -->
  <div class="bg-white rounded-lg shadow-xl max-w-md w-full transform transition-all animate-scale-in">
    <!-- Header -->
    <div class="flex items-center justify-between p-6 border-b">
      <h3 class="text-xl font-semibold text-gray-900">Modal Title</h3>
      <button class="text-gray-400 hover:text-gray-600 transition-colors">
        <svg class="w-6 h-6" fill="none" stroke="currentColor" viewBox="0 0 24 24">
          <path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M6 18L18 6M6 6l12 12"/>
        </svg>
      </button>
    </div>

    <!-- Body -->
    <div class="p-6">
      <p class="text-gray-600">
        This is the modal content. You can put any content here.
      </p>
    </div>

    <!-- Footer -->
    <div class="flex justify-end gap-3 p-6 border-t bg-gray-50">
      <button class="px-4 py-2 border border-gray-300 rounded-md text-gray-700 hover:bg-gray-100 transition-colors">
        Cancel
      </button>
      <button class="px-4 py-2 bg-blue-500 text-white rounded-md hover:bg-blue-600 transition-colors">
        Confirm
      </button>
    </div>
  </div>
</div>
```

### 6. Alert/Notification
```html
<!-- Success Alert -->
<div class="bg-green-50 border-l-4 border-green-500 p-4 mb-4" role="alert">
  <div class="flex items-center">
    <svg class="w-6 h-6 text-green-500 mr-3" fill="currentColor" viewBox="0 0 20 20">
      <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zm3.707-9.293a1 1 0 00-1.414-1.414L9 10.586 7.707 9.293a1 1 0 00-1.414 1.414l2 2a1 1 0 001.414 0l4-4z" clip-rule="evenodd"/>
    </svg>
    <div>
      <p class="font-semibold text-green-800">Success</p>
      <p class="text-green-700">Your changes have been saved.</p>
    </div>
  </div>
</div>

<!-- Error Alert -->
<div class="bg-red-50 border-l-4 border-red-500 p-4 mb-4" role="alert">
  <div class="flex items-center">
    <svg class="w-6 h-6 text-red-500 mr-3" fill="currentColor" viewBox="0 0 20 20">
      <path fill-rule="evenodd" d="M10 18a8 8 0 100-16 8 8 0 000 16zM8.707 7.293a1 1 0 00-1.414 1.414L8.586 10l-1.293 1.293a1 1 0 101.414 1.414L10 11.414l1.293 1.293a1 1 0 001.414-1.414L11.414 10l1.293-1.293a1 1 0 00-1.414-1.414L10 8.586 8.707 7.293z" clip-rule="evenodd"/>
    </svg>
    <div>
      <p class="font-semibold text-red-800">Error</p>
      <p class="text-red-700">There was a problem with your request.</p>
    </div>
  </div>
</div>

<!-- Warning Alert -->
<div class="bg-yellow-50 border-l-4 border-yellow-500 p-4" role="alert">
  <div class="flex items-center">
    <svg class="w-6 h-6 text-yellow-500 mr-3" fill="currentColor" viewBox="0 0 20 20">
      <path fill-rule="evenodd" d="M8.257 3.099c.765-1.36 2.722-1.36 3.486 0l5.58 9.92c.75 1.334-.213 2.98-1.742 2.98H4.42c-1.53 0-2.493-1.646-1.743-2.98l5.58-9.92zM11 13a1 1 0 11-2 0 1 1 0 012 0zm-1-8a1 1 0 00-1 1v3a1 1 0 002 0V6a1 1 0 00-1-1z" clip-rule="evenodd"/>
    </svg>
    <div>
      <p class="font-semibold text-yellow-800">Warning</p>
      <p class="text-yellow-700">Please review before proceeding.</p>
    </div>
  </div>
</div>
```

### 7. Badge/Tag
```html
<div class="flex flex-wrap gap-2">
  <span class="inline-flex items-center px-3 py-0.5 rounded-full text-sm font-medium bg-blue-100 text-blue-800">
    Primary
  </span>

  <span class="inline-flex items-center px-3 py-0.5 rounded-full text-sm font-medium bg-green-100 text-green-800">
    Success
  </span>

  <span class="inline-flex items-center px-3 py-0.5 rounded-full text-sm font-medium bg-red-100 text-red-800">
    Error
  </span>

  <span class="inline-flex items-center px-3 py-0.5 rounded-full text-sm font-medium bg-yellow-100 text-yellow-800">
    Warning
  </span>

  <!-- Badge with remove button -->
  <span class="inline-flex items-center px-3 py-0.5 rounded-full text-sm font-medium bg-purple-100 text-purple-800">
    Tag
    <button class="ml-2 inline-flex items-center p-0.5 rounded-full hover:bg-purple-200">
      <svg class="w-3 h-3" fill="currentColor" viewBox="0 0 20 20">
        <path fill-rule="evenodd" d="M4.293 4.293a1 1 0 011.414 0L10 8.586l4.293-4.293a1 1 0 111.414 1.414L11.414 10l4.293 4.293a1 1 0 01-1.414 1.414L10 11.414l-4.293 4.293a1 1 0 01-1.414-1.414L8.586 10 4.293 5.707a1 1 0 010-1.414z" clip-rule="evenodd"/>
      </svg>
    </button>
  </span>
</div>
```

### 8. Loading Spinner
```html
<!-- Spinner -->
<div class="flex justify-center items-center">
  <div class="animate-spin rounded-full h-12 w-12 border-b-2 border-blue-500"></div>
</div>

<!-- Spinner with text -->
<div class="flex flex-col items-center gap-4">
  <div class="animate-spin rounded-full h-16 w-16 border-t-2 border-b-2 border-purple-500"></div>
  <p class="text-gray-600">Loading...</p>
</div>

<!-- Pulse loader -->
<div class="flex gap-2">
  <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse"></div>
  <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse" style="animation-delay: 0.2s"></div>
  <div class="w-3 h-3 bg-blue-500 rounded-full animate-pulse" style="animation-delay: 0.4s"></div>
</div>
```

### 9. Dropdown Menu
```html
<div class="relative inline-block text-left">
  <!-- Trigger button -->
  <button class="inline-flex justify-center items-center w-full px-4 py-2 bg-white border border-gray-300 rounded-md shadow-sm text-sm font-medium text-gray-700 hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-blue-500">
    Options
    <svg class="ml-2 -mr-1 h-5 w-5" fill="currentColor" viewBox="0 0 20 20">
      <path fill-rule="evenodd" d="M5.293 7.293a1 1 0 011.414 0L10 10.586l3.293-3.293a1 1 0 111.414 1.414l-4 4a1 1 0 01-1.414 0l-4-4a1 1 0 010-1.414z" clip-rule="evenodd"/>
    </svg>
  </button>

  <!-- Dropdown menu (hidden by default, toggle with JS) -->
  <div class="origin-top-right absolute right-0 mt-2 w-56 rounded-md shadow-lg bg-white ring-1 ring-black ring-opacity-5 divide-y divide-gray-100">
    <div class="py-1">
      <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Edit</a>
      <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Duplicate</a>
    </div>
    <div class="py-1">
      <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Archive</a>
      <a href="#" class="block px-4 py-2 text-sm text-gray-700 hover:bg-gray-100">Move</a>
    </div>
    <div class="py-1">
      <a href="#" class="block px-4 py-2 text-sm text-red-700 hover:bg-red-50">Delete</a>
    </div>
  </div>
</div>
```

### 10. Pricing Card
```html
<div class="max-w-sm rounded-lg overflow-hidden shadow-lg bg-white border border-gray-200 hover:border-blue-500 transition-colors">
  <div class="px-6 py-8 bg-gradient-to-br from-blue-500 to-blue-600 text-white text-center">
    <h3 class="text-2xl font-bold mb-2">Pro Plan</h3>
    <div class="text-4xl font-bold mb-2">
      $29<span class="text-lg font-normal">/month</span>
    </div>
    <p class="text-blue-100">Best for professionals</p>
  </div>

  <div class="px-6 py-8">
    <ul class="space-y-4">
      <li class="flex items-center">
        <svg class="w-5 h-5 text-green-500 mr-3" fill="currentColor" viewBox="0 0 20 20">
          <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
        </svg>
        <span>Unlimited projects</span>
      </li>
      <li class="flex items-center">
        <svg class="w-5 h-5 text-green-500 mr-3" fill="currentColor" viewBox="0 0 20 20">
          <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
        </svg>
        <span>Priority support</span>
      </li>
      <li class="flex items-center">
        <svg class="w-5 h-5 text-green-500 mr-3" fill="currentColor" viewBox="0 0 20 20">
          <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
        </svg>
        <span>Advanced analytics</span>
      </li>
      <li class="flex items-center">
        <svg class="w-5 h-5 text-green-500 mr-3" fill="currentColor" viewBox="0 0 20 20">
          <path fill-rule="evenodd" d="M16.707 5.293a1 1 0 010 1.414l-8 8a1 1 0 01-1.414 0l-4-4a1 1 0 011.414-1.414L8 12.586l7.293-7.293a1 1 0 011.414 0z" clip-rule="evenodd"/>
        </svg>
        <span>Team collaboration</span>
      </li>
    </ul>
  </div>

  <div class="px-6 pb-8">
    <button class="w-full bg-blue-500 hover:bg-blue-600 text-white font-bold py-3 px-4 rounded-lg transition-colors">
      Get Started
    </button>
  </div>
</div>
```

---

## JIT Mode Patterns

JIT (Just-In-Time) mode generates styles on-demand as you author your templates. It's enabled by default in Tailwind CSS 3.0+.

### Arbitrary Values
```html
<!-- Arbitrary colors -->
<div class="bg-[#1da1f2]">Twitter blue</div>
<div class="text-[#ff6b6b]">Custom red text</div>

<!-- Arbitrary spacing -->
<div class="top-[117px]">Custom position</div>
<div class="p-[13px]">Custom padding</div>
<div class="m-[33px]">Custom margin</div>

<!-- Arbitrary sizes -->
<div class="w-[347px]">Custom width</div>
<div class="h-[600px]">Custom height</div>
<div class="text-[17px]">Custom font size</div>

<!-- Arbitrary values with CSS functions -->
<div class="w-[calc(100%-2rem)]">Calculated width</div>
<div class="h-[min(100vh,800px)]">Min height</div>
<div class="text-[clamp(1rem,2vw,1.5rem)]">Fluid typography</div>

<!-- Arbitrary gradients -->
<div class="bg-[linear-gradient(45deg,#ff0000,#00ff00)]">
  Custom gradient
</div>

<!-- Arbitrary grid -->
<div class="grid-cols-[200px_1fr_1fr]">Custom grid columns</div>
<div class="grid-cols-[repeat(auto-fit,minmax(250px,1fr))]">
  Responsive auto-fit grid
</div>
```

### Arbitrary Properties
```html
<!-- Any CSS property -->
<div class="[mask-type:luminance]">Custom mask type</div>
<div class="[backdrop-filter:saturate(180%)_blur(20px)]">
  Custom backdrop filter
</div>
<div class="[text-wrap:balance]">Balanced text wrap</div>

<!-- Grid properties -->
<div class="[grid-auto-rows:minmax(100px,auto)]">
  Custom grid auto rows
</div>

<!-- Custom properties for animations -->
<div class="[@keyframes_slide-in:{0%{transform:translateX(-100%)}100%{transform:translateX(0)}}] animate-[slide-in_1s_ease-out]">
  Custom keyframe animation
</div>
```

### Arbitrary Variants
```html
<!-- Custom media queries -->
<div class="[@media(min-width:400px)]:block">
  Custom breakpoint
</div>

<!-- Custom selectors -->
<div class="[&:nth-child(3)]:bg-blue-500">
  Third child styling
</div>

<div class="[&>*]:p-4">
  Style all direct children
</div>

<!-- Data attributes -->
<div class="data-[state=open]:bg-blue-500">
  Based on data attribute
</div>

<!-- Aria attributes -->
<button class="aria-[expanded=true]:rotate-180">
  Rotate when expanded
</button>
```

### Advanced JIT Patterns
```html
<!-- Complex selectors -->
<div class="[&:not(:last-child)]:mb-4">
  Margin on all but last
</div>

<!-- Peer and group with arbitrary values -->
<div class="group">
  <div class="peer"></div>
  <div class="peer-hover:[transform:scale(1.1)]">
    Complex peer interaction
  </div>
</div>

<!-- Combining multiple arbitrary values -->
<div class="
  [background:linear-gradient(45deg,#000,#fff)]
  [box-shadow:0_20px_60px_rgba(0,0,0,0.3)]
  [clip-path:polygon(0_0,100%_0,100%_85%,0_100%)]
">
  Multiple custom values
</div>

<!-- Important modifier with arbitrary values -->
<div class="!text-[#ff0000]">
  Important custom color
</div>
```

### Dynamic Class Names with Safelist
```javascript
// tailwind.config.js
module.exports = {
  safelist: [
    // Safelist dynamic class patterns
    {
      pattern: /bg-(red|green|blue)-(100|500|900)/,
    },
    {
      pattern: /text-(sm|base|lg|xl)/,
      variants: ['sm', 'md', 'lg'],
    },
    // Safelist specific classes
    'bg-gradient-to-r',
    'from-purple-400',
    'to-pink-600',
  ],
}
```

---

## Performance Optimization

### 1. Purge Unused Styles
```javascript
// tailwind.config.js
module.exports = {
  content: [
    './src/**/*.{html,js,jsx,ts,tsx,vue}',
    './pages/**/*.{html,js,jsx,ts,tsx}',
    './components/**/*.{html,js,jsx,ts,tsx}',
    './app/**/*.{html,js,jsx,ts,tsx}',
  ],
  // Tailwind will scan these files and remove unused styles
}
```

### 2. Optimize Build Size
```javascript
// tailwind.config.js
module.exports = {
  // Disable unused core plugins
  corePlugins: {
    float: false,
    objectFit: false,
    objectPosition: false,
  },

  // Or use a blocklist
  corePlugins: {
    preflight: true, // Keep
    // Disable specific plugins
  },
}
```

### 3. Use CSS Layer for Better Control
```css
/* global.css */
@tailwind base;
@tailwind components;
@tailwind utilities;

/* Custom base styles */
@layer base {
  h1 {
    @apply text-4xl font-bold;
  }

  h2 {
    @apply text-3xl font-semibold;
  }

  a {
    @apply text-blue-600 hover:text-blue-800;
  }
}

/* Custom component styles */
@layer components {
  .btn-primary {
    @apply py-2 px-4 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700 focus:outline-none focus:ring-2 focus:ring-blue-400 focus:ring-opacity-75;
  }

  .card {
    @apply p-6 max-w-sm mx-auto bg-white rounded-xl shadow-lg;
  }
}

/* Custom utility classes */
@layer utilities {
  .text-shadow {
    text-shadow: 0 2px 4px rgba(0,0,0,0.1);
  }

  .text-shadow-lg {
    text-shadow: 0 15px 30px rgba(0,0,0,0.3);
  }

  @variants responsive {
    .no-scrollbar::-webkit-scrollbar {
      display: none;
    }
    .no-scrollbar {
      -ms-overflow-style: none;
      scrollbar-width: none;
    }
  }
}
```

### 4. Extract Components (Don't Repeat)
```html
<!-- ❌ Bad: Repeating classes -->
<button class="py-2 px-4 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700">
  Button 1
</button>
<button class="py-2 px-4 bg-blue-500 text-white font-semibold rounded-lg shadow-md hover:bg-blue-700">
  Button 2
</button>

<!-- ✅ Good: Extract to component -->
<!-- MyButton.jsx -->
<button className="btn-primary">
  {children}
</button>
```

### 5. Use @apply Wisely
```css
/* Use for component classes that are reused */
@layer components {
  .btn {
    @apply py-2 px-4 font-semibold rounded-lg shadow-md focus:outline-none focus:ring-2 focus:ring-opacity-75;
  }
}

/* But prefer component composition in JS frameworks */
```

### 6. Minimize Arbitrary Values
```html
<!-- ❌ Avoid too many arbitrary values -->
<div class="w-[347px] h-[219px] p-[17px] text-[14.5px]">
  <!-- These can't be purged efficiently -->
</div>

<!-- ✅ Use design tokens instead -->
<div class="w-80 h-56 p-4 text-sm">
  <!-- Uses predefined scale -->
</div>
```

### 7. Preload Critical CSS
```html
<!-- In your HTML head -->
<link rel="preload" href="/dist/app.css" as="style">
<link rel="stylesheet" href="/dist/app.css">
```

### 8. Monitor Bundle Size
```bash
# Install bundle analyzer
npm install -D tailwindcss-bundle-size

# Add to package.json
"scripts": {
  "analyze": "tailwindcss-bundle-size"
}
```

### 9. Use Production Build
```javascript
// postcss.config.js
module.exports = {
  plugins: {
    tailwindcss: {},
    autoprefixer: {},
    ...(process.env.NODE_ENV === 'production'
      ? { cssnano: { preset: 'default' } }
      : {}),
  },
}
```

### 10. Lazy Load Non-Critical Styles
```html
<!-- Load print styles lazily -->
<link
  rel="stylesheet"
  href="/print.css"
  media="print"
  onload="this.media='all'"
>
```

---

## Searchable Class Index

### Layout
- `container` - Responsive container
- `block`, `inline-block`, `inline`, `flex`, `grid` - Display types
- `hidden` - Hide element
- `static`, `relative`, `absolute`, `fixed`, `sticky` - Positioning
- `inset-{0,x-0,y-0}` - Position all sides
- `top-{size}`, `right-{size}`, `bottom-{size}`, `left-{size}` - Position
- `overflow-{auto,hidden,visible,scroll}` - Overflow
- `z-{index}` - Z-index

### Flexbox
- `flex-{row,col,row-reverse,col-reverse}` - Direction
- `flex-{wrap,nowrap,wrap-reverse}` - Wrapping
- `justify-{start,end,center,between,around,evenly}` - Main axis
- `items-{start,end,center,baseline,stretch}` - Cross axis
- `content-{start,end,center,between,around,evenly}` - Multi-line
- `flex-{1,auto,initial,none}` - Flex item
- `order-{number}` - Flex order
- `self-{auto,start,end,center,stretch}` - Align self

### Grid
- `grid-cols-{1-12}` - Grid columns
- `grid-rows-{1-6}` - Grid rows
- `gap-{size}`, `gap-x-{size}`, `gap-y-{size}` - Grid gap
- `col-span-{1-12}`, `row-span-{1-6}` - Span columns/rows
- `col-start-{number}`, `row-start-{number}` - Start position
- `grid-flow-{row,col,dense}` - Auto flow

### Spacing
- `p-{size}` - Padding all
- `px-{size}`, `py-{size}` - Padding horizontal/vertical
- `pt-{size}`, `pr-{size}`, `pb-{size}`, `pl-{size}` - Padding sides
- `m-{size}` - Margin all
- `mx-{size}`, `my-{size}` - Margin horizontal/vertical
- `mt-{size}`, `mr-{size}`, `mb-{size}`, `ml-{size}` - Margin sides
- `space-x-{size}`, `space-y-{size}` - Space between children

### Sizing
- `w-{size}`, `h-{size}` - Width/height
- `w-{fraction}`, `h-{fraction}` - Fractional width/height
- `min-w-{size}`, `max-w-{size}` - Min/max width
- `min-h-{size}`, `max-h-{size}` - Min/max height

### Typography
- `font-{sans,serif,mono}` - Font family
- `text-{xs,sm,base,lg,xl,2xl-9xl}` - Font size
- `font-{thin,extralight,light,normal,medium,semibold,bold,extrabold,black}` - Weight
- `leading-{size}` - Line height
- `tracking-{size}` - Letter spacing
- `text-{left,center,right,justify}` - Text alignment
- `text-{color}` - Text color
- `underline`, `line-through`, `no-underline` - Text decoration
- `uppercase`, `lowercase`, `capitalize` - Text transform
- `truncate` - Truncate text

### Backgrounds
- `bg-{color}` - Background color
- `bg-gradient-to-{direction}` - Gradient direction
- `from-{color}`, `via-{color}`, `to-{color}` - Gradient colors
- `bg-{center,top,bottom,left,right}` - Background position
- `bg-{cover,contain,auto}` - Background size
- `bg-{repeat,no-repeat}` - Background repeat

### Borders
- `border`, `border-{0,2,4,8}` - Border width
- `border-{t,r,b,l}` - Border sides
- `border-{color}` - Border color
- `border-{solid,dashed,dotted,double,none}` - Border style
- `rounded-{none,sm,md,lg,xl,2xl,3xl,full}` - Border radius
- `rounded-{t,r,b,l,tl,tr,br,bl}` - Corner radius
- `divide-{x,y}` - Divide between children

### Effects
- `shadow-{sm,md,lg,xl,2xl,inner,none}` - Box shadow
- `opacity-{0-100}` - Opacity
- `blur-{sm,md,lg,xl,2xl,3xl}` - Blur filter
- `brightness-{0-200}` - Brightness filter
- `contrast-{0-200}` - Contrast filter
- `grayscale` - Grayscale filter
- `saturate-{0-200}` - Saturation filter

### Transitions
- `transition-{all,colors,opacity,shadow,transform}` - Transition property
- `duration-{75-1000}` - Transition duration
- `ease-{linear,in,out,in-out}` - Transition timing
- `delay-{75-1000}` - Transition delay
- `animate-{spin,ping,pulse,bounce}` - Animations

### Transforms
- `scale-{0-150}` - Scale transform
- `rotate-{0-180}` - Rotate transform
- `translate-{x,y}-{size}` - Translate transform
- `skew-{x,y}-{size}` - Skew transform
- `origin-{position}` - Transform origin

### Interactivity
- `cursor-{pointer,wait,text,move,not-allowed}` - Cursor
- `select-{none,text,all,auto}` - User select
- `resize-{none,x,y}` - Resize
- `snap-{x,y,both}` - Scroll snap

### States & Variants
- `hover:` - Hover state
- `focus:` - Focus state
- `active:` - Active state
- `disabled:` - Disabled state
- `group-hover:` - Group hover
- `peer-hover:` - Peer hover
- `first:`, `last:`, `odd:`, `even:` - Pseudo-classes
- `sm:`, `md:`, `lg:`, `xl:`, `2xl:` - Responsive breakpoints
- `dark:` - Dark mode

### Accessibility
- `sr-only` - Screen reader only
- `not-sr-only` - Not screen reader only
- `focus-visible:` - Focus visible
- `aria-{attribute}:` - ARIA states

---

## Quick Tips

### 1. Debugging Classes
```html
<!-- Add outline to see element boundaries -->
<div class="outline outline-red-500">Debug element</div>

<!-- Ring for interactive debugging -->
<div class="ring-2 ring-yellow-500">Debug ring</div>
```

### 2. Common Centering Patterns
```html
<!-- Horizontal center with margin -->
<div class="mx-auto max-w-md">Centered</div>

<!-- Center with flexbox -->
<div class="flex justify-center items-center h-screen">
  Centered both ways
</div>

<!-- Absolute center -->
<div class="absolute top-1/2 left-1/2 -translate-x-1/2 -translate-y-1/2">
  Perfect center
</div>
```

### 3. Aspect Ratio Containers
```html
<div class="aspect-square">1:1</div>
<div class="aspect-video">16:9</div>
<div class="aspect-[4/3]">4:3</div>
```

### 4. Truncate Text
```html
<!-- Single line -->
<p class="truncate">Long text that will be truncated...</p>

<!-- Multiple lines with line-clamp (requires @tailwindcss/line-clamp plugin) -->
<p class="line-clamp-3">
  Long text that will be clamped to 3 lines...
</p>
```

### 5. Dark Mode
```javascript
// tailwind.config.js
module.exports = {
  darkMode: 'class', // or 'media'
}
```

```html
<!-- Usage -->
<div class="bg-white dark:bg-gray-900 text-black dark:text-white">
  Adapts to dark mode
</div>
```

---

## Resources

### Official Documentation
- [Tailwind CSS Docs](https://tailwindcss.com/docs)
- [Tailwind CSS Playground](https://play.tailwindcss.com)
- [Tailwind UI Components](https://tailwindui.com)

### Community Resources
- [Awesome Tailwind CSS](https://github.com/aniftyco/awesome-tailwindcss)
- [Tailwind Components](https://tailwindcomponents.com)
- [Headless UI](https://headlessui.com)

### Tools
- [Tailwind CSS IntelliSense](https://marketplace.visualstudio.com/items?itemName=bradlc.vscode-tailwindcss)
- [Tailwind Shades](https://www.tints.dev)
- [Hypercolor](https://hypercolor.dev) - Gradient generator

---

This comprehensive reference covers 100+ utility patterns, responsive design patterns, custom configurations, plugin development, component recipes, JIT mode patterns, and performance optimization techniques for Tailwind CSS. Use this as a searchable guide when building with Tailwind CSS.
