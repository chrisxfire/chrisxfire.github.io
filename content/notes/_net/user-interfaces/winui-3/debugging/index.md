---
title: debugging
date: 2023-01-01T17:22:55-0700
draft: false
weight: 1
---

# Live Visual Tree
**Debug** > **Windows** > **Live Visual Tree**

Toggle between showing all WinUI XAML or just XAML you have written:  
![](./Debugging-image1.png)

Show all elements in the MainWindow:  
![](./Debugging-image2.png)

The numbers indicate how many children (direct and indirect) each element contains:  
![](./Debugging-image3.png)

Click to enable a toolbar that floats over the app UI:  
![](./Debugging-image4.png)

Select Element—select an element in UI and it will be selected in Live Visual Tree:  
![](./Debugging-image5.png)

Click brackets to navigate to this element:  
![](./Debugging-image6.png)

# Inspecting Properties at Runtime with Live Property Explorer
![](./Debugging-image7.png)

![](./Debugging-image8.png)

Live Property Explorer always shows the properties of the element selected in the Live Visual Tree:  
![](./Debugging-image9.png)

![](./Debugging-image10.png)

This Padding property is crossed out because it is set by a more specific Style.  

Changes made to values in Live Property Explorer do not persist.  
