---
title: canvas element
date: 2023-04-27T09:50:36-0600
draft: false
weight: 1
---

# overview
The `<canvas>` element is a container for graphics drawn by JavaScript.
Syntax: 
```html
<canvas id="myCanvas" width="200" height="100"></canvas>
```
# empty canvas
```html
<canvas id="myCanvas"width="200"height="100"style="border:1px solid #000000;">
</canvas>
```
![A screenshot of an empty canvas](./xHTML_Graphics---canvas--Element-image1.png)

# line
```html
<canvas id="myCanvas" width="200" height="100" style="border:1px solid #d3d3d3;">
Your browser does not support the HTML canvas tag.</canvas>

<script>
    var c = document.getElementById("myCanvas");
    var ctx = c.getContext("2d");
    ctx.moveTo(0,0);
    ctx.lineTo(200,100);
    ctx.stroke();
</script>
```
![A screenshot of a canvas with a single line from the upper left to the lower right](./xHTML_Graphics---canvas--Element-image2.png)

# circle
```html
<script>
    var c = document.getElementById("myCanvas");
    var ctx = c.getContext("2d");
    ctx.beginPath();
    ctx.arc(95, 50, 40, 0, 2 * Math.PI);
    ctx.stroke();
</script>
```
![A screenshot of a blank canvas with a dark circle in the middle of it](./xHTML_Graphics---canvas--Element-image3.png)

# text
```html
<script>
    var c = document.getElementById("myCanvas");
    var ctx = c.getContext("2d");
    ctx.font = "30px Arial";
    /* or strokeText: */
    ctx.fillText("Hello World", 10, 50);
</script>
```
![A screenshot of a canvas with text that reads 'Hello world'](./xHTML_Graphics---canvas--Element-image4.png)

# gradient
```html
<script>
    var c = document.getElementById("myCanvas");
    var ctx = c.getContext("2d");

    // Create gradient
    /* or createRadialGradient: */
    var grd = ctx.createLinearGradient(0, 0, 200, 0);
    grd.addColorStop(0, "red");
    grd.addColorStop(1, "white");

    // Fill with gradient
    ctx.fillStyle = grd;
    ctx.fillRect(10, 10, 150, 80);
</script>
```

![A screenshot of a canvas with a red square that grades from dark to light from left to right](./xHTML_Graphics---canvas--Element-image5.png)


