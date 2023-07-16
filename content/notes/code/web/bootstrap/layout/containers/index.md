---
title: notes > code > web > bootstrap > layout > containers
date: 2023-06-16T00:00:00-06:00
draft: false
weight: 3
---

# Overview
- Documentation: https://getbootstrap.com/docs/5.3/layout/containers/
- A build block that contains, pads, and aligns content within a given device or viewport.
- <o>Required when using default grid system</o>.
- Can be nested, but most layotus do not require this.

# 3 Containers
- `.container` — sets a `max-width` at each responsive breakpoint
- `.container-<breakpoint>` — uses `width: 100%` until the specified breakpoint
- `.container-fluid` — sets `width: 100%` at all breakpoints

Comparison:  
| Extra small <576px | Small ≥576px | Medium ≥768px | Large ≥992px | X-Large ≥1200px | XX-Large ≥1400px |
| ------------------ | ------------ | ------------- | ------------ | --------------- | ---------------- |
| `.container`       | 100%         | 540px         | 720px        | 960px           | 1140px           | 1320px |
| `.container-sm`    | 100%         | 540px         | 720px        | 960px           | 1140px           | 1320px |
| `.container-md`    | 100%         | 100%          | 720px        | 960px           | 1140px           | 1320px |
| `.container-lg`    | 100%         | 100%          | 100%         | 960px           | 1140px           | 1320px |
| `.container-xl`    | 100%         | 100%          | 100%         | 100%            | 1140px           | 1320px |
| `.container-xxl`   | 100%         | 100%          | 100%         | 100%            | 100%             | 1320px |
| `.container-fluid` | 100%         | 100%          | 100%         | 100%            | 100%             | 100%   |

# Usage
## Default container
```css
<div class="container">
  <!-- Content here -->
</div>
```

## Responsive containers
```css
<div class="container-sm">100% wide until small breakpoint</div>
<div class="container-md">100% wide until medium breakpoint</div>
<div class="container-lg">100% wide until large breakpoint</div>
<div class="container-xl">100% wide until extra large breakpoint</div>
<div class="container-xxl">100% wide until extra extra large breakpoint</div>
```

## Fluid containers
```css
<div class="container-fluid">
  ...
</div>
```

# Customize
In `scss/_variables.css`:
```css
$container-max-widths: (
  sm: 540px,
  md: 720px,
  lg: 960px,
  xl: 1140px,
  xxl: 1320px
);
```

Create custom mix-ins:
```css
/* Source mixin */
@mixin make-container($padding-x: $container-padding-x) {
  width: 100%;
  padding-right: $padding-x;
  padding-left: $padding-x;
  margin-right: auto;
  margin-left: auto;
}

/* Usage */
.custom-container {
  @include make-container();
}
```
