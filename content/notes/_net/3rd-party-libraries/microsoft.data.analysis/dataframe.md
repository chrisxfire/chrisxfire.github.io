---
title: dataframe
date: 2022-01-25T13:17:51-0700
draft: false
weight: 1
---

# [DataFrame](https://docs.microsoft.com/en-us/dotnet/api/microsoft.data.analysis.dataframe?view=ml-dotnet-preview)
`Object` –> `DataFrame`   

A data structure to support indexing, binary operations, sorting, selecting, and other APIs.
```powershell
dotnet add package Microsoft.Data.Analysis
```

# accessing 
## elements
```cs
// Access the element at row, col:
df[row, col]
// or
df.Rows[row, col]
```

## rows
```cs
// Access the nth row:
df.Rows[n]
```

## columns
```cs
// Access a column by name:
df["column_name"]

// Access the nth column:
df.Columns[n]
```

## dataframe
```cs
// Filter the DataFrame:
df.Filter(df.Columns["column"].ElementwiseGreaterThan(50)) // All rows in column with values > 50.
```

# manipulating
## elements
```cs
df[row, col] = value;
```

## rows
```cs
// Add a row:
df.Append(new List<KeyValuePair<string, object>>() 
{
    new KeyValuePair<string, object>("foo_column", value),
    new KeyValuePair<string, object>("bar_column", value),
    new KeyValuePair<string, object>("baz_column", value)
}, true);
```

## columns
```cs
// Manipulate all rows of a column:
df.Columns["column_name"] = df.Columns["column_name"] + value;

// Add a column:
df.Columns.Add(new DataFrameColumn("column_name", numberOfRows);
// In place of `numberOfRows`, consider `df.Rows.Count()`

// Fill the nulls in a column with a value:
df.Columns["column_name"].FillNulls(value, true);
```

## dataframe
### sorting
```cs
// Sort (order) by ascending:
df.OrderBy("column");

// Sort (order) by descending:
df.OrderByDescending("column");
```
### grouping
```cs
// Group dataframe rows by unique value in columns:
var groupByData = df.GroupBy("column");
```

### merging
```cs
// Merge df2 into df1 using a column of Type named df1_column_name in df1 and df2_column_name in df2:
df1.Merge<Type>(df2, "df1_column_name", "df2_column_name");

// Merge df2 with df1 on the common column named "Date" of type DateTime:
df1.Merge<DateTime>(df2, "Date", "Date");
```

# properties
- `Columns` - Returns the columns in the DataFrame as a DataFrameColumnCollection.
- `Item(rowIndex, colIndex)` - An indexer to get or set values.
- `Item(someString)` - An indexer based on Name.
- `Rows` - Returns the rows in the DataFrame as a DataFrameRowCollection.

# methods
- `AddPrefix`
- `AddSuffix`
- `Append`
- `Clamp`
- `Clone` - Return a full copy of the DataFrame.
- `Divide`
- `DropNulls(DropNullOptions)` - Return a DataFrame with no missing values.
- `FillNulls`
- `Filter`
- `GroupBy` - Group the rows in the DataFrame by unique values.
- `Head(n)` - Return the first n rows of the DataFrame.
- `Info()` - Generate a concise summary of each column in the DataFrame.
- `Join`
- `LoadCsv` - Read a CSV into a DataFrame.
- `Merge` - Merge DataFrames with a database style join.
- `Modulo`
- `OrderBy` - Orders the DataFrame by a specified column.
- `Tail(n)` - Return the last n rows of the DataFrame.
- `WriteCsv` - Write a DataFrame to a CSV.

## comparison methods
- `ElementwiseEquals`
- `ElementwiseGreaterThan`
- `ElementwiseGreaterThanOrEqual`
- `ElementwiseLessThan`
- `ElementwiseLessThanOrEqual`
- `ElementwiseNotEquals`

## mathematical methods
- `Add`
- `And`
- `Divide`
- `Modulo`
- `Multiply`
- `Or`
- `Subtract`
- `Xor`
- `ReverseAdd`
- `ReverseAnd`
- `ReverseDivide`
- `ReverseModulo`
- `ReverseMultiply`
- `ReverseSubtract`
- `ReverseXor`

## statistical methods
- `Description()` - Generate descriptive statcs that summarize each numeric column.
- `Sample(n)` - Return a random sample of n rows.
