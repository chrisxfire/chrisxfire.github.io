---
title: notes > code > cli > dotnet > tools > httprepl
date: 2021-11-28T19:53:05-0700
draft: false
weight: 1
---
# [httprepl](https://aka.ms/http-repl-doc)
httprepl is a dotnet CLI tool used for Web API development.
REPL - Read-Evaluate-Print-Loop.
An interactive HTTP shell.

# Installation
`dotnet tool install --global microsoft.dotnet-httprepl`
# 
# Commands
```powershell
connect *URI* # Connect to a web server.
ls # Returns all API endpoints available on this server.
cd *endpoint* # Connect to *endpoint*.
exit # Disconnect from the server.
get # Send HTTP GET request to this endpoint.
```
