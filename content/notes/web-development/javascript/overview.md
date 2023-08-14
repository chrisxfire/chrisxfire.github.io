---
title: overview
date: 2023-04-28T16:26:09-0600
draft: false
weight: -1
---

# Embedding in HTML
JavaScript is embedded in HTML in `<script>` tags.

# Variables
```js
let someVariable = "someString"
const someConstant = 3
```

## Arrays
JavaScript arrays are zero-indexed:
```js
let array1 = [1, 2, 3, 4];
let array2 = [100, true, "JavaScript"];

array1[0] // returns 1

array1.push(5);
```

# Strings
Strings are C-style.

## Template strings
```js
day: ${day}, index: ${index};
```
# Operators
```js
===
```

# Flow Control
C-style:
```js
if
while
for
```

## ForEach
`forEach` works by defining an anonymous function that takes action on each element in the array:
```js
array1.forEach(function(day, index) {
    …
});

// or, with a lambda:
someArray.forEach(item => {
    …
});
```

# Type Conversions
Parse a string to integer: `parseInt`

# Functions
```js
function function-name(arg1, …) {
    …
}
```

# Object Literals
```js
let person = {
    firstName: "John",
    lastName: "Doe",
    greet: function() {
        console.log("My name is " + this.firstName);
    }
};
```
# Selecting HTML Elements
```js
// By ID:
document.getElementById("some-value");

// By class:
document.querySelector(".class-name");returns the first matching element
document.querySelectorAll(".class-name"); returns a NodeList of all matching elements

// By tag:
document.querySelector("tag-name[attribute-name='attribute-value']");
document.querySelector("#someId someAttribute");
```

# Getting / Setting / Removing Attributes
```js
let links = document.querySelectorAll(".classname");
links.forEach(function(link) {
    link.setAttribute("target", "_blank"); // set the "target" attribute to "_blank"
});
```

# Accessing an Element's class
"class" is a reserved word in JavaScript, so instead of…
```js
link.class
```

…use:
```js
link.classList
```

# Window Object
The window object hosts the DOM for the current tab.

## Adding an Event Listener to Window
Creates an event listener that listens for the DOMContentLoaded event and runs the lambda specified
in the segment argument when the event occurs:
```js
window.addEventListener('DOMContentLoaded', () => {
    …
}
```

## Events for Input Boxes
`'change'` when the value in an input box changes  
`'keyup'` when a key is pressed and released  
