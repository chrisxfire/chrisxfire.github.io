---
title: local storage
date: 2023-05-31T00:00:00-06:00
draft: false
weight: 1
---

# overview
## apis
| API | Description |
|-----|-------------|
| `SetItem`, `SetItemAsync` | Store a value in LocalStorage |
| `GetItem`, `GetItemAsync` | Retrieve a value based on a key |
| `ContainKey`, `ContainKeyAsync` | Check if a key exists |
| `RemoveItem`, `RemoveItemAsync` | Remove a value from LocalStorage |

## ilocalstorage
```cs
@inject Blazored.LocalStorage.ILocalStorageService localStorage

var firstName = await localStorage.GetItemAsync<string>("EmployeeFirstName");
```
