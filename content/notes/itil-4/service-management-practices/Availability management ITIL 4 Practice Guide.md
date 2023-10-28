---
title: "Availability management"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# 1. Source
Axelos International (https://www.axelos.com)

# 2. Overview
*Key message*: The purpose of the availability management practice is to ensure that services deliver the agreed levels of availability to meet the needs of customers and users.

The availability management practice ensures that requirements for the availability of services and resources are understood and fulfilled efficiently and in line with the organization’s strategy and commitments. To enable this, this practice is applied throughout the organization’s product and service lifecycle, from ideation to operations.

This practice is extremely important when products and services are planned and designed; decisions made at this stage will affect availability levels and related constraints, as well as the organization’s ability to monitor and manage these aspects.

Availability is an important service characteristic from the consumers’ perspective, and therefore it is subject to negotiation, agreement, monitoring, and reporting. These activities involve multiple practices (including the business analysis, relationship management, service design, service level management (SLM), and measurement and reporting practices, among others), and the availability management practice is used in conjunction with those to ensure that availability is sufficiently and consistently addressed.

> **Availability** — The ability of an IT service or other configuration item to perform its agreed function when required.

  
Theoretically, availability is simple to measure and understand; it depends on how frequently the service fails and how quickly it recovers after a failure. These characteristics are often expressed as mean time between failures (MTBF) and mean time to restore service (MTRS):
* **MTBF**  
    measures how frequently the service fails. For example, on average, a service with a MTBF of four weeks fails 13 times each year.
* **MTRS**  
    measures how quickly service is restored after a failure. For example, on average, a service with a MTRS of four hours will fully recover from failure in four hours.

In practice, availability is a complex characteristic. To be measured and understood, multiple measurements and agreements about how these measurements should be understood in the context of a service are needed. Availability depends on the service architecture, importance of certain service components or service actions, criteria of unavailability, service hours, and other parameters.

Availability from the perspective of a user or a group of users can be different from the availability measured from the provider’s or customer’s perspective. For example, a service that is unavailable to five users in a group of 200 will be perceived by the five as interrupted, but the agreed availability targets for the group may still be met.

The availability management practice should ensure a transparent, consistent, and practical understanding of availability (expected, agreed, designed, and actual) among all relevant parties.

When a service is provided to thousands or even millions of people, there is not usually a single generic availability agreement with customers, but the overall service availability is critical for the service provider. Such services are usually designed for high availability, where reliability (high MTBF) is balanced with fast recovery (short MTRS).

Availability is closely connected to service performance, capacity, continuity, and information security. The ITIL management practice guides that discuss these areas often address the same characteristics of configuration items and services, but focus on different aspects of their quality. These practices can significantly benefit from sharing resources of all four dimensions of service management; however, clear separation of responsibilities is required in some cases, especially in heavily regulated areas, such as service continuity and information security.

## 2.2 Terms and concepts
Service availability is central to business success, there is a direct correlation between service availability and customer and user satisfaction. However, it is possible to achieve customer satisfaction when services fail. The way in which a service provider reacts in a failed situation has a major influence on customer perception.

It is difficult to improve availability without understanding how the services support the consumer.

### 2.2.1 Vital business function
Vital business function (VBF) is a term used to reflect the part of a service that is critical to the organization’s success. A service may also support a number of business functions that are not vital.

For example, an e-mail service’s VBFs would be sending and receiving email, and accessing archived messages. The ability to access a calendar may not be vital.

This distinction between vital and non-vital functions is important and should influence availability design and associated costs. Generally, the more vital the business function, the more resilient and available it needs to be.

### 2.2.2 Availability for different types of services
Availability can be defined differently for different types of service offerings. For example, if the service offering:
* Enables business operations (such as a loan approval process or financial reporting process), availability is normally defined in terms of the execution of business operations.
* Provides access to a resource (such as network, print, or email services), availability is defined and measured in terms of resource availability.
* Includes fulfilment actions (such as user support), availability is often not an applicable measure. Instead, the focus should be on timely request completion.

### 2.2.3 Availability criteria
Defining availability requirements for services is often complicated. A service may have multiple functions and customers, each of whom may have different availability requirements for each function.

Quite often for non-functional requirements, the line between underperformance (the service being slow, unsecure, non‑compliant, and so on) and unavailability is difficult to identify.

When defining service availability, it is essential to consider the following:
* the criticality of business functions that are enabled by the service
* thresholds for various forms of underperformance and unavailability; for example, delays in sending or receiving e-mail may be treated as service level degradation, not service unavailability, until they reach the agreed threshold
* the number of users, business units, and/or sites that are impacted; for example, the service may only be considered unavailable if more than a certain percentage of users are impacted
* whether certain vital users, business units, sites, and so on, are impacted; for example, for an e-mail service, it may be that, if users who need to communicate directly with customers and partners are able to use the service, the service is considered available
* the service delivery schedule and peak hours: a service that only has outages at night or on weekends may not be considered unavailable.

These factors reflect how the service provider and customers define unavailability. It is good practice to document the agreed availability criteria for the service in a service level agreement.

### 2.2.4 Availability metrics
Availability is one of the most essential indicators of service quality, so service providers must be able to measure, assess, and report availability. Widely accepted practice is to report availability as a percentage, which can be calculated using a simple formula:

Availability = (agreed service time - downtime ) / agreed service time.

This formula can be useful, especially for resource provision services, but it does not reflect the business impacts of complicated service disruption scenarios.

The ideal availability metric would measure financial losses due to service unavailability. Unfortunately, it is often difficult or impossible to measure or estimate such a metric. Therefore, the service provider and the customer should define a set of acceptable metrics that reflect how the consumer loses money due to service outages, even if these metrics may be slightly inaccurate.

The following factors should be considered:
* The longer the cumulative service downtime is, the higher the losses are.
* The longer a single service outage is, the higher the losses are. In most cases, financial losses grow exponentially during an outage. The service provider may face fines, regulatory judgments, diminished competitive advantage, reputational damage, and so on.
* The more frequent the outages are, the higher the losses are, because the expenses associated with managing a loss event and restarting business operations are high.

Availability can be measured, assessed, and reported in various ways. These include, but are not limited to, the following metrics:
* MTBF
* minimum time between failures
* number of service disruptions
* total downtime over the period
* maximum single outage
* MTRS.

When defining metrics to measure availability, it is crucial to reflect the business impact of service disruptions rather than the technical availability of service components.

### 2.2.5 Availability measurement  
Availability measurements are based on accurately tracked periods of downtime. Therefore, one of the most important objectives for the availability management practice is to design and manage availability monitoring tools and translate the resulting data into meaningful service availability information.

Incident management records are a source of service disruptions data. However, availability data based on incident logs is often unreliable and difficult to align to the agreed service availability metrics.

Infrastructure monitoring tools are common sources of availability data. However, although information from these tools is useful when measuring the availability of resource provision services, it is less useful when measuring the availability of services that enable business operations. Tools such as real user monitoring and business transaction monitoring are more useful for these services.

### Table 2.1 outlines the availability measurement methods further.
| Availability measured method | Description
Incident records
Incident records usually include the timestamps when the incident was identified and resolved so that the duration of outage can be calculated. However, this method has limitations, including:
* The incident may not be identified and recorded at the same time as the service becoming unavailable.
* The incident may not be resolved, and its resolution may not be recorded, at the same time as service availability is restored.
* Not all incidents are availability incidents (see section 2.2.3 for details about availability criteria).
* Related incident records should be linked and the possible overlap of incidents over time should be considered in order to accurately estimate the period of downtime.

  
In small-scale service providers, this method of measuring availability may work well, but it is less useful in large-scale organizations due to the larger number of services and incidents. |

IT infrastructure monitoring
Infrastructure monitoring tools are also sources of availability data. However, such tools measure CI availability, not service availability. Service and configuration models might be used to understand service availability based on components’ availability data.

However, this method’s limitations should be considered:
* The service component outage may not cause a service outage.
* Service unavailability may be caused by underperformance, as well as the outage, of components.

These issues might be overcome by developing a service health model; a model that determines how the underperformance or outage of a component impacts other components in the service model.

  
Developing a service health model is a time-consuming exercise that, in many cases, is not the best use of time because the IT infrastructure changes rapidly. |

Business transaction monitoring/real user monitoring
Business transaction monitoring is a way of measuring the availability and performance of IT services from a business operations/transactions perspective. A variety of data collection methods might be used for the purpose, including network packet sniffing, log parsing, agent-based middleware protocol sniffing, reading database records, and others.

Two particular methods of business transaction monitoring are:
* **Synthetic monitoring** A method for monitoring applications by simulating users’ activity. Synthetic monitoring uses simulated transactions from a robot client that mimic typical user actions.
* **Real user monitoring (RUM)** RUM may capture server-side data in order to reconstruct end-user experience or directly monitor user interactions with the application and what users experience at the point of service consumption.

## 2.3 Scope
The availability management practice ensures that services deliver agreed levels of availability to meet the needs of customers and users cost-effectively. To achieve this, the practice includes the definition, measurement, analysis, and improvement of availability and provides a centre of expertise for availability matters to support other service management practices.

The scope of the availability management practice is very broad. Almost every ITIL practice contributes to service availability, directly or indirectly. Activities of other practices that are closely related to the availability management practice are listed in Table 2.2. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

### Table 2.2 Activities related to the availability management practice described in other practice guides
| **Activity** | **Practice Guide** 
Negotiating and agreeing customer requirements for availability
SLM
Designing availability controls as a part of the service model
Service design
Aligning availability controls with business architecture

 | Architecture management |
| Identifying risks associated with availability | Risk management |
| Analysing the impacts of changes on availability targets | Change enabled |
| Monitoring availability of services | Monitoring and event management |
| Justifying new availability controls | Portfolio management |

Implementing risk mitigation measures  
Changing the IT infrastructure to improve availability
Project management, change enablement
Testing availability controls during the service transition
Service validation and testing
Reacting to events which might affect the organization’s ability to meet availability targets

  
Managing availability incidents 
Incident management, monitoring and event management
Managing and implementing improvements on an ongoing basis
Continual improvement

### 2.3.1 The line between availability and continuity
The line between service continuity and availability management is subtle. Both of these practices involve the concept of risk and identifying and preparing for events that threaten to disable services. In both cases, an understanding of VBFs, risk assessment, and business impact analysis (BIA) of service failures is required. Ultimately, both practices ensure the organization's resistance to failures.

Some organizations prefer not to separate availability and continuity management. However, there are some differences, as is outlined in Table 2.3.

### Table 2.3 The distinction between the availability management and service continuity management practices
<table><tbody><tr><td><p><strong>Availability management</strong></p></td><td><p><strong>Service continuity management</strong></p></td></tr><tr><td><p>Focuses on high-probability risks</p></td><td><p>Focuses on high-impact risks (emergencies, disasters)</p></td></tr><tr><td><p>More proactive</p></td><td><p>More reactive</p></td></tr><tr><td><p>Reduces the likelihood of unwanted events</p></td><td><p>Reduces the impacts of unwanted events</p></td></tr><tr><td><p>Focuses on technical solutions</p></td><td><p>Focuses on organizational measures</p></td></tr><tr><td><p>Focuses on optimization</p></td><td><p>Focuses on creating redundancy</p></td></tr><tr><td><p>Is not a part of the corporate function</p></td><td><p>Often is part of the corporate function</p></td></tr><tr><td><p>Business-as-usual</p></td><td><p>Force-majeure</p></td></tr><tr><td><p>MTRS, MTBF, mean time between</p><p>service incidents</p></td><td><p>Recovery time objective, recovery point objective</p></td></tr></tbody></table>

The service continuity management practice is not interested in minor or short-term failures that do not have serious impacts on the organization. It focuses on risks associated with significant damage, regardless of the likelihood of their occurrence. Often these are emergency situations; disasters such as fires, flooding, power outages, data centre or site failures, and so on. Although the availability management practice does not ignore the negative impacts of failures on the service provider and the consumer, minor interruptions of individual components are also considered in the process.

Availability planning focuses on fulfilling current and future agreed customer requirements and avoiding deviations. The availability management practice finds and eliminates single points of failure by implementing countermeasures that are generally proactive and reduce the likelihood of unwanted events. The service continuity management practice focuses on planning to manage the serious consequences of disruptive events. Service continuity management activities generally do not impact the probability of an incident occurring.

The purpose of the availability management practice is to ensure that the availability of the services provided meets the current and future agreed requirements of customers at a reasonable cost. Through optimization, practitioners try to achieve the maximum level of availability with the available resources. Continuity management activities almost always create redundancies (such as backup sites, a replacement equipment fund, external agreements, and so on) in case of an emergency. There is a tension between the objectives of the two practices.

Lastly, the availability management practice works with statistics and analyzes trends, whereas the continuity management practice is concerned with how to respond to disruptive events.

### 2.3.2 Availability management’s role in managing service risks
The concept of risk is central to the availability management practice. In order to meet service availability targets, the practice needs information about risks, which can be provided by the risk management practice.

An effective availability management practice can therefore contribute significantly to risk management. A large proportion of risk mitigation measures are related in some way to availability controls.

Availability management generally focuses on identifying and eliminating single points of failure or unreliable or weak components, when it is cost-justifiable (see 2.4.3 for details).

## 2.4 Practice success factors
> **Practice success factor** — A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The availability management practice includes the following PSFs:
* identifying service availability requirements
* measuring, assessing, and reporting service availability
* treating service availability risks.

### 2.4.1 Identifying service availability requirements
To effectively manage availability, the service provider should identify the service availability requirements. These requirements should reflect how service customers may be impacted by service outages.

Identifying a service’s availability requirements may be a separate activity, but it is more commonly a part of service level negotiation within the SLM practice, or a broader BIA performed jointly with the service continuity management practice.

Identifying service availability requirements includes:
* understanding customer requirements for service availability
* determining availability criteria
* determining availability metrics and setting targets.

### 2.4.1.1  Understanding customer requirements for service availability
The business analysis and SLM practices normally involve communicating with customers to understand their availability requirements for IT services and negotiate service level requirements. The availability management practice provides important support and input to the SLM, business analysis, and service design practices. Availability requirements always balance cost and quality; the availability management practice can play a key role in optimizing the availability of a service to meet increasing availability demands while deferring an increase in costs.

### 2.4.1.2 Determining availability criteria
The line between availability and unavailability should be clearly defined. The following factors should be considered when determining service availability criteria:
* the criticality of business functions that are enabled by a service
* thresholds for underperformance and complete unavailability (there may be acceptable delays that should not be considered service unavailability)
* scale factor (number of users, business units, sites impacted)
* certain users, business units, sites, and so on that are impacted
* the service delivery schedule and peak hours.

See section 2.2.3 for more details.

### 2.4.1.3 Determining availability metrics and setting targets
Availability is the most crucial service quality indicator because service customers typically lose money because of service outages. Availability metrics and targets should accurately reflect how consumers are impacted by service unavailability (see section 2.2.4 for details).

### 2.4.2 Measuring, assessing, and reporting service availability
Service providers must be able to measure, assess, and report availability correctly. It is a widely accepted practice to report availability as a percentage, which can be calculated using a simple formula based on uptime and downtime. Although it can be suitable in many cases (especially for resource provision services), this method lacks visibility of the business impacts of complicated service disruption scenarios.

It is important to consider various ways of measuring, assessing, and reporting availability, including, but not limited to, the following metrics (see 2.2.4 for details):
* MTBF
* minimum time between failures
* number of service disruptions
* total downtime over the period
* maximum single outage
* MTRS.

Whichever set of metrics is suitable for a service, it is important to reflect the business impact of service disruptions, rather than the technical availability of service components.

One of the most important objectives for the availability management practice is to design and ensure sufficient availability monitoring. Then, to translate the monitoring data into meaningful service availability information.

Incident records are one obvious source of service disruptions data. However, it is often difficult to obtain reliable availability data based on incident records, especially for user-‑reported incidents. It is also difficult to align the data with agreed service availability metrics.

Infrastructure monitoring tools are more reliable sources of availability data. However, although they work well for measuring resource provision services, it is very difficult to measure the availability of services that enable business operations correctly based on infrastructure monitoring data. Tools such as real user monitoring, business transaction monitoring, and so on can help with this (see section 2.2.5).

### 2.4.3 Treating service availability risks
The availability management practice is not only about planning and monitoring availability. This practice includes the definition and management of controls to manage a range of risks that might impact service availability. For this, it is used in conjunction with the risk management practice and other risk-focused practices (including the service continuity management, capacity and performance management, and information security management practice). An effective availability management practice can make a significant contribution to risk management<sup>1</sup>.

The measures outlined in Table 2.4 may be designed and implemented as a part of an overall risk mitigation plan.

### Table 2.4 The four dimensions of availability management
<table><tbody><tr><td><p><strong>Service management dimension</strong></p></td><td><p><strong>Countermeasures to availability risks</strong></p></td></tr><tr><td><p>Organizations and people</p></td><td><p>Developing the people’s capabilities with training</p></td></tr><tr><td><p>Information and technology</p></td><td><ul><li>The exploitation of fault-tolerant technology to mask the impacts of planned or unplanned component downtime</li><li>Duplexing, or the provision of alternative IT infrastructure components, to allow one component to take over the work of another component</li><li>Improving component reliability by enhancing testing regimes</li><li>Improving software design and development</li><li>Introducing a resilient telecommunication network</li><li>Data protection in operation: RAID arrays and disk mirroring for LAN servers to prevent data loss and ensure the continued availability of data</li><li>Monitoring (to provide prompt alerts)</li></ul></td></tr><tr><td><p>Partners and suppliers</p></td><td><p>Improved externally supplied services, contracts, or agreements</p></td></tr><tr><td><p>Value streams and processes</p></td><td><ul><li>Improved incident management</li><li>Improved testing</li><li>Continuous integration/continuous delivery</li></ul></td></tr></tbody></table>

When choosing an availability control, the effectiveness and efficiency of each option should be assessed<sup>2</sup>. It is also important to continually control and validate the effectiveness and efficiency of availability arrangements.

* **Effectiveness** According to risk management principles, the effects of availability controls should be assessed and compared to the expected losses due to incidents.
* **Efficiency** The costs of an availability control should also be assessed and compared to its benefits. Benefits are calculated by estimating the reduction in the likelihood of incidents after the control is implemented, then multiplying it by the severity of the impact the incidents would have if they occurred. This value should be compared in terms of cost to the cost of implementing the measure (cost benefit analysis can be used here).

It is usually cheaper to design the right level of service availability into a service from the start, rather than try and add it subsequently. Also, once a service gets a reputation for unreliability, it becomes very difficult to repair.

The following forms of loss, proposed by FAIR<sup>3</sup>, might be useful when assessing service availability risks:
* **productivity** the reduction in a service provider’s ability to deliver services
* **response** expenses associated with managing a loss event
* **replacement** the intrinsic value of an asset, or the expense associated with replacing lost or damaged assets (e.g. purchasing a replacement server)
* **SLA fines and regulatory judgments** legal or regulatory actions levied against the service provider
* **competitive advantage** losses associated with diminished competitive advantage
* **reputation** losses associated with an external perception of the service provider.

It is also important to understand how impacts may change over time. Losses due to service outages often grow exponentially over time. Along with losses related to the reduction in an organization’s ability to generate its primary value proposition, reputational risks and the threat of financial sanctions arise.

Agreed availability controls are implemented through service design, software development and management, and infrastructure and platform management practices.

## 2.5 Key metrics
The effectiveness and performance of ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to their purpose. Further guidance on metrics, key performance indicators (KPIs), and other tools that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the availability management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.5.

#### Table 2.5 Example metrics for the practice success factors
<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Identifying service availability requirements</p></td><td><ul><li>Percentage of products and services with clearly documented availability criteria</li><li>Percentage of (critical) products and services with availability requirements documented in an SLA</li><li>Timely updating of service availability requirements in case of service changes</li></ul></td></tr><tr><td><p>Measuring, assessing, and reporting service availability</p></td><td><ul><li>Percentage of products and services with determined availability metrics</li><li>Percentage of products and services covered by availability and performance monitoring</li><li>Percentage of products and services included in service availability reports</li></ul></td></tr><tr><td><p>Treating service availability risks</p></td><td><ul><li>MTBF achievement</li><li>Minimum time between failures achievement</li><li>Number of service disruptions achievement</li><li>Total downtime over the period achievement</li><li>Maximum service outage achievement</li><li>MTRS achievement</li><li>Percentage of effective availability controls</li><li>Ratio between actual losses and expected losses</li></ul></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the availability management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as the goals of the value streams to which the practice contributes.

## 3.1 Value streams contribution
Like any other ITIL management practice, the availability management practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The availability management practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which availability management contributes are:
* plan
* deliver and support
* design and transition
* obtain/build
* improve.

The contribution of the availability management practice to the service value chain is shown in Figure 3.1.

![Heat map image showing contribution of availability management practice to value chain activites](Availability%20management%20ITIL%204%20Practice%20Guide/Picture1.png "Figure 3.1 Heat map of the contribution of the availability management practice to value chain activities**")

## 3.2 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

> **Process** — A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.

Availability management activities form two processes:
* establishing service availability control
* analysing and improving service availability.

### 3.2.1 Establishing service availability control
This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

### Table 3.1 Inputs, activities, and outputs of the establishing service availability control process
<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td><ul><li>Customer requirements</li><li>SLR drafts</li><li>Information about available resources</li></ul></td><td><ul><li>Identifying service availability requirements</li><li>Agreeing service availability requirements</li><li>Determining availability measurement requirements</li><li>Designing availability metrics and reports</li></ul></td><td><ul><li>Agreed service availability requirements</li><li>Availability measurement requirements</li><li>Availability report template(s)<br></li></ul></td></tr></tbody></table>

![Workflow diagram of the establishing service availability control processPicture2.png](Availability%20management%20ITIL%204%20Practice%20Guide/Picture2.png)

  
**Figure 3.2 Workflow for the establishing service availability control process**

These activities may be performed with varying levels of formality by many people in the organization. Table 3.2 describes these activities further.

### Table 3.2 Activities of the establishing service availability control process
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Identifying service availability requirements</p></td><td><ul><li>The organization may have draft SLRs and service availability requirements, but they are rarely defined in a measurable and manageable way. Customers communicate their requirements for service availability based on their business needs.</li><li>The availability management practice should work with the SLM practice to clarify service availability criteria and availability indicators, which should accurately reflect the impacts of service outages on the customer (see sections 2.2.3 and 2.4.1 for details).</li><li>Service provider representatives from a customer-facing team or business-analysis team, or product and service owners, are usually involved in documenting service availability requirements.</li></ul></td></tr><tr><td><p>Agreeing service availability requirements</p></td><td><ul><li>Analysis of resource requirements may be needed to define whether fulfilling availability requirements is possible and affordable. The main output is a quote with estimated costs and a timeline for fulfilment.</li><li>This analysis should include agreements with the service provider’s suppliers and partners to ensure that they will support the required service level.</li></ul></td></tr><tr><td><p>Determining availability measurement requirements</p></td><td><ul><li>In order to analyze, report, and improve service availability, the service provider must measure it. The availability monitoring approach should be defined based on the service availability requirements, reporting policy, customer reporting requirements, type of the service, and available monitoring tools.</li><li>The main task is to define how service outages will be tracked.</li></ul></td></tr><tr><td><p>Designing availability metrics and reports</p></td><td><p>Metrics should be determined based on the service availability requirements. The following availability metrics should be considered:</p><ul><li>availability percentage</li><li>MTBF</li><li>minimum time between failures</li><li>number of service disruptions</li><li>total downtime over the period</li><li>maximum downtime</li><li>MTRS.</li></ul><p>Whatever set of metrics is suitable for the service, is important to reflect the business impact of service disruptions, rather than the technical availability of the service components (see 2.4.2 for details).</p><p>After metrics are chosen, a report or dashboard template should be designed to display the results.</p></td></tr></tbody></table>

## 3.2. Analysing and improving service availability
This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

#### Table 3.3 Inputs, activities, and outputs of the analysing and improving service availability process
<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Monitoring data</li><li>Incident records</li><li>Service models</li><li>Availability report template(s)</li><li>Agreed service availability requirements</li><li>Risk register(s)</li><li>Service specification(s)</li></ul></td><td><ul><li>Service availability analysis</li><li>Reporting service availability</li><li>Planning and designing service availability</li></ul></td><td><ul><li>Service availability report(s)</li><li>Problem records</li><li>Availability management plan(s)</li><li>New and updated controls</li></ul></td></tr></tbody></table>

These activities may be carried out with varying levels of formality by many people in the organization.

Figure 3.2 shows a workflow diagram of the process.

![workflow diagram showing the analysis and improving services availability process](Availability%20management%20ITIL%204%20Practice%20Guide/Picture3.png "Figure 3.3 Workflow of the analysing and improving service availability process**")

Table 3.4 describes these activities further.

### Table 3.4 Activities of the analysing and improving service availability process
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Service availability analysis</p></td><td><p>The achievement of service availability requirements must be confirmed. All deviations from pre-defined levels must be subject to investigation, and corrective action must be undertaken if a fault is found.</p><p>The availability management practice uses monitoring data, such as incident records, as inputs for the review and analysis of service availability. This analysis may be performed on different levels:</p><ul><li>service components/IT infrastructure level: performed by the availability manager, system administrators, and engineers</li><li>service level: performed by the availability manager, service owner, and SLM manager.</li></ul><p>Trend analysis should be performed to detect flaws that have not yet caused incidents. Problems or risks may be logged.</p><p>Because business needs and customer demand may change, the levels of availability for a service may need to be revised. Such reviews should be part of the SLM practice’s regular service reviews. Inputs from the service continuity management practice, particularly from BIAs and risk assessment exercises, should also be considered regularly.</p><p>Continually considering opportunities to optimize the availability of the IT infrastructure and services is important. The benefits of this regular-review approach are that, enhanced levels of availability, with much lower costs, may be achievable.</p></td></tr><tr><td><p>Reporting service availability</p></td><td><p><sup><sub>The service provider produces reports or dashboards demonstrating service availability achievements. These are communicated by agreed-upon channels.</sub></sup></p><p><sup><sub>Service availability reporting is usually a part of overall service quality reporting through the SLM practice</sub></sup><sup>4</sup><sup><sub>.</sub></sup></p></td></tr><tr><td><p>Planning and designing service availability</p></td><td><p>The service provider should determine an appropriate, cost-effective set of service continuity strategies. More preventive measures need to be adopted for those processes and services that have earlier and higher impacts. For services where the impacts are lower and take longer to develop, greater emphasis should be placed on recovery measures (see section 2.4.3 for details).</p><p>The availability management practice ensures that new or changed services meet the customer’s availability requirements. The work involves producing recommendations, plans, and documents on design guidelines for new and changed services. In some cases, an availability plan may be produced, which will include the following:</p><ul><li>current availability levels</li><li>key service components</li><li>anticipated customer requirement changes</li><li>availability impacts of new requirements</li><li>recommendations of availability controls.</li></ul></td></tr></tbody></table>

## 4.1 Roles, competencies, and responsibilities
The ITIL practice guides do not describe the practice management roles, such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

### Table 4.1 Competency codes and profiles
<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p><strong>L</strong></p></td><td><p><strong>Leader </strong>Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p><strong>A</strong></p></td><td><p><strong>Administrator </strong>Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p><strong>C</strong></p></td><td><p><strong>Coordinator/communicator </strong>Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p><strong>M</strong></p></td><td><p><strong>Methods and techniques expert </strong>Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p><strong>T</strong></p></td><td><p><strong>Technical expert </strong>Providing technical (IT) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

Examples of roles that are involved in availability management activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

  

### Table 4.2 Examples of roles with responsibility for availability management activities
<table><tbody><tr><td><p>A<strong>ctivity</strong></p></td><td><p><strong>Responsible roles</strong></p></td><td><p><strong>Competency profile</strong></p></td><td><p><strong>Specific skills</strong></p></td></tr><tr><td><p>Establishing service availability control</p></td></tr><tr><td><p>Identifying service availability requirements</p></td><td><ul><li>Service/product owner</li><li>Relationship manager</li><li>Service designer</li><li>Customer</li></ul></td><td><p>CTA</p></td><td><ul><li>Business analysis</li><li>Good knowledge of the service consumer’s business</li><li>Good knowledge of the products, including their architecture and configuration</li><li>Communication and coordination</li></ul></td></tr><tr><td><p>Agreeing service availability requirements</p></td><td><ul><li>Service owner</li><li>Relationship manager</li><li>Customer</li></ul></td><td><p>CA</p></td><td><ul><li>Communication and negotiation</li><li>Good knowledge of the product, including its architecture and configuration</li></ul></td></tr><tr><td><p>Determining availability measurement requirements</p></td><td><ul><li>Availability manager</li><li>Monitoring tool administrator</li><li>Monitoring and event manager Service designer</li><li>Technical expert</li></ul></td><td><p>TM</p></td><td><ul><li>Good understanding of monitoring tools and techniques</li><li>Awareness of technology available on the market for monitoring and event management</li></ul></td></tr><tr><td><p>Designing availability metrics and reports</p></td><td><ul><li>Availability manager</li><li>Service owner<br>Relationship manager</li><li>IT quality manager</li></ul></td><td><p>CM</p></td><td><ul><li>Communication and negotiation</li><li>Report and dashboard design skills</li></ul></td></tr><tr><td><p>Service availability analysis and improvement</p></td></tr><tr><td><p>Service availability analysis</p></td><td><ul><li>Availability manager</li><li>Service owner</li><li>Technical expert</li><li>IT quality manager</li></ul></td><td><p>MT</p></td><td><ul><li>Excellent analytical skills</li><li>Knowledge of methods and techniques, such as fault-tree analysis, component failure impact analysis, and so on</li><li>Familiarity with analytical tools</li><li>Good understanding of possible business impacts due to service outages</li></ul></td></tr><tr><td><p>Reporting service availability</p></td><td><ul><li>Service owner</li><li>Relationship manager</li><li>Customer</li></ul></td><td><p>CA</p></td><td><ul><li>Knowledge of agreements and expectations</li><li>Understanding the consumer context</li><li>Communication and negotiation</li></ul></td></tr><tr><td><p>Planning and designing service availability</p></td><td><ul><li>Availability manager</li><li>Service designer</li><li>Technical expert</li><li>Architecture manager</li></ul></td><td><p>TM</p></td><td><ul><li>Good understanding of resilience options</li><li>Awareness of existing controls</li><li>Awareness of the technology available on the market</li><li>Good understanding of possible business impacts due to service outages</li></ul></td></tr></tbody></table>

## 4.2 Organizational structures and teams
Although the role of availability manager may be supported with formal positions and job descriptions, it is unusual to see a dedicated organizational structure for the availability management practice. Service availability is managed by other practices and organizational functions. These functions are outlined in Table 4.3.

### Table 4.3 Examples of availability management activities connected with other practices and organizational functions
<table><tbody><tr><td><p><strong>Process</strong></p></td><td><p><strong>Activity</strong></p></td><td><p><strong>Common execution scenario</strong></p></td></tr><tr><td><p>Establishing service availability control</p></td><td><p>Identifying service availability requirements</p></td><td><p>Service/product owner</p></td></tr><tr><td></td><td><p>Agreeing service availability requirements</p></td><td><p>May be performed as a part of the SLM practice</p></td></tr><tr><td></td><td><p>Determining availability measurement requirements</p></td><td><ul><li>Monitoring tools administrator</li><li>May be performed as a part of monitoring and event management practice</li></ul></td></tr><tr><td></td><td><p>Designing availability metrics and reports</p></td><td><ul><li>Service/product owner</li><li>May be performed as a part of the SLM or measurement and reporting practices</li></ul></td></tr><tr><td><p>Service availability analysis and improvement</p></td><td><p>Service availability analysis</p></td><td><ul><li>For service components/IT infrastructure: system and infrastructure administrators</li><li>For the service level: service/product owner</li></ul></td></tr><tr><td></td><td><p>Reporting service availability</p></td><td><ul><li>Service/product owner</li><li>May be performed as a part of overall service level reporting within SLM practice</li></ul></td></tr><tr><td></td><td><p>Planning and designing service availability</p></td><td><p>Performed in conjunction with the risk manager and business continuity administrator. Depending on the service lifecycle stage and organizational context, a business analyst, architecture manager, information security manager, and/or system administrator may be involved</p></td></tr></tbody></table>

Because availability is impacted by almost every ITIL practice, it is a good idea to appoint an availability manager who is accountable for ensuring cost‑efficient availability management. This role may be combined with the roles of service continuity administrator or IT risk manager.

### 5.1 Information exchange, inputs/outputs
The effectiveness of the availability management practice is based on the quality of the information used. This information includes, but is not limited to, information about:
* consumer’s business processes
* services and their architecture and design
* partners and suppliers and information on the services they provide
* regulatory requirements regarding service availability
* technology and services available on the market that may be relevant for service availability arrangements
* information about monitoring tools and techniques.

This information may take various forms. The key inputs and outputs of the practice are listed in section 3.

### 5.2 Automation and tooling
In some cases, the availability management practice can significantly benefit from automation (see section 3 for details). Where this is possible and effective, it may involve the solutions outlined in Table 5.1.

### Table 5.1 Automation solutions for availability management activities
**Process activity**
**Means of automation**
**Key functionality**
**Impact on the effectiveness of the practice**

 |  |
| --- | --- | --- | --- | --- |

Establishing service availability control

 |  |

Identifying service availability requirements
Service catalogue, CMDB, BPM tools, CMDB, service models, availability and capacity monitoring and management tools, and asset management tools
In order to identify VBFs of the service and availability requirements analyst should have access to information about service components and service actions. BPM tools may provide information about consumer’s processes and operations supported by the service
Very high
Agreeing service availability requirements
Contracting tools, service portals
* Selection of alternative options
* Communication with the service customer
Low
Determining availability measurement requirements

___

Designing availability metrics and reports
Reporting and dashboarding tools, service portals, and apps
Report and dashboard template design
Low to high, depending on the volume of services and stakeholders who must receive reports
Service availability analysis and improvement

 |  |

Service availability analysis
Infrastructure and application monitoring and reporting tools, built-in user behaviour monitoring tools, dashboarding and reporting tools, advanced analytics tools
Collection of system and service health data, processing and analysis, dashboard and report design and presentation
High
Reporting service availability
Reporting and dashboarding tools, service portals and apps, email, other communication tools, and social media
Report presentation
Low to high, depending on the volume of services and stakeholders who must receive reports
Planning and designing service availability
Architecture management tools, CMDB, change initiation and control tools
* Determining existing controls and resilience measures.
* Initiation changes which should be implemented as a part of availability management plan realization.
Medium

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of *ITIL Foundation: ITIL 4 Edition* for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the practice guides for service design, architecture management, and supplier management.

Partners and suppliers may provide critical products and service components. The service provider needs to negotiate and agree availability requirements with partners and suppliers in order to meet service availability requirements.

Partners and suppliers may also provide services and solutions for ensuring resilience, such as fault-tolerant and clustering technologies, load balancing, multi-level backup systems, monitoring tools, and so on. In these cases, they should consider service availability when designing and planning service provision.

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:
* focus on value
* start where you are
* progress iteratively with feedback
* collaborate and promote visibility
* think and work holistically
* keep it simple and practical
* optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of *ITIL® Foundation: ITIL 4 Edition*.

Axelos Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

## 8.1 Authors
Pavel Demin

## 8.2 Reviewers
Roman Jouravlev

## References
1.  *Risk management: ITIL® Practice Guide*.
2.  For details see Risk management: ITIL® Practice Guide.
3.  An Introduction to Factor Analysis of Information Risk (FAIR)[ftp://mail.im.tku.edu.tw/Prof_Liang/IRM/10%20An%20Introduction%20to%20Factor%20Analysis%20of%20Information%20Risk.pdf](ftp://mail.im.tku.edu.tw/Prof_Liang/IRM/10%20An%20Introduction%20to%20Factor%20Analysis%20of%20Information%20Risk.pdf)(Accessed 24thFebruary 2020)
4.  See the Service level management: ITIL® 4 Practice Guide for details.
