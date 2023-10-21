---
title: "Release management: ITIL 4 Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---


## 1. About this guide

This guide provides practical guidance for the release management practice. It is split into seven main sections, covering:

*   general information about the practice
*   the practice’s processes and activities and their roles in the service value chain
*   the organizations and people involved in the practice
*   the information and technology supporting the practice
*   considerations for partners and suppliers for the practice

#### 1.1 ITIL 4 qualification scheme

Selected content of this document is examinable as a part of the following syllabuses:

*   **ITIL Specialist** Create, Deliver and Support
*   **ITIL Specialist** High-Velocity IT
*   **ITIL Practitioner** Release Management
*   **ITIL Specialist** Plan, Implement and Control

Please refer to the relevant syllabus documents for details.

## 2. General information

#### 2.1 Purpose and description

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>The purpose of the release management practice is to make new and changed services and features available for use.</p></td></tr></tbody></table>

The release management practice ensures that services are available to use in line with organization’s policies and agreements between the organization and its service consumers.

It should be noted that the term ‘release’ is often used to describe transfer of a new or changed set of components from a development team to a service operations team. In ITIL terms, this transfer is a form of deployment. The term ‘release’ is reserved for making the new and changed services and features available for use. See sections 2.2.1 and 3.2.2 for more information.

Traditionally, service components are visible and accessible for users including infrastructure, software, and documentation. As infrastructure and documentation are increasingly digitized, software management methods and approaches become more applicable to these types of service components. This affects the release management practice and other practices with significant focus on changes in IT resources, such as change enablement, service validation and testing, deployment management, software development and management, and infrastructure and platform management.

From the customer and user journey perspective, release management supports onboarding and offboarding. For users, this practice may support the very first touchpoints and interactions with the service provider. After initial onboarding is complete, this practice supports the delivery of service updates, which is important for the success of service delivery and consumption.

The release management practice is beneficial for both IT service providers and their service consumers.

Benefits for the service provider include:

*   Controlled enablement of new and changed services for users
*   Ability to experiment and test hypotheses with different user groups
    
*   Reduced risks and losses resulting from releases
    
*   Better image due to smooth and timely release of IT services
    
*   Higher user and customer satisfaction.
    

Benefits for the service consumer include:

*   Controlled enablement of new and changed business services for users
*   Reduced risks and losses resulting from releases
    
*   Better image due smooth and timely release of business services
    
*   Higher client and employee satisfaction.
    

#### 2.2 Terms and concepts

##### 2.2.1 Release management and deployment management

<table><tbody><tr><td><p><strong>Release</strong></p></td></tr><tr><td><p>A version of a service or any other configuration item, or a collection of configuration items, that is made available for use.</p></td></tr></tbody></table>

Organizations should define a high-level approach to release and deployment management practices and their role in organization’s value streams and service relationships.

One approach is to combine release and deployment to the live environment. Once moved to the live environment, service components become available to users. Co-existence of different versions of one component in live environment is rare and does not last long. In this approach, there may be no clear distinction between deployment to live environment and release activities (and steps of a product and service lifecycle), especially if enabling the released version for use does not require any additional user training. This approach is typically applied to hardware service components and large monolithic software systems.

Another approach is more common to digital products and environments. In this approach, new versions of software can be deployed to the live environment before release activities start, and then released to all or some of the users. In this case, release management activities focus on enabling the use of the service and can be very simple and technical or complex and human-focused. For example, release can be as simple as changing the application’s status in a repository so that it is available for download by a selected audience. A more complex example can include a user communication and training aiming to reduce risks and increase effectiveness of the version changes.

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>CI/CD and release management</p><p>The key concepts for deployment in Agile and DevOps are continuous integration, continuous delivery, and continuous deployment. These can be defined as:</p><ul><li>Continuous integration usually refers to integrating, building, and testing codes within the software development environment.</li></ul><ul><li>Continuous delivery extends this integration, covering the final stages for production deployment. Continuous delivery means that built software can be released to production at any time.</li></ul><ul><li>Continuous deployment refers to the changes that go through the process and are automatically put into production. This enables multiple production deployments a day. Continuous delivery means that frequent deployments are possible, but deployment decisions are taken case by case, usually due to businesses preferring a slower rate of deployment. Continuous deployment requires that continuous delivery is in place.</li></ul><ul><li>In organizations using continuous deployment, release management as a separate practice is common and effective. New software versions, documents, and digital infrastructure are deployed to live environments as soon as they are ready, and then release management practice is used to ‘switch them on’ for users.</li></ul><ul><li>If continuous delivery is used without continuous deployment, deployment to live environment and release for users may be synchronized and managed as a single step in respective value streams.</li></ul><ul><li>Similarly, if an organization uses neither continuous delivery nor continuous deployment, release management activities are likely to be combined with deployment to the live environment.<span></span></li></ul></td></tr></tbody></table>

  
Organizations can define the approach for release and deployment management practices for all products and services, or per product. This usually depends on the organization’s product architecture (and its consistency across products), and on the organization’s approaches to management of software lifecycle.

##### 2.2.2 Release management approaches, models, and plans

If an organization manages products of different architectures, it is likely that several approaches for release management will be defined. A product-specific release management model can be agreed for a specific product.

<table><tbody><tr><td><p><strong>Definition: Release model</strong></p></td></tr><tr><td><p>A repeatable approach to the management of particular types of releases.</p></td></tr></tbody></table>

This model includes, but is not limited to:  

*   agreed high-level approach
*   target user audience of releases and rules for user enablement
*   push/pull conditions
*   verification and acceptance criteria
*   terms and conditions of release usage for hypothesis verification and experimentation.

It is possible to have more than one release management model for a product. For example, when a product is used to provide services on different markets or to business and individual service consumers.

One of the factors that usually affects the development of the release management model and the practice, is the organization’s scope of control of the product. When the organization controls full product lifecycle, including development, testing and deployment, it has more freedom in defining release management models. In contrast, if the organization’s services are based on third-party components, or the development and deployment are managed by a supplier, it usually introduces constraints that the organization should consider. It still may be able to decide whether to include updated components in its services, but only to a certain extent (for example, until the components’ vendor allows the organization to keep using the previous versions).

##### 2.2.3 Push/pull considerations

One of the decisions made during the development of the release management model is whether new versions of service components will be pushed to users, pulled by users, or there will be a mix of the approaches.

A ‘push’ approach implies that new or changed components of services are enabled for users without their specific consent(or the users consent to the updates by continuing to use the service), and users are obliged to use these versions. In contrast, the ‘pull’ approach makes new components and services available to users, but users can decide whether they prefer using these new versions, stick to older ones, or not using the service at all.

Typically, organizations do not apply a single approach; they define conditions where the ‘pull’ or ‘push’ approach would work better. Considerations are common for internal and external service providers include:

*   the benefits of having a single version across the user base (maintainability, compatibility)
*   the benefits of allowing users to have more freedom (better image, flexible pricing options)
*   technical and organizational ability to manage multiple versions in a live environment
*   emergency changes (an update addressing a critical security vulnerability is likely to be ‘pushed’)
*   functional and other customer’s requirements (if a required new functionality is implemented, customers may mandate the update for all users)
*   regulatory requirements.

##### 2.2.4 Hypothesis testing and experimentation

Release management may be used to validate a hypothesis and to experiment. When an organization needs to test a hypothesis with a sample user audience, new or updated services may be released to sample user groups (sometimes called treatment groups). This approach is widely used by providers of mass services, such as social networks, but also applied to small user groups. Related techniques include blue/green releases, canary releases, and A/B testing.

These experiments require the involvement of other practices. This includes, but not limited to:

*   infrastructure and platform management
*   software development and management
*   service validation and testing
*   deployment management
*   architecture management
*   service desk
*   incident management.

#### 2.3 Scope

The scope of the release management practice includes the following:

*   Development and maintenance of the organization’s approach to release new and changed services[1](https://my.axelos.com/resource-hub/practice/release-management-itil-4-practice-guide#_bookmark0) and components.
*   Management and coordination of all release instances in line with the defined approach, from planning, to implementation, and review.

1 Removal of services and components from users is included in ‘new and changed’ here.

There are a number of activities and areas of responsibility that are closely associated with release management, but not part of the scope of the practice.

Some of those key areas are listed in Table 2.1, and includes references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams, and they should be combined as necessary depending on the situation.

##### Table 2.1 Release related activities described in other practice guides

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Authorization of changes/releases</p></td><td><p>Change enablement</p></td></tr><tr><td><p>Deployment of new and changed components and services in live environment</p></td><td><p>Deployment management</p></td></tr><tr><td><p>Development of software</p></td><td><p>Software development and management</p></td></tr><tr><td><p>Development and building of infrastructure components</p></td><td><p>Infrastructure and platform management</p></td></tr><tr><td><ul><li>User training</li><li>Support and operational staff training</li></ul></td><td><p>Workforce and talent management</p></td></tr><tr><td><p>Testing and validating the services and service components</p></td><td><p>Service validation and testing</p></td></tr><tr><td><p>Naming, versioning and control of the service components</p></td><td><p>Service configuration management</p></td></tr><tr><td><p>Management of organizational changes related to large-scale releases</p></td><td><p>Organizational change management</p></td></tr><tr><td><p>Management of projects</p></td><td><p>Project management</p></td></tr></tbody></table>

#### 2.4 Practice success factors

<table><tbody><tr><td><p><strong>Definition: Practice success factor</strong></p></td></tr><tr><td><p>A practice success factor (PSF) is a complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The release management practice includes the following PSFs:

*   establishing and maintaining effective approaches to the release of services and service components across the organization
*   ensuring an effective release of services and service components in the context of the organization’s value streams and service relationships.

##### 2.4.1 Establishing and maintaining effective approaches to the release of services and service components across the organization

The release management practice includes defining and agreeing approaches and models to follow for the release of new and changed services and service components. Organizations are likely to combine several approaches and to define several release management models for every product they manage.

Apart from organization’s and product’s characteristics, release models are defined by service relationships between the organization and its service consumers. This includes factors such as:

*   internal or external service consumers
*   individual or corporate service consumption
*   out-of-the-box or tailored services

See *ITIL® 4: Drive Stakeholder Value* for more details on how these factors influence service provision.

The approaches and models for release management should have enough flexibility to adapt to changing circumstances, such as scale, urgency, or complexity. A plan for every release instance may be developed based on one of the agreed models to reflect the specifics of the release instance.

Release approaches, models, and the practice in general, should be subject to continual improvement, constantly looking for ways to eliminate waste and increase effectiveness and efficiency.

##### 2.4.2 Ensuring an effective release of services and service components in the context of the organization’s value streams and service relationships

Ensuring an effective release may require organizing resources in all four dimensions of service management.

Depending on the release management model, activities and resources that are required to implement a release instance, vary significantly:

*   A release of a new version of mobile application for all users in a certain country or region may be performed by changing the status of the previously deployed version of the software, related release notes, and user documentation. Relevant stakeholders within the service provider organization. No further actions may be required.
*   A release of a new custom-made ERP system with on premises installation and a need for user equipment upgrade may be managed as a large-scale project, involving many teams and practices across and from outside of the organization.

In any case, effective coordination, use of automation, and good planning of the release model from the early steps of product lifecycle are crucial for the success of release.

This practice is focused on identifying the tasks and coordinating the participants. It also provides recommendations on procedures and techniques to use during release implementation. Therefore, an effective combination of practices and cooperation from teams is necessary during the implementation.

Effective coordination of software development and management, infrastructure and platform management, deployment management, service validation and testing, and release management is especially important. This coordination is usually within the scope of the change enablement practice.

#### 2.5 Key metrics

The ITIL practices are means or tools for the management of products and services. Like the performance of any tool, practice performance can be assessed only in the context of that tool’s application. However, tools can differ in quality. This difference defines the tool’s potential or capability to be effective when used according to their purpose.

The same applies to practices: their performance should be assessed in the context of value streams, but their potential is defined by their design and the quality of the resources. Further guidance on metrics, KPIs, and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the release management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the monitoring and event management practice to the effectiveness and efficiency of those value streams. The key metrics are listed in Table 2.2.

##### Table 2.2 Example of key metrics for the practice success factors

<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Establishing and maintaining effective approaches to the release of services and service components across the organization</p></td><td><ul><li>Stakeholders’ satisfaction with the way new and changed services are introduced to users</li><li>Adoption of the agreed approach to release management across the organization</li><li>Key partners and service consumers’ alignment with release management approaches and models</li><li>Audit findings and external compliance issues caused by releases</li></ul></td></tr><tr><td><p>Ensuring an effective release of the services and service components in the context of the organization’s value streams and service relationships</p></td><td><ul><li>Stakeholders’ satisfaction with release instances</li><li>Percentage of successful release instances/number of release errors/failures</li><li>Number and percentage of incidents related to release</li><li>Timeliness/adherence to release schedule</li><li>Release backlog throughput</li></ul></td></tr></tbody></table>

The correct selection and aggregation/segregation of metrics into composite/hierarchical indicators will make it easier to use them for the ongoing management of value streams and for the periodic assessment and continual improvement of the deployment management practice. There is no single best solution; metrics will be based on the overall context, service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

## 3. Value streams and processes

#### 3.1 Value stream contribution

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><p><strong>Definition: Process</strong></p></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

Release management activities form two processes:

*   **Release model development and improvement** This process is focused on the continual improvement of the release management practice, release approaches, and models.
*   **Release planning and coordination** This process is focused on managing the lifecycle of individual releases.

##### 3.1.1 Release model development and improvement

This process is focused on the continual improvement of the release management practice, release approaches, and models. It is performed regularly but can also be triggered by events or requests. Regular reviews may take place every two to three months or more frequently, depending on the effectiveness of the existing models and procedures. Inputs, activities and outputs of the release model development and improvement process are represented in Table 3.1.

##### Table 3.1 Inputs, activities, and outputs of the release planning process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Current release management approaches and models</li><li>Release records</li><li>Release review reports</li><li>Policies and regulatory requirements</li><li>Product architecture</li><li>Service catalogue</li><li>Service level agreements</li><li>Incident records and reports</li><li>IT asset information</li><li>Agreements and contracts with suppliers and partners</li><li>Relevant policies and plans (information security, continuity, capacity, and so on)</li></ul></td><td><ul><li>Product architecture and service relationship analysis</li></ul><ul><li>Release management approach review and development</li><li>Release model review and development</li><li>Release model communication</li></ul></td><td><ul><li>Updated release management approaches and models</li><li>Release plans</li><li>Release schedule</li><li>Improvement initiatives</li><li>Change requests</li><li>Updated knowledge management articles</li><li>Lessons learnt</li></ul></td></tr></tbody></table>

Figure 3.1 shows a workflow diagram of the process.

![](Release%20management%20ITIL%204%20Practice%20Guide/Release_management_Fig3_1.jpg)

Figure 3.1 Workflow of the release model development and improvement process

Table 3.2 provides a description of the process activities.

#### Table 3.2 Activities of the release model development and improvement process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Product architecture and service relationship analysis</p></td><td><p>The release manager, together with product/service owners, architects, and other teams, analyse and discuss new or changed conditions affecting release approaches:</p><ul><li>preferred approach to the creation/modification of a group of products and services</li><li>nature of the group products or services</li></ul><ul><li>the organization’s architecture approaches and decisions</li><li>main release audiences and relationship with them, existing service level agreements</li><li>the organization’s risk management approach and risk appetite</li></ul><ul><li>compliance, policies and technology opportunities and constraints that are present</li><li>market position and financial&nbsp;conditions</li></ul></td></tr><tr><td><p>Release management approach review and development</p></td><td><p>The team discusses the new release approach or changes to the existing release approach and agree on the approach. Release approach is developed or updated.</p></td></tr><tr><td><p>Release management model review and development</p></td><td><p>Based on the new or changed approach, the release models are defined or updated. The models may include:</p><ul><li>release procedures</li><li>release authorities</li><li>release plan template</li><li>schedules templates</li><li>communications plan template.</li></ul></td></tr><tr><td><p>Release model communication</p></td><td><p>The new or updated release models are communicated to the relevant parties.</p></td></tr></tbody></table>

#### 3.1.2 Release planning and coordination

This process is focussed on managing the lifecycle of individual releases. The process includes the inputs, activities, and outputs shown in Table 3.3.

#### **Table 3.3 Inputs, activities, and outputs of the release planning and coordination process**

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Release management models</li><li>Change schedule</li><li>Environment details</li><li>Service component/release components deployed to live environment or prepared for deployment</li><li>Acceptance and verification criteria</li></ul></td><td><ul><li>Identification of applicable model or plan</li><li>Release instance planning</li><li>Verification of the service components</li><li>Verification of the release procedures</li><li>Release execution</li><li>Release verification</li><li>Release review</li></ul></td><td><ul><li>R<span>eleased service components/services</span></li><li>Release records</li><li>Release communications</li><li>Feedback from users, customers, and involved team members</li><li>Release review report</li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![](Release%20management%20ITIL%204%20Practice%20Guide/ITIL_4_Release_management_3_2_EN.jpg)

Figure 3.2 A workflow diagram of the release planning and coordination process

Table 3.4 describes the release planning and coordination process activities.

#### Table 3.4 Activities of the release planning and coordination process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Automated release of a software component</strong></p></td><td><p><strong>Complex release project</strong></p></td></tr><tr><td><p>Identification of applicable model or plan</p></td><td><p>A release pipeline is organized, so that the release model or plan is detected automatically based on the product or service, target environment, or development team.</p></td><td><p>A product/service owner, together with the deployment and operations teams, identifies an appropriate release model to use based on the product, market, scope of the released changes and the value stream context (purpose and urgency of the release).</p></td></tr><tr><td><p>Release instance planning</p></td><td><p>The release instance components, activities, and schedule are automatically defined based on the release model.</p></td><td><p>The release manager assigned according to the identified release model, together with product/ service owner, confirms the release instance components and activities suggested by the release model and schedule the activities aligning the release instance with other releases in the change schedule and taking the business context into consideration.</p></td></tr><tr><td><p>Verification of the service components</p></td><td><p>The release instance components run pre-defined component tests.</p></td><td><ul><li>Based on the release model, component verification is performed by the release manager or assigned specialists.</li><li>Verification may trigger additional building, deployment, or testing, if some of the components are not ready for the release.</li></ul></td></tr><tr><td><p>Verification of the release procedures</p></td><td><p>Release procedure is chosen automatically based on the component attributes.</p></td><td><p>The release procedures for the chosen model are verified for the release instance. Release execution may start only when all requirements of the selected release model are met (all required resources are available and procedures are ready to run)</p></td></tr><tr><td><p>Release execution</p></td><td><p>The release is executed according to predefined script and affected user groups are informed automatically.</p></td><td><p>The release procedures are executed according to the agreed model and plan.</p></td></tr><tr><td><p>Release verification</p></td><td><p>An automated script verifies that all features/components were released.</p></td><td><p>The release teams and dedicated users check that all planned features/components were released and procedures were successfully performed, including training and communications, where applicable.</p></td></tr><tr><td><p>Release review</p></td><td><ul><li>Any exceptions and logs of the automated release process are analysed by the product team.</li><li>The product team runs a post-mortem, updates the knowledge base, and records any lessons learnt.</li></ul></td><td><ul><li>Feedback is gathered from the user groups.</li><li>The release team reviews the release records and results, updates the knowledge base and records any lessons learnt. The resulting release review report may trigger the release model planning and improvement process.</li></ul></td></tr></tbody></table>

#### 3.2 Value stream contribution

##### 3.2.1 Service value streams

To perform certain tasks or respond to particular situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario. Once designed, value streams should be subject to continual improvement.

<table><tbody><tr><td><p><strong>Definition: Value stream</strong></p></td></tr><tr><td><p>A series of steps an organization undertakes to create and deliver products and services to consumers.</p></td></tr></tbody></table>

In practice, however, many organizations come to use of the value stream concept after having worked for a while, sometimes for years, without the value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the current situation, and the typical flows of work, and to analyse them in order to identify and eliminate waste.

Identifying and understanding the existing value streams is critical to improving an organization’s performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services. Combined, organizations’ value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations have been following best practice recommendations for various service management practices, such as incident management, change enablement, software development, and many others. Incident management is one of the most adopted and mature practices; organizations often start their ITSM journey with incident management.

However, the practices have often been adopted and organized in a siloed, isolated manner, just as they were presented in the service management bodies of knowledge. In reality, a flow of work required to create or restore value, for a customer or another stakeholder, is almost never limited to one practice.

##### 3.2.2 Release management in service value streams

Release management contributes to implementation of changes initiated by a range of sources. The practice plays an important role in service value streams involving changes. These are outlined in Table 3.5.

Table 3.5 Role of the release management practice in service value streams

<table><tbody><tr><td><p><strong>Service value stream</strong></p></td><td><p><strong>Role of the release management practice</strong></p></td></tr><tr><td><p>Incident resolution</p></td><td><p>Release of the fixed components, patches, updated versions of software, and other changes executed to solve an incident and restore normal service operations</p></td></tr><tr><td><p>Request fulfilment</p></td><td><p>Release of changed or new components and versions required to fulfil a request model</p></td></tr><tr><td><p>Product and service continual improvement</p></td><td><p>Release of fixed components, patches, updated versions of software, and other changes executed to realize an approved improvement initiative</p></td></tr><tr><td><p>Delivery of new and changed services</p></td><td><p>Release of fixed components, patches, updated versions of software, and other changes executed to fulfil an agreed product or service development plan</p></td></tr><tr><td><p>Ongoing operations and maintenance</p></td><td><p>Release of changed or new components and versions required to fulfil an agreed maintenance of the live systems and components.</p></td></tr></tbody></table>

In all cases, the release is a part of a change implementation and should be coordinated with other activities in the change lifecycle, such as purchasing, configuring, testing, and deployment. Releases are within the scope of the change lifecycle management process (see the change enablement practice guide). The change enablement practice ensures the correct selection of a relevant change model, which in turn suggests a relevant release model; scheduling of the release phase of the change implementation; and acceptance of the release results. At the same time, the release management practice ensures that valid release models are available and correctly executed when required according to the change plan and change schedule. Figure 3.3 illustrates the positioning of the release planning and coordination process in the various value streams involving changes.

![](Release%20management%20ITIL%204%20Practice%20Guide/Release_management_Fig3_3.jpg)

Figure 3.3 Deployment to live environment, component verification, and release planning and coordination in service value streams

It is important to ensure the effective integration of the release management practice in the management of change lifecycles and further in the service value streams. Depending on the business context of the changes, a release may be assigned different levels of urgency and impact, which should be possible to address with the application of a relevant release model.

#### 3.2.3 Analysing a service value stream

##### 3.2.3.1 The key steps of a service value stream analysis

The following are some simple and practical recommendations for service value stream analysis and mapping.

**Identify the scope of the value stream analysis**

It can be mapped to a particular product or service or applied to most or all of them. Similarly, service value streams may differ for different consumers; for example, releases are performed and communicated differently for internal and external customers, or for B2B and B2C products, or for services based on products developed inhouse or sourced externally.

**Define the purpose of the value stream from the business standpoint**

Make sure the stakeholder’s concerns are clearly understood, since they are the ones defining value. In the case of release management, the key groups of stakeholders are users and customers on the service consumer side and product or service owners on the service provider side. However, there are usually other interested parties, depending on the service value stream. For example, if a release is required to respond to a changed business requirement, the stakeholders would be different from those of a release aiming to resolve an incident.

**Do the service value stream walk**

Walk through or directly experience the steps and information flow as they go in practice (consider the Lean technique of Gemba walk):

**a. Identify the workflow steps**

**b. Collect data as you walk**

**c. Evaluate the workflow steps**

Typically, the criteria for evaluation are:

*   value for the stakeholder (does the step add value for the business stakeholder?)
*   effectiveness or performance (is the step performed well?)
*   availability (are required resources available to execute the step?)
*   capacity (are the required resources enough?)
*   flexibility (are the required resources interchangeable within the step?).

**d. Map the activities and the information flows**

In an ideal situation, the flow goes smoothly without delays and pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

**e. Create and review the timeline and resource level**

Map out process times and lead times for resources and workload through the workflow steps.

**4\. Reflect on the value stream map (VSM)**

Identify factors that might not have been entirely apparent at first. The information collected is used at this step to find the waste.

**5\. Create a 'to be' VSM**

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

**6\. Using the 'to be' VSM, plan improvements**

Refer to the continual improvement practice guide for a practical improvement model.

###### 3.2.3.2 Release management considerations in a service value stream analysis

To ensure that relevant release management activities are included in service value streams, the following steps can be added to the above recommendations.

*   At the scoping step (1), identify the IT and business services related to the value stream and the involved business stakeholders. This depends on the value stream purpose and context. See Table 3.5 for examples.
*   Make sure the value stream is understood (step 2) from the standpoint of the business, not only from the standpoint of the service provider.
*   During the service value stream walk (3a), identify other practices assisting in release management at every step. Which practices provide required information (service configuration data, asset data, change schedules, and so on)? What if release execution involves third parties?
*   During the workflow steps evaluation (3c), evaluate the step’s impact on the value creation or restoration. Special attention should be paid to steps with low business value, low performance, and availability or capacity issues. It is not unusual to find steps which serve some internal control or bureaucratic purposes but delay the change implementation.
*   At the reflection and planning steps (4-5), ensure that the release management flow is optimized for business value throughout the stream, not only at the release management practice activities.
*   Include the creating or updating of release models (see section 3.1.1) in the value stream improvement plans (step 6).

## 4. Organizations and people

### 4.1 Roles, competency and responsibilities

The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. The practice guides focus on specialist roles specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competence profile based on the model shown in Table 4.1.

#### **Table 4.1 Competency codes and profiles**

<table><tbody><tr><td><p><strong>Competence code</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p><strong>L</strong></p></td><td><p>Leader Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p><strong>А</strong></p></td><td><p><u>Administrator</u> Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p><strong>C</strong></p></td><td><p><u>Coordinator/communicator</u> Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p><strong>М</strong></p></td><td><p><u>Methods and techniques expert</u> Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p><strong>Т</strong></p></td><td><p><u>Technical expert</u> Providing technical (IT or other subject matter) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

There is one practice-specific role in release management that may be found in the organizations: release manager. This role is often introduced in organizations where there is a significant volume of releases, especially if they need manual planning and execution. In other organizations, the responsibilities of a release manager may be taken by product or service owners.

##### 4.1.1 Release manager role

Where a release manager role is defined, it is usually assigned to specialists that have strong knowledge of the organization’s business, products and services, technology, platforms, frameworks, and processes. The role will require strong planning and project management skills, ability, and authority to coordinate teamwork.

The competence profile for this role is CTMA. This role is usually responsible for planning, managing, and coordinating release management as a practice as well as individual release instances, including:

*   reviewing and developing the release approaches and models
*   promoting the adoption of the agreed release management approaches and models across the organization
*   planning complex releases
*   managing and communicating the release schedule
*   ensuring the practice is aligned and coordinated with other practices
*   reviewing and continually developing the practice.

In some complex organizations, part of the release manager’s responsibilities may be delegated to the role of release coordinators.

##### 4.1.2 Roles involved in the release management activities

Examples of other roles which can be involved in the release management activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

#### Table 4.2 Example of roles involved in release management activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Responsible roles</strong></p></td><td><p><strong>Competency profile</strong></p></td><td><p><strong>Specific skills</strong></p></td></tr><tr><td colspan="4"><p><em>Release model development and improvement</em></p></td></tr><tr><td><p>Product architecture and service relationship analysis</p></td><td><ul><li>Release manager</li><li>Service owner</li><li>Product owner</li><li>Development team member</li></ul></td><td><p>TCA</p></td><td><ul><li>Knowledge of service relationship Business analysis</li><li>Knowledge of service architecture</li><li>Knowledge of release and deployment approaches and models</li><li>Good knowledge of the organization’s products and services</li><li><p>Communication skills</p></li></ul></td></tr><tr><td><p>Release management approach <span>review and development</span></p></td><td><ul><li>Service owner</li><li>Product owner</li><li>Release manager</li><li>Development team member</li></ul></td><td><p>MTCA</p></td><td><ul><li>Good knowledge of service relationship</li><li>Knowledge of release and deployment methods</li><li>Good knowledge of the organization’s products and services</li><li>Communication skills</li></ul></td></tr><tr><td><p>Release model review and development</p></td><td><ul><li>Service owner</li><li>Product owner</li><li>Development team member</li><li>Release manager</li></ul></td><td><p>MTCA</p></td><td><ul><li>Knowledge of service relationship</li><li>Knowledge of release and deployment methods</li><li>Good knowledge of the organization’s products and services</li><li>Communication skills</li></ul></td></tr><tr><td><p>Release plan communication</p></td><td><ul><li>Service owner</li><li>Product owner</li><li>Release manager</li></ul></td><td><p>CA</p></td><td><ul><li>Knowledge of service relationship</li><li>Communication skills</li><li>Marketing knowledge</li></ul></td></tr><tr><td colspan="4"><p><em>Release planning and coordination process</em></p></td></tr><tr><td><p>Identification of applicable model</p></td><td><ul><li>Service owner</li><li>Product owner</li><li>Development team member</li><li>Release manager</li></ul></td><td><p>TM</p></td><td><ul><li>Knowledge of release models</li><li>Good knowledge of the organization’s products and services</li><li>Knowledge of the value stream context</li></ul></td></tr><tr><td><p>Release instance planning</p></td><td><ul><li>Release manager</li><li>Product owner</li><li>Service owner</li></ul></td><td>TMA</td><td><ul><li>Knowledge of release models</li><li>Good knowledge of the organization’s products and services</li><li>Knowledge of the value stream context</li></ul></td></tr><tr><td><p>Verification of the service components</p></td><td><ul><li>Release manager</li><li>Resource owner</li><li>Product owner</li><li>Service owner</li></ul></td><td><p>TA</p></td><td><ul><li>Knowledge of release models and plans</li><li>Good knowledge of the organization’s products and services</li><li>Knowledge of the value stream context</li><li>Technical knowledge of the service components</li></ul></td></tr><tr><td><p>Verification of the release procedures</p></td><td><ul><li>Release manager</li><li>Resource owner</li><li>Product owner</li><li>Service owner</li></ul></td><td><p>MTA</p></td><td><ul><li>Knowledge of release models and plans</li><li>Good knowledge of the organization’s products and services</li><li>Knowledge of the value stream context</li></ul></td></tr><tr><td><p>Release execution</p></td><td><ul><li>Resource owner</li><li>Systems administrator</li><li>Information security specialist</li></ul></td><td><p>T</p></td><td><ul><li>Technical knowledge of service/product</li><li>Knowledge of the value stream context</li><li>Knowledge of release models and plans</li></ul></td></tr><tr><td><p>Release verification</p></td><td><ul><li>Release manager</li><li>Resource owner</li><li>Product owner</li><li>Service owner</li></ul></td><td><p>AT</p></td><td><ul><li>Technical knowledge of service/product</li><li>Knowledge of the value stream context</li><li>Knowledge of release models and plans</li></ul></td></tr><tr><td><p>Release review</p></td><td><ul><li>Release manager</li><li>Product owner</li><li>Service owner</li></ul></td><td><p>MTA</p></td><td><ul><li>Knowledge of release models and plans</li><li>Good knowledge of the organization’s products and services</li><li>Knowledge of the value stream context</li></ul></td></tr></tbody></table>

#### 4.2 Organizational structures and teams

A designated release management team is typically found in large organizations with significant volumes and complexity of releases. In some cases, such teams tend to act in isolation, adopting a bureaucratic, siloed approach which may prevent effective integration of the practice into the service provider’s value streams.

Usually, release management does not need a dedicated team; either these activities are highly automated, or releases are managed by members of product teams, or a temporary project team is built for a large-scale complex release.

However, the role (and a dedicated job position) of a release manager may still be relevant in many cases. This role acts as a coach to ensure the practice is adopted across the organization. Depending on the organization’s approach to release management, this role may be combined with the role of change and/or deployment manager.

## 5. Information and technology

#### 5.1 Information exchange

The effectiveness of release management is dependent on the quality of information used. This information includes, but is not limited to, information about:

*   product architecture
*   service consumer organizations and users
*   software development and management practice
*   planned and ongoing deployments
*   ongoing and past incidents
*   emerging release management techniques.

This information may take various forms. The detailed list of inputs and outputs of the practice are listed in chapter 3.

#### 5.2 Automation and tooling

Release management in a digital environment is highly automated. But even in legacy environments the work of the release management practice can significantly benefit from automation. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to, the full automation of activities where technology solutions remove the need for human intervention. Where this is possible and effective, it may involve the solutions outlined in Tables 5.1 and 5.2.

##### Table 5.1 Automation solutions for release management activities

<table><tbody><tr><td><p><strong>Automation tools</strong></p></td><td><p><strong>Application in release management</strong></p></td></tr><tr><td><p>Workflow management and collaboration tools</p></td><td><ul><li>Management of release records</li><li>Support and automation of release models</li><li>Communications between specialists involved in release planning and coordination</li><li>Integration of practices into service value streams</li></ul></td></tr><tr><td><p>Enterprise architecture tools</p></td><td><p>Analysis of the product and service architecture</p></td></tr><tr><td><p>Monitoring and event management tools</p></td><td><p>Verification of releases</p></td></tr><tr><td><p>Work planning and prioritization tools</p></td><td><p>Release instance planning</p></td></tr><tr><td><p>Analysis and reporting tools</p></td><td><p>Analysis of the release records and reporting of the release models performance</p></td></tr><tr><td><p>Service configuration tools</p></td><td><ul><li>Release model development</li><li>Release instance planning</li><li>Verification of releases</li></ul></td></tr><tr><td><p>CI/CD toolchain</p></td><td><p>Automation of the release coordination activities and integration in the CI/CD pipeline</p></td></tr><tr><td><p>Deployment management tools</p></td><td><ul><li>Verification of components and procedures</li><li>Execution of the release models</li></ul></td></tr></tbody></table>

##### Table 5.2 Details of automation of the release management activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><p><strong>Key functionality</strong></p></td><td><p><strong>Impact on practice</strong></p></td></tr><tr><td colspan="4"><p><em>Release model development and improvement process</em></p></td></tr><tr><td><p>Product architecture and service relationship analysis</p></td><td><ul><li>Enterprise architecture tools</li><li>Workflow management and collaboration tools</li><li>Service configuration tools</li></ul></td><td><p>Visualization of the product/service architecture and relationships, connections, and constraints</p></td><td><p>Medium</p></td></tr><tr><td><p>Release management approach review and development</p></td><td><ul><li>Workflow management and collaboration tools</li><li>CI/CD toolchain</li></ul></td><td><p>Design and management of workflow models</p></td><td><p>Medium to High</p></td></tr><tr><td><p>Release model review and development</p></td><td><ul><li>Workflow management and collaboration tools</li><li>CI/CD toolchain</li></ul></td><td><p>Design and management of workflow models</p></td><td><p>Medium to High</p></td></tr><tr><td><p>Release model communication</p></td><td><p><span>Workflow management and collaboration tools</span></p></td><td><p>Automated communications, messaging, status updates</p></td><td><p>High</p></td></tr><tr><td colspan="4"><p><em>Release coordination process</em></p></td></tr><tr><td><p>Identification of applicable model or plan</p></td><td><ul><li>Workflow management and collaboration tools</li><li>CI/CD toolchain</li></ul></td><td><p>Design and management of workflow models</p></td><td><p>Medium</p></td></tr><tr><td><p>Release instance planning</p></td><td><ul><li>Workflow management and collaboration tools</li><li>CI/CD toolchain</li><li>Work planning and prioritization tools</li></ul></td><td><ul><li>Design and management of workflow models</li><li>Resource planning and work scheduling</li></ul></td><td><p>High</p></td></tr><tr><td><p>Verification of the service components</p></td><td><ul><li>Deployment management tools</li><li>CI/CD toolchain</li><li>Service configuration tools</li></ul></td><td><ul><li>Automated release coordination based on pre-planned, developed scripts</li><li>Configuration items verification</li></ul></td><td><p>High</p></td></tr><tr><td><p>Verification of the release procedures</p></td><td><ul><li>Deployment management tools</li><li>CI/CD toolchain</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Automated release coordination based on pre-planned, developed scripts</li><li>Design and management of workflow models</li></ul></td><td><p>High</p></td></tr><tr><td><p>Release execution</p></td><td><ul><li>Deployment management tools</li><li>CI/CD toolchain</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Automated release execution based on pre-planned, developed scripts</li><li>Coordination of multiple workflows and interdependencies</li></ul></td><td><p>High</p></td></tr><tr><td><p>Release verification</p></td><td><ul><li>Deployment management tools</li><li>CI/CD toolchain</li><li>Service configuration tools</li><li>Workflow management and collaboration tools</li><li>Monitoring and event management tools</li></ul></td><td><ul><li>Automated release verification based on pre-planned, developed scripts</li><li>Configuration items verification</li><li>Coordination of multiple workflows and interdependencies</li></ul></td><td><p>High</p></td></tr><tr><td><p>Release review</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Analysis and reporting tools</li></ul></td><td><ul><li>Generating and presenting reports based on the release records</li><li>Knowledge sharing</li><li>Analysis of the release models and plans performance</li></ul></td><td><p>Medium</p></td></tr></tbody></table>

##### 5.2.1 Recommendations for the automation of release management

The following recommendations can help when applying automation to release management:

*   **Automate the value stream** Automation of releases should be integrated into the value streams including deployment management, change enablement, service validation and testing, and, where relevant, activities of other management practices. Lack of integration complicates the value streams and reduces their effectiveness and efficiency. Consider implementing a CI/CD toolchain to support the end-to-end flow from development to operations but maintain the end-to-end approach to other value streams as well.
*   **Allow for a variety of release models** Do not try to squeeze all releases in one universal workflow. Ensure that the software tools support different release models and allow to plan a release instance based on a model.
*   **Automate release management for all product architectures used by the organization** Different models apply to products developed in-house, products developed for the organization by a third party, and products based on the off-the-shelf solutions. Make sure that release models relevant for these and other configurations are supported by the automation tools.
*   **Communication is important** Informing relevant people about planned, ongoing, and completed releases, both on the service consumer side and within the service provider, is a crucial part of release management. Relevant and proactive communication significantly helps to optimize resources and improve user and customer satisfaction.
*   **Ensure effective measurement and reporting from the beginning** In all value streams where release management is involved, release timeliness and effectiveness significantly affect the overall value stream performance. Make sure that the key metrics of the practice are captured and reported correctly and, wherever possible, automatically.

## 6. Partners and suppliers

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services. These are often provided by third parties outside the organization.

As previously mentioned, the role of partners and suppliers is connected to the level of control an organization has over its product and services, or their components. When an organization controls a full product or service lifecycle, including development and deployment, it has more freedom in making a full range of decisions about release management. In contrast, if an organization’s products or services are based on third-party components, or development and deployment are managed by a supplier, it usually introduces constraints that an organization must consider. It still may be able to decide whether to include updated components in its services, but only to a certain extent.

Partners and suppliers may contribute to the release management practice – usually, in the release planning and coordination process, and particularly in release execution. Examples include the setup and activation of service components, user training and other activities, especially involving release of physical infrastructure components in multiple and/or remote locations. The same partners and suppliers are likely to be involved in deployment activities.

For the products and services based on third-party solutions, vendors or suppliers can be involved in development and improvement of the release models. This contribution may be limited to the initial development of the release models or include participation in the regular reviews.

Apart from the product-specific competencies, third parties may assist service providers in development and improvement of the release management practice. This advice is often combined with wider scope of consulting on the change lifecycle management, CI/CD, product lifecycle management and automation of the related activities.

Naturally, consulting on automation of the practice may be combined with provision of the relevant tools, listed in section 5.2.

## 7. Capability assessment and development

#### 7.1 The practice capability levels

The practice success factors described in section 2.4 cannot be developed overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:

**Level 1** The practice is not well organized; it’s performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

**Level 2** The practice systematically achieves its purpose through a basic set of activities supported by specialized resources.

**Level 3** The practice is well defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

**Level 4** The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

**Level 5** The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level two to level five. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to the practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well-defined and organized.

![](Release%20management%20ITIL%204%20Practice%20Guide/Release_management_Fig7_1.jpg)

Figure 7.1 Design of the capability criteria

This approach results in every practice having up to 30 capability criteria based on the practice PSFs and mapped to the four dimensions of service management. The number of criteria at each level differs; the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

The following capability criteria are defined in the ITIL maturity model for the release management practice:

##### Table 7.1 Release management capability criteria

<table><tbody><tr><td><p><strong>PSF</strong></p></td><td><p><strong>Criterion</strong></p></td><td><p><strong>Dimension</strong></p></td><td><p><strong>Capability level</strong></p></td></tr><tr><td rowspan="6"><p>Establishing and maintaining effective approaches to the release of services and service components across the organization</p></td><td><p>The approach to release management is defined, discussed, and agreed at the relevant level of the organization</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>The responsibility for the approach to release management is clearly defined</p></td><td><p><span>Value streams and processes</span></p></td><td><p>3</p></td></tr><tr><td><p>The competencies required for performing the release management are identified and skilled human resources are available</p></td><td><p>Organizations and people<span></span></p></td><td><p>3</p></td></tr><tr><td><p>The release management approach is integrated with other standards and approaches adopted by the organization</p></td><td><p><span>Value streams and processes</span></p></td><td><p>4</p></td></tr><tr><td><p>The effectiveness of the release management approach is measured and reported</p></td><td><p><span>Value streams and processes</span></p></td><td><p>4</p></td></tr><tr><td><p>The release management approach is regularly reviewed and continually improved</p></td><td><p><span>Value streams and processes</span></p></td><td><p>5</p></td></tr><tr><td rowspan="10"><p>Ensuring an effective release of services and service components in the context of the organization’s value streams and service relationships</p></td><td><p>New services, changed services, and service components are successfully released into the live environments</p></td><td><p><span>Value streams and processes</span></p></td><td><p>2</p></td></tr><tr><td><p>Releases are automated where reasonably possible</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>The release information is tracked and managed in an integrated information system</p></td><td><p><span>Information and technology</span></p></td><td><p>3</p></td></tr><tr><td><p>The releases include the required competencies and human resources, where relevant</p></td><td><p><span>Organizations and people</span></p></td><td><p>3</p></td></tr><tr><td><p>The releases include the dependencies and relationships with third parties, where relevant</p></td><td><p>Partners and suppliers</p></td><td><p>3</p></td></tr><tr><td><p>The releases include the required workflows and procedures, where relevant</p></td><td><p><span>Value streams and processes</span></p></td><td><p>3</p></td></tr><tr><td><p>The releases include the required technologies and information flows, where relevant</p></td><td><p><span>Information and technology</span></p></td><td><p>3</p></td></tr><tr><td><p>The releases are effectively integrated into the organization’s value streams</p></td><td><p><span>Value streams and processes</span></p></td><td><p>4</p></td></tr><tr><td><p>The effectiveness of releases is measured and reported</p></td><td><p><span>Value streams and processes</span></p></td><td><p>4</p></td></tr><tr><td><p>The effectiveness of releases is regularly reviewed and continually improved</p></td><td><p><span>Value streams and processes</span></p></td><td><p>5</p></td></tr></tbody></table>

These capability criteria can be used by organizations for self-assessment and improvement of the practice.

#### 7.2 Capability self-assessment

The self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team in the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed.

1.  Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
2.  If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider’s employees.
3.  If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
4.  If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met; what is missing in the organization? Why? How can it affect the service consumer and the quality of the IT services? What can be done to meet the criteria that are currently missed?
5.  The same approach is applied at every next level; the practice is considered to be at the level where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.

#### 7.3 Release management capability development

Management practices should support achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at the capability level 5. Higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but it comes with a cost: cost of management, automation, and training, for example. To achieve optimal performance with sufficient level of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and Table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

![](Release%20management%20ITIL%204%20Practice%20Guide/Release_management_Fig7_2.jpg)

Figure 7.2 The capability development steps and levels

##### Table 7.2 The release management capability development steps

<table><tbody><tr><td><p><strong>Capability level</strong></p></td><td><p><strong>Define, agree, and implement</strong></p></td><td><p><strong>Comment for release management</strong></p></td><td><p><strong>Chapter (for recommendations)</strong></p></td></tr><tr><td rowspan="5"><p>2</p></td><td><p>Purpose and objectives</p></td><td rowspan="2"><ul><li>Key stakeholder groups, types of releases</li><li>The relationships between release and deployment management</li></ul></td><td><p>2.1</p></td></tr><tr><td><p>Scope</p></td><td><p>2.3</p></td></tr><tr><td><p>Processes and activities</p></td><td rowspan="3"><ul><li>Workflows, release models, roles and responsibilities</li><li>Automation and information exchange</li></ul></td><td><p>3</p></td></tr><tr><td><p>Roles and responsibilities</p></td><td><p>4</p></td></tr><tr><td><p>Tools and procedures</p></td><td><p>5</p></td></tr><tr><td rowspan="3"><p>3</p></td><td rowspan="3"><p>Dependencies and integration</p></td><td><p>Integration into the service value streams</p></td><td><p>3.2</p></td></tr><tr><td><p>Use of integrated information system</p></td><td><p>5</p></td></tr><tr><td><p>Suppliers and other parties involved in release management</p></td><td><p>6</p></td></tr><tr><td><p>4</p></td><td><p>Measurement and reporting</p></td><td><p>Metrics</p></td><td><p>2.5</p></td></tr><tr><td><p>5</p></td><td><p>Continual improvement</p></td><td><p>Regular review of practice and the release management capability development</p></td><td><p>2.4, 2.5, 7</p></td></tr></tbody></table>

## 8. Recommendations for practice success

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:

*   focus on value
*   start where you are
*   progress iteratively with feedback
*   collaborate and promote visibility
*   think and work holistically
*   keep it simple and practical
*   optimize and automate.

In Table 8.1, recommendations for success of the release management practice are linked to the relevant guiding principles.

<table><tbody><tr><td><p><strong>Recommendations</strong></p></td><td><p><strong>Comments</strong></p></td><td><p><strong>ITIL guiding principles</strong></p></td></tr><tr><td><p>Design and optimize the practice for the value streams</p></td><td><p>Release management is a part of change lifecycle but changes always have a purpose defined by the value streams. Understanding of the value stream context helps to plan and coordinate releases with the maximum value for the organization.</p></td><td><ul><li>Focus on value</li><li>Think and work holistically</li></ul></td></tr><tr><td><p>When release involves interactions with users, ensure the best user experience possible</p></td><td><p>Release management is not a purely technical practice, it is a part of user journey and impacts user experience. Service provider should understand and continually improve the release-related experience of the users, even if this means making releases invisible to users.</p></td><td><ul><li>Focus on value</li><li>Collaborate and promote visibility</li></ul></td></tr><tr><td><p>Review the effectiveness of release models</p></td><td><p>Do not limit release reviews to major or unsuccessful releases. Make it a regular activity and a part of continual improvement of the practice. Include stakeholder feedback (including user feedback) in the reviews.</p></td><td><ul><li>Progress iteratively with feedback</li><li>Collaborate and promote visibility</li></ul></td></tr><tr><td><p>Start with the most important products and services</p></td><td><p>Different products and services may need different release models. It is not possible to develop comprehensive release models for all of them at once. Start with the products and services that are the most important for the organization, and with those updated more often. But don’t stop there – continue developing release models for the most common product architectures.</p></td><td><ul><li>Start where you are</li><li>Progress iteratively with feedback</li></ul></td></tr><tr><td><p>Don’t overcomplicate the practice</p></td><td><p>Don’t aim to create a model for every possible scenario. Keep them practical and applicable to a wide range of products and services. Use ad-hoc planning for release instances where relevant, especially for releases of physical components.</p></td><td><p>Keep it simple and practical</p></td></tr><tr><td><p>Integrate release management in the CI/CD pipeline for digital products</p></td><td><p>Where applicable, harvest the benefits of CI/CD techniques and technologies. But remember that it is very likely to have products and services to which these techniques are not applicable.</p><p>Consider other automation tools for such products and services.</p></td><td><p>Optimize and automate</p></td></tr><tr><td><p>Demonstrate business value</p></td><td><p>Measure the practice and produce regular reports and dashboards for internal (within the service provider) and external (service consumer) stakeholders.</p><p>Use dashboards for the current status and regular reports for analysis and highlights.</p></td><td><ul><li>Focus on value</li><li>Collaborate and promote visibility</li></ul></td></tr></tbody></table>

## 9. Acknowledgements

PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following people:

## Authors

Anil Bahl, Martin Cross

## Reviewers

Roman Jouravlev

## 2023 Revision

Antonina Douannes, Adam Griffith, Roman Jouravlev, Kaimar Karu, Olga Masalina, Avinash Singh
