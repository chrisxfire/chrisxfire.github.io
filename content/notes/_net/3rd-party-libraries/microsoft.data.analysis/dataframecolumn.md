---
title: dataframecolumn
date: 2022-01-25T13:39:48-0700
draft: false
weight: 1
---

# [DataFrameColumn](https://docs.microsoft.com/en-us/dotnet/api/microsoft.data.analysis.dataframecolumn?view=ml-dotnet-preview)
`Object` –> `DataFrameColumn`   

A collection of values that represent a column in a `DataFrame`.  

# Properties
- `DataType` - The type of data this column holds.
- `Item(length, startIndex)` - Returns length number of values starting from startIndex.
- `Item(rowIndex)` - Get/set values at rowIndex.
- `Length` - The length of this column.
- `Name` - The name of this column.
- `NullCount` - The number of null values in this column.

# Methods
- `AddDataViewColumn`
- `AddValueUsingCursor`
- `All` - Boolean if all the elements are True.
- `Any` - Boolean if any element is True.
- `Clamp`
- `Clone` - Produce a copy of the column.
- `Create` - Create a StringDataFrameColumn or PrimitiveDataFrameColumn.
  - Uses type inference.
- `FillNulls`
- `Filter`
- `GetDataViewGetter`
- `GetEnumeratorCore` - Returns an enumerator that iterates this column.
- `GetValue(rowIndex)`
- `GetValues(length, startIndex)` - Return length values starting from startIndex.
- `GroupColumnValues`
- `Info`
- `IsNumericColumn`
- `SetName` - Sets the name of this column.
- `SetValue(rowIndex, value)` - Sets the value at rowIndex to value.
- `ValueCounts` - Returns a DataFrame containing counts of unique values.

## Mathematical Methods
- `Abs`
- `Add`
- `And`
- `Divide`
- `Modulo`
- `Multiply`
- `Or`
- `Product`
- `Subtract`
- `Xor`

## Statistical Methods
- `CumulativeMax`
- `CumulativeMin`
- `CumulativeProduct`
- `CumulativeSum`
- `Description`
- `Max`
- `Mean`
- `Median`
- `Min`
- `Round`
- `Sum`
