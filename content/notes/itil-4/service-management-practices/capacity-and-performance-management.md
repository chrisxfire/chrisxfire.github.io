---
title: capacity and performance management
date: 2023-10-20T00:00:00-06:00
draft: true
weight: 1
---


February 23, 2020
27 min read

ITIL
ITIL4 Practice Guides
Capacity and performance management: ITIL 4 Practice Guide
46 Likes
This document provides practical guidance for the capacity and performance management practice.

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
Selected content from this document is examinable as a part of the following syllabus:

ITIL Specialist High-velocity IT.
Please refer to the relevant syllabus document for details.

2. 
General information
2.1 Purpose and description
Key message
The purpose of the capacity and performance management practice is to ensure that services achieve the agreed and expected levels of performance and satisfy current and future demand in a cost-effective way.

The capacity and performance management practice usually covers service performance and the performance of the resources which support services, such as infrastructure, applications, and third-party services. In many organizations, this practice also covers the capacity and performance of staff, especially when staff are directly involved in service transactions.

This practice ensures that the requirements for the capacity and performance of services and resources are understood and fulfilled efficiently, in line with the organization’s strategy and commitments. To achieve this, the practice is applied throughout the organization’s product and service lifecycle, from ideation to operations. This practice is extremely important when products and services are planned and designed; decisions made at these stages will affect performance-level and other constraints, as well as the organization’s ability to monitor and manage these aspects.

Capacity and performance are closely connected to service availability, continuity, information security, and the respective practices. These practices often address the same characteristics of CIs and services but focus on different aspects of their quality. Sharing resources across all four dimensions of service management can be significantly beneficial in these areas. However, a clear separation of responsibilities is required in some areas, such as externally regulated areas like service continuity and information security.

2.2 Terms and concepts
Definition: Performance
A measure of what is achieved or delivered by a system, person, team, practice, or service.

Service performance is usually associated with the rate of service transactions and the time needed to fulfil service transactions at a given level of demand. Service performance depends on service capacity; the maximum throughput that a configuration item (CI) or service can deliver. The specific metrics that are used will depend on the technology and business nature of the service or CI.

For consumers, performance is an important service characteristic, and therefore it is a topic for negotiation, agreement, monitoring, and reporting. These activities involve multiple practices (including the business analysis, relationship management, service design, service level management (SLM), and measurement and reporting practices, and others). The capacity and performance management practice is used in conjunction with these to ensure that capacity and performance are sufficiently and consistently addressed.

Service performance is a complex characteristic. Analysing service performance is only possible with multiple measurements and agreements about how those measurements should be understood. Agreements should depend on the service architecture, importance of certain transactions and supporting components, quality criteria, and other parameters. Moreover, performance from the perspective of a user or a group of users can be different from the performance measured from the provider’s or customer’s perspectives. For example, service transaction delays that are experienced by 2.5% of users will be perceived by the 2.5% as poor performance, but the agreed performance targets might still be being met.

The capacity and performance management practice should ensure a transparent, consistent, and practical understanding of capacity and performance (expected, agreed, designed, and actual) among all relevant parties.

When services are provided to thousands or millions of people, there is usually no single generic agreement on the service performance with customers. However, overall service performance is critical for the service provider.

2.3 Scope
The capacity and performance management practice ensures that services deliver agreed levels of performance to meet the needs of customers and users in a cost-effective way. To achieve this, the capacity and performance management practice includes the definition, measurement, analysis, and improvement of the capacity and performance of services, products, and components. It is a centre of expertise for capacity-related matters and supports other service management practices.

The scope of the capacity and performance management is very broad. Many practices directly or indirectly contribute to service performance. Table 2.1 lists activities which are closely related to capacity and performance management. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams and should be combined as necessary depending on the specific organizational, service, and customer contexts.

Table 2.1 Activities related to the capacity and performance management practice described in other practice guides
Activity

Practice guide

Negotiating and agreeing the customer requirements for capacity and performance

SLM

Designing capacity and performance controls as a part of the service model

Service design

Aligning capacity and performance controls with the business architecture

Architecture management

Identifying the risks associated with capacity and performance

Risk management

Analysing the impacts of changes on capacity and performance targets

Change enablement

Monitoring the capacity and performance of services

Monitoring and event management

Justifying new capacity and performance controls

Portfolio management

Implementing risk mitigation measures and changing the service infrastructure to ensure resilience

Project management, change enablement

Testing the capacity and performance controls during service transition

Service validation and testing

Reacting to events which might affect the organization’s ability to meet capacity and performance targets

Managing capacity and performance incidents

Incident management

Managing and implementing improvements related to capacity and performance on an ongoing basis

Continual improvement

2.4 Practice success factors
Definition: Practice success factor
A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity, as it includes components from all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The capacity and performance management practice includes the following PSFs:

identifying service capacity and performance requirements
measuring, assessing, and reporting service performance and capacity
treating service performance and capacity risks.
2.4.1 Identifying service capacity and performance requirements
Identifying service capacity and performance requirements includes:

Understanding customer requirements for service performance The business analysis and SLM practices are normally used to communicate with customers in order to understand their performance and capacity requirements for IT services and negotiate the service level requirements (SLRs). The capacity and performance management practice supports and inputs into the SLM, business analysis, and service design practices. Capacity and performance management can be crucial for optimizing a service design to meet increasing capacity demands while deferring an increase in costs.
Determining performance and capacity criteriaThe line between high and low performance should be clearly defined. The following factors should be considered when determining service performance criteria:
service actions/functionality/vital business functions; service performance is defined by critical service actions
acceptable delays in executing service transactions, which should not be counted as service degradation; and unacceptable degradation, which should be treated as unavailability
scale factor: service performance degradation generally means that delays are experienced by significant numbers of users, not individuals.
Choosing the right set of capacity and performance metrics Metrics should reflect how service degradation may affect the service provider and customers.
2.4.2 Measuring, assessing, and reporting service capacity and performance
Performance is one of the most essential indicators of service quality, so it is important that the service provider can measure, assess, and report performance. Reporting performance in terms of the lead time and the number of transactions per time frame is widely accepted practice. However, it is important to ensure that the measurements are understandable from the users’ perspective, as well as from the technical perspective. For more on defining meaningful metrics for services, readers should refer to the SLM practice guide.

When defining suitable measurements, it is crucial to reflect the business impacts of service degradation, rather than the technical performance of the service components.

Two of the most important objectives of the capacity and performance management practice are to ensure sufficient capacity and performance monitoring and translate monitoring data into service performance information.

Incident records can be sources of service disruption data. However, it is often difficult to obtain reliable performance and capacity data based on these, especially for user-reported incidents, and to align it with the agreed service performance metrics.

More reliable sources of performance and capacity data are infrastructure monitoring tools. However, although these can work well for measuring resource-provision type services, it is almost impossible to correctly measure the performance of service transactions based solely on the infrastructure monitoring data. Tools such as real user monitoring and business transaction monitoring can help to overcome this issue.

2.4.3 Treating service capacity and performance risks
The capacity and performance management practice is not only about planning and monitoring capacity and performance. This practice includes defining and managing controls to manage a wide range of risks that might impact services’ capacity and performance. For this, it is used in conjunction with the risk management and other risk-focused practices, such as the availability management, service continuity management, and information security management practices. Agreed performance controls are implemented through the service design, software development and management, and infrastructure and platform management practices.

In the context of risk management, the risk identification, prioritization, and measurement stages are key to the capacity and performance management practice.

The capacity and performance management practice ensures that risks will be treated effectively by:

assessing the impacts of components’ capacity and performance on the end-to-end performance of products and services and identifying related vulnerabilities and constraints
assessing the impacts of products’ and services’ capacity and performance on the user and customer experience
designing effective controls and countermeasures to prevent, detect, and mitigate capacity and performance risks
monitoring and controlling capacity and performance risks on an ongoing basis and optimizing risk management activities within the scope of the practice.
2.5 Key metrics
The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the capacity and performance management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams in order to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.2.

Table 2.2 Examples of key metrics for the practice success factors
Practice success factors

Key metrics

Identifying service capacity and performance requirements

Percentage of products and services with capacity and performance requirements clearly documented in SLAs
Percentage of new or changed operational products and services that match capacity and performance requirements documented in SLAs
Timely updates on service capacity and performance requirements and criteria during major service changes
Measuring, assessing, and reporting service capacity and performance

Percentage of accepted business cases for new components and architecture designs that are in line with the performance requirements
Reduction in the use of old (unsupported) components or architecture designs that cause breached SLAs due to performance issues
Percentage of products and services:

with defined capacity and performance metrics
whose capacity and performance is monitored
included in service capacity and performance reports
Percentage of enacted improvement initiatives logged by the capacity and performance management practitioners

Treating service capacity and performance risks

Number of unplanned capacity and performance upgrades to products, services, and components
Ratio of actual losses to expected losses due to insufficient capacity and performance of products or services
The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the capacity and performance management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

3. 
Value Streams and processes
3.1 Value stream contribution
Like any other ITIL management practice, the capacity and performance management practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The capacity and performance management practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which the practice contributes are:

deliver and support
design and transition
improve
obtain/build
plan.
The contribution of the capacity and performance management practice to the service value chain is shown in Figure 3.1.



Figure 3.1 Heat map of the contribution of the capacity and performance management practice to value chain activities

3.2 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

Definition: Process
A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.

The capacity and performance management practice activities form two processes:

establishing capacity and performance control
analysing and improving service capacity and performance.
3.2.1 Establishing capacity and performance control
This process includes the activities listed in Table 3.1 and transforms the inputs onto outputs.

Table 3.1 Inputs, activities, and outputs of the establishing capacity and performance control process
Key inputs

Activities

Key outputs

Business needs
Business process performance, transaction volumes and activity patterns and forecasts
Service component manufacturer requirements and standards
Service monitoring and measurement framework
Service reporting framework
SLAs
Existing service and component performance data
Identifying service capacity and performance requirements
Agreeing service capacity and performance requirements
Determining capacity and performance measurement requirements
Designing capacity and performance metrics and reports
Identified, agreed, and documented service and component requirements
Performance and capacity measurement requirements
Performance and capacity baselines, metrics, alerts, thresholds, and reports set up in the monitoring toolset
Automated scaling and load balancing controls in place (where applicable)

Figure 3.2 shows a workflow diagram of the process.

Image of Figure 3.2 shows workflow of the establishing Capacity and Performance Control process

Figure 3.2 Workflow of the establishing capacity and performance control process

This process may vary, depending on the type of services and service components to which it is applied. Table 3.2 demonstrates how the activities may vary for a modern cloud-enabled services and for the first tier of service support staff.

Table 3.2 Activities of the establishing capacity and performance control process
Activity

Cloud IT infrastructure

First tier support staff

Identifying service capacity and performance requirements

Capacity and performance management practitioners discover performance needs based on activity patterns and transaction volumes. This information may be already available from the SLM practice as a SLR, or from business case documents. Ongoing reporting can also be useful for identifying unmet scaling requirements.


These needs are then compared to the technical capacity characteristics of various service components, such as computing power, storage, end-user device input and output capacity, and network performance parameters (bandwidth, latency, connectivity, and so on).


Capacity and performance practitioners then suggest the optimal balance of performance needs, required component architecture, and efficient sourcing models (private, community, public, or hybrid options).


The output of this activity is a proposed architecture design and plans to supply the required capacity for medium and long-term cloud infrastructure designs. This output is supplied to the service design and to the SLM practices for cost-benefit analysis.


It is important to differentiate between the above requirements and short-term service demand spikes (such as an increased user flow to a website following a marketing campaign) that in a cloud environment can be detected and satisfied automatically via specialized capacity extension tools, and do not require thorough analysis.

Where user support is essential, strong consideration must be given to the resources needed for the service desk team that handles user enquiries.


Although other practices, such as the service desk and workforce and talent management practices, may manage staff planning and measurement, the capacity and performance management practice can provide business patterns and transaction volumes to those.


Capacity practitioners can also deduce the minimum required staff numbers, skills, and capabilities to enable optimal service speed and quality.

Agreeing service capacity and performance requirements

The SLM practice is responsible for SLA negotiations, including capacity and performance service quality criteria. Capacity and performance practitioners support this activity with service component expertise. The important to balance the cost/benefit ratio and to internally communicate the price of the service, which can vary considerably depending on the architecture options for different capacity.

Capacity and performance can be an important part of SLA negotiations. The practice can suggest several combinations of staff numbers and capabilities that will enable different levels of support at a different prices and costs.


This practice can also suggest support tool improvement initiatives that would help to optimize staff numbers, such as self-service interfaces, online chats, a social media presence, and so on.


These analytical efforts underpin SLA negotiations on the service support criteria.

Determining capacity and performance measurement requirements

In order to analyse, report on, and improve service performance, the service provider must measure it. Based on the agreed requirements, reporting policy, customer reporting requirements, and monitoring tools, an approach for performance monitoring should be defined.


Capacity and performance management practitioners understand that existing cloud orchestration tools can extend (or reduce) the existing paid-for capacity based on a set of internal or external triggers. Practitioners can design a set of thresholds and alerts that will start automated capacity altering procedures.

Staff performance measurement for the service support is likely to be linked to the duration parameters, such as time to respond, time to resolve, direct user contact, and so on. The capacity and performance management practice is likely to own relevant measurement tools (such as support phone line monitoring and reporting tools). Capacity practitioners will make these metrics available to other practices for managing personnel performance.

Designing capacity and performance metrics and reports

This activity focuses on service performance metrics and reporting. Practitioners design tools to imitate or manually control the service performance from the consumer perspective, deeming any technical indicators (such as the real-time network throughput) secondary. Technical indicators only help to verify the consumer experience of the service productivity, responsiveness, storage capability, and so on.

3.2.2 Analysing and improving service capacity and performance
This process includes the activities listed in Table 3.3 and transforms the inputs onto outputs.

Table 3.3 Inputs, activities, and outputs of the analysing and improving service capacity and performance process
Key inputs

Activities

Key outputs

Capacity and performance reports and alerts
New service designs and proposed architectures
Performance-related incident and problem records
Change schedule
Service capacity and performance analysis
Reporting on service capacity and performance
Planning and designing service capacity and performance
Improvement initiatives submitted to the continual improvement register (CIR)
Service design and architecture review and recommendations
Ongoing communications with service design and operational practices
IT budget planning updates
Figure 3.3 shows a workflow diagram of the process.

Image of Figure 3.3 shows workflow of the analysing and improving service capacity and performance process

Figure 3.3 Workflow of the analysing and improving service capacity and performance process

This process may vary, depending on the type of services and service components to which it is applied. Table 3.4 demonstrates how the activities may vary for modern cloud-enabled services and for a first tier of technical support staff.

Table 3.4 Activities of the analysing and improving service capacity and performance process
Activity

Cloud IT infrastructure

First tier support staff

Service capacity and performance analysis

Cloud orchestration and load balancing toolsets allow for the automated adjustment of cloud resources to meet demand. However, trend analyses of business activity patterns may signal that current service architecture may need to be changed in order to ensure high performance while avoiding excessive costs.

Capacity and performance practitioners can monitor technology metrics for the service desk staff and raise alerts (with the service desk practice) where deficiencies occur or thresholds are reached; for example, where no new user calls are picked up because the first-tier support staff are busy. This could be caused by a number of things, but the technology metric is an objective fact and is worth investigating.

Reporting on service capacity and performance

Cloud orchestration toolsets, as well as cloud provider reporting, can report on many technical indicators. However, the performance analysis in a cloud environment’s central idea is the focus on customers’ business processes. Technical component reporting may support the findings, but it should not be focus of the final report.

Based on the automated monitoring tools (such as a support phone line), capacity and performance practitioners can automate basic technology metrics reporting and provide reports in as-is or aggregated forms to the consumers.

Planning and designing service capacity and performance

It can be tempting to use the virtually unlimited scalability of computing power in the cloud to tackle the volatile and growing demand for services. However, it may be more prudent to alter the underlying application, middleware, and load balancing architecture when the demand hits a certain threshold (for example, altering the network design to cater to users on a newly acquired geographical market).

Capacity practitioners possess the necessary expertise to suggest these optimizations to avoid the excessive service costs that are associated with linear scaling.

Other practices can request the capacity and performance management practice help with specific calculations upon staff numbers and capabilities, and with planning for the automation of manual support tasks. The outputs of these efforts are improvement initiatives. For example, practitioners can suggest automated diagnostic data being harvested from end user devices in order to save time spent on user questionnaires.

4. 
Organizations and people
4.1 Roles, competencies, and responsibilities
The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

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

Examples of roles that can be involved in capacity and performance management activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

Table 4.2 Examples of roles with responsibility for capacity and performance management activities
Activity

Responsible roles

Competency profile

Specific skills

Establishing capacity and performance control

Service capacity and performance analysis

Capacity and performance manager
Service owner
Technical expert
IT quality manager
MT

Excellent analytical skills
Knowledge of methods and techniques, such as Fault-Tree Analysis, Component Failure Impact Analysis, and so on
Familiarity with analytical tools
Good understanding of the possible business impacts of service outages
Reporting on service capacity and performance

Service owner
Relationship manager
Customer
CA

Knowledge of agreements and expectations
Understanding of the consumer context
Communication and negotiation
Planning and designing service capacity and performance

Capacity and performance manager
Service designer
Technical expert
Architecture manager
TM

Good understanding of resilience options
Awareness of existing controls
Awareness of technology available on the market
Good understanding the possible business impacts of service outages
Analysing and improving service capacity and performance

Analysing and improving service capacity and performance

Analysing and improving service capacity and performance

Analysing and improving service capacity and performance

Identifying service capacity and performance requirements

Service or product owner
Relationship manager
Service designer
Customer
CTA

Business analysis
Good knowledge of business activity patterns, throughputs, and markets that generate demand
Good knowledge of service architecture and configuration
Communication and coordination
Agreeing service capacity and performance requirements

Service owner
Relationship manager
Customer
CA

Communication and negotiation, and ability to advocate for improvements
Good knowledge of service architecture and configuration
Determining capacity and performance measurement requirements

Capacity and performance manager
Monitoring tool administrator
Monitoring and event manager
Service designer
Technical expert
TM

Good understanding of monitoring tools and techniques
Awareness of technology available on the market for monitoring and event management
Designing capacity and performance metrics and reports

Capacity and performance manager
Service owner
Relationship manager
IT quality manager
CM

Communication and negotiation
Report and dashboard design skills
4.2 Organizational structures and teams
It is unusual to see a dedicated organizational structure for the capacity and performance management practice, although capacity and performance practitioners may be supported by formal positions and job descriptions. Service capacity is normally managed by other organizational functions, where roles can be combined depending on the nature of the services.

Where service providers are responsible for a limited number of services and components (such as a service integrator function), there can be a capacity and performance manager. This role is accountable for coordinating practices, functions, and organizations to ensure cost-efficient service capacity and sufficient levels of service performance.

Business and technical knowledge is pivotal to the success of this practice, as well as the service provider’s staff’s ability to plan, monitor, and report on the performance of services and components.

Managers and practitioners should complement their technical knowledge with communication and advocating abilities to ensure that capacity concerns and prognoses are heard, measured, and addressed during service design, negotiations, and operation.

5. 
Information and technology
5.1 Information exchange
The effectiveness of the capacity and performance management practice is based on the quality of the information used. This information includes, but is not limited to, information about:

component-based reports
service-based reports
performance exception reports
performance and workload forecasts
architecture models for different ranges of service demand
vendor-sizing recommendations and models.
This information may take various forms. The key inputs and outputs of the practice are listed in section 3.

In most cases, the capacity and performance management practice can significantly benefit from automation. Where this is possible and effective, it may involve the solutions outlined in Table 5.1.

Table 5.1 Automation solutions for capacity and performance management activities
Process activity 

Means of automation 

Key functionality 

Impact on the effectiveness of the practice 

Establishing capacity and performance control

Service capacity and performance analysis

Infrastructure and application monitoring and reporting tools, built-in user behaviour monitoring tools, dashboarding and reporting tools, advanced analytics tools

Collection of system and service health data, processing and analysis, dashboard and report design and presentation

High

Reporting on service capacity and performance

Reporting and dashboarding tools, service portals and apps, email and other communication tools, social media

Report presentation

Low to high, depending on the volume of services and stakeholders who must be reported to

Planning and designing service capacity and performance

Architecture management tools, CMDB, change initiation and control tools

Determining existing controls and resilience measures.

Improvement-related changes initiation and control.

Medium

Analysing and improving service capacity and performance

Analysing and improving service capacity and performance

Analysing and improving service capacity and performance

Analysing and improving service capacity and performance

Identifying service capacity and performance requirements

Service catalogue, CMDB, BPM tools, CMDB, service models, performance and capacity monitoring and management tools, and asset management tools

In order to identify service and performance vital business functions, analysts should have access to information about service components and service actions.

BPM tools may provide information about consumer’s processes and operations that are supported by the service.

Very high

Agreeing service capacity and performance requirements

Contracting tools and service portals

Selection of alternative options

Communication with the service customer

Low

Determining capacity and performance measurement requirements

Reporting and dashboarding tools, service portals, and apps

Report and dashboard template design

Low to high, depending on the volume of services and stakeholders who must be reported to

Designing capacity and performance metrics and reports

Reporting and dashboarding tools, service portals, and apps

Report and dashboard template design

Low to high, depending on the volume of services and stakeholders who must be reported to

6. 
Partners and suppliers
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services. These are often provided by third parties (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the practice guides for service design, supplier management, and SLM.

As the service integration model becomes common within modern corporate service consumer environments, the importance of orchestrating the service performance becomes apparent. Where multiple external service providers are responsible for different service components, or even for entire service offerings, the end-user experience is at risk of being overlooked (especially when it comes to such less-tangible impressions as ‘waiting for the system to unfreeze’). A service integration and management body should be responsible for maintaining the end-user focus of all efforts relating to service capacity and performance by multiple service providers.

Incentivizing service providers to communicate performance issues to a centralized (or user-focused) entity can help to coordinate service integration efforts. This could be a dedicated capacity and performance manager, service-desk inbox, or any other body. Whatever it is, analysing how issues affect the end-user experience enables transparency and rapid recovery. Such an incentive could be to escalate potential issues quickly in order to limit liability when things go wrong.

Frequently, in multi-vendor IT environments, service providers limit capacity growth options to linear models only. Businesses, when their user bases expand rapidly, will often add resources to the same infrastructure in direct proportion to the growing workload. Modern public cloud offerings that resemble the ‘shopping cart’ experience may encourage this behaviour. However, other architectural arrangements may be applicable for operations of a different scale, and can ensure efficient load balancing, optimal resource utilization, and even increased system reliability.

Capacity management practitioners should have a strong understanding of modern IT infrastructure architectures. Where appropriate, they should suggest altering designs to cater for increased or changed demand and ensure cost savings. The service integration body can then suggest these alternative models to service providers.

Where organizations aim to ensure fast and effective capacity and performance management, they usually try to agree to close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision-making. All parties in such relationships should aim for mutual transparency and visibility of changes that may affect the other parties (see the supplier management practice guide for more information).

7. 
Important reminder
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the practice guides, organizations should always follow the ITIL guiding principles:

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
AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

8.1 Authors
Konstantin Naryzhny

8.2 Reviewers
Roman Jouravlev

