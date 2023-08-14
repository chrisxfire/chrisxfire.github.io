---
title: canvas element
date: 2023-04-27T09:50:36-0600
draft: false
weight: 1
---
# Overview
The `<canvas>` element is a container for graphics drawn by JavaScript.
Syntax: 
```html
<canvas id="myCanvas" width="200" height="100"></canvas>
```
# Empty Canvas
```html
<canvas id="myCanvas"width="200"height="100"style="border:1px solid #000000;">
</canvas>
```
<img src="xHTML_Graphics---canvas--Element-image1.png" style="width:1.40833in;height:0.7in" />  

# Line
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
<img src="xHTML_Graphics---canvas--Element-image2.png" style="width:1.5in;height:0.81667in" />  

# Circle
```html
<script>
    var c = document.getElementById("myCanvas");
    var ctx = c.getContext("2d");
    ctx.beginPath();
    ctx.arc(95, 50, 40, 0, 2 * Math.PI);
    ctx.stroke();
</script>
```
<img src="xHTML_Graphics---canvas--Element-image3.png" style="width:1.46667in;height:0.75in" />  

# Text
```html
<script>
    var c = document.getElementById("myCanvas");
    var ctx = c.getContext("2d");
    ctx.font = "30px Arial";
    /* or strokeText: */
    ctx.fillText("Hello World", 10, 50);
</script>
```
<img src="xHTML_Graphics---canvas--Element-image4.png" style="width:1.5in;height:0.79167in" />  

# Gradient
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

<img src="xHTML_Graphics---canvas--Element-image5.png" style="width:1.50833in;height:0.775in" />


