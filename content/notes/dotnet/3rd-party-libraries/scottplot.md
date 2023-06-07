---
title: notes > dotnet > 3rd party libraries > scottplot.md
date: 2022-04-20T13:32:51-0600
draft: false
---
# [ScottPlot](https://scottplot.net/)

<https://scottplot.net/cookbook/4.1/>

Pros:
- Interactive (only in GUI?)
Cons:
- API designed after Matplotlib (instead of Plotly).

# QuickStart
```cs
double[] dataX = new double[] { 1, 2, 3, 4, 5 };
double[] dataY = new double[] { 1, 4, 9, 16, 25 };
var plt = new ScottPlot.Plot(400, 300);
plt.AddScatter(dataX, dataY);
plt.SaveFig("quickstart.png");
```
