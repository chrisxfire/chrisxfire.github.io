---
title: notes > web development > bootstrap > components > modal
date: 2023-06-22T00:00:00-06:00
draft: true
weight: 1
---

# Overview
- A JavaScript modal plugin to add dialogs for lightboxes, notifications, or custom content
- Built with HTML, CSS and JavaScript
- Documentation: https://getbootstrap.com/docs/5.3/components/modal/

# Details
- Positioned over everything else in the document and remove scroll from the `<body>` (the modal scrolls instead)
- Clicking on the modal's backdrop closes it
- Only one modal window at a time is supported
- Uses `position: fixed`; whenever possible, place the modal HTML in a  top-level position
  - Nesting a `.modal` in another element is often problematic
- The HTML `autofocus` attribute has no effect in modals
- The animation in modals is dependent on `prefers-reduced-motion` media query
