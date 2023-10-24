---
title: "BPMN Clarifications :: BPMN Quick Guide"
date: 2023-10-24T00:00:00-06:00
draft: true
weight: 1
---

Following are a few clarifications regarding some common misconceptions in BPMN:

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-clarifications.html#_processes_models_diagrams_and_files)Processes, Models, Diagrams and Files

*   In BPMN there is no equivalence between: Process, Model, Diagram and File
    
    *   A BPMN Model may contain one or more BPMN Business Process (such as in Collaborations)
        
    *   Various portions of a BPMN Model may be saved in various Files
        
    *   A BPMN Diagram depicts a subset (maybe complete) of a BPMN Process Model
        
    *   A BPMN Model may be depicted using multiple Diagrams
        
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-clarifications.html#_dataflow)Dataflow

*   A BPMN Diagram is not a Dataflow diagram
    
    *   Although [Data Objects](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/data.html) are now first class entities in BPMN. It is not recommended to try to model Dataflow using BPMN
        
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-clarifications.html#_gateways)[Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html)

*   [Gateway](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) are not decisions
    
    *   [Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) do not make decisions they only direct the flow
        
    *   ✪ A decision outcome should be determined in an [Activity](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/activity.html) prior to the [Gateway](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html)
        
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-clarifications.html#_sending_and_receiving_messages)Sending and Receiving Messages

*   ✪ Use a Message Event if the sending or receiving of the Message is considered instantaneous
    
*   ✪ [Message Task](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/tasks.html) if the sending or receiving of the Message can be interrupted
    
*   From a temporal perspective; an Event maps to a time point on a time line and a [Task](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/tasks.html) maps to a time interval
