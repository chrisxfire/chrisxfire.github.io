---
title: notes > software engineering > testing > unit testing
date: 2023-05-04T00:00:00-06:00
draft: false
---

# Unit Testing
Unit Testing is part of Test-Driven Development (TDD).  
An automated piece of code that invokes a unit of work in the system and then checks a single assumption about the behavior of that unit of work.
- A "unit" of work is calling a method and getting a result.
- A unit test is a test of that unit of work.
- Unit tests generally test the public API of a class, not the private methods
- Unit tests are run in isolation and are independent of other code

General process: Create/change code —> Create repeatable test that exercises this code —> Examine results.

# Concepts
Arrange – Declare any variables the test might need.
Act – Call the code you want to test.
Assert – Check if the outcome is what is expected.
