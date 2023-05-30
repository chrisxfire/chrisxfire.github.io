---
title: "notes > dotnet > linq > standard query operators > group"
date: 2022-11-10T20:15:40-0700
draft: true
---
A group operation puts data into groups such that the elements in each group share a common attribute.

# Methods
| Method   | Description                                                                                                              | Query expression |
|----------|--------------------------------------------------------------------------------------------------------------------------|------------------|
| GroupBy  | Groups elements that share a common attribute. Groups are represented by an IGrouping<TKey,TElement>.                  | group … by       |
| ToLookup | Inserts elements into a Lookup<TKey, TElement> based on a key-selector function. A Lookup is a one-to-many dictionary. | N/A              |

# Examples
## <u>Query Expression</u>
List<int> numbers = new List<int>() { 35, 44, 200, 84, 3987, 4, 199, 329, 446, 208 };

IEnumerable<IGrouping<int, int>> query = from number in numbers
group number by number % 2;

foreach (var group in query)
if (group.Key == 0) // These are the even numbers
group.ForEach(i => Console.WriteLine(i));
else // These are the odd numbers
…

## <u>Method</u>
Assuming:
class Pet
{
public string Name { get; set; }
public double Age { get; set; }
}

Given a List<Pet> petList:
var query = petsList.GroupBy(
pet => Math.Floor(pet.Age), // key-selector: group pet.Age values by the floor of the age
pet => pet.Age, // element-selector: map each source element to an element in an IGrouping
(baseAge, ages) => new // result-selector: project an anonymous type from each group
{
Key = baseAge,
Count = ages.Count(),
Min = ages.Min(),
Max = ages.Max()
});


