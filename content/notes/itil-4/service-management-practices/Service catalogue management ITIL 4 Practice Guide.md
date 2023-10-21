---
title: "Service catalogue management: ITIL 4 Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

## 1. About this document

It is split into five main sections, covering:

*   general information about the practice
*   the practice’s processes and activities and their roles in the service value chain
*   the organizations and people involved in the practice
*   the information and technology supporting the practice
*   considerations for partners and suppliers for the practice.

### 1.1 ITIL® 4 qualification scheme

Selected content from this document is examinable as a part of the following syllabus:

*   **ITIL Specialist** Drive Stakeholder Value.

Please refer to the syllabus document for details.

## 2. General information

### 2.1 Purpose and description

<table><tbody><tr><td><strong>Key message</strong></td></tr><tr><td><p>The purpose of service catalogue management practice is to provide a single source of consistent information on all services and service offerings, and to ensure that it is available to the relevant audience.</p></td></tr></tbody></table>

The service catalogue management practice ensures that all stakeholders refer to a single, consistent source of information about services and service offerings. It also helps to provide all stakeholders with relevant views on services and service offerings, matching their needs and level of access.

There are many internal and external stakeholders who have access to and use various views of services and service offerings in their work. These include users, current and potential customers, product teams, support teams, supplier managers, relationship managers, and others. Their service catalogue views are different in scope and structure and include information from different additional sources. For example, internal teams may need technical details on services, the structure of support teams, lists of users, and other information that is neither required nor allowed to be included in a user-facing service catalogue.

The service catalogue management practice ensures a single source of service and service offering information for all groups and supports effective information exchange with other sources, in conjunction with other practices including service configuration management, service financial management, relationship management, supplier management, service request management, and others.

The service catalogue management practice covers all services managed by an organization, including internal, external, provided, and consumed. For example, a supplier manager’s view may include the third-party services that are consumed by the organization, as well as the organization’s services that are dependent on them.

### 2.2 Terms and concepts

<table><tbody><tr><td><strong>Definition: Resources</strong></td></tr><tr><td><p>Personnel, material, finance, or other entity that is required for the execution of an activity or the achievement of an objective. Resources used by an organization may be owned by the organization or used according to an agreement with the resource owner.</p></td></tr></tbody></table>

Organization’s resources can be configured into a product to offer value for a consumer or consumer group.

<table><tbody><tr><td><strong>Definition: Product</strong></td></tr><tr><td><p>A configuration of an organization’s resources designed to offer value for a consumer.</p></td></tr></tbody></table>

A product is not always fully visible to the consumer and is not exclusive to one consumer group as it can be used to address the needs of several different groups. For example, a software service can be offered as a simpler version for individual users, or as a more comprehensive corporate version. Products can exist regardless of the consumer.

<table><tbody><tr><td><strong>Definition: Service</strong></td></tr><tr><td><p>A means of enabling value co-creation by facilitating outcomes that customers want to achieve, without the customer having to manage specific costs and risks.</p></td></tr></tbody></table>

The services that an organization provides are based on one or more of its products. A service occurs during an interaction with a consumer, which becomes a service relationship. In order to start this relationship, an organization must present a service offering to a potential customer and a service agreement should be signed.

<table><tbody><tr><td><strong>Definition: Service offering</strong></td></tr><tr><td><p>A formal description of one or more services, designed to address the needs of a target consumer group. A service offering may include goods, access to resources, and service actions.</p></td></tr></tbody></table>

The visible part of a product is described in one or more service offerings addressing the needs of potential service consumers. Service offerings are often presented in a service catalogue for potential customers. For existing customers, a service catalogue provides a view on the services being consumed and agreements associated with them. These views are based on the stakeholder’s role within the customer organization.

<table><tbody><tr><td><strong>Definition: Service catalogue</strong></td></tr><tr><td><p>Structured information about all the services and service offerings of a service provider, relevant for a specific target audience.</p></td></tr></tbody></table>

The ‘service catalogue’ term usually refers to a tailored view on services and service offerings. In the context of the service catalogue practice, it can also be used for a collection of service data used as a single source of all service catalogue views. This may be managed as a centralized database or as multiple databases that are managed by different teams of the organization. This practice ensures effective integration of the data and quality of service-related information. This includes ensuring that the service information is correct, up to date, and available to relevant stakeholders. A close integration with other practices in the context of multiple value streams is needed to make it possible.

<table><tbody><tr><td><strong>Definition: Request catalogue</strong></td></tr><tr><td><p>A view of the service catalogue, providing details on service requests for existing and new services, which is made available for the user.</p></td></tr></tbody></table>

Request catalogues are addressed to users and can also be used by the service provider’s teams when they are interacting with users. As part of the service catalogue practice, request catalogues are maintained in a correct and up-to-date condition.

### 2.3 Scope

The scope of the service catalogue management practice includes:

*   defining the appropriate service description structure for the service catalogue to be well-structured and meeting the needs of stakeholders, including the agreed mandatory attributes and relationships
*   capturing the service information and keeping it up to date, ensuring the quality of data in the service catalogue
*   defining the different tailored views of the service catalogue for the relevant groups of stakeholders and, once agreed, implementing the views and changes to the service catalogue structure
*   publishing the service catalogue and managing different views for different stakeholders.

There are several activities and areas of responsibility that are not included in the service catalogue management practice, although they are still closely related to service catalogue management. These are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

#### Table 2.1 Activities related to the service catalogue management practice described in other practice guides

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Defining and managing the service portfolio</p></td><td><p>Portfolio management</p></td></tr><tr><td><p>Defining services and service offerings, including details of service utility and warranty</p></td><td><p>Business analysis<br>Service design</p></td></tr><tr><td><p>Establishing service level agreements with customers and suppliers</p></td><td><p>Service level management<br>Supplier management</p></td></tr><tr><td><p>Managing service requests</p></td><td><p>Service request management</p></td></tr><tr><td><p>Managing information about the relationships between services and other configuration items</p></td><td><p>Service configuration management</p></td></tr><tr><td><p>Managing information about IT service assets</p></td><td><p>IT asset management<br>Service financial management</p></td></tr></tbody></table>

### 2.4 Practice success factors

<table><tbody><tr><td><strong>Definition: Practice success factor</strong></td></tr><tr><td><p>A complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The service catalogue management practice includes the following PSFs:

*   ensuring that the organization’s service catalogues’ structure and scope meet organizational requirements
*   ensuring that the information in service catalogues meets stakeholders’ current and anticipated needs.

#### 2.4.1 Ensuring that the organization’s service catalogues’ structure and scope meet organizational requirements

The structure and scope of service catalogue should reflect the organization’s architecture of business, products, and services. To ensure this occurs, the service catalogue practice should be based on input from the strategy management, architecture management, and portfolio management practices. This input helps to answer the following questions:

*   Who is the target audience for service catalogue views?
*   What are their requirements for service catalogue views?
*   What services and service offerings should be included in the service catalogue?
*   What is the reasonable granularity of the service description?
*   What level of detail is needed to present services to stakeholders in an understandable way?
*   What set of service attributes can be sufficient to describe all the services and be applicable to all the services?
*   How should product and service relationships be reflected?
*   What service-related information is needed and where should it be sourced from?
*   How is the service catalogue published?
*   How should service catalogue information be updated?
*   What are the access requirements and controls?

Other sources of information for service catalogue planning include the following practices: service level management, service request management, relationship management, service configuration management, service financial management, and supplier management. These practices maintain information that is usually included in service catalogue views.

After analysing the requirements and expectations of an organization, service catalogue design is performed. It covers all four dimensions of service management:

*   **organizations and people** roles and responsibilities, service owners, and teams involved in development and operations
*   **information and technology** data and technology used, any data, or technology pre-requisites
*   **partners and suppliers** third-parties’ involvement, existing agreements and contracts, levels of support from partners
*   **value streams and processes** procedures and workflows.

Service catalogue design is subject to continual improvement. The main sources of improvements are:

*   regular reviews
*   catalogues of user feedback
*   changes in requirements
*   changes in the organization’s architecture
*   technology opportunities.

#### 2.4.2 Ensuring that the information in service catalogues meets stakeholders’ current and anticipated needs

Maintaining, updating, and providing the service catalogue should be automated as much as possible. It is uncommon to create service catalogue views manually upon request; typically, they are agreed with relevant stakeholders and updated and provided automatically. Where tailoring is needed, it is usually achieved by providing users with view-setting features.

This practice ensures that different stakeholder groups are considered, and tailored views are defined for them in the service catalogue based on the expectations of the respective stakeholders’ groups. The most popular and useful views may include:

*   **User view** Providing the information on the services and service offerings, containing the respective details from a user perspective. For example, service description, prerequisites, procedure to request a service, service level agreements, technology and channel usage, and information on service support. All this information should be filtered based on the user status and entitlement to the services.
*   **Customer view** Providing the information from a business perspective, containing information about agreed service levels, financial data, service performance and measurement, contractual requirements, and so on. This view may include service offerings describing services and service levels available to the customer. The customer view needs to be filtered to only reflect services and service offerings relevant to the customer and/or customer group. Views for new and existing customers differ in the details and scope of services.
*   **Service provider view** Providing technical, security-, risk-, and process-related information for use in service delivery. This includes technical requirements to use a service, technical solution details, security requirements, potential risks and possible mitigating measures, incident and problem information regarding the service, and so on. Multiple views are usually defined for service provider’s teams depending on their needs. For example, supplier managers and business analysts are likely to need different details of services. This tailoring can be achieved by creating different pre-set views or by providing flexible settings for internal catalogue users.

While multiple tailored views of the service catalogue are possible and useful, the creation of separate or isolated service catalogues within different technology systems should be avoided as this will increase segregation and complexity within the organization. Instead, a single repository of service data should be used to generate the agreed tailored views, which is beneficial for the organization. Service catalogue is usually built and managed as a database with a central repository for the services data and additional external data sources for service-related data; it is fed from other tools, providing role-based views and service dashboards. For example, for any given service, core service data is stored in the service catalogue, but also data from the financial, monitoring and event, and customer and user service systems is used seamlessly under the service catalogue interface.

To ensure that service catalogues are used and meet stakeholders’ requirements, it is important to measure and evaluate service catalogue usage. The easiest option is to survey stakeholders’ satisfaction; in many cases, using technology allows for user experience to be monitored directly (use patterns, favourite view settings, search requests). It is also useful to ensure that errors and inconsistencies in service catalogue information are reported, analysed, and corrected. For user- and customer-facing catalogue views, catalogue errors should be treated as incidents.

An understanding of the quality of service catalogue information and stakeholders’ satisfaction should be used as input for the continual improvement of the service catalogue and the practice.

The service catalogue management practice includes promoting the service catalogue and ensuring the catalogue is adopted across target audiences. Adoption is based on the positive experience of catalogue users. Several approaches and techniques can be useful for understanding and improving this experience, including:

*   agreeing on the service catalogue utility and warranty and ensuring the agreements are met
*   designing for usability
*   ensuring new users are enabled for effective catalogue use
*   treating internal and external users equally
*   monitoring and improving user satisfaction
*   monitoring and addressing feedback.

Service catalogue views for users and customers is an important factor of the overall satisfaction with the organization’s services. It is one of the key interfaces between the service provider and service consumers. It is also one of the most used tools within a service provider, and therefore should be easy to use.

Although some services and service management tools require special skills and experience from their users, the service catalogue should have an intuitive, familiar, and smooth interface for both internal and external users. This is especially important for service providers addressing their services to individual consumers on external markets. In this scenario, user and customer roles are usually combined, and individual consumers use a catalogue published by a service provider to engage, agree, and consume services. Inefficiencies in the catalogue interface can easily prevent these consumers from engaging with the service provider.

### 2.5 Key metrics

The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, KPIs, and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for service catalogue management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the service catalogue management practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.2.

#### Table 2.2 Examples of key metrics for the practice success factors

<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Ensuring that the organization’s service catalogues’ structure and scope meet organizational requirements</p></td><td><ul><li>Completeness of the service catalogue (number of services that are managed de-facto, yet not included in the catalogue)</li><li><span>Fulfilment of the agreed organization’s requirements to the catalogue design</span></li><li><span>Number and impact of missing, ineffective, or manual integrations with information sources required for the catalogue</span></li><li><span>Progress of implementation of documented catalogue design improvements</span></li></ul></td></tr><tr><td><p>Ensuring that the information in service catalogues meets stakeholders’ current and anticipated needs</p></td><td><ul><li>Satisfaction with the catalogue information, by stakeholder groups</li></ul><ul><li><span>Number and impact of catalogue errors (incorrect, missing, or dated information)</span><span></span></li><li><span>Satisfaction with the catalogue interface, by stakeholder group</span></li><li><span>Progress of implementation of documented catalogue content and interface improvements</span></li></ul></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the service catalogue management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

## 3. Value Streams and processes

### 3.1 Value stream contribution

Like any other ITIL management practice, the service catalogue management practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The service catalogue management practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which the practice contributes are:

*   engage
*   design and transition
*   deliver and support.

The contribution of the service catalogue management practice to the service value chain is shown in Figure 3.1.

![Image of Figure 3.1 shows Heatmap of the contribution of Service Catalogue Management to Value Chain activities](Service%20catalogue%20management%20ITIL%204%20Practice%20Guide/Picture1.png)

**Figure 3.1 Heatmap of the contribution of service catalogue management to value chain activities.**

### 3.2 Processes

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><strong>Definition: Process</strong></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

Service catalogue management activities form two main processes:

*   defining and maintaining service catalogue data and standard service catalogue views
*   providing and maintaining up-to-date service catalogue views to the agreed target audience.

#### 3.2.1 Defining and maintaining service catalogue data and standard service catalogue views

This process is focused on defining, agreeing, and maintaining the service catalogue structure, data, and standard views according to the stakeholder requirements. It includes the activities listed in Table 3.1 and transforms the inputs into outputs.

#### Table 3.1 Inputs, activities, and outputs of the defining and maintaining service catalogue data and standard service catalogue views process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Organization’s architecture</li><li>Organization’s strategy</li><li>Organization’s service portfolio</li><li>Customers’ and users’ requirements</li><li>Contracts and agreements with customers and suppliers</li><li>External data sources as relevant</li><li>Service catalogue feedback</li><li>Continual improvement register</li></ul></td><td><ul><li>Analyse stakeholders' requirements for the service catalogue</li><li>Define service catalogue data structure</li><li>Define and agree service catalogue standard views for key stakeholder groups</li><li>Collect and maintain service catalogue data</li></ul></td><td><ul><li>List of key service catalogue stakeholder groups</li><li>Agreed stakeholders’ requirements</li><li>Service catalogue data structure</li><li>Standard service catalogue views and user manuals</li><li>Template for new service data</li><li>Requirements for catalogue management tools</li><li>Data integration requirements</li><li>Requests for changes</li><li>Catalogue data published</li></ul></td></tr></tbody></table>

![Image of Figure 3.2 shows workflow process diagram for defining and maintaining Service Catalogue data and standard Service Catalogue views](Service%20catalogue%20management%20ITIL%204%20Practice%20Guide/Picture2.png)

**Figure 3.2 Workflow of the defining and maintaining service catalogue data and standard service catalogue views process.**

This process may vary, depending on the type and size of the organization, type and complexity of services, service customers, and service catalogue stakeholders. Table 3.2 gives an example of these variations.

#### Table 3.2 Activities of the defining and maintaining service catalogue data and standard service catalogue views process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Service catalogue for internal services (‘IT to business’)</strong></p></td><td><p><strong>Service catalogue for external services in a service provider company (‘IT as a business’)</strong></p></td></tr><tr><td><p>Analyse stakeholders' requirements for the service catalogue</p></td><td><p>The team responsible for service catalogue management analyses the organization’s strategy, architecture, and service portfolio. They identify key stakeholder groups, typically:</p><ul><li>within IT</li><li>customers</li><li>users.</li></ul><p>The team discovers and analyses stakeholders’ requirements. This may involve relationship managers, business analysts, and user support specialists. Where possible, interviews with key stakeholders and direct observation of their work are used.</p></td><td><p>The team responsible for the service catalogue management practice analyses the organization’s strategy, architecture, and service portfolio. They identify key stakeholder groups, which are typically internal and/or external users and customers, internal teams, partners and suppliers.</p><p>The team discovers and analyses stakeholders’ requirements. This may involve relationship managers, business analysts, supplier managers, and user support specialists.</p><p>Sources of requirements include:</p><ul><li>marketing research</li><li>benchmarking research</li><li>existing market or industry standards and good practices</li><li>applicable regulations</li></ul></td></tr><tr><td colspan="3"><p>The requirements analysis is used to define the following:</p><ul><li>Service description granularity required for the service catalogue</li><li>Structure of the core service data applicable to all services</li><li>Sources of data required by the stakeholders</li></ul></td></tr></tbody></table>

<table><tbody><tr><td><strong>Define service catalogue data structure</strong></td><td><p>Based on the gathered and analysed requirements, the structure of service catalogue is defined, including core services data that is common for all the services across the organization and view-specific data obtained from other sources.</p><p>The resulting data structure is analysed to define:</p><ul><li>the technical approach to collect and maintain the data</li><li>the approach to defining and presenting standard catalogue views</li><li>the requirements for automation and integration</li></ul><p>The requirements for automation and integration are processed as other requirements for automation, either internally or in cooperation with a third-party supplier. The implementation of technical solutions for the catalogue is outside of the practice’s scope; however, the service catalogue manager acts as a customer for automation solutions and participates in this role in all related activities.</p></td></tr><tr><td><strong>Define and agree service catalogue standard views for key stakeholder groups</strong></td><td><p>Based on the agreed requirements and data structure, standard views for key catalogue users groups are defined. Where necessary, requirements for automation are documented and submitted; where relevant, user manuals for setting and using the views are documented in cooperation with catalogue automation team(s).</p></td></tr><tr><td><strong>Collect and maintain service catalogue data</strong></td><td><p>After all of the requirements for automation and integration are fulfilled and the catalogue automation solutions are implemented, the agreed data is collected and entered following the agreed structure.</p><p>Where relevant, data update procedures and tools are agreed, tested, and implemented.</p><p>The service catalogue manager works with external data owners to ensure timely and efficient updates to the catalogue. Where applicable, data sharing protocols or application interfaces are agreed with the partners and suppliers, to ensure a structured and managed data flow.</p><p>The service catalogue manager works with other teams to ensure that the catalogue data is correct and complete, automation tools work as agreed, and stakeholders’ requirements for the service catalogue are fulfilled.</p></td></tr></tbody></table>

#### 3.2.2 Providing and maintaining up-to-date service catalogue views to the agreed target audience

This process is focused on operations of the service catalogue. It ensures that requests from catalogue users for an agreed catalogue view are fulfilled promptly and correctly.

In most situations, this process is fully or largely automated. Request channels, access rules, presented data, and its visualization are agreed as part of service catalogue design and automated; catalogue users simply ‘open’ the catalogue view they need and have access to. In some cases, this process may have manual activities due to unusual requests or incomplete automation.

This process includes the following activities and transforms the following inputs into outputs, as shown in Table 3.3.

#### Table 3.3 Inputs, activities, and outputs of the providing and maintaining up-to-date service catalogue views to the agreed target audience process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Service catalogue data</li><li>User and customer feedback, including compliments and complaints</li><li>Catalogue users’ requests for catalogue views</li><li>Access rules and controls</li><li>Relevant external data<br></li></ul></td><td><ul><li>Process a request for a service catalogue view</li><li>Validate service catalogue request</li><li>Form and present the requested view</li><li>Request and process users’ feedback</li></ul></td><td><ul><li>Service catalogue views</li><li>Feedback data</li><li>External data queries</li></ul></td></tr></tbody></table>

Figure 3.3 shows the workflow of providing and maintaining an up to date service catalogue.

![Image of Figure 3.3 shows workflow diagram for providing and maintaining an up to date Service Catalogue](Service%20catalogue%20management%20ITIL%204%20Practice%20Guide/Picture3.png)

**Figure 3.3 Workflow of the providing and maintaining up-to-date service catalogue views to the agreed target audience process.**

The activities of this process should be automated as much as possible.

#### Table 3.4 Activities of the providing and maintaining up-to-date service catalogue views to the agreed target audience process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Fully automated process</strong></p></td><td><p><strong>Largely manual process</strong></p></td></tr><tr><td><p>Process request for a service catalogue view</p></td><td><p>The catalogue user works with the application interface to select a catalogue view.</p></td><td><ul><li>Internal catalogue users contact the service catalogue manager; external users and customers contact the service provider through agreed channels.</li><li>After receiving the request, the service catalogue manager identifies data and data sources needed to fulfil the request.</li></ul></td></tr><tr><td><p>Validate service catalogue request</p></td><td><ul><li>Where applicable, the catalogue management information system checks the availability and quality of the requested data, including external integrations.</li><li>If the validation has failed, the user receives a relevant message.</li></ul></td><td><ul><li>The service catalogue manager validates the requestor’s entitlement to the requested data and data availability.</li><li>If the validation has failed, the user receives a relevant message.</li></ul></td></tr><tr><td><p>Form and present the requested view</p></td><td><p>The requested data is used to form the requested view and present it in the agreed form (usually on-screen).</p></td><td><p>The service catalogue manager collects relevant data and forms the requested view. It is presented to the requestor in the agreed form.</p></td></tr><tr><td><p>Request and process users’ feedback</p></td><td><p>According to the agreed schedule or in case of validation check failure, the catalogue user is invited to leave feedback. The feedback data is used as input to the process of catalogue design and other improvement initiatives.</p></td><td><p>According to the agreed schedule or in case of validation check failure, the catalogue user is invited to leave feedback. The feedback data is used as input to the process of catalogue design and other improvement initiatives.</p></td></tr></tbody></table>

Service catalogue management activities are performed by the service catalogue managers and teams responsible for the service's development and operation as described in tables 3.2 and 3.4. They may also involve suppliers and partners. These activities are also supported (and sometimes fully or partially automated) by tools and technologies. Automation is described in section 5.

## 4. Organizations and people

### 4.1 Roles, competencies, and responsibilities

The practice guides do not describe practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

#### Table 4.1 Competency codes and profiles

<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p><strong>L</strong></p></td><td><p><strong>Leader</strong> Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p><strong>A</strong></p></td><td><p><strong>Administrator</strong> Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p><strong>C</strong></p></td><td><p><strong>Coordinator/communicator</strong> Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p><strong>M</strong></p></td><td><p><strong>Methods and techniques expert</strong> Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p><strong>T</strong></p></td><td><p><strong>Technical expert</strong> Providing technical (IT) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

Table 4.2 shows the roles involved in service management practice activities.

#### Table 4.2 Examples of roles with responsibility for service catalogue management activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Responsible roles</strong></p></td><td><p><strong>Competency profile</strong></p></td><td><p><strong>Specific skills</strong></p></td></tr><tr><td><p><strong>Defining and maintaining service catalogue data and standard service catalogue views</strong></p></td></tr><tr><td><p>Analyse stakeholders' requirements for the service catalogue</p></td><td><ul><li>Service catalogue manager</li><li>Service designer</li><li>Business analyst</li><li>Service owner</li></ul></td><td><p>CTA</p></td><td><ul><li>Understanding the stakeholder’s work and needs</li><li>Analytical skills</li><li>Communication skills</li></ul></td></tr><tr><td><p>Define service catalogue data structure</p></td><td><ul><li>Service catalogue manager</li><li>Service architect</li><li>Service designer</li><li>Supplier manager</li></ul></td><td><p>TC</p></td><td><ul><li>Understanding of the organization’s system and data architecture</li><li>System analysis</li><li>Communication skills</li></ul></td></tr><tr><td><p>Define and agree service catalogue standard views for key stakeholder groups</p></td><td><ul><li>Service catalogue manager</li><li>service architect</li><li>service designer</li><li>service owner</li><li>customer relationship manager</li><li>supplier manager</li></ul></td><td><p>TC</p></td><td><ul><li>Understanding of the catalogue users’ needs</li><li>Available tools and user experience</li><li>Design thinking</li><li>Communication skills</li></ul></td></tr><tr><td><p>Collect and maintain service catalogue data</p></td><td><ul><li>Service catalogue manager</li><li>System owners</li><li>Technical specialists</li></ul></td><td><p>T</p></td><td><ul><li>Knowledge of the data architecture</li><li>Technical skills</li></ul></td></tr><tr><td><p><strong>Providing and maintaining up-to-date service catalogue views to the agreed target audience</strong></p></td></tr><tr><td><p>Process request for a service catalogue view</p></td><td><p>If manual:</p><ul><li>Service catalogue manager</li><li>Service desk agent</li><li>Account manager</li><li>Service owner</li><li>Sales manager</li></ul></td><td><p>C</p></td><td><p>Understanding of the requestor’s context and needs</p></td></tr><tr><td><p>Validate service catalogue request</p></td><td><p>If manual:</p><p>Service catalogue manager</p></td><td><p>CTA</p></td><td><ul><li>Understanding of the catalogue users’ needs</li><li>Good knowledge of the service catalogue structure and integrations</li><li>Skills in access control and related tools</li></ul></td></tr><tr><td><p>Form and present the requested view</p></td><td><p>If manual:</p><p>Service catalogue manager</p></td><td><p>TC</p></td><td><ul><li>Technical skills</li><li>Good knowledge of the service catalogue structure and integrations Communication skills</li></ul></td></tr><tr><td><p>Request and process users’ feedback</p></td><td><p>If manual:</p><ul><li>Service catalogue manager</li><li>Service desk agent</li><li>Relationship manager</li></ul></td><td><p>C</p></td><td><ul><li>Communication skills</li><li>Knowledge of the previous feedback and improvement status</li></ul></td></tr></tbody></table>

#### 4.1.1 Service catalogue manager role

The service catalogue manager is responsible for the service catalogue in the organization. This role has the following main responsibilities:

*   defining, designing, and maintaining the service catalogue
*   understanding and managing stakeholder relationships
*   continually improving the service catalogue structure, automation, and views
*   effectively integrating the service catalogue into value streams
*   effectively cooperating with other teams and roles
*   continually improving the practice.

In larger organizations, it is common to see job positions fully dedicated to this role, with one or more employees.

#### 4.1.2 Organizational structures and teams

If an organization employs more than one service catalogue manager, a service catalogue management team may be formed. This team may be formed from members of different organizational structures, or can be supported by an organizational structure of its own.

It is more common to have a dedicated team for service catalogue management when one of the following conditions are met:

*   The service catalogue is complex and critical for the organization’s business.
*   There is no sufficient automation of the catalogue data updates, so manual work is required.
*   Requirements for the catalogue’s structure and content are constantly changing.

Together, members of the service catalogue management team should develop the competencies and skills described in Table 4.2.

## 5. Information and technology

### 5.1 Information exchange

The effectiveness of the service catalogue management practice is based on the quality of the information used. This information includes, but is not limited to, information about:

*   the organization’s strategy, portfolios, and architectures
*   the organizational structure and stakeholder groups
*   service consumer groups, customers, and users
*   services and their architecture and design, statuses, and configurations
*   partners and suppliers, including contracts and agreements
*   legislation, policies, and requirements that regulate service provision
*   the financial aspects of services and service offerings (prices, promotions, offers, terms and conditions)
*   the service provision procedures and workflows
*   service delivery and support teams’ contact details and work schedules.

This information may take various forms. The key inputs and outputs of the practice are listed in section 3.

The volume of information used in the service catalogue may vary depending on its agreed purpose and structure. However, there is key service data that is usually included:

*   service name
*   service description
*   service status
*   service owner
*   service target audience.

Table 5.1 includes examples of information that is usually included in a service catalogue from other sources.

#### Table 5.1 Examples of service catalogue information obtained from other sources

<table><tbody><tr><td><p><strong>Attributes</strong></p></td><td><p><strong>Sources</strong></p></td></tr><tr><td><p>Service level, customers, users and users’ details, prices, agreements’ statuses, and key dates, contacts, available service requests, service metrics, and KPIs</p></td><td><p>Service level agreements with customers</p></td></tr><tr><td><p>Supporting services, related contracts, service levels, contacts, constraints, statuses, and key dates</p></td><td><p>Service level agreements with suppliers</p></td></tr><tr><td><p>Service costs, prices, other financial data</p></td><td><p>Service financial models, budgets, pricelists</p></td></tr><tr><td><p>Related services and configuration items, and supporting teams and their contacts</p></td><td><p>Configuration management database, service models</p></td></tr><tr><td><p>Related records (incidents, problems, changes)</p></td><td><p>Respective records</p></td></tr></tbody></table>

### 5.2 Automation and tooling

In most cases, the service catalogue management practice can significantly benefit from automation. Where this is possible and effective, it may involve the solutions outlined in Table 5.2.

#### Table 5.2 Automation solutions for service catalogue management activities

| 
**Process activity**

 | 

**Means of automation**

 | 

**Key functionality**

 | 

Impact on the effectiveness of the practice

 |
| --- | --- | --- | --- |
| 

**Defining and maintaining service catalogue data and standard service catalogue views**

 |
| 

Analyse stakeholders' requirements for the service catalogue

 | 

Communication and collaboration tools

 | 

Requirements gathering and review

 | 

Low

 |
| 

Define service catalogue data structure

 | 

Data modelling tools

 | 

Data modelling and visualization

 | 

High

 |
| 

Define and agree service catalogue standard views for key stakeholder groups

 | 

Information systems design and modelling tools

 | 

Forms design

 | 

High

 |
| 

Collect and maintain service catalogue data

 | 

Data integration tools, database management tools, specialized catalogue management tools, integrated service management toolsets

 | 

Initial population and ongoing maintenance of the service catalogue data, integrations and views

 | 

High

 |
| 

**Providing and maintaining up-to-date service catalogue views to the agreed target audience**

 |
| 

Process request for a service catalogue view

Validate service catalogue request

Form and present the requested view

 | 

Integrated service management toolsets, user portals

 | 

Presentation of a relevant actionable catalogue view

 | 

High

 |
| 

Request and process users’ feedback

 | 

Integrated service management toolsets, user portals, survey tools, rating tools

 | 

Collection of users’ feedback

 | 

Medium

 |

## 6. Partners and suppliers

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see *section 2.4 of ITIL Foundation: ITIL 4 Edition* for a model of a service relationship). These dependencies are likely to affect the service catalogue management practice and be reflected in the service catalogue. There are three major considerations for the practice:

*   third-party services reflected in the service catalogue
*   suppliers’ access to the organization’s service catalogue
*   using third-party tools for service catalogue automation.

### 6.1 Third-party services reflected in the service catalogue

Some third-party services may be technically provided directly to an organization’s customers, with the organization serving as a single point of responsibility and contact. Service catalogue serves as a key interface for customers and users and should provide correct and up-to-date information about third-party services; it should be as actionable as other organization’s services.

Quite often, organization’s services depend on third-party services and many of these dependencies affect service attributes included in the catalogue.

It is important to ensure that the organization’s service catalogue is integrated with suppliers’ data sources and their service catalogues. This integration should be as seamless as possible, ensuring an update of the relevant data without delays that may impact the quality of the organization’s service catalogue information.

When organizations participate in a complex service network, as a service integrator or as one of the integrated suppliers, the service catalogue is likely to become an important integration point between the parties involved in the network.

### 6.2 Suppliers’ access to organization’s service catalogue

The need for suppliers’ specialists to be involved in the organization’s service operation and support is reliant on the organization’s dependency on third-party services. Many organizations provide access to relevant information about their services to suppliers and partners, and service catalogue serves as a key interface. Suppliers’ specialists may use catalogue views similar to those used by organization’s technical teams, but with different level of access. It is important to ensure that security policies and contract obligations in an organization are not compromised, especially where suppliers may have access to information about service consumers and other suppliers.

### 6.3 Using third-party tools for service catalogue automation

The service catalogue management practice depends greatly on automation, and it is common to use third-party specialized solutions to automate service catalogue management activities. It is important to consider requirements for this automation and integration when organizations select an integrated service management toolset. Service catalogue data most likely will be available to the ITSM toolset vendor or support partner during service catalogue structure design and review, and during ongoing operations. This access implies extra due diligence checks when an ITSM toolset vendor is selected and support contracts are agreed. The more integrated the service catalogue, the more sensitive its raw data.

## 7. Important reminder

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the content of the ITIL practice guides, organizations should always follow the ITIL guiding principles:

*   focus on value
*   start where you are
*   progress iteratively with feedback
*   collaborate and promote visibility
*   think and work holistically
*   keep it simple and practical
*   optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of *ITIL Foundation: ITIL 4 Edition*.

## 8. Acknowledgements

AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

### 8.1 Authors

Donka Raytcheva, Antonina Klentsova.

### 8.2 Reviewers

Dinara Adyrbai, Akshay Anand, Roman Jouravlev.
