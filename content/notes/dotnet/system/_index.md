---
title: "notes > dotnet > system"
date: 2021-11-11T20:19:33-0700
draft: true
---
# [DateTimeOffset](https://docs.microsoft.com/en-us/dotnet/api/system.datetimeoffset?view=net-6.0)
Object –> ValueType –> DateTimeOffset
Represents a date and time with an offset against UTC.
Includes all functionality from DateTime as well as (some) time zone awareness.
Consider this the default date and time type.

See also: <https://docs.microsoft.com/en-us/dotnet/standard/base-types/standard-date-and-time-format-strings>

See also: [System.TimeSpan](onenote:#System.TimeSpan&section-id={7CEF68E6-44B3-4DC6-BEC7-E9AABAE7A0B2}&page-id={4C3679DC-E67C-47C3-8B6F-C8278555E9A7}&end&base-path=https://d.docs.live.net/1489beaac91cb6b6/Documents/Notebooks/Code/DotNet%20Libraries.one)

# Notes
- The time component is measured in ticks.
- DateTimeOffset values can be created by assigning it a DateTime value (implicit conversion).

# Uses
- "Now"
- Date and time arithmetic.
- Date and time conversion.
- Date and time comparison.
- Conversion: DateTimeOffset <–> DateTime.
- Time manipulation and extraction.

# Construction
DateTimeOffset(*DateTime*, *TimeSpan*)*TimeSpan* is optional.
DateTimeOffset(*yyyy, mm, dd, hh, mm, ss, ms, TimeSpan*)*ms* is optional.
DateTimeOffset(*ticks*, *TimeSpan*)

# Casting & Conversions
<https://docs.microsoft.com/en-us/dotnet/standard/datetime/converting-between-datetime-and-offset>
DateTime dt;
DateTimeOffset dto;

## DateTime –> DateTimeOffset
dto = DateTimeOffset(*dt*)

## DateTime <– DateTimeOffset
dt = dto.DateTime// Information about the dto's relationship to UTC is lost.
dt = dto.UtcDateTime// Use this if the dto is in UTC.
dt = dto.LocalDateTime// Use this if the dto is in local time.

# Fields
UnixEpoch00:00:00.0000000 UTC, January 1, 1970

# Methods
## <u>Manipulating</u>
.Add(*timespan*)
.AddYears(*int*)
.AddMonths(*int*)
.AddDays(*double*)
.AddHours(*double*)
.AddMinutes(*double*)
.AddSeconds(*double*)
.AddMilliseconds(*double*)
.AddTicks(*int64*)
.Subtract(*datetimeoffset*)
.Subtract(*timespan*)

## <u>Comparing</u>
DateTimeOffset.Compare(*datetimeoffset1*, *datetimeoffset2*)
.CompareTo(*datetimeoffset*)
.Equals(*datetimeoffset*)Boolean if two datetimeoffsets have the same time.
DateTimeOffset.Equals(*datetimeoffset1*, *datetimeoffset2*)
.EqualsExact(*datetimeoffset*)Boolean if two datetimeoffsets have the same time and offset.

## <u>Converting</u>
.FromFileTime(*int64*)Convert Windows file time to equivalent local time.
.FromUnixTimeSeconds(*int64*)Convert a time expressed as seconds since UNIX epoch to a DateTimeOffset.
.FromunixTimeMilliseconds(*int64*)
.ToFileTime()
.ToLocalTime()
.ToOffset(*timespan*)
.ToString
.ToUnixTimeSeconds()
.ToUnixTimeMilliseconds()

## <u>Parsing</u>
.Parse
.ParseExact
.TryParse

# Operators
DateTimeOffset + TimeSpan
DateTimeOffset - DateTimeOffset
DateTimeOffset - TimeSpan

DateTimeOffset > DateTimeOffset (also <=, ==, !=, <, <=)

# Properties
.Date
.DateTimeRepresent a DateTimeOffset object as a DateTime.
.LocalDateTime
.Now
.OffsetOffset from UTC.
.UtcDateTime
.UtcNow
.UtcTicks

.Year
.Month
.DayDay of month
.DayOfWeek
.DayOfYear
.Hour
.Minute
.Second
.Millisecond
.Ticks
.TimeOfDay