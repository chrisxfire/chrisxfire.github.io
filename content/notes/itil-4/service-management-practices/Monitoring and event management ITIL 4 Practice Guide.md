---
title: "Monitoring and event management"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# 1. Source
Axelos International (https://www.axelos.com)

# 2. Overview
**Key message**: The purpose of the monitoring and event management practice is to support the normal operation of service components by observing, analyzing, and appropriately responding to changes of state in those components.

The definition of ‘normal operation of services components’ is based on the level of service defined in service level agreements (SLAs) as well as instructions or manuals from vendors and system creators that specify actions required to maintain the effective operation of each service component. Other forms of service quality specification could also be used to define normal operation, such as company policies, regulatory compliance, and learning documented in journals by service component managers. This practice identifies and prioritizes infrastructure, application, service, business process, and information security events, and establishes the appropriate response to those events. Responses include identifying potential faults, responding to conditions that could lead to incidents, and performing activities required for services to perform at agreed levels.

> **Event** — Any change of state that has significance for the management of a service or other configuration item (CI).

Monitoring and event management is used to understand the significance of events, and to identify the appropriate response to optimize the quality and performance of services. Monitoring and event management is also used to manage events throughout their lifecycle to ensure that services are managed to meet both utility and warranty objectives.

Monitoring and event management activities are essential for managing service operation and performance. They provide operational staff with information about the status and performance of components under their control and help them to identify actions that need to be taken to ensure agreed levels of performance.

Monitoring and event management includes identification and categorization, or analysis, of events related to all levels of infrastructure and to service interactions between the organization and its service consumers. Monitoring and event management ensures appropriate and timely response to those events.

The monitoring part of the practice focuses on services and configuration items (CIs) to detect conditions of potential significance, track and record the state of servicers and CIs, and provide this information to relevant parties.

The event management part of the practice focuses on those monitored changes of state defined by the organization as an event, determining their significance, and identifying and initiating the correct response to them. Information about events is also recorded, stored and provided to relevant parties.

**Key message**: Effective monitoring and event management depends on service design including definitions of:<br>- changes of state that should be monitored<br>- significant of changes of state<br>- instruments to track changes of state<br>- the correct responses to the events.<p>These definitions and instruments should be included in the service development and deployment, and adopted by the operational staff as part of the service release and acceptance.</p>

The monitoring and event management practice is a fundamental element of the service value system, and is beneficial for both IT service provider and their service consumers.

Benefits for service providers include:
* early warnings of IT service interruption or degradation
* better IT service availability
* proactive or early detection of incidents and problems
* better understanding of service health
* better availability and performance reporting
* reduced cost of outages and a reduction in ‘firefighting’ approaches to incidents
* greater visibility of, and ability to manage, dependencies that impact value stream performance.

Benefits for service consumers include:
* better IT and business service availability
* reliable and predictable service performance
* early warnings of IT service interruption or degradation, and reduced impact.

Monitoring and event management data and information are an important input to many practices, including:
* incident management
* problem management
* information security management
* availability management
* performance and capacity management
* change enablement
* risk management
* infrastructure and platform management
* software development and management.

A key point is that events take place whether they are monitored or not. Service providers need to assess the significance of events before deciding which need to be formally detected, monitored, and managed. Some of this assessment is done as part of service design; however, some events are only identified as significant when the service is already in use. Where current monitoring and event management tools and activities are sufficient to address these newly discovered types of events, the monitoring plans and event definitions should be updated (see section 3 for more on this). If the available tools and activities are not suitable for detection and management of the newly discovered events, a service design improvement should be initiated to update the monitoring and event management capabilities of the service provider.

Not all events indicate that something bad or unusual is happening. Some events are a sign that the service is working as designed. Ensuring service health requires that these events are monitored, as well as events that represent unexpected changes in state.

The event management and monitoring practice also identifies thresholds at which changes in normal event activity indicate potential service performance or quality issues.

Events are categorized according to what action is required when they are detected. Typical categories, in order of significance, include:
* Informational: no action is required other than logging the event for reporting, trend analysis or potential forensic analysis and auditing
* Instructional: an event has occurred as part of the normal service operation, which requires the performance of a pre-defined human action
* Warning: unusual activity has been detected, or a threshold has been reached, which warrants further investigation
* Exception: activity has occurred which represents the failure of an operational activity or a disruption to the agreed level of service.

## 2.2 Terms and concepts
> **Monitoring** — Repeated observation of a system, practice, process, service, or other entity to detect events and to ensure that the current status is known.

Knowing the current status of services and service components is essential for managing them. Information about service health and performance enables the organization to:
* perform operational activities that are required to ensure that service components are performing optimally
* respond appropriately to service-impacting events that have already occurred
* take proactive actions, based on pattern analysis of past events, to prevent future adverse events from occurring.

A key aspect of event management is that the significance of events depends on the context in which they occur, and the importance of variables in that context. Defining events and deciding which events to monitor therefore requires an understanding of the context of the CI and the role it plays relative to services and value streams. An event that is normal in one situation might be suspicious in a different context.

For example: a consumer logging into an application is a normal part of using a service provided by that application. However, if that consumer logs in from an unusual location, this might raise questions about the validity of the login and would prompt an additional security check.

It is therefore impossible to define a universal set of monitoring and event management criteria, since every organization will need to define the context within which events occur, and what those events mean for them. In addition, it is important that each configuration item (CI) stakeholder has input into the criteria that are used to define and monitor events related to that CI.

Monitoring can be active or passive. In active monitoring a monitoring tool actively polls CIs, that is they issue requests to CIs to provide specific targeted data. In passive monitoring CIs themselves are configured to notify a monitoring tool when certain conditions are met.

The results of this monitoring activity may be used reactively or proactively, as shown in figure 2.1. Event management is reactive when it uses monitoring to respond to events after an impact on the service or service component has occurred. Event management is proactive when it analyzes non-impacting events (past and current) to identify a potential future impact.

Figure 2.1 Types on monitoring and event management:  
![Figure 2.1 Types on monitoring and event management](Monitoring%20and%20event%20management%20ITIL%204%20Practice%20Guide/ITIL_Monitoring_and_Event_2_1.jpg)

Another consideration is the frequency of event monitoring. In passive monitoring, CIs report the event when it occurs. In active monitoring, CIs will be polled at intervals to collect targeted information. Active monitoring takes place whether an event has occurred or not.

Passive monitoring occurs in close to real time, but only when an event occurs, or a defined set of conditions has been met. Active monitoring will detect events only when CIs are polled. This means that the polling interval must be set appropriately for the type of CI being monitored. If the frequency is too high, CI performance (and network performance) may be impaired. If it is set too low, important events may not be detected in time.

The frequency of polling, from continuous to a longer interval-based frequency, will be determined by several factors, including:
* how frequently the state of the CI changes
* the significance of events related to the CI
* the role of the CI in providing a service
* the required speed of the response
* the level of service committed to in the SLA and internal service quality specifications
* initiatives or changes which might cause changes to normal patterns of business activity (for example a marketing promotion for online services).

Monitoring is based on three types of system:
* Native monitoring features of the service components being observed. Most infrastructure components (physical and virtual) and applications have built-in monitoring capabilities and will generate data about access, utilization, performance, and so on. This data can easily be sent to a centralized event monitoring tool. Deciding which features to monitor can be challenging as these tools are generally designed to be able to report on any and every aspect of the component, many of which will not be useful in an organization’s specific context.
* Instrumentation that has been custom-built into systems, especially those that have been developed in-house. These consist of code or interfaces which collect and expose the measurement data that is important for the organization.
* Event monitoring systems that are designed for purpose. These are tools that have been designed to monitor and manage events in the context of operational activities, service performance, and contribution to value streams. These tools rely on both native monitoring and custom-built instrumentation and may also contain some pre-defined monitoring capability for common scenarios.

Although monitoring and event management is traditionally focused on technology components of services, it can also be useful to understand the state of other service management resources and activities, including processes, people, and suppliers.

> **Metric** — A measurement or calculation that is monitored or reported for management and improvement.

Metrics are sources of data for the monitoring and event management practice. Metrics data is collected, aggregated, and analyzed by the monitoring systems. The metric is compared with a benchmark, representing a range of normal operations, to detect any event which is significant in that context. Metrics range across multiple layers, including:
* low-level infrastructure metrics (host-, server-, network- and others)
* application metrics (response time, error rate, resource usage)
* service performance metrics, including infrastructure-, connectivity-, application-based and service action-based, where applicable
* third-party service performance metrics (based on agreed service levels)
* operations, process, and value stream performance metrics.

> **Threshold** — The value of a metric that triggers a pre-defined response.

Thresholds define the upper and/or lower limits of an acceptable range of values. These could be based on several factors, including performance (for example response times longer than one second are not acceptable), number of events (for example total number of transactions on a website per minute), or utilization levels (for example total percentage of network that may be consumed by a single service).

Thresholds play two important roles:
* First, they are a way of initially filtering the vast amount of monitoring data which can be collected through the monitoring tools, reporting only those events which are significant for the management of the service or service component. Threshold values should be defined to prevent resources being overwhelmed by reports of relatively insignificant events.
* Second, they provide advance warning of potential disruptions to the service or the service component. Rather than waiting for a component to fail before acting, thresholds are used to issue a warning when there are signs that a component is likely to fail if no action is taken. Thresholds should not be set too close to the point at which service is disrupted. Common practice is to set an initial warning threshold value lower or higher than the point at which disruption occurs. The exact level at which the threshold is set should strike a balance between providing ample time for resources to respond, yet not alerting them unnecessarily.

Responses to a threshold vary and may include:
* creating an alert or other notification
* creating an incident record
* change of a status of a previously recorded alert or notification
* initiating a reactive action towards the respective component or service.

Other rules for processing the measurement data are usually combined with thresholds, such as event correlation rules and engines. These are prescribed by component vendors or defined by the organization, and can be supported by machine learning.

> **Alert** — A notification that an action needs to be taken, a threshold has been reached, something has changed, or a failure has occurred.

Alerts are created and controlled by monitoring tools and are managed by the monitoring and event management practice. Alerting is a very important aspect of a monitoring system. The alerting system must have several characteristics, including being:
* highly reliable
* flexible, so that it can notify operators through multiple media
* capable of generating detailed and actionable notification messages.

‘Over-alerting’ is a potential danger for monitoring and event management. A situation arises where more alerts are generated than the enterprise can deal with and where truly significant alerts become lost in the ‘alert noise’. Aggregation, correlation, and filtering of alerts, nowadays enabled by artificial intelligence operations (AIOps) and machine learning (ML), provide the remedy for this potential danger. It is important to note, however, that these technologies are only effective if the context of the events is clearly defined and decisions are monitored and corrected where necessary.

Changes of state for services and service components occur continuously in the IT environment. As mentioned in this practice, they are typically recognized through notifications created by an IT service, CI, or monitoring tool. To properly handle and respond to the stream of data, it is necessary to filter and categorize the incoming information.

Typical processing of change-of-state data places events into one of four event groups based on their impact and defines four respective responses: informational, instructional, warning, or exception.

* Informational events do not require action at the time they are identified. Informational events provide the status of a device or service or confirm the state of a task. Examples of informational events include: a user login, an operation completed, and so forth. Informational events signify that regular operation is occurring and are stored in log files for a set period. The organization may choose to analyze the informational events later and may uncover proactive steps that can be beneficial to the service. Informational events can also be published on status dashboards for service provider’s or service consumer’s audience. Informational events are also used for audits and forensic investigations.
* Instructional events specify that a specific, pre-defined action needs to be taken for successful operation or service completion. This specifically refers to a manual activity, or an activity that requires manual sign-off, for example loading paper into a printer, or commissioning a new virtual server in the cloud.
* Warning events allow action to be taken before any negative impact is experienced. Warning events signify that an unusual, but not exceptional, operation is occurring. A warning event notifies the appropriate team or tool to take necessary actions to prevent an exception from occurring. Examples of warning events include when scheduled backups are not running, or resource utilization is within 10% of the agreed exception threshold.
* Exception events indicate that a critical threshold for a service or component metric has been reached, or that a component has failed. This identified breach of an established norm for the service or component performance may not yet be having an impact on business operations. However, the exception event may also indicate that a service or component is experiencing a failure, performance degradations, or loss of functionality, all of which impact business operations. In either case, exception events require action, as they signify that an exception to regular operation is occurring. Examples of exception events are when a PC scan reveals the installation of unauthorized software, a server is down, a backup has failed, and so on. This is how detection of incidents is enabled by the monitoring and event management practice.

The four types of the events are summarized in Table 2.1.

### **Table 2.1 The four types of events**
<table><tbody><tr><td><strong>Type</strong></td><td><strong>Condition</strong></td><td><strong>Service/user negative impact</strong></td><td><strong>Response required</strong></td></tr><tr><td>Informational</td><td>Normal</td><td>No</td><td>No</td></tr><tr><td>Instructional</td><td>Normal</td><td>Pending</td><td>Y, predefined</td></tr><tr><td>Warning</td><td>Abnormal</td><td>No or pending</td><td>Y, investigation</td></tr><tr><td>Exception</td><td>Incident</td><td>Yes</td><td>Y, incident management</td></tr></tbody></table>

Event categorization focuses attention on the events that are truly significant for the management and delivery of services. It ensures that operational events are tracked, assessed, and managed appropriately.

Monitoring and event management enables the detection of incidents, distinguishing them from information events and warnings. Detected incidents are handled by the incident management practice. Monitoring and event management also enables problem identification by providing information about trends and events affecting services and service components. In addition, monitoring and event management enables error control for known errors by monitoring and reporting on services and service components. Identified problems and error control for known errors are handled by the problem management practice.

## 2.3 Scope
The scope of the monitoring and event management practice covers all aspects of an organization’s service management that need to be controlled and can be automated. This includes:
* identifying and optimizing the scope of monitoring
* implementing and maintaining continuous monitoring
* establishing and maintaining event identification, categorization and processing rules
* implementing processes and automation tools to operationalize the defined event management rules
* ongoing processing of events according to the agreed and implemented rules and processes
* providing information about the current and historical state of the monitored services and resources to relevant stakeholders in an agreed form.

There are several activities and areas of responsibility that are not included in the monitoring and event management practice, although they are still closely related to monitoring and event management. They are listed in Table 2.2, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams and should be combined as necessary depending on the situation.

##### Table 2.2 Activities related to the monitoring and event management practice described in other practice guides
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Practice Guide</strong></td></tr><tr><td>Management of incidents</td><td>Incident management</td></tr><tr><td>Investigation of causes of events and trends</td><td>Problem management</td></tr><tr><td>Management of changes in response to events</td><td>Change enablement</td></tr><tr><td>Communications with users</td><td>Service desk</td></tr><tr><td>Support decision-making based on monitoring data</td><td>Measurement and reporting</td></tr><tr><td>Setting targets and thresholds for service quality and performance</td><td>Service level management<br>Availability management<br>Performance and capacity management<br>Information<br>Information security management<br>Continuity management<br>Service design</td></tr><tr><td>Setting thresholds for infrastructure and application components</td><td>Infrastructure and platform management Software development and management Service design</td></tr><tr><td>Setting targets and thresholds for third parties’ services</td><td>Supplier management<br>Service design</td></tr></tbody></table>

## 2.4 Practice success factors
> **Practice success factors** — A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity; it includes components from all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The monitoring and event management practice includes the following PSFs:
* establishing and maintaining approaches/models that describe the various types of events and monitoring capabilities needed to detect them
* ensuring that timely, relevant, and sufficient monitoring data is available to relevant stakeholders
* ensuring that events are detected, interpreted, and acted upon as quickly as possible if necessary.

#### 2.4.1 Establishing and maintaining approaches/models that describe the various types of events and monitoring capabilities needed to detect them
The monitoring and event management practice integrates the technical expertise required to operate service elements with the knowledge of how those elements are used to support value streams and business outcomes. On the one hand the practice depends on the deeply technical understanding of how the service components operate, contained in manuals, knowledge articles, and the extensive informal documentation maintained by technical experts from their own experience. On the other hand, it depends on understanding how those components should perform so that they achieve the intended objectives of services and service value streams.

Modern technologies can measure and monitor most aspects of the services and service component operation, but only a subset of these are usually relevant in a particular situation. A practitioner should carefully manage the scope of the monitoring, as well as frequency and number of metrics. The main challenge of the modern monitoring and event management practice is not lack of data but the volume of data that monitoring must deal with. The focus of the monitoring and event management practice should be getting meaningful information to support service operations, service improvement, decision-making, and value creation. When establishing or improving the monitoring and event management practice, the following aspects should be considered:
* Identifying and prioritizing services and service components monitored. Identifying and prioritizing which entities should be monitored is a key activity of the practice, helping to detect changes of state (or lack of desired changes in state) that are most significant for the management of a service of CI. Deciding which services, systems, CIs, and other service components to monitor will be based on the organization’s business objectives. It will also require a thorough understanding of the organization’s service design architecture. Practitioners of monitoring and event management will need to know service dependency mapping: what top-level business capabilities map to which products and services support those capabilities, and in turn which products and services map to the underlying IT infrastructure that enables the products and services. By having a full end-to-end picture of what entities are involved in delivering a service, the monitoring and event management practitioners will be able to correctly identify and prioritize the critical entities that need to be monitored. Here, ‘monitorability’ of a service component should also be assessed and effective set of criteria defined. Criteria chosen should be revealing enough and provide a basis for diagnostics and decision making.

* Finding balance between informativity, granularity, and frequency of the monitoring.
* Establishing and maintaining monitoring of a service component could be considered as an investment of resources (monitoring tools, data storage, manhours, and so on), and the more data is captured, the less return is expected. This is because the greater the number of criteria monitored and frequency of probing, the more time and effort needs to be spent filtering, classifying and analysing data. Automation and machine learning-based solutions could help to free people and improve results of data analysis, but a practitioner should always aim at making the monitoring the most efficient.
* Maintaining capabilities for data gathering, storage, filtering and data correlation. The monitoring and event management practice relies heavily on the Information and Technology dimension of service management. Without the native monitoring features of the services and service components being observed, and without the IT monitoring tools (generic widely available commercial tools as well as custom-built tools) it would be virtually impossible to detect changes of state that have significance for the management of a CI or a service.
* Information about service elements is collected by polling, that is, in response to interrogation by a monitoring tool to collect specific targeted data, or by automatically notifying a monitoring tool when certain conditions are met. This communication depends on the availability of the monitoring tools and on the networks to transmit the event data.
* Additional attention should be paid to the tools that classify, filter and correlate data, as well as the tools that are used to automate responses to events.

Deciding which services, systems, CIs, and other service components to monitor will be based on the organization’s business and mission objectives. It also requires a thorough understanding of the organization’s service architecture and any service level agreements for each service. Practitioners of monitoring and event management will need to know service dependency mapping: how products and services map to the underlying IT infrastructure that enables them. By having a full end-to-end picture of what entities are involved in delivering a service, the monitoring and event management practitioners will be able to correctly identify and prioritize the critical entities that need to be monitored.

A great deal of the service architecture of individual services often consists of third-party products and services which the organization has integrated to deliver an end-to-end service to customers and users. The built-in monitoring capabilities of these third-party products and services are a key part of the monitoring and event management practice. Monitoring and event management practitioners along with their counterparts in the service design practice need to be able to cooperate frequently and well with their equipment and service vendors. In doing so, monitoring and event management and Service Design secure the necessary goods and services that constitute the organization’s services and ensure that these services are monitorable and manageable.

Determining the appropriate control action for events relies on the filtering and categorization of the detected events. Filtering and categorization, occurring in the information and technology service dimension, are largely done automatically by the organization’s event management system (EMS) into which the IT monitoring tools feed the detected, collected, and transmitted information. The business rules, however, by which the EMS filters and categorizes the data and makes determinations of significance about them (deciding whether the data represent an informational, instructional, warning, or exception event) are established in the organizations and people dimension of service management. The thresholds, the alerting parameters, the criteria which the monitoring tools and the EMS are configured to address are all the product of organizational priorities and the skilled leadership and staff working to ensure the operational health of the service ecosystem.

Policies need to be in place to handle different types of events. A ‘one size fits all’ approach to events is inappropriate and a waste of resources. Different types of events require a response that is tailored and specific to the type of event it is. A common set of control actions should be established for each class of event. Policies will address when an auto response is appropriate, when an alert and escalation to human intervention is appropriate, when an incident, problem, or change should be initiated, or when special handling is required. For example, in the case of a security breach that potentially could have operational impact but has not yet affected service availability. Policies are defined in the organizations and people dimension and are operationalized in the Information and Technology dimension.

Having in place a standard classification scheme for events, such as informational, instructional, warning, and exception, enables common handling and escalation processes. It also enables event notifications to be sent only to those responsible for the handling of further actions or decisions related to the events. Avoiding notifications to individuals not directly involved in processing events is an efficient use of resources. To do this, event notifications will identify which departments, groups or individuals need to respond to events. Maintaining event routing information is a constant task as new events are added, or personnel responsibilities change.

A standard classification scheme for events will enable a common set of actions to be established for each class of event. In the value streams, when action is being taken on recognized events, operational and service level objectives for the service are taken into consideration. Actions for events that trigger the notification of incidents and problems can be tied into existing categorization and prioritization policies that have been established by incident and problem management.

Many of the IT monitoring tools and the EMS itself will likely be supplied by third party suppliers with whom the monitoring and event management practice in conjunction with the supplier management practice will maintain solid working relationships.

#### 2.4.2 Ensuring that timely, relevant, and sufficient monitoring data is available to relevant stakeholders
The reporting aspect of monitoring and event management enables ground truth with respect to a service provider’s actual operating performance and behaviour when benchmarked against the standards in the original service design and in the service level agreements (SLAs) agreed with the customers. Monitoring and event management provides direct observation results, real-world empirical evidence as opposed to intended or aspirational results.

It should be noted that SLAs exist to define the level of services to be delivered. SLAs are used as input to defining which events are significant and how they should be managed and reported. SLAs should not be defined for individual events. If a specific level of performance is required when managing a particular event, or if certain events need to be reported to users or customers, this should be defined as one of the parameters of that type of event linked to the originating SLA, and not as a separate ‘event SLA’.

Gathering data that has accuracy and integrity in the monitoring and event management practice is critical to the work of delivering a high-quality service and a high-quality customer experience when using the service. Areas that depend on the activities of monitoring and event management include:
* Service measurement (the gathering of data about the service).
* Continual improvement efforts rely on the effectiveness and efficiency of services and service components. Monitoring and event management identifies weak areas, so that remedial action can be taken (if there is a justifiable business case), therefore improving future service quality. Monitoring and event management can also show where customer actions are at fault and identify where working efficiency and/or training can be improved.
* The management of internal and external suppliers, since their performance must be evaluated and managed.

#### 2.4.3 Ensuring that events are detected, interpreted, and acted upon as quickly as possible if necessary
Defining rules for monitoring and event management is not enough; actual detection and processing of events is required to make these rules valuable. Event management efficiency and scope depend on the service architecture and level of service management automation. In digital infrastructure and modern application, many tools for monitoring and event management are built-in, and the focus of the practice is on the integration and tuning of the event processing rules.

Organizations with many legacy systems which were not designed for monitoring must focus on implementing specialized monitoring and event management tools and add-ons, or even on manual monitoring and event management.

Technology opportunities and constraints should inform monitoring and event management scope, policy making, and daily activities.

Regardless of how limited an organization’s monitoring and event management capabilities are, they should be subject to continual improvement, to ensure that the practice meets the needs of the organization.

## 2.5 Key Metrics
The ITIL practices are means or tools for the management of products and services. Like the performance of any tool, practice performance can be assessed only in the context of that tool’s application. However, tools can differ in quality. This difference defines the tool’s potential or capability to be effective when used according to their purpose.

The same applies to practices: their performance should be assessed in the context of value streams, but their potential is defined by their design and the quality of the resources. Further guidance on metrics, KPIs, and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the monitoring and event management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the monitoring and event management practice to the effectiveness and efficiency of those value streams. The key metrics are listed in Table 2.3.

##### Table 2.3 Key metrics for monitoring and event management
<table><tbody><tr><td><strong>Practice success factors</strong></td><td><strong>Key metrics</strong></td></tr><tr><td>Establishing and maintaining approaches/models that describe the various types of events and monitoring capabilities needed to detect them</td><td>Satisfaction of the stakeholders with monitoring and event management approach<br>Adherence of the organization to the approach<br>Percentage of the recommendations/requirements of the approach that are not followed or found unrealistic<br></td></tr><tr><td>Ensuring that timely, relevant, and sufficient monitoring data is available to relevant stakeholders</td><td>Satisfaction of the stakeholders with monitoring data and its presentation Quality of the monitoring data (as per agreed data quality criteria)</td></tr><tr><td>Ensuring that events are detected, interpreted, and acted upon as quickly as possible if necessary</td><td>Impact of event management errors<br>Number and impact of event communications ‘noise’<br>Impact of incidents and problems that could not be prevented or resolved due to poor event management</td></tr></tbody></table>

While individual metrics for specific service components is valuable to the managers of those components, the ongoing management of value streams and continual improvement of the monitoring and event management practice rely on the correct aggregation of metrics into complex indicators.

There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

# 3. Value streams and processes
## 3.1 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

> **Process** — A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.

Monitoring and event management activities form two processes:
* **Monitoring planning** This is a process of adding an element into monitoring, defining the priority of the element, choosing features to monitor, establishing metrics and thresholds for event classification, mapping events with the action plans and teams responsible.
* **Event handling** This process is focused on capturing events, making sense of them, and processing them according to the agreed monitoring plans.

In addition to these processes there is a set of review activities ensuring continual improvement for the practice:
* **Monitoring and event management review** These activities do not form a single process.

#### 3.1.1 Monitoring planning
This process includes the activities listed in Table 3.1, and transforms the inputs into outputs.

##### Table 3.1 Inputs, activities, and outputs of the monitoring planning process
<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Service health criteria from service design<p>SLAs</p><p>Service performance thresholds from availability, capacity and performance management practices</p><p>Knowledge articles</p><p>Service catalogue</p><p>CI data</p></td><td><span>Defining the objective of monitoring<p>Defining what needs to be, and can be monitored</p><p>Defining types of events for the object of monitoring</p><p>Defining the thresholds for different type of events</p><p>Defining a service ‘health model’ (end-to-end events)</p><p>Defining events correlations and rule sets</p><p>Defining the monitoring action plans</p><p>Defining the required capabilities of monitoring and event management tools</p></span></td><td>Monitoring plan for the object<br>Service health model<p>Defined types of events, criteria for event detection, priority, and response to the events</p><p>Responsibility matrix for events</p></td></tr></tbody></table>

##### Table 3.2 Activities of the monitoring planning process
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Description</strong></td></tr><tr><td>Defining the objective of monitoring</td><td>With information received from the service design stage and service validation and testing practice and practices involved in the development of the service (availability, capacity, and performance management practices) and service level management practice, the team defines key objectives of monitoring.<p>This discussion should move from warranty to utility requirements (first covering the most obvious functionality requirements, that were, for example, in the user stories for the application).</p><p>Also, it should increase in granularity, starting with the key service performance and moving to more details and components.</p><p>Team should make a list with descending monitoring priority.</p></td></tr><tr><td>Defining what needs to be, and can be monitored</td><td>Monitoring priority list items are then mapped or translated into available measurements or synthetic measurements based on available measurements.<p>Adding measurements should be explored.</p></td></tr><tr><td>Defining types of events for the object of monitoring</td><td>The team defines and classifies different types of events. Types could be general, like informational, instructional, warning, exception, or may depend on the functionality, user groups and their priorities, divided by components or types of key monitoring objectives. It is important to note that some event types are not native to a system. In these cases the system has to be instrumented to generate meaningful information about the events. For example, if a particular operator action is required, and event should be generated that specifies what that action is, and perhaps who should perform it, and so on.</td></tr><tr><td>Defining the thresholds for different type of events</td><td>The team, together with service or component development team, defines the thresholds for types of events. The same component metric could be treated differently based on the service it contributes into, depending on the existing SLAs and availability, capacity and performance requirements defined for the service or component.<p>Also, event handling throughput should be taken into consideration, as, although modern IT systems can detect almost any event, not any event should be acted upon. So generally monitoring and event management should be developed iteratively, from preventing disasters in the very beginning, to refinement of components later.</p></td></tr><tr><td>Defining a service ‘health model’ (end-to-end events)</td><td>Based on input from teams involved in the service design, a ‘health model’ is built, that reflects the key events in the service and connections between them. There could be several models for one service.<p>Such models let monitoring team assess user experience of the service. For example, a model can be built for a single bank customer transaction, and measure how much time it takes from a request in mobile app, with all the bank database systems in-between, to the notification of completed transaction in the mobile app.</p><p>Service health models could also be implemented as reports or dashboards on service health and performance are used on an ad-hoc basis by service owners, teams involved in other practices, and other stakeholders. This way the information about the service is 'pulled' by a stakeholder.</p></td></tr><tr><td>Defining event correlations and rule sets</td><td>Together with teams involved in the service design, event correlations and corresponding sets of rules are defined.<br>Some correlations might use second event as a check of the first event, or to further filter the scope of the event. Also, defined correlations can help preventing some negative synergic effects events might have when occurring simultaneously.<p>A rule set consists of several rules that define how the event messages for a particular event will be processed and evaluated. For example, a warning event may be generated each time a disk log file reaches its capacity, but an exception event will be generated if more than four warning events have been generated.</p><p>Rules themselves are typically embedded into monitoring and event handling technologies. They consist of Boolean kinds of algorithms to correlate events that have been generated in order to create additional events that need to be communicated. These algorithms can be codified into event management software typically referred to as correlation engines.</p><p>Artificial Intelligence (AI) systems could be used to define typical and atypical behaviour of users, admins, systems, and so on. This may form an additional check to filter the events.</p></td></tr><tr><td>Defining the monitoring action plans</td><td>For each event or group of events, an action plan to minimize the negative impact of the event is defined. Based on the action plan, the team or function responsible for actions following the event, can be defined.<p>Action plans can also be executed automatically or be semi-automated, including human intervention for some important actions.</p><p>Action plans created at this stage become a basis for event procedures and automation.</p></td></tr><tr><td>Defining the required capabilities of monitoring and event management tools</td><td>Determining the level of instrumentation already in place in service components, and defining how this will be handled in the selected monitoring and event management tools.<p>Identifying which tools are already in place, and whether they will meet the needs of all monitoring and event management requirements.</p></td></tr></tbody></table>

##### Figure 3.1 shows a workflow diagram of the process.
Figure 3.1 Workflow of the monitoring planning process:  
![Figure 3.1 Workflow of the monitoring planning process](Monitoring%20and%20event%20management%20ITIL%204%20Practice%20Guide/ITIL_Monitoring_and_Event_3_1_rotate.jpg)

#### 3.1.2 Event handling
This process includes the activities listed in Table 3.3, and transforms the inputs into outputs.

##### Table 3.3 Inputs, activities, and outputs of the event handling process
<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Notifications from monitoring objects, monitoring tools<br>Monitoring plan</td><td>Event detection<br>Event logging<br>Event filtering and correlation check (might be iterative)<br>Event classification<br>Event response selected<br>Notifications sent; response procedure carried out</td><td>Event record<br>Events statistics updated<br>Event response errors<br>Major event post-mortem initiated<br>Stakeholder notifications<br>Knowledge articles update<br>Incidents logged<br>Updated reports and dashboards</td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

Figure 3.2 Workflow of the event handling process:  
![Figure 3.2 Workflow of the event handling process](Monitoring%20and%20event%20management%20ITIL%204%20Practice%20Guide/ITIL_Monitoring_and_Event_3_2.jpg)

#### Table 3.4 Activities of the event handling process
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Description</strong></td></tr><tr><td>Event detection</td><td>The event is detected by monitoring systems, or as a result of manual monitoring.<br>Not all events should be detected, and monitoring systems bandwidth should be taken into consideration. Only critical events and events that can be acted upon should be detected within existing resource constraints.</td></tr><tr><td>Event logging</td><td>The event should be logged in the monitoring system, preferably automatically.</td></tr><tr><td>Event filtering and correlation check (might be iterative)</td><td>The event should be treated according to rule sets, to filter and find correlations, to enable better classification.<br>This activity might be iterative.</td></tr><tr><td>Event classification</td><td>The event classified into a group or type, and the specific event is filtered further within a group if needed to select a proper response.</td></tr><tr><td>Event response selected</td><td>An action plan or response procedure should be planned for each event in the monitoring planning process. Based on the rules defined in planning, an event response is selected, and teams are notified.</td></tr><tr><td>Notifications sent; response procedure carried out</td><td>The response procedure is carried out, and teams responsible for actions, or supervision if the response procedure is fully automated, are notified.</td></tr></tbody></table>

#### 3.1.3 Monitoring and event management review activities
The monitoring and event management review inputs, activities and outputs are listed in Table 3.5.

##### Table 3.5 Monitoring and event management review inputs, activities, and outputs
<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Updated knowledge articles<br>Major event records<br>Major incident records<br>Improvement proposals<br>Event records and statistics<br>User and administrator manuals created by suppliers or developers<br>Information requests from service owners and stakeholders</td><td>Major events review<br>Review of filtering and correlation analysis<br>Review of service health models<br>Review of event response procedures and automation<br>Review of monitoring and event tools<br>Review of statistical information</td><td>Updated event response procedures<br>Improvement proposals for filtering and correlation analysis<br>Changes proposed to automation<br>Updated monitoring criteria and thresholds<br>Updated filtering methods<br>Updated list of tools and technology used<br>Updated list of reports and statistical information provided</td></tr></tbody></table>

##### Table 3.6 Monitoring and event management review activities
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Description</strong></td></tr><tr><td>Major events review</td><td>The fact that a major incident occurred may often mean that some abnormal service or component behaviour was not detected and acted upon.<p>Therefore, major events provide a good basis for knowledge discovery and improvements.</p><p>The nature of the major event should be reviewed, analyzed for event correlations, decomposed to component level, and corresponding metrics should be explored that may have helped to detect or respond to the major event or failure that led to the major incident.</p><p>Risks to similar components should be explored, and events identified should be added to monitoring plans.</p></td></tr><tr><td>Review of filtering and correlation analysis</td><td>Filtering and correlation should be addressed when monitoring detects a huge number of events or does not detect events when it should. Sometimes temporary measures could be considered, like loosening the thresholds or grouping of events. Otherwise, detailed analysis and thorough rules definition should be undertaken, and changes to monitoring proposed as a result.</td></tr><tr><td>Review of service health models</td><td>Reviews of the service health models are conducted with the service owner and other stakeholders using dashboards to measure the performance and health of services. These reviews validate that the appropriate events are being managed in the appropriate manner. It also ensures that the items being measured still represent what is important to the service stakeholder. Following the reviews, updates are made to the health models and to the monitoring plan as necessary.</td></tr><tr><td>Review of event response procedures and automation</td><td>Incidents and failures occurring as a result of event response should be reviewed and changes proposed.<p>Also, this review should aim at increasing automation in both detecting events and responding to them. Additional automation should be proposed.</p></td></tr><tr><td>Review of monitoring and event tools</td><td>Any tools available internally and in the market, which may increase efficiency of monitoring, should be reviewed. Trials and proof of concept should be proposed within the budget for monitoring.<p>Also, this review should discuss any new techniques or best practices used in monitoring, market benchmarking should be carried out, and improvements to monitoring proposed.</p></td></tr><tr><td>Review of statistical information</td><td>Statistical information should be reviewed, to propose improvements to monitoring, services monitored.<br>Trends detected for services should be reviewed by all teams involved in the service lifecycle.</td></tr></tbody></table>

### 3.2 Value stream contribution
#### 3.2.1 Service value streams
To perform certain tasks or respond to particular situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario. Once designed, value streams should be subject to continual improvement.

> **Value stream** — A series of steps an organization undertakes to create and deliver products and services to consumers.

In practice, however, many organizations come to use of the value stream concept after having worked for a while (sometimes for years) without the value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the ‘As Is’ situation, the de-facto flows of work, and to analyze them in order to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding the existing value streams is critical to improving organization’s performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services.

Combined, organizations’ value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations follow best practice recommendations for various service management practices, such as incident management, change enablement, software development, and many others. Problem management is one of the most adopted and developed practices.

However, the practices have often been adopted and organized in a siloed, isolated manner, just as they were presented in the service management bodies of knowledge. In reality, a flow of work required to create or restore value for a customer, or another stakeholder is almost never limited to one practice.

#### 3.2.2 Monitoring and event management in service value streams
Monitoring and event management exists to some extent in every organization that uses technology. On its own, this is no indicator that services are effectively managed or that value streams are achieving their outcomes.

To be fully effective, the monitoring and event management practice must be designed to include every level of service component used to deliver and support services, as well as any relevant operational activity that is used to create value.

Most technology components include monitoring and event management capabilities by default that are designed to assist operations staff and administrators to keep the component functioning optimally,

according to specifications set by the component’s designers and developers. It should not be assumed that the designers or developers were working with the specific needs of individual services or value streams in mind, especially when using components delivered by an external supplier.

To be effective, monitoring and event management should include activities that are required for optimal performance of the device, those required to ensure that services are being delivered as agreed, and those that are required for the component to contribute to the creation of value in the organization.

Monitoring and event management is involved in various service value streams, including those mentioned in Table 3.7

##### Table 3.7 Role of the monitoring and event management practice in service value streams
<table><tbody><tr><td><strong>Service value stream</strong></td><td><strong>Role of the monitoring and event management practice</strong></td></tr><tr><td>Resolution of incidents</td><td>Detection of incidents<br>Confirmation of the restoration of normal operations</td></tr><tr><td>Fulfilment of service requests</td><td>Confirmation of successful fulfilment<br>Detection of errors during fulfilment<br>Detection of conditions for fulfilment activities</td></tr><tr><td>Ongoing operations of the technology infrastructure</td><td>Detection of events that trigger predefined maintenance activities<br>Detection of abnormal events that require investigation<br>Confirmation of normal operation of the components and services</td></tr><tr><td>Deployment and release of new components, products, and services</td><td>Confirmation of successful implementation Detection of errors during deployment and release</td></tr><tr><td>Testing and live implementation of disaster recovery plans (DRPs)</td><td>Detection of emergency events activating the DRPs<br><span>Confirmation of successful implementation of emergency measures<br>Detection of errors during DRP implementation</span></td></tr></tbody></table>

#### 3.2.3 Analysing a service value stream
##### 3.2.3.1 The key steps of a service value stream analysis
The following are some simple and practical recommendations for service value stream analysis and mapping:
* **Identify the scope of the value stream analysis** Value streams can be mapped to a particular product or service or applied to most or all of them. Value streams may differ for different consumers; for example, incidents can be solved and communicated differently for internal and external customers, or for B2B and B2C products, or for services based on products developed inhouse or sourced externally.
* **Define the purpose of the value stream from the business standpoint** Make sure the stakeholder’s concerns are clearly understood, since they are the ones defining value. In the case of monitoring and event management, it is usually the service owners who need to ensure that service quality is known and meets the agreed requirements; however, there are usually other interested parties. For example, internal users may be unable to provide normal service to a business customer because of the incident, and the value of the value stream should be considered from the business perspective, not solely from the user perspective.
* **Do the service value stream walk** Walk or directly experience the steps and information flow as they go in practice (consider the Lean technique of Gemba walk):
**a. Identify the workflow steps**

**b. Collect data as you walk**

**c. Evaluate the workflow steps** Typically, the criteria for evaluation are:
* value for the stakeholder (does the step add value for the business stakeholder?)
* effectiveness and performance (is the step performed well?)
* availability (are required resources available to execute the step?)
* capacity (are required resources enough?)
* flexibility (are the required resources interchangeable within the step?).

**d. Map the activities and the information flows** In an ideal situation, the flow goes smoothly without delays and pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

**e. Create and review the timeline and resource leve**l Map out process times and lead times for resources and workload through the workflow steps.  

* **Reflect on the value stream map (VSM)** Identify factors that might not have been entirely apparent at first. The information collected is used at this step to find the waste.
* **Create a ‘to be’ VSM** This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.
* **Using the ‘to be’ VSM, plan improvements** Refer to the continual improvement practice guide for a practical improvement model.

### 3.2.3.2 Monitoring and event management considerations in a service value stream analysis
To ensure that relevant monitoring and event management activities are included in service value streams, the following steps can be added to the above recommendations.

* At the scoping step (1), identify the key stakeholders using the monitoring and event information, and their expectations. Identify the services and components subjected to monitoring, associated required information and currently available data.
* Make sure the value stream is understood (step 2) from the standpoint of the business, not only of the service provider. Specifically, understand what information the users and customers expect, and what events may have a direct impact on the service consumer and the success of the service value stream.
* During the service value stream walk (3a), confirm (and sometimes identify new) components and events that need to be monitored. Many of these components and events are not visible to the users. However, they may be crucial for normal operations of the services, fulfilment of SLAs, and for the user experience.
* During the workflow steps evaluation (3c), evaluate the step’s impact on the business value. Special attention should be paid to steps with low business value, low performance, and availability or capacity issues. It is not unusual to find steps which serve some internal control or bureaucratic purposes but delay the business results of the value stream and the associated value. In case of monitoring and event management, opportunities for improvement can be found in manual operations (or approvals), overly complicated and inconvenient interfaces of dashboards and reports, inefficient scope and/or frequency of active monitoring, and so on.
* At the reflection and planning steps (4-5), ensure that the monitoring and event management processes are optimized for business value throughout the stream, not only at the within the operations team of the service provider.
* Consider including the creation or updating of the event monitoring, management, and reporting in the value stream improvement plans (step 6).

# 4. Organizations and people
### 4.1 Roles, competencies, and responsibilities
The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. The practice guides focus on specialist roles specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended.

Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

##### Table 4.1 Competency codes and profiles
<table><tbody><tr><td><strong>Competency code</strong></td><td><strong>Competency profile (activities and skills)</strong></td></tr><tr><td>L</td><td><strong>Leader</strong> Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</td></tr><tr><td>A</td><td><span><strong>Administrator </strong></span><span>Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</span></td></tr><tr><td>C</td><td><strong>Coordinator/communicator </strong>Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</td></tr><tr><td>M</td><td><strong>Methods and techniques expert </strong>Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</td></tr><tr><td>T</td><td><strong>Technical expert</strong> Providing technical (subject matter) expertise and conducting expertise-based assignments</td></tr></tbody></table>

Examples of roles which can be involved in monitoring and event management activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

##### Table 4.2 Examples of roles with responsibility for monitoring and event management activities
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Responsibilities</strong></td><td><strong>Competency profile</strong></td><td><strong>S</strong><strong>pecific skills</strong></td></tr><tr><td><em>Monitoring planning process</em></td><td></td><td></td><td></td></tr><tr><td>Defining the objective of monitoring</td><td>Service owner<br>Designer<br>Developer<br>User<br>Delivery manager<br>Account manager<br>Tester<br>Service validation specialist<br>Operations manager</td><td>CA</td><td>Understanding of service value for stakeholders and service proposition<br>Knowledge of service levels and user experience</td></tr><tr><td>Defining what needs to be and can be monitored<br>Defining types of events for the object of monitoring<br>Defining the thresholds for different type of events</td><td>Tester<br>Service validation specialist<br>Monitoring specialist<br>Developer<br>Designer<br>Architect Operations</td><td>TM</td><td>Knowledge service architecture and design<br>Expertise in monitoring tools, probe detectors and sensors</td></tr><tr><td>Defining a service 'health model' (end-to-end events)<br>Defining events correlations and rule sets</td><td>Service owner<br>User<br>Delivery manager<br>Account manager<br>Operations manager<br>Tester<br>Service validation specialist<br>Monitoring specialist<br>Developer<br>Designer<br>Architect</td><td>TMA</td><td>Knowledge of user experience<br>Knowledge of warranty and utility requirements<br>Knowledge of service subject matter and business processes<br>Knowledge of service architecture and design<br>Expertise in monitoring tools and probe detectors and sensors</td></tr><tr><td>Defining the monitoring action plans</td><td>Service owner<br>User<br>Delivery manager<br>Account manager<br>Tester<br>Service validation specialist<br>Monitoring specialist<br>Developer<br>Designer<br>Architect</td><td>ATM</td><td>Knowledge of operations and support infrastructure and organization<br>Knowledge of service architecture and design<br>Expertise in monitoring tools and probe detectors and sensors</td></tr><tr><td>Defining the required capabilities of monitoring and event management tools</td><td>Designer<br>Developer<br>Service validation specialist<br>Monitoring specialist<br>Operations manager<br>Architect</td><td>TMA</td><td>Knowledge of the monitoring plan elements<br>Understanding of internal and external monitoring and event management tools available<br>Expertise in monitoring tools, probe detectors and sensors</td></tr><tr><td><em>Event handling process</em></td><td></td><td></td><td></td></tr><tr><td>Event detection</td><td>Monitoring specialist<br>Product or service owner<br>Project manager<br>User or super-user<br>CI owner<br>Tester</td><td>T</td><td>Understanding of the monitoring context</td></tr><tr><td>Event logging</td><td>Monitoring specialist<br>Product or service owner<br>Project manager<br>User, super-user<br>CI owner<br>Tester</td><td>AC</td><td>Understanding of the monitoring context<br>Knowledge of the event logging procedures</td></tr><tr><td>Event filtering and correlation check (might be iterative)</td><td>Monitoring specialist<br>Product or service owner<br>Project manager<br>User, super-user<br>CI owner<br>Tester</td><td>TA</td><td>Understanding of the events context</td></tr><tr><td>Event classification</td><td>Monitoring specialist<br>Product or service owner<br>Project manager<br>User, super-user<br>CI owner<br>Tester</td><td>TA</td><td>Understanding of the events context<br>Understanding of the impact of the events and of the actions required</td></tr><tr><td>Event response selected</td><td>Monitoring specialist<br>Product or service owner<br>Project manager<br>User, super-user<br>CI owner<br>Tester</td><td>TA</td><td>Understanding of the events context<br>Understanding of the impact of the events and of the actions required</td></tr><tr><td>Notifications sent, response procedure carries out</td><td>Monitoring specialist<br>Product or service owner<br>Project manager<br>User, super-user<br>CI owner<br>Tester</td><td>TCA</td><td>Understanding of the event context<br>Knowledge of the event-triggered standard operating procedures and other predefined actions<br>Knowledge of the assigned responsibilities and communication channels</td></tr><tr><td>Note: activities of the event handling processes should be automated where reasonably possible, the above roles and competencies are needed only when the respective activities cannot be automated.</td><td></td><td></td><td></td></tr><tr><td><em>Monitoring and event management review</em></td><td></td><td></td><td></td></tr><tr><td>Major events review<br>Review of filtering and correlation analysis<br>Review of service health models</td><td>Service owner<br>User<br>Delivery manager<br>Account manager<br>Monitoring specialist<br>Developer<br>Designer<br>Architect</td><td>TMA</td><td>Knowledge of service architecture and design<br>Expertise in monitoring tools<br>Knowledge of service subject matter and business processes<br>Continual improvement skills</td></tr><tr><td>Review of event response procedures and automation</td><td>Service owner<br>Delivery manager<br>Account manager<br>Monitoring specialist<br>Developer<br>Designer<br>Architect<br>Service desk manager<br>Operations manager</td><td>ATMC</td><td>Knowledge of operations and support infrastructure and organization<br>Expertise in monitoring tools<br>Expertise in automation<br>Knowledge of service subject matter and business processes<br>Continual improvement skills</td></tr><tr><td>Review of monitoring and event tools</td><td>Monitoring specialist<br>Architect<br>Business analyst<br>Technology consultant</td><td>MTA</td><td>Expertise in monitoring tools, AI, ML<br>Expertise in automation<br>Continual improvement skills</td></tr><tr><td>Review of statistical information</td><td>Monitoring specialist<br>Architect<br>Buisness analyst</td><td>MTA</td><td>Knowledge of service architecture and design<br>Expertise in monitoring tools<br>Knowledge of service subject matter and business processes<br>Continual improvement skills</td></tr></tbody></table>

## 4.2 Organizational structures and teams
It is rare that a dedicated monitoring and event management team exists in the organization. Usually, people responsible for the service delivery and operations are those involved in the monitoring.

It is important to ensure that monitoring is planned at the design stage of the service lifecycle. Therefore, people responsible for monitoring should be involved in the design phase, and teams that developed the service or component are available for service hand-over to operations and setting up the monitoring. This includes architects, software development teams, infrastructure teams, designers, teams responsible for service validation, availability, continuity, capacity, and performance, and so on.

Although it is unlikely to find a single, dedicated monitoring and event management team, it is important that the practice exists and is used consistently throughout the organization, so that stakeholders with diverse responsibilities and from different parts of the organization can collaborate on those aspects of services that cross organizational boundaries. A single set of monitoring and event management design, configuration, and procurement guidelines should be maintained to assist teams in:
* Defining the minimum levels of event that need to be tracked and how they should be monitored and reported
* Identifying existing automation activities
* Knowing when to collaborate with other stakeholders and what information they will need
* Understanding how to optimize the type and number of events that are monitored
* Defining scenarios in which combinations of events have a particular significance

Every organization will approach this task differently, but it is likely to be the responsibility of an architectural board or operations governance body. At the very least, the guidelines should be created according to the current level of integration in the organization, for example:
* If each technical team defines and automates its own monitoring and events, then guidelines should be provided by the most senior operations executive
* If technology-based services are defined and managed by a service management office, then these guidelines should be provided by the SMO
* Cross-functional teams that support a product line or value stream directly should define the monitoring and events that are relevant to them, and cascade these to each functional group to ensure that their monitoring and event management processes and tools accommodate the requirements.

# 5. Information and technology
## 5.1 Information exchange
The effectiveness of the monitoring and event management practice is based on the quality of the information used. This information includes, but is not limited to, information about:
* customers and users
* services, their architecture, and design, acceptance criteria and SLAs
* partners and suppliers, including SLA information on the services they provide
* policies and requirements which regulate service provision
* ongoing service delivery, including:  
    \- information about the current operational status of services  
    \- service warranty and utility requirements  
    \- service metrics available  
    \- CIs the service is dependent on  
    \- interdependencies of service components and their performance  
    \- information about major incidents  
    \- information about planned and ongoing changes and expected impact on service performance  
    \- availability, capacity and performance targets  
    \- teams responsible for service and components  
    \- knowledge articles about the service
* information about the status of service improvements.

This information may take various forms. The key inputs and outputs of the practice are listed in the ‘value streams and processes’ section of this guide.

## 5.2 Automation and tooling
The monitoring and event management practice can significantly benefit from automation. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to the full automation of activities where technology solutions remove the need for human intervention. Table 5.1 provides a list of the key automation supporting the practice and their most common application.

##### Table 5.1 Automation solutions for the monitoring and event management practice
<table><tbody><tr><td><strong>Automation tools</strong></td><td><strong>Application in monitoring and event management</strong></td></tr><tr><td>Workflow management and collaboration tools</td><td>Collaboration during monitoring and event management planning<br>Handling monitoring activities and event-triggered records and tasks<br>Support of collaboration between teams performing monitoring and processing events</td></tr><tr><td>Monitoring and event management tools, including native (built-in) and add-on tools for monitoring of systems, services, and business operations</td><td>Setup of monitoring scope, thresholds, health models, rule sets<br>Monitoring of components, systems, services, and business operations<br>Capturing and processing events</td></tr><tr><td>Service configuration management tools</td><td>Events correlation and impact assessment</td></tr><tr><td>Analysis and reporting tools</td><td>Event correlation and impact assessment<br>Practice measurement and reporting</td></tr><tr><td>Knowledge management tools</td><td>Retrieving, managing, and communicating information about events significance and recommended response</td></tr></tbody></table>

Detailed descriptions of how these tools support the practice’s activities are outlined in Table 5.2.  

##### Table 5.2 Details of automation of the monitoring and event management activities  
<table><tbody><tr><td><strong>Process activity</strong></td><td><strong>Means of automation</strong></td><td><strong>Key functionality</strong></td><td><strong>Impact on the effectiveness of the practice</strong></td></tr><tr><td><em>Monitoring planning process</em></td><td></td><td></td><td></td></tr><tr><td>Monitoring planning process<p>Defining what needs to be, and can be monitored</p><p>Defining types of events for the object of monitoring</p></td><td>Workflow management and collaboration tools<p>Monitoring and event management tools</p><p>Service configuration management tools</p></td><td>Visualization of service structure, dependencies, CIs, and so on.<p>Providing information on service structure and component/service interdependencies</p><p>Providing information on service SLAs and requirements</p></td><td>Medium</td></tr><tr><td>Defining the thresholds for different type of events<p>Defining a service ‘health model’ (end-to-end events)</p><p>Defining events correlations and rule sets</p></td><td>Monitoring and event management tools<p>Service configuration management tools</p></td><td>Active and reactive monitoring, event setup, data gathering, data analysis, alerting, rules setting</td><td>High</td></tr><tr><td>Defining the monitoring action plans<p>Defining the required capabilities of monitoring and event management tools</p></td><td>Monitoring and event management tools<p>Workflow management and collaboration tools</p><p>Service configuration management tools</p></td><td>ITSM tools integration (for example incidents logging based on events)<br>Notifications and communications, task creation<p>Automated scripts running</p><p>AI and ML event correlation, normal/abnormal behaviour analysis</p></td><td>High</td></tr><tr><td><em>Event handling process</em></td><td></td><td></td><td></td></tr><tr><td>Event detection<br>Event logging<br>Event filtering and correlation check (might be iterative)<br>Event classification<br>Event response selected<br>Notifications sent, response procedure carries out</td><td>Workflow management and collaboration tools<p>Monitoring and event management tools</p><p>Service configuration management tools</p><p>Knowledge management tools<br>Analysis and reporting tools</p></td><td>ITSM tools integration (for example incidents logging based on events)<p>Notifications and communications, task creation</p><p>Automated scripts running</p><p>AI and ML event correlation, normal/abnormal behaviour analysis</p><p>Reports and dashboard publishing</p></td><td>High</td></tr><tr><td><em>Monitoring and event management review</em></td><td></td><td></td><td></td></tr><tr><td>Major events review<br>Review of filtering and correlation analysis<br>Review of service health models<br>Review of event response procedures and automation<br>Review of monitoring and event tools<br>Review of statistical information</td><td>Analysis and reporting tools<br>Service configuration management tools<br>Monitoring and event management tools<br>Workflow management and collaboration tools<br>Knowledge management tools</td><td>Visualization of service structure, dependencies, CIs, etc.<p>Providing information on service structure and component/service interdependencies</p><p>Providing information on service SLAs and requirements, compliance and breaches</p><p>Providing information on major incidents<br>Reports and dashboard publishing</p><p>Notifications, chats</p><p>Analysis and assessment</p><p>Knowledge sharing</p></td><td>Medium</td></tr></tbody></table>

#### 5.2.1 Recommendations for automation of monitoring and event management
The following tips can help when applying automation to monitoring and event management:
* **Define a strategy for monitoring and event management** This should specify the tools that are used, as well as the role of the practice in supporting services and value streams, and the standard activities and criteria for each team to set up and use monitoring and event management
* **Before automating, clearly define where each CI fits relative to its context (for example services, people, other CIs, value streams, etc.)** This will ensure that any dependencies are defined, and other stakeholders can provide input into the automation if needed.
* **Some automation is configured into technology products, but it is a good rule of thumb to fully understand how to perform manual activities before automating them** This will ensure accuracy of automation and avoiding any unintended consequences resulting from operational teams defining a response that they did not fully understand.
* **Even though some teams are responsible for monitoring and managing individual CIs, monitoring should be centralized as far as possible** This minimizes the risk of events not being detected.
* **Use machine learning technology to detect patterns and anomalies accurately and quickly, even if they are not readily apparent to humans** Include the scanning and analysis of logs in this activity.
* **Rule correlation engines and robotic process automation tools are helpful in responding to known events and scenarios** Artificial intelligence tools are helpful in responding to events that have ambiguous or unknown significance. However, these tools must be ‘taught’ to accurately understand and interpret the context in which the events occur. This depends on a combination of machine learning and human input, especially regarding the significance of services, culture, and other environmental conditions.
* **Automation should be tested frequently** This will ensure that automation is still valid as the organization and its technology change.

# 6. Partners and suppliers
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of the ITIL® Foundation: ITIL 4 Edition publication for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the practice guides for supplier management.

Partners and suppliers may support the development, management, and execution of the monitoring and event management practice. The forms of support include the following:
* **Providing monitoring and event management capabilities in their technology products** A product can only meet its utility and warranty specifications if its performance can be measured and any changes in state can be detected and managed. Tuning performance and adjusting functionality to meet changing conditions is impossible without being able to detect and respond to events. Most suppliers build extensive event generation capabilities into their product’s native operating system.
* **Comprehensive documentation about their technology product’s monitoring and event management configurations and capabilities** Most suppliers provide the ability to communicate extensive information about their products, often more than will ever be needed by a single consumer. A good product should therefore include clear categorization and instructions about the meaning of each type of event and how to use it. They should also include clear documentation about how rules are defined and processed by their product; and how to integrate their product with other monitoring and event management tools to ensure that rules and responses do not conflict.
* **Instrumentation of common scenarios** Some products operate in complex environments where certain events might occur together. These combinations of events might represent a well understood scenario with a known response that is different to just responding to each event individually. These scenarios can be configured in a third-party event management tool, or may be included as standard scenarios in the product’s native operating system
* **Providing monitoring tools and/or APIs for hosted environments** Some service components run on a hosted platform or device, for example an application hosted on a cloud platform, or storage offered by an IaaS provider. Cloud service providers offer extensive event information about their environment, and many also offer monitoring tools or application programme interfaces (APIs) that integrate with their customer’s monitoring and event management tools and processes. This integration is not automatic and must be configured according to the customer’s monitoring and event management strategy and practice.
* **Performing monitoring and event management activities** Some suppliers specialize in providing monitoring and event management services for a range of service components across multiple environments (for example in-house, outsourced, and cloud).

An important consideration is the agreement concerning the access to monitoring for outsourced services and components, so that an organization has control over measurements and metrics agreed with the service provider. Also, all services that are developed by external suppliers must be designed as monitoring-enabled, which means that a designed service must be able to provide information on its performance and health.

Where organizations aim to ensure fast and effective the monitoring and event management, they usually try to agree to close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision making. Refer to the supplier management practice guide for more information on this.

# 7. Capability assessment and development
### 7.1 The practice capacity levels
  
The practice success factors described in section 2.4 cannot be developed overnight. ITIL maturity model defines the following capability levels applicable to any management practice:
**Level 1** The practice is not well organized; it is performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

**Level 2** The practice systematically achieves its purpose through a basic set of activities supported by specialized resources.

**Level 3** The practice is well defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

**Level 4** The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

**Level 5** The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level two to level five. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to the practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well defined and organized.

Figure 7.1 Design of the capability criteria:  
![Figure 7.1 Design of the capability criteria](Monitoring%20and%20event%20management%20ITIL%204%20Practice%20Guide/ITIL_Monitoring_and_Event_7_1.jpg)

This approach results in every practice having up to 30 capability criteria based on the practice PSFs and mapped to the four dimensions of service management. The number of criteria at each level differs; the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

Table 7.1 outlines the capability criteria that are defined in the ITIL maturity model for the monitoring and event management practice.

##### Table 7.1 Monitoring and event management capability criteria
<table><tbody><tr><td><strong>PSF</strong></td><td><strong>Criterion</strong></td><td><strong>Dimension</strong></td><td><strong>Capability level</strong></td></tr><tr><td>Establishing and maintaining approaches/models that describe the various types of events and monitoring capabilities needed to detect them</td><td>The approach to monitoring and event management is defined, discussed, and agreed at the relevant level of the organization</td><td>Value streams and processes</td><td>3</td></tr><tr><td></td><td>The responsibility for the approach to monitoring and event management is clearly defined</td><td>Value streams and processes</td><td>3</td></tr><tr><td></td><td>The technologies required for performing the monitoring and event management are identified and effective tools are available</td><td>Information and technology</td><td>3</td></tr><tr><td></td><td>The monitoring and event management approach is integrated with the other standards and approaches adopted by the organization</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>The effectiveness of the monitoring and event management approach is measured and reported</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>The monitoring and event management approach is regularly reviewed and continually improved</td><td>Value streams and processes</td><td>5</td></tr><tr><td>Ensuring that timely, relevant, and sufficient monitoring data is available to relevant stakeholders</td><td>The key users of the monitoring data and their requirements are identified</td><td>Value streams and processes</td><td>2</td></tr><tr><td></td><td>The monitoring data is available when needed and meets the user requirements</td><td>Information and technology</td><td>2</td></tr><tr><td></td><td>The users of the monitoring data know how to request, access, and utilize the data</td><td>Organization and people</td><td>2</td></tr><tr><td></td><td>The gathering, management, and provision of monitoring data is automated where relevant</td><td>Information and technology</td><td>3</td></tr><tr><td></td><td>The monitoring data from third-party services is available when needed</td><td>Partners and suppliers</td><td>3</td></tr><tr><td></td><td>The monitoring data is tracked and managed in an integrated information system</td><td>Information and technology</td><td>3</td></tr><tr><td></td><td>The quality of monitoring data is measured and reported</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>The quality of monitoring data is regularly reviewed and continually improved</td><td>Value streams and processes</td><td>5</td></tr><tr><td>Ensuring that events are detected, interpreted, and if need acted upon as quickly as possible</td><td>Events are usually detected immediately after they occur</td><td>Value streams and processes</td><td></td></tr><tr><td></td><td>Trends are analyzed and used to predict the event occurrence</td><td>Information and technology</td><td></td></tr><tr><td></td><td>Events detection, interpretation, and processing are automated, where relevant</td><td>Information and technology</td><td></td></tr><tr><td></td><td>Detected events are interpreted and acted upon, where relevant</td><td>Value streams and processes</td><td></td></tr><tr><td></td><td>Events in third-party services are detected and processed, where relevant</td><td>Partners and suppliers</td><td></td></tr><tr><td></td><td>Event detection and processing information is managed using an integrated information system</td><td>Information and technology</td><td></td></tr><tr><td></td><td>Event detection and processing is integrated into value streams</td><td>Value streams and processes</td><td></td></tr><tr><td></td><td>The effectiveness of event detection and processing is measured and reported</td><td>Value streams and processes</td><td></td></tr><tr><td></td><td>The effectiveness of event detection and processing is regularly reviewed and continually improved</td><td>Value streams and processes</td><td></td></tr></tbody></table>

These capability criteria can be used by organizations for self-assessment and improvement of the practice.  

## 7.2 Capability self-assessment  
The self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team in the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.  

To perform a quick self-assessment using the capability criteria, the following rules should be followed:

1.  Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
2.  If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider’s employees.
3.  If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
4.  If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met; what is missing in the organization? Why? How can it affect the business relationship? What can be done to meet the criteria that are currently missed?
5.  The same approach is applied at every next level; the practice is considered to be at the level where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.

### 7.3 Monitoring and event management capability development  
Management practices should support achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at the capability level 5. Higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but it comes with a cost; the cost of management, automation, and training, for example. To achieve optimal performance with sufficient level of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and Table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

Figure 7.2 The capability development steps and levels:  
![Figure 7.2 The capability development steps and levels](Monitoring%20and%20event%20management%20ITIL%204%20Practice%20Guide/ITIL_Monitoring_and_Event_7_2.jpg)

##### Table 7.2 The monitoring and event management capability development steps  
<table><tbody><tr><td><strong>Capability level</strong></td><td><strong>Define, agree, and implement</strong></td><td><strong>Comment for monitoring and event management</strong></td><td><strong>Chapter (for recommendations)</strong></td></tr><tr><td>2</td><td>Purpose and objectives</td><td>Key stakeholder groups</td><td>2.1</td></tr><tr><td></td><td>Scope</td><td></td><td>2.3</td></tr><tr><td></td><td>Processes and activities<p>Roles and responsibilities</p><p>Tools and procedures</p></td><td>Workflows; event handling automation; monitoring plans; including roles and responsibilities; automation and information exchange</td><td>3<br>4<br>5</td></tr><tr><td>3</td><td>Dependencies and integration</td><td>Integration in the service value streams</td><td>3.2</td></tr><tr><td></td><td></td><td>use of Integrated information system</td><td>5</td></tr><tr><td></td><td></td><td>Suppliers and other parties involved in monitoring and event management</td><td>6</td></tr><tr><td>4</td><td>Measurement and reporting</td><td>Metrics</td><td>2.5</td></tr><tr><td>5</td><td>Continual improvement</td><td>Regular review of practice and the monitoring and event management capability development</td><td>2.4, 2.5, 7</td></tr></tbody></table>

# 8. Recommendations for practice success
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:
* focus on value
* start where you are
* progress iteratively with feedback
* collaborate and promote visibility
* think and work holistically
* keep it simple and practical
* optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of ITIL Foundation: ITIL 4 Edition.

Table 8.1 outlines recommendations for the success of the monitoring and event management practice, linked to the guiding principles.

##### Table 8.1 Recommendations for the success of monitoring and event management
<table><tbody><tr><td><strong>Recommendation</strong></td><td><strong>Comments</strong></td><td><strong>ITIL guiding principles</strong></td></tr><tr><td>Establish a monitoring and event management strategy that includes the right tools and processes</td><td>Inconsistencies in approach between teams can reduce the effectiveness of monitoring and event management. A strategy helps to ensure that every team uses monitoring and event management consistently and avoids potential issues early on.</td><td>Start where you are</td></tr><tr><td>Regularly review and update your monitoring strategy to ensure that it is effective and efficient</td><td>Some events and the appropriate responses are well known, but many are new, or change as the environment changes. Continually updating the strategy ensures that the practice does not waste time monitoring events that are no longer significant, detects new types of events, and does not respond inaccurately in a changed situation.</td><td>Progress iteratively with feedback</td></tr><tr><td>Understand the purpose of the component being monitored</td><td>While it is easy to follow the administration manual to identify the most common events to be monitored, these might not be helpful in achieving specific service objectives or value stream activities</td><td>Focus on value<p>Think and work holistically</p></td></tr><tr><td>Ensure that the needs of all stakeholders involved in managing and using a service component are considered when defining events, monitoring, and reporting</td><td>Monitoring and event management should ensure that service component’s role in services and value chains are understood and that stakeholders who could benefit from knowing about events have input into defining monitoring and event management for that component.</td><td>Collaborate and promote visibility<p>Think and work holistically</p></td></tr><tr><td>Know how the significance of an event may change in different contexts, and adjust your monitoring tools and processes accordingly</td><td>Service and value streams are not static, neither is the technology that supports them. As each of these evolve, it is important keep updating the monitoring and event management appropriately.</td><td>Think and work holistically<p>Progress iteratively with feedback</p></td></tr><tr><td>Do not try to monitor events with unknown significance just in case it might be needed in future, or because a tool enables it</td><td>The sheer number of potential events that can be monitored can overwhelm operational teams. Teams should monitor only events that are significant to the effective operation of the service component, and its contribution to a service or value stream.</td><td>Keep it simple and practical<p>Focus on value</p></td></tr><tr><td>Regularly review how monitoring reports are used, and whether they achieve their anticipated outcomes</td><td>Continual fine tuning of the events that are monitored and how they are reported will ensure that unnecessary monitoring is eliminated, and any areas that have been overlooked are incorporated in future.</td><td>Progress iteratively with feedback<p>Collaborate and promote visibility</p></td></tr><tr><td>After outages or disruptions, work with other stakeholders to determine if monitoring and event management can be used to prevent recurrence or similar situations</td><td>Unforeseen disruption and new types of error cannot often be prevented by event management. But as soon as they have manifested, incorporating that knowledge into monitoring and event management can ensure that they do not recur, or at least that they are not as impactful. This requires close linkage with incident and problem management.</td><td>Collaborate and promote visibility<p>Progress iteratively with feedback</p></td></tr><tr><td>Use automation to evaluate the significance of events, and to take the appropriate response</td><td>Automation is key to an effective monitoring and event management practice, but it does not happen automatically. Continual evaluation of the practice, events, monitoring, reporting, and changes to the services and value streams provide input to how automation can benefit the practice.</td><td>Optimize and automate<p>Progress iteratively with feedback</p></td></tr></tbody></table>

# 9. Acknowledgements
PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following people.

#### Authors
Dennis Cotter

#### Reviewers
Roman Jouravlev

#### 2023 revision
David Cannon, Antonina Douannes, Peter Farenden, Adam Griffith, Kaimar Karu, Barclay Rae, Stuart Rance, Nicola Reeves
