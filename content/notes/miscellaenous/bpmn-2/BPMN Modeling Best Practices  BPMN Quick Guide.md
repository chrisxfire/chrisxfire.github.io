---
title: "BPMN Modeling Best Practices :: BPMN Quick Guide"
date: 2023-10-24T00:00:00-06:00
draft: true
weight: 1
---

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-modeling-best-practices.html#_process_scope)Process Scope

*   ✪ Clearly define the scope of the Process by identifying the Who, What, When, Where and Why of your process (the Process is the How)
    
*   ✪ Identify what each instance of your Process will represent
    
    *   Instances are discreet and identifiable: you can refer to each one of them and can count them
        
    
*   ✪ Identify the potential alternative ways to trigger the Process using [Start Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/start-event.html)
    
*   ✪ Identify the potential alternative end states of the instances of the Process using [End Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/start-event.html)
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-modeling-best-practices.html#_diagram_layouts)Diagram layouts

*   ✪ Aim for BPMN Diagrams that fit one page
    
*   ✪ Layout your BPMN Diagrams neatly to ease readability by minimizing flow crossing
    
*   ✪ Use consistent layout with horizontal [Sequence Flows](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sequence-flow.html) and vertical [Data Associations](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/data-association.html) and [Message Flows](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/message-flow.html)
    
    *   BPMN Diagrams are not strict temporal orderings (as it is possible to loop back) but most readers expect a left-to-right ordering
        
    
*   ✪ Do not create zigzag layouts of elements
    
*   ✪ It should be clear what the primary (“Happy”) path of the Process is
    
*   ✪ Whenever possible, externalize the business rules from the Process to create more concise and more agile Process models using Business Rule Tasks
    
*   ✪ Create alternative visualizations of the same Process for different communication purposes and stakeholders. For example:
    
    *   ❖ A summary Diagram with all [Sub-Processes](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sub-process.html) and [Call Activities](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/call-activity.html) collapsed and not showing any [Data Objects](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/data.html)
        
    *   ❖ A verbose Diagram with all [Sub-Processes](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sub-process.html) and [Call Activities](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/call-activity.html) expanded, showing all [Data Objects](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/data.html) and [Annotations](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/artifact.html)
        
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-modeling-best-practices.html#_process_partitioning_and_structure)Process Partitioning and Structure

*   ✪ Create hierarchical multi layers of details for your Process
    
*   ✪ Use [Sub-Processes](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sub-process.html) to split your Process into "phases"
    
*   ✪ Use [Call Activities](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/call-activity.html) to re-use other Processes
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-modeling-best-practices.html#_start_and_end_events)[Start](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/start-event.html) and [End](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/end-event.html) Events

*   ✪ Always use [Start](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/start-event.html) and [End](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/end-event.html) Events
    
*   ✪ Distinguish alternative instantiation of the process as separate [Start Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/start-event.html)
    
*   ✪ Distinguish various end states as separate [End Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/end-event.html)
    
*   ✪ Flows that end in the same end state should be merged to the same [End Event](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/end-event.html)
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-modeling-best-practices.html#_gateways)[Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html)

*   ✪ Always use [Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) to depict split or merge of flows
    
*   Do not use mixt mode [Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) (both diverging and converging)
    
*   ✪ Always place an [Activity](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/activity.html) that will determine the diverging condition(s) just before a diverging [Gateway](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) of type Exclusive, Inclusive and Complex
    
    *   A benefit ' of this best practice is that this decision [Activity](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/activity.html) can now be interrupted if need be
        
    
*   ✪ Abstract multiple daisy-chained diverging [Gateways](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/gateway.html) into a Business Rule Task
    
    *   A benefit of this best practice is simplification of overloaded diagrams
        
    

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-modeling-best-practices.html#_collaborations)Collaborations

*   Do not model the internal process under focus into a [Pool](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/pool.html)
    
    *   Without a [Pool](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/pool.html) to label, one will not have the opportunity to fall into the bad practice of naming the Pool with the Process Name
