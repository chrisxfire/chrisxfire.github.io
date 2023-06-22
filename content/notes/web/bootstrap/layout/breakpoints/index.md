---
title: notes > web > bootstrap > layout > breakpoints
date: 2023-06-16T00:00:00-06:00
draft: false
weight: 1
---

# Overview
- Customizable widths that determine how responsive layout behaves across device or viewport sizes.
- The building blocks of responsive design.  Used to control when layout can be adapted at a particular viewport or device size.
- Works in conjunction with CSS media queries.

# Available Breakpoints
Also referred to as *grid tiers*.  Holds containers at width multiples of 12:
| Breakpoint        | Class infix | Dimensions |
| ----------------- | ----------- | ---------- |
| Extra small       | None        | <576px     |
| Small             | `sm`          | ≥576px     |
| Medium            | `md`          | ≥768px     |
| Large             | `lg`          | ≥992px     |
| Extra large       | `xl`          | ≥1200px    |
| Extra extra large | `xxl`         | ≥1400px    |

Customizable via `scss/_variables.css`:
```css
$grid-breakpoints: (
  xs: 0,
  sm: 576px,
  md: 768px,
  lg: 992px,
  xl: 1200px,
  xxl: 1400px
);
```

# Usage:
## Min-width
```css
// No media query necessary for xs breakpoint as it's effectively `@media (min-width: 0) { ... }`

// Example: Hide starting at `min-width: 0`, and then show at the `sm` breakpoint
.custom-class {
  display: none;
}
@include media-breakpoint-up(sm) {
  .custom-class {
    display: block;
  }
}
```

## Max-width
```css
// No media query necessary for xs breakpoint as it's effectively `@media (max-width: 0) { ... }`

// Example: Style from medium breakpoint and down
@include media-breakpoint-down(md) {
  .custom-class {
    display: block;
  }
}
```

## Single breakpoint
For targeting a single segment of screen sizes:
```css
@include media-breakpoint-only(xs) { ... }
@include media-breakpoint-only(sm) { ... }
@include media-breakpoint-only(md) { ... }
@include media-breakpoint-only(lg) { ... }
@include media-breakpoint-only(xl) { ... }
@include media-breakpoint-only(xxl) { ... }
```

## Between breakpoints
For spanning multiple breakpoint widths:
```css
@include media-breakpoint-between(md, xl) { ... }
```