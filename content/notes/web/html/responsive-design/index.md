---
title: "notes > web > html > responsive design"
date: 2023-04-26T20:48:26-0600
draft: true
---
# Overview
Responsive designs automatically adjust for different screen sizes and viewports:

To achieve responsive design:
- Always set the viewport in the meta tag

# Images
- Set the CSS width property to 100% to allow the image to scale up and down
- Set the CSS max-width property to 100% to allow the image to scale down, but never scale up
- Use the <picture> element to use different images for different browser window sizes.

# Text
- Set the CSS font-size property with a viewport value (the viewport is the browser window size):
`<h1 style="font-size:10vw">Hello World</h1> <!-- 10vw is 10% of the viewport size -->`

# Media Queries
Use media queries to change layouts based on browser sizes, like this one that changes from a horizontal stack to a vertical stack:
`<style>`
`.left, .right {`
`float: left;`
`width: 20%; /* The width is 20%, by default */`
`}`

`.main {`
`float: left;`
`width: 60%; /* The width is 60%, by default */`
`}`

`/* Use a media query to add a breakpoint at 800px: */`
`@media screen and (max-width: 800px) {`
`.left, .main, .right {`
`width: 100%; /* The width is 100%, when the viewport is 800px or smaller */`
`}`
`}`
`</style>`