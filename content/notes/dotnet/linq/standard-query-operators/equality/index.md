---
title: "notes > dotnet > linq > standard query operators > equality"
date: 2022-11-10T20:49:03-0700
draft: true
---
Two sequences, whose pair-wise elements are equal, and which have the same number of such elements, are equal.

NOTE: This method uses equality (reference equality), not equivalence (value equality) unless an `IEqualityComparer<T>` is used.

# Methods
| Method        | Description                                                                            | Query expression |
|---------------|----------------------------------------------------------------------------------------|------------------|
| SequenceEqual | Determines whether two sequences are equal by comparing elements in a pair-wise manner | N/A              |

# Examples
Pet pet1 = new Pet { Name = "Turbo", Age = 2 };
Pet pet2 = new Pet { Name = "Peanut", Age = 8 };

List<Pet> pets1 = new List<Pet> { pet1, pet2 };
List<Pet> pets2 = new List<Pet> { pet1, pet2 };

bool equal = pets1.SequenceEqual(pets2);

// equal is true (the lists refer to the same objects)