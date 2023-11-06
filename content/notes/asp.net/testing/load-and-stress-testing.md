---
title: load and stress testing
date: 2023-10-15T00:00:00-06:00
draft: false
weight: 1
---

# Overview
> Documentation: https://learn.microsoft.com/en-us/aspnet/core/test/load-tests?view=aspnetcore-7.0

Load test and stress tests are types of performance tests:
- *Load tests* test whether an app can handle a specified load of users for a certain scenario while satisfying a response goal. The app's conditions are normal.  
- *Stress tests* test app stability under extreme conditions for extended periods of time. This is done via high user load or limiting the app's compute resources.
  - In stress tests, the app is expected to recover from failure and gracefully return to expected behavior.

Both tests should be conducted in release mode, not debug mode. This is because debug mode has more logging that can impact performance.

Third party performance testing tools include [Apache JMeter](https://jmeter.apache.org/) and [k6](https://k6.io/)