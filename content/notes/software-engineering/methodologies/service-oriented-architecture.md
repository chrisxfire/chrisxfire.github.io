---
title: service oriented architecture
date: 2023-02-22T11:30:23-0700
draft: false
weight: 1
---

# Service-Oriented Architecture (SOA)
An architectural style with a focus on discrete *services* vs. a monolithic design.  

Service — a function made available over a network to consumers.
- Represents a repeatable business activity with a specific outcome.
- Self-contained
- Black box to consumers
- Composable

Service Mesh — a conjunction of services that provide functionality akin to an application.  

Services must be *stateless* — they must return the requested value or an exception.  

# soa roles
1.  Service provider
2.  Service broker / registry / repository
3.  Service consumer

# implementation approaches
- Web Services — SOAP, REST, gRPC
- Microservices
- Messaging (ex: RabbitMQ)
- WCF

# soa structure
- App frontend
- Service
  - Contract
  - Interface
  - Implementation
    - Business logic
    - Data
- Service repository
- Service bus

# microservices
An architectural approach that builds an application as a series of small services that are decentralized
and autonomously developed. The services are loosely coupled, independently deployable, and easily maintainable.

Characteristics:
- Processes that communicate over a network via vendor-agnostic protocols.
- Services organized around business capabilities.
- Small; message-enabled; bound by contexts; decentralized; independently deployable.
- "Do one thing and do it well."
- Lowry: "Every class is a service."

Service granularity — defines how big a service is.
- At Amazon, 1 service = 3 to 10 engineers

# service mesh architecture
- Each service instance (SI) is paired with a reverse proxy sidecar.
- SI + sidecar share a container.
- Container is managed via orchestration.

## sidecar
- Handles communication with other Sis
- Supports service discovery
- Provides load balancing
- Handles authentication & authorization

## data plane
- Consists of SI + Sidecar
- Handles data management, request processing and response

## control plane
- Manages interaction between services via their sidecars.

## management plane
- Lifecycle
- Configuration
- Performance management

See also:
- SOA Manifesto
- Service-oriented modeling framework
- Hexagonal architecture
- Spring vs Kubernetes
