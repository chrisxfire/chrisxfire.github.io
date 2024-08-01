---
title: draw.io
date: 2022-01-18T00:00:00-06:00
draft: false
weight: 1
---

# Canvas
| Action            | Keystrokes                                        |
| ----------------- | ------------------------------------------------- |
| Grid (toggle)     | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>G</kbd> |
| Move drawing area | <kbd>Space</kbd> + **drag mouse**                 |
| Zoom              | <kbd>Alt</kbd> + **scroll wheel**                 |

# Connectors
| Action                              | Keystrokes                                                               |
| ----------------------------------- | ------------------------------------------------------------------------ |
| Clone connectors                    | <kbd>Ctrl</kbd> + **Select** connector's endpoint + **Drag**             |
| Connect to a point within the shape | **Drag** > hold <kbd>Alt</kbd> > **Release mouse button** at destination |
| Add another Waypoint to connector   | **Right-click** connector > **Add Waypoint**                             |

## Connections
Floating connections connect to the frame of a shape.  This is the default when creating new connectors. 
When a shape with a floating connection is moved, the connection relocates and the line is kept simple.

Fixed connections connect to a specific point on a shape.

| Action                                   | Keystrokes                                                                                                                 |
| ---------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| Create floating connection               | Start a connection > **Drag** to *inside* of target shape                                                                  |
| Create fixed connection                  | Start a connection > **Drag** to <g>green</g> circle or <g>green</g> frame of target shape                                 |
| Change from floating to fixed connection | **Drag** connection away from shape a bit > Select it again > Drag until <g>green</g> circle or frame appears around shape |

# Layers
The default layer is "Background."  It is always visible. The order of layers affects some shape and connector effects:
* Line jumps only work for the layer on top.

## Layer Panel
When a shape is selected, the layer it is on is indicated by a black dot in the layer panel.

| Action                                       | Keystrokes                                               |
| -------------------------------------------- | -------------------------------------------------------- |
| Add a layer                                  | **View** > **Layers** > ➕                                |
| Duplicate layers                             | **View** > **Layers** > **Select** layer > **Duplicate** |
| Disable editing for all shapes on this layer | **View** > **Layers** > 🔒                                |
| Move shapes between layers                   | **Select** the shapes > ⋯ > **Move Selection**           |
| Show/hide all shapes on this layer           | **View** > **Layers** > 👁                                |

# Placeholders (predefined)
Add a property globally to the page:
1. Make sure nothing is selected
2. Diagram > **Edit Data**
3. Add the property > **Apply**
4. Select the shape that should use the property > **Edit** > **Edit Data** > check **Placeholders**
5. In the shape, type `%placeholder%`

Add a property to a specific shape:
1. **Right-click** shape > **Edit** > **Edit Data**
2. **ID**: `%placeholder%`
3. Check **Placeholders**
4. In the text field of the shape, enter `%placeholder%`

| Placeholder        | Description                                      |
| ------------------ | ------------------------------------------------ |
| %id%               | Prints the ID of a shape or connector.           |
| %date%             | Prints the current date using the system locale. |
| %time%             | Prints the current time using the system locale. |
| %timestamp%        | Prints a timestamp using the system locale.      |
| %date{yyyy-mm-dd}% | Prints a timestamp using a custom format.        |
| %pagenumber%       | Prints the page number of the current page.      |
| %pagecount%        | Prints the total number of pages.                |
| %page%             | Prints the title of the current page.            |
| %filename%         | Prints the name of the file.                     |

# Selecting
| Action                                                                 | Keystrokes                                                          |
| ---------------------------------------------------------------------- | ------------------------------------------------------------------- |
| Select all connectors                                                  | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>E</kbd>                   |
| Select all shapes                                                      | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>I</kbd>                   |
| Select next/previous shape                                             | <kbd>Tab</kbd> or <kbd>Shift</kbd> + <kbd>Tab</kbd>                 |
| Select parent Shape                                                    | <kbd>Shift</kbd> + <kbd>Alt</kbd> + <kbd>P</kbd>                    |
| Select shape/connector underneath                                      | Hold <kbd>Alt</kbd> + **Click** on shape to select next lower shape |
| Select all intersecting shapes (not juse those fully in selection box) | <kbd>Alt</kbd> + **Drag**                                           |

# Shapes
| Action                                         | Keystrokes                                                                         |
| ---------------------------------------------- | ---------------------------------------------------------------------------------- |
| Aligning                                       | **Select** multiple shapes > Format panel > **Arrange** > **Align**                |
| Clone shape with connectors                    | **Select** shape > <kbd>Alt</kbd> + <kbd>Shift</kbd> + <kbd>Arrow</kbd>            |
| Change shape after cloning                     | Release <kbd>Alt</kbd> > **Click** new shape                                       |
| Copy style of one shape to another             | **Style** tab > **Copy Style** and **Paste Style**                                 |
| Flip shapes                                    | **Select** shape > Format panel >> **Arrange** tab > **Flip**                      |
| Group Shapes                                   | <kbd>Ctrl</kbd> + <kbd>G</kbd>                                                     |
| Ungroup Shapes                                 | <kbd>Ctrl</kbd> + <kbd>Shift</kbd> + <kbd>U</kbd>                                  |
| Replace shape                                  | **Drag** new shape over existing until the blue/black conversion symbol is shown   |
| Replace multiple shapes                        | **Select** all shapes to be replaced > **Drag** new shape over *one* of the shapes |
| Insert a new connected shape                   | **Hover** over the shape > **Click** blue arrow > **Select** new shape             |
| Delete a shape and the connected leading to it | <kbd>Ctrl</kbd> + <kbd>Backspace</kbd>                                             |
| Add a hyperlink to a Shape > **Right-click**   | **Edit Link** > **Web Link**                                                       |

# Swimlane Diagrams
| Action                              | Keystrokes                                                                                       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------ |
| Add a swimlane                      | **Hover** over the last lane > **Click** the blue arrow                                          |
| Move a swimlane to another position | **Drag** the swimlane slightly to the right > Hold <kbd>Alt</kbd> > **Drag** to desired location |
| Select the entire pool              | **Click** a lane > **Click** again                                                               |
