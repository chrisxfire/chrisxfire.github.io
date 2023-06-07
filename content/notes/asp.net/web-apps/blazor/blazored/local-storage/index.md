---
title: notes > asp.net > web apps > blazor > blazored > local storage
date: 2023-05-31T00:00:00-06:00
draft: false
---

TODO...

# Overview
## APIs
| API | Description |
|-----|-------------|
| `SetItem`, `SetItemAsync` | Store a value in LocalStorage |
| `GetItem`, `GetItemAsync` | Retrieve a value based on a key |
| `ContainKey`, `ContainKeyAsync` | Check if a key exists |
| `RemoveItem`, `RemoveItemAsync` | Remove a value from LocalStorage |

## ILocalStorage
```cs
@inject Blazored.LocalStorage.ILocalStorageService localStorage

var firstName = await localStorage.GetItemAsync<string>("EmployeeFirstName");
```
