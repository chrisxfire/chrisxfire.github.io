---
title: deployment management
date: 2023-10-20T00:00:00-06:00
draft: true
weight: 1
---


August 29, 2023
26 min read

ITIL
ITIL4 Practice Guides
Deployment management: ITIL 4 Practice Guide
73 Likes
This document provides practical guidance for the deployment management practice.

Table of Contents
1. 
About this guide
This guide provides practical guidance for the deployment management practice. It is split into seven main sections, covering:

general information about the practice
the practice’s processes and activities and their roles in the service value chain
the organizations and people involved in the practice
the information and technology supporting the practice
considerations for partners and suppliers for the practice
information on assessing and developing the capability of the practice

recommendations for succeeding in the practice.

1.1 ITIL® 4 qualification scheme
Selected content of this document is examinable as a part of the following syllabus:

ITIL Specialist Create, Deliver and Support
ITIL Specialist High-velocity IT
ITIL Practitioner Deployment Management
ITIL Specialist Plan, Implement and Control.
Please refer to the respective syllabus documents for details.

2. 
General information
2.1 Purpose and description
Key message

The purpose of the deployment management practice is to move new or changed hardware, software, documentation, processes, or any other component to live environments. It may also be involved in deploying components to other environments for testing or staging.

Definition: Deployment

The movement of any service component into any environment.

The deployment management practice is responsible for moving a service or service component into a designated environment. This practice enables the deployment or removal of service components from or to different environments, including development, integration, live, production, test, or staging environments.

The practice is usually applied to digital and physical IT components, including software, hardware, documentation, licences, and data, within the agreed scope of environments controlled by the organization.

The deployment management practice is a key practice of service management. Effective deployment management is beneficial for both the service provider and service consumer.

Benefits for the service provider include:

Faster time to market by delivering working software and hardware to users quickly and efficiently
Reduced risk of errors and downtime related to product and service updates
Controlled and efficient deployment of service components to different environments
Improved agility supporting faster and more efficient software development and release
Effective integration of deployments into the service provider’s value streams.

Benefits for the service consumer include:

Support of business agility; faster time to market for new and improved business products and services
Seamless updates of business products and services

Reduced risks and losses caused by product and service updates

Reduced costs of product and service updates.

2.2 Terms and concepts
2.2.1 Environments
The deployment management practice enables the movement of products, services, and service components between the environments.

Definition: Environment

A subset of the IT infrastructure that is used for a particular purpose.

A service component’s lifecycle may vary depending on its type and the sourcing approach. The number and purpose of controlled environments within the organization may also vary. Table 2.1 provides a list of example environments for an organization that develops software.

Table 2.1 List of example environments for an organization that develops software
Environment

Purpose

Development/Integration

Developing and integrating software

Test

Testing service components

Staging

Testing releases including products, services and other configuration items

Live/Production

Delivering IT services to service consumers


For products and components sourced outside the organization, development environments can be out of the organization’s control. For products and services delivered to service consumers outside of the organization, control over the live environment can be limited. Other variations are possible.

2.2.2 Continuous integration, continuous delivery, and continuous deployment (CI/CD)
The key concepts for deployment in Agile and DevOps are:

Continuous integration Integrating, building, and testing code within the software development environment.
Continuous delivery Continuous delivery means that built software can be released to production at any time. Frequent deployments are possible, but deployment decisions are taken on a case-by-case basis, usually because organizations prefer a slower rate of deployment.
Continuous deployment Changes go through the pipeline and are automatically put into the production environment, enabling multiple production deployments per day. Continuous deployment relies on continuous delivery.
These approaches are supported by the software development and management, service validation and testing, deployment management, infrastructure and platform management, and release management practices. These practices involve specific skills, processes, procedures, automation tools, and agreements with third parties. They enable the continuous pipeline for integration, delivery, and deployment. This also affects the design of other practices, such as service configuration management, monitoring and event management, incident management, and others.

2.3 Scope
The scope of the deployment management practice includes:

the effective movement (transition) of products, services, and service components between controlled environments, such as the development, test, staging, and live environments.
the effective removal of products, services, and service components from designated environments.
These additions, modifications, and removals can be part of authorized changes or releases which can be triggered by:

new or changed service requirements
new features or releases
technical and operational changes
third-party change requirements
service retirements and removals
support or troubleshooting
service requests
service and component maintenance.

Several activities and areas of responsibility are not included in the deployment management practice, although they are still closely related to deployment. These are listed in Table 2.2, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.


Table 2.2 Deployment-related activities described in other practice guides
Activity

Practice guide

Authorizing changes/releases

Change enablement

Making services and components in the live environment available to users

Release management

Testing and validating services and service components

Service validation and testing

Developing software

Software development and management

Developing and building infrastructure components

Preparing and maintaining target environments for deployments

Infrastructure and platform management

Maintaining authorized repositories of service components

IT asset management

Naming, versioning, and controlling the service components

Service configuration management

2.4 Practice success factors
Definition: Practice success factor

A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The deployment management practice includes the following PSFs:

establishing and maintaining effective approaches to the deployment of services and service components across the organization
ensuring the effective deployment of services and service components in the context of the organization’s value streams.

2.4.1 Establishing and maintaining effective approaches to the deployment of services and service components across the organization
The deployment management practice includes defining and agreeing a model or several models to use when deploying products, services, and components.

Definition: Deployment model

A repeatable approach to the management of particular types of deployments.

These models may use one deployment approach or combine deployment approaches, depending on their specific services and requirements, as well as the sizes, types, and impacts of the service components that are being deployed.

Models can be defined for deploying services or service components of similar types. Such deployment models could be defined based on several factors, including:

automation considerations
costs/resource limitations
expected frequency of the deployments
rate of change of customer requirements
rate of change of technology
risks of flaws in components
source of components
user adoption behaviours and preferences
visibility of the technology change to service consumers.
Based on these and other relevant considerations, organizations define a set of models for the deployment of different service components. These models may describe different solutions in all four dimensions of service management. Table 2.3 outlines some example models.

Table 2.3 Example models for the deployment of different service components.
Deployment model applicability

Organizations and people

Information and technology

Value streams and processes

Partners and suppliers

Hardware components of services provided to external service consumers

A service provider should arrange a delivery team for the transportation and installation of the components

A range of tools can be used to automate the procurement, invoicing, user communication, and scheduling of the installation of hardware

An installation order can be triggered by new or changed value streams that include clear authorizations to procure and install new hardware

Third-party shipping, delivery, and installation service providers can be employed, as agreed between the parties

Hardware components of services obtained from a vendor

According to the delivery and installation clause in the vendor contract, the responsibilities for obtaining hardware and ensuring its correct installation should be clearly defined

Vendor catalogues may be used for ordering the components, as well as to store and provide up-to-date installation manuals. A configuration management tool should be populated with documentation supplied with the hardware, including records and documents, such as warranty certificates, maintenance schedules, and so on

Vendor activities, such as invoicing and shipping, should be accounted for during the value stream design; interfaces between parties need to be founded in the contracts

Third-party shipping, delivery, and installation service providers can be employed, as agreed between the parties

Software components of services provided to external service consumers

The service provider can have staff perform roadshows to service consumers to promote new software components and facilitate change awareness

An automated deployment toolset is utilized to make software available for use or ordering

Service providers can implement additional controls before a component is deployed, such as quality assurances, security, or commercial; is is crucial to account for such controls in-partially or fully-automated deployment pipelines

Partners can be engaged in deployment, such as additional bespoke testing of the software made available by the vendor prior to its deployment to the consumer environment

Software components of services developed in house

DevOps teams are likely to perform the deployment of software

The continual integration and continual deployment pipeline toolset can be used to deploy software to a controlled environment

Service provider organizations have to establish organizational controls over the course of deployment, ensuring that controls are not excessive

Third parties can action some steps of the deployment model; for example, manual environment configuration activities

Deployment models also define the flow of deployment through controlled environments, responsibilities of the involved parties, triggers for deployment, and interactions with other practices’ activities in the context of value streams.

These models may be flexible enough to adapt to changing circumstances, such as the scale, urgency, or complexity of the deployment.

Deployment models, and the deployment management practice in general, should be a subject to continual improvement with an aim to eliminate waste and increase effectiveness and efficiency.

2.4.2 Ensuring the effective deployment of services and service components in the context of the organization’s value streams
Ensuring effective deployment requires orchestrating resources in all four dimensions of service management.

The effectiveness and efficiency of the deployment is significantly dependent on, and can be considerably impacted by, the availability of the relevant resources, skills, technology, tools and infrastructure. The effective use of technology and automation in deployment can improve the consistency, agility, and efficiency of the practice.

For changes and releases to be successful, it is crucial that the changed or released service’s or service component’s integrity is maintained throughout the move process. Any unauthorized change caused by manual, process, or technology errors can negatively impact the objectives and outcomes of the changes and releases, often significantly impacting the organization.

The success of service moves depends on the effective and efficient management of changes and releases, which in turn depends on timely deployments that align with requirements and objectives. Alignment of the deployment to the change and release requirements, as well as key aspects such as schedule and cost, must be managed effectively.

2.5 Key metrics
The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for deployment management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of deployment management to the effectiveness and efficiency of those value streams. Some examples of key metrics of deployment management are given in Table 2.4.

Table 2.4 Examples of metrics for the practice success factors
Practice success factors

Key metrics

Establishing and maintaining effective approaches to the deployment of services and service components across the organization

Level of stakeholders’ satisfaction with the rate of change of products and services supported by deployments
Rate of adoption of the agreed approach to deployment across the organization

Level of key partners’ and service consumers’ alignment with deployment approaches

Number of audit findings and external compliance issues caused by deployments

Ensuring effective deployment of services and service components in the context of the organization’s value streams

Level of stakeholders’ satisfaction with lead time to deploy
Percentage of successful deployments/number of deployment errors/failures
Number/percentage of incidents related to deployments
Timeliness/adherence to deployments schedule
Deployment backlog throughput
Level of stakeholders’ satisfaction with quality of deployments
The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the deployment management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

3. 
Value Streams and processes
3.1 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

Definition: Process

A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.

Deployment management activities form two processes:

Deployment model development and improvement
Deployment lifecycle management.
3.1.1 Deployment model development and improvement
This process focuses on the continual improvement of the deployment management practice, deployment models, and the deployment procedures. It is performed regularly but can also be triggered by deployment failures which highlight inefficiencies and other improvement opportunities. Regular reviews may occur every three months, or more frequently, depending on the effectiveness of the existing models and procedures.

This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

Table 3.1 Inputs, activities, and outputs of the deployment model development and improvement
Key inputs

Activities

Key outputs

Current deployment approach, models and procedures
Deployment records
Deployment failure reports
Policies and regulatory requirements
Release models
Service configuration information
IT asset information
SLAs with consumers and suppliers/partners
Capacity and performance plans and reports
Continuity policies and plans
Security policies and plans
Deployment model planning
Deployment model implementation
Deployment model testing
Deployment review and deployment records analysis
Deployment model improvement initiation
Deployment model update and communication
Updated deployment models and procedures
Communication of updates to deployment models and procedures update
Change requests
Improvement initiatives
Deployment review reports
Updated knowledge management articles
Lessons learnt
Figure 3.1 Workflow of the deployment model development and improvement process
Table 3.2 provides examples of the process activities.

Table 3.2 Activities of the deployment model development and improvement process
Activity

Description

Deployment model planning

When a product follows a similar low-risk, high-success-rate deployment pattern and there are means to eliminate waste and reduce deployment lead times, the deployment manager may choose to define a new deployment model. The deployment model should reduce the human involvement and control over the deployment.

Deployment model implementation

The deployment manager arranges for appropriate pipeline tools to be configured to support the new model, such as access settings, code support, or branching procedures. Alternatively, if automated deployment tools are not applicable, the deployment manager establishes and communicates adequate guidelines to the teams and parties involved.

Deployment model testing

The deployment manager tests the new deployment model to ensure proper edge-case handling and workflow. Where testing is impossible, the deployment manager oversees the first of the model’s live runs.

Deployment review and deployment failure records analysis

The deployment manager, together with service owners and other relevant stakeholders, performs a review of selected deployments or deployment failures. They identify opportunities for the optimization of deployment models and deployment procedures.

Deployment model improvement initiation

The deployment manager registers the improvement initiatives to be processed with the involvement of the continual improvement practice, or initiates a change request, if the deployment models and procedures are included within the scope of change enablement.

Deployment model update and communication

If the deployment model is successfully updated, it is communicated to the relevant stakeholders. This is usually done by the deployment manager and/or the service or resource owner.

3.1.2 Deployment lifecycle management
This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

Table 3.3 Inputs, activities, and outputs of the deployment lifecycle management process
Key inputs

Activities

Key outputs

Deployment requirements and expectations
Environment details
Service components/release components
Hardware and software components from the authorized repositories of ITAM and definitive media library
Acceptance criteria
Deployment planning
Verification of the service components
Verification of the target environments
Deployment execution
Deployment verification
Deployed service components/releases
Deployment records
Deployment communications
Feedback and inputs to change enablement, release management, service validation and testing, project management, and so on
Updates to onboarding procedures, customer knowledge base, service desk data
Figure 3.2 shows a workflow diagram of the process.

Figure 3.2 Workflow of the deployment lifecycle management process
In an organization that has adopted a CI/CD framework, many of these activities will be performed in an automated fashion, without manual intervention.

Table 3.4 provides examples of the process activities.

Table 3.4 Activities of the deployment models development and review process
Activity

Manual deployment to a datacenter	Automated deployment of a software component
Deployment planning	After a trigger from deployment (often procurement or the change request initiator), the service provider will schedule the shipping, delivering, verification, storing, and installation of hardware components. This schedule will align with the priorities of other work units for the affected teams and other resources.	Deployments in automated pipelines are triggered by committing all of the necessary pieces of code to a branch of the development version control system that will contain software features that are prepared for deployment.
Verification of the service components	Upon receiving delivered components, the service provider checks the completeness of the inventory, including the documentation, and conducts basic quality checks before accepting the delivery.	The code in the appointed branch is deployed to a suitable test environment, tested, and any issues are fixed directly in the branch.
The ‘deploy, test, fix, redeploy, retest’ cycle continues until a pre-set quality threshold of automated tests is met.

Verification of the target environment	The item is delivered to the installation location, where it is installed with the aim of causing minimal disruption to the service users. The installation location should have sufficient power, back-up power, air- conditioning, and fire protection arrangements. It may be necessary to include target environment checks in the deployment plan.	For Infrastructure as Code (IaC) solutions, the configuration of a virtual environment in which the software should be run also follows an automated pipeline and is deployed to the virtual resources alongside the software code.
Deployment execution	The service provider or staff of a supplier installs and activates the equipment according to the installation instructions, which may include intermediate checks.	Deployment to an environment is automated, but can include additional human interaction steps before the actual deployment to account for business, security, or other non-automated types of verification.
Deployment verification	After the item has been installed, a series of tests is performed to confirm the equipment is functioning.
The staff performing the installation notifies those who triggered the deployment of the deployment results.

The version control system sends notifications to the change requestor, such as a product owner, when the deployment is complete.
3.2 Value stream contribution
3.2.1 Service value streams
To perform certain tasks or respond to particular situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario. Once designed, value streams should be subject to continual improvement.

Definition: Value stream

A series of steps an organization undertakes to create and deliver products and services to consumers.

In practice, however, many organizations come to the use of the value stream concept after having worked for a while (sometimes for years) without the value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the ‘As Is’ situation, and the de-facto flows of work, and to analyse them in order to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding the existing value streams is critical to improving an organization’s performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services. Combined, the organizations’ value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations follow best practice recommendations for various service management practices, such as incident management, change enablement, software development, and many others. However, the practices are often adopted and organized in a siloed, isolated manner, as they are presented in service management bodies of knowledge. In reality, a flow of work required to create or restore value, for a customer or another stakeholder, is almost never limited to one practice.

3.2.2 Deployment management in service value streams
As mentioned in section 2.3, deployment management contributes to implementation of changes initiated by a range of sources. The practice plays an important role in service value streams involving changes. These are outlined in Table 3.5.

Table 3.5 Role of the deployment management practice in service value streams
Service value stream	Role of the deployment management practice
Incident resolution	Deployment of fixed components, patches, updated versions of software, and other changes executed to solve an incident and restore normal service operations
Request fulfilment	Deployment of changed or new components and versions required to fulfil a request model
Product and service continual improvement	Deployment of fixed components, patches, updated versions of software, and other changes executed to realize an approved improvement initiative
Delivery of new and changed services	Deployment of new and changed components, patches, updated versions of software, and other changes executed to fulfil an agreed product or service development plan
Ongoing operations and maintenance	Deployment of changed or new components and versions required to fulfil an agreed maintenance of the live systems and components
In all cases, deployment is a part of a change implementation and should be coordinated with other activities in the change lifecycle, such as purchasing, configuring, testing, and release. Deployments are within the scope of the change lifecycle management process (see the change enablement practice guide). The change enablement practice ensures the correct selection of a relevant deployment model; scheduling of the deployment phase of the change implementation; and acceptance of the deployment. At the same time, the deployment management practice ensures that valid deployment models are available and correctly executed when required according to the change plan and change schedule. Figure 3.3 illustrates the positioning of the deployment lifecycle management process in the various value streams involving changes. Note: the figure only addresses deployments to live environments. In practice, there may be a number of transitions between environments during one change, and each one would be subject to deployment lifecycle management.
Figure 3.3 Deployment lifecycle management in service value streams
It is important to ensure the effective integration of the deployment management practice in the management of change lifecycles and further in the service value streams. Depending on the business context of the changes, deployment may be assigned different levels of urgency and impact, which should be possible to address with the application of a relevant deployment model.

3.2.3 Analysing a service value stream
3.2.3.1 The key steps of a service value stream analysis
The following are some simple and practical recommendations for service value stream analysis and mapping:

1. Identify the scope of the value stream analysis

This can be mapped to a particular product or service or applied to most or all of them. Similarly, service value streams may differ for different consumers; for example, Deployments can be performed differently for internal and external service consumers, or for B2B and B2C products, Service category, services based on products developed inhouse or sourced externally, automated or manual deployment method, change models, waterfall or agile approach followed by the organization.

2. Define the purpose of the value stream from the business standpoint

Make sure the stakeholders’ outcomes or concerns are clearly understood, since they are the ones defining value. In the case of Deployment management, it is usually the change requestor, product owner or business user who needs a new functionality, feature, or a new service; however, there are usually other interested parties. For example, internal stakeholders such as release managers, the quality assurance team, and the software development teams, as well as the value of the value stream, should be considered from the business perspective, not solely from the user perspective.

3. Do the value stream walk

Walk through or directly experience the steps and information flow as they go in practice (consider the Lean technique of Gemba walk):

a. Identify the workflow steps

b. Collect data as you walk

c. Evaluate the workflow steps

Typically, the criteria for evaluation are:

value for the stakeholder (does the step add value for the business stakeholder?)
effective or performance (is the step performed well?)
efficiency (is the step being performed in an optimal manner?)
availability (are required resources available to execute the step?)
capacity (are required resources enough?)
flexibility (are the required resources interchangable within the step?).
d. Map the activities and the information flows

In an ideal situation, the flow goes smoothly without delays and pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

e. Create and review the timeline and resource level

Map out process times and lead times for resources and workload through the workflow steps.

4. Reflect on the value stream map (VSM)

Identify factors that might not have been entirely apparent at first. The information collected is used at this step to find waste.

5. Create a 'to be' VSM

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

6. Using the 'to be' VSM, plan improvements

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

3.2.3.2 Deployment management considerations in a service value stream analysis
To ensure that relevant deployment management activities are included in service value streams, the following steps can be added to the above recommendations.

At the scoping step (1), identify the IT and business services related to the value stream and the involved business stakeholders. For example, when an IT service provider deploys IT services or software or hardware components desired by the business users who in turn provide services to the business clients, should the deployment value stream involve full deployment or incremental deployment in the live environment for the clients, or should it be limited to the deployment in the staging or test environment? 

Make sure the value stream is understood (step 2) from the standpoint of the business, not only of the service provider.

During the service value stream walk (3a), identify other practices involved in dealing with deployments at every step. Which practices provide required information (service configuration, CI information, target destination, solution architecture, and so on)? What if the deployment activities involve third parties?

During the evaluation of workflow steps (3c), evaluate the step’s impact on the transition of new or changed hardware, software, documentation, processes, or any other component to live environments or any other stage such as test or staging environments. Special attention should be paid to steps with low business value, low performance, waiting time, manual activities and availability or capacity issues. It is not unusual to find steps which serve some internal control or bureaucratic purposes but delay the deployment velocity.
At the reflection and planning steps (4-5), ensure that the deployment management flow is optimized for business value throughout the stream, not only at the deployment management practice activities.

Include the creation or update of deployment models (see section 3.1.1) in the value stream improvement plans (step 6).

4. 
Organizations and people
4.1 Roles, competences, and responsibilities
The practice guides do not describe the practice management roles, such as practice owner, practice lead, or practice coach. They focus instead on specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

Table 4.1 Competency codes and profiles
Competency code

Competency profile (activities and skills)

L

Leader Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes

А

Administrator Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements

C

Coordinator/communicator Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns

М

Methods and techniques expert Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement

Т

Technical expert Providing technical (IT or other subject matter) expertise and conducting expertise-based assignments

Two practice-specific roles may be found in organizations: deployment manager and deployment practitioner. These roles are often introduced in organizations where the number of deployments is high. In other organizations, these roles might be combined with, or assigned to, other roles carrying related responsibilities in development, operations, IT asset teams, and so on.

4.1.1 Deployment manager role
A deployment manager role calls for a strong knowledge of the organization’s business, products and services, technology, platforms, frameworks, and processes. The role requires strong planning and project management skills and the ability and authority to coordinate teamwork. The competency profile for this role is LACM. This role is usually responsible for the planning, management, and coordination of deployment management as a practice as well as the deployment of individual releases, including:

planning deployments
ensuring the alignment of deployment plans with change/release plans, requirements, and objectives
planning, coordinating, and ensuring the availability of the resources needed for the effective completion of deployments
effectively managing overlaps or conflicts among multiple deployments
implementing and maintaining effective control and governance to ensure the integrity of components throughout the deployment practice
managing and/or ensuring effective interfaces between and coordination with other practices and stakeholders
managing and optimizing deployment resources to ensure optimum levels of availability, capability, and capacity to manage deployments
monitoring, reporting, analysing, and improving deployment performance against defined KPIs.
In more complex organizations, some of the deployment management responsibilities may be delegated to the role of deployment coordinators, team leaders, or any other similar additional roles.

4.1.2 Deployment practitioner role
A deployment practitioner role calls for strong technical skills and effective teamwork. The competency profile for this role is TAC. This role is usually responsible for effective deployments to the target environments in alignment with applicable requirements, objectives, and targets, including:

acquiring, maintaining, and continually improving the skills and capabilities required for technical aspects of deployments
contributing and assisting in deployment planning
ensuring the integrity of components throughout the deployment practice
managing and coordinating deployment documentation, records, and communications, including for training purposes
coordinating with other practices and stakeholders and facilitating interfaces between groups
verifying and providing feedback on deployments to stakeholders
contributing to monitoring, reporting, analysing, and improving deployment performance against defined KPIs.
In some organizational contexts, the deployment practitioner role can be divided into multiple categories and levels based on the types and requirements of the deployments and platforms, the complexity of organization’s products and services, and so on.

4.1.3 Roles involved in the deployment management activities
Examples of other roles which can be involved in the deployment management activities are listed in Table 4.1, together with the associated competency profiles and specific skills.


Table 4.2 Examples of roles with responsibility for deployment management activities
Activity

Responsible roles

Competency profile

Specific skills

Deployment model development and improvement process

Deployment model planning

Deployment manager
Service owner
Product owner
MTCA

Understanding of the service design, resource configuration, and business impact
Good knowledge of existing deployment activities
Deployment model implementation

Deployment manager
Service owner
Product owner
CMTA

Knowledge of deployment pipeline tools
Knowledge of the continual improvement and change enablement practices
Deployment model testing

Deployment manager
Service owner
Product owner
TAC

Good knowledge of testing practices across the workflows
Good knowledge of requirements and commitments, service levels
Knowledge of deployment models and methods; analytical skills
Deployment review and deployment records analysis

Deployment manager
Service owner
Product owner
Supplier

MTCA

Understanding of the service design, resource configuration, and business impacts
Good knowledge of deployment models
Good knowledge of requirements and commitments, service levels
Knowledge of deployment models and methods; analytical skills
Deployment model improvement initiation

Deployment manager
Service owner
Product owner
MTCA

Understanding of the service design, resource configuration, business impacts, and service levels
Good knowledge of deployment models, diagnostic tools, and methods
Knowledge of the continual improvement and change enablement practices
Deployment model update and communication

Deployment manager
Service owner
Product owner
Service desk agent
MCA

Knowledge of communication procedures and tools

Deployment lifecycle management process

Deployment planning

Service owner
Product owner
Development team member
Technical specialist
Service desk agent
Engagement manager
Delivery manager
Users
MCTA

Understanding the deployment’s impact on the service levels, user experiences, and environments
Good communication and cross-team coordination skills
Good knowledge of deployment models
Understanding of technical service design, supporting infrastructure and platforms, development tools
Verification of the target environments

Technical specialist
Deployment manager
Development team member
Systems administrator
Infrastructure team member
Service owner
Product owner
TA

Good knowledge of environments and infrastructure

Deployment execution

Technical specialist
Deployment manager
Development team member
Systems administrator
Infrastructure team member
TCA

Understanding of technical service design, supporting infrastructure and platforms, development tools
Good knowledge of deployment models
Deployment verification

Technical specialist
Deployment manager
Development team member
Systems administrator
Infrastructure team member
TA	
Understanding of technical design of services and components
Good knowledge of service performance, service levels, and user experience
4.2 Organization structures and teams
Designated deployment management teams are unusual, except in very large organizations with significant volumes and complexity of deployment. This role is often handled by the technical/operations or platform teams.

In a DevOps environment, deployment is often automated through the continual deployment practice/framework with use of deployment pipelines. However, the role of deployment manager is often still relevant; the deployment manager would own the overall practice and aspects around deployment. This role could be independently established or combined with other relevant and suitable roles, such as release manager.

4.2.1 Team structures for deployment management
Typically, in large organizations with significant volumes and complexity of deployments, deployment teams are structured in one of three ways:

Product/service based
Practice-based
Deployment as a service.
4.2.1.1 Product/service based
Deployment managers and practitioners belong to teams, each of which is focused on a particular product- or technology-defined scope such as a single product, service, platform, or a set of features. This type of deployment team is empowered to build and deliver value quickly by moving new or changed hardware, software, documentation, processes, or any other component within the team’s responsibility to live environments. It may also be involved in deploying components to other environments for testing or staging. The product-based teams are cross functional teams and perform all or most activities throughout the product lifecycle, from planning to development, deployment, release, and operations.

4.2.1.2 Practice-based
Many organizations adopt organizational structures based on the practices or groups of practices. It is not uncommon to see dedicated change enablement (also known as change management) teams, release teams, deployment teams, and testing teams, sometimes combined into an umbrella department under a name such as service transition or similar. This approach provides the organization with dedicated resources shared across many products, services and technology domains. These teams sometimes evolve to centers of excellence which may become service providers focused on a particular area of service management, as described below. The most important requirement to such teams is to be able to effectively participate in the end-to-end value streams of the service provider and to understand all products, services, and technologies in scope well enough.

4.2.1.3 Deployment as a service
The purpose of a deployment as a service team is to enable and support value stream-aligned teams to deliver work independently. While the value stream-aligned team has end to end ownership of building, testing, deploying and running the service, the deployment as a service team provides internal services and specialized expertise with regards to practices, tooling and automation to reduce the workload for value stream aligned teams.

5. 
Information and technology
5.1 Information exchange
The effectiveness of the deployment management practice is dependent on the quality of the information used. This information includes, but is not limited to, information about:

authorized repositories of service components and assets, such as IT asset databases and DML
assets and configurations
change and release plans
deployment communications
deployment documentation and records
deployment plans
deployment metrics and reports
entry, exit, and acceptance criteria for each stage of deployment
feedback from deployment
issues and errors identified during deployment
platforms and environments within deployment’s scope
products and services and their architecture and design
requirements and expectations about changes and releases
stakeholder needs, expectations, and contact details.
This information may take various forms. The key inputs and outputs of the practice are listed in Chapter 3.

5.2 Automation and tooling
In most cases, the deployment management practice can significantly benefit from automation. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to the full automation of activities where technology solutions remove the need for human intervention. Deployments in Agile and DevOps environments are predominantly automation - and technology - oriented.

Where automation is possible and effective for deployment, it may involve the solutions outlined in Tables 5.1 and 5.2.

Table 5.1 Automation solutions for the deployment management activities
Automation tools

Application in deployment management

Work planning and prioritization tools

Activity planning
Scheduling deployments
Deployment tracking
Workflow management and collaboration tools

Record management
Integration in the value streams
Communication and collaboration between teams
Service configuration management tools

Compare the components on various parameters

Environment configuration and management tools

Check the target platform(s) against set of parameters and attributes

Deployment Tools

Deployment of the designated service components/releases to target environment(s) in a scheduled and controlled manner

CI/CD Tools

Automate development
Automate testing
Automate deployment
Table 5.2 Automation solutions for deployment management activities
Process activity

Means of automation

Key functionality

Impact on the effectiveness of the practice

Deployment model development and improvement

Deployment model planning

Workflow management and collaboration tools
CI/CD tools
Service configuration management tools
Definition, recording, review and approval of a deployment model components and steps

High

Deployment model implementation

Environment configuration and management tools
CI/CD tools
Service configuration tools
Deployment tools
Setup of the defined deployment model’s components and steps

High

Deployment model testing

Environment configuration and management tools
CI/CD tools
Service configuration tools
Deployment tools
Testing of the set up deployment model

High

Deployment review and deployment failure records analysis

Workflow management and collaboration tools
CI/CD tools
Service configuration management tools
Deployment tools
Environment configuration and management tools
Reporting of the deployment model performance
Communication and collaboration during the review
Medium to High

Deployment model improvement initiation

Workflow management and collaboration tools
CI/CD tools
Service configuration management tools
Recording and communication of the improvement initiatives for deployment models and other aspects of the practice

Medium to High

Deployment model update and communication

Workflow management and collaboration tools
CI/CD tools
Service configuration management tools
Update of the deployment models information for the relevant stakeholders

Medium to High

Deployment lifecycle management (partially automated)

Deployment planning

Work planning and prioritization tools
Workflow management and collaboration tools
Activity planning, scheduling, and tracking

High

Verification of the service components

Service configuration management tools
Deployment tools
Configuration verification by selected parameters and by pre-defined models

High

Verification of the target environment

Environment configuration and management tools
Service configuration tools
Verification of the target environment against set of parameters and attributes

High

Deployment execution

Deployment management tools

Deployment of the designated service components/releases to target environment(s) in a scheduled and controlled manner

High

Deployment verification

Service configuration tools
Deployment tools
Environment configuration and management tools
Verification of the deployment and deployed service components against defined acceptance criteria

High

Deployment lifecycle management (fully automated CI/CD toolchain)

Automated deployments to dev, test, staging, and production

Integrated CI/CD toolchains

Schedule/trigger-based, automated deployment of the required components to target environments at each stage

High

5.2.1 Recommendations for the automation of deployment management
The following recommendations can help when applying automation to deployment management:

Automate the end-to-end value stream Automation of the deployment lifecycles should be integrated into the value streams including release management, change enablement, and, where relevant, activities of other management practices. A lack of integration complicates the value streams and reduces their effectiveness and efficiency. Consider implementing a CI/CD toolchain to support the end-to-end flow from development to operations but maintain the end-to-end approach to other value streams as well.
Infrastructure as code  The adoption of digital infrastructure allows for the automation of deployment of infrastructure components using tools and methods similar to those used for the deployment of application software. This supports better integration of deployment in the value streams, faster deployment execution, and more effective control of the service components.

Utilize environment configuration and management tools Ensure that the scope of deployment models includes the verification and, if necessary, configuration of the target environments. Management of environments should include version control; ensure integration with service configuration and asset management data.

Ensure effective integration with validation and testing Although service validation and testing is a different practice, in highly automated environments deployment and testing are closely integrated. Ensure that all steps of deployment models include relevant validation and testing.
6. 
Partners and suppliers
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the ITIL practices for service design, architecture management, and supplier management.

It is important to understand how the organization depends on third-party components and how it aims to establish effective and efficient collaboration with its key suppliers and partners around many activities, including those of the deployment management practice.

In an environment with multiple suppliers, it is important to understand the scope and boundaries of each organization’s deployment activities, and how these will interact. Most organizations have a process for deployment, which is often supported by standard tools and detailed procedures to ensure that software is deployed consistently. It is common to have different processes for different environments.

Many areas of the deployment management practice might be enabled by external resources, including people, tools, processes, and other capabilities.

The deployment management practice and its PSFs can be enabled and enhanced through selective and judicial sourcing in many forms, including those outlined in Table 6.1.

Table 6.1 Sourcing in the deployment management practice
Sourcing area

Details

People

Where deployment management activities are manual, resources could be sourced from a partner. Key considerations include the schedule of deployments, availability of internal resources, cost, and so on.

Technical/Non- technical skills and capabilities

Sourcing specific skills, including technical (about specific systems, technologies, platforms) and non-technical (planning, governing, and execution capabilities), are useful or even required in many deployment management activities. Key considerations include the variety and complexity of technical/service environments, dynamic technology environments, lack of appropriate internal resources, and so on.

Outsourced deployment management

In certain contexts, it may be necessary or useful to source the entire deployment management practice from a partner.

Tools and technologies for deployment

Several areas of the deployment management practice can be enhanced through the adoption of tools and technologies. Except in minor cases, these technologies, tools, and tool-chains are sourced from specific product/service providers.

Partners and suppliers may support the development, management, and execution of the deployment management practice. The forms of support include the following:

Performing the deployment management activities Some deployment management activities can be largely or completely performed by a specialized supplier. Third parties may get involved in deployment and the automation of deployment management activities. It is important to ensure effective integration of the third parties in the deployment, release management and software development management workflows and information exchange, as well as their adherence/compliance to relevant policies.

Deployment strategy, practices and value streams should define how third parties are involved in deployment management and how the organization ensures effective collaboration. Once the end-to-end value stream is defined considering deployment management and key interfacing practices such as release management, service validation and testing and software development and management, further consideration of third-party dependencies is needed during building, testing and deployment activities.

Defined standard interfaces may become an easy way to communicate the necessary conditions and requirements for a supplier to become a part of the organization's ecosystem. Such interface description may include rules of data exchange, tools, and processes that will create a common language, practice and value streams in the multi-vendor environment.
Where organizations aim to ensure faster and more effective delivery of hardware and software in the live environments, they usually try to agree close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision-making (see the supplier management practice guide for more information).
Provision of software tools Most software tools used for deployment management such as software configuration management, continuous testing, continuous delivery and continuous deployment tools are shared with other practices such as release management. However, the implementation and use of integrated CI/CD pipeline often starts with automating coding, building, testing and deployment activities. In this case, the stakeholders of the deployment management practice and the managers of the teams involved in release management, service validation testing and software deployment management should define requirements and interact with other teams and practices of the service provider to ensure that the required tools are procured, implemented, and used in an optimal way.
Consulting and advisory Specialized suppliers who have developed expertise in deployment management with capabilities in agile and DEVOPS practices and technologies can help establish and develop practices, adopt methods, deploy tools and techniques in automating the CI/CD pipeline along with relevant deployment management activities.
7. 
Capability assessment and development
7. 1 The practice capability levels
The practice success factors described in section 2.4 cannot be developed overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:

Level 1 The practice is not well organized; it’s performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

Level 2 The practice systematically achieves its purpose through a basic set of activities supported by specialized resources.

Level 3 The practice is well defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

Level 4 The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

Level 5 The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level 2 to level 5. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to the practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well defined and organized.

Figure 7.1 Design of the capability criteria
This approach results in every practice having up to 30 capability criteria based on the practice PSFs and mapped to the four dimensions of service management. The number of criteria at each level differs; the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

Table 7.1 outlines the capability criteria that are defined in the ITIL maturity model for the deployment

management practice.

Table 7.1 Deployment management capability criteria
PSF

Criterion

Dimension

Capability level

Establishing and maintaining effective approaches to the deployment of services and service components across the organization

An approach to deployment is defined and agreed for the organization

Value streams and processes

3

Responsibility for the approach to deployment is clearly defined

Value streams and processes

3

The deployment approach is integrated with other standards and approaches adopted by the organization

Value streams and processes

4

The effectiveness of the deployment approach is monitored and evaluated

Value streams and processes

4

The deployment approach is regularly reviewed and continually improved

Value streams and processes

5

Ensuring the effective deployment of services and service components in the context of the organization’s value streams

New and changed services and service components are successfully deployed in the target environments

Value streams and processes

2

Deployment is automated where reasonably possible

Information and technology

3

Deployment information is tracked and managed in an integrated information system

Information and technology

3

Deployment includes required competencies and human resources

Organizations and people

3

Deployment includes dependencies and relationships with third parties where appropriate

Partners and suppliers

3

Deployment includes required workflows and procedures where appropriate

Value streams and processes

3

Deployment includes required technologies and information flows

Information and technology

3

Deployment is effectively integrated in the organization’s value streams

Value streams and processes

4

Deployment models, plans, and scenarios are regularly reviewed and continually improved

Value streams and processes

5

These capability criteria can be used by organizations for self-assessment and improvement of the practice.

7.2 Capability self-assessment
A self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team in the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed.

Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider’s employees.
If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met; what is missing in the organization? Why? How can it affect the service consumer and the quality of the IT services? What can be done to meet the criteria that are currently missed?
The same approach is applied at every next level; the practice is considered to be at the level, where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.
7.3 Deployment management capability development
Management practices should support the achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at the capability level 5. A higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but it comes with a cost; cost of management, automation, and training, for example. To achieve optimal performance with sufficient level of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and Table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

Figure 7.2 The capability development steps and levels
Table 7.2 The deployment management capability development steps
Capability level

Define, agree, and implement

Comment for deployment management

Chapter (for recommendations)

2

Purpose and objectives

Key stakeholders, objectives

2.1

Scope

2.3

Processes and activities

Deployment models, workflows, roles and responsibilities
Automation and information exchange
3

Roles and responsibilities

4

Tools and procedures

5

3

Dependencies and integration

Integration with other practices in the context of service value streams

3.2

Use of an integrated information system

5

Suppliers and other parties involved in deployment management

6

4

Measurement and reporting

Metrics

2.5

5

Continual improvement

Regular review of practice and the deployment management capability development

2.4, 2.5, 7

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
In Table 8.1, recommendations for the success of the deployment management practice are linked to the relevant guiding principles.

Table 8.1 Recommendations for the success of deployment management
Recommendations

Comments

ITIL guiding principles

Automate the deployment pipeline for faster delivery and reduced errors

Automate release, service validation and testing and deployment management activities with the objective of delivering value faster. Remove manual steps in the CI/CD pipeline by identifying bottlenecks.

Focus on value
Optimize and automate
Start where you are
Integrate build, test, and deployment activities

CI/CD integration results in shortening the lead time to deliver services or features to the live environment, and enables enhanced collaboration between development, testing and deployment teams.

Collaborate and promote visibility
Optimize and automate
Think and work holistically
Continuous phased deployment with integrated testing

Focus on incremental deployment to manage deployments and scale accordingly.

Progress iteratively with feedback
Keep it simple and practical
Leverage Infrastructure as Code

Infrastructure as Code provides multiple benefits such as reducing costs, offering more scalability, and enhancing security. It provides automated process of installing and configuring software that enable reliable releases.

Optimize and automate
Collaborate and promote visibility
Demonstrate business value

Measure the practice and produce regular reports and dashboards for internal (within the service provider) and external (service consumer) stakeholders. Use dashboards for the reporting and regular reports for analysis and highlights.

Focus on value
Collaborate and promote visibility
9. 
Acknowledgements
PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following:

Authors
Vinod Kumar Agrasala, Roman Jouravlev, Konstantin Naryzhny.

Reviewers
Jon Hall, Anton Lykov, Samantha Robertson, Oleg Skrynnik.

2023 Revision
Antonina Douannes, Adam Griffith, Roman Jouravlev, Kaimar Karu, Olga Masalina, Avinash Singh

