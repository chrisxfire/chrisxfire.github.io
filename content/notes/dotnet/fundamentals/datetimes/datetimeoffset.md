---
title: datetimeoffset
date: 2021-11-11T20:08:41-0700
draft: false
weight: 1
---

# [DateTimeOffset](https://docs.microsoft.com/en-us/dotnet/api/system.datetimeoffset?view=net-6.0)
`Object` –> `ValueType` –> `DateTimeOffset`  
Represents a date and time with an offset against UTC.  
Includes all functionality from DateTime as well as (some) time zone awareness.  
Consider this the default date and time type.  

See also: <https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings>  

# Notes
- The time component is measured in ticks
- DateTimeOffset values can be created by assigning it a DateTime value (implicit conversion)

# Uses
- "Now"
- Date and time arithmetic, conversion, and comparisons
- Conversion: `DateTimeOffset` <–> `DateTime`
- Time manipulation and extraction

# Construction
```cs
DateTimeOffset(DateTime, TimeSpan) // TimeSpan is optional.
DateTimeOffset(yyyy, mm, dd, hh, mm, ss, ms, TimeSpan) // ms is optional.
DateTimeOffset(ticks, TimeSpan)
```

# Casting & Conversions
<https://docs.microsoft.com/en-us/dotnet/standard/datetime/converting-between-datetime-and-offset>  
```cs
DateTime dt;  
DateTimeOffset dto;  
```

## `DateTime` –> `DateTimeOffset`
```cs
dto = DateTimeOffset(dt)
```

## `DateTime` <– `DateTimeOffset`
```cs
dt = dto.DateTime // Information about the dto's relationship to UTC is lost.
dt = dto.UtcDateTime // Use this if the dto is in UTC.
dt = dto.LocalDateTime // Use this if the dto is in local time.
```

# Fields
`UnixEpoch` // 00:00:00.0000000 UTC, January 1, 1970
