---
title: glossary
date: 2023-11-12T00:00:00-06:00
draft: false
weight: 1
---

# Abstract
Terms defined here are not defined elsewhere in these notes.

# Agile
An iterative approach to project management and software development that helps teams deliver value to their customers quickly.
It involves breaking the project down into phases and emphasizes continuous collaboration and improvement. 

Agile was encoded in the Agile Manifesto which defines four values and 12 principles for agile software development.

## 4 Values
1. Individuals and interactions over processes and tools
2. Working software over comprehensive documentation
3. Customer collaboration over contract negotiation
4. Responding to change over following a plan

## 12 Principles
1. Our highest priority is to satisfy the customer through early and continuous delivery of valuable software.
2. Welcome changing requirements, even late in development. Agile processes harness change for the customer's competitive advantage.
3. Deliver working software frequently, from a couple of weeks to a couple of months, with a preference to the shorter timescale.
4. Business people and developers must work together daily throughout the project.
5. Build projects around motivated individuals. Give them the environment and support they need, and trust them to get the job done.
6. The most efficient and effective method of conveying information to and within a development team is face-to-face conversation.
7. Working software is the primary measure of progress.
8. Agile processes promote sustainable development. The sponsors, developers, and users should be able to maintain a constant pace indefinitely.
9. Continuous attention to technical excellence and good design enhances agility.
10. Simplicity--the art of maximizing the amount of work not done--is essential.
11. The best architectures, requirements, and designs emerge from self-organizing teams.
12. At regular intervals, the team reflects on how to become more effective, then tunes and adjusts its behavior accordingly.

# Continuous Integration & Delivery (CI/CD)
**Continuous Integration** — the practice of automating the integration of code changes into a software project. Accomplished through
frequent commits to a common source code repository. Code conflicts are identified quickly and remediated easily.

**Continuous Delivery** — the practice of automating deployment of code changes to a testing/production environment. Utilizes a 
*CI/CD pipeline* where automated builds, tests and deployments are orchestrated as a *release* workflow. Ensures that the "main" or
"trunk" branch is always in a releaseable state. 

## CI/CD Pipeline (or DevOps Pipeline)
Consists of:
1. Continuous Integration/Continuous Delivery (defined above)
2. Continuous Feedback
   1. Feedback from stakeholders
   2. Feedback from *continuous testing* 
   3. Feedback from *continuous monitoring*
3. Continuous Operations — or "continuous uptime" — such as that achieved with a blue/green deployment strategy

# DevOps
A set of practices, tools, and cultural philosophy that automate and integrate the processes between software development and
IT operations.

Implementing DevOps involves:
* Implementing Agile.
* "Shifting left" with CI/CD — bringing testing earlier in the development process.
* Using a DevOps toolchain.
* Using the DevOps Lifecycle.

## DevOps Lifecycle
1. Discover — research and define the scope of the project.
2. Plan
3. Build
4. Test
5. Deploy
6. Operate — incident, change, and problem tracking.
7. Observe — application and server performance monitoring.
8. Continuous Feedback

![The infinity loop. The left side is the "product" side; the right side is the "operations" side.](../image.png)

# Functional vs. Non-functional Requirements
**Functional Requirements** — requirements that define *what the software does*.  
* Examples: authentication; authorization; business rules; certification requirements; external interfaces

**Non-functional Requirements** — requirements that define *how the software works*. Since these requirements are 
non-functional, the software still performs its primary functions even if these requirements are not met.
* Examples: capacity; data integrity; flexibility; maintainability; performance; portability; reliability; scalability; security

# SDLC
System Development Lifecycle (SDLC) — A process to plan, create, test, and deploy an information system. A description of the phases of the lifecycle of a system.  

Phases:
1.  Preliminary analysis (choosing by advantage, alternatives)
2.  Systems analysis (requirements gathering)
3.  Design
4.  Development
5.  Integration & testing
6.  Deployment
7.  Maintenance
8.  Decommission