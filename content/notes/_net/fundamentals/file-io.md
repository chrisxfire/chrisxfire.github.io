---
title: file io
date: 2021-11-10T00:00:00-06:00
draft: true
weight: 1
---

# Convenience vs. Control
These APIs are listed from low level (most control) to high level (most convenient)

## Reading a Text File
1. `File.OpenHandle` + `RandomAccess.Read`
2. `File.Open` + `FileStream.Read`
3. `File.OpenText` + `StreamReader.ReadLine`
4. `File.ReadLines` + `IEnumerable<string>`
5. `File.ReadAllLines` + `string[]`
6. `File.ReadAllText` + `string`

## Reading JSON Text
1. `Utf8JsonReader` + `Pipelines` or `Stream`
2. `JsonDocument` + `Stream`
3. `JsonSerializer` + `Stream`
4. `JsonSerializer` + `string`