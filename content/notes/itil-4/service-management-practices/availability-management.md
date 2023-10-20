---
title: availability management
date: 2023-10-20T00:00:00-06:00
draft: true
weight: 1
---


January 31, 2020
34 min read

ITIL
ITIL4 Practice Guides
Availability management: ITIL 4 Practice Guide
32 Likes
This document provides practical guidance for the service continuity management practice.

Table of Contents
1. 
About this document
It is split into five main sections, covering:

general information about the practice
the practice’s processes and activities and their roles in the service value chain
the organizations and people involved in the practice
the information and technology supporting the practice
considerations for partners and suppliers for the practice.
1.1 ITIL® 4 qualification scheme
Selected content of this document is examinable as a part of the following syllabus:

ITIL Specialist High-velocity IT
Please refer to the respective syllabus document for details.

2. 
General information
2.1 Purpose and description
Key message
The purpose of the availability management practice is to ensure that services deliver the agreed levels of availability to meet the needs of customers and users.

The availability management practice ensures that requirements for the availability of services and resources are understood and fulfilled efficiently and in line with the organization’s strategy and commitments. To enable this, this practice is applied throughout the organization’s product and service lifecycle, from ideation to operations.

This practice is extremely important when products and services are planned and designed; decisions made at this stage will affect availability levels and related constraints, as well as the organization’s ability to monitor and manage these aspects.

Availability is an important service characteristic from the consumers’ perspective, and therefore it is subject to negotiation, agreement, monitoring, and reporting. These activities involve multiple practices (including the business analysis, relationship management, service design, service level management (SLM), and measurement and reporting practices, among others), and the availability management practice is used in conjunction with those to ensure that availability is sufficiently and consistently addressed.

Definition: Availability
The ability of an IT service or other configuration item to perform its agreed function when required.


Theoretically, availability is simple to measure and understand; it depends on how frequently the service fails and how quickly it recovers after a failure. These characteristics are often expressed as mean time between failures (MTBF) and mean time to restore service (MTRS):

MTBF
measures how frequently the service fails. For example, on average, a service with a MTBF of four weeks fails 13 times each year.
MTRS
measures how quickly service is restored after a failure. For example, on average, a service with a MTRS of four hours will fully recover from failure in four hours.
In practice, availability is a complex characteristic. To be measured and understood, multiple measurements and agreements about how these measurements should be understood in the context of a service are needed. Availability depends on the service architecture, importance of certain service components or service actions, criteria of unavailability, service hours, and other parameters.

Availability from the perspective of a user or a group of users can be different from the availability measured from the provider’s or customer’s perspective. For example, a service that is unavailable to five users in a group of 200 will be perceived by the five as interrupted, but the agreed availability targets for the group may still be met.

The availability management practice should ensure a transparent, consistent, and practical understanding of availability (expected, agreed, designed, and actual) among all relevant parties.

When a service is provided to thousands or even millions of people, there is not usually a single generic availability agreement with customers, but the overall service availability is critical for the service provider. Such services are usually designed for high availability, where reliability (high MTBF) is balanced with fast recovery (short MTRS).

Availability is closely connected to service performance, capacity, continuity, and information security. The ITIL management practice guides that discuss these areas often address the same characteristics of configuration items and services, but focus on different aspects of their quality. These practices can significantly benefit from sharing resources of all four dimensions of service management; however, clear separation of responsibilities is required in some cases, especially in heavily regulated areas, such as service continuity and information security.

2.2 Terms and concepts
Service availability is central to business success, there is a direct correlation between service availability and customer and user satisfaction. However, it is possible to achieve customer satisfaction when services fail. The way in which a service provider reacts in a failed situation has a major influence on customer perception.

It is difficult to improve availability without understanding how the services support the consumer.

2.2.1 Vital business function
Vital business function (VBF) is a term used to reflect the part of a service that is critical to the organization’s success. A service may also support a number of business functions that are not vital.

For example, an e-mail service’s VBFs would be sending and receiving email, and accessing archived messages. The ability to access a calendar may not be vital.

This distinction between vital and non-vital functions is important and should influence availability design and associated costs. Generally, the more vital the business function, the more resilient and available it needs to be.

2.2.2 Availability for different types of services
Availability can be defined differently for different types of service offerings. For example, if the service offering:

Enables business operations (such as a loan approval process or financial reporting process), availability is normally defined in terms of the execution of business operations.
Provides access to a resource (such as network, print, or email services), availability is defined and measured in terms of resource availability.
Includes fulfilment actions (such as user support), availability is often not an applicable measure. Instead, the focus should be on timely request completion.
2.2.3 Availability criteria
Defining availability requirements for services is often complicated. A service may have multiple functions and customers, each of whom may have different availability requirements for each function.

Quite often for non-functional requirements, the line between underperformance (the service being slow, unsecure, non‑compliant, and so on) and unavailability is difficult to identify.

When defining service availability, it is essential to consider the following:

the criticality of business functions that are enabled by the service
thresholds for various forms of underperformance and unavailability; for example, delays in sending or receiving e-mail may be treated as service level degradation, not service unavailability, until they reach the agreed threshold
the number of users, business units, and/or sites that are impacted; for example, the service may only be considered unavailable if more than a certain percentage of users are impacted
whether certain vital users, business units, sites, and so on, are impacted; for example, for an e-mail service, it may be that, if users who need to communicate directly with customers and partners are able to use the service, the service is considered available
the service delivery schedule and peak hours: a service that only has outages at night or on weekends may not be considered unavailable.
These factors reflect how the service provider and customers define unavailability. It is good practice to document the agreed availability criteria for the service in a service level agreement.

2.2.4 Availability metrics
Availability is one of the most essential indicators of service quality, so service providers must be able to measure, assess, and report availability. Widely accepted practice is to report availability as a percentage, which can be calculated using a simple formula:

Availability = (agreed service time - downtime ) / agreed service time.

This formula can be useful, especially for resource provision services, but it does not reflect the business impacts of complicated service disruption scenarios.

The ideal availability metric would measure financial losses due to service unavailability. Unfortunately, it is often difficult or impossible to measure or estimate such a metric. Therefore, the service provider and the customer should define a set of acceptable metrics that reflect how the consumer loses money due to service outages, even if these metrics may be slightly inaccurate.

The following factors should be considered:

The longer the cumulative service downtime is, the higher the losses are.
The longer a single service outage is, the higher the losses are. In most cases, financial losses grow exponentially during an outage. The service provider may face fines, regulatory judgments, diminished competitive advantage, reputational damage, and so on.
The more frequent the outages are, the higher the losses are, because the expenses associated with managing a loss event and restarting business operations are high.
Availability can be measured, assessed, and reported in various ways. These include, but are not limited to, the following metrics:

MTBF
minimum time between failures
number of service disruptions
total downtime over the period
maximum single outage
MTRS.
When defining metrics to measure availability, it is crucial to reflect the business impact of service disruptions rather than the technical availability of service components.

2.2.5 Availability measurement
Availability measurements are based on accurately tracked periods of downtime. Therefore, one of the most important objectives for the availability management practice is to design and manage availability monitoring tools and translate the resulting data into meaningful service availability information.

Incident management records are a source of service disruptions data. However, availability data based on incident logs is often unreliable and difficult to align to the agreed service availability metrics.

Infrastructure monitoring tools are common sources of availability data. However, although information from these tools is useful when measuring the availability of resource provision services, it is less useful when measuring the availability of services that enable business operations. Tools such as real user monitoring and business transaction monitoring are more useful for these services.

Table 2.1 outlines the availability measurement methods further.
Availability measured method	Description
Incident records

Incident records usually include the timestamps when the incident was identified and resolved so that the duration of outage can be calculated. However, this method has limitations, including:

The incident may not be identified and recorded at the same time as the service becoming unavailable.
The incident may not be resolved, and its resolution may not be recorded, at the same time as service availability is restored.
Not all incidents are availability incidents (see section 2.2.3 for details about availability criteria).
Related incident records should be linked and the possible overlap of incidents over time should be considered in order to accurately estimate the period of downtime.

In small-scale service providers, this method of measuring availability may work well, but it is less useful in large-scale organizations due to the larger number of services and incidents.
IT infrastructure monitoring

Infrastructure monitoring tools are also sources of availability data. However, such tools measure CI availability, not service availability. Service and configuration models might be used to understand service availability based on components’ availability data.

However, this method’s limitations should be considered:

The service component outage may not cause a service outage.
Service unavailability may be caused by underperformance, as well as the outage, of components.
These issues might be overcome by developing a service health model; a model that determines how the underperformance or outage of a component impacts other components in the service model.


Developing a service health model is a time-consuming exercise that, in many cases, is not the best use of time because the IT infrastructure changes rapidly.
Business transaction monitoring/real user monitoring

Business transaction monitoring is a way of measuring the availability and performance of IT services from a business operations/transactions perspective. A variety of data collection methods might be used for the purpose, including network packet sniffing, log parsing, agent-based middleware protocol sniffing, reading database records, and others.

Two particular methods of business transaction monitoring are:

Synthetic monitoring A method for monitoring applications by simulating users’ activity. Synthetic monitoring uses simulated transactions from a robot client that mimic typical user actions.
Real user monitoring (RUM) RUM may capture server-side data in order to reconstruct end-user experience or directly monitor user interactions with the application and what users experience at the point of service consumption.
2.3 Scope
The availability management practice ensures that services deliver agreed levels of availability to meet the needs of customers and users cost-effectively. To achieve this, the practice includes the definition, measurement, analysis, and improvement of availability and provides a centre of expertise for availability matters to support other service management practices.

The scope of the availability management practice is very broad. Almost every ITIL practice contributes to service availability, directly or indirectly. Activities of other practices that are closely related to the availability management practice are listed in Table 2.2. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

Table 2.2 Activities related to the availability management practice described in other practice guides
Activity	Practice Guide 
Negotiating and agreeing customer requirements for availability

SLM

Designing availability controls as a part of the service model

Service design

Aligning availability controls with business architecture

Architecture management
Identifying risks associated with availability	Risk management
Analysing the impacts of changes on availability targets	Change enabled
Monitoring availability of services	Monitoring and event management
Justifying new availability controls	Portfolio management
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

2.3.1 The line between availability and continuity
The line between service continuity and availability management is subtle. Both of these practices involve the concept of risk and identifying and preparing for events that threaten to disable services. In both cases, an understanding of VBFs, risk assessment, and business impact analysis (BIA) of service failures is required. Ultimately, both practices ensure the organization's resistance to failures.

Some organizations prefer not to separate availability and continuity management. However, there are some differences, as is outlined in Table 2.3.

Table 2.3 The distinction between the availability management and service continuity management practices
Availability management

Service continuity management

Focuses on high-probability risks

Focuses on high-impact risks (emergencies, disasters)

More proactive

More reactive

Reduces the likelihood of unwanted events

Reduces the impacts of unwanted events

Focuses on technical solutions

Focuses on organizational measures

Focuses on optimization

Focuses on creating redundancy

Is not a part of the corporate function

Often is part of the corporate function

Business-as-usual

Force-majeure

MTRS, MTBF, mean time between

service incidents

Recovery time objective, recovery point objective

The service continuity management practice is not interested in minor or short-term failures that do not have serious impacts on the organization. It focuses on risks associated with significant damage, regardless of the likelihood of their occurrence. Often these are emergency situations; disasters such as fires, flooding, power outages, data centre or site failures, and so on. Although the availability management practice does not ignore the negative impacts of failures on the service provider and the consumer, minor interruptions of individual components are also considered in the process.

Availability planning focuses on fulfilling current and future agreed customer requirements and avoiding deviations. The availability management practice finds and eliminates single points of failure by implementing countermeasures that are generally proactive and reduce the likelihood of unwanted events. The service continuity management practice focuses on planning to manage the serious consequences of disruptive events. Service continuity management activities generally do not impact the probability of an incident occurring.

The purpose of the availability management practice is to ensure that the availability of the services provided meets the current and future agreed requirements of customers at a reasonable cost. Through optimization, practitioners try to achieve the maximum level of availability with the available resources. Continuity management activities almost always create redundancies (such as backup sites, a replacement equipment fund, external agreements, and so on) in case of an emergency. There is a tension between the objectives of the two practices.

Lastly, the availability management practice works with statistics and analyses trends, whereas the continuity management practice is concerned with how to respond to disruptive events.

2.3.2 Availability management’s role in managing service risks
The concept of risk is central to the availability management practice. In order to meet service availability targets, the practice needs information about risks, which can be provided by the risk management practice.

An effective availability management practice can therefore contribute significantly to risk management. A large proportion of risk mitigation measures are related in some way to availability controls.

Availability management generally focuses on identifying and eliminating single points of failure or unreliable or weak components, when it is cost-justifiable (see 2.4.3 for details).

2.4 Practice success factors
Definition: Practice success factor
A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The availability management practice includes the following PSFs:

identifying service availability requirements
measuring, assessing, and reporting service availability
treating service availability risks.
2.4.1 Identifying service availability requirements
To effectively manage availability, the service provider should identify the service availability requirements. These requirements should reflect how service customers may be impacted by service outages.

Identifying a service’s availability requirements may be a separate activity, but it is more commonly a part of service level negotiation within the SLM practice, or a broader BIA performed jointly with the service continuity management practice.

Identifying service availability requirements includes:

understanding customer requirements for service availability
determining availability criteria
determining availability metrics and setting targets.
2.4.1.1  Understanding customer requirements for service availability
The business analysis and SLM practices normally involve communicating with customers to understand their availability requirements for IT services and negotiate service level requirements. The availability management practice provides important support and input to the SLM, business analysis, and service design practices. Availability requirements always balance cost and quality; the availability management practice can play a key role in optimizing the availability of a service to meet increasing availability demands while deferring an increase in costs.

2.4.1.2 Determining availability criteria
The line between availability and unavailability should be clearly defined. The following factors should be considered when determining service availability criteria:

the criticality of business functions that are enabled by a service
thresholds for underperformance and complete unavailability (there may be acceptable delays that should not be considered service unavailability)
scale factor (number of users, business units, sites impacted)
certain users, business units, sites, and so on that are impacted
the service delivery schedule and peak hours.
See section 2.2.3 for more details.

2.4.1.3 Determining availability metrics and setting targets
Availability is the most crucial service quality indicator because service customers typically lose money because of service outages. Availability metrics and targets should accurately reflect how consumers are impacted by service unavailability (see section 2.2.4 for details).

2.4.2 Measuring, assessing, and reporting service availability
Service providers must be able to measure, assess, and report availability correctly. It is a widely accepted practice to report availability as a percentage, which can be calculated using a simple formula based on uptime and downtime. Although it can be suitable in many cases (especially for resource provision services), this method lacks visibility of the business impacts of complicated service disruption scenarios.

It is important to consider various ways of measuring, assessing, and reporting availability, including, but not limited to, the following metrics (see 2.2.4 for details):

MTBF
minimum time between failures
number of service disruptions
total downtime over the period
maximum single outage
MTRS.
Whichever set of metrics is suitable for a service, it is important to reflect the business impact of service disruptions, rather than the technical availability of service components.

One of the most important objectives for the availability management practice is to design and ensure sufficient availability monitoring. Then, to translate the monitoring data into meaningful service availability information.

Incident records are one obvious source of service disruptions data. However, it is often difficult to obtain reliable availability data based on incident records, especially for user-‑reported incidents. It is also difficult to align the data with agreed service availability metrics.

Infrastructure monitoring tools are more reliable sources of availability data. However, although they work well for measuring resource provision services, it is very difficult to measure the availability of services that enable business operations correctly based on infrastructure monitoring data. Tools such as real user monitoring, business transaction monitoring, and so on can help with this (see section 2.2.5).

2.4.3 Treating service availability risks
The availability management practice is not only about planning and monitoring availability. This practice includes the definition and management of controls to manage a range of risks that might impact service availability. For this, it is used in conjunction with the risk management practice and other risk-focused practices (including the service continuity management, capacity and performance management, and information security management practice). An effective availability management practice can make a significant contribution to risk management1.

The measures outlined in Table 2.4 may be designed and implemented as a part of an overall risk mitigation plan.

Table 2.4 The four dimensions of availability management
Service management dimension

Countermeasures to availability risks

Organizations and people

Developing the people’s capabilities with training

Information and technology

The exploitation of fault-tolerant technology to mask the impacts of planned or unplanned component downtime
Duplexing, or the provision of alternative IT infrastructure components, to allow one component to take over the work of another component
Improving component reliability by enhancing testing regimes
Improving software design and development
Introducing a resilient telecommunication network
Data protection in operation: RAID arrays and disk mirroring for LAN servers to prevent data loss and ensure the continued availability of data
Monitoring (to provide prompt alerts)
Partners and suppliers

Improved externally supplied services, contracts, or agreements

Value streams and processes

Improved incident management
Improved testing
Continuous integration/continuous delivery



When choosing an availability control, the effectiveness and efficiency of each option should be assessed2. It is also important to continually control and validate the effectiveness and efficiency of availability arrangements.

Effectiveness According to risk management principles, the effects of availability controls should be assessed and compared to the expected losses due to incidents.
Efficiency The costs of an availability control should also be assessed and compared to its benefits. Benefits are calculated by estimating the reduction in the likelihood of incidents after the control is implemented, then multiplying it by the severity of the impact the incidents would have if they occurred. This value should be compared in terms of cost to the cost of implementing the measure (cost benefit analysis can be used here).
It is usually cheaper to design the right level of service availability into a service from the start, rather than try and add it subsequently. Also, once a service gets a reputation for unreliability, it becomes very difficult to repair.

The following forms of loss, proposed by FAIR3, might be useful when assessing service availability risks:

productivity the reduction in a service provider’s ability to deliver services
response expenses associated with managing a loss event
replacement the intrinsic value of an asset, or the expense associated with replacing lost or damaged assets (e.g. purchasing a replacement server)
SLA fines and regulatory judgments legal or regulatory actions levied against the service provider
competitive advantage losses associated with diminished competitive advantage
reputation losses associated with an external perception of the service provider.
It is also important to understand how impacts may change over time. Losses due to service outages often grow exponentially over time. Along with losses related to the reduction in an organization’s ability to generate its primary value proposition, reputational risks and the threat of financial sanctions arise.

Agreed availability controls are implemented through service design, software development and management, and infrastructure and platform management practices.

2.5 Key metrics
The effectiveness and performance of ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to their purpose. Further guidance on metrics, key performance indicators (KPIs), and other tools that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the availability management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.5.

Table 2.5 Example metrics for the practice success factors
Practice success factors

Key metrics

Identifying service availability requirements

Percentage of products and services with clearly documented availability criteria
Percentage of (critical) products and services with availability requirements documented in an SLA
Timely updating of service availability requirements in case of service changes
Measuring, assessing, and reporting service availability

Percentage of products and services with determined availability metrics
Percentage of products and services covered by availability and performance monitoring
Percentage of products and services included in service availability reports
Treating service availability risks

MTBF achievement
Minimum time between failures achievement
Number of service disruptions achievement
Total downtime over the period achievement
Maximum service outage achievement
MTRS achievement
Percentage of effective availability controls
Ratio between actual losses and expected losses
The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the availability management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as the goals of the value streams to which the practice contributes.

3. 
Value streams and processes
3.1 Value streams contribution
Like any other ITIL management practice, the availability management practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The availability management practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which availability management contributes are:

plan
deliver and support
design and transition
obtain/build
improve.
The contribution of the availability management practice to the service value chain is shown in Figure 3.1.

Heat map image showing contribution of availability management practice to value chain activites

Figure 3.1 Heat map of the contribution of the availability management practice to value chain activities

3.2 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

Definition: Process
A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.
Availability management activities form two processes:

establishing service availability control
analysing and improving service availability.
3.2.1 Establishing service availability control
This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

Table 3.1 Inputs, activities, and outputs of the establishing service availability control process
Key inputs	Activities	Key outputs
Customer requirements
SLR drafts
Information about available resources
Identifying service availability requirements
Agreeing service availability requirements
Determining availability measurement requirements
Designing availability metrics and reports
Agreed service availability requirements
Availability measurement requirements
Availability report template(s)
Workflow diagram of the establishing service availability control processPicture2.png


Figure 3.2 Workflow for the establishing service availability control process

These activities may be performed with varying levels of formality by many people in the organization. Table 3.2 describes these activities further.

Table 3.2 Activities of the establishing service availability control process
Activity

Description

Identifying service availability requirements

The organization may have draft SLRs and service availability requirements, but they are rarely defined in a measurable and manageable way. Customers communicate their requirements for service availability based on their business needs.
The availability management practice should work with the SLM practice to clarify service availability criteria and availability indicators, which should accurately reflect the impacts of service outages on the customer (see sections 2.2.3 and 2.4.1 for details).
Service provider representatives from a customer-facing team or business-analysis team, or product and service owners, are usually involved in documenting service availability requirements.
Agreeing service availability requirements

Analysis of resource requirements may be needed to define whether fulfilling availability requirements is possible and affordable. The main output is a quote with estimated costs and a timeline for fulfilment.
This analysis should include agreements with the service provider’s suppliers and partners to ensure that they will support the required service level.
Determining availability measurement requirements

In order to analyse, report, and improve service availability, the service provider must measure it. The availability monitoring approach should be defined based on the service availability requirements, reporting policy, customer reporting requirements, type of the service, and available monitoring tools.
The main task is to define how service outages will be tracked.
Designing availability metrics and reports

Metrics should be determined based on the service availability requirements. The following availability metrics should be considered:

availability percentage
MTBF
minimum time between failures
number of service disruptions
total downtime over the period
maximum downtime
MTRS.
Whatever set of metrics is suitable for the service, is important to reflect the business impact of service disruptions, rather than the technical availability of the service components (see 2.4.2 for details).

After metrics are chosen, a report or dashboard template should be designed to display the results.

3.2. Analysing and improving service availability
This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

Table 3.3 Inputs, activities, and outputs of the analysing and improving service availability process
Key inputs

Activities

Key outputs

Monitoring data
Incident records
Service models
Availability report template(s)
Agreed service availability requirements
Risk register(s)
Service specification(s)
Service availability analysis
Reporting service availability
Planning and designing service availability
Service availability report(s)
Problem records
Availability management plan(s)
New and updated controls
These activities may be carried out with varying levels of formality by many people in the organization.

Figure 3.2 shows a workflow diagram of the process.



workflow diagram showing the analysis and improving services availability process

Figure 3.3 Workflow of the analysing and improving service availability process

Table 3.4 describes these activities further.

Table 3.4 Activities of the analysing and improving service availability process
Activity

Description

Service availability analysis

The achievement of service availability requirements must be confirmed. All deviations from pre-defined levels must be subject to investigation, and corrective action must be undertaken if a fault is found.

The availability management practice uses monitoring data, such as incident records, as inputs for the review and analysis of service availability. This analysis may be performed on different levels:

service components/IT infrastructure level: performed by the availability manager, system administrators, and engineers
service level: performed by the availability manager, service owner, and SLM manager.
Trend analysis should be performed to detect flaws that have not yet caused incidents. Problems or risks may be logged.

Because business needs and customer demand may change, the levels of availability for a service may need to be revised. Such reviews should be part of the SLM practice’s regular service reviews. Inputs from the service continuity management practice, particularly from BIAs and risk assessment exercises, should also be considered regularly.

Continually considering opportunities to optimize the availability of the IT infrastructure and services is important. The benefits of this regular-review approach are that, enhanced levels of availability, with much lower costs, may be achievable.

Reporting service availability

The service provider produces reports or dashboards demonstrating service availability achievements. These are communicated by agreed-upon channels.

Service availability reporting is usually a part of overall service quality reporting through the SLM practice4.

Planning and designing service availability

The service provider should determine an appropriate, cost-effective set of service continuity strategies. More preventive measures need to be adopted for those processes and services that have earlier and higher impacts. For services where the impacts are lower and take longer to develop, greater emphasis should be placed on recovery measures (see section 2.4.3 for details).

The availability management practice ensures that new or changed services meet the customer’s availability requirements. The work involves producing recommendations, plans, and documents on design guidelines for new and changed services. In some cases, an availability plan may be produced, which will include the following:

current availability levels
key service components
anticipated customer requirement changes
availability impacts of new requirements
recommendations of availability controls.
4. 
Organizations and people
4.1 Roles, competencies, and responsibilities
The ITIL practice guides do not describe the practice management roles, such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

Table 4.1 Competency codes and profiles
Competency code

Competency profile (activities and skills)

L

Leader Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes

A

Administrator Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements

C

Coordinator/communicator Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns

M

Methods and techniques expert Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement

T

Technical expert Providing technical (IT) expertise and conducting expertise-based assignments

Examples of roles that are involved in availability management activities are listed in Table 4.2, together with the associated competency profiles and specific skills.


Table 4.2 Examples of roles with responsibility for availability management activities
Activity

Responsible roles

Competency profile

Specific skills

Establishing service availability control

Identifying service availability requirements

Service/product owner
Relationship manager
Service designer
Customer
CTA

Business analysis
Good knowledge of the service consumer’s business
Good knowledge of the products, including their architecture and configuration
Communication and coordination
Agreeing service availability requirements

Service owner
Relationship manager
Customer
CA

Communication and negotiation
Good knowledge of the product, including its architecture and configuration
Determining availability measurement requirements

Availability manager
Monitoring tool administrator
Monitoring and event manager Service designer
Technical expert
TM

Good understanding of monitoring tools and techniques
Awareness of technology available on the market for monitoring and event management
Designing availability metrics and reports

Availability manager
Service owner
Relationship manager
IT quality manager
CM

Communication and negotiation
Report and dashboard design skills
Service availability analysis and improvement

Service availability analysis

Availability manager
Service owner
Technical expert
IT quality manager
MT

Excellent analytical skills
Knowledge of methods and techniques, such as fault-tree analysis, component failure impact analysis, and so on
Familiarity with analytical tools
Good understanding of possible business impacts due to service outages
Reporting service availability

Service owner
Relationship manager
Customer
CA

Knowledge of agreements and expectations
Understanding the consumer context
Communication and negotiation
Planning and designing service availability

Availability manager
Service designer
Technical expert
Architecture manager
TM

Good understanding of resilience options
Awareness of existing controls
Awareness of the technology available on the market
Good understanding of possible business impacts due to service outages
4.2 Organizational structures and teams
Although the role of availability manager may be supported with formal positions and job descriptions, it is unusual to see a dedicated organizational structure for the availability management practice. Service availability is managed by other practices and organizational functions. These functions are outlined in Table 4.3.

Table 4.3 Examples of availability management activities connected with other practices and organizational functions
Process

Activity

Common execution scenario

Establishing service availability control

Identifying service availability requirements

Service/product owner

Agreeing service availability requirements

May be performed as a part of the SLM practice

Determining availability measurement requirements

Monitoring tools administrator
May be performed as a part of monitoring and event management practice
Designing availability metrics and reports

Service/product owner
May be performed as a part of the SLM or measurement and reporting practices
Service availability analysis and improvement

Service availability analysis

For service components/IT infrastructure: system and infrastructure administrators
For the service level: service/product owner
Reporting service availability

Service/product owner
May be performed as a part of overall service level reporting within SLM practice
Planning and designing service availability

Performed in conjunction with the risk manager and business continuity administrator. Depending on the service lifecycle stage and organizational context, a business analyst, architecture manager, information security manager, and/or system administrator may be involved

Because availability is impacted by almost every ITIL practice, it is a good idea to appoint an availability manager who is accountable for ensuring cost‑efficient availability management. This role may be combined with the roles of service continuity administrator or IT risk manager.

5. 
Information and technology
5.1 Information exchange, inputs/outputs
The effectiveness of the availability management practice is based on the quality of the information used. This information includes, but is not limited to, information about:

consumer’s business processes
services and their architecture and design
partners and suppliers and information on the services they provide
regulatory requirements regarding service availability
technology and services available on the market that may be relevant for service availability arrangements
information about monitoring tools and techniques.
This information may take various forms. The key inputs and outputs of the practice are listed in section 3.

5.2 Automation and tooling
In some cases, the availability management practice can significantly benefit from automation (see section 3 for details). Where this is possible and effective, it may involve the solutions outlined in Table 5.1.

Table 5.1 Automation solutions for availability management activities
Process activity

Means of automation

Key functionality

Impact on the effectiveness of the practice

Establishing service availability control

Identifying service availability requirements

Service catalogue, CMDB, BPM tools, CMDB, service models, availability and capacity monitoring and management tools, and asset management tools

In order to identify VBFs of the service and availability requirements analyst should have access to information about service components and service actions. BPM tools may provide information about consumer’s processes and operations supported by the service

Very high

Agreeing service availability requirements

Contracting tools, service portals

Selection of alternative options
Communication with the service customer
Low

Determining availability measurement requirements

Designing availability metrics and reports

Reporting and dashboarding tools, service portals, and apps

Report and dashboard template design

Low to high, depending on the volume of services and stakeholders who must receive reports

Service availability analysis and improvement

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

Determining existing controls and resilience measures.
Initiation changes which should be implemented as a part of availability management plan realization.
Medium

6. 
Partners and suppliers
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the practice guides for service design, architecture management, and supplier management.

Partners and suppliers may provide critical products and service components. The service provider needs to negotiate and agree availability requirements with partners and suppliers in order to meet service availability requirements.

Partners and suppliers may also provide services and solutions for ensuring resilience, such as fault-tolerant and clustering technologies, load balancing, multi-level backup systems, monitoring tools, and so on. In these cases, they should consider service availability when designing and planning service provision.

7. 
Important reminder
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:

focus on value
start where you are
progress iteratively with feedback
collaborate and promote visibility
think and work holistically
keep it simple and practical
optimize and automate.
More information on the guiding principles and their application can be found in section 4.3 of ITIL® Foundation: ITIL 4 Edition.

8. 
Acknowledgements
Axelos Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

8.1 Authors
Pavel Demin

8.2 Reviewers
Roman Jouravlev

References
Risk management: ITIL® Practice Guide
.
For details see Risk management: ITIL® Practice Guide.
An Introduction to Factor Analysis of Information Risk (FAIR)
ftp://mail.im.tku.edu.tw/Prof_Liang/IRM/10%20An%20Introduction%20to%20Factor%20Analysis%20of%20Information%20Risk.pdf
[Accessed 24thFebruary 2020]
See the Service level management: ITIL® 4 Practice Guide for details.
