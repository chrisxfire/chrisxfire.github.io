---
title: notes > .net > winui 3 > debugging
date: 2023-01-01T17:22:55-0700
draft: false
---
# Live Visual Tree
**Debug** > **Windows** > **Live Visual Tree**

Toggle between showing all WinUI XAML or just XAML you have written:  
<img src="Debugging-image1.png" style="width:2.14167in;height:0.8in" />    

Show all elements in the MainWindow:  
<img src="Debugging-image2.png" style="width:3.04167in;height:1.28333in" />    

The numbers indicate how many children (direct and indirect) each element contains:  
<img src="Debugging-image3.png" style="width:3.775in;height:1.36667in" />    

Click to enable a toolbar that floats over the app UI:  
<img src="Debugging-image4.png" style="width:3.74167in;height:0.94167in" />  

Select Element—select an element in UI and it will be selected in Live Visual Tree:  
<img src="Debugging-image5.png" style="width:3.125in;height:0.99167in" />  

Click brackets to navigate to this element:  
<img src="Debugging-image6.png" style="width:3.81667in;height:0.825in" />  

# Inspecting Properties at Runtime with Live Property Explorer
<img src="Debugging-image7.png" style="width:3.83333in;height:1.66667in" />  

<img src="Debugging-image8.png" style="width:3.96667in;height:4.99167in" />  

Live Property Explorer always shows the properties of the element selected in the Live Visual Tree:  
<img src="Debugging-image9.png" style="width:6.99167in;height:2.78333in" />   

<img src="Debugging-image10.png" style="width:4.36667in;height:5.7in" />   

This Padding property is crossed out because it is set by a more specific Style.  

Changes made to values in Live Property Explorer do not persist.  