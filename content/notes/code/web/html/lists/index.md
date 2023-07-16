---
title: notes > code > web > html > lists
date: 2023-04-26T17:34:30-0600
draft: false
---
# Lists
Unordered:
```html
<ul style="list-style-type:disc;"> <!-- style for list item markers; also circle, square, none -->
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ul>
```

Ordered:
```html
<!-- style for list item markers; also A, a, I, i -->
<!-- start: where to start the count -->
<ol type="1" start="50">
    <li>Coffee</li>
    <li>Tea</li>
    <li>Milk</li>
</ol>
```

# Horizontal Lists
Use CSS to make a horizontal list, like a navigation menu:
```html
<!DOCTYPE html>
<html>
<head>
<style>
ul {
    list-style-type: none;
    margin: 0;
    padding: 0;
    overflow: hidden;
    background-color: #333333;
}

li {
    float: left;
}

li a {
    display: block;
    color: white;
    text-align: center;
    padding: 16px;
    text-decoration: none;
}

li a:hover {
    background-color: #111111;
}
</style>
</head>
<body>

<ul>
    <li><a href="#home">Home</a></li>
    <li><a href="#news">News</a></li>
    <li><a href="#contact">Contact</a></li>
    <li><a href="#about">About</a></li>
</ul>

</body>
</html>
```

# Description Lists
A list of terms with descriptions of each:
```html
<dl>
    <dt>Coffee</dt> <!-- description term -->
    <dd>- black hot drink</dd> <!-- description definition -->
    <dt>Milk</dt>
    <dd>- white cold drink</dd>
</dl>
```
