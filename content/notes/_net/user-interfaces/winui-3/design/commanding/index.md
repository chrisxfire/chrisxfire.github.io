---
title: notes > .net > user interfaces > winui 3 > design > commanding
date: 2023-01-02T17:19:09-0700
draft: false
weight: 1
---
# Overview
*Command elements* are interactive UI elements that let users perform actions (send an email, delete an item, submit a form). *Command interfaces* are composed of common command elements, the command surfaces that host them, the interactions they support, and the experience they provide.

## Command elements
- Buttons—trigger an immediate action
- Lists—present items in an interactive list or grid (drop-down list, list box, list view, grid view)
- Selection controls—select from a few options (CheckBox, RadioButton, toggle switch)
- Calendar, date and time pickers—view/modify date and time info (calendar date picker, calendar view, date picker, time picker)
- Predictive text entry—Provide suggestions as users type (AutoSuggestBox)

## Command surfaces
- App canvas (content area)  
<img src="DESIGN_Commanding-image1.png" style="width:1.7in;height:1.675in" />
- Command bars and menu bars  
<img src="DESIGN_Commanding-image2.png" style="width:1.80833in;height:1.03333in" />
- Menus and context menus—CommandBarFlyout  
<img src="DESIGN_Commanding-image3.png" style="width:1.58333in;height:0.95833in" />

# Providing Command Feedback
- Command bar  
<img src="DESIGN_Commanding-image4.png" style="width:1.8in;height:1.03333in" />
- Flyouts—lightweight contextual popups  
<img src="DESIGN_Commanding-image5.png" style="width:1.40833in;height:0.625in" />
- Dialog controls—usually must be explictly dismissed  
<img src="DESIGN_Commanding-image6.png" style="width:1.375in;height:0.88333in" />



