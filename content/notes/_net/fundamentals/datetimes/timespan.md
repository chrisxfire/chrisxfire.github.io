---
title: timespan
date: 2021-11-11T20:40:42-0700
draft: false
weight: 1
---

# [TimeSpan](https://docs.microsoft.com/en-us/dotnet/api/system.timespan?view=net-6.0)
`Object` –> `ValueType` –> `TimeSpan`  

Represents a time interval.  
Subtracting one `DateTime` from another results in a `TimeSpan`.  

# Uses
- Reflecting interval between two dates or times.
- Measuring elapsed time

# Construction
```cs
TimeSpan interval = new TimeSpan(); // interval is TimeSpan.Zero.
TimeSpan interval = TimeSpan.Zero;
TimeSpan(hh, mm, ss);
TimeSpan(dd, hh, mm, ss, ms); // ms is optional.
TimeSpan(ticks);
TimeSpan interval = datetime1, datetime2;
```
