---
title: "Service configuration management: ITIL4 Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# Overview
<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>The purpose of the service configuration management practice is to ensure that accurate and reliable information about the configuration of services, and the configuration items that support them, is available when and where it is needed. This includes information on how configuration items are configured and the relationships between them.</p></td></tr></tbody></table>

Organizations use resources to create and deliver products and services. These resources may belong to the organization, or they may be available as part of a service the organization consumes. The service configuration management practice collects and manages information about a variety of resources, typically including hardware, software, networks, buildings, people, suppliers, products, services, and documentation. The resources in the scope of the practice are called configuration items (CIs).

<table><tbody><tr><td><p><strong>Definition: Configuration item</strong></p></td></tr><tr><td><p>Any component that needs to be managed in order to deliver an IT service.</p></td></tr></tbody></table>

The primary objective of the service configuration management practice is to efficiently provide useful information to the organization. The scope of the components under its control should be defined by their usefulness and efficiency. The main factors shaping this practice are the usefulness of the configuration information and the costs of obtaining and maintaining it.

<table><tbody><tr><td><p><strong>Tip</strong></p></td></tr><tr><td><ul><li>Resources that cannot be individually managed are usually not considered CIs. For example, the knowledge used by an analyst to manage incidents is important but will probably not be treated as a CI. At the same time, virtual resources, such as a virtual server or network, may be CIs and require similar management as physical resources.</li><li>The service configuration management practice is focused on resources that are important for product and service management, regardless of whether these resources are the organization’s property or provided as part of a third-party service. However, different lifecycle models and controls may apply to these two groups of resources.</li></ul></td></tr></tbody></table>

The service configuration management practice is an important element of service management. This practice is beneficial for both the service provider and their service consumers.

Benefits for the service provider include:

*   improved risk management due to better understanding of the relationship between the CIs
*   better planning and control of changes
*   better understanding and management of the capacity, availability, and security of IT services and components
*   understanding and accurate allocation of service costs
*   better understanding, planning and control of service performance
*   better cause and effect analysis, which improves effectiveness and efficiency of incident and problem management.

Benefits for the service consumer include:

*   more realistic and accurate service level agreements
*   higher quality of IT services
*   better management of IT risks.

### 2.1.1 Service configuration models

The service configuration management practice involves identifying and documenting the connections and relationships between configuration items. This usually results in models (known as service configuration models, service resourcing models, or functional and financial service models). These models can be focused on various aspects of the service architecture and the relationships between the components. They represent various level of abstraction, from high-level functional models (as shown in Figure 2.1) to an accurate mapping of the connections and relationships between physical and digital CIs.

![Image of Figure 2.1 show a diagram of the high-level service configuration model](Service%20configuration%20management%20ITIL4%20Practice%20Guide/Picture1.png)

**Figure 2.1 A high-level service configuration model**

Service configuration models are used for various purposes, including:

*   impact analysis
*   cause and effect analysis
*   risk analysis
*   cost allocation
*   availability analysis and planning.

Service configuration models should be designed and maintained to meet stakeholder needs.

The service configuration management practice is a highly-automated practice. It relies on the collection, maintenance, and control of large amounts of configuration data and often includes building, maintaining, and presenting complex configuration models. The practice involves gathering data from multiple sources, integrating it and presenting in a meaningful way. Specialized tools are typically used alongside monitoring, discovery, analytical, and record-keeping systems.

This practice often allows configuration information to integrate with records that are managed as part of other practices, including the incident management, change enablement, problem management, monitoring and event management, and service request management practices, among others. However, some configuration models are difficult or impossible to automate; they require manual data maintenance and/or relationship mapping. Examples include user data, organizational structures, contracts with suppliers and partners, and so on. Manual efforts and associated costs, alongside automation and integration costs, should be considered when the practice is being designed and improved.

### 2.2 Terms and concepts

##### 2.2.1 IT assets and configuration items

The service configuration management and IT asset management practices, as well as IT assets and CIs are closely related, and share much of the same information and tooling; each has some critical dependencies on the other. Nevertheless, these are distinct concepts. The definition of a configuration item was already given in section 2.1, but is repeated here for comparison with that of an IT asset.

<table><tbody><tr><td><p><strong>Definition: Configuration item</strong></p></td></tr><tr><td><p>Any component that needs to be managed in order to deliver an IT service.</p></td></tr></tbody></table>

<table><tbody><tr><td><p><strong>Definition: IT asset</strong></p></td></tr><tr><td><p>Any financially valuable component that can contribute to the delivery of an IT product or service.</p></td></tr></tbody></table>

As Figure 2.2 illustrates, some items can be both CIs and IT assets, and some items are specifically just an IT asset or just a CI.

For example, a portable storage device may be considered an IT asset but not a CI. Which IT assets are, and are not, recognized as CIs depends on how an organization’s services are defined and configured, and which IT assets are needed for them.

Conversely, some CIs may not be IT assets. For example, a configuration script or documented knowledge artefacts may be considered CIs but not assets. There is no single rule as to how these should be defined. Whether something is considered to be an IT asset or a CI is not an inherent property of the item. The distinction will depend on how an organization defines its services and what it needs to manage.

![](Service%20configuration%20management%20ITIL4%20Practice%20Guide/Figure_2.2.PNG)

Another differentiator between IT assets and CIs is the information and attributes related to them. The attributes for CIs are focused more on the information that is critical for the management of the CI in relation to service utility and warranty, whereas the attributes for IT assets are focused more on the management of the asset itself (see section 2.2.3 for more information on the categorization and attributes of CIs).

It is important to initiate the discussion within an organization and to understand the distinction between IT assets and CIs to properly comprehend the differences in the scope of the configuration management and ITAM practices (for more information, see sections 2.3 in this and the IT asset management practice guides). This understanding will help to define the relationships between the practices and ensure that data from both is used in a mutually beneficial way.

#### 2.2.4 Configuration management systems and databases

The service configuration management practice involves a significant amount of data from various sources and depends on the ability to collect, integrate, process, and present this data in a reliable, cost-efficient way. CMSs are designed to fulfil this need. Because of the multiplicity of data sources for the practice, a CMS is usually a complex system that combines one or more specialized solutions and integrations with sources of configuration data.

<table><tbody><tr><td><p><strong>Definition: Configuration management system</strong></p></td></tr><tr><td><p>A set of tools, data, and information that is used to support the service configuration management practice.</p></td></tr></tbody></table>

A key functionality of a CMS is keeping and managing CI records and the relationships between them. This is usually achieved with one or more configuration management databases (CMDBs).

<table><tbody><tr><td><p><strong>Definition: Configuration management database</strong></p></td></tr><tr><td><p>A database used to store configuration records throughout their lifecycle. It also maintains the relationships between configuration records.</p></td></tr></tbody></table>

Sometimes the terms ‘CMS’ and ‘CMDB’ are used interchangeably, usually in accordance with the CMS definition.

In some organizations, a CMS is used to integrate configuration management data in a CMDB with IT asset data in the asset management database (AMDB).

Other organizations tend to use a fully combined asset configuration database. Such an approach allows them to manage both IT assets and CIs from within one facility. In this scenario, distinguishing between an IT asset and a CI is achieved using ‘label’ fields. ‘Asset attributes’ and ‘CI attributes’ can then be defined and recorded for any component as needed. More information on the CMS and its utilization can be found in Chapter 5.

In some cases, it is more efficient to retrieve configuration data upon request than to make it permanently available in a CMS. There is no correct answer and no recommended solution for defining which data should be included into a CMS. These decisions should be driven by the value of the configuration information to stakeholders and the costs of obtaining and maintaining the information.

#### 2.2.3 CI categorization and attributes

Services and products comprise numerous CIs and connections between them. When defining and categorizing CIs, an organization should find a presentation method that helps all stakeholders, including non-technical roles, to comprehend these complex structures. To categorize CIs and define data representation levels, the configuration management team should rely on service architecture and continuously collaborate with the service architecture team throughout the lifecycle of the CI.

As an example, CIs may be grouped into the following domains:

*   **Business service domain** These CIs represent the business capability (service offering or business service) that the organization provides to its customers.
*   **Product domain** These CIs represent products and all the distributed components that each product may encompass (as such they are vital for documentation, images, installation scripts and other aspects of the products). Product CIs may support one or many business services. Business services may include multiple products. Products can contain one or many applications, however they may consist of a wider range of components beyond applications.
    

*   **Application domain** These CIs represent applications and all the distributed components that make them work (as such they are vital for documentation, images, startup script and other aspects of the application). Application CIs may support one or many business services. Business services may include multiple applications. Some organizations separate the application and product domains. Application domain CIs may include:

\- Elements that are vital for the application documentation (requirements, design documents, disaster recovery plans, and so on)

\- Licenses (agreements, contracts, and so on)

\- Configuration files or scripts (for example, installation scripts)

\- Support tools (log analysis tools, testing tools, and so on).

*   **End user CIs domain (sometime also named Office CIs domain)** These are the CIs used by end-users to perform their daily tasks. These CIs include, among others:

\- Printers

\- Mobile devices

\- User workstations

\- Peripheral devices

*   **Infrastructure domain CIs (sometimes also named the technical service domain)** These CIs are technical infrastructure components (such as servers, storage devices, network gear and so on) that support one or more application services. Some organizations choose to divide the infrastructure domain into smaller domains to mirror the infrastructure architecture. Examples of these domains may include, but are not limited to:

\- middleware CI domain

\- data center CI domain

\- network CI domain

\- server CI domain and other.

CIs of different types have different key attributes. Attributes are data elements which help to describe the CIs under a relevant CI domain. The attributes may have different lifecycles and different levels of control from within the organization. The differences are usually reflected in the way information about the CIs is collected, stored, controlled, and presented throughout their lifecycles. As CIs are often structured in a domain (classes) hierarchy, each lower subdomain may inherit the attributes of its parent CI. Example of the attributes of CIs within different domains are shown in Table 2.1.

<table><tbody><tr><td><p><strong>Infrastructure domain CIs</strong></p></td><td><p><strong>Application domain CIs</strong></p></td><td><p><strong>Business service domain CIs</strong></p></td></tr><tr><td><ul><li>Owner</li><li>Memory</li><li>Processor</li><li>CPU size</li><li>Energy consumption</li><li>Lifecycle state related to the service (pipeline, active, retired)</li></ul></td><td><ul><li>Owner</li><li>Version</li><li>Installation date</li><li>License</li><li>CO2 emission</li><li>Lifecycle state related to the service (pipeline, active, retired)</li></ul></td><td><ul><li>Owner</li><li>Business impact</li><li>Contract</li><li>SLA</li><li>Amount of waste and e-waste</li><li>associated with the service</li><li>Lifecycle state related to the service (pipeline, active, retired)</li></ul></td></tr></tbody></table>

Much of the data required for describing CIs is stored and managed in other databases. This includes data on:

*   customers
    

*   users

*   locations

*   organizational units

*   service agreements and other relevant documentation

*   information from other practices (such as incidents, requests, changes, problems associated with a relevant CI).

Some attributes can be managed as separate CIs in the scope of the relevant domain and vice versa (for example, location can be an attribute of the hardware domain or separate CI connected to hardware; licence can be an application domain CI attribute, or a separate CI linked to the application). CIs of different domains are mapped to each other, thus another important CI attribute is the relationship between them. The information about the relationships allows for analysis of the dependencies between CI instances when planning changes, diagnosing incidents, or designing a new service. This information is also beneficial for capacity management and calculating the costs of IT services.

The relationship between CIs, along with the relationship type, should be defined, documented, and visualized in the CMDB. Examples of how organizations may categorize different types of relationships include:

*   Dependency: one CI depends on another, for example, a server may depend on a network switch.
*   Communication: CIs communicate with each other, for example, a web server communicates with a database.
*   Parent/Child: a CI is made up of other CI, for example, a virtual machine host may contain multiple virtual machines.
*   Aggregation: multiple CIs are combined to form a single CI. For example, a storage array may be made up of multiple hard drives.
*   As mentioned before all decisions about CI data should be driven by the usefulness of the CI to stakeholders and the costs of obtaining and maintaining the information.

#### 2.2.4 CI lifecycle models

<table><tbody><tr><td><p><strong>Definition: CI lifecycle model</strong></p></td></tr><tr><td><p>A comprehensive set of rules, policies and guidelines that define, standardize and optimize the organization’s approach to managing the lifecycle of CI records within a specific domain or any other category.</p></td></tr></tbody></table>

Each CI lifecycle model may have its own lifecycle and management approach. However, the model should define all stages of the CI record’s lifecycle from creation to deletion, and provide guidelines to ensure the accuracy, reliability and security of the CMDB data.

Organizations often define a model for each CMDB domain, but a model can also be defined for any specified group of CIs based on the organizational needs. For example, a specific model can be created for CIs in a certain location, or a model can be defined for all the CIs connected to a certain business service.

When creating a model, CIs can be grouped into types based on their features, including, but not limited to, the following attributes:

*   related IT asset type
*   types of stakeholders
*   responsible party or parties
*   financial significance and reporting requirements
*   level of tangibility (from very tangible hardware equipment to intangible licences, data, cloud computing capacity, services, or subscriptions)
*   location (for example, physically on the premises, physically in co-location or on the provider’s premises, cloud resources, or licences on the organization’s own servers) and method of access.

CI lifecycle models define, for a particular type of CI:

*   CI type owner(s)
*   naming and labelling policy
*   key group and individual attributes
*   key relationships (taxonomic and functional)
*   key lifecycle stages
*   procedures and/or guidelines for CI identification, ongoing control, verification, and audit
*   responsibility for following the model
*   key stakeholders (interested in the configuration information) and their requirements
*   key reports and dashboards presenting the configuration information, where applicable.

The CI lifecycle models combine to form CMDB data governance.

CMDB data governance is a vital part of data quality. It is the set of policies, guidelines and rules that govern the collection, storage, analysis, and use of data in the CMDB. For example, when an organization decides on the level of granularity of data for a service, data governance defines how to record the attributes of smaller items inside of a top-level CI.

The design of effective CI lifecycle models and CMDB data governance in general requires the involvement of key stakeholders, such as representatives of the service architect, security, and IT operations teams, as well as other relevant CMDB data users.

#### 2.2.5 Service configuration management and sustainability

Digital sustainability is a developing area at the intersection of digital service and product management, electricity markets, data science and sustainable development (see ITIL 4 Sustainability in Digital and IT for more information on digital sustainability).

<table><tbody><tr><td><p><strong>Definition: Sustainability</strong></p></td></tr><tr><td><p>A business approach focused on creating long-term value for society and other stakeholders, by addressing the risks and opportunities associated with economic, environmental, and social developments.</p></td></tr></tbody></table>

Service configuration management supports digital sustainability by including relevant attributes in the CI information. These may include:

*   Carbon footprint
*   Source information (whether the supplier of the CI is known and meets sustainability requirements)
*   Recycling information (may apply to the CI materials and to the end of CI lifecycle).

The organization may decide to store information in the asset management database, rather than the CMDB. However, even if no sustainability-specific attributes are used in the CMDB, accurate, reliable, and relevant information about CIs and their relationships can make a significant contribution to the following areas of an organization’s sustainability journey:

*   E-waste reduction

*   Energy efficiency

*   Digital carbon footprint optimization

*   Cybersecurity.

Beyond supporting sustainability initiatives, the service configuration management practice should be also be designed and executed in a sustainable way. To reduce the digital carbon footprint of the CMDB, the amount of data stored within it should be sufficient but not excessive; the integration of the CMDB with the external databases should be secure and reliable; and processes and procedures should be compliant with both internal policies and external regulatory standards.

#### 2.2.6 CI verification and audit

As an important source of information for decision-making, CI records and configuration models are subject to continual verification and regular audits.

Service configuration data should:

*   reflect the actual attributes, statuses, and relationships of the CIs
*   highlight deviations from the baseline configuration(s)
*   provide sufficient data to restore or re-create the approved configuration(s).

<table><tbody><tr><td><p><strong>Definition: Baseline configuration</strong></p></td></tr><tr><td><p>A configuration of a product, service, or other configuration item, that has been formally reviewed and agreed. It serves as the basis for further activities, such as planning, development, and usage.</p></td></tr></tbody></table>

The service configuration management practice ensures that relevant CI data is captured in the CMDB at each stage of the lifecycle. The practice should ensure that changes in CIs are correctly and promptly captured in the CMDB. To that end, CI record-keeping should be automated wherever possible. Automation improves the reliability of the configuration data and decreases the need for verification (but does not remove it).

<table><tbody><tr><td><p><strong>Definition: Verification</strong></p></td></tr><tr><td><p>An activity that ensures that a new or changed IT service, process, plan, or other deliverable matches its design specification and is complete, accurate, and reliable.</p></td></tr></tbody></table>

In this practice, verification is a continual activity of identifying and correcting gaps and deviations between the data in CMDB and the actual environment and/or the approved configurations. In many cases, verification can be largely automated, such as checking CMDB data (including CIs and relationships) for completeness, correctness, and compliance.

<table><tbody><tr><td><p><strong>Definition: Compliance</strong></p></td></tr><tr><td><p>The act of ensuring that a standard or set of guidelines is followed, or that proper, consistent accounting or other practices are being employed.</p></td></tr></tbody></table>

<table><tbody><tr><td><p><strong>Definition: Inventory</strong></p></td></tr><tr><td><p>Data collection and clean up, performed as manual tasks, to build or verify the contents of the CI register.</p></td></tr></tbody></table>

<table><tbody><tr><td><p><strong>Definition: Discovery</strong></p></td></tr><tr><td><p>Data collection and clean up, achieved through automation technology and tools, to build or verify the contents of the CMDB. Discovery produces the location and identification of CIs that exist within the organization, particularly those that were previously undocumented or inadequately documented in the CMDB.</p></td></tr></tbody></table>

Verification of the CMDB data should ideally be performed through a combination of inventory and discovery.

Depending on the CI types that are in scope and the available automation tools, inventory is performed manually or through integration with discovery tools and other systems that are collecting data about the status of the organization’s resources. The CMDB indicates what should be found, and the inventory reveals what is found. The identification and resolution of gaps between the CMDB and the inventory is verification. When verifying data, it may help to:

*   identify and investigate unregistered CIs found in the organization
*   identify and document unregistered authorized changes (typically indicating ineffective CI control)
*   identify, investigate, and revert or otherwise address unauthorized changes.

There are different approaches to dealing with identified gaps between the actual and documented configuration information. The key challenge is to ensure that the data in the CMDB reflects the status of the organization’s resources and that this status is correct (meaning there are no unauthorized changes). Possible solutions include:

*   carefully investigating every finding and correction of the organization’s resources or configuration data, depending on the investigation’s results
*   (semi-)automatically updating the CMDB to reflect the de-facto situation, regardless of whether the situation is authorized (this decouples the investigation of unauthorized changes from the CMDB verification)
*   (semi-)automatically correcting the de-facto situation based on the latest configuration baseline, without investigating the gaps’ origins (this is more applicable to digital resources and can be difficult to do with physical resources).

These solutions are not mutually exclusive. They can be combined as necessary, depending on the situation.

Organizations may also formally audit configuration data. These audits are often combined with IT asset audits (see the IT asset management practice guide).

<table><tbody><tr><td><p><strong>Definition: CMDB audit</strong></p></td></tr><tr><td><p>A planned, structured, and documented inspection of the organization’s configuration items that aims to assess the correctness of the CMDB data in scope.</p></td></tr></tbody></table>

Auditing is one of the tools of CMDB verification; a resource-demanding planned verification endeavour. It is usually organized and managed as a project and, like any project, should be justified and approved in order to occur.

Verification is an integral part of the service configuration management practice. It is necessary to ensure that the configuration data is accurate, up to date, reliable, understandable, easy to use, and relevant.

#### 2.3 Scope

For the chosen types of CIs, the service configuration management practice ensures that:

*   trustworthy configuration data is provided and maintained, which includes updating the configuration data to reflect ongoing changes in the statuses, attributes, and relationships of CIs
*   relevant and accurate reports are provided to support decision making
*   the CI lifecycle is integrated with other practices.

There are several activities and areas of responsibility that are not included in the service configuration management practice, although they are still closely related to service configuration management. In some cases, the practice depends on these activities. They are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams and should be combined as necessary, depending on the situation.

#### Table 2.2 Activities related to the service configuration management practice described in other practice guides

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Managing IT assets and IT asset data</p></td><td><p>IT asset management</p></td></tr><tr><td><p>Managing contracts with suppliers and partners</p></td><td><p>Supplier management</p></td></tr><tr><td><ul><li>Ensuring that only authorized changes are made to CIs</li><li>Analysing the impacts of changes that involve CIs</li><li>Authorizing and planning changes requiring CI modification</li><li>Defining rules for CI changes triggered by standard changes or service requests</li></ul></td><td><p>Change enablement</p></td></tr><tr><td><p>Defining and managing the architectures of the organization’s products and services</p></td><td><p>Architecture management</p></td></tr></tbody></table>

### 2.4 Practice success factors

<table><tbody><tr><td><p><strong>Definition: Practice success factor</strong></p></td></tr><tr><td><p>A complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The service configuration management practice includes the following PSFs:

*   ensuring that the organization has relevant configuration information about its products and services
*   ensuring that the costs of providing configuration information are continually optimized.

#### 2.4.1 Ensuring that the organization has relevant configuration information about its products and services

The focus of the service configuration management practice is ensuring that relevant configuration information is captured, maintained, and provided to the stakeholders when needed.

Typically, stakeholders that benefit from configuration information use it in the contexts of other management practices and in the wider context of the organization’s value streams.

As listed in section 2.1, configuration information can be used for:

*   impact analysis
*   cause and effect analysis
*   risk analysis
*   cost allocation
*   availability analysis and planning.

Table 2.3 shows how these activities contribute to various management practices. These and other ways to use configuration information are applicable to every practice and value stream. However, in every case there should be a justification for adding more data or complexity to the CMDB. Key questions to consider include:

*   Is this information available from other sources?
*   Is this information critical or optional for decision-making?
*   What are the initial and ongoing costs of including this information in the CMDB?
*   How often is this information required?
*   How soon does it need to be available?

In some cases, it is more efficient to retrieve configuration data upon request than to make it permanently available in the CMDB. These considerations apply to a range of CI types, attributes, relationships, and lifecycle stages.

#### Table 2.3 Service configuration information supports other management practices

<table><tbody><tr><td></td><td><p><strong>Impact analysis</strong></p></td><td><p><strong>Cause and effect analysis</strong></p></td><td><p><strong>Risk analysis</strong></p></td><td><p><strong>Cost allocation</strong></p></td><td><p><strong>Availability analysis and planning</strong></p></td></tr><tr><td><p><strong>Incident management</strong></p></td><td><p>Analysis of the impacts of incidents on resources, products, services, and users</p></td><td><p>Localization of failed CIs based on information about their impacts</p></td><td><p>Analysis of the expected impacts of developing incidents</p></td><td><p>Allocation of costs of supporting cost centres and/or customers</p></td><td><p>Assessment of service availability during incidents and workaround planning</p></td></tr><tr><td><p><strong>Problem management</strong></p></td><td><p>Analysis of the impacts of errors on resources, products and services, service consumers, and users</p></td><td><p>Identification of CIs and relationships that might cause or have caused incidents</p></td><td><p>Analysis of the potential impacts and probabilities associated with identified errors</p></td><td><p>Allocation of problem investigation and control to cost centres and/or customers</p></td><td><p>Assessment of the impacts of identified errors on service availability and the planning of temporary solutions</p></td></tr><tr><td><p><strong>Change enablement</strong></p></td><td><p>Analysis of the impacts of ongoing and planned changes on resources, products and services, service consumers, and users</p></td><td><p>Review of unsuccessful changes and changes with unplanned effects, as well as the identification of possible causes of failures</p></td><td><p>Analysis of risks during the planning of changes</p></td><td><p>Allocation of costs of changes to cost centres and/or customers</p></td><td><p>Assessment of the impacts of planned changes on service availability</p><p>Planning of service availability during planned changes</p></td></tr><tr><td><p><strong>Availability management</strong></p></td><td><ul><li>Analysis of the impacts of events and changes on the availability of resources, and products and services</li><li>Analysis of the impacts of unavailable resources on products and services</li></ul></td><td><p>Identification of causes of product and service unavailability</p></td><td><p>Analysis of (un)availability risks</p></td><td><p>Allocation of costs of enhanced availability measures to cost-centres and/or customers</p></td><td><p>Analysis and planning of product and service availability</p></td></tr><tr><td><p><strong>Service continuity management</strong></p></td><td><ul><li>Analysis of the impacts of possible and actual disasters on resources, and products and services</li><li>Analysis of the impacts of the unavailability of resources on vital business functions</li></ul></td><td><p>Identification of causes of disasters</p></td><td><p>Analysis of service continuity risks</p></td><td><p>Allocation of the costs of enhanced availability measures to cost-centres and/or customers</p></td><td><p>Analysis and planning of product and service availability</p></td></tr><tr><td><p><strong>Information security management</strong></p></td><td><p>Analysis of the impacts of security events, incidents, and vulnerabilities on resources and products and services</p></td><td><p>Identification of the causes of information security incidents</p><p>Identification of vulnerabilities</p></td><td><p>Analysis of information security risks</p></td><td><p>Allocation of the costs of information security controls to cost-centres and/or customers</p></td><td><p>Analysis and planning of product and service information security</p></td></tr></tbody></table>

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>Configuration information should be relevant to the organization’s needs. Including all available data in a CMDB or blindly following examples from other organizations is not beneficial. The service configuration management practice is only as valuable as the information it provides is accurate, up to date, reliable, understandable, easy to use, and relevant.</p></td></tr></tbody></table>

Data quality is a key factor for CMDB utilization. Data quality can be defined based on such factors as accuracy, currency, reliability, understandability, usability, and relevancy.

Just a few cases of incorrect data (such as an attribute not being up to date or accurate) may undermine trust from CMDB users, and in some cases cause incidents.

As described in 2.2.4, CMDB data governance and CI record lifecycle models are a vital factor of data quality. They support the integration of service configuration management into value streams.

#### 2.4.2 Ensuring that the costs of providing configuration information are continually optimized

Following the ‘optimize and automate’ guiding principle, routine tasks, such as discovery, inventory, and verification, should be optimized and automated to streamline workloads and improve the effectiveness and efficiency of the practice.

In line with the ‘keep it simple and practical’ guiding principle, the service configuration management practice should not become a bureaucratic control system. Rather, it should streamline work by providing valuable information in a convenient, useful form. This provision of information typically involves channels managed as part of other practices (including the supplier management and service desk practices). The effective integration of practices is essential for the configuration information consumers to have a positive experience.

The service configuration management practice provides information to other practices, acting as a supporting practice in most of the organization’s value streams. However, it is unlikely that it will contribute to a value stream with core value-creating activities. This means that it is important to ensure that the cost of configuration information is continually optimized.

Cost optimization can be achieved in multiple ways, but a good way to drive optimization is to follow the ITIL guiding principles, as described in Table 2.4.

#### Table 2.4 ITIL guiding principles and the continual optimization of configuration information costs

<table><tbody><tr><td><p><strong>Guiding principles</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Focus on value</p></td><td><p>Include only the relevant information required by stakeholders</p></td></tr><tr><td><p>Start where you are</p></td><td><p>Use available sources of information; avoid adding new sources and tools unless they are justified</p></td></tr><tr><td><p>Progress iteratively with feedback</p></td><td><p>Regularly review information use and confirm its relevance, adjusting the CMDB scope if needed</p></td></tr><tr><td><p>Collaborate and promote visibility</p></td><td><p>Explain and promote available sources of configuration information and the best ways to use them, then provide hints and tips for more efficient use</p></td></tr><tr><td><p>Think and work holistically</p></td><td><p>Consider other sources of data for decision-making, do not try to put everything in the CMDB</p></td></tr><tr><td><p>Keep it simple and practical</p></td><td><p>Provide relevant information in the most convenient way; avoid complex interfaces and reports</p></td></tr><tr><td><p>Optimize and automate</p></td><td><p>Continually optimize resource-consuming practice activities. Automate CMDB verification, data collection, relationship discovery, and other activities.</p></td></tr></tbody></table>

There are several sources of costs to consider when managing a CMDB:

*   for the CMS:

\- software (costs of purchasing or licensing the CMDB and other CMS software)

\- hardware (costs of using additional hardware to run the CMS)

\- data integration (costs of integrating different databases, including efforts and time for data

mapping and migration if required)

\- implementation (cost for planning, configuring, and testing the CMDB)

\- maintenance (costs for ongoing maintenance actions such as software updates, troubleshooting,

implementing enhancements)

\- carbon footprint (indirect and non-monetary costs caused by the amount of data stored in the CMS, sustainability of hardware and software and electricity consumption)

\- human time and effort required for the manual activities caused by the service configuration management practice (for example updating CMDB records as a part of a change, or adding the relationships of new CIs when implementing a new service)

\- training (costs for training of the CMS users and maintenance team)

\- audits (cost of conducting internal and supporting external CMDB audits)

\- external services (from CMS implementation, to conducting CMDB audits).

The ITIL 4 concept of the four dimensions of service management can be used to ensure that cost calculations are comprehensive and holistic. The cost calculation procedure should be aligned with the financial management and project management practices to ensure that the calculation is consistent, and that costs are compliant with existing organizational approaches and fit for purpose.

### 2.5 Key metrics

Key metrics for the service configuration management practice are mapped to its PSFs. The key metrics are listed in Table 2.5.

The practice metrics should be applied to a specific context such as type of incident, services, specialist groups, or periods of time. The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which the practices contribute. The context of the business and the value streams is important when defining whether the practice’s performance is considered good or not. This is why this practice guide cannot recommend universal key performance indicators for service configuration management: the target values for each metric can only be defined in the organization’s context.

### Table 2.5 Key metrics for service configuration management

<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Ensuring that the organization has relevant configuration information about its products and services</p></td><td><ul><li>Stakeholder satisfaction with configuration information</li><li>Stakeholder satisfaction with service configuration management interfaces, procedures, and reports</li><li>Number and impact of bad decisions made due to insufficient or incorrect configuration information</li><li>Number and impact of incorrect data in the CMDB</li><li>Percentage of CMDB data verified over the period</li></ul></td></tr><tr><td><p>Ensuring that the costs of providing configuration information are continually optimized</p></td><td><ul><li>The direct costs of service configuration management</li><li>Percentage of the CMDB data used by the organization</li></ul></td></tr></tbody></table>

## 3. Value Streams and processes

### 3.1 Processes

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><p><strong>Definition: Process</strong></p></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one of more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

Service configuration management activities form three processes:

*   managing a common approach to service configuration management
*   capturing, managing, and providing configuration information
*   verifying configuration data.

#### 3.2.1 Managing a common approach to service configuration management

This process is focused on establishing an effective and efficient approach to the management of configuration information in the organization. It includes the activities listed in Table 3.1 and transforms the inputs into outputs.

### Table 3.1 Inputs, activities, and outputs of the managing a common approach to service configuration management process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Organizational architecture</li><li>Stakeholder requirements</li><li>Organizational structure</li><li>Organization’s portfolios</li><li>Monitoring data</li><li>Practice records</li><li>Organizational polices</li><li>External regulations and standards</li></ul></td><td><ul><li>Analyse stakeholder requirements</li><li>Define and agree the service configuration management approach</li><li>Communicate and integrate the service configuration management approach into the organization’s value streams</li><li>Review and adjust the service configuration management approach and procedures</li></ul></td><td><ul><li>Service configuration management approach</li><li>CMDB</li><li>Service configuration management communications and knowledge management materials</li><li>Requests for change and implementation initiatives</li><li>Service configuration management approach performance reports</li></ul></td></tr></tbody></table>

Figure 3.1 shows a workflow diagram of the process.

![Image of Figure 3.2 shows workflow diagram of managing a common approach to Service Configuration Management process](Service%20configuration%20management%20ITIL4%20Practice%20Guide/Picture3.png)

**Figure 3.1 Workflow of the managing a common approach to service configuration management process**  

Table 3.2 describes the process activities.

#### Table 3.2 Activities of the managing a common approach to the service configuration management process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Example</strong></p></td></tr><tr><td><p>Analyse stakeholder requirements</p></td><td><p>A configuration manager identifies key stakeholders who expect configuration information and requirements. These stakeholders typically include:</p><ul><li>practice owners</li></ul><ul><li>value stream owners</li></ul><ul><li>product owners</li></ul><ul><li>service owners</li></ul><ul><li>resource owners</li></ul><ul><li>project managers.</li></ul><p>The configuration manager documents, prioritizes, and analyses the requirements with the stakeholders. Configuration coordinators, configuration librarians, and external consultants may also be involved.</p><p>The configuration manager forms a configuration management team from those involved.</p></td></tr><tr><td><p>Define and agree the service configuration management approach</p></td><td><p>The configuration management team discusses and agrees a service configuration management approach (or plan).</p><p>The approach typically defines:</p><ul><li>service configuration management policies for:</li></ul><ul><li>assessing the relevance of the configuration management information and planning the CMDB scope</li></ul><ul><li>optimization of the costs of service configuration information</li></ul><ul><li>verification of the CMDB data</li></ul><ul><li>integration of the service configuration management activities into the organization’s value streams and practices</li></ul><ul><li>review of the approach</li></ul><ul><li>CI types, taxonomy, and CI lifecycle models</li></ul><ul><li>naming and labelling conventions</li></ul><ul><li>automation and integration</li></ul><ul><li>CI identification plan: activities, targets, and KPIs</li></ul><ul><li>roles and responsibilities</li></ul><ul><li>monitoring and ongoing control procedures</li></ul><ul><li>verification procedures</li></ul><ul><li>reporting procedures</li></ul><ul><li>configuration discovery and reporting procedures, when necessary</li></ul><ul><li>funding and cost allocation.</li></ul><p>Another decision to make is which CI attributes need to be included into the scope of the process of change realization control (see the change enablement practice guide for more information on this process), and if these attributes should be updated automatically or manually.</p><p>The approach is discussed and approved by the key stakeholders, including the sponsors and leaders of the organization.</p></td></tr><tr><td><p>Communicate and integrate the service configuration management approach into the organization's value streams</p></td><td><ul><li>The agreed service configuration management approach is communicated to and discussed with stakeholders across the organization. These typically include practitioners who will be participating in the service configuration management activities, technical experts involved in practice automation, and other teams.</li><li>Stakeholders can decide how formal the training on the service configuration management controls and procedures should be. For the people most involved in the practice, formal initial training and periodic awareness trainings will be necessary.</li><li>The implementation of the service configuration management approach is performed in conjunction with the IT asset management, supplier management, change enablement, project management, organizational change management, workforce and talent management, relationship management, infrastructure and platform management, and software development and management practices, among others.</li></ul></td></tr><tr><td><p>Review and adjust the service configuration management approach and procedures</p></td><td><ul><li>The service configuration manager monitors and reviews the adoption, compliance, and effectiveness of the agreed service configuration management approach and procedures. This is done on an event-based (non-standard requests for information, identified gaps in CI data, new requirements) and interval-based basis.</li><li>Based on the reviews, the approach and/or its practical implementation may be changed. The service configuration management approach performance reports provide input for the approach update.</li></ul></td></tr></tbody></table>

#### 3.1.2 Capturing, managing and providing configuration information

This process is focused on updating, maintaining, and providing configuration information. It includes the activities listed in Table 3.3 and transforms the inputs into outputs.

#### Table 3.3 Inputs, activities, and outputs of the capturing, managing, and providing configuration information process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Service configuration management approach</li><li>Configuration data</li><li>Requests for configuration information</li><li>Service management records</li></ul></td><td><ul><li>Analyse resources and identify CIs</li><li>Confirm a CI lifecycle model</li><li>Follow the CI lifecycle model</li><li>Manage exceptions</li><li>Review the CI lifecycle model</li></ul></td><td><ul><li>Updated CMDB</li><li>Configuration information for stakeholders</li><li>Exception reports</li><li><p>CI lifecycle model review reports</p></li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process

![Image of Figure 3.3 shows workflow diagram of the capturing, managing, and providing configuration information process](Service%20configuration%20management%20ITIL4%20Practice%20Guide/Picture4.png)

**Figure 3.2 Workflow of the** **capturing, managing, and providing configuration information process**

Table 3.4 describes the process activities.

#### Table 3.4 Activities of the capturing, managing, and providing configuration information process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Analyse resources and identify CIs</p></td><td><p>Upon discovering a new resource, resource type, or change in the existing CI, the resource owner or configuration librarian identifies the relevant CI model. If in doubt, the resource owner escalates the issue to a configuration manager.</p></td></tr><tr><td><p>Confirm a CI model</p></td><td><p>The configuration manager reviews the situation, confirms the CI model, or suggests a different one. If needed, the configuration manager may suggest adjustments to the selected CI model.</p></td></tr><tr><td><p>Follow the CI model</p></td><td><p>The resource owner, configuration manager, and/or configuration librarian follows the selected model. This typically includes:</p><ul><li>capturing and updating the CI data in the CMDB at each stage of the CI lifecycle</li><li>ensuring the ongoing verification of the CMDB data</li><li>providing up-to-date CI information to relevant stakeholders.</li></ul></td></tr><tr><td><p>Manage exceptions</p></td><td><ul><li>If an exception occurs during the CI lifecycle, the configuration manager and resource owner handle it in line with organization’s service configuration management approach.</li></ul><ul><li>Deviations from the agreed procedures should be rare. It is important to ensure ongoing compliance and the maintenance of controls.</li><li>Exceptions may include non-standard ad-hoc requests for confiIf an exception occurs during the CI lifecycle, the configuration manager and resource owner handle it in line with organization’s service configuration management approach. Deviations from the agreed procedures should be rare. It is important to ensure ongoing compliance and the maintenance of controls. Exceptions may include non-standard requests, when necessary, for configuration information not included in the CI lifecycle model.</li><li>Exceptions should be documented to be used when reviewing the service configuration management approach, CI lifecycle models, and procedures.</li></ul></td></tr><tr><td><p>Review the CI model</p></td><td><p>Upon significant exceptions, or regularly, the configuration manager and the configuration team review the CI models and update them based on collected feedback, reviewed requirements, CI records, verification reports, and new optimization opportunities.</p></td></tr></tbody></table>

#### 3.1.3 Verifying configuration data

This process is focused on keeping configuration data complete, correct, and compliant. It includes the activities listed in Table 3.5 and transforms the inputs into outputs.

Table 3.5 Inputs, activities and outputs of the verifying configuration data process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td><td></td></tr><tr><td><ul><li>Service configuration management approach</li><li>CMDB</li><li>Inventory data</li><li>Exception reports</li><li>Previous CMDB verification reports</li></ul></td><td><ul><li>Plan the verification activities</li><li>Identify a CI lifecycle model</li><li>Verify configuration data</li><li>Review the verification output</li><li>Define and implement corrective actions</li><li>Compose and communicate a CMDB verification report</li></ul></td><td><ul><li>Updated CMDB</li><li>Requests for changes</li><li>Improvement initiatives</li><li>CMDB verification report</li></ul></td></tr></tbody></table>

Figure 3.3 shows a workflow diagram of the process.

![Image of Figure 3.4 shows workflow diagram of the Verifying Configuration Data process](Service%20configuration%20management%20ITIL4%20Practice%20Guide/Picture5.png)

**Figure 3.3 Workflow for the verifying configuration data process**

Table 3.6 describes the process activities.

#### Table 3.6 Activities of the verifying configuration data process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Example</strong></p></td></tr><tr><td><p>Plan the verification activities</p></td><td><ul><li>A configuration manager (where necessary – assisted by a project management team) clarifies the purpose of the verification and plans the execution.</li><li>For periodic audits this results in a thorough audit plan defining the purpose, scope, activities and schedule of the audit, along with the roles and responsibilities.</li><li>For ongoing verification, verification activities and responsibilities are defined in the CI lifecycle model.</li></ul></td></tr><tr><td>Identify a CI lifecycle mode</td><td>A configuration manager identifies a CI lifecycle model applicable to the organization’s resources, confirms the verification procedures for the CI, and assigns and communicates responsibilities for verification activities.</td></tr><tr><td>Verify configuration data</td><td>In line with the communicated procedures, teams responsible for the verification procedures collect inventory data. The configuration manager and the CI owner compare inventory data with CMDB data; this comparison should be automated wherever possible.</td></tr><tr><td>Review the verification output</td><td>All cases of CMDB-data incompleteness, incorrectness, or non-compliance, as well as unauthorized changes in resources, must be reviewed by the configuration manager, resource owner, or other people assigned according to the CI lifecycle model.</td></tr><tr><td><span>Define and implement corrective actions</span></td><td>The configuration manager, resource owner, or other people assigned according to the CI lifecycle model agree, document, and communicate corrective actions to the CMDB and/or organization’s resources. Improvement initiatives to the CI lifecycle model and/or service configuration management approach may also be suggested.</td></tr><tr><td><span>Compose and communicate a CMDB verification report</span></td><td><span>The configuration manager, resource owner, or other people assigned according to the CI model compose and communicate a CMDB verification report to relevant stakeholders. This report should include proposed corrective actions and improvement initiatives.</span></td></tr></tbody></table>

### 3.2 Value stream contribution

#### 3.2.1 Service value streams

To perform certain tasks or respond to particular situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario. Once designed, value streams should be subject to continual improvement.

<table><tbody><tr><td><p><strong>Definition: Value stream</strong></p></td></tr><tr><td><p>A series of steps an organization undertakes to create and deliver products and services to consumers.</p></td></tr></tbody></table>

In practice, however, many organizations come to use of the value stream concept after having worked for a while (sometimes for years) without the value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the ‘As Is’ situation and the de-facto flows of work, and to analyse them in order to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding the existing value streams is critical to improving an organization’s performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services. Combined, the organizations’ value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations follow best practice recommendations for various service management practices, such as incident management, change enablement, software development, and many others. However, the practices are often adopted and organized in a siloed, isolated manner, just as they are presented in service management bodies of knowledge. In reality, a flow of work required to create or restore value, for a customer or another stakeholder, is almost never limited to one practice.

#### 3.2.2 Service configuration management in service value streams

Although service configuration management plays a supporting role in the service provider’s service value streams, this role is important; as shown in Table 2.3, many practices rely on service configuration information to achieve their purposes.

Table 3.7 describes how the key service value streams involve service configuration management.

#### Table 3.7 Service configuration management in key service value streams

<table><tbody><tr><td>Value stream</td><td>The role of service configuration information</td></tr><tr><td>Creation of a new or changed product<p>or service</p></td><td><ul><li>Assessment of the impact of the new requirements on the current services</li><li>Identification of the scope of required changes in products and services</li><li>Control of the implementation of the approved changes throughout the change</li><li>lifecycle</li><li>Scheduling of changes with minimum impact on the live services</li></ul></td></tr><tr><td>Incident resolution</td><td><ul><li>Impact assessment during incident classification</li><li>Incident diagnosis, identification of the failed components</li><li>Identification of the teams/specialists responsible for the failed components</li><li>Mapping of incidents records to each other and other records (problem, change)</li><li>Planning and control of the changes required for incident resolution</li><li>Verification of the changes made to resolve an incident</li></ul></td></tr><tr><td>Service request fulfilment</td><td><ul><li>Identification of the team/specialist to which to assign the request</li><li>Planning and control of the changes required to fulfil a request</li><li>Verification of the changes required to fulfil a request</li></ul></td></tr><tr><td>Ongoing operation and maintenance</td><td><ul><li>Detection of unauthorized changes</li><li>Impact assessment of events</li><li>Impact assessment of proposed and scheduled actions and changes</li></ul></td></tr><tr><td>Continual improvement of products and services</td><td><ul><li>Capacity, performance, availability, and continuity assessment and planning</li><li>Information security assessment and planning</li><li>Service cost allocation and planning</li></ul></td></tr></tbody></table>

For all value streams, the service configuration management practice provides configuration information via the CMS either by maintaining it on an ongoing basis, or by gathering and publishing it on demand. It is unusual to see activities of service configuration management in the core workflow of a value stream, but many of the core activities use configuration information. The effectiveness and efficiency of some of the value stream activities (such as impact assessment and change planning) are highly dependent on the availability and quality of service configuration information. This makes the service configuration management practice critical for many service value streams.

#### 3.2.3 Analysing a service value stream

#### 3.2.3.1 The key steps of a service value stream analysis

The following are some simple and practical recommendations for service value stream analysis and mapping.

1\. **Identify the scope of the value stream analysis**

This can be mapped to a particular product or service or applied to most or all of them. Similarly, service value streams may differ for different consumers; for example, incidents can be solved and communicated differently for internal and external customers, or for B2B and B2C products, or for services based on products developed inhouse or sourced externally.

2\. **Define the purpose of the value stream from the business standpoint**

Make sure the stakeholder’s concerns are clearly understood, since they are the ones defining value. In the case of service configuration management, these are usually service provider teams who need configuration information. However, the information may also be useful for third parties involved in the management of the organization’s services.

3\. **Do the service value stream walk**

Walk through or directly experience the steps and information flow as they go in practice (consider the Lean technique of Gemba walk):

a. **Identify the workflow steps**

b. **Collect data as you walk**

c. **Evaluate the workflow steps**

Typically, the criteria for evaluation are:

*   value for the stakeholder (does the step add value for the business stakeholder?)

*   effectiveness or performance (is the step performed well?)

*   availability (are required resources available to execute the step?)

*   capacity (are required resources enough?)

*   flexibility (are the required resources interchangeable within the step?).

d. **Map the activities and the information flows**

In an ideal situation, the flow goes smoothly without delays and pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

e. **Create and review the timeline and resource level**

Map out process times and lead times for resources and workload through the workflow steps.

4\. **Reflect on the value stream map (VSM)**

Identify factors that might not have been entirely apparent at first. The information collected is used at this step to find the waste.

5\. **Create a ‘to be’ VSM**

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

6\. **Using the ‘to be’ VSM, plan improvements**

Refer to the continual improvement practice guide for a practical improvement model.

#### 3.2.3.2 Service configuration management considerations in a service value stream analysis

To ensure that relevant service configuration management activities are included in service value streams, the following steps can be added to the above recommendations.

*   At the scoping step (1), identify the IT and business services related to the value stream and the involved business stakeholders. Are they in the scope of service configuration management, and to what extent? What configuration information may be relevant for the stakeholders?

*   During the service value stream walk (3a), identify the practices involved at every step and the configuration information they use. What configuration information which they may need is readily available? Is there a chance that ad-hoc configuration analysis will be needed? Are there third parties involved in the value stream? If so, what configuration information might they need? Can this information be shared with them, and what are the applicable information security policies?

*   During the workflow steps evaluation (3c), evaluate the service configuration information impact on the value stream effectiveness and efficiency. Special attention should be paid to steps with low business value, low performance, and availability or capacity issues. Does service configuration management create any delays? Is the configuration information sufficient? Is it provided in a timely and convenient way?

*   At the reflection and planning steps (4-5), ensure that the service configuration information is available throughout the value stream and its provision and use are optimized for business value.

*   Include the creation or update of CI lifecycle models and other elements of the service configuration management approach in the value stream improvement plans (step 6).

## 4. Organizations and people

### 4.1 Roles, competencies, and responsibilities

The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended.

Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

#### Table 4.1 Competency codes and profiles

<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p>L</p></td><td><p><u>Leader</u> Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes.</p></td></tr><tr><td><p>А</p></td><td><p><u>Administrator</u> Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements.</p></td></tr><tr><td><p>C</p></td><td><p><u>Coordinator/Communicator</u> Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns.</p></td></tr><tr><td><p>М</p></td><td><p><u>Methods and techniques expert</u> Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement.</p></td></tr><tr><td><p>Т</p></td><td><p><u>Technical expert</u> Providing technical (IT) expertise and conducting expertise-based assignments.</p></td></tr></tbody></table>

#### 4.1.1 Configuration manager and configuration coordinator roles

The key role of the service configuration management practice is the configuration manager.

The configuration manager oversees the service configuration management approach and CI models for all CIs that are in scope. In many organizations, the configuration manager role is performed by a dedicated person. In larger organizations operating in many locations or in multiple industries, the configuration manager is supported by a team of configuration coordinators who have very similar responsibilities, but who specialize in a particular territory, industry, or other part of the organization.

This configuration manager role is typically responsible for:

*   managing the service configuration management approach
*   communicating the service configuration management approach and procedures
*   integrating the service configuration management approach into value streams
*   deciding whether to include new resources and resource types in the scope
*   managing exceptions
*   ensuring CI models are followed
*   ensuring the CMDB contains valid data
*   ensuring the organization complies with practice-related requirements, if applicable
*   optimizing and automating the practice
*   reporting on the service configuration management performance.

#### 4.1.2 Configuration librarian

Some organizations introduce the role of configuration librarian. This role focuses on manually updating configuration data, verifying the CMDB on an ongoing and periodic basis, and processing ad-hoc requests for configuration information.

This role is important in organizations with a low level of automation and high demand for ad-hoc, non-standard configuration information. It is rarely supported by dedicated resources and may be performed by resource owners.

#### 4.1.3 Resource owner role

A resource owner (sometimes called a resource custodian) is a person or team that ensures that a resource or group of resources in the organization are utilized correctly. They ensure that relevant CI models are consistently applied to the resource throughout its lifecycle in the context of the organization’s practices and value streams.

#### 4.1.4 Other roles involved in the service configuration management activities

Examples of other roles involved in change enablement activities are listed in Table 4.2.

Table 4.2 Examples of roles with responsibility for service configuration management activities

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Responsible roles</strong></td><td><strong>Competency profile</strong></td><td><strong>Specific skills</strong></td></tr><tr><td colspan="3">Managing a common approach to service configuration management</td><td></td></tr><tr><td>Analyse stake holder requirements</td><td><ul><li>Configuration manager</li><li>Configuration coordinator</li><li>Practice owner</li></ul><ul><li>Product owner</li><li>Service owner</li><li>Resource owner</li><li>Project manager</li></ul></td><td>TC</td><td><ul><li>Good knowledge of the organization, its resources and available information</li><li>Good understanding of the service configuration management practice and its role in the organization</li></ul></td></tr><tr><td>Define and agree the service configuration management approach</td><td><ul><li>Configuration manager and coordinators</li><li>Product and service architects</li><li>Consultants</li></ul></td><td>MTC</td><td><ul><li>Good understanding of stakeholder requirements, service configuration management methods and tools, available sources of information, and means of automation</li></ul></td></tr><tr><td>Communicate and integrate the service configuration management approach into the organization’s value streams</td><td><ul><li>Configuration manager and coordinators</li><li>Resource owners</li><li>Key users of the configuration information</li></ul></td><td>CLMA</td><td><ul><li>Leadership and communication skills</li><li>Good understanding of the agreed approach</li><li>Good understanding of stakeholder requirements</li></ul></td></tr><tr><td>Review and adjust the service configuration management approach and procedures</td><td><ul><li>Configuration manager</li><li>Product and service architects</li><li>Key users of the configuration information</li></ul></td><td>MCTA</td><td><ul><li>Good understanding of stakeholder requirements, service configuration management methods and tools, available sources of information, and means of automation</li></ul></td></tr><tr><td colspan="4"><span>Capturing, managing, and providing configuration information</span></td></tr><tr><td>Analyse resources and identify CIs</td><td><ul><li>Configuration manager</li><li>Configuration coordinator</li><li>Configuration librarian</li><li>Resource owner</li></ul></td><td>TA</td><td>Good knowledge of the organization’s resources and relevant CI models</td></tr><tr><td>Confirm a CI lifecycle model</td><td><ul><li>Configuration manager</li><li>Configuration coordinator</li><li>Configuration librarian</li><li>Resource owner</li></ul></td><td>MTC</td><td><ul><li>Good knowledge of the organization’s resources and relevant CI models</li><li>Good knowledge of the organization’s approach to service configuration management</li></ul></td></tr><tr><td>Follow the CI lifecycle model</td><td><ul><li>Configuration librarian</li><li>Resource owner</li></ul></td><td>AT</td><td>Good knowledge of the CI model</td></tr><tr><td>Manage exceptions</td><td><ul><li>Configuration manager</li><li>Configuration coordinator</li><li>Configuration librarian</li><li>Resource owner</li></ul></td><td>TCMA</td><td><ul><li>Good knowledge of the CI model</li><li>Good knowledge of the organization’s approach to service configuration management</li><li>Understanding stakeholder needs</li></ul></td></tr><tr><td>Review the CI lifecycle model</td><td><ul><li>Configuration manager</li><li>Resource owner</li></ul></td><td>MCTA</td><td><ul><li>Good knowledge of the CI model</li><li>Good knowledge of the organization’s approach to service configuration management</li><li>Understanding stakeholder needs</li></ul></td></tr><tr><td colspan="4">Verifying configuration data</td></tr><tr><td>Plan the verification activities</td><td><ul><li>Configuration manager</li><li>Configuration coordinator</li><li>Configuration librarians</li><li>Resource owner</li></ul></td><td>MCA</td><td><ul><li>Good knowledge of the service configuration management approach and the CI lifecycle models</li><li>Good understanding of the organization’s objectives and priorities</li><li>Good knowledge of the configuration verification methods and tools</li></ul></td></tr><tr><td>Identify a CI lifecycle model</td><td><ul><li>Configuration manager</li><li>Configuration coordinator</li><li>Configuration librarian</li><li>Resource owner</li></ul></td><td>TA</td><td><ul><li>Good knowledge of the CI model</li><li>Good knowledge of the organization’s approach to service configuration management</li></ul></td></tr><tr><td>Verify configuration data</td><td><ul><li>Configuration manager</li></ul><ul><li>Configuration coordinator</li><li>Configuration librarian</li><li>Resource owner</li></ul></td><td>TA</td><td><ul><li>Good knowledge of the CI model</li></ul><ul><li>Good understanding of configuration data sources and means of automation</li><li>Knowledge of the relevant organizational resources</li></ul></td></tr><tr><td>Review the verification output</td><td><ul><li>Configuration manager</li><li>Configuration coordinator</li><li>Configuration librarian</li><li>Resource owner</li></ul></td><td>TA</td><td><ul><li>Good knowledge of the CI model</li><li>Good knowledge of the organization’s approach to service configuration management</li><li>Understanding of the configuration data sources and means of automation</li></ul></td></tr><tr><td>Define and implement corrective actions</td><td><ul><li>Configuration manager</li><li>Configuration coordinator</li><li>Resource owner</li></ul></td><td>TMCA</td><td><ul><li>Good knowledge of the CI model</li><li>Good knowledge of the organization’s approach to service configuration management</li><li>Understanding stakeholder needs</li></ul></td></tr><tr><td>Compose and communicate a CMDB verification report</td><td><ul><li>Configuration manager</li></ul><ul><li>Configuration coordinators</li><li>Resource owners</li></ul></td><td>CAT</td><td><ul><li>Good knowledge of the CI model</li></ul><ul><li>Good knowledge of the organization’s approach to service configuration management</li><li>Understanding stakeholder needs</li></ul></td></tr></tbody></table>

#### 4.2 Organizational structures and teams

Two types of teams support this practice: a team for ongoing management of service configuration information and a team for regular review of the service configuration management approach. The exact structure and positioning of the teams depend on the size and structure of the organization.

Larger organizations have a specialized team of configuration manager(s) and configuration coordinator(s): dedicated specialists focused primarily on the service configuration management practice (in some organization these toles will focus on both the service configuration management and IT asset management practices). This team may be supported by external consultants when specific expertise is needed; typically this will be to review and update the service configuration management approach. Configuration coordinators may be focused on particular regions, locations, products, or clients, depending on the organizational and service architecture.

In smaller organizations, the configuration management specialist team is usually virtual, formed of people with other roles and tasks to perform. The ongoing activities embedded in the service value streams can be fulfilled by resource owners and coordinated by product and service owners, acting as configuration coordinators.

Wider temporary configuration teams may be formed in such organizations to review and update the service configuration management approach. These teams represent multiple stakeholders and may include:

*   configuration managers

*   practice owners
    
*   product owners
    
*   service owners
    
*   resource owners
    
*   service architects
    
*   project managers
    
*   other stakeholders or representatives.
    

## 5. Information and technology

### 5.1 Information exchange

The effectiveness of the service configuration management practice is based on the quality of the information used. This information includes, but is not limited to, information about:

*   organizational strategy
*   organizational architecture
*   the organization’s portfolios
*   stakeholder requirements and needs for configuration information
*   applicable regulatory requirements
*   configuration data from internal and external sources
*   technology trends
*   CI-related records from management practices
*   financial data
*   IT asset data.

This information may take various forms, depending on the CI types, organizational requirements, and service configuration management automation. The key inputs and outputs of the practice are listed in Chapter 3.

### 5.2 Automation and tooling

The CMS solution is often a part of integrated service management tools, or else designed for easy integration with them. It ensures the effective exchange of configuration information between the practices. Typically, key functionalities of CMS solutions include:

*   CI discovery

*   Updating and managing CI records

*   Modelling of relationships between CIs

*   CI version control

*   Impact assessment

*   Data health checks and verification

*   Configuration data integration and reconciliation.

Capturing configuration data, ensuring that configuration data is updated at every relevant change of status of the CIs, and automating other activities is very important for the service configuration management practice. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to the full automation of activities where technology solutions remove the need for human intervention. Where automation is possible and effective, it may involve the solutions outlined in Table 5.1.

#### Table 5.1 Automation solutions for service configuration management activities

<table><tbody><tr><td><strong>Automation tools</strong></td><td><strong>Application in service configuration management</strong></td></tr><tr><td>CMS tools</td><td><ul><li>Discover CI data</li><li>Store and manage CI data (create, update and delete CI records, display and modify attributes)</li><li>Integrate different databases</li><li>Identify and reconcile data from different data sources</li><li>Monitor and control CMDB health</li><li>Verify data</li><li>Certify CMDB data (compliance tool)</li></ul></td></tr><tr><td>Workflow management and collaboration tools</td><td><ul><li>Support planning and review activities of the practice</li><li>Support communications during ad-hoc provision of configuration information</li><li>Integrate the CMS into service value streams (mapping of CIs and service management records; access to CMS in the context of other practices)</li><li>Manage exceptions</li></ul></td></tr><tr><td>Inventory and discovery tools</td><td>Gather and verify information about the CIs</td></tr><tr><td>Knowledge management tools</td><td><ul><li>Share and utilize guidelines for service configuration management</li><li>Support ad-hoc provision of service configuration</li></ul></td></tr><tr><td>Classification and analysis tools</td><td>Analyse stakeholders requirements and CI data</td></tr><tr><td>Work planning and prioritization tools</td><td>Plan and track improvement initiatives</td></tr><tr><td>Analysis and reporting tools</td><td>Practice measurement and reporting</td></tr></tbody></table>

Because of the growing adoption of digital infrastructure solutions (such as infrastructure-as-a-code, virtual machines and networks, and various cloud services), new dilemmas and challenges frequently appear.

For example, new types of CIs and CI relationships have emerged. In these instances, information about relationships between hardware servers and the virtual machines running on them may be relevant in the context of a service model and therefore expected to be available through the service configuration management practice.

These relationships are usually managed by virtual machine monitor (VMM, also known as Hypervisor) systems. However, there is some debate about whether this information should be obtained directly from the VMM system or imported into the configuration management system (CMS). Similar practical questions are applicable to virtual networks, environment configuration scripts, and other means of virtual solutions management.

There is no universal answer and no recommended solution for defining which resources should be under the service configuration management practice’s control. These decisions should be driven by the value of the configuration information to stakeholders and costs of obtaining and maintaining the information.

Detailed descriptions of how tools listed in Table 5.1 support the practice’s activities are outlined in Table 5.2.

#### Table 5.2 Details of automation of the service configuration management activities

<table><tbody><tr><td><p><strong>Process activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><strong>Key functionality</strong></td><td><strong></strong><span><strong>Impact on the effectiveness of the practice</strong></span><strong></strong></td></tr><tr><td colspan="4">Managing a common approach to service configuration management</td><td></td></tr><tr><td><p>Analyse stakeholder requirements</p></td><td><p>Workflow management and collaboration tools</p></td><td><p>Collection and analysis of requirements, discussions, and prioritization</p></td><td><span>Medium</span></td><td></td></tr><tr><td><p>Define and agree the service configuration management approach</p></td><td><ul><li>Workflow management and collaboration tools</li><li>CMS tools</li></ul></td><td><p>Discussions, prioritization, data and workflow modelling, integration, and data exchange</p></td><td><span>High</span></td><td></td></tr><tr><td><p>Communicate and integrate the service configuration management approach into the organization's value streams</p></td><td><ul><li>CMS tools</li><li>Discovery and monitoring tools</li><li>Service management record-keeping tools</li></ul></td><td><p>Integration with other practices for data exchange</p></td><td><span>High</span></td><td></td></tr><tr><td><p>Review and adjust the service configuration management approach and procedures</p></td><td><ul><li>Workflow management and collaboration tools</li><li>CMS tools</li><li>Analysis and reporting tools</li></ul></td><td><p>Discussions, prioritization, data and workflow modelling, integration, and data exchange</p></td><td><span>High</span></td><td></td></tr><tr><td colspan="4">Capturing, managing, and providing configuration information</td></tr><tr><td><p>Analyse resources and identify CIs</p></td><td><ul><li>CMS tools</li><li>Inventory and discovery tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation</li><li>CI models library</li></ul></td><td><p>High</p></td></tr><tr><td><p>Confirm a CI lifecycle model</p></td><td><ul><li>CMS tools</li><li>Inventory and discovery tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation</li><li>CI models library</li></ul></td><td><p>High</p></td></tr><tr><td><p>Follow the CI lifecycle model</p></td><td><ul><li>CMS tools</li><li>Inventory and discovery tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation</li><li>CI models library</li></ul></td><td><p>High</p></td></tr><tr><td><p>Manage exceptions</p></td><td><ul><li>CMS tools</li><li>Inventory and discovery tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation</li><li>CI models library</li></ul></td><td><p>High</p></td></tr><tr><td><p>Review the CI lifecycle model</p></td><td><ul><li>CMS tools</li><li>Inventory and discovery tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation</li><li>CI models library</li></ul></td><td><p>High</p></td></tr><tr><td colspan="4"><p>Verifying configuration data</p></td><td></td></tr><tr><td><p>Plan the verification activities</p></td><td><ul><li>Inventory and discovery tools</li><li>CMS tools</li><li>Work planning and prioritization tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Reports of the CIs requiring additional verification</li><li>Scoping of audits and ongoing verification</li><li>Task generation, assignment, and coordination</li><li>Record keeping, integration of multiple practices</li></ul></td><td>Medium to High</td></tr><tr><td>Identify a CI model</td><td><ul><li>CMS tools</li><li>Inventory and discovery tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation</li><li>CI models library</li></ul></td><td>High</td></tr><tr><td>Verify configuration data</td><td><ul><li>CMS tools</li><li>Inventory and discovery tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation and audit</li><li>Data health monitoring and verification</li><li>CI models library</li></ul></td><td>High</td></tr><tr><td><p>Review the verification output</p></td><td><ul><li>CMS tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation and audit</li><li>Data health monitoring and verification</li></ul></td><td><p>High</p></td></tr><tr><td><p>Define and implement corrective actions</p></td><td><ul><li>CMS tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Integration with other practices for data exchange</li><li>CMDB navigation and audit</li><li>Configuration baselines library</li><li>CI models library</li></ul></td><td><p>High</p></td></tr><tr><td><p>Compose and communicate a CMDB verification report</p></td><td><ul><li>CMS tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Communication, discussions</li><li>Record-keeping</li></ul></td><td><p>Medium</p></td></tr></tbody></table>

#### 5.2.1 Recommendations for the automation of service configuration management

The following recommendations can help when applying automation to service configuration management:

*   **Support the value stream** Configuration information is only valuable in the context of the organization’s service value streams. The CMS tool should be either a part of the ITSM workflow management and collaboration system or have good integration with it. It is important to be able to map CI records to other records such as incidents, problems, changes and so on. Access to information about CIs for different users and situations should be adjustable according to the information security policies. Focus on value. Think and work holistically.

*   **Do not overcomplicate the CI attributes, lifecycle models, and relationships** An up-to-date CMDB with the most important information is more valuable than a comprehensive CMDB which is never up to date. Add new classes of CIs, new attributes, and new types of relationship only when it has a solid justification and demand for the information. Keep it simple and practical.

*   **Pay attention to automated measurement and reporting from the beginning** The amount of information in a CMS is large, and tends to keep growing, and manual analysis very quickly becomes impossible. Aim to automate analysis of the CMDB utilization, detection of errors, verification of changes and other repeating operations. Optimize and automate.

*   **Ensure effective integration with discovery and inventory tools** Verification is a key process of this practice, and it cannot be effectively performed manually. Make sure that baselines are created and used to control the correctness of the configuration data, make sure that unauthorized changes are detected effectively, and data discrepancy analysis is mostly automated.

*   **Ensure clear and useful visualization of the CMDB** Many use case scenarios require an interactive visualization of configuration items and the relationships between them.

*   **Expand the scope of the CMDB only when the current scope is effectively managed** When reviewing the practice, consider removing unused attributes or classes before adding new ones. Maintain a manageable size of CMDB. Consider starting with the CMDB structure suggested by the vendor before tailoring it. Progress iteratively with feedback.

## 6. Partners and suppliers

### 6.1 Service configuration management in the service relationship ecosystem

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of *ITIL Foundation: ITIL 4 Edition* for a model of a service relationship). This means that organizations constantly handle resources that are provided as part of third-party services. Similarly, organizations’ resources are widely used by their service consumers. This requires the effective coordination of the service configuration management practice between the members of the service relationship ecosystem. The exact level of coordination depends on the type of service relationship. The closer the relationship and higher the trust, the more configuration information can be shared and management activities performed together. At minimum, an exchange of limited configuration data between the organizations is established: at maximum, a wide integration or sharing of CMSs can be considered.

### 6.2 How partners and suppliers support the practice

Partners and suppliers integrated into the service provider organization usually have access to the organization’s CMS so that they can effectively fulfil their roles.

Partners and suppliers are often involved in the service provider’s value streams in various roles, and some of these roles include using and sometimes updating configuration information. This should be done in line with the CI lifecycle models and agreed in the contracts with the partners and suppliers.

Partners and suppliers can support the service configuration management practice by advising the service provider on the development and review of the service configuration management approach, integration of tools, and CMDB verification.

Third parties supply automation tools for many management practices, but this role of suppliers and partners is particularly important for service configuration management. It is likely that the practice will be supported by multiple tools; at least CMS tools, inventory and discovery tools, and ITSM workflow management and collaboration tools. It is very important to ensure effective integration across these tools, and organizations often involve third-party system integrators to help with the integration projects.

## 7. Capability assessment and development

### 7.1 The practice capability levels

The practice success factors described in section 2.4 cannot be developed overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:

**Level 1** The practice is not well organized; it’s performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

**Level 2** The practice systematically achieves its purpose through a basic set of activities supported by specialized resources.

**Level 3** The practice is well-defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

**Level 4** The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

**Level 5** The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level 2 to level 5. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well-defined and organized.

![](Service%20configuration%20management%20ITIL4%20Practice%20Guide/Figure_7.1.PNG)

**Figure 7.1 Design of the capability criteria**

This approach results in every practice having up to 30 capability criteria based on the practice PSFs and mapped to the four dimensions of service management. The number of criteria at each level differs: the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

Table 7.1 outlines the capability criteria that are defined in the ITIL maturity model for the service configuration management practice

#### Table 7.1 Service configuration management capability criteria

<table><tbody><tr><td><strong>PSF</strong></td><td><strong>Criterion</strong></td><td><strong>Dimension</strong></td><td><strong>Capability level</strong></td></tr><tr><td rowspan="8">Ensuring that the organization has relevant configuration information about its products and services</td><td>Key users of the configuration information and their requirements are identified</td><td>Value streams and processes</td><td>2</td></tr><tr><td>Information about product and service<p>configuration is available when needed and meets user requirements</p></td><td>Information and technology</td><td>2</td></tr><tr><td>Procedures for requesting and obtaining configuration information are defined and communicated to relevant stakeholders</td><td>Value streams and processes</td><td>3</td></tr><tr><td>Responsibility for the management of configuration information is clearly defined</td><td>Value streams and processes</td><td>3</td></tr><tr><td>Configuration information covers relevant details about third-party services</td><td>Partners and suppliers</td><td>3</td></tr><tr><td>Configuration information is managed using an integrated information system</td><td>Information and technology</td><td>4</td></tr><tr><td>Configuration information is exchanged between the organization and its suppliers and partners, where needed</td><td>Partners and suppliers</td><td>4</td></tr><tr><td>The quality and availability of the configuration information is continually reviewed and improved</td><td>Value streams and processes</td><td>5</td></tr><tr><td rowspan="5">Ensuring that the costs of providing configuration information are continually optimized</td><td>Costs of providing configuration information are identified and tracked</td><td>Value streams and processes</td><td>2</td></tr><tr><td>Users of configuration information are aware of and satisfied with the procedures and interfaces for requesting and obtaining the information</td><td>Value streams and processes</td><td>2</td></tr><tr><td>The processes and tools for the discovery, management, and provision of configuration information are designed for cost efficiency</td><td>Value streams and processes</td><td>3</td></tr><tr><td>Configuration management is integrated with internal and external sources of relevant data</td><td>Information and technology</td><td>4</td></tr><tr><td>The costs of providing configuration information are regularly reviewed and continually improved</td><td>Value streams and processes</td><td>5</td></tr></tbody></table>

These capability criteria can be used by organizations for self-assessment and improvement of the practice.

### 7.2 Capability self-assessment

A self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team in the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed.

1.  Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
2.  If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider’s employees.
    
3.  If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
    
4.  If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met; what is missing in the organization? Why? How can it affect the service consumer and the quality of the IT services? What can be done to meet the criteria that are currently missed
    
5.  The same approach is applied at every next level; the practice is considered to be at the level, where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.
    

### 7.3 Service configuration management capability development

Management practices should support the achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at capability level 5. A higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but it comes with a cost; cost of management, automation, and training, for example. To achieve optimal performance with sufficient level of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and Table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

![](Service%20configuration%20management%20ITIL4%20Practice%20Guide/Figure_7.2.PNG)

**Figure 7.2 The capability development steps and levels**

Table 7.2 The service configuration management capability development steps

<table><tbody><tr><td><strong>Capability level</strong></td><td><strong>Define, agree, and implement</strong></td><td><strong>Comment for service configuration management</strong></td><td><strong>Chapter (for recommendations)</strong></td></tr><tr><td rowspan="5">2</td><td>Purpose and objectives</td><td rowspan="2">Key stakeholder groups and requirements, domains and types of CIs</td><td>2.1</td></tr><tr><td>Scope</td><td>2.3</td></tr><tr><td>Processes and activities</td><td rowspan="3">Workflows, CI lifecycle models, roles and responsibilities, automation and information exchange</td><td>3.1</td></tr><tr><td>Roles and responsibilities</td><td>4</td></tr><tr><td>Tools and procedures</td><td>5</td></tr><tr><td rowspan="3">3</td><td rowspan="3">Dependencies and integration</td><td>Integration in the organization's service value streams</td><td>3.2</td></tr><tr><td>Use of integrated information system</td><td>5</td></tr><tr><td>Suppliers and other parties involved in service configuration management</td><td>6</td></tr><tr><td>4</td><td>Measurement and reporting</td><td>Metrics</td><td>2.5</td></tr><tr><td>5</td><td>Continual improvement</td><td>Regular review of practice and the service configuration management capability development</td><td>2.4, 2.5, 7</td></tr></tbody></table>

## 8. Recommendations for practice success

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:

*   focus on value

*   start where you are

*   progress iteratively with feedback

*   collaborate and promote visibility

*   think and work holistically

*   keep it simple and practical

*   optimize and automate.

In Table 8.1, recommendations for the success of the service configuration management practice are linked to the relevant guiding principles.

#### Table 8.1 Recommendations for the success of service configuration management

<table><tbody><tr><td><strong>Recommendation</strong></td><td><strong>Comments</strong></td><td><strong>ITIL guiding principles</strong></td></tr><tr><td>Design the practice to provide service configuration information required by the organization’s stakeholders</td><td><ul><li>The value of the practice is defined by those using the configuration information.</li><li>Make sure the requirements of the stakeholders are clear, and discussed with the stakeholders before building the CMDB.</li><li>A comprehensive ‘perfect’ CMDB is unlikely to be justified as the costs of creating and maintaining it would be higher than the value from it.</li></ul></td><td><ul><li>Focus on value</li><li>Collaborate and promote visibility</li></ul></td></tr><tr><td>Systematically review the scope of and level of details in the CMDB</td><td><ul><li>Analyse the utilization of the configuration data.</li><li>Consider removing attributes, relationships, or even CIs with unused CMDB information, especially if the information is verified and updated manually.</li><li>Expand or decrease the scope of the CMDB based on the changing requirements.</li></ul></td><td><ul><li>Collaborate and promote visibility</li><li>Progress iteratively with feedback</li><li>Keep it simple and practical</li></ul></td></tr><tr><td>Make CMDB verification an ongoing activity</td><td><ul><li>Regular audits are not enough. Combine ongoing verification with regular selective audits, aiming for full coverage of the CMDB over a period of a few months.</li></ul><ul><li>Aim to automate CMDB verification wherever possible.</li><li>Where manual verification is required, integrate it into the operations and maintenance value streams and make sure it is part of the regular activities.</li></ul></td><td><ul><li>Optimize and automate</li><li>Keep it simple and practical</li><li>Progress iteratively with feedback</li></ul></td></tr><tr><td>Automate handling of the configuration data where reasonably possible</td><td>Service configuration data should be reliable. If the data is handled manually, reliability can only be achieved by keeping the amount of data to minimum, which would limit the benefits of the practice. To support the needs of the organization and control larger amounts of data, CMDB should be effectively automated.</td><td>Optimize and automate</td></tr><tr><td>Develop the practice continually but don’t overcomplicate it</td><td><ul><li>Start with the most critical configuration data available in the available tools.</li><li>Add complexity where it is justified and manageable.</li><li>Aim to demonstrate value from the practice before making a significant investment.</li></ul></td><td><ul><li>Start where you are</li><li>Progress iteratively with feedback</li><li>Keep it simple and practical</li></ul></td></tr><tr><td>Involve third parties</td><td>Make sure that partners and suppliers involved in the organization’s value streams have access to the relevant configuration information but use it in line with the organization’s policies.</td><td>Collaborate and promote visibility</td></tr><tr><td>Demonstrate business value</td><td><ul><li>Measure the practice and produce regular reports and dashboards for internal (within the service provider) and external (service consumer) stakeholders.</li><li>Use dashboards for the current status and regular reports for analysis and highlights.</li></ul></td><td><ul><li>Focus on value</li><li>Collaborate and promote visibility</li></ul></td></tr></tbody></table>

## 9. Acknowledgements

PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following people:

#### Authors

Tatiana Peftieva, Roman Jouravlev

#### Contributors

Anton Lykov, Evgeniy Shilov

#### Reviewers

Dinara Adyrbai, Graham Heard, Antonina Douannes, Anton Lykov, Irina Matantseva

#### 2023 Revision

Antonina Douannes, Adam Griffith, Roman Jouravlev, Kaimar Karu, Olga Masalina, Avinash Singh
