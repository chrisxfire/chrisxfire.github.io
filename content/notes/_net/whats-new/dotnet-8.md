---
title: dotnet 8
date: 2023-11-25T00:00:00-06:00
draft: false
weight: 1
---

# What's New in .NET 8
- .NET Aspire — an opinionated stack to build observable, production-ready cloud applications.
  - Includes a curated set of components for cloud nativity including telemetry, resilience, configuration, and health checks.
- Container Enhancements
  - Hardened
    - Non-root base images
    - Default port 8080
  - Smaller
    - AOT base images
    - Chiseled images
  - More Productive
    - Publish with >NET SDK
    - Cross compilation
    - Azure auth support
- Native AOT
  - Compile apps into native code
  - Use less memory; start instantly (no JIT compiler delay)
- AI
  - System.Numerics now includes Tensor Primitives
  - AI models, services and platforms available through various SDKs 
  - Reference templates: customer chat, retrieval augmented generation, and developing apps using Azure AI services
- Blazor
  - Full stack web UI with client and server together
  - Use Blazor Server and Blazor WASM in the same app and shift users from the server to the client at runtime
  - .NET code runs significantly faster on Blazor WASM
  - New built-in components
  - Full Blazor-based Identity UI