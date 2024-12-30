---
title: datetime
date: 2021-11-11T20:08:41-0700
draft: false
weight: 1
---

# [DateTime](https://docs.microsoft.com/en-us/dotnet/api/system.datetime?view=net-6.0)
`Object` –> `ValueType` –> `DateTime`  
Represents an instant in time.  

Note: Time values are measured in 100-nanosecond units called ticks.  
Note: `System.DateOnly` is useful if working with dates only. This type maps to date columns in SQL server.  
Note: `System.TimeOnly` is useful if working with times only. This type maps to time columns in SQL server.  

Also: <https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings>

# uses
- Work with dates only or times only
- Work with dates and times for which timezone information is missing
- Work with UTC dates and times only
- Retrieve date/time information from sources outside of .NET

# construction
```cs
DateTime(yyyy, mm, dd, hh, mm, ss) // hh, mm, ss are optional.
DateTime(yyyy, mm, dd, hh, mm, ss, ms) // ms is optional.
DateTime(ticks) // where ticks is an Int64.
```

# properties
Note: Properties contained within DateTimeOffset are not listed here.

```cs
.Kind // A value that specifies if this DateTime is based on local time, UTC, or neither.
```

# methods
Note: Methods contained within DateTimeOffset are not listed here.

## information
```cs
DateTime.DaysInMonth(mm, yyyy)
DateTime.IsLeapYear(year)

.GetDateTimeFormats()
.IsDaylightSavingsTime() // Boolean if this instance is within the daylight savings time range for the current timezone.
```

## converting
```cs
DateTime.FromBinary(int64)Convert a 64-bit binary value to DateTime.
DateTime.SpecifyKind(DateTime, DateTimeKind)

.ToLongDateString()
.ToLongTimeString()
.ToShortDateString()
.ToShortTimeString()
.ToString()
.ToUniversalTime()
```

## parsing
```cs
.Parse(string) // Parse string into a DateTime object.
.TryParse(string, out DateTime result) // Try to parse string into DateTime result.
```

## adding and subtracting
```cs
.Add()
.AddDays()
.AddHours()
.AddMilliseconds()
.AddMinutes()
.AddMonths()
.AddTicks()
.AddYears()
```

Note: add negative numbers to subtract.

# format specifiers
<https://docs.microsoft.com/en-us/dotnet/api/system.datetime.tostring?view=net-6.0>

