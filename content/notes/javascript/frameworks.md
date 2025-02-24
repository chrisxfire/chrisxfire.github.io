---
title: frameworks
date: 2025-02-23T00:00:00-06:00
draft: true
weight: 1
tags:
 - javascript
---

# overview
## [Node](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-overview)
- An open source, cross-platform, server-side JavaScript runtime environment built for Chrome's V8 JavaScript engine.
- Uses event-driven, non-blocking I/O model.
- Great for data-intensive real-time applications that run across distributed devices.

## [React](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/react-overview)
- An open source JavaScript library for building front end user interfaces.
- Creates application views through encapsulated units called *components* that maintain state and generate UI elements.

React components are written in JavaScript and JSX. JSX is a JavaScript XML extension that looks like HTML but has syntax features that make common tasks easier. React components have a `render` method which returns the JSX representing the component's UI. In a web app, the returned JSX is translated into HTML rendered in the browser.

## [Vue](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/vue-overview)
- An open source front end JavaScript framework for building user interfaces and SPAs.
- Uses a model-view-viewmodel architecture. Focused only on the view layer.

## [Next.js](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nextjs-on-wsl)
- A JavaScript framework for building SSR JavaScript apps based on React, Node, Webpack, and Babel.
- Supports both static and SSR rendering.
- Enables creation of "universal", isomorphic (code shared between client and server) web apps in a consistent manner with minimal configuration.

# comparison
| System  | Type      | Source model | Platforms      | Model     | SPAs | RTAs | APIs | SSR | CLI | Desktop | Mobile |
|---------|-----------|--------------|----------------|-----------|------|------|------|-----|-----|---------|--------|
| Node.js | Framework | Open         | Cross-platform | Back end  | Yes  | Yes  | Yes  | Yes | Yes | No      | No     |
| ReactJS | Library   | Open         | Cross-platform | Front end | Yes  | No   | No   | No  | No  | Yes     | Yes    |
| Vue.js  | Framework | Open         | Cross-platform | Front end | Yes  | No   | No   | No  | No  | No      | No     |
| Next.js | Framework | ?            | Cross-platform | Back end  | Yes  | No   | No   | Yes | No  | No      | No     |