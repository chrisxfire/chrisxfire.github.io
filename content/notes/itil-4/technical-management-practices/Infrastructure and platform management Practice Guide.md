---
title: "Infrastructure and platform management: Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# 1. Source
Axelos International (https://www.axelos.com)

# 2. Overview
<table><tbody><tr><td><strong>Key message</strong></td></tr><tr><td><p>The purpose of the infrastructure and platform management practice is to oversee the infrastructure and platforms used by an organization. When carried out properly, this practice enables the monitoring of technology solutions available to the organization, including the technology and external service providers.</p></td></tr></tbody></table>

The infrastructure and platform management practice ensures that the organization has a high-quality IT infrastructure that efficiently meets its current and anticipated needs. ‘IT infrastructure’ as a concept includes all of the hardware, software, networks, and facilities that are required to develop, test, deliver, monitor, manage, and support IT services.

Depending on the architecture of the organization’s IT infrastructure, this practice may focus on the management of the physical environment, physical equipment, or digital infrastructure solutions, which may be the organization’s own resources or services provided by suppliers and partners. Often, IT infrastructure solutions are managed as services; in these cases, the infrastructure and platform management practice may include dedicated teams acting as service providers for the application and/or product teams within the organization. If this approach is taken, it is important to ensure that the infrastructure and platform teams are closely involved in the overall service delivery activities of the organization and follow the ITIL principles focus on value, think and work holistically, and collaborate and promote visibility. Members of these teams should understand the wider context of the organization and its service value system (SVS).

This practice covers all stages of the infrastructure solutions lifecycle, from ideation and gathering requirements to delivery and support. At every stage, it is used in conjunction with other practices (including the business analysis, architecture management, service design, availability management, capacity and performance management, service continuity management, information security management, risk management practices, and others). The importance of high-quality infrastructure and platforms for service delivery cannot be overstated; this practice is vital for the success of the organization’s digital services and digitized business processes.

## 2.2 Terms and concepts

The infrastructure and platform management practice provides the structure to deliver and support stable and well-performing technology services. Infrastructure and platform management is provided directly to the business, or supports the applications used by the business. With a robust infrastructure and platform management practice, an organization can enable value creation with the confidence that the underlying technology will meet organization’s and service consumers’ needs.

<table><tbody><tr><td><strong>Definition: IT infrastructure</strong></td></tr><tr><td><p>All of the hardware, software, networks, and <em>facilities</em> that are required to develop, test, deliver, monitor, manage, and support IT services.</p></td></tr></tbody></table>

A wide range of activities are used to run and manage IT infrastructure effectively. These activities range from understanding organization’s requirements and developing and planning infrastructure and platforms, to performing routine maintenance and overseeing infrastructure performance.

<table><tbody><tr><td><strong>Definition: Operation</strong></td></tr><tr><td><p>The routine of running and managing an activity, product, service, or other configuration item.</p></td></tr></tbody></table>

A large portion of the operational activities can be automated. Automation tools can monitor the environment, identify changes, distribute patches and other updates, provide asset inventory, and schedule and automate jobs.

### 2.2.1 Business alignment for infrastructure and platform solutions

Infrastructure and platform solutions are designed to meet specific quality criteria defined to support the organization’s needs. The infrastructure and platform management practice is closely connected with the architecture management practice, ensuring that all infrastructure and platform solutions comply with the chosen architectural approach, model and standards, as well as sharing knowledge on the innovation available and feeding possible infrastructure and platform solutions into architecture management. The infrastructure and platform management practice must support application architecture, data architecture, and business architecture as well as align to the organization’s overall vision and principles.

To ensure alignment to the overall architectural model, standardized infrastructure and platform solutions are defined to meet the organization’s needs in a repeatable manner, to simplify delivery and ongoing management for these services. Standardized services allow for efficient provisioning through repeatability and automation. Many infrastructure services are designed to enable speed and agility. Self-service capabilities leverage automation capabilities to allow for users or other IT staff to request and receive items without manual steps behind the scenes. This should account for the majority of the services that are in utilized in the environment. Examples of standardized solutions may include storage systems, application servers, database platforms, authentication systems, single-sign-on, and others.

In integration with the architecture management the practice, the infrastructure and platform management practice should ensure development or outsourcing and cost-efficient operation of flexible and compatible core infrastructure and platform solutions, that should be easily deployable and easily configured or merged to support the organization’s services or products, serving as building blocks for the complex solutions, products, and services. One of the examples of implementing such approach is usage of microservices, that are “small in size, messaging-enabled, bounded by contexts, autonomously developed, independently deployable, decentralized and built and released with automated processes”<sup>1</sup>.

When the standard solution does not align with the business, a tailored or customized solution must be developed. The selection of a non-standard service delays the delivery of the solution and increases the ongoing effort and cost to the business for support for the solution. These non-standard solutions should be deployed and managed as an exception due to the additional overhead it requires.

In cases where the technology is not currently in place, the solution must be designed together with the architecture management and service design practices for conceptual and detailed design. During design, the infrastructure and platform management practice, business, and technical requirements are aligned and the recommended infrastructure and platform solutions are determined. As the solution is not currently available within the environment, additional steps are taken to address the procurement, build, sourcing, and support of the solution. The solution should be evaluated by infrastructure and enterprise architecture to determine if this should be offered to additional consumers or to remain as an exception to the existing documented standards.

When an organization needs an infrastructure and platform solution, infrastructure and platform management practice ensures that a solution is designed and delivered to meet the organization’s requirements. There are several ways to provide a solution. For requests that can be fulfilled using documented standard packages, the solution is provided through defined provisioning methods.

### 2.2.2 Infrastructure and platform solution technologies – physical and virtual

The technology used for infrastructure and platform solutions is either physical or virtual. Physical resources run directly from the hardware, such as an operating system that is installed directly on the hardware. This operating system can either host the application or services directly or virtual systems can run on top of it.

Virtualization allows for additional systems to be built on the physical system. Virtualization software runs on the hardware and allows for additional operating systems that are isolated and separated to be installed, creating multiple servers residing on the physical server. All virtual systems may run on the same or different hardware, but the virtual capabilities allow for dynamic workload placement and other capabilities; it also allows for better utilization of the hardware. The logical structure that connects the virtual servers and the physical servers should be accounted for in the configuration management database (CMDB). Additional capabilities that allow for dynamic moving of workloads should also be represented in the data model.

Infrastructure technologies, such as software-defined networking, virtual servers, and object storage, simplify the provisioning of infrastructure services. This allows the organization to deliver services quickly through automation.

Virtualization has greatly improved provisioning, performance, capacity, and availability for solutions. Further development in the virtualization direction is the usage of infrastructure-as-code (IaC) solutions. IaC is a way of managing and provisioning IT infrastructure and platforms by using machine-readable definition files rather than physically configuring hardware components. IaC solutions significantly speed up design (including hypothesis testing), development, building, provisioning and changing the infrastructure and platform solutions. Such solutions also usually make the infrastructure more reliable and fault resistant.

### 2.2.3 Infrastructure and platform solution delivery models

Advancements in technical capabilities have changed how services are delivered. Service providers have embraced the ability to scale services. As organizations move to services offerings that allow for flexibility in terms of how the service is provided, the organization can choose the model that best aligns to their strategic goals. Many times, the preferred model is a combination of both internal and external provided services. This complexity drives the need for a comprehensive management approach that ensures end-to-end delivery meets customer expectations.

There are many models for providing infrastructure and platform solutions, ranging from in-house dedicated data centres to fully out-sourced cloud environments. Many organizations continue to provide and support infrastructure residing in their internal data centres. They can also use solutions external to their organization. Cloud solutions provide offerings that allow systems and applications to run in internal and external data centres. Most enterprises use public cloud providers for at least part of their infrastructure. *Cloud providers offer many solutions based on the expected needs of the business. An application may be accessed through the cloud, leaving infrastructure management activities beyond connecting to the cloud to be done externally by the application provider.* Cloud offerings can include platforms for application development and infrastructure specific services like storage or backup as a service.

*There is usually a mix of public and private cloud services in any organization.* Both cloud services and outsourcing can provide infrastructure and platform services. Cloud services provide technical capabilities whereas outsourcing performs IT functions in a similar manner to internal teams. The contract defines the outsourcing scope and service levels. Instead of managing technology directly, internal IT teams focus on managing the contractual obligations and interactions with internal teams in an outsourced environment.

### 2.2.4 Agile methods in infrastructure and platform management

Recent technology innovations have enabled changes to how infrastructure is delivered and supported. Development practices have been adopted by teams providing infrastructure and platform solutions. Engineering and support functions rely heavily on coding and other development capabilities for automation.

Along with a focus on development from a system perspective, many organizations have also moved into models that blend development and infrastructure capabilities on one team to provide coverage throughout the lifecycle. DevOps and site reliability engineering (SRE) are examples of these models.

Specifically, DevOps brings a robust landscape of tools to automate the tracking, building, and deploying of small, agile-based releases. Agile is a development framework, but DevOps includes the infrastructure components and operational activities. DevOps focuses on the opportunities across all technology components and drives automation to enable rapid system updates. Infrastructure can now fully benefit from structured development practices.

By accounting for the end-to-end development and management of the solution, this approach allows for operational improvements to be included in the development releases. Machine learning and AIOps leverages data collected on solutions to automate, address issues, or manage requests without development. Through operational visibility and development capabilities, the overall system is managed in a more comprehensive and consistent manner through automation.

When using DevOps for infrastructure and platform management, special attention must be paid to obsolete systems and monolithic solutions that require manual operation and, therefore, slow down all management processes and changes. There should be a clear roadmap of decommissioning and replacing such solutions or replacing the manual activities with automation. One of the ways to do this is have an SRE team to run operations.

SRE is a discipline that incorporates aspects of software engineering and applies them to infrastructure and operations problems with the goal of creating ultra-scalable and highly reliable solutions. SRE is an approach that tries to bridge the gap between development and operations and find a consensus of their opposite objectives, which is to develop and release solutions fast and have a stable solution to support. SRE teams usually have software developers who must support the solutions they develop, and this stimulates them to automate most of the manual support and management tasks (in the course of reducing toil: manual, repetitive, automatable, non-creative work). With this, infrastructure and platform solutions become more manageable, require less manual work, and gain agility in changes, delivery, and support. Probably one of the most important gains of SRE operations is that infrastructure scale-out doesn’t lead to according linear growth of the team size, as it often happens in classical operations.

<table><tbody><tr><td><strong>Key message</strong></td></tr><tr><td><p>The practice is involved throughout the lifecycle of product and services. Figure 2.1 from “The Site Reliability Workbook” by Google, illustrates how SRE teams are involved during the lifecycle. With minor variations, this illustration is applicable to other approaches to infrastructure and platform management.</p></td></tr></tbody></table>

![Image of Figure 2.1 shows diagram of Infrastructure and Platform Management during product and service lifecycle](Infrastructure%20and%20platform%20management%20Practice%20Guide/Picture1.png)

**Figure 2.1 Infrastructure and platform management during product and service lifecycle**

### 2.2.5 Reliability and maintainability

Once the solution is in production, the primary focus of the team supporting and operating the infrastructure is to ensure high-quality delivery through managing the ongoing performance and functionality of the infrastructure and platform solutions. This team may be a dedicated infrastructure team or a dedicated product team. The products and services rely on the solution’s availability and performance to support them. In production, the organization has high expectations for uptime and very little tolerance for any impact of any type on service or product. To meet these demands, the solutions must be reliable and maintainable. Beyond infrastructure and platform configurations to support reliability and maintainability, the infrastructure and platform management practice must ensure the solution is supportable. Supportability addresses the organization’s requirements to ensure that the solution is functional and ready to support products and services.

Reliability is designed with the system. Reliability requirements are aligned to the uptime and performance requirements, defined by the capacity and performance management practice. These requirements ensure the solutions are built in to support the organization’s requirements. For example, this may include high availability or redundant network connectivity.

<table><tbody><tr><td><strong>Definition: Reliability</strong></td></tr><tr><td><p>The ability of a product, service, or other configuration item to perform its intended function for a specified period of time or number of cycles.</p></td></tr></tbody></table>

Maintainability of a system should be addressed during the design of a new system and tested before being transitioned to production. There could be rules agreed for an infrastructure and platform solution, ensuring maintainability based on the organization’s requirements and industry practices. One example is the existence of a monitoring tool to identify issues, or general monitorability of the solution planned at the design phase. Other examples could be the existence of tools used to configure, deploy, and provision the solutions. These rules could also be used to manage partners and suppliers responsible for infrastructure and platform service components.

<table><tbody><tr><td><strong>Definition: Maintainability</strong></td></tr><tr><td><p>The ease with which a service or other entity can be repaired or modified.</p></td></tr></tbody></table>

If maintainability is not addressed during the initial design and as part of daily operations, higher support costs, extended outages, and negative impacts to performance will affect the production environment. Maintainability is improved through appropriate monitoring configurations, automation, and utilization of standards.

Another aspect of maintainability involves ensuring the solution is recoverable to meet availability targets. This aspect is tightly aligned with the service continuity management. Maintainability ensures that infrastructure and platform solutions can be recovered to meet availability targets. This may mean, for example, ensuring that the hardware contract supports on-site replacements within a set timeframe. It may also cover having on-site resources performing the repair. When committing to availability targets, the parts and resources needed to restore service need to be factored in and be in place throughout the solution lifecycle. The infrastructure and platform management practice requires that the right pieces are in place to diagnose, repair, and recover in order to restore services on time.

Automation is also used to improve a system’s maintainability. Repeatable actions are excellent candidates for automation. Software development and management tools and techniques, such as Agile and DevOps, can be applied to infrastructure and platform management to drive frequent updates to systems and configurations. By addressing opportunities as they are identified and implementing solutions in small releases, benefits are realized quickly.

## 2.3. Scope

The scope of the infrastructure and platform practice includes:
* activities used to plan, design, develop, deliver, maintain, and support infrastructure and platform technology
* infrastructure and platform technology including:
    * hardware (servers, desktops, routers, switches, storage, cabling, and data centre)
    * software (operating systems, desktop applications, and middleware)
    * management tools (monitoring, management tools, deployment, inventory)
    * web hosting
    * cloud infrastructure and platform
    * identification systems and single sign-on (SSO).
* infrastructure and platform management skills, including:
    * technical architecture and engineering
    * technical administration and operations
    * execution and enforcement of policies and procedures connected to infrastructure and platform management (planning, decision making, oversight).
* integration with other practices
* skills required for infrastructure and platform management, including infrastructure architecture, engineering, and administration.

There are many activities and areas of responsibility that are not included in the infrastructure and platform management practice, although they are still closely related to infrastructure and platform management. These are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices combine value chain activities through value streams to deliver value.

### Table 2.1 Activities related to the infrastructure and platform management practice described in other practice guides

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Restoration of infrastructure and platform technology and services including major incidents</p></td><td><p>Incident management</p></td></tr><tr><td><p>Defining permanent resolution or workarounds for infrastructure and platform known errors</p></td><td><p>Problem management</p></td></tr><tr><td><p>Management of changes to the infrastructure and platforms</p></td><td><p>Change enablement</p></td></tr><tr><td><p>Tracking and management of infrastructure and platform assets</p></td><td><p>IT asset management</p></td></tr><tr><td><p>Tracking of infrastructure and platform configurations in relationship to other configuration items (CIs)</p></td><td><p>Service configuration management</p></td></tr><tr><td><p>Monitoring, event management, and log management for infrastructure and platform technologies</p></td><td><p>Monitoring and event management</p></td></tr><tr><td><p>Infrastructure and platform design</p></td><td><p>Service design</p></td></tr><tr><td><p>Defining requirements for infrastructure and platform solutions</p></td><td><p>Business analysis</p></td></tr><tr><td><p>Definition of standards and road map for infrastructure and platforms</p></td><td><p>Architecture management</p></td></tr></tbody></table>

## 2.4 Practice success factors

<table><tbody><tr><td><strong>Definition: Practice success factor</strong></td></tr><tr><td><p>A complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity; it includes components from all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The infrastructure and platform practice includes the following PSFs:
* establishing an infrastructure and platform management approach to meet evolving organizational needs
* ensuring that the infrastructure and platform solutions meet the organization’s current and anticipated needs.

### 2.4.1 Establishing an infrastructure and platform management approach to meet evolving organizational needs

The needs of organizations and their customers are continually changing which leads to the technology industry continually transforming. The changes may result from industry trends, changes within organizations, business process innovation, or changes to business volumes. The infrastructure and platform management practice ensures that infrastructure and platform solutions are flexible and scalable so that they are aligned with demand. Organizational infrastructure and platforms meet this demand through optimized solutions that are designed for and used by all parts of the organization.

To properly design these solutions, teams delivering infrastructure and platform change must be aware of new technologies and techniques. The evolution of technology can be seen in examples like email, virtual server farms, storage arrays, single sign-on, and cloud platforms. When solutions are identified based on requirements, requests are promptly fulfilled. With virtual server technology that is used both internally and for cloud offerings, the turnaround time for requests can be reduced to minutes. Technological progress, such as virtualization, containers, continuous integration/continuous delivery (CI/CD), and IaC, significantly impacts the rate of change and innovation.

Organizations that deliver and support infrastructure and platform solutions have evolved through models, such as DevOps and SRE; they eliminate the use of traditional waterfall techniques in favour of end-to-end development and management within one team. Crucially, the organization’s structure and technology components must align with its overall strategic direction in order to ensure the consistent delivery and support of infrastructure and platform solutions. Components must align with the overall strategic direction to ensure consistent delivery and support of infrastructure and platform solutions.

It is important to plan how infrastructure and platform teams will identify, design, and introduce innovation into the environment at the solution and strategic levels. Depending on the current needs, infrastructure and platform management might need initial research and testing so that, when the need is presented, there is a clear plan of action. If the need is pressing, the technology may be selected, purchased, designed, and configured before any official requests are received.

The infrastructure and platform management practice should ensure that the infrastructure and platforms are built to promote experimentation, quick technology adoption, the ability to test theories and hypotheses, change the infrastructure and platform iteratively with feedback, fail fast, and learn from experience and errors in a safe environment. Each organization should define its innovation and risk appetite and consider their financial constraints for innovation in the infrastructure and platforms areas.

### 2.4.2 Ensuring that the infrastructure and platform solutions meet the organization’s current and anticipated needs

The main focus of the infrastructure and platform management practice should be ensuring that stakeholders receive value throughout the infrastructure and platform solution lifecycle. Stakeholders must be engaged from the initiation of a request or project until the solution’s retirement. Understanding stakeholder expectations, from design to the ongoing management and support of the solutions, is an essential aspect of delivering infrastructure and platform solutions. This ongoing relationship will drive improvement opportunities and ensure value continues to be co-created as the solution evolves.

When the organization needs a technical solution, requirements are defined in order to ensure that the solution meets the organization’s needs. The solution design should include technical and business requirements. The infrastructure and platform management practice is involved in analysing requirements to create a high-level design (in conjunction with the architecture management, business analysis, and service design practices, and others).

The requirements for infrastructure and platform solutions may come from different sources, including:
* architectural standards and guidelines
* compliance requirements, if the organization is subject to legislation
* direct requirements from customers, if a solution is a service or service component that will be directly released to customers.

Where possible, the infrastructure and platform management practice ensures that standards can be defined and utilized in order to simplify the management of infrastructure and platform solutions. The enforcement of these standards ensures the reliability and maintainability of solutions. Standards enable efficient and effective operations and may include the hardware and software versions, configuration settings, management and monitoring tools, and support structures. Through standards, solutions are easier to operate, monitor, and upgrade.

Designs should be assessed against current and planned standards and validated against the current and anticipated levels of availability, performance, capacity, information security, and so on. Management practices supporting these should have active involvement.

Standard infrastructure solution packages should be utilized wherever possible. Any portion of the solution that is not standard increases cost, delays delivery, and requires customized support throughout the life of the solution. Exceptions to standards may result in extended downtime or other impacts to the customer. They may also delay teams responsible for performing other activities for other infrastructure and platform solutions.

If there are multiple exceptions to a standard, a review should be conducted to ensure that the standard still meets the organization’s needs. If it does not, a new standard should be designed and its implementation should be planned. Retiring the standard may include planning the removal of current systems that were installed as part the retired offering in order to reduce technical debt and the potential risk to the environment. The development and maintenance of the standards and standard packages are also within the scope of the infrastructure and platform management practice.

Part of the practice’s focus is to manage risk to the organization throughout the infrastructure and platform. As part of this effort, input from practices such as information security, service continuity, and risk management are taken to ensure that risks are managed throughout the lifecycle of the solution. This ongoing management includes, for example, ensuring that network devices are configured based on defined security policies, controls are tested periodically, and risks are identified and effectively managed. Requirements are handled on an ongoing basis to prevent adverse impacts, such as extended service downtime or a security breach of confidential information.

The overall management of infrastructure and platform solutions often includes internal and third-party solutions and components. Understanding the overall structure of these solutions and ensuring that the overall level of service provided meets customer expectations is critical.

Management need visibility to validate that solutions are performing at acceptable levels and to highlight opportunities. These may include addressing any issues and identifying areas that could be improved. The infrastructure and platform management practice should provide visibility to stakeholders in performance and improvement plans. This practice interacts with other practices to ensure that any issues or requests on solutions are resolved promptly. For this reason, the practice participates in agreeing targets for incident response, restoration, and request fulfilment times to align with customer expectations. This practice may include managing and reporting on the ability of solutions to meet targets. This visibility also provides an opportunity to improve performance in this area through automation or process refinement.

This practice also contributes to ensure that the agreed-upon levels of service is met. The scope of this effort includes any internal or external components used in the solution. Third-party services must align with customer expectations, or the expectations must be reset. External providers must meet the service levels in their contracts. By managing performance levels across internal and external services, the practice is able to report performance and other outcomes to the business.

The infrastructure and platform management practice ensures that solutions within its scope effectively contribute to overall financial targets. Infrastructure and platform solutions should be benchmarked against cloud offerings and external provider solutions. From a technology perspective, automation, consolidation, and standardization simplify the infrastructure and platforms and release resources, which can then be used to drive value. The current and potential partnerships with external providers can also be evaluated and existing agreements optimized.

## 2.5 Key metrics

The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for infrastructure and platform management are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.3.

### Table 2.3 Examples of key metrics for the practice success factors

<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Establishing an infrastructure and platform management approach to meet evolving organizational needs</p></td><td><ul><li>Stakeholder satisfaction with the approach to management of infrastructure and platforms</li><li>Alignment of the infrastructure and platform management approach with the organization’s strategy and architecture</li><li>Number and impact of deviations from the organization’s strategy and architecture road map</li><li>Level of benefits, costs, and risks associated with the approach to management of infrastructure and platforms</li></ul></td></tr><tr><td><p>Ensuring that the infrastructure and platform solutions meet the organization’s current and anticipated needs</p></td><td><ul><li>Stakeholder satisfaction with infrastructure and platform solutions</li><li>Number and impact of infrastructure incidents</li><li>Number and impact of constraints imposed by infrastructure and platform solutions</li><li>Number and impact of deviations from the agreed approach</li></ul></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make them easier to use for the ongoing management of value streams and for the periodic assessment and continual improvement of the infrastructure and platform management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

[\[1\]](https://my.axelos.com/resource-hub/practice/infrastructure-and-platform-management-itil-4-practice-guide#_ftnref1) Nadareishvili, I., Mitra, R., McLarty, M., Amundsen, M., Microservice Architecture: Aligning Principles, Practices, and Culture, O’Reilly 2016

# 3. Value Streams and processes

## 3.1 Value stream contribution

Like any other ITIL management practice, the infrastructure and platform management practice contributes to multiple value streams. Remember, no value stream is made up of a single practice. The infrastructure and platform management practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which this practice contributes are:
* deliver and support
* design and transition
* obtain/build
* plan.

The contribution of the infrastructure and platform management practice to the service value chain is shown in Figure 3.1.

![Image of Figure 3.1 shows Heat map of the contribution of the infrastructure and platform management practice to Value Chain activities](Infrastructure%20and%20platform%20management%20Practice%20Guide/Picture2.png)

**Figure 3.1 Heat map of the contribution of the infrastructure and platform management practice to value chain activities**

## 3.2 Processes

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><strong>Definition: Process</strong></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

There are numerous models to structure activities of the infrastructure and platform management practice. These span several decades and range from waterfall and manual, to iterative and incremental.

This practice is one of the two ITIL practices (the other is the software development and management practice) where activities do not always form processes that could be described as sequences at the level of detail appropriate to this guide. This is because the infrastructure and platform management activities are always performed in a context of one or another value stream, and always in conjunction with other practices. However, activities of this practice can be categorized in three groups:
* technology planning
* product development
* technology operations.

### 3.2.1 Technology planning activities

Technology planning activities ensure that the organization has a technology management approach and a roadmap for infrastructure development and improvement. These activities ensure the organization’s financial, architectural, and resource plans are aligned. With formalized and repeatable planning and effective integration with other practices, infrastructure and platform solutions will continually support alignment with the strategic goals of the organization. Table 3.1 shows how the activities transforms the inputs into outputs.

### Table 3.1 Inputs, activities, and outputs of technology planning

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Organization’s principles, policies, and vision</li><li>Organizational strategy</li><li>Organizational structure</li><li>Product and service portfolio</li><li>Customer portfolio</li><li>Business analysis records and review reports</li><li>Audit reports<br></li></ul></td><td><ul><li>analyze the organization’s strategy and architecture</li><li>Develop and agree the infrastructure and platform management approach</li><li>Review the infrastructure and platform management approach</li></ul></td><td><ul><li>Infrastructure and platform management approach and roadmap</li><li>Improvement initiatives and requests for changes</li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![Image of Figure 3.2 workflow of technology planning process](Infrastructure%20and%20platform%20management%20Practice%20Guide/Picture3.png)

**Figure 3.2 Workflow of technology planning**

Table 3.2 provides an example of the technology planning activities.

### Table 3.2 Example activities of technology planning

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Example</strong></p></td></tr><tr><td><p>analyze the organization’s strategy and architecture</p></td><td><p>IT Leaders of the organization analyze the organization’s strategy, architecture road map, and portfolios and define requirements to the infrastructure and platform management approach.</p></td></tr><tr><td><p>Develop and agree the infrastructure and platform management approach</p></td><td><p>Business analysts, architects, product owners, and infrastructure experts agree and communicate an infrastructure and platform approach, including scope, sourcing strategy, methods and techniques, procedures, and responsibilities.</p></td></tr><tr><td><p>Review the infrastructure and platform management approach</p></td><td><p>Based on infrastructure review reports, periodic reviews, and audit reports, product owners and infrastructure experts review the effectiveness of the infrastructure and platform management approach and provide input to the analyze the organization and requirements activity, and/or initiate required changes.</p></td></tr></tbody></table>

### 3.2.2 Product development activities

In many organizations these activities are performed within product development value streams in conjunction with other practices. The infrastructure and platform management practice serves as a source of technical expertise and other resources to support product ideation, design, development, and deployment. In other organizations, infrastructure and platform solutions are developed in a separate value stream and provided to as services to product teams and their products. The activities of the infrastructure and platform practices are similar in these scenarios. In many cases, infrastructure solutions are sourced from external developers; the activities of the practice are focused on ensuring that the solutions meet the organization’s requirements and constraints.

This group includes the activities outlined in Table 3.3 and transforms the inputs into outputs.

## Table 3.3 Inputs, activities, and outputs of product development

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Infrastructure and platform management approach</li><li>Solution requirements</li><li>Budget and other resources and constraints</li><li>Sourcing and supplier management policies</li><li>Sourcing and build policies and guidance</li><li>Operational standards</li><li>Success criteria</li><li>Project structure (schedule, assignment, methods)<br></li></ul></td><td><ul><li>Create a basic solution design</li><li>Create a detailed solution design</li><li>Source/develop/configure the components</li><li>Source/build/configure the solution</li><li>Support validation and testing</li><li>Support deployment and release</li><li>Review solution development and implementation</li></ul></td><td><ul><li>Basic and detailed design</li></ul><ul><li>Agreed service level objectives</li><li>Components and solutions</li><li>Solution documentation</li><li>Setup in management tools including monitoring, ITSM tools</li><li>Operational run books</li><li>Reports and scheduled reviews</li></ul></td></tr></tbody></table>

The focus of technology delivery and engineering is on designing, building, and transitioning infrastructure and platform services. These activities may vary, depending on how the services will be delivered and how the organization applies these steps, as is outlined in Table 3.4.

### Table 3.4 Technology delivery and engineering activities

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Internal build</strong></td><td><strong>Sourced</strong></td></tr><tr><td><span>Create a basic solution design</span></td><td colspan="2"><span>Based on the requirements identified by business analysts and product owner, infrastructure specialists agree service level objectives for the infrastructure solution and create a basic solution design. The basic design is approved by the product owner.</span></td></tr><tr><td><span>Create a detailed solution design</span></td><td colspan="2"><p>Infrastructure specialists and/or site reliability engineers creates a detailed solution design, ensuring its reliability, efficiency, scalability, and other quality characteristics required by the agreed SLOs and the organization’s infrastructure management approach are met.</p><p>The resulting design includes a recommended sourcing and delivery model for the components and the solution.</p></td></tr><tr><td>Source/develop/configure the components</td><td>Agreed components are developed and configured by infrastructure specialists according to the design</td><td>Agreed components are procured and configured by a supplier according to the design; their work is monitored and accepted by infrastructure specialists</td></tr><tr><td>Source/build/configure the solution</td><td>Agreed solution/system is built/configured by infrastructure specialists according to the design; their work is accepted by the product owner</td><td>Agreed solution/system is built/configured by a supplier according to the design; their work is monitored and accepted by infrastructure specialists and the product owner</td></tr><tr><td>Support validation and testing</td><td>Infrastructure specialists participate in the validation and testing of the components and the solution at all stages of the solution development, ensuring effective integration with the service validation and testing practice</td><td>Infrastructure specialists participate in the validation and testing of the components and the solution at all stages of the solution development, ensuring effective integration with the service validation and testing practice and the supplier management practice</td></tr><tr><td>Support deployment and release</td><td>Infrastructure specialists participate in the deployment and release of the solution, ensuring effective integration with the respective practices</td><td>Infrastructure specialists participate in the deployment and release of the solution, ensuring effective integration with the supplier management practice</td></tr><tr><td>Review solution development and implementation</td><td>Infrastructure specialists, product owners, and application developers review the infrastructure solution development activities and outcomes. The resulting report is used as an input to the technology planning activities and other improvement initiatives</td><td>Infrastructure specialists, product owners, application developers, and supplier representatives review the infrastructure solution development activities and outcomes. The resulting report is used as an input to the technology planning activities, supplier management improvements, and other improvement initiatives</td></tr></tbody></table>

Product development activities ensure the delivery of a supportable solution that meets the organization’s needs and agreed SLOs. Even if an external provider provides a solution, steps are taken to ensure it fits into the overall delivery and support model.

### 3.2.3 Technology operation activities

The technology operations activities are performed after the solution goes into the live environment. These activities include planned maintenance and unplanned support activities. Maintenance focuses on the normal operations of the solution, such as administration and monitoring. Support focuses on addressing events, incidents, alerts, and other areas that are not performing as planned. In an organization that is not functioning well, the unplanned activities typically take most, if not all resource time. A more mature organization will focus on planned activities that will result in less unplanned work.

This group includes the following activities, and transforms the following inputs into outputs:

### Table 3.5 Inputs, activities, and outputs of the technology operation

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Solutions and support documentation, such as operational run books</li><li>Policies and guidelines</li><li>Monitoring data</li><li>Queries (incidents, problems, and so on)</li><li>SLAs<br></li></ul></td><td><ul><li>Manage queues of queries and events</li><li>Perform scheduled tasks</li><li>Patch and update the system</li></ul></td><td><ul><li>Reports</li><li>Closed tickets and events</li><li>Scheduled job completion</li><li>Backup completion</li><li>Updated solution and support documentation</li><li>Automation</li><li>Improvements</li></ul></td></tr></tbody></table>

Table 3.6 provides example descriptions of the technology operation activities

### Table 3.6 Technology operation activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Example</strong></p></td></tr><tr><td><p>Manage queues of queries and events</p></td><td><p>Infrastructure management teams and tools process incoming queries and events, ensuring timely and successful resolution of detected incidents, alerts, and other events requiring a response. Logs and reports reflecting this activity are created as agreed in the infrastructure and platform management approach and solution documentation.</p><p>Examples of this work include:</p><ul><li>rolling back a bad software push</li><li>blocking or rate-limiting unwanted traffic</li><li>bringing up additional serving capacity</li><li>using the monitoring systems (for alerting and dashboards)</li><li>solving incidents</li><li>analysing problems</li><li>conducting post-mortems.</li></ul></td></tr><tr><td><p>Perform scheduled tasks</p></td><td><p>Several actions are performed by infrastructure management teams or tools on a scheduled basis, such as daily backups or a data transfer between systems. Logs and reports reflecting this activity are created as agreed in the infrastructure and platform management approach and solution documentation.</p><p>Examples of this work include:</p><ul><li>administering production jobs</li><li>describing the architecture, various components, and dependencies of the services</li><li>testing back-up restoration</li><li>training users</li><li>reviewing supplier performance</li><li>reviewing solution performance.</li></ul></td></tr><tr><td><p>Patch and update the system</p></td><td><p>Patches and system updates are released to the environment in a structured manner. Typically, patches deployed to the lower environments for testing and then deployed to production. Despite this structure, there are exceptions where systems are not patched as part of this scheduled release due to an application incompatibility, business usage of the solution, or issues identified through testing. It is important to track the solutions that are not at current levels. Completing these updates should be rolled out promptly to maintain overall supportability. Up-to-date solutions reduce the risk of downtime or security breaches.</p><p>There are also situations where system updates or patches are installed to resolve an incident and then need to be rolled out to the rest of the organization. The result of applying patches and updates reactively creates a non-standard environment.</p><p>The infrastructure specialist manages these exceptions and identifies a plan to address these exceptions. Understanding and addressing these deviations is a vital part of technology management.</p></td></tr></tbody></table>

The technology operation activities ensure that solutions are available and functioning as designed from acceptance into the live environment through retirements. Technical experts and technical coordinators perform the activities in this process.

# 4. Organizations and people

## 4.1 Roles, competencies, and responsibilities

The practice guides do not describe the roles of practice owners or managers that should exist for all practices. They focus instead on specialist roles specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

### Table 4.1 Competency codes and profiles

<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p><strong>L</strong></p></td><td><p><strong>Leader</strong> Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p><strong>A</strong></p></td><td><p><strong>Administrator</strong> Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p><strong>C</strong></p></td><td><p><strong>Coordinator/communicator</strong> Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p><strong>M</strong></p></td><td><p><strong>Methods and techniques expert</strong> Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p><strong>T</strong></p></td><td><p><strong>Technical expert</strong> Providing technical (IT) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

### Table 4.2 Examples of the roles involved in infrastructure and platform management activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Responsible roles</strong></p></td><td><p><strong>Competency profile</strong></p></td><td><p><strong>Specific skills</strong></p></td></tr><tr><td><p><strong>Technology planning</strong></p></td></tr><tr><td><p>analyze the organization’s strategy and architecture</p></td><td><p>Architects, business analysts, product owners, infrastructure specialists</p></td><td><p>TC</p></td><td><ul><li>Good knowledge of the organization and its environment, portfolios, products, resources, and customers</li></ul><ul><li>Understanding of the current infrastructure architecture and architecture roadmap</li></ul><ul><li>Analytical skills</li></ul><li>Good knowledge of current and available technology</li></td></tr><tr><td><p>Develop and agree the infrastructure and platform management approach</p></td><td><p>Architects, business analysts, product owners, infrastructure specialists, consultants</p></td><td><p>TLMC</p></td><td><ul><li>Good knowledge of the organization and its environment, portfolios, products, resources, and customers</li><li>Excellent knowledge of current and available infrastructure and platform solutions</li><li>Good knowledge of infrastructure and technology services suppliers and market</li></ul></td></tr><tr><td><p>Review the infrastructure and platform management approach</p></td><td><p>Architects, business analysts, product owners, infrastructure specialists, consultants</p></td><td><p>TCA</p></td><td><ul><li>Good knowledge of the organization and its environment, portfolios, products, resources, and customers</li><li>Understanding of the current infrastructure architecture and architecture roadmap</li><li>Analytical skills</li><li>Good knowledge of current and available technology</li></ul></td></tr><tr><td><p><strong>Product development</strong></p></td></tr><tr><td><p>Create a basic solution design</p></td><td><p>Solution architects, infrastructure specialists, site reliability engineers, product owners</p></td><td><p>TA</p></td><td><ul><li>Understanding of the requirements</li><li>Good knowledge of the infrastructure and platform management approach</li><li>Expertise in the available technology</li></ul></td></tr><tr><td><p>Create a detailed solution design</p></td><td><p>Solution architects, infrastructure specialists, site reliability engineers, product owners</p></td><td><p>TA</p></td><td><ul><li>Understanding of the requirements</li><li>Good knowledge of the infrastructure and platform management approach</li><li>Expertise in the available technology and services</li></ul></td></tr><tr><td><p>Source/develop/configure the components</p></td><td><p>Infrastructure specialists, site reliability engineers, product owners, suppliers</p></td><td><p>TC</p></td><td><ul><li>Technical expertise</li><li>Communication and collaboration skills</li></ul></td></tr><tr><td><p>Source/build/configure the solution</p></td><td><p>Infrastructure specialists, site reliability engineers, product owners, suppliers</p></td><td><p>TC</p></td><td><ul><li>Technical expertise</li><li>Communication and collaboration skills</li></ul></td></tr><tr><td><p>Support validation and testing</p></td><td><p>Infrastructure specialists, site reliability engineers, product owners, suppliers</p></td><td><p>TC</p></td><td><ul><li>Technical expertise</li><li>Communication and collaboration skills</li></ul></td></tr><tr><td><p>Support deployment and release</p></td><td><p>Infrastructure specialists, site reliability engineers, product owners, suppliers</p></td><td><p>TC</p></td><td><ul><li>Technical expertise</li><li>Communication and collaboration skills</li></ul></td></tr><tr><td><p>Review solution development and implementation</p></td><td><p>Solution architects, infrastructure specialists, site reliability engineers, product owners</p></td><td><p>TCA</p></td><td><ul><li>Good knowledge of the infrastructure and platform management approach</li><li>Technical expertise</li><li>Good knowledge of the organization and its environment, portfolios, products, resources, and customers</li></ul></td></tr><tr><td><p><strong>Technology operations</strong></p></td></tr><tr><td><p>Manage queues of queries and events</p></td><td><p>Infrastructure specialists, site reliability engineers</p></td><td><p>TA</p></td><td><ul><li>Technical knowledge</li><li>Understanding of business and customer context</li><li>Communication and coordination skills</li></ul></td></tr><tr><td><p>Perform scheduled tasks</p></td><td><p>Infrastructure specialists, site reliability engineers</p></td><td><p>TA</p></td><td><ul><li>Technical administration knowledge</li></ul></td></tr><tr><td><p>Patch and update the system</p></td><td><p>Infrastructure specialists, site reliability engineers</p></td><td><p>TA</p></td><td><ul><li>Knowledge of security policies, standards, and requirements</li><li>Technical knowledge</li></ul></td></tr></tbody></table>

### 4.1.1 Infrastructure specialist

The key role for this practice is infrastructure specialist. This is a generic term to describe roles that can be specified either by the technology, like network, SRE, and so on (for example, network specialist, site reliability engineer, or virtualization specialist) or by the phase in product lifecycle, like design, testing, or operations (for example,. infrastructure designer/development specialist, testing specialist, or operations administrator).

Those distinctions are defined by the organization’s size and structure, but the general set of competencies are similar, and usually includes:
* technology subject matter expertise
* good understanding of the organization’s architecture
* knowledge of the frameworks and techniques adopted by the organization
* knowledge of organization’s products and services
* service mindset
* good knowledge of organization’s operating model and value streams.

Examples of other roles which can be involved in infrastructure and platform management activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

## 4.2 Organizational structures and teams

Infrastructure and platform management specialists often form a dedicated team (or teams). However, in some organizations they are included in product teams and focused on infrastructure solutions supporting respective products. Regardless of the organizational solution, it is important to maintain shared view and responsibility across infrastructure and product teams.

<table><tbody><tr><td><strong>Key message</strong></td></tr><tr><td><p>Rigid boundaries between “application development” and “production” (sometimes called programmers and operators) are counterproductive. This is especially true if the segregation of responsibilities and classification of ops as a cost centre leads to power imbalances or discrepancies in esteem or pay</p><p>(…) Ideally, both product development and SRE teams should have a holistic view of the stack—the frontend, backend, libraries, storage, kernels, and physical machine—and no team should jealously own single components. It turns out that you can get a lot more done if you “blur the lines”11 and have SREs instrument JavaScript, or product developers qualify kernels: knowledge of how to make changes and the authority to do so are much more widespread, and incentives to jealously guard any particular function are removed.”</p><p>This quote from “The Site Reliability Workbook” by Google refers specifically to SRE teams. However, it is valid for any other approach to infrastructure and platform management.</p></td></tr></tbody></table>

The infrastructure and platform management practice needs to allow for organization variations while ensuring some level of consistency across infrastructure teams. The teams may be split by geography, type of technology, or business service. Having an overall structure to manage practice changes and communication is important to keep the overall service functioning in an optimal manner. This may be done with an overall governance group or through representation in an infrastructure committee.

# 5. Information and technology

## 5.1 Information exchange

The effectiveness of the infrastructure and platform management practice is based on the quality of the information used. This information includes, but is not limited to:
* business services and processes
* customers and users
* partner and suppliers including contracts and service levels
* SLAs
* architecture and design documentation
* portfolio and project management plans
* policies, requirements, and controls
* change records
* incident records
* request records
* problem records
* release records
* financial information
* application development and testing information
* system information (versions, baselines, configurations)
* monitoring and event information
* IT assets and inventory information.

## 5.2 Automation and tooling

In most cases, the infrastructure and platform management practice can significantly benefit from automation. Where this is possible and effective, it may involve the solutions outlined in Table 5.1.

### Table 5.1. Automation solutions for infrastructure platform management activities

<table><tbody><tr><td><p><strong>Process activity </strong></p></td><td><p><strong>Means of automation </strong></p></td><td><p><strong>Key functionality </strong></p></td><td><p><strong>Impact on the effectiveness of the practice </strong></p></td><td></td></tr><tr><td><p><strong>Technology planning</strong></p></td></tr><tr><td><p>analyze the organization’s strategy and architecture</p></td><td><ul><li>Communication and collaboration tools</li></ul><ul><li>Analytical systems</li></ul><li>Knowledge management tools</li></td><td><p>Collection, processing, and presentation of data from diverse sources</p></td><td><p>High</p></td><td></td></tr><tr><td><p>Develop and agree the infrastructure and platform management approach</p></td><td><p>Communication and collaboration tools</p></td><td><p>Collaboration and information sharing</p></td><td><p>Medium</p></td><td></td></tr><tr><td><p>Review the infrastructure and platform management approach</p></td><td><ul><li>Communication and collaboration tools</li><li>Analytical systems</li><li>Knowledge management tools</li></ul></td><td><ul><li>Collection, processing, and presentation of data from diverse sources</li></ul><ul><li>Reporting engines</li><li><span>Dashboard systems</span></li></ul></td><td><p>High</p></td><td></td></tr><tr><td><p><strong>Product development</strong></p></td></tr><tr><td><p>Create a basic solution design</p></td><td><p>Workflow tools including task assignment, routing, approvals, tracking, and notifications</p></td><td><p>Ability to assign design tasks and approval for planning activities, including status tracking, notifications, and reporting to ensure actions are on task and the design is approved</p></td><td><p>High</p></td><td></td></tr><tr><td><p>Create a detailed solution design</p></td><td><p>Workflow tools including task assignment, routing, approvals, tracking and notifications, contract management with templates, approvals, and review schedules</p></td><td><p>Ability to assign tasks and approval for planning activities, including status tracking, notifications, and reporting to ensure actions are on task</p></td><td><p>High</p></td><td></td></tr><tr><td><p>Source/develop/configure the components</p></td><td><p>Automated provisioning, building, and configuring tools</p></td><td><p>Ability to receive approved request and to build a solution with no or limited manual intervention ensuring consistent and timely delivery</p></td><td><p>High</p></td><td></td></tr><tr><td><p>Source/build/configure the solution</p></td><td><p>Automated provisioning, building, and configuring tools</p></td><td><p>Ability to receive approved request and to build a solution with no or limited manual intervention ensuring consistent and timely delivery</p></td><td><p>High</p></td><td></td></tr><tr><td><p>Support validation and testing</p></td><td><p>Automated testing and defect tracking</p></td><td><p>Automated testing, reporting, and logging into the defect management system</p></td><td><p>High</p></td><td></td></tr><tr><td><p>Support deployment and release</p></td><td><p>Deployment tools</p></td><td><p>Automated deployment from testing to implementation, including submission of change request</p></td><td><p>High</p></td><td></td></tr><tr><td><p>Review solution development and implementation</p></td><td><ul><li>Workflow tools including task assignment, routing, approvals, tracking, and notifications</li><li>System health monitoring and reporting tools</li></ul></td><td><p>Dashboards and reports, trend analysis</p></td><td><p>Medium to high</p></td><td></td></tr><tr><td><p><strong>Technology operation</strong></p></td></tr><tr><td><p>Manage queues of queries and events</p></td><td><ul><li>Automated request provisioning, automated resolution, ChatOps, AIOps,</li><li>Workflow tools</li></ul></td><td><ul><li>Ability to close repeat tickets automatically and assign the tickets automatically to the correct group without manual triage steps</li><li>Task assignment, routing, approvals, tracking and notifications</li></ul></td><td><p>High</p></td></tr><tr><td><p>Perform scheduled tasks</p></td><td><ul><li>Job scheduling tools and scripts for backup, batch, and other automated tasks</li><li>Vulnerability tools and report and testing automation for compliance, automated solution recovery, and testing</li><li>TSM report and dashboard automation</li><li>Automated report consolidation and generation, customer feedback surveys</li><li>Workflow tools including task assignment, routing, approvals, tracking, and notifications</li></ul></td><td><ul><li>Automation of scheduled tasks including notification on failures reducing the potential for missed procedure execution</li><li>Ability to automatically verify and test solutions for security hardening, recoverability, and controls</li></ul></td><td><p>High</p></td></tr><tr><td><p>Patch and update the system</p></td><td><p>System and security patch deployment and inventory tools, software distribution and inventory tools</p></td><td><p>Ability to automatically deploy and report on installation status for patches and system updates</p></td><td><p>High</p></td></tr></tbody></table>

# 6. Partners and suppliers

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of *ITIL Foundation: ITIL 4 Edition* for a model of a service relationship).

The infrastructure and platform management practice allows for many outsourcing options both from an activity perspective as well as from a technology perspective. Table 6.1 provides examples of areas that are candidates for outsourcing.

### Table 6.1 Infrastructure and platform management sourcing considerations

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Opportunity</strong></p></td><td><p><strong>Applicability</strong></p></td></tr><tr><td><p>Provisioning</p></td><td><p>Delivery of desktops, servers, computer, network, and storage services or other technology services</p></td><td><p>Outsourcing is most effective when standards are in place. Outsourcing may be selectively used for remote locations.</p></td></tr><tr><td><p>Support</p></td><td><p>Restoration and prevention of incidents for in-scope technologies</p></td><td><p>Support for the entire capability may be outsourced or focused on specific roles. Providers should adhere to standard service desk processes for a consistent customer experience. This works well for remote sites, especially for desktop support.</p></td></tr><tr><td><p>Administration</p></td><td><p>Performing routine tasks based on operational procedures and requests</p></td><td><p>Administrative tasks need to be well documented and sufficient access must be provided.</p></td></tr><tr><td><p>Operations centre</p></td><td><p>Outsourcing the operations centre function reduces the need to ensure adequate coverage with internal staff, especially if it is provided at all times. This function can provide monitoring, systems management, job scheduling, or other activities</p></td><td><p>This reduces internal staffing requirements. This function must be well documented, have adequate access and frequent touchpoints are recommended to understand any open issues or improvement opportunities.</p></td></tr><tr><td><p>Backup/restore</p></td><td><p>Provider configures and manages backup jobs and repositories, addresses backup failures, and restores files as needed</p></td><td><p>Providers may leverage internal backup tools or may include backup solutions and storage as part of the agreement.</p></td></tr><tr><td><p>Systems management, patching, or other updates</p></td><td><p>Manage systems to keep up to date for versions, configurations, and patches</p></td><td><p>Standards and configurations must be well documented, and access provided. Access to management tools is required.</p></td></tr><tr><td><p>Technology ownership</p></td><td><p>Technology can be leased through subscription services, reducing the capital required to implement and maintain technology</p></td><td><p>With cloud offerings, this is a prominent trend in the industry. This allows for service levels and capabilities to be delivered without the overhead of building and supporting technology internally.</p></td></tr></tbody></table>

With a large amount of opportunity within this space, understanding and managing outsourcing risks is an important activity to ensure that services meet customer expectations. This should be done in a close conjunction with other practices, such as the risk management and supplier management practices.

Some examples of these risks are:
* loss of flexibility due to constraints of agreement
* additional unplanned costs if the scope needs to be modified or if consumption exceeds the contractual terms
* contractual service levels may not align with customer expectations
* security and policy adherence of providers
* loss of internal talent as role moves from performing activities to oversight of those activities
* lack of visibility.

Although all functions can be outsourced, it is recommended to retain oversight and architecture functions. Oversight ensures providers are delivering to their committed levels and allows insight into potential improvements to the existing agreement. To effectively support and continue to deliver services, the knowledge of how solutions connect across providers must be well understood by the internal team. As the specific knowledge in specific technologies moves to the provider, there should be an architectural role internally that understands the design and operations of the infrastructure environment.

# 7. Important reminder

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the content of the ITIL practice guides, organizations should always follow the ITIL guiding principles:
* focus on value
* start where you are
* progress iteratively with feedback
* collaborate and promote visibility
* think and work holistically
* keep it simple and practical
* optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of *ITIL Foundation: ITIL 4 Edition*.

# 8. Acknowledgements

AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

## 8.1 Authors

Angie Pederson.

## 8.2  Reviewers

Dinara Adyrbayeva, Akshay Anand, Peter Farenden, Roman Jouravlev, Vernon Lloyd.

## References

1.  Nadareishvili, I., Mitra, R., McLarty, M., Amundsen, M., Microservice Architecture: Aligning Principles, Practices, and Culture, O’Reilly 2016
