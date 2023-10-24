---
title: "BPMN Naming Conventions Best Practices :: BPMN Quick Guide"
date: 2023-10-24T00:00:00-06:00
draft: true
weight: 1
---

There are no official naming conventions in BPMN, but here are a few best practices recognized over the years:

*   ✪ Always use keywords that are meaningful to the business
    
*   Do not use uncommon abbreviations
    
*   Do not use the element type in its name
    
*   Avoid articles and pronouns
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_activity)[Activity](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/activity.html)

*   ✪ All [Activities](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/activity.html) should be named
    
*   ✪ Name [Activities](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/activity.html) using a Verb-Noun phrase
    
    *   Use the present tense of an active verb of meaning to the business
        
    *   Use a qualified noun of meaning to the business
        
    
*   Do not name multiple [Activities](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/activity.html) with the same name (except for Call Activities)
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_gateways)[Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html)

*   ✪ [Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) do not perform any work or make decisions; it is simply a visualization of divergence or convergence of flow
    
*   Do not name converging [Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html)
    
    *   Associate a [Text Annotation](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/artifact.html) when convergence logic is not obvious
        
    
*   ✪ Name diverging Exclusive [Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) with an interrogative phrase
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_sequence_flows)[Sequence Flows](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sequence-flow.html)

*   ✪ Name [Sequence flows](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sequence-flow.html) coming out of diverging [Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) of type Exclusive, Inclusive and Complex using their associated conditions stated as outcomes
    
*   ✪ Name [Conditional Sequence Flows](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sequence-flow.html) using their associated conditions stated as outcomes
    
*   Do not name [Default Sequence Flows](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sequence-flow.html)
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_events)[Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/event.html)

*   ✪ All [Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/event.html) should be named
    
*   ✪ Name Message, Signal, Escalation, and Error [Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/event.html) with a past participle using an active verb
    
*   ✪ Name Link [Event](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/event.html) with a noun
    
*   ✪ Name paired Message, Link, Signal, Escalation, and Error [Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/event.html) using a matching name
    
*   ✪ Name Timer [Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/event.html) using their schedule
    
*   ✪ Name Conditional [Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/event.html) using their trigger condition
    
*   ✪ Name [End Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/event.html) using the name of the end state
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_data_objects)[Data Objects](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/data.html)

*   ✪ All [Data Objects](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/data.html) should be named
    
*   Name [Data Objects](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/data.html) using a qualified noun that is the name of a business object or information object of meaning to the business
    
*   ✪ Name multiple instances of the same [Data Object](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/data.html) (which are really Data Object References) using a matching name followed by the applicable State in square Brackets
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_participants)Participants

*   ✪ Name Participants using a qualified noun or a noun phrase
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_roles)Roles

*   ✪ Name Roles using a qualified noun or noun phrase
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_pools)[Pools](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/pool.html)

*   ✪ Name [Pools](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/pool.html) using the Participant’s name
    
*   Do not name [Pools](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/pool.html) using the Process Name
    
    *   In BPMN a [Pool](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/pool.html) is a depiction of a Participant
        
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-naming-conventions-best-practices.html#_lanes)[Lanes](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/lane.html)

*   ✪ Name [Lanes](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/lane.html) using the Category’s name
    
    *   [Lanes](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/lane.html) are often used to categorize elements by Roles
