---
title: notes > code > web > html > images
date: 2023-04-26T17:22:39-0600
draft: false
---
# Overview
Syntax:  
```html
<img src="url" alt="alternatetext">
```

The `alt` attribute's value is also displayed if the image is not found.  

Always specify `alt`, `width` and `height` for images.

# Sizing
Images can be sized. Failing to size them will result in page flicker while the page loads.

Use the width and height attributes:  
```html
<img src="img_girl.jpg" alt="Girl in a jacket" width="500" height="600">
```
Or, use the style attribute with width and height properties with the pixels suffix:
```html
<img src="img_girl.jpg" alt="Girl in a jacket" style="width:500px;height:600px;">
```

# Image Maps
Image maps are images with clickable areas.

Create an image map and use it in an image:
```html
<imgsrc="workplace.jpg"alt="Workplace"usemap="#workmap">

<map name="workmap">
  <areashape="rect"coords="34,44,270,350"alt="Computer"href="computer.htm">
  <areashape="rect"coords="290,172,333,250"alt="Phone"href="phone.htm">
  <areashape="circle"coords="337,300,44"alt="Coffee"href="coffee.htm">
</map>
```

## Image Map shape Attribute
Shapes can be:
- `rect, coords="x1, y1, x2, y2"` where:
  - x1, x2 = number of pixels from left
  - y1, y2 = from top
- `circle, coords="x, y, r"` where:
  - x, y = coordinates of center
  - r = radius
- `poly (polygonal), coords="x1,y1, …"` where:
  - x1, y1 is repeated for all coordinates of the edges of the shape
- `default` (the entire region).

# Background Images
Use the background-image CSS property:
```html
<p style="background-image: url('img_girl.jpg');">
```

To set the background image for an entire page, specify it in the body element:
```html
<style>
  body {
    background-image: url('img_girl.jpg');
    background-repeat: no-repeat;
  }
</style>
```

If the image is smaller than the element, it will tile. Avoid this with background-repeat.

To cover an entire element, set:
```css
background-attachment: fixed;
background-size:cover;
```

To stretch, set:
```css
background-size: 100% 100%;
```

# picture Element
Use to display different images for differnet devices/screen sizes:
```html
<picture>
  <!-- uses this image when screen width >= 650px -->
  <source media="(min-width: 650px)" srcset="img_food.jpg">
  <source media="(min-width: 465px)" srcset="img_car.jpg">
  <img src="img_girl.jpg"> <!-- always make the img element last -->
</picture>
```

If you don't specify `media`, but specify two images with different filetypes via `srcset`, the browser will choose the most appropriate one for the device.
