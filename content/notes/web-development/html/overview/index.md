---
title: overview
date: 2023-04-26T00:00:00-07:00
draft: false
weight: -1
---

# Introduction
```html
<!DOCTYPE html> <!--defines this HTML 5 document-->
<html lang="en-US"> <!--the root element-->
	<head> <!-- metadata about the page -->
		<title>Page Title</title>
	</head>
	<body> <!-- a container for all visible contents -->

		<h1>My First Heading</h1>
		<p>My first paragraph.</p>

	</body>
</html>
```

# Elements
HTML elements have opening tags, content, and closing tags:
```html
<title>Page title</title>
```

## Empty elements
Empty elements like `<br>` (line break) have no content nor closing tag.

# Attributes
Attribute names should be lowercase.
Attribute values should be quoted.
- Use double quotes unless the value itself contains double quotes.

Style attribute to add styles to an element:  
```html
<p style="color:red;">This is a red paragraph.</p>
```
Title attributes to provide a tooltip when you mouse-over the element:  
```html
<p title="I'm a tooltip">This is a paragraph.</p>
```

# `style` Attribute
The style attribute uses CSS properties and values:
```html
<tagname style="property:value;">
```

## Style properties
```
background-color
color (text color)
font-family
font-size (either as a % or fixed value)
text-align
border:2px solid color
```

# Colors
Colors can be specified with names, RGB, hexadecimal, HSL, RGBA, or HSLA values:
- RGB as `RGB(n, n, n)` and `RGBA(n, n, n, n)` where `n` is 0-255
- Hexadecimal as `#rrggbb`
- HSL as `HSL(hue, saturation, lightness)`
	- `hue` = 0 to 360 on the color wheel
	- `saturation` = 0% as a shade of grey to 100% full color
	- `lightness` = 0% as black to 100% white

# Favicons
Link to the favicon in the head section:
```html
<link rel="icon" type="image/x-icon" href="/images/favicon.ico">
```

Supported formats for all major browsers:  ICO, PNG, GIF, JPG, SVG

# IFrames
Inline frames; embeds one HTML document within another.
Syntax:  
```html
<iframe name="someName" src="url" title="description"></iframe> <!-- good practice to always include a title element -->
```

IFrames have borders by default.  Remove via `style="border:none";`

Links can target IFrames via their name attribute:
```html
<iframe src="demo_iframe.htm" name="iframe_a" title="Iframe Example"></iframe>
	
<p><a href="https://www.w3schools.com" target="iframe_a">W3Schools.com</a></p>
```

# `<script>` Tag
Client-side JavaScript is defined in script elements:
```html
<script>
    document.getElementById("demo").innerHTML = "Hello JavaScript!";
</script>
```

To reference a script in an external file:
```html
<script src="filename.js" type="text/javascript"></script>
```

This element should be the last element before `</body>`.
	
# `<noscript>` Tag
Defines alternate content to be displayed to browsers that do not support JavaScript:
```html
<script>
	document.getElementById("demo").innerHTML = "Hello JavaScript!";
</script>
<noscript>Sorry, your browser does not support JavaScript!</noscript>
```

# Layout
`<header>` - Defines a header for a document or a section  
`<nav>` - Defines a set of navigation links  
`<section>` - Defines a section in a document  
`<article>` - Defines an independent, self-contained content  
`<aside>` - Defines content aside from the content (like a sidebar)  
`<footer>` - Defines a footer for a document or a section  
`<details>` - Defines additional details that the user can open and close on demand  
`<summary>` - Defines a heading for the `<details>` element  

## Layout Techniques
There are four techniques:
- CSS Framworks (W3.CSS, Bootstrap)
- CSS Float Layout
- CSS Flexbox Layout
- CSS Grid Layout

# Entities
Character entities are used to display characters that are reserved in HTML.
Syntax:  `&entity_name` or `&#entity_number`
Example:  a less than sign < is represented as `&lt;` or `&#60;`

## Common Entities
`&nbsp;` — non-breaking space; force two words to stick together and not break across a newline:  `10&nbsp;mph`  
`&#8209;` — non-breaking hyphen  
`&gt;`  
`&lt;`  
`&amp;` — ampersand  
`&quot;` — double quote  
`&apos;` — apostrophe  
`&cent;` — cent sign  
`&pound;` — british pound  
`&copy;` — copyright  
`&reg;` — registered trademark  

Entities can also represent emojis.
