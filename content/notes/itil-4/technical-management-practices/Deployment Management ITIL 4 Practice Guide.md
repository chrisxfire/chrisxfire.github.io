---
title: "Deployment Management: ITIL 4 Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---


## 1. About this guide

This guide provides practical guidance for the deployment management practice. It is split into seven main sections, covering:

*   general information about the practice
*   the practice’s processes and activities and their roles in the service value chain
*   the organizations and people involved in the practice
*   the information and technology supporting the practice
*   considerations for partners and suppliers for the practice
*   information on assessing and developing the capability of the practice
    
*   recommendations for succeeding in the practice.
    

#### 1.1 ITIL® 4 qualification scheme

Selected content of this document is examinable as a part of the following syllabus:

*   **ITIL Specialist** Create, Deliver and Support
*   **ITIL Specialist** High-velocity IT
*   **ITIL Practitioner** Deployment Management
*   **ITIL Specialist** Plan, Implement and Control.

Please refer to the respective syllabus documents for details.

## 2. General information

#### 2.1 Purpose and description

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>The purpose of the deployment management practice is to move new or changed hardware, software, documentation, processes, or any other component to live environments. It may also be involved in deploying components to other environments for testing or staging.</p></td></tr></tbody></table>

<table><tbody><tr><td><p><strong>Definition: Deployment</strong></p></td></tr><tr><td><p>The movement of any service component into any environment.</p></td></tr></tbody></table>

The deployment management practice is responsible for moving a service or service component into a designated environment. This practice enables the deployment or removal of service components from or to different environments, including development, integration, live, production, test, or staging environments.

The practice is usually applied to digital and physical IT components, including software, hardware, documentation, licences, and data, within the agreed scope of environments controlled by the organization.

The deployment management practice is a key practice of service management. Effective deployment management is beneficial for both the service provider and service consumer.

Benefits for the service provider include:

*   Faster time to market by delivering working software and hardware to users quickly and efficiently

*   Reduced risk of errors and downtime related to product and service updates

*   Controlled and efficient deployment of service components to different environments

*   Improved agility supporting faster and more efficient software development and release
*   Effective integration of deployments into the service provider’s value streams.
    

Benefits for the service consumer include:

*   Support of business agility; faster time to market for new and improved business products and services
*   Seamless updates of business products and services
    
*   Reduced risks and losses caused by product and service updates
    
*   Reduced costs of product and service updates.
    

#### 2.2 Terms and concepts

##### 2.2.1 Environments

The deployment management practice enables the movement of products, services, and service components between the environments.

<table><tbody><tr><td><p><strong>Definition: Environment</strong></p></td></tr><tr><td><p>A subset of the IT infrastructure that is used for a particular purpose.</p></td></tr></tbody></table>

A service component’s lifecycle may vary depending on its type and the sourcing approach. The number and purpose of controlled environments within the organization may also vary. Table 2.1 provides a list of example environments for an organization that develops software.

##### Table 2.1 List of example environments for an organization that develops software

<table><tbody><tr><td><p><strong>Environment</strong></p></td><td><p><strong>Purpose</strong></p></td></tr><tr><td><p>Development/Integration</p></td><td><p>Developing and integrating software</p></td></tr><tr><td><p>Test</p></td><td><p>Testing service components</p></td></tr><tr><td><p>Staging</p></td><td><p>Testing releases including products, services and other configuration items</p></td></tr><tr><td><p>Live/Production</p></td><td><p>Delivering IT services to service consumers</p></td></tr></tbody></table>

For products and components sourced outside the organization, development environments can be out of the organization’s control. For products and services delivered to service consumers outside of the organization, control over the live environment can be limited. Other variations are possible.

##### 2.2.2 Continuous integration, continuous delivery, and continuous deployment (CI/CD)

The key concepts for deployment in Agile and DevOps are:

*   **Continuous integration** Integrating, building, and testing code within the software development environment.
*   **Continuous delivery** Continuous delivery means that built software can be released to production at any time. Frequent deployments are possible, but deployment decisions are taken on a case-by-case basis, usually because organizations prefer a slower rate of deployment.
*   **Continuous deployment** Changes go through the pipeline and are automatically put into the production environment, enabling multiple production deployments per day. Continuous deployment relies on continuous delivery.

These approaches are supported by the software development and management, service validation and testing, deployment management, infrastructure and platform management, and release management practices. These practices involve specific skills, processes, procedures, automation tools, and agreements with third parties. They enable the continuous pipeline for integration, delivery, and deployment. This also affects the design of other practices, such as service configuration management, monitoring and event management, incident management, and others.

#### 2.3 Scope

The scope of the deployment management practice includes:

*   the effective movement (transition) of products, services, and service components between controlled environments, such as the development, test, staging, and live environments.
*   the effective removal of products, services, and service components from designated environments.

These additions, modifications, and removals can be part of authorized changes or releases which can be triggered by:

*   new or changed service requirements
*   new features or releases
*   technical and operational changes
*   third-party change requirements
*   service retirements and removals
*   support or troubleshooting
*   service requests
*   service and component maintenance.
    

Several activities and areas of responsibility are not included in the deployment management practice, although they are still closely related to deployment. These are listed in Table 2.2, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

  

##### Table 2.2 Deployment-related activities described in other practice guides

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Authorizing changes/releases</p></td><td><p>Change enablement</p></td></tr><tr><td><p>Making services and components in the live environment available to users</p></td><td><p>Release management</p></td></tr><tr><td><p>Testing and validating services and service components</p></td><td><p>Service validation and testing</p></td></tr><tr><td><p>Developing software</p></td><td><p>Software development and management</p></td></tr><tr><td><p>Developing and building infrastructure components</p><p>Preparing and maintaining target environments for deployments</p></td><td><p>Infrastructure and platform management</p></td></tr><tr><td><p>Maintaining authorized repositories of service components</p></td><td><p>IT asset management</p></td></tr><tr><td><p>Naming, versioning, and controlling the service components</p></td><td><p>Service configuration management</p></td></tr></tbody></table>

#### 2.4 Practice success factors

<table><tbody><tr><td><p><strong>Definition: Practice success factor</strong></p></td></tr><tr><td><p>A complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The deployment management practice includes the following PSFs:

*   establishing and maintaining effective approaches to the deployment of services and service components across the organization
*   ensuring the effective deployment of services and service components in the context of the organization’s value streams.

  

##### 2.4.1 Establishing and maintaining effective approaches to the deployment of services and service components across the organization

The deployment management practice includes defining and agreeing a model or several models to use when deploying products, services, and components.

<table><tbody><tr><td><p><strong>Definition: Deployment model</strong></p></td></tr><tr><td><p>A repeatable approach to the management of particular types of deployments.</p></td></tr></tbody></table>

These models may use one deployment approach or combine deployment approaches, depending on their specific services and requirements, as well as the sizes, types, and impacts of the service components that are being deployed.

Models can be defined for deploying services or service components of similar types. Such deployment models could be defined based on several factors, including:

*   automation considerations
*   costs/resource limitations
*   expected frequency of the deployments
*   rate of change of customer requirements
*   rate of change of technology
*   risks of flaws in components
*   source of components
*   user adoption behaviours and preferences
*   visibility of the technology change to service consumers.

Based on these and other relevant considerations, organizations define a set of models for the deployment of different service components. These models may describe different solutions in all four dimensions of service management. Table 2.3 outlines some example models.

##### Table 2.3 Example models for the deployment of different service components.

<table><tbody><tr><td><p><strong>Deployment model applicability</strong></p></td><td><p><strong>Organizations and people</strong></p></td><td><p><strong>Information and technology</strong></p></td><td><p><strong>Value streams and processes</strong></p></td><td><p><strong>Partners and suppliers</strong></p></td></tr><tr><td><p>Hardware components of services provided to external service consumers</p></td><td><p>A service provider should arrange a delivery team for the transportation and installation of the components</p></td><td><p>A range of tools can be used to automate the procurement, invoicing, user communication, and scheduling of the installation of hardware</p></td><td><p>An installation order can be triggered by new or changed value streams that include clear authorizations to procure and install new hardware</p></td><td><p>Third-party shipping, delivery, and installation service providers can be employed, as agreed between the parties</p></td></tr><tr><td><p>Hardware components of services obtained from a vendor</p></td><td><p>According to the delivery and installation clause in the vendor contract, the responsibilities for obtaining hardware and ensuring its correct installation should be clearly defined</p></td><td><p>Vendor catalogues may be used for ordering the components, as well as to store and provide up-to-date installation manuals. A configuration management tool should be populated with documentation supplied with the hardware, including records and documents, such as warranty certificates, maintenance schedules, and so on</p></td><td><p>Vendor activities, such as invoicing and shipping, should be accounted for during the value stream design; interfaces between parties need to be founded in the contracts</p></td><td><p>Third-party shipping, delivery, and installation service providers can be employed, as agreed between the parties</p></td></tr><tr><td><p>Software components of services provided to external service consumers</p></td><td><p>The service provider can have staff perform roadshows to service consumers to promote new software components and facilitate change awareness</p></td><td><p>An automated deployment toolset is utilized to make software available for use or ordering</p></td><td><p>Service providers can implement additional controls before a component is deployed, such as quality assurances, security, or commercial; is is crucial to account for such controls in-partially or fully-automated deployment pipelines</p></td><td><p>Partners can be engaged in deployment, such as additional bespoke testing of the software made available by the vendor prior to its deployment to the consumer environment</p></td></tr><tr><td><p>Software components of services developed in house</p></td><td><p>DevOps teams are likely to perform the deployment of software</p></td><td><p>The continual integration and continual deployment pipeline toolset can be used to deploy software to a controlled environment</p></td><td><p>Service provider organizations have to establish organizational controls over the course of deployment, ensuring that controls are not excessive</p></td><td><p>Third parties can action some steps of the deployment model; for example, manual environment configuration activities</p></td></tr></tbody></table>

Deployment models also define the flow of deployment through controlled environments, responsibilities of the involved parties, triggers for deployment, and interactions with other practices’ activities in the context of value streams.

These models may be flexible enough to adapt to changing circumstances, such as the scale, urgency, or complexity of the deployment.

Deployment models, and the deployment management practice in general, should be a subject to continual improvement with an aim to eliminate waste and increase effectiveness and efficiency.

##### 2.4.2 Ensuring the effective deployment of services and service components in the context of the organization’s value streams

Ensuring effective deployment requires orchestrating resources in all four dimensions of service management.

The effectiveness and efficiency of the deployment is significantly dependent on, and can be considerably impacted by, the availability of the relevant resources, skills, technology, tools and infrastructure. The effective use of technology and automation in deployment can improve the consistency, agility, and efficiency of the practice.

For changes and releases to be successful, it is crucial that the changed or released service’s or service component’s integrity is maintained throughout the move process. Any unauthorized change caused by manual, process, or technology errors can negatively impact the objectives and outcomes of the changes and releases, often significantly impacting the organization.

The success of service moves depends on the effective and efficient management of changes and releases, which in turn depends on timely deployments that align with requirements and objectives. Alignment of the deployment to the change and release requirements, as well as key aspects such as schedule and cost, must be managed effectively.

#### 2.5 Key metrics

The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for deployment management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of deployment management to the effectiveness and efficiency of those value streams. Some examples of key metrics of deployment management are given in Table 2.4.

##### Table 2.4 Examples of metrics for the practice success factors

<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Establishing and maintaining effective approaches to the deployment of services and service components across the organization</p></td><td><ul><li>Level of stakeholders’ satisfaction with the rate of change of products and services supported by deployments</li></ul><ul><li><p>Rate of adoption of the agreed approach to deployment across the organization</p></li><li><p>Level of key partners’ and service consumers’ alignment with deployment approaches</p></li><li><p>Number of audit findings and external compliance issues caused by deployments</p></li></ul></td></tr><tr><td><p>Ensuring effective deployment of services and service components in the context of the organization’s value streams</p></td><td><ul><li>Level of stakeholders’ satisfaction with lead time to deploy</li><li>Percentage of successful deployments/number of deployment errors/failures</li><li>Number/percentage of incidents related to deployments</li><li>Timeliness/adherence to deployments schedule</li><li>Deployment backlog throughput</li><li>Level of stakeholders’ satisfaction with quality of deployments</li></ul></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the deployment management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

## 3. Value Streams and processes

#### 3.1 Processes

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><p><strong>Definition: Process</strong></p></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

Deployment management activities form two processes:

*   Deployment model development and improvement
*   Deployment lifecycle management.

##### 3.1.1 Deployment model development and improvement

This process focuses on the continual improvement of the deployment management practice, deployment models, and the deployment procedures. It is performed regularly but can also be triggered by deployment failures which highlight inefficiencies and other improvement opportunities. Regular reviews may occur every three months, or more frequently, depending on the effectiveness of the existing models and procedures.

This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

##### Table 3.1 Inputs, activities, and outputs of the deployment model development and improvement

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Current deployment approach, models and procedures</li><li>Deployment records</li></ul><ul><li>Deployment failure reports</li><li>Policies and regulatory requirements</li><li>Release models</li><li>Service configuration information</li><li>IT asset information</li><li>SLAs with consumers and suppliers/partners</li><li>Capacity and performance plans and reports</li><li>Continuity policies and plans</li><li>Security policies and plans</li></ul></td><td><ul><li>Deployment model planning</li></ul><ul><li>Deployment model implementation</li><li>Deployment model testing</li><li>Deployment review and deployment records analysis</li><li>Deployment model improvement initiation</li><li>Deployment model update and communication</li></ul></td><td><ul><li>Updated deployment models and procedures</li><li>Communication of updates to deployment models and procedures update</li><li>Change requests</li><li>Improvement initiatives</li><li>Deployment review reports</li><li>Updated knowledge management articles</li><li>Lessons learnt</li></ul></td></tr></tbody></table>

![](Deployment%20Management%20ITIL%204%20Practice%20Guide/Deployment_management_Fig3_1.jpg)

Figure 3.1 Workflow of the deployment model development and improvement process

Table 3.2 provides examples of the process activities.

##### Table 3.2 Activities of the deployment model development and improvement process

<table><colgroup data-width="732"><col><col></colgroup><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Deployment model planning</p></td><td><p>When a product follows a similar low-risk, high-success-rate deployment pattern and there are means to eliminate waste and reduce deployment lead times, the deployment manager may choose to define a new deployment model. The deployment model should reduce the human involvement and control over the deployment.</p></td></tr><tr><td><p>Deployment model implementation</p></td><td><p>The deployment manager arranges for appropriate pipeline tools to be configured to support the new model, such as access settings, code support, or branching procedures. Alternatively, if automated deployment tools are not applicable, the deployment manager establishes and communicates adequate guidelines to the teams and parties involved.</p></td></tr><tr><td><p>Deployment model testing</p></td><td><p>The deployment manager tests the new deployment model to ensure proper edge-case handling and workflow. Where testing is impossible, the deployment manager oversees the first of the model’s live runs.</p></td></tr><tr><td><p>Deployment review and deployment failure records analysis</p></td><td><p>The deployment manager, together with service owners and other relevant stakeholders, performs a review of selected deployments or deployment failures. They identify opportunities for the optimization of deployment models and deployment procedures.</p></td></tr><tr><td><p>Deployment model improvement initiation</p></td><td><p>The deployment manager registers the improvement initiatives to be processed with the involvement of the continual improvement practice, or initiates a change request, if the deployment models and procedures are included within the scope of change enablement.</p></td></tr><tr><td><p>Deployment model update and communication</p></td><td><p>If the deployment model is successfully updated, it is communicated to the relevant stakeholders. This is usually done by the deployment manager and/or the service or resource owner.</p></td></tr></tbody></table>

##### 3.1.2 Deployment lifecycle management

This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

##### Table 3.3 Inputs, activities, and outputs of the deployment lifecycle management process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Deployment requirements and expectations</li><li>Environment details</li><li>Service components/release components</li><li>Hardware and software components from the authorized repositories of ITAM and definitive media library</li><li>Acceptance criteria</li></ul></td><td><ul><li>Deployment planning</li><li>Verification of the service components</li><li>Verification of the target environments</li><li>Deployment execution</li><li>Deployment verification</li></ul></td><td><ul><li>Deployed service components/releases</li><li>Deployment records</li><li>Deployment communications</li><li>Feedback and inputs to change enablement, release management, service validation and testing, project management, and so on</li><li>Updates to onboarding procedures, customer knowledge base, service desk data</li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![](Deployment%20Management%20ITIL%204%20Practice%20Guide/Deployment_management_Fig3_2.jpg)

Figure 3.2 Workflow of the deployment lifecycle management process

In an organization that has adopted a CI/CD framework, many of these activities will be performed in an automated fashion, without manual intervention.

Table 3.4 provides examples of the process activities.

##### Table 3.4 Activities of the deployment models development and review process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><strong></strong><span><strong>Manual deployment to a datacenter</strong></span><strong></strong></td><td><strong></strong><span><strong>Automated deployment of a software component</strong></span><strong></strong></td></tr><tr><td><span>Deployment planning</span></td><td><span>After a trigger from deployment (often procurement or the change request initiator), the service provider will schedule the shipping, delivering, verification, storing, and installation of hardware components. This schedule will align with the priorities of other work units for the affected teams and other resources.</span></td><td><span>Deployments in automated pipelines are triggered by committing all of the necessary pieces of code to a branch of the development version control system that will contain software features that are prepared for deployment.</span></td></tr><tr><td><span>Verification of the service components</span></td><td><span>Upon receiving delivered components, the service provider checks the completeness of the inventory, including the documentation, and conducts basic quality checks before accepting the delivery.</span></td><td><span>The code in the appointed branch is deployed to a suitable test environment, tested, and any issues are fixed directly in the branch.</span><p><span>The ‘deploy, test, fix, redeploy, retest’ cycle continues until a pre-set quality threshold of automated tests is met.</span></p></td></tr><tr><td><span>Verification of the target environment</span></td><td><span>The item is delivered to the installation location, where it is installed with the aim of causing minimal disruption to the service users. The installation location should have sufficient power, back-up power, air- conditioning, and fire protection arrangements. It may be necessary to include target environment checks in the deployment plan.</span></td><td><span>For Infrastructure as Code (IaC) solutions, the configuration of a virtual environment in which the software should be run also follows an automated pipeline and is deployed to the virtual resources alongside the software code.</span></td></tr><tr><td><span>Deployment execution</span></td><td><span>The service provider or staff of a supplier installs and activates the equipment according to the installation instructions, which may include intermediate checks.</span></td><td><span>Deployment to an environment is automated, but can include additional human interaction steps before the actual deployment to account for business, security, or other non-automated types of verification.</span></td></tr><tr><td><span>Deployment verification</span></td><td><span>After the item has been installed, a series of tests is performed to confirm the equipment is functioning.</span><p><span>The staff performing the installation notifies those who triggered the deployment of the deployment results.</span></p></td><td><span>The version control system sends notifications to the change requestor, such as a product owner, when the deployment is complete.</span></td></tr></tbody></table>

#### 3.2 Value stream contribution

##### 3.2.1 Service value streams

To perform certain tasks or respond to particular situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario. Once designed, value streams should be subject to continual improvement.

<table><tbody><tr><td><p><strong>Definition: Value stream</strong></p></td></tr><tr><td><p>A series of steps an organization undertakes to create and deliver products and services to consumers.</p></td></tr></tbody></table>

In practice, however, many organizations come to the use of the value stream concept after having worked for a while (sometimes for years) without the value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the ‘As Is’ situation, and the de-facto flows of work, and to analyse them in order to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding the existing value streams is critical to improving an organization’s performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services. Combined, the organizations’ value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations follow best practice recommendations for various service management practices, such as incident management, change enablement, software development, and many others. However, the practices are often adopted and organized in a siloed, isolated manner, as they are presented in service management bodies of knowledge. In reality, a flow of work required to create or restore value, for a customer or another stakeholder, is almost never limited to one practice.

##### 3.2.2 Deployment management in service value streams

As mentioned in section 2.3, deployment management contributes to implementation of changes initiated by a range of sources. The practice plays an important role in service value streams involving changes. These are outlined in Table 3.5.

##### Table 3.5 Role of the deployment management practice in service value streams

<table><colgroup data-width="992"><col><col></colgroup><tbody><tr><td><strong>Service value stream</strong></td><td><strong>Role of the deployment management practice</strong></td></tr><tr><td>Incident resolution</td><td><span>Deployment of fixed components, patches, updated versions of software, and other changes executed to solve an incident and restore normal service operations</span></td></tr><tr><td>Request fulfilment</td><td><span>Deployment of changed or new components and versions required to fulfil a request model</span></td></tr><tr><td>Product and service continual improvement</td><td><span>Deployment of fixed components, patches, updated versions of software, and other changes executed to realize an approved improvement initiative</span></td></tr><tr><td><span>Delivery of new and changed services</span></td><td><span>Deployment of new and changed components, patches, updated versions of software, and other changes executed to fulfil an agreed product or service development plan</span></td></tr><tr><td>Ongoing operations and maintenance</td><td><span>Deployment of changed or new components and versions required to fulfil an agreed maintenance of the live systems and components</span></td></tr></tbody></table>

In all cases, deployment is a part of a change implementation and should be coordinated with other activities in the change lifecycle, such as purchasing, configuring, testing, and release. Deployments are within the scope of the change lifecycle management process (see the change enablement practice guide). The change enablement practice ensures the correct selection of a relevant deployment model; scheduling of the deployment phase of the change implementation; and acceptance of the deployment. At the same time, the deployment management practice ensures that valid deployment models are available and correctly executed when required according to the change plan and change schedule. Figure 3.3 illustrates the positioning of the deployment lifecycle management process in the various value streams involving changes. Note: the figure only addresses deployments to live environments. In practice, there may be a number of transitions between environments during one change, and each one would be subject to deployment lifecycle management.

![](Deployment%20Management%20ITIL%204%20Practice%20Guide/Deployment_management_Fig3_3.jpg)

Figure 3.3 Deployment lifecycle management in service value streams

It is important to ensure the effective integration of the deployment management practice in the management of change lifecycles and further in the service value streams. Depending on the business context of the changes, deployment may be assigned different levels of urgency and impact, which should be possible to address with the application of a relevant deployment model.

#### 3.2.3 Analysing a service value stream

##### 3.2.3.1 The key steps of a service value stream analysis

The following are some simple and practical recommendations for service value stream analysis and mapping:

**1\. Identify the scope of the value stream analysis**

This can be mapped to a particular product or service or applied to most or all of them. Similarly, service value streams may differ for different consumers; for example, Deployments can be performed differently for internal and external service consumers, or for B2B and B2C products, Service category, services based on products developed inhouse or sourced externally, automated or manual deployment method, change models, waterfall or agile approach followed by the organization.

**2\. Define the purpose of the value stream from the business standpoint**

Make sure the stakeholders’ outcomes or concerns are clearly understood, since they are the ones defining value. In the case of Deployment management, it is usually the change requestor, product owner or business user who needs a new functionality, feature, or a new service; however, there are usually other interested parties. For example, internal stakeholders such as release managers, the quality assurance team, and the software development teams, as well as the value of the value stream, should be considered from the business perspective, not solely from the user perspective.

**3\. Do the value stream walk**

Walk through or directly experience the steps and information flow as they go in practice (consider the Lean technique of Gemba walk):

**a. Identify the workflow steps**

**b. Collect data as you walk**

**c. Evaluate the workflow steps**

Typically, the criteria for evaluation are:

*   value for the stakeholder (does the step add value for the business stakeholder?)
*   effective or performance (is the step performed well?)
*   efficiency (is the step being performed in an optimal manner?)
*   availability (are required resources available to execute the step?)
*   capacity (are required resources enough?)
*   flexibility (are the required resources interchangable within the step?).

**d. Map the activities and the information flows**

In an ideal situation, the flow goes smoothly without delays and pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

**e. Create and review the timeline and resource level**

Map out process times and lead times for resources and workload through the workflow steps.

**4\. Reflect on the value stream map (VSM)**

Identify factors that might not have been entirely apparent at first. The information collected is used at this step to find waste.

**5\. Create a 'to be' VSM**

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

**6\. Using the 'to be' VSM, plan improvements**

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

##### 3.2.3.2 Deployment management considerations in a service value stream analysis

To ensure that relevant deployment management activities are included in service value streams, the following steps can be added to the above recommendations.

*   At the scoping step (1), identify the IT and business services related to the value stream and the involved business stakeholders. For example, when an IT service provider deploys IT services or software or hardware components desired by the business users who in turn provide services to the business clients, should the deployment value stream involve full deployment or incremental deployment in the live environment for the clients, or should it be limited to the deployment in the staging or test environment? 
    
*   Make sure the value stream is understood (step 2) from the standpoint of the business, not only of the service provider.
    
*   During the service value stream walk (3a), identify other practices involved in dealing with deployments at every step. Which practices provide required information (service configuration, CI information, target destination, solution architecture, and so on)? What if the deployment activities involve third parties?
    
*   During the evaluation of workflow steps (3c), evaluate the step’s impact on the transition of new or changed hardware, software, documentation, processes, or any other component to live environments or any other stage such as test or staging environments. Special attention should be paid to steps with low business value, low performance, waiting time, manual activities and availability or capacity issues. It is not unusual to find steps which serve some internal control or bureaucratic purposes but delay the deployment velocity.
*   At the reflection and planning steps (4-5), ensure that the deployment management flow is optimized for business value throughout the stream, not only at the deployment management practice activities.
    
*   Include the creation or update of deployment models (see section 3.1.1) in the value stream improvement plans (step 6).
    

## 4. Organizations and people

#### 4.1 Roles, competences, and responsibilities

The practice guides do not describe the practice management roles, such as practice owner, practice lead, or practice coach. They focus instead on specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

##### Table 4.1 Competency codes and profiles

<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p>L</p></td><td><p><strong>Leader </strong>Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p>А</p></td><td><p><strong>Administrator </strong>Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p>C</p></td><td><p><strong>Coordinator/communicator </strong>Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p>М</p></td><td><p><strong>Methods and techniques expert </strong>Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p>Т</p></td><td><p><strong>Technical expert </strong>Providing technical (IT or other subject matter) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

Two practice-specific roles may be found in organizations: deployment manager and deployment practitioner. These roles are often introduced in organizations where the number of deployments is high. In other organizations, these roles might be combined with, or assigned to, other roles carrying related responsibilities in development, operations, IT asset teams, and so on.

##### 4.1.1 Deployment manager role

A deployment manager role calls for a strong knowledge of the organization’s business, products and services, technology, platforms, frameworks, and processes. The role requires strong planning and project management skills and the ability and authority to coordinate teamwork. The competency profile for this role is LACM. This role is usually responsible for the planning, management, and coordination of deployment management as a practice as well as the deployment of individual releases, including:

*   planning deployments
*   ensuring the alignment of deployment plans with change/release plans, requirements, and objectives
*   planning, coordinating, and ensuring the availability of the resources needed for the effective completion of deployments
*   effectively managing overlaps or conflicts among multiple deployments
*   implementing and maintaining effective control and governance to ensure the integrity of components throughout the deployment practice
*   managing and/or ensuring effective interfaces between and coordination with other practices and stakeholders
*   managing and optimizing deployment resources to ensure optimum levels of availability, capability, and capacity to manage deployments
*   monitoring, reporting, analysing, and improving deployment performance against defined KPIs.

In more complex organizations, some of the deployment management responsibilities may be delegated to the role of deployment coordinators, team leaders, or any other similar additional roles.

##### 4.1.2 Deployment practitioner role

A deployment practitioner role calls for strong technical skills and effective teamwork. The competency profile for this role is TAC. This role is usually responsible for effective deployments to the target environments in alignment with applicable requirements, objectives, and targets, including:

*   acquiring, maintaining, and continually improving the skills and capabilities required for technical aspects of deployments
*   contributing and assisting in deployment planning
*   ensuring the integrity of components throughout the deployment practice
*   managing and coordinating deployment documentation, records, and communications, including for training purposes
*   coordinating with other practices and stakeholders and facilitating interfaces between groups
*   verifying and providing feedback on deployments to stakeholders
*   contributing to monitoring, reporting, analysing, and improving deployment performance against defined KPIs.

In some organizational contexts, the deployment practitioner role can be divided into multiple categories and levels based on the types and requirements of the deployments and platforms, the complexity of organization’s products and services, and so on.

##### 4.1.3 Roles involved in the deployment management activities

Examples of other roles which can be involved in the deployment management activities are listed in Table 4.1, together with the associated competency profiles and specific skills.

  

##### Table 4.2 Examples of roles with responsibility for deployment management activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Responsible roles</strong></p></td><td><p><strong>Competency profile</strong></p></td><td><p><strong>Specific skills</strong></p></td></tr><tr><td colspan="4"><p><span>Deployment model development and improvement process</span></p></td></tr><tr><td><p>Deployment model planning</p></td><td><ul><li>Deployment manager</li><li>Service owner</li><li>Product owner</li></ul></td><td><p>MTCA</p></td><td><ul><li>Understanding of the service design, resource configuration, and business impact</li><li><span></span>Good knowledge of existing deployment activities</li></ul></td></tr><tr><td><p><span>Deployment model implementation</span></p></td><td><ul><li>Deployment manager</li><li>Service owner</li><li><span></span>Product owner</li></ul></td><td><p>CMTA</p></td><td><ul><li>Knowledge of deployment pipeline tools</li><li><span></span>Knowledge of the continual improvement and change enablement practices</li></ul></td></tr><tr><td><p><span>Deployment model testing</span></p></td><td><ul><li>Deployment manager</li><li>Service owner</li><li><span></span>Product owner</li></ul></td><td><p>TAC</p></td><td><ul><li>Good knowledge of testing practices across the workflows</li><li>Good knowledge of requirements and commitments, service levels<span></span></li><li>Knowledge of deployment models and methods; analytical skills</li></ul></td></tr><tr><td><p><span>Deployment review and deployment records analysis</span></p></td><td><ul><li>Deployment manager</li><li>Service owner</li><li>Product owner</li><li>Supplier</li></ul><span></span><br></td><td><p>MTCA</p></td><td><ul><li>Understanding of the service design, resource configuration, and business impacts</li><li>Good knowledge of deployment models</li><li>Good knowledge of requirements and commitments, service levels</li><li><span></span>Knowledge of deployment models and methods; analytical skills</li></ul></td></tr><tr><td><p><span>Deployment model improvement initiation</span></p></td><td><ul><li>Deployment manager</li><li>Service owner<span></span></li><li>Product owner</li></ul></td><td><p>MTCA</p></td><td><ul><li>Understanding of the service design, resource configuration, business impacts, and service levels</li><li>Good knowledge of deployment models, diagnostic tools, and methods</li><li>Knowledge of the continual improvement and change enablement practices</li></ul></td></tr><tr><td><p><span>Deployment model update and communication</span></p></td><td><ul><li>Deployment manager</li><li>Service owner</li><li>Product owner<span></span></li><li>Service desk agent</li></ul></td><td><p>MCA</p></td><td><p><span>Knowledge of communication procedures and tools</span></p></td></tr><tr><td colspan="4"><p>Deployment lifecycle management process</p></td></tr><tr><td><p>Deployment planning</p></td><td><ul><li>Service owner</li></ul><ul><li>Product owner</li><li>Development team member</li><li>Technical specialist</li><li>Service desk agent</li><li>Engagement manager</li><li>Delivery manager</li><li>Users</li></ul></td><td><p>MCTA</p></td><td><ul><li>Understanding the deployment’s impact on the service levels, user experiences, and environments</li><li>Good communication and cross-team coordination skills</li><li>Good knowledge of deployment models</li><li><span></span>Understanding of technical service design, supporting infrastructure and platforms, development tools</li></ul></td></tr><tr><td><p><span>Verification of the target environments</span></p></td><td><ul><li>Technical specialist</li><li>Deployment manager</li><li>Development team member</li><li>Systems administrator</li><li>Infrastructure team member</li><li>Service owner<span></span></li><li>Product owner</li></ul></td><td><p>TA</p></td><td><p><span>Good knowledge of environments and infrastructure</span></p></td></tr><tr><td><p>Deployment execution</p></td><td><ul><li>Technical specialist</li><li>Deployment manager</li><li>Development team member</li><li>Systems administrator<span></span></li><li>Infrastructure team member</li></ul></td><td><p>TCA</p></td><td><ul><li>Understanding of technical service design, supporting infrastructure and platforms, development tools</li><li>Good knowledge of deployment models</li></ul></td></tr><tr><td><p>Deployment verification</p></td><td><ul><li>Technical specialist</li><li>Deployment manager</li><li>Development team member</li><li>Systems administrator<span></span></li><li>Infrastructure team member</li></ul></td><td>TA</td><td><ul><li>Understanding of technical design of services and components</li><li><span></span>Good knowledge of service performance, service levels, and user experience</li></ul></td></tr></tbody></table>

#### 4.2 Organization structures and teams

Designated deployment management teams are unusual, except in very large organizations with significant volumes and complexity of deployment. This role is often handled by the technical/operations or platform teams.

In a DevOps environment, deployment is often automated through the continual deployment practice/framework with use of deployment pipelines. However, the role of deployment manager is often still relevant; the deployment manager would own the overall practice and aspects around deployment. This role could be independently established or combined with other relevant and suitable roles, such as release manager.

##### 4.2.1 Team structures for deployment management

Typically, in large organizations with significant volumes and complexity of deployments, deployment teams are structured in one of three ways:

*   Product/service based
*   Practice-based
*   Deployment as a service.

###### 4.2.1.1 Product/service based

Deployment managers and practitioners belong to teams, each of which is focused on a particular product- or technology-defined scope such as a single product, service, platform, or a set of features. This type of deployment team is empowered to build and deliver value quickly by moving new or changed hardware, software, documentation, processes, or any other component within the team’s responsibility to live environments. It may also be involved in deploying components to other environments for testing or staging. The product-based teams are cross functional teams and perform all or most activities throughout the product lifecycle, from planning to development, deployment, release, and operations.

###### 4.2.1.2 Practice-based

Many organizations adopt organizational structures based on the practices or groups of practices. It is not uncommon to see dedicated change enablement (also known as change management) teams, release teams, deployment teams, and testing teams, sometimes combined into an umbrella department under a name such as service transition or similar. This approach provides the organization with dedicated resources shared across many products, services and technology domains. These teams sometimes evolve to centers of excellence which may become service providers focused on a particular area of service management, as described below. The most important requirement to such teams is to be able to effectively participate in the end-to-end value streams of the service provider and to understand all products, services, and technologies in scope well enough.

###### 4.2.1.3 Deployment as a service

The purpose of a deployment as a service team is to enable and support value stream-aligned teams to deliver work independently. While the value stream-aligned team has end to end ownership of building, testing, deploying and running the service, the deployment as a service team provides internal services and specialized expertise with regards to practices, tooling and automation to reduce the workload for value stream aligned teams.

## 5. Information and technology

#### 5.1 Information exchange

The effectiveness of the deployment management practice is dependent on the quality of the information used. This information includes, but is not limited to, information about:

*   authorized repositories of service components and assets, such as IT asset databases and DML
*   assets and configurations
*   change and release plans
*   deployment communications
*   deployment documentation and records
*   deployment plans
*   deployment metrics and reports
*   entry, exit, and acceptance criteria for each stage of deployment
*   feedback from deployment
*   issues and errors identified during deployment
*   platforms and environments within deployment’s scope
*   products and services and their architecture and design
*   requirements and expectations about changes and releases
*   stakeholder needs, expectations, and contact details.

This information may take various forms. The key inputs and outputs of the practice are listed in Chapter 3.

#### 5.2 Automation and tooling

In most cases, the deployment management practice can significantly benefit from automation. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to the full automation of activities where technology solutions remove the need for human intervention. Deployments in Agile and DevOps environments are predominantly automation - and technology - oriented.

Where automation is possible and effective for deployment, it may involve the solutions outlined in Tables 5.1 and 5.2.

##### Table 5.1 Automation solutions for the deployment management activities

<table><tbody><tr><td><p><strong>Automation tools</strong></p></td><td><p><strong>Application in deployment management</strong></p></td></tr><tr><td><p><span>Work planning and prioritization tools</span></p></td><td><ul><li>Activity planning</li><li>Scheduling deployments<span></span></li><li>Deployment tracking</li></ul></td></tr><tr><td><p><span>Workflow management and collaboration tools</span></p></td><td><ul><li>Record management</li><li>Integration in the value streams<span></span></li><li>Communication and collaboration between teams</li></ul></td></tr><tr><td><p><span>Service configuration management tools</span></p></td><td><p><span>Compare the components on various parameters</span></p></td></tr><tr><td><p><span>Environment configuration and management tools</span></p></td><td><p><span>Check the target platform(s) against set of parameters and attributes</span></p></td></tr><tr><td><p><span>Deployment Tools</span></p></td><td><p><span>Deployment of the designated service components/releases to target environment(s) in a scheduled and controlled manner<wbr></span></p></td></tr><tr><td><p><span>CI/CD Tools</span></p></td><td><ul><li>Automate development</li><li>Automate testing</li><li><span></span>Automate deployment</li></ul></td></tr></tbody></table>

##### Table 5.2 Automation solutions for deployment management activities

<table><colgroup data-width="1002"><col><col><col><col></colgroup><tbody><tr><td><p><strong>Process activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><p><strong>Key functionality</strong></p></td><td><p><strong>Impact on the effectiveness of the practice</strong></p></td></tr><tr><td colspan="4"><p><span>Deployment model development and improvement</span></p></td></tr><tr><td><p>Deployment model planning</p></td><td><ul><li>Workflow management and collaboration tools</li><li>CI/CD tools</li><li><span></span>Service configuration management tools</li></ul></td><td><p><span>Definition, recording, review and approval of a deployment model components and steps</span></p></td><td><p>High</p></td></tr><tr><td><p><span>Deployment model implementation</span></p></td><td><ul><li>Environment configuration and management tools</li><li>CI/CD tools</li><li>Service configuration tools</li><li><span></span>Deployment tools</li></ul></td><td><p><span>Setup of the defined deployment model’s components and steps</span></p></td><td><p>High</p></td></tr><tr><td><p><span>Deployment model testing</span></p></td><td><ul><li>Environment configuration and management tools</li><li>CI/CD tools</li><li>Service configuration tools</li><li><span></span>Deployment tools</li></ul></td><td><p><span>Testing of the set up deployment model</span></p></td><td><p>High</p></td></tr><tr><td><p>Deployment review and deployment failure records analysis</p></td><td><ul><li>Workflow management and collaboration tools</li><li>CI/CD tools</li><li>Service configuration management tools</li><li>Deployment tools<span></span></li><li>Environment configuration and management tools</li></ul></td><td><ul><li>Reporting of the deployment model performance</li><li><span></span>Communication and collaboration during the review</li></ul></td><td><p>Medium to High</p></td></tr><tr><td><p><span>Deployment model improvement initiation</span></p></td><td><ul><li>Workflow management and collaboration tools</li><li>CI/CD tools</li><li><span></span>Service configuration management tools</li></ul></td><td><p><span>Recording and communication of the improvement initiatives for deployment models and other aspects of the practice</span></p></td><td><p><span>Medium to High</span></p></td></tr><tr><td><p><span>Deployment model update and communication</span></p></td><td><ul><li>Workflow management and collaboration tools</li><li>CI/CD tools</li><li><span></span>Service configuration management tools</li></ul></td><td><p><span>Update of the deployment models information for the relevant stakeholders</span></p></td><td><p><span>Medium to High</span></p></td></tr><tr><td colspan="4"><p><span>Deployment lifecycle management (partially automated)</span></p></td></tr><tr><td><p><span>Deployment planning</span></p></td><td><ul><li>Work planning and prioritization tools</li><li><span></span>Workflow management and collaboration tools</li></ul></td><td><p><span>Activity planning, scheduling, and tracking</span></p></td><td><p>High</p></td></tr><tr><td><p><span>Verification of the service components</span></p></td><td><ul><li>Service configuration management tools</li><li><span></span>Deployment tools</li></ul></td><td><p><span>Configuration verification by selected parameters and by pre-defined models</span></p></td><td><p>High</p></td></tr><tr><td><p><span>Verification of the target environment</span></p></td><td><ul><li>Environment configuration and management tools</li><li><span></span>Service configuration tools</li></ul></td><td><p><span>Verification of the target environment against set of parameters and attributes</span></p></td><td><p>High</p></td></tr><tr><td><p><span>Deployment execution</span></p></td><td><p><span>Deployment management tools</span></p></td><td><p><span>Deployment of the designated service components/releases to target environment(s) in a scheduled and controlled manner</span></p></td><td><p>High</p></td></tr><tr><td><p><span>Deployment verification</span></p></td><td><ul><li>Service configuration tools</li><li>Deployment tools</li><li><span></span>Environment configuration and management tools</li></ul></td><td><p><span>Verification of the deployment and deployed service components against defined acceptance criteria</span></p></td><td><p>High</p></td></tr><tr><td colspan="4"><p><span>Deployment lifecycle management (fully automated CI/CD toolchain)</span></p></td></tr><tr><td><p><span>Automated deployments to dev, test, staging, and production</span></p></td><td><p><span>Integrated CI/CD toolchains</span></p></td><td><p><span>Schedule/trigger-based, automated deployment of the required components to target environments at each stage</span></p></td><td><p>High</p></td></tr></tbody></table>

##### 5.2.1 Recommendations for the automation of deployment management

The following recommendations can help when applying automation to deployment management:

*   **Automate the end-to-end value stream** Automation of the deployment lifecycles should be integrated into the value streams including release management, change enablement, and, where relevant, activities of other management practices. A lack of integration complicates the value streams and reduces their effectiveness and efficiency. Consider implementing a CI/CD toolchain to support the end-to-end flow from development to operations but maintain the end-to-end approach to other value streams as well.
*   **Infrastructure as code**  The adoption of digital infrastructure allows for the automation of deployment of infrastructure components using tools and methods similar to those used for the deployment of application software. This supports better integration of deployment in the value streams, faster deployment execution, and more effective control of the service components.
    
*   **Utilize environment configuration and management tools** Ensure that the scope of deployment models includes the verification and, if necessary, configuration of the target environments. Management of environments should include version control; ensure integration with service configuration and asset management data.
    
*   **Ensure effective integration with validation and testing** Although service validation and testing is a different practice, in highly automated environments deployment and testing are closely integrated. Ensure that all steps of deployment models include relevant validation and testing.

## 6. Partners and suppliers

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of *ITIL Foundation: ITIL 4 Edition* for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the ITIL practices for service design, architecture management, and supplier management.

It is important to understand how the organization depends on third-party components and how it aims to establish effective and efficient collaboration with its key suppliers and partners around many activities, including those of the deployment management practice.

In an environment with multiple suppliers, it is important to understand the scope and boundaries of each organization’s deployment activities, and how these will interact. Most organizations have a process for deployment, which is often supported by standard tools and detailed procedures to ensure that software is deployed consistently. It is common to have different processes for different environments.

Many areas of the deployment management practice might be enabled by external resources, including people, tools, processes, and other capabilities.

The deployment management practice and its PSFs can be enabled and enhanced through selective and judicial sourcing in many forms, including those outlined in Table 6.1.

##### Table 6.1 Sourcing in the deployment management practice

<table><tbody><tr><td><p><strong>Sourcing area</strong></p></td><td><p><strong>Details</strong></p></td></tr><tr><td><p>People</p></td><td><p>Where deployment management activities are manual, resources could be sourced from a partner. Key considerations include the schedule of deployments, availability of internal resources, cost, and so on.</p></td></tr><tr><td><p>Technical/Non- technical skills and capabilities</p></td><td><p>Sourcing specific skills, including technical (about specific systems, technologies, platforms) and non-technical (planning, governing, and execution capabilities), are useful or even required in many deployment management activities. Key considerations include the variety and complexity of technical/service environments, dynamic technology environments, lack of appropriate internal resources, and so on.</p></td></tr><tr><td><p>Outsourced deployment management</p></td><td><p>In certain contexts, it may be necessary or useful to source the entire deployment management practice from a partner.</p></td></tr><tr><td><p>Tools and technologies for deployment</p></td><td><p>Several areas of the deployment management practice can be enhanced through the adoption of tools and technologies. Except in minor cases, these technologies, tools, and tool-chains are sourced from specific product/service providers.</p></td></tr></tbody></table>

Partners and suppliers may support the development, management, and execution of the deployment management practice. The forms of support include the following:

*   **Performing the deployment management activities** Some deployment management activities can be largely or completely performed by a specialized supplier. Third parties may get involved in deployment and the automation of deployment management activities. It is important to ensure effective integration of the third parties in the deployment, release management and software development management workflows and information exchange, as well as their adherence/compliance to relevant policies.
    
    Deployment strategy, practices and value streams should define how third parties are involved in deployment management and how the organization ensures effective collaboration. Once the end-to-end value stream is defined considering deployment management and key interfacing practices such as release management, service validation and testing and software development and management, further consideration of third-party dependencies is needed during building, testing and deployment activities.
    
    Defined standard interfaces may become an easy way to communicate the necessary conditions and requirements for a supplier to become a part of the organization's ecosystem. Such interface description may include rules of data exchange, tools, and processes that will create a common language, practice and value streams in the multi-vendor environment.  
    Where organizations aim to ensure faster and more effective delivery of hardware and software in the live environments, they usually try to agree close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision-making (see the supplier management practice guide for more information).
    
*   **Provision of software tools** Most software tools used for deployment management such as software configuration management, continuous testing, continuous delivery and continuous deployment tools are shared with other practices such as release management. However, the implementation and use of integrated CI/CD pipeline often starts with automating coding, building, testing and deployment activities. In this case, the stakeholders of the deployment management practice and the managers of the teams involved in release management, service validation testing and software deployment management should define requirements and interact with other teams and practices of the service provider to ensure that the required tools are procured, implemented, and used in an optimal way.
*   **Consulting and advisory** Specialized suppliers who have developed expertise in deployment management with capabilities in agile and DEVOPS practices and technologies can help establish and develop practices, adopt methods, deploy tools and techniques in automating the CI/CD pipeline along with relevant deployment management activities.

## 7. Capability assessment and development

#### 7\. 1 The practice capability levels

The practice success factors described in section 2.4 cannot be developed overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:

**Level 1** The practice is not well organized; it’s performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

**Level 2** The practice systematically achieves its purpose through a basic set of activities supported by specialized resources.

**Level 3** The practice is well defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

**Level 4** The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

**Level 5** The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level 2 to level 5. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to the practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well defined and organized.

![](Deployment%20Management%20ITIL%204%20Practice%20Guide/Deployment_management_Fig7_1.jpg)

Figure 7.1 Design of the capability criteria

This approach results in every practice having up to 30 capability criteria based on the practice PSFs and mapped to the four dimensions of service management. The number of criteria at each level differs; the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

Table 7.1 outlines the capability criteria that are defined in the ITIL maturity model for the deployment

management practice.

##### Table 7.1 Deployment management capability criteria

<table><tbody><tr><td><p><strong>PSF</strong></p></td><td><p><strong>Criterion</strong></p></td><td><p><strong>Dimension</strong></p></td><td><p><strong>Capability level</strong></p></td></tr><tr><td rowspan="5"><p>Establishing and maintaining effective approaches to the deployment of services and service components across the organization</p></td><td><p>An approach to deployment is defined and agreed for the organization</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>Responsibility for the approach to deployment is clearly defined</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>The deployment approach is integrated with other standards and approaches adopted by the organization</p></td><td><p>Value streams and processes</p></td><td><p>4</p></td></tr><tr><td><p>The effectiveness of the deployment approach is monitored and evaluated</p></td><td><p>Value streams and processes</p></td><td><p>4</p></td></tr><tr><td><p>The deployment approach is regularly reviewed and continually improved</p></td><td><p>Value streams and processes</p></td><td><p>5</p></td></tr><tr><td rowspan="9"><p>Ensuring the effective deployment of services and service components in the context of the organization’s value streams</p></td><td><p>New and changed services and service components are successfully deployed in the target environments</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>Deployment is automated where reasonably possible</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>Deployment information is tracked and managed in an integrated information system</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>Deployment includes required competencies and human resources</p></td><td><p>Organizations and people</p></td><td><p>3</p></td></tr><tr><td><p>Deployment includes dependencies and relationships with third parties where appropriate</p></td><td><p>Partners and suppliers</p></td><td><p>3</p></td></tr><tr><td><p>Deployment includes required workflows and procedures where appropriate</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>Deployment includes required technologies and information flows</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>Deployment is effectively integrated in the organization’s value streams</p></td><td><p>Value streams and processes</p></td><td><p>4</p></td></tr><tr><td><p>Deployment models, plans, and scenarios are regularly reviewed and continually improved</p></td><td><p>Value streams and processes</p></td><td><p>5</p></td></tr></tbody></table>

These capability criteria can be used by organizations for self-assessment and improvement of the practice.

#### 7.2 Capability self-assessment

A self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team in the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed.

1.  Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
2.  If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider’s employees.
3.  If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
4.  If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met; what is missing in the organization? Why? How can it affect the service consumer and the quality of the IT services? What can be done to meet the criteria that are currently missed?
5.  The same approach is applied at every next level; the practice is considered to be at the level, where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.

#### 7.3 Deployment management capability development

Management practices should support the achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at the capability level 5. A higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but it comes with a cost; cost of management, automation, and training, for example. To achieve optimal performance with sufficient level of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and Table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

![](Deployment%20Management%20ITIL%204%20Practice%20Guide/Deployment_management_Fig7_2.jpg)

Figure 7.2 The capability development steps and levels

##### Table 7.2 The deployment management capability development steps

<table><tbody><tr><td><p><strong>Capability level</strong></p></td><td><p><strong>Define, agree, and implement</strong></p></td><td><p><strong>Comment for deployment management</strong></p></td><td><p><strong>Chapter (for recommendations)</strong></p></td></tr><tr><td rowspan="5"><p>2</p></td><td><p>Purpose and objectives</p></td><td rowspan="2"><p>Key stakeholders, objectives</p></td><td><p>2.1</p></td></tr><tr><td><p>Scope</p></td><td><p>2.3</p></td></tr><tr><td><p>Processes and activities</p></td><td rowspan="3"><ul><li>Deployment models, workflows, roles and responsibilities</li><li>Automation and information exchange</li></ul></td><td><p>3</p></td></tr><tr><td><p>Roles and responsibilities</p></td><td><p>4</p></td></tr><tr><td><p>Tools and procedures</p></td><td><p>5</p></td></tr><tr><td rowspan="3"><p>3</p></td><td rowspan="3"><p>Dependencies and integration</p></td><td><p>Integration with other practices in the context of service value streams</p></td><td><p>3.2</p></td></tr><tr><td><p>Use of an integrated information system</p></td><td><p>5</p></td></tr><tr><td><p>Suppliers and other parties involved in deployment management</p></td><td><p>6</p></td></tr><tr><td><p>4</p></td><td><p>Measurement and reporting</p></td><td><p>Metrics</p></td><td><p>2.5</p></td></tr><tr><td><p>5</p></td><td><p>Continual improvement</p></td><td><p>Regular review of practice and the deployment management capability development</p></td><td><p>2.4, 2.5, 7</p></td></tr></tbody></table>

## 8. Recommendations for practice success

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:

*   focus on value
*   start where you are
*   progress iteratively with feedback
*   collaborate and promote visibility
*   think and work holistically
*   keep it simple and practical
*   optimize and automate.

In Table 8.1, recommendations for the success of the deployment management practice are linked to the relevant guiding principles.

##### Table 8.1 Recommendations for the success of deployment management

<table><tbody><tr><td><p><strong>Recommendations</strong></p></td><td><p><strong>Comments</strong></p></td><td><p><strong>ITIL guiding principles</strong></p></td></tr><tr><td><p>Automate the deployment pipeline for faster delivery and reduced errors</p></td><td><p>Automate release, service validation and testing and deployment management activities with the objective of delivering value faster. Remove manual steps in the CI/CD pipeline by identifying bottlenecks.</p></td><td><ul><li>Focus on value</li><li>Optimize and automate</li><li>Start where you are</li></ul></td></tr><tr><td><p>Integrate build, test, and deployment activities</p></td><td><p>CI/CD integration results in shortening the lead time to deliver services or features to the live environment, and enables enhanced collaboration between development, testing and deployment teams.</p></td><td><ul><li>Collaborate and promote visibility</li><li>Optimize and automate</li><li>Think and work holistically</li></ul></td></tr><tr><td><p>Continuous phased deployment with integrated testing</p></td><td><p>Focus on incremental deployment to manage deployments and scale accordingly.</p></td><td><ul><li>Progress iteratively with feedback</li><li>Keep it simple and practical</li></ul></td></tr><tr><td><p>Leverage Infrastructure as Code</p></td><td><p>Infrastructure as Code provides multiple benefits such as reducing costs, offering more scalability, and enhancing security. It provides automated process of installing and configuring software that enable reliable releases.</p></td><td><ul><li>Optimize and automate</li><li>Collaborate and promote visibility</li></ul></td></tr><tr><td><p>Demonstrate business value</p></td><td><p>Measure the practice and produce regular reports and dashboards for internal (within the service provider) and external (service consumer) stakeholders. Use dashboards for the reporting and regular reports for analysis and highlights.</p></td><td><ul><li>Focus on value</li><li>Collaborate and promote visibility</li></ul></td></tr></tbody></table>

## 9. Acknowledgements

PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following:

#### Authors

Vinod Kumar Agrasala, Roman Jouravlev, Konstantin Naryzhny.

#### Reviewers

Jon Hall, Anton Lykov, Samantha Robertson, Oleg Skrynnik.

#### 2023 Revision

Antonina Douannes, Adam Griffith, Roman Jouravlev, Kaimar Karu, Olga Masalina, Avinash Singh
