---
title: notes > .net > 3rd party libraries > plotly.net
date: 2022-04-20T10:07:37-0600
draft: false
---
# [Plotly.NET](https://plotly.net/)

<https://plotly.com/csharp/creating-and-updating-figures/>  

Pros:
- Uses `Plotly.JS`

Cons:
- Documentation is mostly in F#.
- Poor IntelliSense.

# Getting Started
```powershell
dotnet add package plotly.net
```

```cs
using Plotly.NET;
using Microsoft.FSharp.Core; // less verbose and more helpful intellisense(?)
```

# Basics
General design philosophy:
1.  Initialize a generic chart
2.  Style the chart
3.  Display or save the chart

## Initialize a Chart
A chart consists of:
- data: a collection of traces, which represent the data and chart type.
- layout: controls the axis positions and styles.
- config: high-level properties like making all chart elements editable.

```cs
double[] x = new double[] { 1, 2 };
double[] y = new double[] { 5, 10 };
GenericChart.GenericChart chart = Chart2D.Chart.Point<double, double, string>(x: x, y: y);
// or
GenericChart.GenericChart chart = Chart.Line(…)
```
## Styling a Chart
```cs
chart
    .WithTraceName("*Chart name*", true)
    .WithXAxisStyle("title: Title.init("*xAxis*"), ShowGrid: false, ShowLine: true)
    .WithYAxisStyle("title: Title.init("*yAxis*"), ShowGrid: false, ShowLine: true)
    .Show();
```

## Displaying a Chart
```cs
chart.Show();
```

# Image Export
```powershell
dotnet add package plotly.net.imageexport
```
```cs
using Plotly.Net.ImageExport;
using Plotly.Net.GenericChartExtensions;

chart.SaveJPG // | SavePNG | SaveSVG (*"path*", width=*n*, height=*m*);
```

# Marker Symbols
Marker symbols used in charts:
```cs
StyleParam.MarkerSymbol.Square
```
