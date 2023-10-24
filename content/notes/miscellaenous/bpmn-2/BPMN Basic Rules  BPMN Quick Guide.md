---
title: "BPMN Basic Rules :: BPMN Quick Guide"
date: 2023-10-24T00:00:00-06:00
draft: true
weight: 1
---

## [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-basic-rules.html#_a_few_basic_rules_of_bpmn)A few basic rules of BPMN:

### [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-basic-rules.html#_sequence_flows)[Sequence Flows](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sequence-flow.html)

Are used to show the order that [Activities](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/activity.html) will be performed in a Process

They cannot cross [Sub-Process](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sub-process.html) boundaries

They cannot cross [Pool](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/pool.html) boundaries

### [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-basic-rules.html#_message_flows)[Message Flows](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/message-flow.html)

Are used to show communication between Participants

They cannot connect objects that are within the same [Pool](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/pool.html)

### [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-basic-rules.html#_boundary_events)[Boundary Events](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/intermediate-event.html)

✪ Must have at most one outgoing [Sequence Flow](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sequence-flow.html)

Must not have any incoming [Sequence Flow](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sequence-flow.html)

### [](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/bpmn-basic-rules.html#_sub_process)[Sub-Process](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sub-process.html)

✪ A [Start Event](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/start-event.html) in a [Sub-Process](https://www.bpmnquickguide.com/quickguide/bpmn-quick-guide/sub-process.html) must be of type None
