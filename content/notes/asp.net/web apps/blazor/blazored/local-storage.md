---
title: "notes > asp.net > web apps > blazor > blazored > local storage "
date: 2023-01-01T00:00:00-06:00
draft: true
---

# Overview
## APIs
| API | Description |
|-----|-------------|
| SetItem, SetItemAsync | Store a value in LocalStorage |
| GetItem, GetItemAsync | Retrieve a value based on a key |
| ContainKey, ContainKeyAsync | Check if a key exists |
| RemoveItem, RemoveItemAsync | Remove a value from LocalStorage |

## ILocalStorage
@inject Blazored.LocalStorage.ILocalStorageService localStorage

var firstName = await localStorage.GetItemAsync<string>("EmployeeFirstName");