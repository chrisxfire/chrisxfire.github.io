---
title: "bpmn 2.0"
date: 2024-01-05T00:00:00-06:00
draft: false
weight: 1
---

# Abstract
Business Process Modeling Notation (BPMN) 2.0 is a standard for graphically representing [business process models](https://en.wikipedia.org/wiki/Business_process_modeling).

This mind map describes the elements of BPMN 2.0 along with rules and naming conventions.  Click the image for the full-size version.

> Credit: This mind map was created with content from https://www.bpmnquickguide.com/

<a href="./BPMN 2.0.svg">
    <img alt="BPMN v2.0" src="./BPMN 2.0.svg" width="100%" height="100%">
</a>

# Rules
## Overview
* A BPMN *Diagram* depicts a subset (which may be complete) of a BPMN *Process Model*.
* A BPMN Diagram is not a dataflow diagram.
* A BPMN *Model* may contain one or more BPMN *Business Processes*.
* A BPMN MOdel may be depicted using multiple Diagrams.

## Activities <img alt="" src="./activity.png" width="3%" height="3%"> 
* **Call Activities** — use these to re-use other *Processes*.
* **Sub-Process**
  * Are used to split a **Process** into "phases".
  * A **Start Event** in a **Sub-process** must be of type **None**.
* **Tasks**
  * Use **Manual Task** to depict work performed without the aid of any software application.
  * Use **User Task** to depict semi-automated work where a human performer uses a software application to complete the **Task**.
  * Use **Service Task** to depict automated work.

### Naming Conventions
* All **Activities** must be named with a *verb-noun* phrase
  * Use the present tense of an active verb of meaning to the business.
  * Use a qualified noun of meaning to the business.
* Activities other than **Call Activities** cannot have the same name. 

## Data Objects
### Naming Conventions
* All **Data Objects** must be named with a qualified noun that is the name of a business object or information object of meaning to the business.
* Name multiple instances of the same **Data Object** using a matching name followed by the applicable *State* in square brackets.

## Events <img alt="" src="./event.png" width="3%" height="3%">
* Boundary Events
  * Must have at most one outgoing **Sequence Flow**.
  * Must not have any incoming **Sequence Flows**.
* **End Events**
  * Distinguish various end states as separate **End Events**.
  * Flows that end in the same end state merge to the same **End Event**.
* **Start Events**
  * Distinguish alternative instantiation of the process as separate **Start Events**.

### Naming Conventions
* All **Events** must be named.
* **Conditional Events** — name these with their trigger condition.
* **End Events** — name these with the name of the end state.
* **Link Events** — name these with a noun.
* **Message**, **Signal**, **Escalation** and **Error Events** — name these with a past participle using an active verb.
* Paired **Message**, **Link**, **Signal**, **Escalation**, and **Error Events** — name these with a matching name.
* Timer Events — name these with their schedule.

## Flows <img alt="" src="./flow.png" width="3%" height="3%">
* **Association** Flows are laid out vertically.
* **Data Association** Flows are laid out vertically.
* **Message** Flows
  * Used to show communication between **Participants**.
  * Cannot connect objects that are within the same **Pool**.
  * Are laid out vertically.
* **Sequence** Flows
  * Are used to show the order that **Activities** are performed in a process.
  * Cannot cross **Sub-process** boundaries.
  * Cannot cross **Pool** boundaries.
  * Are laid out horizontally.
* **Messages**
  * Use a **Message Event** if the sending or receiving of the Message is instantaneous.
  * Use a **Message Task** if the sending or receiving of the Message can be interrupted.

### Naming Conventions
* **Sequence Flows**
  * Name **Sequence Flows** coming out of diverging **Gateways** of type **Exclusive**, **Inclusive** and **Complex** using their associated conditions stated as outcomes.
  * Name **Conditional Sequence Flows** using their associated conditions stated as outcomes.
  * Do not name **Default Sequence Flows**.

## Gateways <img alt="" src="./gateway.png" width="3%" height="3%">  
* Are used to split or merge **Flows**.
* Gateways are either converging or diverging (but not both).
* Gateways are not decisions
  * They do not make decisions; they only direct flow.
  * Decision outcome (diverging conditions) must be determined in an **Activity** prior to the **Gateway**.
* Use a **Business Rule Task** instead of multiple, chained diverging Gateways.

### Naming Conventions
* Converging
  * Do not name these.
  * Use a text annotation when converging logic is not obvious.
* Diverging
  * Name exclusive diverging **Gateways** with an interrogative phrase.

## Participants
### Naming Conventions
Name these using a qualified noun or noun phrase.

## Roles
### Naming Conventions
Name these using a qualified noun or noun phrase.

## Swimlanes
### Naming Conventions
* **Lanes**
  * Are often used to categorize elements by Roles.
  * Name these using the **Category's** name.
* **Pools**
  * Name these using the **Participant**'s name.
  * Do not use the Process name (in BPMN, a Pool is always a depiction of a Participant).