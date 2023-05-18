---
title: "notes > asp.net > web apps > razor pages > scaffolding"
date: 2023-01-07T00:00:00-06:00
draft: false
---

# Overview
A model can be scaffolded so that the scaffolding tool creates the CRUD operations for that model:
- Under `Pages/` add a folder for the model being scaffolded
- Right-click that folder > **Add** > **New scaffolded item** > **Razor Pages using Entity Framework (CRUD)** > Select a *Model* class > select **+** button in Data context class

In lab-tutorial-razor-pages, this creates `/Pages/Movies/Create.cshtml`, `/Delete.cshtml`, `/Details.cshtml`, and `/Edit.cshtml`
