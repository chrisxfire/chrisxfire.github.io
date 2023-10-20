---
title: service configuration management
date: 2023-10-20T00:00:00-06:00
draft: true
weight: 1
---


August 29, 2023
37 min read

ITIL
ITIL4 Practice Guides
Service configuration management: ITIL 4 Practice Guide
71 Likes
This document provides practical guidance for the service configuration management practice.

Table of Contents
1. 
About this document
This guide provides practical guidance for the service configuration management practice. It is split into seven main sections, covering:

general information about the practice
the practice’s processes and activities and their roles in the service value chain
the organizations and people involved in the practice
the information and technology supporting the practice
considerations for partners and suppliers for the practice
information on assessing and developing the capability of the practice
recommendations for succeeding in the practice.
1.1 ITIL® 4 qualification scheme
Selected content of this guide is examinable as a part of the following syllabus:

ITIL Specialist Create, Deliver and Support
ITIL Specialist High-velocity IT
ITIL Specialist Plan, Implement, and Control
ITIL Practitioner Change enablement
Please refer to the respective syllabus documents for details.

2. 
General information
2.1 Purpose and description
Key message

The purpose of the service configuration management practice is to ensure that accurate and reliable information about the configuration of services, and the configuration items that support them, is available when and where it is needed. This includes information on how configuration items are configured and the relationships between them.

Organizations use resources to create and deliver products and services. These resources may belong to the organization, or they may be available as part of a service the organization consumes. The service configuration management practice collects and manages information about a variety of resources, typically including hardware, software, networks, buildings, people, suppliers, products, services, and documentation. The resources in the scope of the practice are called configuration items (CIs).

Definition: Configuration item

Any component that needs to be managed in order to deliver an IT service.

The primary objective of the service configuration management practice is to efficiently provide useful information to the organization. The scope of the components under its control should be defined by their usefulness and efficiency. The main factors shaping this practice are the usefulness of the configuration information and the costs of obtaining and maintaining it.

Tip

Resources that cannot be individually managed are usually not considered CIs. For example, the knowledge used by an analyst to manage incidents is important but will probably not be treated as a CI. At the same time, virtual resources, such as a virtual server or network, may be CIs and require similar management as physical resources.
The service configuration management practice is focused on resources that are important for product and service management, regardless of whether these resources are the organization’s property or provided as part of a third-party service. However, different lifecycle models and controls may apply to these two groups of resources.
The service configuration management practice is an important element of service management. This practice is beneficial for both the service provider and their service consumers.

Benefits for the service provider include:

improved risk management due to better understanding of the relationship between the CIs
better planning and control of changes
better understanding and management of the capacity, availability, and security of IT services and components
understanding and accurate allocation of service costs
better understanding, planning and control of service performance
better cause and effect analysis, which improves effectiveness and efficiency of incident and problem management.
Benefits for the service consumer include:

more realistic and accurate service level agreements
higher quality of IT services
better management of IT risks.
2.1.1 Service configuration models
The service configuration management practice involves identifying and documenting the connections and relationships between configuration items. This usually results in models (known as service configuration models, service resourcing models, or functional and financial service models). These models can be focused on various aspects of the service architecture and the relationships between the components. They represent various level of abstraction, from high-level functional models (as shown in Figure 2.1) to an accurate mapping of the connections and relationships between physical and digital CIs.

Image of Figure 2.1 show a diagram of the high-level service configuration model

Figure 2.1 A high-level service configuration model

Service configuration models are used for various purposes, including:

impact analysis
cause and effect analysis
risk analysis
cost allocation
availability analysis and planning.
Service configuration models should be designed and maintained to meet stakeholder needs.

The service configuration management practice is a highly-automated practice. It relies on the collection, maintenance, and control of large amounts of configuration data and often includes building, maintaining, and presenting complex configuration models. The practice involves gathering data from multiple sources, integrating it and presenting in a meaningful way. Specialized tools are typically used alongside monitoring, discovery, analytical, and record-keeping systems.

This practice often allows configuration information to integrate with records that are managed as part of other practices, including the incident management, change enablement, problem management, monitoring and event management, and service request management practices, among others. However, some configuration models are difficult or impossible to automate; they require manual data maintenance and/or relationship mapping. Examples include user data, organizational structures, contracts with suppliers and partners, and so on. Manual efforts and associated costs, alongside automation and integration costs, should be considered when the practice is being designed and improved.

2.2 Terms and concepts
2.2.1 IT assets and configuration items
The service configuration management and IT asset management practices, as well as IT assets and CIs are closely related, and share much of the same information and tooling; each has some critical dependencies on the other. Nevertheless, these are distinct concepts. The definition of a configuration item was already given in section 2.1, but is repeated here for comparison with that of an IT asset.

Definition: Configuration item

Any component that needs to be managed in order to deliver an IT service.

Definition: IT asset

Any financially valuable component that can contribute to the delivery of an IT product or service.

As Figure 2.2 illustrates, some items can be both CIs and IT assets, and some items are specifically just an IT asset or just a CI.

For example, a portable storage device may be considered an IT asset but not a CI. Which IT assets are, and are not, recognized as CIs depends on how an organization’s services are defined and configured, and which IT assets are needed for them.

Conversely, some CIs may not be IT assets. For example, a configuration script or documented knowledge artefacts may be considered CIs but not assets. There is no single rule as to how these should be defined. Whether something is considered to be an IT asset or a CI is not an inherent property of the item. The distinction will depend on how an organization defines its services and what it needs to manage.


Another differentiator between IT assets and CIs is the information and attributes related to them. The attributes for CIs are focused more on the information that is critical for the management of the CI in relation to service utility and warranty, whereas the attributes for IT assets are focused more on the management of the asset itself (see section 2.2.3 for more information on the categorization and attributes of CIs).

It is important to initiate the discussion within an organization and to understand the distinction between IT assets and CIs to properly comprehend the differences in the scope of the configuration management and ITAM practices (for more information, see sections 2.3 in this and the IT asset management practice guides). This understanding will help to define the relationships between the practices and ensure that data from both is used in a mutually beneficial way.

2.2.4 Configuration management systems and databases
The service configuration management practice involves a significant amount of data from various sources and depends on the ability to collect, integrate, process, and present this data in a reliable, cost-efficient way. CMSs are designed to fulfil this need. Because of the multiplicity of data sources for the practice, a CMS is usually a complex system that combines one or more specialized solutions and integrations with sources of configuration data.

Definition: Configuration management system

A set of tools, data, and information that is used to support the service configuration management practice.

A key functionality of a CMS is keeping and managing CI records and the relationships between them. This is usually achieved with one or more configuration management databases (CMDBs).

Definition: Configuration management database

A database used to store configuration records throughout their lifecycle. It also maintains the relationships between configuration records.

Sometimes the terms ‘CMS’ and ‘CMDB’ are used interchangeably, usually in accordance with the CMS definition.

In some organizations, a CMS is used to integrate configuration management data in a CMDB with IT asset data in the asset management database (AMDB).

Other organizations tend to use a fully combined asset configuration database. Such an approach allows them to manage both IT assets and CIs from within one facility. In this scenario, distinguishing between an IT asset and a CI is achieved using ‘label’ fields. ‘Asset attributes’ and ‘CI attributes’ can then be defined and recorded for any component as needed. More information on the CMS and its utilization can be found in Chapter 5.

In some cases, it is more efficient to retrieve configuration data upon request than to make it permanently available in a CMS. There is no correct answer and no recommended solution for defining which data should be included into a CMS. These decisions should be driven by the value of the configuration information to stakeholders and the costs of obtaining and maintaining the information.

2.2.3 CI categorization and attributes
Services and products comprise numerous CIs and connections between them. When defining and categorizing CIs, an organization should find a presentation method that helps all stakeholders, including non-technical roles, to comprehend these complex structures. To categorize CIs and define data representation levels, the configuration management team should rely on service architecture and continuously collaborate with the service architecture team throughout the lifecycle of the CI.

As an example, CIs may be grouped into the following domains:

Business service domain These CIs represent the business capability (service offering or business service) that the organization provides to its customers.
Product domain These CIs represent products and all the distributed components that each product may encompass (as such they are vital for documentation, images, installation scripts and other aspects of the products). Product CIs may support one or many business services. Business services may include multiple products. Products can contain one or many applications, however they may consist of a wider range of components beyond applications.

Application domain These CIs represent applications and all the distributed components that make them work (as such they are vital for documentation, images, startup script and other aspects of the application). Application CIs may support one or many business services. Business services may include multiple applications. Some organizations separate the application and product domains. Application domain CIs may include:
- Elements that are vital for the application documentation (requirements, design documents, disaster recovery plans, and so on)

- Licenses (agreements, contracts, and so on)

- Configuration files or scripts (for example, installation scripts)

- Support tools (log analysis tools, testing tools, and so on).

End user CIs domain (sometime also named Office CIs domain) These are the CIs used by end-users to perform their daily tasks. These CIs include, among others:
- Printers

- Mobile devices

- User workstations

- Peripheral devices

Infrastructure domain CIs (sometimes also named the technical service domain) These CIs are technical infrastructure components (such as servers, storage devices, network gear and so on) that support one or more application services. Some organizations choose to divide the infrastructure domain into smaller domains to mirror the infrastructure architecture. Examples of these domains may include, but are not limited to:
- middleware CI domain

- data center CI domain

- network CI domain

- server CI domain and other.

CIs of different types have different key attributes. Attributes are data elements which help to describe the CIs under a relevant CI domain. The attributes may have different lifecycles and different levels of control from within the organization. The differences are usually reflected in the way information about the CIs is collected, stored, controlled, and presented throughout their lifecycles. As CIs are often structured in a domain (classes) hierarchy, each lower subdomain may inherit the attributes of its parent CI. Example of the attributes of CIs within different domains are shown in Table 2.1.

Infrastructure domain CIs

Application domain CIs

Business service domain CIs

Owner
Memory
Processor
CPU size
Energy consumption
Lifecycle state related to the service (pipeline, active, retired)
Owner
Version
Installation date
License
CO2 emission
Lifecycle state related to the service (pipeline, active, retired)
Owner
Business impact
Contract
SLA
Amount of waste and e-waste
associated with the service
Lifecycle state related to the service (pipeline, active, retired)
Much of the data required for describing CIs is stored and managed in other databases. This includes data on:

customers

users
locations
organizational units
service agreements and other relevant documentation
information from other practices (such as incidents, requests, changes, problems associated with a relevant CI).
Some attributes can be managed as separate CIs in the scope of the relevant domain and vice versa (for example, location can be an attribute of the hardware domain or separate CI connected to hardware; licence can be an application domain CI attribute, or a separate CI linked to the application). CIs of different domains are mapped to each other, thus another important CI attribute is the relationship between them. The information about the relationships allows for analysis of the dependencies between CI instances when planning changes, diagnosing incidents, or designing a new service. This information is also beneficial for capacity management and calculating the costs of IT services.

The relationship between CIs, along with the relationship type, should be defined, documented, and visualized in the CMDB. Examples of how organizations may categorize different types of relationships include:

Dependency: one CI depends on another, for example, a server may depend on a network switch.
Communication: CIs communicate with each other, for example, a web server communicates with a database.
Parent/Child: a CI is made up of other CI, for example, a virtual machine host may contain multiple virtual machines.
Aggregation: multiple CIs are combined to form a single CI. For example, a storage array may be made up of multiple hard drives.
As mentioned before all decisions about CI data should be driven by the usefulness of the CI to stakeholders and the costs of obtaining and maintaining the information.
2.2.4 CI lifecycle models
Definition: CI lifecycle model

A comprehensive set of rules, policies and guidelines that define, standardize and optimize the organization’s approach to managing the lifecycle of CI records within a specific domain or any other category.

Each CI lifecycle model may have its own lifecycle and management approach. However, the model should define all stages of the CI record’s lifecycle from creation to deletion, and provide guidelines to ensure the accuracy, reliability and security of the CMDB data.

Organizations often define a model for each CMDB domain, but a model can also be defined for any specified group of CIs based on the organizational needs. For example, a specific model can be created for CIs in a certain location, or a model can be defined for all the CIs connected to a certain business service.

When creating a model, CIs can be grouped into types based on their features, including, but not limited to, the following attributes:

related IT asset type
types of stakeholders
responsible party or parties
financial significance and reporting requirements
level of tangibility (from very tangible hardware equipment to intangible licences, data, cloud computing capacity, services, or subscriptions)
location (for example, physically on the premises, physically in co-location or on the provider’s premises, cloud resources, or licences on the organization’s own servers) and method of access.
CI lifecycle models define, for a particular type of CI:

CI type owner(s)
naming and labelling policy
key group and individual attributes
key relationships (taxonomic and functional)
key lifecycle stages
procedures and/or guidelines for CI identification, ongoing control, verification, and audit
responsibility for following the model
key stakeholders (interested in the configuration information) and their requirements
key reports and dashboards presenting the configuration information, where applicable.
The CI lifecycle models combine to form CMDB data governance.

CMDB data governance is a vital part of data quality. It is the set of policies, guidelines and rules that govern the collection, storage, analysis, and use of data in the CMDB. For example, when an organization decides on the level of granularity of data for a service, data governance defines how to record the attributes of smaller items inside of a top-level CI.

The design of effective CI lifecycle models and CMDB data governance in general requires the involvement of key stakeholders, such as representatives of the service architect, security, and IT operations teams, as well as other relevant CMDB data users.

2.2.5 Service configuration management and sustainability
Digital sustainability is a developing area at the intersection of digital service and product management, electricity markets, data science and sustainable development (see ITIL 4 Sustainability in Digital and IT for more information on digital sustainability).

Definition: Sustainability

A business approach focused on creating long-term value for society and other stakeholders, by addressing the risks and opportunities associated with economic, environmental, and social developments.

Service configuration management supports digital sustainability by including relevant attributes in the CI information. These may include:

Carbon footprint
Source information (whether the supplier of the CI is known and meets sustainability requirements)
Recycling information (may apply to the CI materials and to the end of CI lifecycle).
The organization may decide to store information in the asset management database, rather than the CMDB. However, even if no sustainability-specific attributes are used in the CMDB, accurate, reliable, and relevant information about CIs and their relationships can make a significant contribution to the following areas of an organization’s sustainability journey:

E-waste reduction
Energy efficiency
Digital carbon footprint optimization
Cybersecurity.
Beyond supporting sustainability initiatives, the service configuration management practice should be also be designed and executed in a sustainable way. To reduce the digital carbon footprint of the CMDB, the amount of data stored within it should be sufficient but not excessive; the integration of the CMDB with the external databases should be secure and reliable; and processes and procedures should be compliant with both internal policies and external regulatory standards.

2.2.6 CI verification and audit
As an important source of information for decision-making, CI records and configuration models are subject to continual verification and regular audits.

Service configuration data should:

reflect the actual attributes, statuses, and relationships of the CIs
highlight deviations from the baseline configuration(s)
provide sufficient data to restore or re-create the approved configuration(s).
Definition: Baseline configuration

A configuration of a product, service, or other configuration item, that has been formally reviewed and agreed. It serves as the basis for further activities, such as planning, development, and usage.

The service configuration management practice ensures that relevant CI data is captured in the CMDB at each stage of the lifecycle. The practice should ensure that changes in CIs are correctly and promptly captured in the CMDB. To that end, CI record-keeping should be automated wherever possible. Automation improves the reliability of the configuration data and decreases the need for verification (but does not remove it).

Definition: Verification

An activity that ensures that a new or changed IT service, process, plan, or other deliverable matches its design specification and is complete, accurate, and reliable.

In this practice, verification is a continual activity of identifying and correcting gaps and deviations between the data in CMDB and the actual environment and/or the approved configurations. In many cases, verification can be largely automated, such as checking CMDB data (including CIs and relationships) for completeness, correctness, and compliance.

Definition: Compliance

The act of ensuring that a standard or set of guidelines is followed, or that proper, consistent accounting or other practices are being employed.

Definition: Inventory

Data collection and clean up, performed as manual tasks, to build or verify the contents of the CI register.

Definition: Discovery

Data collection and clean up, achieved through automation technology and tools, to build or verify the contents of the CMDB. Discovery produces the location and identification of CIs that exist within the organization, particularly those that were previously undocumented or inadequately documented in the CMDB.

Verification of the CMDB data should ideally be performed through a combination of inventory and discovery.

Depending on the CI types that are in scope and the available automation tools, inventory is performed manually or through integration with discovery tools and other systems that are collecting data about the status of the organization’s resources. The CMDB indicates what should be found, and the inventory reveals what is found. The identification and resolution of gaps between the CMDB and the inventory is verification. When verifying data, it may help to:

identify and investigate unregistered CIs found in the organization
identify and document unregistered authorized changes (typically indicating ineffective CI control)
identify, investigate, and revert or otherwise address unauthorized changes.
There are different approaches to dealing with identified gaps between the actual and documented configuration information. The key challenge is to ensure that the data in the CMDB reflects the status of the organization’s resources and that this status is correct (meaning there are no unauthorized changes). Possible solutions include:

carefully investigating every finding and correction of the organization’s resources or configuration data, depending on the investigation’s results
(semi-)automatically updating the CMDB to reflect the de-facto situation, regardless of whether the situation is authorized (this decouples the investigation of unauthorized changes from the CMDB verification)
(semi-)automatically correcting the de-facto situation based on the latest configuration baseline, without investigating the gaps’ origins (this is more applicable to digital resources and can be difficult to do with physical resources).
These solutions are not mutually exclusive. They can be combined as necessary, depending on the situation.

Organizations may also formally audit configuration data. These audits are often combined with IT asset audits (see the IT asset management practice guide).

Definition: CMDB audit

A planned, structured, and documented inspection of the organization’s configuration items that aims to assess the correctness of the CMDB data in scope.

Auditing is one of the tools of CMDB verification; a resource-demanding planned verification endeavour. It is usually organized and managed as a project and, like any project, should be justified and approved in order to occur.

Verification is an integral part of the service configuration management practice. It is necessary to ensure that the configuration data is accurate, up to date, reliable, understandable, easy to use, and relevant.

2.3 Scope
For the chosen types of CIs, the service configuration management practice ensures that:

trustworthy configuration data is provided and maintained, which includes updating the configuration data to reflect ongoing changes in the statuses, attributes, and relationships of CIs
relevant and accurate reports are provided to support decision making
the CI lifecycle is integrated with other practices.
There are several activities and areas of responsibility that are not included in the service configuration management practice, although they are still closely related to service configuration management. In some cases, the practice depends on these activities. They are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams and should be combined as necessary, depending on the situation.

Table 2.2 Activities related to the service configuration management practice described in other practice guides
Activity

Practice guide

Managing IT assets and IT asset data

IT asset management

Managing contracts with suppliers and partners

Supplier management

Ensuring that only authorized changes are made to CIs
Analysing the impacts of changes that involve CIs
Authorizing and planning changes requiring CI modification
Defining rules for CI changes triggered by standard changes or service requests
Change enablement

Defining and managing the architectures of the organization’s products and services

Architecture management

2.4 Practice success factors
Definition: Practice success factor

A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The service configuration management practice includes the following PSFs:

ensuring that the organization has relevant configuration information about its products and services
ensuring that the costs of providing configuration information are continually optimized.
2.4.1 Ensuring that the organization has relevant configuration information about its products and services
The focus of the service configuration management practice is ensuring that relevant configuration information is captured, maintained, and provided to the stakeholders when needed.

Typically, stakeholders that benefit from configuration information use it in the contexts of other management practices and in the wider context of the organization’s value streams.

As listed in section 2.1, configuration information can be used for:

impact analysis
cause and effect analysis
risk analysis
cost allocation
availability analysis and planning.
Table 2.3 shows how these activities contribute to various management practices. These and other ways to use configuration information are applicable to every practice and value stream. However, in every case there should be a justification for adding more data or complexity to the CMDB. Key questions to consider include:

Is this information available from other sources?
Is this information critical or optional for decision-making?
What are the initial and ongoing costs of including this information in the CMDB?
How often is this information required?
How soon does it need to be available?
In some cases, it is more efficient to retrieve configuration data upon request than to make it permanently available in the CMDB. These considerations apply to a range of CI types, attributes, relationships, and lifecycle stages.

Table 2.3 Service configuration information supports other management practices
Impact analysis

Cause and effect analysis

Risk analysis

Cost allocation

Availability analysis and planning

Incident management

Analysis of the impacts of incidents on resources, products, services, and users

Localization of failed CIs based on information about their impacts

Analysis of the expected impacts of developing incidents

Allocation of costs of supporting cost centres and/or customers

Assessment of service availability during incidents and workaround planning

Problem management

Analysis of the impacts of errors on resources, products and services, service consumers, and users

Identification of CIs and relationships that might cause or have caused incidents

Analysis of the potential impacts and probabilities associated with identified errors

Allocation of problem investigation and control to cost centres and/or customers

Assessment of the impacts of identified errors on service availability and the planning of temporary solutions

Change enablement

Analysis of the impacts of ongoing and planned changes on resources, products and services, service consumers, and users

Review of unsuccessful changes and changes with unplanned effects, as well as the identification of possible causes of failures

Analysis of risks during the planning of changes

Allocation of costs of changes to cost centres and/or customers

Assessment of the impacts of planned changes on service availability

Planning of service availability during planned changes

Availability management

Analysis of the impacts of events and changes on the availability of resources, and products and services
Analysis of the impacts of unavailable resources on products and services
Identification of causes of product and service unavailability

Analysis of (un)availability risks

Allocation of costs of enhanced availability measures to cost-centres and/or customers

Analysis and planning of product and service availability

Service continuity management

Analysis of the impacts of possible and actual disasters on resources, and products and services
Analysis of the impacts of the unavailability of resources on vital business functions
Identification of causes of disasters

Analysis of service continuity risks

Allocation of the costs of enhanced availability measures to cost-centres and/or customers

Analysis and planning of product and service availability

Information security management

Analysis of the impacts of security events, incidents, and vulnerabilities on resources and products and services

Identification of the causes of information security incidents

Identification of vulnerabilities

Analysis of information security risks

Allocation of the costs of information security controls to cost-centres and/or customers

Analysis and planning of product and service information security

Key message

Configuration information should be relevant to the organization’s needs. Including all available data in a CMDB or blindly following examples from other organizations is not beneficial. The service configuration management practice is only as valuable as the information it provides is accurate, up to date, reliable, understandable, easy to use, and relevant.

Data quality is a key factor for CMDB utilization. Data quality can be defined based on such factors as accuracy, currency, reliability, understandability, usability, and relevancy.

Just a few cases of incorrect data (such as an attribute not being up to date or accurate) may undermine trust from CMDB users, and in some cases cause incidents.

As described in 2.2.4, CMDB data governance and CI record lifecycle models are a vital factor of data quality. They support the integration of service configuration management into value streams.

2.4.2 Ensuring that the costs of providing configuration information are continually optimized
Following the ‘optimize and automate’ guiding principle, routine tasks, such as discovery, inventory, and verification, should be optimized and automated to streamline workloads and improve the effectiveness and efficiency of the practice.

In line with the ‘keep it simple and practical’ guiding principle, the service configuration management practice should not become a bureaucratic control system. Rather, it should streamline work by providing valuable information in a convenient, useful form. This provision of information typically involves channels managed as part of other practices (including the supplier management and service desk practices). The effective integration of practices is essential for the configuration information consumers to have a positive experience.

The service configuration management practice provides information to other practices, acting as a supporting practice in most of the organization’s value streams. However, it is unlikely that it will contribute to a value stream with core value-creating activities. This means that it is important to ensure that the cost of configuration information is continually optimized.

Cost optimization can be achieved in multiple ways, but a good way to drive optimization is to follow the ITIL guiding principles, as described in Table 2.4.

Table 2.4 ITIL guiding principles and the continual optimization of configuration information costs
Guiding principles

Description

Focus on value

Include only the relevant information required by stakeholders

Start where you are

Use available sources of information; avoid adding new sources and tools unless they are justified

Progress iteratively with feedback

Regularly review information use and confirm its relevance, adjusting the CMDB scope if needed

Collaborate and promote visibility

Explain and promote available sources of configuration information and the best ways to use them, then provide hints and tips for more efficient use

Think and work holistically

Consider other sources of data for decision-making, do not try to put everything in the CMDB

Keep it simple and practical

Provide relevant information in the most convenient way; avoid complex interfaces and reports

Optimize and automate

Continually optimize resource-consuming practice activities. Automate CMDB verification, data collection, relationship discovery, and other activities.

There are several sources of costs to consider when managing a CMDB:

for the CMS:
- software (costs of purchasing or licensing the CMDB and other CMS software)

- hardware (costs of using additional hardware to run the CMS)

- data integration (costs of integrating different databases, including efforts and time for data

mapping and migration if required)

- implementation (cost for planning, configuring, and testing the CMDB)

- maintenance (costs for ongoing maintenance actions such as software updates, troubleshooting,

implementing enhancements)

- carbon footprint (indirect and non-monetary costs caused by the amount of data stored in the CMS, sustainability of hardware and software and electricity consumption)

- human time and effort required for the manual activities caused by the service configuration management practice (for example updating CMDB records as a part of a change, or adding the relationships of new CIs when implementing a new service)

- training (costs for training of the CMS users and maintenance team)

- audits (cost of conducting internal and supporting external CMDB audits)

- external services (from CMS implementation, to conducting CMDB audits).

The ITIL 4 concept of the four dimensions of service management can be used to ensure that cost calculations are comprehensive and holistic. The cost calculation procedure should be aligned with the financial management and project management practices to ensure that the calculation is consistent, and that costs are compliant with existing organizational approaches and fit for purpose.

2.5 Key metrics
Key metrics for the service configuration management practice are mapped to its PSFs. The key metrics are listed in Table 2.5.

The practice metrics should be applied to a specific context such as type of incident, services, specialist groups, or periods of time. The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which the practices contribute. The context of the business and the value streams is important when defining whether the practice’s performance is considered good or not. This is why this practice guide cannot recommend universal key performance indicators for service configuration management: the target values for each metric can only be defined in the organization’s context.

Table 2.5 Key metrics for service configuration management
Practice success factors

Key metrics

Ensuring that the organization has relevant configuration information about its products and services

Stakeholder satisfaction with configuration information
Stakeholder satisfaction with service configuration management interfaces, procedures, and reports
Number and impact of bad decisions made due to insufficient or incorrect configuration information
Number and impact of incorrect data in the CMDB
Percentage of CMDB data verified over the period
Ensuring that the costs of providing configuration information are continually optimized

The direct costs of service configuration management
Percentage of the CMDB data used by the organization
3. 
Value Streams and processes
3.1 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

Definition: Process

A set of interrelated or interacting activities that transform inputs into outputs. A process takes one of more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.

Service configuration management activities form three processes:

managing a common approach to service configuration management
capturing, managing, and providing configuration information
verifying configuration data.
3.2.1 Managing a common approach to service configuration management
This process is focused on establishing an effective and efficient approach to the management of configuration information in the organization. It includes the activities listed in Table 3.1 and transforms the inputs into outputs.

Table 3.1 Inputs, activities, and outputs of the managing a common approach to service configuration management process
Key inputs

Activities

Key outputs

Organizational architecture
Stakeholder requirements
Organizational structure
Organization’s portfolios
Monitoring data
Practice records
Organizational polices
External regulations and standards
Analyse stakeholder requirements
Define and agree the service configuration management approach
Communicate and integrate the service configuration management approach into the organization’s value streams
Review and adjust the service configuration management approach and procedures
Service configuration management approach
CMDB
Service configuration management communications and knowledge management materials
Requests for change and implementation initiatives
Service configuration management approach performance reports

Figure 3.1 shows a workflow diagram of the process.

Image of Figure 3.2 shows workflow diagram of managing a common approach to Service Configuration Management process

Figure 3.1 Workflow of the managing a common approach to service configuration management process

Table 3.2 describes the process activities.

Table 3.2 Activities of the managing a common approach to the service configuration management process
Activity

Example

Analyse stakeholder requirements

A configuration manager identifies key stakeholders who expect configuration information and requirements. These stakeholders typically include:

practice owners
value stream owners
product owners
service owners
resource owners
project managers.
The configuration manager documents, prioritizes, and analyses the requirements with the stakeholders. Configuration coordinators, configuration librarians, and external consultants may also be involved.

The configuration manager forms a configuration management team from those involved.

Define and agree the service configuration management approach

The configuration management team discusses and agrees a service configuration management approach (or plan).

The approach typically defines:

service configuration management policies for:
assessing the relevance of the configuration management information and planning the CMDB scope
optimization of the costs of service configuration information
verification of the CMDB data
integration of the service configuration management activities into the organization’s value streams and practices
review of the approach
CI types, taxonomy, and CI lifecycle models
naming and labelling conventions
automation and integration
CI identification plan: activities, targets, and KPIs
roles and responsibilities
monitoring and ongoing control procedures
verification procedures
reporting procedures
configuration discovery and reporting procedures, when necessary
funding and cost allocation.
Another decision to make is which CI attributes need to be included into the scope of the process of change realization control (see the change enablement practice guide for more information on this process), and if these attributes should be updated automatically or manually.

The approach is discussed and approved by the key stakeholders, including the sponsors and leaders of the organization.

Communicate and integrate the service configuration management approach into the organization's value streams

The agreed service configuration management approach is communicated to and discussed with stakeholders across the organization. These typically include practitioners who will be participating in the service configuration management activities, technical experts involved in practice automation, and other teams.
Stakeholders can decide how formal the training on the service configuration management controls and procedures should be. For the people most involved in the practice, formal initial training and periodic awareness trainings will be necessary.
The implementation of the service configuration management approach is performed in conjunction with the IT asset management, supplier management, change enablement, project management, organizational change management, workforce and talent management, relationship management, infrastructure and platform management, and software development and management practices, among others.
Review and adjust the service configuration management approach and procedures

The service configuration manager monitors and reviews the adoption, compliance, and effectiveness of the agreed service configuration management approach and procedures. This is done on an event-based (non-standard requests for information, identified gaps in CI data, new requirements) and interval-based basis.
Based on the reviews, the approach and/or its practical implementation may be changed. The service configuration management approach performance reports provide input for the approach update.
3.1.2 Capturing, managing and providing configuration information
This process is focused on updating, maintaining, and providing configuration information. It includes the activities listed in Table 3.3 and transforms the inputs into outputs.

Table 3.3 Inputs, activities, and outputs of the capturing, managing, and providing configuration information process
Key inputs

Activities

Key outputs

Service configuration management approach
Configuration data
Requests for configuration information
Service management records
Analyse resources and identify CIs
Confirm a CI lifecycle model
Follow the CI lifecycle model
Manage exceptions
Review the CI lifecycle model
Updated CMDB
Configuration information for stakeholders
Exception reports
CI lifecycle model review reports

Figure 3.2 shows a workflow diagram of the process

Image of Figure 3.3 shows workflow diagram of the capturing, managing, and providing configuration information process

Figure 3.2 Workflow of the capturing, managing, and providing configuration information process

Table 3.4 describes the process activities.

Table 3.4 Activities of the capturing, managing, and providing configuration information process
Activity

Description

Analyse resources and identify CIs

Upon discovering a new resource, resource type, or change in the existing CI, the resource owner or configuration librarian identifies the relevant CI model. If in doubt, the resource owner escalates the issue to a configuration manager.

Confirm a CI model

The configuration manager reviews the situation, confirms the CI model, or suggests a different one. If needed, the configuration manager may suggest adjustments to the selected CI model.

Follow the CI model

The resource owner, configuration manager, and/or configuration librarian follows the selected model. This typically includes:

capturing and updating the CI data in the CMDB at each stage of the CI lifecycle
ensuring the ongoing verification of the CMDB data
providing up-to-date CI information to relevant stakeholders.
Manage exceptions

If an exception occurs during the CI lifecycle, the configuration manager and resource owner handle it in line with organization’s service configuration management approach.
Deviations from the agreed procedures should be rare. It is important to ensure ongoing compliance and the maintenance of controls.
Exceptions may include non-standard ad-hoc requests for confiIf an exception occurs during the CI lifecycle, the configuration manager and resource owner handle it in line with organization’s service configuration management approach. Deviations from the agreed procedures should be rare. It is important to ensure ongoing compliance and the maintenance of controls. Exceptions may include non-standard requests, when necessary, for configuration information not included in the CI lifecycle model.
Exceptions should be documented to be used when reviewing the service configuration management approach, CI lifecycle models, and procedures.
Review the CI model

Upon significant exceptions, or regularly, the configuration manager and the configuration team review the CI models and update them based on collected feedback, reviewed requirements, CI records, verification reports, and new optimization opportunities.

3.1.3 Verifying configuration data
This process is focused on keeping configuration data complete, correct, and compliant. It includes the activities listed in Table 3.5 and transforms the inputs into outputs.

Table 3.5 Inputs, activities and outputs of the verifying configuration data process

Key inputs

Activities

Key outputs

Service configuration management approach
CMDB
Inventory data
Exception reports
Previous CMDB verification reports
Plan the verification activities
Identify a CI lifecycle model
Verify configuration data
Review the verification output
Define and implement corrective actions
Compose and communicate a CMDB verification report
Updated CMDB
Requests for changes
Improvement initiatives
CMDB verification report
Figure 3.3 shows a workflow diagram of the process.

Image of Figure 3.4 shows workflow diagram of the Verifying Configuration Data process

Figure 3.3 Workflow for the verifying configuration data process

Table 3.6 describes the process activities.

Table 3.6 Activities of the verifying configuration data process
Activity

Example

Plan the verification activities

A configuration manager (where necessary – assisted by a project management team) clarifies the purpose of the verification and plans the execution.
For periodic audits this results in a thorough audit plan defining the purpose, scope, activities and schedule of the audit, along with the roles and responsibilities.
For ongoing verification, verification activities and responsibilities are defined in the CI lifecycle model.
Identify a CI lifecycle mode	A configuration manager identifies a CI lifecycle model applicable to the organization’s resources, confirms the verification procedures for the CI, and assigns and communicates responsibilities for verification activities.
Verify configuration data	In line with the communicated procedures, teams responsible for the verification procedures collect inventory data. The configuration manager and the CI owner compare inventory data with CMDB data; this comparison should be automated wherever possible.
Review the verification output	All cases of CMDB-data incompleteness, incorrectness, or non-compliance, as well as unauthorized changes in resources, must be reviewed by the configuration manager, resource owner, or other people assigned according to the CI lifecycle model.
Define and implement corrective actions	The configuration manager, resource owner, or other people assigned according to the CI lifecycle model agree, document, and communicate corrective actions to the CMDB and/or organization’s resources. Improvement initiatives to the CI lifecycle model and/or service configuration management approach may also be suggested.
Compose and communicate a CMDB verification report	The configuration manager, resource owner, or other people assigned according to the CI model compose and communicate a CMDB verification report to relevant stakeholders. This report should include proposed corrective actions and improvement initiatives.
3.2 Value stream contribution
3.2.1 Service value streams
To perform certain tasks or respond to particular situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario. Once designed, value streams should be subject to continual improvement.

Definition: Value stream

A series of steps an organization undertakes to create and deliver products and services to consumers.

In practice, however, many organizations come to use of the value stream concept after having worked for a while (sometimes for years) without the value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the ‘As Is’ situation and the de-facto flows of work, and to analyse them in order to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding the existing value streams is critical to improving an organization’s performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services. Combined, the organizations’ value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations follow best practice recommendations for various service management practices, such as incident management, change enablement, software development, and many others. However, the practices are often adopted and organized in a siloed, isolated manner, just as they are presented in service management bodies of knowledge. In reality, a flow of work required to create or restore value, for a customer or another stakeholder, is almost never limited to one practice.

3.2.2 Service configuration management in service value streams
Although service configuration management plays a supporting role in the service provider’s service value streams, this role is important; as shown in Table 2.3, many practices rely on service configuration information to achieve their purposes.

Table 3.7 describes how the key service value streams involve service configuration management.

Table 3.7 Service configuration management in key service value streams
Value stream	The role of service configuration information
Creation of a new or changed product
or service

Assessment of the impact of the new requirements on the current services
Identification of the scope of required changes in products and services
Control of the implementation of the approved changes throughout the change
lifecycle
Scheduling of changes with minimum impact on the live services
Incident resolution	
Impact assessment during incident classification
Incident diagnosis, identification of the failed components
Identification of the teams/specialists responsible for the failed components
Mapping of incidents records to each other and other records (problem, change)
Planning and control of the changes required for incident resolution
Verification of the changes made to resolve an incident
Service request fulfilment	
Identification of the team/specialist to which to assign the request
Planning and control of the changes required to fulfil a request
Verification of the changes required to fulfil a request
Ongoing operation and maintenance	
Detection of unauthorized changes
Impact assessment of events
Impact assessment of proposed and scheduled actions and changes
Continual improvement of products and services	
Capacity, performance, availability, and continuity assessment and planning
Information security assessment and planning
Service cost allocation and planning
For all value streams, the service configuration management practice provides configuration information via the CMS either by maintaining it on an ongoing basis, or by gathering and publishing it on demand. It is unusual to see activities of service configuration management in the core workflow of a value stream, but many of the core activities use configuration information. The effectiveness and efficiency of some of the value stream activities (such as impact assessment and change planning) are highly dependent on the availability and quality of service configuration information. This makes the service configuration management practice critical for many service value streams.

3.2.3 Analysing a service value stream
3.2.3.1 The key steps of a service value stream analysis
The following are some simple and practical recommendations for service value stream analysis and mapping.

1. Identify the scope of the value stream analysis

This can be mapped to a particular product or service or applied to most or all of them. Similarly, service value streams may differ for different consumers; for example, incidents can be solved and communicated differently for internal and external customers, or for B2B and B2C products, or for services based on products developed inhouse or sourced externally.

2. Define the purpose of the value stream from the business standpoint

Make sure the stakeholder’s concerns are clearly understood, since they are the ones defining value. In the case of service configuration management, these are usually service provider teams who need configuration information. However, the information may also be useful for third parties involved in the management of the organization’s services.

3. Do the service value stream walk

Walk through or directly experience the steps and information flow as they go in practice (consider the Lean technique of Gemba walk):

a. Identify the workflow steps

b. Collect data as you walk

c. Evaluate the workflow steps

Typically, the criteria for evaluation are:

value for the stakeholder (does the step add value for the business stakeholder?)
effectiveness or performance (is the step performed well?)
availability (are required resources available to execute the step?)
capacity (are required resources enough?)
flexibility (are the required resources interchangeable within the step?).
d. Map the activities and the information flows

In an ideal situation, the flow goes smoothly without delays and pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

e. Create and review the timeline and resource level

Map out process times and lead times for resources and workload through the workflow steps.

4. Reflect on the value stream map (VSM)

Identify factors that might not have been entirely apparent at first. The information collected is used at this step to find the waste.

5. Create a ‘to be’ VSM

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

6. Using the ‘to be’ VSM, plan improvements

Refer to the continual improvement practice guide for a practical improvement model.

3.2.3.2 Service configuration management considerations in a service value stream analysis
To ensure that relevant service configuration management activities are included in service value streams, the following steps can be added to the above recommendations.

At the scoping step (1), identify the IT and business services related to the value stream and the involved business stakeholders. Are they in the scope of service configuration management, and to what extent? What configuration information may be relevant for the stakeholders?
During the service value stream walk (3a), identify the practices involved at every step and the configuration information they use. What configuration information which they may need is readily available? Is there a chance that ad-hoc configuration analysis will be needed? Are there third parties involved in the value stream? If so, what configuration information might they need? Can this information be shared with them, and what are the applicable information security policies?
During the workflow steps evaluation (3c), evaluate the service configuration information impact on the value stream effectiveness and efficiency. Special attention should be paid to steps with low business value, low performance, and availability or capacity issues. Does service configuration management create any delays? Is the configuration information sufficient? Is it provided in a timely and convenient way?
At the reflection and planning steps (4-5), ensure that the service configuration information is available throughout the value stream and its provision and use are optimized for business value.
Include the creation or update of CI lifecycle models and other elements of the service configuration management approach in the value stream improvement plans (step 6).
4. 
Organizations and people
4.1 Roles, competencies, and responsibilities
The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended.

Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

Table 4.1 Competency codes and profiles
Competency code

Competency profile (activities and skills)

L

Leader Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes.

А

Administrator Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements.

C

Coordinator/Communicator Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns.

М

Methods and techniques expert Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement.

Т

Technical expert Providing technical (IT) expertise and conducting expertise-based assignments.

4.1.1 Configuration manager and configuration coordinator roles
The key role of the service configuration management practice is the configuration manager.

The configuration manager oversees the service configuration management approach and CI models for all CIs that are in scope. In many organizations, the configuration manager role is performed by a dedicated person. In larger organizations operating in many locations or in multiple industries, the configuration manager is supported by a team of configuration coordinators who have very similar responsibilities, but who specialize in a particular territory, industry, or other part of the organization.

This configuration manager role is typically responsible for:

managing the service configuration management approach
communicating the service configuration management approach and procedures
integrating the service configuration management approach into value streams
deciding whether to include new resources and resource types in the scope
managing exceptions
ensuring CI models are followed
ensuring the CMDB contains valid data
ensuring the organization complies with practice-related requirements, if applicable
optimizing and automating the practice
reporting on the service configuration management performance.
4.1.2 Configuration librarian
Some organizations introduce the role of configuration librarian. This role focuses on manually updating configuration data, verifying the CMDB on an ongoing and periodic basis, and processing ad-hoc requests for configuration information.

This role is important in organizations with a low level of automation and high demand for ad-hoc, non-standard configuration information. It is rarely supported by dedicated resources and may be performed by resource owners.

4.1.3 Resource owner role
A resource owner (sometimes called a resource custodian) is a person or team that ensures that a resource or group of resources in the organization are utilized correctly. They ensure that relevant CI models are consistently applied to the resource throughout its lifecycle in the context of the organization’s practices and value streams.

4.1.4 Other roles involved in the service configuration management activities
Examples of other roles involved in change enablement activities are listed in Table 4.2.

Table 4.2 Examples of roles with responsibility for service configuration management activities

Activity	Responsible roles	Competency profile	Specific skills
Managing a common approach to service configuration management	
Analyse stake holder requirements	
Configuration manager
Configuration coordinator
Practice owner
Product owner
Service owner
Resource owner
Project manager
TC	
Good knowledge of the organization, its resources and available information
Good understanding of the service configuration management practice and its role in the organization
Define and agree the service configuration management approach	
Configuration manager and coordinators
Product and service architects
Consultants
MTC	
Good understanding of stakeholder requirements, service configuration management methods and tools, available sources of information, and means of automation
Communicate and integrate the service configuration management approach into the organization’s value streams	
Configuration manager and coordinators
Resource owners
Key users of the configuration information
CLMA	
Leadership and communication skills
Good understanding of the agreed approach
Good understanding of stakeholder requirements
Review and adjust the service configuration management approach and procedures	
Configuration manager
Product and service architects
Key users of the configuration information
MCTA	
Good understanding of stakeholder requirements, service configuration management methods and tools, available sources of information, and means of automation
Capturing, managing, and providing configuration information
Analyse resources and identify CIs	
Configuration manager
Configuration coordinator
Configuration librarian
Resource owner
TA	Good knowledge of the organization’s resources and relevant CI models
Confirm a CI lifecycle model	
Configuration manager
Configuration coordinator
Configuration librarian
Resource owner
MTC	
Good knowledge of the organization’s resources and relevant CI models
Good knowledge of the organization’s approach to service configuration management
Follow the CI lifecycle model	
Configuration librarian
Resource owner
AT	Good knowledge of the CI model
Manage exceptions	
Configuration manager
Configuration coordinator
Configuration librarian
Resource owner
TCMA	
Good knowledge of the CI model
Good knowledge of the organization’s approach to service configuration management
Understanding stakeholder needs
Review the CI lifecycle model	
Configuration manager
Resource owner
MCTA	
Good knowledge of the CI model
Good knowledge of the organization’s approach to service configuration management
Understanding stakeholder needs
Verifying configuration data
Plan the verification activities	
Configuration manager
Configuration coordinator
Configuration librarians
Resource owner
MCA	
Good knowledge of the service configuration management approach and the CI lifecycle models
Good understanding of the organization’s objectives and priorities
Good knowledge of the configuration verification methods and tools
Identify a CI lifecycle model	
Configuration manager
Configuration coordinator
Configuration librarian
Resource owner
TA	
Good knowledge of the CI model
Good knowledge of the organization’s approach to service configuration management
Verify configuration data	
Configuration manager
Configuration coordinator
Configuration librarian
Resource owner
TA	
Good knowledge of the CI model
Good understanding of configuration data sources and means of automation
Knowledge of the relevant organizational resources
Review the verification output	
Configuration manager
Configuration coordinator
Configuration librarian
Resource owner
TA	
Good knowledge of the CI model
Good knowledge of the organization’s approach to service configuration management
Understanding of the configuration data sources and means of automation
Define and implement corrective actions	
Configuration manager
Configuration coordinator
Resource owner
TMCA	
Good knowledge of the CI model
Good knowledge of the organization’s approach to service configuration management
Understanding stakeholder needs
Compose and communicate a CMDB verification report	
Configuration manager
Configuration coordinators
Resource owners
CAT	
Good knowledge of the CI model
Good knowledge of the organization’s approach to service configuration management
Understanding stakeholder needs
4.2 Organizational structures and teams
Two types of teams support this practice: a team for ongoing management of service configuration information and a team for regular review of the service configuration management approach. The exact structure and positioning of the teams depend on the size and structure of the organization.

Larger organizations have a specialized team of configuration manager(s) and configuration coordinator(s): dedicated specialists focused primarily on the service configuration management practice (in some organization these toles will focus on both the service configuration management and IT asset management practices). This team may be supported by external consultants when specific expertise is needed; typically this will be to review and update the service configuration management approach. Configuration coordinators may be focused on particular regions, locations, products, or clients, depending on the organizational and service architecture.

In smaller organizations, the configuration management specialist team is usually virtual, formed of people with other roles and tasks to perform. The ongoing activities embedded in the service value streams can be fulfilled by resource owners and coordinated by product and service owners, acting as configuration coordinators.

Wider temporary configuration teams may be formed in such organizations to review and update the service configuration management approach. These teams represent multiple stakeholders and may include:

configuration managers
practice owners

product owners

service owners

resource owners

service architects

project managers

other stakeholders or representatives.

5. 
Information and technology
5.1 Information exchange
The effectiveness of the service configuration management practice is based on the quality of the information used. This information includes, but is not limited to, information about:

organizational strategy
organizational architecture
the organization’s portfolios
stakeholder requirements and needs for configuration information
applicable regulatory requirements
configuration data from internal and external sources
technology trends
CI-related records from management practices
financial data
IT asset data.
This information may take various forms, depending on the CI types, organizational requirements, and service configuration management automation. The key inputs and outputs of the practice are listed in Chapter 3.

5.2 Automation and tooling
The CMS solution is often a part of integrated service management tools, or else designed for easy integration with them. It ensures the effective exchange of configuration information between the practices. Typically, key functionalities of CMS solutions include:

CI discovery
Updating and managing CI records
Modelling of relationships between CIs
CI version control
Impact assessment
Data health checks and verification
Configuration data integration and reconciliation.
Capturing configuration data, ensuring that configuration data is updated at every relevant change of status of the CIs, and automating other activities is very important for the service configuration management practice. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to the full automation of activities where technology solutions remove the need for human intervention. Where automation is possible and effective, it may involve the solutions outlined in Table 5.1.

Table 5.1 Automation solutions for service configuration management activities
Automation tools	Application in service configuration management
CMS tools	
Discover CI data
Store and manage CI data (create, update and delete CI records, display and modify attributes)
Integrate different databases
Identify and reconcile data from different data sources
Monitor and control CMDB health
Verify data
Certify CMDB data (compliance tool)
Workflow management and collaboration tools	
Support planning and review activities of the practice
Support communications during ad-hoc provision of configuration information
Integrate the CMS into service value streams (mapping of CIs and service management records; access to CMS in the context of other practices)
Manage exceptions
Inventory and discovery tools	Gather and verify information about the CIs
Knowledge management tools	
Share and utilize guidelines for service configuration management
Support ad-hoc provision of service configuration
Classification and analysis tools	Analyse stakeholders requirements and CI data
Work planning and prioritization tools	Plan and track improvement initiatives
Analysis and reporting tools	Practice measurement and reporting
Because of the growing adoption of digital infrastructure solutions (such as infrastructure-as-a-code, virtual machines and networks, and various cloud services), new dilemmas and challenges frequently appear.

For example, new types of CIs and CI relationships have emerged. In these instances, information about relationships between hardware servers and the virtual machines running on them may be relevant in the context of a service model and therefore expected to be available through the service configuration management practice.

These relationships are usually managed by virtual machine monitor (VMM, also known as Hypervisor) systems. However, there is some debate about whether this information should be obtained directly from the VMM system or imported into the configuration management system (CMS). Similar practical questions are applicable to virtual networks, environment configuration scripts, and other means of virtual solutions management.

There is no universal answer and no recommended solution for defining which resources should be under the service configuration management practice’s control. These decisions should be driven by the value of the configuration information to stakeholders and costs of obtaining and maintaining the information.

Detailed descriptions of how tools listed in Table 5.1 support the practice’s activities are outlined in Table 5.2.

Table 5.2 Details of automation of the service configuration management activities
Process activity

Means of automation

Key functionality

Impact on the effectiveness of the practice
Managing a common approach to service configuration management	
Analyse stakeholder requirements

Workflow management and collaboration tools

Collection and analysis of requirements, discussions, and prioritization

Medium	
Define and agree the service configuration management approach

Workflow management and collaboration tools
CMS tools
Discussions, prioritization, data and workflow modelling, integration, and data exchange

High	
Communicate and integrate the service configuration management approach into the organization's value streams

CMS tools
Discovery and monitoring tools
Service management record-keeping tools
Integration with other practices for data exchange

High	
Review and adjust the service configuration management approach and procedures

Workflow management and collaboration tools
CMS tools
Analysis and reporting tools
Discussions, prioritization, data and workflow modelling, integration, and data exchange

High	
Capturing, managing, and providing configuration information
Analyse resources and identify CIs

CMS tools
Inventory and discovery tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation
CI models library
High

Confirm a CI lifecycle model

CMS tools
Inventory and discovery tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation
CI models library
High

Follow the CI lifecycle model

CMS tools
Inventory and discovery tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation
CI models library
High

Manage exceptions

CMS tools
Inventory and discovery tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation
CI models library
High

Review the CI lifecycle model

CMS tools
Inventory and discovery tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation
CI models library
High

Verifying configuration data

Plan the verification activities

Inventory and discovery tools
CMS tools
Work planning and prioritization tools
Workflow management and collaboration tools
Reports of the CIs requiring additional verification
Scoping of audits and ongoing verification
Task generation, assignment, and coordination
Record keeping, integration of multiple practices
Medium to High
Identify a CI model	
CMS tools
Inventory and discovery tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation
CI models library
High
Verify configuration data	
CMS tools
Inventory and discovery tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation and audit
Data health monitoring and verification
CI models library
High
Review the verification output

CMS tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation and audit
Data health monitoring and verification
High

Define and implement corrective actions

CMS tools
Workflow management and collaboration tools
Integration with other practices for data exchange
CMDB navigation and audit
Configuration baselines library
CI models library
High

Compose and communicate a CMDB verification report

CMS tools
Workflow management and collaboration tools
Communication, discussions
Record-keeping
Medium

5.2.1 Recommendations for the automation of service configuration management
The following recommendations can help when applying automation to service configuration management:

Support the value stream Configuration information is only valuable in the context of the organization’s service value streams. The CMS tool should be either a part of the ITSM workflow management and collaboration system or have good integration with it. It is important to be able to map CI records to other records such as incidents, problems, changes and so on. Access to information about CIs for different users and situations should be adjustable according to the information security policies. Focus on value. Think and work holistically.
Do not overcomplicate the CI attributes, lifecycle models, and relationships An up-to-date CMDB with the most important information is more valuable than a comprehensive CMDB which is never up to date. Add new classes of CIs, new attributes, and new types of relationship only when it has a solid justification and demand for the information. Keep it simple and practical.
Pay attention to automated measurement and reporting from the beginning The amount of information in a CMS is large, and tends to keep growing, and manual analysis very quickly becomes impossible. Aim to automate analysis of the CMDB utilization, detection of errors, verification of changes and other repeating operations. Optimize and automate.
Ensure effective integration with discovery and inventory tools Verification is a key process of this practice, and it cannot be effectively performed manually. Make sure that baselines are created and used to control the correctness of the configuration data, make sure that unauthorized changes are detected effectively, and data discrepancy analysis is mostly automated.
Ensure clear and useful visualization of the CMDB Many use case scenarios require an interactive visualization of configuration items and the relationships between them.
Expand the scope of the CMDB only when the current scope is effectively managed When reviewing the practice, consider removing unused attributes or classes before adding new ones. Maintain a manageable size of CMDB. Consider starting with the CMDB structure suggested by the vendor before tailoring it. Progress iteratively with feedback.
6. 
Partners and suppliers
6.1 Service configuration management in the service relationship ecosystem
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). This means that organizations constantly handle resources that are provided as part of third-party services. Similarly, organizations’ resources are widely used by their service consumers. This requires the effective coordination of the service configuration management practice between the members of the service relationship ecosystem. The exact level of coordination depends on the type of service relationship. The closer the relationship and higher the trust, the more configuration information can be shared and management activities performed together. At minimum, an exchange of limited configuration data between the organizations is established: at maximum, a wide integration or sharing of CMSs can be considered.

6.2 How partners and suppliers support the practice
Partners and suppliers integrated into the service provider organization usually have access to the organization’s CMS so that they can effectively fulfil their roles.

Partners and suppliers are often involved in the service provider’s value streams in various roles, and some of these roles include using and sometimes updating configuration information. This should be done in line with the CI lifecycle models and agreed in the contracts with the partners and suppliers.

Partners and suppliers can support the service configuration management practice by advising the service provider on the development and review of the service configuration management approach, integration of tools, and CMDB verification.

Third parties supply automation tools for many management practices, but this role of suppliers and partners is particularly important for service configuration management. It is likely that the practice will be supported by multiple tools; at least CMS tools, inventory and discovery tools, and ITSM workflow management and collaboration tools. It is very important to ensure effective integration across these tools, and organizations often involve third-party system integrators to help with the integration projects.

7. 
Capability assessment and development
7.1 The practice capability levels
The practice success factors described in section 2.4 cannot be developed overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:

Level 1 The practice is not well organized; it’s performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

Level 2 The practice systematically achieves its purpose through a basic set of activities supported by specialized resources.

Level 3 The practice is well-defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

Level 4 The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

Level 5 The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level 2 to level 5. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well-defined and organized.


Figure 7.1 Design of the capability criteria

This approach results in every practice having up to 30 capability criteria based on the practice PSFs and mapped to the four dimensions of service management. The number of criteria at each level differs: the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

Table 7.1 outlines the capability criteria that are defined in the ITIL maturity model for the service configuration management practice

Table 7.1 Service configuration management capability criteria
PSF	Criterion	Dimension	Capability level
Ensuring that the organization has relevant configuration information about its products and services	Key users of the configuration information and their requirements are identified	Value streams and processes	2
Information about product and service
configuration is available when needed and meets user requirements

Information and technology	2
Procedures for requesting and obtaining configuration information are defined and communicated to relevant stakeholders	Value streams and processes	3
Responsibility for the management of configuration information is clearly defined	Value streams and processes	3
Configuration information covers relevant details about third-party services	Partners and suppliers	3
Configuration information is managed using an integrated information system	Information and technology	4
Configuration information is exchanged between the organization and its suppliers and partners, where needed	Partners and suppliers	4
The quality and availability of the configuration information is continually reviewed and improved	Value streams and processes	5
Ensuring that the costs of providing configuration information are continually optimized	Costs of providing configuration information are identified and tracked	Value streams and processes	2
Users of configuration information are aware of and satisfied with the procedures and interfaces for requesting and obtaining the information	Value streams and processes	2
The processes and tools for the discovery, management, and provision of configuration information are designed for cost efficiency	Value streams and processes	3
Configuration management is integrated with internal and external sources of relevant data	Information and technology	4
The costs of providing configuration information are regularly reviewed and continually improved	Value streams and processes	5
These capability criteria can be used by organizations for self-assessment and improvement of the practice.

7.2 Capability self-assessment
A self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team in the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed.

Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider’s employees.

If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.

If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met; what is missing in the organization? Why? How can it affect the service consumer and the quality of the IT services? What can be done to meet the criteria that are currently missed

The same approach is applied at every next level; the practice is considered to be at the level, where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.

7.3 Service configuration management capability development
Management practices should support the achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at capability level 5. A higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but it comes with a cost; cost of management, automation, and training, for example. To achieve optimal performance with sufficient level of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and Table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.


Figure 7.2 The capability development steps and levels

Table 7.2 The service configuration management capability development steps

Capability level	Define, agree, and implement	Comment for service configuration management	Chapter (for recommendations)
2	Purpose and objectives	Key stakeholder groups and requirements, domains and types of CIs	2.1
Scope	2.3
Processes and activities	Workflows, CI lifecycle models, roles and responsibilities, automation and information exchange	3.1
Roles and responsibilities	4
Tools and procedures	5
3	Dependencies and integration	Integration in the organization's service value streams	3.2
Use of integrated information system	5
Suppliers and other parties involved in service configuration management	6
4	Measurement and reporting	Metrics	2.5
5	Continual improvement	Regular review of practice and the service configuration management capability development	2.4, 2.5, 7
8. 
Recommendations for practice success
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:

focus on value
start where you are
progress iteratively with feedback
collaborate and promote visibility
think and work holistically
keep it simple and practical
optimize and automate.
In Table 8.1, recommendations for the success of the service configuration management practice are linked to the relevant guiding principles.

Table 8.1 Recommendations for the success of service configuration management
Recommendation	Comments	ITIL guiding principles
Design the practice to provide service configuration information required by the organization’s stakeholders	
The value of the practice is defined by those using the configuration information.
Make sure the requirements of the stakeholders are clear, and discussed with the stakeholders before building the CMDB.
A comprehensive ‘perfect’ CMDB is unlikely to be justified as the costs of creating and maintaining it would be higher than the value from it.
Focus on value
Collaborate and promote visibility
Systematically review the scope of and level of details in the CMDB	
Analyse the utilization of the configuration data.
Consider removing attributes, relationships, or even CIs with unused CMDB information, especially if the information is verified and updated manually.
Expand or decrease the scope of the CMDB based on the changing requirements.
Collaborate and promote visibility
Progress iteratively with feedback
Keep it simple and practical
Make CMDB verification an ongoing activity	
Regular audits are not enough. Combine ongoing verification with regular selective audits, aiming for full coverage of the CMDB over a period of a few months.
Aim to automate CMDB verification wherever possible.
Where manual verification is required, integrate it into the operations and maintenance value streams and make sure it is part of the regular activities.
Optimize and automate
Keep it simple and practical
Progress iteratively with feedback
Automate handling of the configuration data where reasonably possible	Service configuration data should be reliable. If the data is handled manually, reliability can only be achieved by keeping the amount of data to minimum, which would limit the benefits of the practice. To support the needs of the organization and control larger amounts of data, CMDB should be effectively automated.	Optimize and automate
Develop the practice continually but don’t overcomplicate it	
Start with the most critical configuration data available in the available tools.
Add complexity where it is justified and manageable.
Aim to demonstrate value from the practice before making a significant investment.
Start where you are
Progress iteratively with feedback
Keep it simple and practical
Involve third parties	Make sure that partners and suppliers involved in the organization’s value streams have access to the relevant configuration information but use it in line with the organization’s policies.	Collaborate and promote visibility
Demonstrate business value	
Measure the practice and produce regular reports and dashboards for internal (within the service provider) and external (service consumer) stakeholders.
Use dashboards for the current status and regular reports for analysis and highlights.
Focus on value
Collaborate and promote visibility
9. 
Acknowledgements
PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following people:

Authors
Tatiana Peftieva, Roman Jouravlev

Contributors
Anton Lykov, Evgeniy Shilov

Reviewers
Dinara Adyrbai, Graham Heard, Antonina Douannes, Anton Lykov, Irina Matantseva

2023 Revision
Antonina Douannes, Adam Griffith, Roman Jouravlev, Kaimar Karu, Olga Masalina, Avinash Singh

