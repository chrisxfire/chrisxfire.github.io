---
title: navigation
date: 2023-01-02T17:27:02-0700
draft: false
weight: 1
---
# Overview
An app is a collection of *pages*. *Navigation* is the act of moving between pages and within a page.

<img alt="A diagram depicting navigation." src="DESIGN_Navigation-image1.png" style="width:6.00833in;height:1.69167in" />

# Navigation Structures
## Flat/Lateral
- Pages exist side by side
- Able to navigate from one page to another in any order  

<img alt="A diagram depicting flat/horizontal structures." src="DESIGN_Navigation-image3.png" style="width:1.95in;height:0.675in" />  

## Hierarchical
- Each child page has one parent, but a parent can have
more than one child.
- To reach a child page, you must navigate through parent.  

<img alt="A diagram depicting a hierarchical structure." src="DESIGN_Navigation-image2.png" style="width:1.94167in;height:1.09167in" />  

# Navigation Controls
## Frame
- Any app with multiple pages uses a Frame
- The app's main page contains a Frame and a primary navigation
element like a navigation view control.  

<img alt="A diagram depicting a frame." src="DESIGN_Navigation-image4.png" style="width:1.56667in;height:0.85833in" />  

## Top Navigation (NavigationView)
- A horizontal list of links to pages on the same level
- Use when
  - you want to show all navigation options on the screen
  - you need more space for app's content
  - icons cannot describe your navigation categories

## Tabs (TabView)
- A horizontal set of tabs and their respective content
- Use when
  - you want users to be able to open, close, or rearrange tabs
  - you expect there might be a large number of tabs open at once
  - your users need to easily move tabs between windows  

<img alt="A diagram depicting a TabView." src="DESIGN_Navigation-image5.png" style="width:1.50833in;height:0.88333in" />  

## Breadcrumb (BreadcrumbBar)
- A horizontal list of links to pages at each of the higher levels
- Use when
  - you want to show the path to the current location
  - you have many levels of navigation

## Left navigation
- A vertical list of links to top-level pages
- Use when
  - the pages exist at the top level
  - there are 5+ navigation items
  - users don't switch between pages frequently  

<img alt="A diagram depicting left navigation." src="DESIGN_Navigation-image6.png" style="width:1.53333in;height:0.88333in" />  

## List/details
- Displays a list of items
- Use when
  - users need to switch between child items frequently  

<img alt="A diagram depicting a list." src="DESIGN_Navigation-image7.png" style="width:1.525in;height:0.90833in" />  
