---
title: debugging
date: 2023-01-01T17:22:55-0700
draft: false
weight: 1
---
# Live Visual Tree
**Debug** > **Windows** > **Live Visual Tree**

Toggle between showing all WinUI XAML or just XAML you have written:  
<img alt="A screenshot depicting the above." src="Debugging-image1.png" width="25%" height="25%" />    

Show all elements in the MainWindow:  
<img alt="A screenshot depicting the above." src="Debugging-image2.png" width="25%" height="25%" />    

The numbers indicate how many children (direct and indirect) each element contains:  
<img alt="A screenshot depicting the above." src="Debugging-image3.png" width="25%" height="25%" />    

Click to enable a toolbar that floats over the app UI:  
<img alt="A screenshot depicting the above." src="Debugging-image4.png" width="25%" height="25%" />  

Select Element—select an element in UI and it will be selected in Live Visual Tree:  
<img alt="A screenshot depicting the above." src="Debugging-image5.png" width="25%" height="25%" />  

Click brackets to navigate to this element:  
<img alt="A screenshot depicting the above." src="Debugging-image6.png" width="25%" height="25%" />  

# Inspecting Properties at Runtime with Live Property Explorer
<img alt="A screenshot depicting the above." src="Debugging-image7.png" width="25%" height="25%" />  

<img alt="A screenshot depicting the above." src="Debugging-image8.png" width="25%" height="25%" />  

Live Property Explorer always shows the properties of the element selected in the Live Visual Tree:  
<img alt="A screenshot depicting the above." src="Debugging-image9.png" width="25%" height="25%" />   

<img alt="A screenshot depicting the above." src="Debugging-image10.png" width="25%" height="25%" />   

This Padding property is crossed out because it is set by a more specific Style.  

Changes made to values in Live Property Explorer do not persist.  
