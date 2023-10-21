---
title: "Change enablement: ITIL 4 Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---


## 1. About this document

It is split into seven main sections, covering:

*   general information about the practice
*   the practice’s processes and activities and their roles in the service value chain
*   the organizations and people involved in the practice
*   the information and technology supporting the practice
*   considerations for partners and suppliers for the practice
*   information on assessing and developing the capability of the practice
*   recommendations for succeeding in the practice.

### 1.1 ITIL® 4 qualification scheme

Selected content of this document is examinable as a part of the following syllabus:

*   **ITIL Specialist** Create, Deliver and Support
*   **ITIL Specialist** High-velocity IT
*   **ITIL Specialist** Plan, Implement, and Control
*   **ITIL Practitioner** Change Enablement

Please refer to the respective syllabus for details.

## 2. General information

### 2.1 Purpose and description

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>The purpose of the change enablement practice is to maximize the number of successful service and product changes by ensuring that risks have been properly assessed, authorizing changes to proceed, and managing the change schedule.</p></td></tr></tbody></table>

The change enablement practice aims to ensure that changes to services and their components are controlled and that they meet the organization’s change-related needs. Authorized changes should enable the desired outcomes and meet the organization’s requirements regarding change throughput (the number of changes made and the speed of change realization) and risk management. Flexibility and agility permeate this practice because they are key aspects of a modern organization.

The change enablement practice incorporates three premises:

*   Changes are planned and realized in the context of value streams. The practice is integrated into value streams and ensures that changes are effective, safe, and timely in order to meet stakeholders’ expectations.
*   The practice does not aim to unify all the changes planned and carried out in an organization into one big picture: in a digital environment, where hundreds of changes may be happening simultaneously, this is neither possible nor required.
*   The practice should focus on balancing effectiveness, throughput, compliance, and risk control for all changes in the defined scope.

The change enablement practice has multiple benefits for both service providers and consumers.

Benefits for the service provider include:

*   improved visibility of end-to-end value streams
*   improved risk management capabilities
*   improved ability to respond to novel situations
*   improved security and compliance; and adherence to (audit) standards.

Benefits for the consumer include:

*   improved speed of moving from ideas to working solutions
*   improved speed in delivering ROI from changed services
*   reduced negative impact on services and service components
*   reduced negative impacts on users.

### 2.2 Terms and concepts

<table><tbody><tr><td><p><strong>Definition: Change</strong></p></td></tr><tr><td><p>The addition, modification, or removal of anything that could have a direct or indirect effect on services.</p></td></tr></tbody></table>

The change enablement practice helps to build and maintain an organizational environment that supports creating intended outputs and achieving intended outcomes. The practice aims to balance the different and sometimes conflicting requirements and expectations from various stakeholders by:

*   Making sure the expected value is understood from the viewpoint of and by all stakeholders, following the guiding principle ‘focus on value’, among others.
*   Considering the stakeholders’ interest in transparency and communications at the right level and in the right format when it comes to tracking the progress of value enabled by the changes, rather than just the technical details.
    
*   Tracking and responding to the unintended negative and positive effects of changes on stakeholders and their objectives that are not necessarily directly linked to the changes in question.
    
*   Keeping in mind the importance of those technical details for the success of the changes from the execution, measurement, and continual improvement point of view.
    

Changes that are implemented with technical precision, but which fail to enable the desired outcomes, fall short of expectations. Additionally, changes may have unintended outcomes, including negative impacts on users, service downtime, degradation, and destabilization. It might not be possible to avoid these outcomes, but it is important to control these within possibilities.

Changes are accomplished using various approaches and methodologies, each of which represents a different level of business risk. Changes in software are often made through frequent and regular deployment of new features and modifications. These changes can be delivered through continuous integration/continuous delivery (CI/CD), as recommended by the DevOps approach and practiced in various iterative/Agile methods and techniques. Changes in physical infrastructure may be slower, requiring a staged, ‘waterfall’ approach. Some changes of this type may be run as projects, using relevant project management techniques and controls.

In practice, however, few organizations are fully at one extreme or the other. Organizations have multiple value streams, most of which include changes. The change enablement practice must be adaptive to meet the needs of various approaches to change development.

#### 2.2.1 Complexity-based approach to changes

The change enablement practice should ensure a balance between change effectiveness, change throughput, and risk control. This means that the approaches to change planning authorization and ongoing control need to be selected carefully.

Changes are possible in all business situations, from business as usual to catastrophic (see Figure 2.1). Organizations should be able to make changes in any situation on this spectrum.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_Figure_2.1.png)

Figure 2.1 Changes are needed in all business situations

Business-as-usual situations are relatively predictable, with low levels of uncertainty. Catastrophic situations have the highest levels of uncertainty. Changes in any type of situation, however, have varying levels of complexity and predictability.

Changes can be standardized and automated where uncertainty is low, which helps to decrease the costs and accelerate the changes. Checklists, templates, and standardized ways of working can be used in these situations. Additionally, changes that have a highly constrained potential adverse impact (meaning that the risks are well-managed, services can be restored quickly in case of a failure, and there is minimal or no negative impact on customers) can be handled in a standardized manner. This is reflected in the definition of a standard change.

<table><tbody><tr><td><p><strong>Definition: Standard change</strong></p></td></tr><tr><td><p>A low-risk, pre-authorized change that is well understood and fully documented, and which can be implemented without needing additional authorization.</p></td></tr></tbody></table>

Examples of standard changes include:

*   fulfilment of a service request
*   standard incident resolutions
*   standard responses to disasters (as per DRP)
*   maintenance of infrastructure
*   routine testing of contingency measures
*   highly automated changes flowing through the CI/CD pipeline
*   routine software updates.

Organizations with an automated pipeline for CI/CD often automate most of the change enablement practice processes. Some steps (such as service request registration and approvals) may become practically invisible. Highly automated and fully documented processes can provide additional value for audit-related activities; rather than relying on manual entries and recollections when queried, every step of the process is already fully documented, including all decision points and exceptions. This provides an additional layer of transparency, saves time, and increases trust.

When the procedure for a standard change is created or modified, the procedure should be authorized and undergo a full risk assessment. This risk assessment does not need to be repeated for every change; it is needed only if the procedure itself undergoes another modification.

Although standard changes are usually associated with business-as-usual situations, there are multiple examples of standardization in situations with higher levels of uncertainty. These include:

*   standard incident resolutions
*   standard responses to disasters.

These may help organizations to decrease uncertainty in extreme situations by following a pre- defined routine and applying pre-tested solutions.

However, standard solutions may be unavailable or fail. These cases require a different approach to the change enablement practice.

When there is no effective standardized approach to a change, organizations usually attempt to plan, authorize, and control that change. They follow a process that includes collective expert assessment, authorization, and control. The process is performed by a group of people combining expertise and authority. These are ‘normal changes’, some of which are low risk.

<table><tbody><tr><td><p><strong>Definition: Normal change</strong></p></td></tr><tr><td><p>An unknown, medium, or high risk change that requires additional authorization for planning and control. Handling of normal changes often leverages existing change models for efficiency.</p></td></tr></tbody></table>

A normal change can be triggered by the creation (manual or automated) of a request for change (RFC).

<table><tbody><tr><td><p><strong>Definition: Request for change (RFC)</strong></p></td></tr><tr><td><p>A description of a proposed change used to initiate change enablement.</p></td></tr></tbody></table>

The change authority for these is usually someone who can make rapid decisions, often using automation to accelerate the change. When a normal change is high risk, the change authority might be the management board of the equivalent.

<table><tbody><tr><td><p><strong>Definition: Change authority</strong></p></td></tr><tr><td><p>A person or group responsible for authorizing a change.</p></td></tr></tbody></table>

Change models provide guidance for handling normal changes. Organizations usually develop change models that determine procedures and roles for the assessment, authorization, and ongoing control of changes based on their type.

<table><tbody><tr><td><p><strong>Definition: Change model</strong></p></td></tr><tr><td><p>A repeatable approach to the management of a particular type of change.</p></td></tr></tbody></table>

Change models can be defined based on factors such as:

*   systems/technologies to be changed
*   scale of change
*   locations/territories where the change occurs
*   customers affected by the change

*   regulatory requirements affecting the change.

The models may determine an approach to the change enablement practice in all four dimensions of service management which is shown in Table 2.1.

#### Table 2.1 Examples of factors that may be determined by change models in the four dimensions of service management

<table><tbody><tr><td><p><strong>Value streams and processes</strong></p></td><td><p><strong>Organizations and people</strong></p></td><td><p><strong>Information and technology</strong></p></td><td><p><strong>Partners and suppliers</strong></p></td></tr><tr><td><ul><li>Change process and procedures, including the level of formalization</li><li>Level and form of the change authority</li><li>Acceptance criteria</li></ul></td><td><ul><li>Competencies needed</li><li>Organizational solutions (such as change advisory board, or peer review)</li><li>Accountability</li><li>Responsibilities</li><li>Delegation rules</li></ul></td><td><ul><li>Information requirements</li><li>Tooling Automation</li></ul></td><td><p>Involvement of third parties to the change planning and realization</p><p>Communications with partners and suppliers</p></td></tr></tbody></table>

In addition, organizations need to consider a change’s risk level. An organization may, for example, decide to limit a change’s potential risk by deconstructing it into iterations. Each iteration of the change is then below an agreed risk-level threshold, introducing limited and manageable risk. Generally, smaller changes also cost less and are easier to control. Based on these considerations, many organizations limit the size of individual changes, particularly of software and other digital resources. This also links back to the concepts of standard and normal changes, as efficient risk management for changes can reduce the number of normal changes by creating conditions for these to be addressed as standard changes.

Change models may be helpful when managing uncertainty in complex situations. For example, a process determined by the change model may include the safe-to-fail testing of several hypotheses before one or some of the solutions are implemented. This may help to address incidents and disasters where there is no clarity around what changes are needed. Although this approach is more common for unstable situations, it is also applicable to business-as-usual situations.

The change enablement practice should ensure that changes are implemented effectively, safely, and promptly in emergency situations. Changes that help to correct emergency situations are commonly known as emergency changes.

<table><tbody><tr><td><p><strong>Definition: Emergency change</strong></p></td></tr><tr><td><p>A change that must be introduced as soon as possible.</p></td></tr></tbody></table>

Although some emergency scenarios may be predicted and provided with a standard solution (including standard changes required), many situations do not have a ready solution or the time for safe-to-fail testing. Change models for emergency changes often include bypassed or delayed procedures, such as change request registration or updating of the change schedule. They may also determine a dedicated change authority of high power and availability, together with other special arrangements. The aim is to accelerate changes while keeping risks at an acceptable level.

Two important considerations regarding emergency changes:

*   ‘Emergency’ does not mean ‘no rules or control’. Emergency changes can be standardized and automated. This can accelerate them without compromising control. Emergency does not always mean completely unpredictable and unknown.
*   Some emergency changes do deal with unpredictable and unknown situations. They may need fast implementation of the best available solution without sufficient information or time for testing. This applies to situations where the cost of delay is equal to or higher than the risks associated with unsuccessful change.

Figure 2.2 and table 2.2 outline the key characteristics of different types of changes.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_fig_2.2.png)

Figure 2.2 Types of changes

#### Table 2.2 Characteristics of types of changes

<table><colgroup data-width="776"><col><col><col><col></colgroup><tbody><tr><td><p><strong>Change type/Characteristics</strong></p></td><td><p><strong>Standard change</strong></p></td><td><p><strong>Normal change</strong></p></td><td><p><strong>Emergency change</strong></p></td></tr><tr><td><p><strong>Best suited for</strong></p></td><td><p>Routine, low-risk changes</p></td><td><p>Unknown, medium, or high risk changes</p></td><td><p>Unscheduled changes that need to be implemented quickly</p></td></tr><tr><td><p><strong>Authorization</strong></p></td><td><p>Usually pre-authorized</p></td><td><p>Usually according to change models</p></td><td><p>Usually according to change models; might require higher-level sign-off</p></td></tr><tr><td><p><strong>Change authority</strong></p></td><td><p>Pre-determined</p></td><td><p>Pre-determined, based on a change model, or ad hoc</p></td><td><p>Pre-determined, based on a change model, or ad hoc</p></td></tr><tr><td><p><strong>Tolerance for deviation from agreed procedures</strong></p></td><td><p>Very low</p></td><td><p>Medium</p></td><td><p>High</p></td></tr><tr><td><p><strong>Automation potential</strong></p></td><td><p>Very high</p></td><td><p>Medium</p></td><td><p>Medium</p></td></tr><tr><td><p><strong>Risk of unexpected outcomes</strong></p></td><td><p>Low</p></td><td><p>Medium</p></td><td><p>High</p></td></tr><tr><td><p><strong>Uncertainty</strong></p></td><td><p>Low</p></td><td><p>Medium</p></td><td><p>High</p></td></tr><tr><td><p><strong>Can be managed as a project</strong></p></td><td><p>Usually not needed</p></td><td><p>Yes</p></td><td><p>Usually not possible</p></td></tr><tr><td><p><strong>Examples</strong></p></td><td><ul><li>Replacing a user's laptop of work phone</li><li>An automated software change through the CI/CD pipeline</li></ul></td><td><ul><li>A significant server-side update of hardware or software</li><li>Replacing the internet service provider for the office</li></ul></td><td><ul><li>An emergency security update applied to business software</li><li>Temporarily shutting down a service causing damage to the business or customers</li></ul></td></tr></tbody></table>

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>The change enablement practice should include approaches to situations of different complexity and predictability. These approaches may include:</p><ul><li>standard changes</li><li>changes planned and controlled based on expert analysis of the situation</li><li>changes planned based on multiple safe-to-fail experiments</li><li>emergency changes implemented without sufficient assessment and planning.</li></ul><p>The first three approaches are applicable in all types of situations in business, from business as usual to catastrophic disasters. The last approach applies to chaotic situations where the cost of delay is higher than the cost of a wrong action.</p><p>Standardization and automation can be hugely beneficial for this practice, because they allow for significantly accelerated change while retaining sufficient control. This is the recommended method of change enablement for digital resources, products, and services.</p><p>Decreasing the size of changes can increase the effectiveness and throughput of the practice while decreasing the level of risk. Size should be an important consideration for organizations’ change models.</p></td></tr></tbody></table>

#### 2.2.2 Change definition and scope

The change enablement practice supports all value streams and can be used with any other practice because they can all initiate changes to products and services. However, organizations usually limit the application of the change enablement practice to a finite number of change types based on what is being changed and the context in which the changes are occurring.

Typically, the practice is used for changes to the information and technology dimension of the organization’s products and services. Other practices may significantly contribute to the enablement of changes in the three other dimensions of service management. Respective changes, although formally covered by the change definition, may be excluded from the scope of the change enablement practice (see Table 2.3 for examples of changes).

Organizations define which changes, at which level of control, should be addressed by the change enablement practice. This is based on several considerations, usually including:

*   **Level of risk** Risks that are addressed and introduced by the change should be considered to determine the level of control.
*   **Costs and losses** Costs of the change and losses addressed by the change should be evaluated to determine the level of control.
*   **Scope of configuration and asset control** Registered configuration items and assets usually require control of modifications. The change enablement practice provides means for this.
*   **Internal and external regulatory requirements** The organization may be obliged to comply with explicit change-related requirements.
*   **Need for visibility of the change impact** In the environment where components are dynamically interconnected, the visibility of planned and ongoing changes and change progress is important.

#### Table 2.3 Examples of changes in the four dimensions of service management

<table><tbody><tr><td><p><strong>Dimension of service management</strong></p></td><td><p><strong>Areas subject to potential change</strong></p></td><td><p><strong>Scoping considerations</strong></p></td></tr><tr><td><p>Information and technology</p></td><td><ul><li>Hardware and software</li><li>Service architecture</li><li>Service design</li><li>Technical and user documentation</li></ul></td><td><p>Usually addressed by the change enablement practice in conjunction with the project management, service design, and architecture management practices</p></td></tr><tr><td rowspan="3"><p>Organizations and people</p></td><td><ul><li>Organizational structure</li><li>Roles and responsibilities</li></ul></td><td><p>Usually addressed by the organizational change management and project management practices</p></td></tr><tr><td colspan="2"><p>Culture and rules of work behaviour</p></td></tr><tr><td><p>Personal competencies</p></td><td><p>Usually addressed by the workforce and talent management practice</p></td></tr><tr><td><p>Value streams and processes</p></td><td><ul><li>Value streams architecture</li><li>Work processes and procedures</li><li>Process documentation</li></ul></td><td><p>May be addressed by the change enablement and/or other practices</p></td></tr><tr><td><p>Partners and suppliers</p></td><td><ul><li>Service dependencies on third parties at the architecture level</li><li>Contractual arrangements with third parties (new suppliers, change of responsibilities, for example)</li><li>Contract and other documents (version changes, prolongation, for example)</li></ul></td><td><p>May be addressed by the change enablement practice, in conjunction with the supplier management and/or other practices</p></td></tr></tbody></table>

Based on these and other considerations, organizations decide whether modifications to products and services should be treated as changes and, if so, whether they should be considered as minor, medium, or major. The change enablement practice usually includes different approaches to changes of different scales which are normally detailed in the change models.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_figure_2.3_(1).png)

Figure 2.3 Different scales of changes

Some major changes can be run as programmes and projects, with outcomes dependent on a complex interconnected web of constraints, dependencies, and outputs. Each step of such a project or programme can potentially be viewed as a separate change (medium or minor, in that case) and the success of the programme is linked to the success of individual smaller changes. In these situations, every sub-change might require separate authorization, as while the major change has already been authorized, the ‘why’ that depends on the proposed specific steps needs to be assessed for suitability, and the best alternatives chosen.

At the same time, a major change can also be run in an iterative manner with frequent deliveries, where each iteration is viewed as an individual change. Product management often utilizes such an approach and change authorization is typically delegated to the teams doing the work, or can be pre-authorized thanks to efficient and effective higher-level control mechanisms.

In addition to what are seen as formal or more structured change initiatives, there are also changes of different sizes and levels of impact carried out by all teams across the organization and handled as business-as-usual (BAU) work. Not every change is managed as a programme, project, or as product development work. Change models are often used here for the authorization and execution of such changes.

It is important to keep in mind that changes are not something extraordinary. Change is part of the work, and supporting changes is a capability all teams need to develop. Often it is possible to plan and design many steps of upcoming changes, but sometimes the reaction needs to be swift and there is no time to analyse options or run experiments to find the best solutions. The better the organization manages changes in general, figures out the best approach to authorization and delegation, and improves change enablement across the organization, the easier it becomes to react to unexpected situations with confidence.

#### 2.2.3 Automation of the change enablement practice and its effect on visibility

When changes are made to software and other digital resources, controls that ensure change success may be automated, including change scheduling, integrity control, version control, compatibility control, and many others. Automation increases the throughput and keeps the risks associated with changes to an acceptable level, particularly when combined with the decrease in size of the individual changes (see chapter 5 and the practice guides for software development and management, release management, and deployment management for more information on this).

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_figure_2.4_(1).png)

Figure 2.4 A comparison of manual and automated changes

The full scope of planned and ongoing changes may be hard to oversee across an organization when change enablement is highly automated. It becomes difficult to identify what change is being made where. This is due to the high level of complexity of the controlled environments.

Organizations should embrace this complexity and adapt to the higher level of uncertainty while ensuring that the level of control is sufficient.

Again, the primary means of achieving sufficient levels of control are by decreasing the change size, standardizing, and automating.

### 2.3 Scope

The scope of the change enablement practice includes:

*   planning changes to controlled environments in the organization
*   planning change models and change standardization
*   planning individual change workflows, activities, and controls
*   scheduling and coordinating all ongoing changes
*   controlling the progress of changes from initiation to completion
*   communicating change plans and progress to relevant stakeholders
*   assessing change success, including outputs, outcomes, efficiency, risks, and costs.

There are several activities and areas of responsibility not included in the change enablement practice, although they are still closely related to changes. These are listed in Table 2.3, along with references to the practice guides in which they can be found. It is important to remember that the ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

#### Table 2.4 Activities related to the change enablement practice that are described in other practice guides

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Change initiation</p></td><td><p>All other practices</p></td></tr><tr><td><p>Change realization</p></td><td><ul><li>Architecture management</li><li>Deployment management</li><li>Infrastructure and platform management</li><li>IT asset management</li><li>Release management</li></ul><ul><li>Service catalogue management</li><li>Service configuration management</li><li>Service design</li><li>Service level management</li><li>Software development and management</li><li>Supplier management</li><li>Workforce and talent management</li></ul></td></tr><tr><td><p>Change risks assessment and control</p></td><td><p>Risk management</p></td></tr><tr><td><p>Costs control, financial evaluation of changes</p></td><td><p>Service financial management</p></td></tr><tr><td><p>Management of projects</p></td><td><p>Project management</p></td></tr><tr><td><p>Management of organizational changes</p></td><td><p>Organizational change management</p></td></tr><tr><td><p>Testing</p></td><td><p>Service validation and testing</p></td></tr></tbody></table>

### 2.4 Practice success factors

<table><tbody><tr><td><p><strong>Definition: Practice success factor</strong></p></td></tr><tr><td><p>A complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity; it includes components from all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The change enablement practice includes the following PSFs:

*   ensuring that changes are realized in a timely and effective manner
*   minimizing the negative impacts of changes
*   ensuring stakeholder satisfaction
*   meeting change-related governance and compliance requirements.

#### 2.4.1 Ensuring that changes are realized in a timely and effective manner

The focus of the change enablement practice is the effectiveness and timeliness of the changes.

Change effectiveness can be measured by the levels of outputs and outcomes of the change. In the context of change outputs, effective change can be described as ‘a change that successfully transforms resources from the initial state to the pre-defined target state’. However, the target state is rarely the goal of the change; the target state enables an outcome. At the outcome level, effective change can be described as ‘a change that successfully contributed to the achievement of the desired pre-defined outcomes’.

It is important that both perspectives are considered and included in the change planning, ongoing control, and assessment. The definition and assessment of outputs can be used at the level of individual changes; outcomes are usually enabled by multiple changes and other initiatives. The difference is extremely important for ongoing management and control at the level of teams involved in realization of the changes. These teams should be aware of both the content and the context of the changes they realize. Teams’ performances should be assessed based on their contributions to the outcomes that are within their responsibilities.

Effectiveness may include various characteristics of quality defined for the resources and services in the scope of the change. These may include security, performance, conformance to regulations, and usability.

The timeliness of change is a measure of meeting the expectations and requirements of the change initiator for the time of change completion. Timeliness of change can be measured against the approved change plan, but meeting the change initiator’s needs is the main concern. This should be an important consideration when changes are being planned, controlled, and assessed.

Sometimes failure to meet timeliness requirements makes a change ineffective, useless, or harmful.

Effectiveness and timeliness of changes can be improved by:

*   decreasing the size of individual changes
*   standardizing and automating changes
*   including a feedback loop in every iteration of change planning and realization
*   capturing expectations and communicating the progress of changes
*   effectively integrating multiple ITIL practices for changes in the context of value streams.

#### 2.4.2 Minimizing the negative impact of changes

Changes are sources of disruption and risk. The change enablement practice is expected to keep risks to an acceptable level. In a simple, slow-changing environment, this could be achieved by imposing controls on every step of the change, introducing more stakeholders in the authorization step, and creating a contingency plan for every occasion. However, these controls would lead to ineffective and delayed change realization, which is unacceptable in today’s complex environment. Additionally, the supposed simplicity might be an illusion and the environment could be significantly more fragile than it seems at a first glance.

To balance the timeliness, effectiveness, and risk level of change, organizations define change models where manual and automated controls are combined to standardize changes, continually reduce change size, and monitor and assess the impact of changes on the infrastructure, services, and stakeholders. Minimization of risks is achieved by reducing the impact of every individual change, enabling a quick automated return to the previous stable state in case of change failure, and automated configuration management.

#### 2.4.3 Ensuring stakeholder satisfaction

Many stakeholders have an interest in changes, including:

*   service provider teams
*   users
*   customers
*   sponsors of service provision
*   sponsors of service consumption
*   suppliers and partners.

The change enablement practice ensures that stakeholders are identified and that their expectations are captured, considered, and met as appropriate. This is done in conjunction with the relationship management, risk management, and business analysis practices, among others. The change enablement practice mostly focuses on the continual monitoring of stakeholder engagement and satisfaction during change realization and after the change is complete. Ongoing communication, status updates, and feedback collection are important components of satisfaction management.

#### 2.4.4 Meeting change-related governance and compliance requirements

Many change-related governance and compliance requirements affect the change enablement practice in general as well as individual changes. It is important that organizations capture them, understand them, and ensure that they are met. The change enablement practice supports this by:

*   including required controls in change models, processes, and procedures
*   providing required information
*   initiating improvement to prevent or correct non-compliance.

### 2.5 Key metrics

Key metrics for the change enablement practice are mapped to its PSFs. They can be used as KPIs in the context of value streams in order to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.5.

The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

#### Table 2.5 Key metrics for change enablement

<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Ensuring that changes are realized in a timely and effective manner</p></td><td><ul><li>Aggregated timeliness processing index (TPI)<em>a </em>over the period</li><li>Average time of change realization per change model</li><li>Change initiators’ satisfaction with change outcomes</li><li>Change initiators’ satisfaction with change timeliness</li><li>Change success/acceptance rate over period</li><li>TPI for individual changes</li></ul></td></tr><tr><td><p>Minimizing the negative impact of changes</p></td><td><ul><li>Business impact of change-related incidents</li><li>Impact of changes identified as sources of problems/errors&nbsp;</li><li>Number and duration of change-related incidents</li></ul></td></tr><tr><td><p>Ensuring stakeholder satisfaction</p></td><td><ul><li>Stakeholder satisfaction with the procedures and communications for the change enablement practice</li><li>Stakeholder satisfaction with realization of individual changes</li></ul></td></tr><tr><td><p>Meeting change-related governance and compliance requirements</p></td><td><ul><li>Compliance with formally stated requirements, according to audit reports</li><li>Number and criticality of change-related audit findings and non- compliances</li><li>Number and impact of change-related compliance incidents</li></ul></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the change enablement practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

## 3. Value Streams and processes

### 3.1 Processes

Each practice may include processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><p><strong>Definition: Process</strong></p></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

Change enablement activities form two processes:

*   **Change enablement planning and optimization** This process is focused on the planning and continual improvement of the change enablement practice, change models, and standard change procedures.
*   **Change lifecycle management** This process facilitates the change, and manages it through registration, assessment, authorization, execution, and closure.

#### 3.1.1 Change enablement planning and optimization

This process is focused on the planning and continual improvement of the change enablement practice, change models, and standard change procedures. It is triggered by change reviews highlighting inefficiencies and other improvement opportunities. It can also be performed regularly depending on the effectiveness of the existing models and procedures.

It is important to remember that this practice should be under constant strategic review as it has high potential to enable or hinder continual improvement of all practices and all value streams.

This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

#### Table 3.1 Inputs, activities, and outputs of the change enablement planning and optimization process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Change records</li><li>Current change models and standard change procedures</li><li>Policies and regulatory requirements</li><li>Configuration information</li></ul><ul><li>IT asset information</li><li>Service catalogue</li><li>SLAs with consumers and suppliers/partners</li><li>Financial guidelines and constraints</li><li>Risk information</li><li>Capacity and performance information</li><li>Continuity policies and plans</li></ul></td><td><ul><li>Change enablement initiation</li><li>Change review analysis</li><li>Change model improvement initiation</li><li>Change model update communication</li></ul></td><td><ul><li>Defined roles and responsibilities for the change enablement practic</li><li>Change review analysis report Improvement initiatives</li><li>Change requests</li><li>Updated change models</li><li>Updated standard change procedures</li></ul></td></tr></tbody></table>

Figure 3.1 shows a workflow diagram of the process.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_figure_3.1.png)

Figure 3.1 Workflow of the change enablement planning and optimization process

Table 3.2 provides examples of the process activities.

#### Table 3.2 Activities of the change enablement planning and optimization process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Example</strong></p></td></tr><tr><td><p>Change enablement initiation</p></td><td><p>The team responsible for the introduction or formalization of the existing service management practices documents the initial version of the following:</p><ul><li>the role of change enablement in value streams</li><li><p>existing change enablement related processed and procedures</p></li><li><p>practice roles and responsibilities</p></li><li><p>the levels and responsibilities within change authorities</p></li><li><p>the criteria of change categorization and prioritization</p></li><li><p>change models.</p></li></ul><p>A dedicated change manager is also appointed as part of this activity.</p></td></tr><tr><td><p>Change review and planning</p></td><td><p>The change manager, together with service owners and other relevant stakeholders, performs a review of the available change enablement processes, procedures, and models. If applicable, they also review change reports and especially outstanding changes over the period.</p><p>They identify opportunities for change model and standard change procedures optimization, including standardization of new change types.</p></td></tr><tr><td><p>Change model and procedure improvement initiation</p></td><td><p>The change manager or change coordinator registers improvement initiatives to be processed with the involvement of the continual improvement practice or initiates a change request (if change models and procedures are included in the scope of the change enablement practice).</p></td></tr><tr><td><p>Change model and procedure update communication</p></td><td><p>If the change model is successfully updated, it is communicated to the relevant stakeholders, together with updated procedures and other relevant documentation. This is usually done by the change manager and/or the service or resource owner.</p></td></tr></tbody></table>

Change enablement activities are performed by the service provider. They may involve customers, suppliers, and partners. These activities are also supported (and sometimes fully or largely automated) by tools and technologies. All are described in the following sections.

#### 3.1.2 Change lifecycle management

This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

#### Table 3.2 Inputs, activities, and outputs of the change lifecycle management process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Change requests</li><li>Change models and standard change procedures</li><li>Policies and regulatory requirements</li><li>Configuration information IT asset information Service catalogue</li><li>Service level agreements (SLAs) with consumers and suppliers/partners</li></ul><ul><li>Financial guidelines and constraints</li><li>Risk information</li><li>Capacity and performance information</li><li>Continuity policies and plans</li><li>Information security policies and plans</li></ul></td><td><ul><li>Change registration</li><li>Change assessment</li><li>Change authorization</li><li>Change planning</li><li>Change realization control</li><li>Change review and closure</li></ul></td><td><ul><li>Change records</li><li>Change schedule</li><li>Change review reports</li><li>Changed resources and services</li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_fig_3.2.png)

Figure 3.2 Workflow of the change lifecycle management process

The process may vary depending on the change model. Table 3.4 provides examples of the activities in two change models.

The change model examples in Table 3.4 are just two of many options illustrating different models. Organizations should embrace the diversity of architectures and approaches to management to ensure flexibility of services and to meet stakeholder expectations.

#### Table 3.4 Activities of the change lifecycle management process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Normal changes; manual management</strong></p></td><td><p><strong>Standard software changes; highly automated management</strong></p></td></tr><tr><td><p>Change registration</p></td><td><ul><li>A change request is received from a change initiator.</li><li>Based on the change request, a change record is created by the service owner, resource owner, change manager, or change coordinator.</li><li>The change initiator is sent a confirmation of the change request receipt.</li></ul></td><td><p>Change requests are accumulated in the product or service backlog. The product development team decides which requests will be taken into development.</p></td></tr><tr><td><p>Change assessment</p></td><td><ul><li>The service owner, resource owner, change manager, or change coordinator performs an assessment of the change impact, associated risks, and required resources. If needed, other subject matter experts may be involved.</li><li>Assessment information is added to the change record.</li></ul></td><td><p>The product development team decides on the best way to proceed with the change.</p></td></tr><tr><td><p>Change authorization</p></td><td><ul><li>The change authority who has been assigned in line with the change model reviews the change record and provides authorization. If the change is not authorized, it is sent for review and closure.</li><li>Additional assessments may be required, so the change record is returned for assessment together with the rationale for this.</li></ul></td><td><p>Change authorization is not needed because standard changes are likely to be pre-authorized, where it has been agreed for this model that changes are authorized by taking them into development via backlog assessment.</p></td></tr><tr><td><p>Change planning</p></td><td><ul><li>Authorized changes are planned in line with the change model. According to the model, roles with relevant expertise and authority are involved in the planning. Resulting plans may&nbsp;require additional authorization, depending on the change model.</li><li>This activity is orchestrated by the change coordinator or change manager.</li></ul></td><td><p>The planning phase is minimized: smaller work size allows the delegation of planning to the development teams and reduces the time needed for this.</p></td></tr><tr><td><p>Change realization control</p></td><td><p>Planned changes to the resources are performed by internal and external specialist teams. These may include, among others:</p><ul><li>software developers</li><li>infrastructure engineers</li><li>contract/supplier managers</li><li>testers</li><li>user support specialists.</li></ul><p>Manual and automated control actions are performed by the change manager or other agreed role(s). The change manager ensures that deviations are detected and corrected.</p></td><td><p>Planned changes to the resources are performed by internal and external specialist teams.</p><p>Change realization control is almost fully automated, including:</p><ul><li>validation and testing</li><li>configuration control and verification</li><li>asset control</li><li>version control</li><li>back up and restoration.</li></ul></td></tr><tr><td><p>Change review and closure</p></td><td><p>After the change is complete, or if it fails to be completed in time, an agreed authority reviews the change. Among others, one or more of the following roles may be involved:</p><ul><li>change manager</li><li><p>service owner</p></li><li><p>change initiator</p></li><li><p>resource owner.</p></li></ul><p>The change can be formally closed before or after the review, depending on the change model.</p></td><td><p>Change review is not performed for individual changes unless they are unsuccessful according to the change realization control data. Changes are closed automatically after pre-agreed tests confirm they were successful.</p></td></tr></tbody></table>

### 3.2 Value streams contribution

#### 3.2.1 Service value streams

To perform certain tasks or respond to particular situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario. Once designed, value streams should be subject to continual improvement.

<table><tbody><tr><td><p><strong>Definition: Value stream</strong></p></td></tr><tr><td><p>A series of steps an organization undertakes to create and deliver products and services to consumers.</p></td></tr></tbody></table>

In practice, however, many organizations come to the use of the value stream concept after having worked for a while (sometimes for years) without the value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the ‘As Is’ situation and the de-facto flows of work, and to analyse them in order to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding the existing value streams is critical to improving an organization’s performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services. Combined, the organizations’ value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations follow best practice recommendations for various service management practices, such as incident management, change enablement, software development, and many others. However, the practices are often adopted and organized in a siloed, isolated manner, just as they are presented in the service management bodies of knowledge. In reality, a flow of work required to create or restore value, for a customer or another stakeholder, is almost never limited to one practice.

#### 3.2.2 Change enablement in service value streams

The change enablement practice supports most service value streams as it governs the changes around or within a specific value stream. At each step of each service value stream there might be a need to request a change to an aspect of services provided. Also, each of these steps might be impacted by changes to services and service components upstream, downstream, or above the value stream in question. The practice plays an important role in service value streams involving changes. These are outlined in Table 3.5.

#### Table 3.5 The role of the change enablement practice in service value streams

<table><tbody><tr><td><p><strong>Service value stream</strong></p></td><td><p><strong>Role of the change enablement practice</strong></p></td></tr><tr><td><p>Incident resolution</p></td><td><p>Planning and coordination of changes required to solve an incident and restore normal service operations.</p></td></tr><tr><td><p>Request fulfilment</p></td><td><p>Planning and coordination of changes required to fulfil a request model</p></td></tr><tr><td><p>Product and service continual improvement</p></td><td><p>Planning and coordination of changes required to realize an approved improvement initiative</p></td></tr><tr><td><p>Delivery of new and changed services</p></td><td><p>Planning and coordination of changes required to fulfil an agreed product or service development plan</p></td></tr><tr><td><p>Ongoing operations and maintenance</p></td><td><p>Planning and coordination of changes required to fulfil an agreed maintenance of the live systems and components.</p></td></tr></tbody></table>

Change requests can originate from any team, team member, customer, user, practice, process, or service, depending on the procedures in place and the roles assigned to different parties involved. Change models should be created for all such situations, where possible. However, it is not common for service users to be able to submit change requests directly; their needs are usually handled as service requests and managed by the service request management practice. Customers, on the other hand, usually do have the right to submit change requests. Figure 3.3 illustrates how requests for change originate from different service value streams.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_fig_3.3.png)

Figure 3.3 Sources of changes

Depending on the scope and nature of the change the change realization control activity of the change lifecycle management process may cover pre-deployment tasks, as well as deployment and release tasks. These tasks may involve various management practices but are coordinated as part of the change lifecycle. Figures 3.4 and 3.5 illustrate the involvement of the change realization control process in multiple value streams initiated by various triggers.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_fig_3.4.png)

Figure 3.4 Change lifecycle tasks

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_fig_3.5.png)

Figure 3.5 The change lifecycle management process is included in multiple value streams

Attention should be given to workforce planning. The change assessment and change authorization steps of the lifecycle management process, when invoked, can involve roles in the organization that do not typically participate in a particular service value stream. This needs to be considered for situations such as emergency changes, as well as changes that follow an agreed change plan and schedule.

The agreed change schedule is one of the inputs for teams to plan their work and also to highlight resource and priority conflicts. Depending on how work is managed, this could be an input to the programme/project plan or an input to the team backlog (for instance, for Scrum or Kanban methods).

##### 3.2.2.1 Request fulfilment value stream

The change enablement practice supports the request fulfilment value stream by providing change models and automation tools for standard changes underpinning the value stream. This includes, among other aspects, pre-authorization and standardization of procedures for quicker request fulfilment.

##### 3.2.2.2 Service improvement value stream

The service improvement value stream follows the whole lifecycle of a change from ideation to post-release confirmation. This value stream focuses on outcomes. The value stream invokes the deployment management and release management practices that are responsible for the related tasks, and returns to change enablement once the change has been released to confirm its success. This value stream can be initiated by an RFC from any service, process, or team and should result in outcomes or outputs as defined by the RFC submitter.

Success can be measured directly (for example expected outputs, adherence to plans, effectiveness of risk management, and so on) and indirectly (such as assessing the outcomes related to the change). While a single change can be easily tracked in terms of outputs, the assessment of outcomes might require looking at several related changes in combination. It is also important to remember that achieving the expected outcomes might not be in any one team’s hands, therefore the metrics applied need to be built accordingly.

##### 3.2.2.3 Product improvement value stream

The product improvement value stream usually focuses on software/code and does not require any non-code-based changes to hardware, networks, or procedures. This value stream focuses on outputs. Agile practices that are partially or fully automated using a CI/CD pipeline make use of this value stream. Changes that are developed and deployed by software engineers are often pre-authorized at a high level (for example, by customers and the product lead) and also on a more detailed level (for example, by a product owner or product manager). The developer pulls tasks from their personal backlog, or preferably that of the team, starts working on these, and verifies their quality with the help of (automated) quality gates that control for integration compatibility and for live use suitability. The role of change enablement is mostly to support the automation aspects of this service value stream.

#### 3.2.3 Analysing a service value stream

##### 3.2.3.1 The key steps of a service value stream analysis

The following are some simple and practical recommendations for service value stream analysis and mapping.

**1\. Identify the scope of the value stream analysis**

It can be mapped to a particular product or service or applied to most or all of them. Similarly, service value streams may differ for different consumers.

**2\. Define the purpose of the value stream from the business standpoint**

Make sure the stakeholder’s concerns are clearly understood, since they are the ones defining value. In the case of change enablement, this is usually the customer who has requested the change, however there will also be other interested parties.

**3\. Do the service value stream walk**

Walk through or directly experience the steps and information flow as they go in practice (consider the Lean technique of Gemba walk):

**a. Identify the workflow steps**

**b. Collect data as you walk**

**c. Evaluate the workflow steps**

Typically, the criteria for evaluation are:

*   value for the stakeholder (does the step add value for the business stakeholder?)
*   effectiveness or performance (is the step performed well?)
*   availability (are required resources available to execute the step?)
*   capacity (are required resources enough?)
*   flexibility (are the required resources interchangeable within the step?).

**d. Map the activities and the information flows**

In an ideal situation, the flow goes smoothly without delays and pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

**e. Create and review the timeline and resource level**

Map out process times and lead times for resources and workload through the workflow steps.

**4\. Reflect on the value stream map (VSM)**

Identify factors that might not have been entirely apparent at first. The information collected is used at this step to find the waste.

**5\. Create a ‘to be’ VSM**

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

**6\. Using the ‘to be’ VSM, plan improvements**

Refer to the continual improvement practice guide for a practical improvement model.

##### 3.2.3.2 Change enablement considerations in a service value stream analysis

As stated earlier, the change enablement practice supports many other practices either by enabling continual improvement activities (from planning to realization) or by providing mechanisms for following through with individual changes. The following is a list of recommendations to consider when analysing service value streams through the lens of change enablement.

● At step (1), keep in mind that the change enablement practice has multiple layers that need to be tailored specifically for different parts or levels in the organization. Change enablement provides assistance with:

*   the continual improvement practice across the organization,
*   major change initiatives (often managed as portfolios, programmes, and projects; please see the project management practice guide for more details),
*   changes to practices and value streams,
*   changes to processes and procedures,
*   changes to individual products and services,
*   changes to service components or configuration items.

It is important to ensure the practice does not increase unnecessary bureaucracy in any of the service value streams. The focus should remain on enabling change, not making it unnecessarily difficult.

● At step (2) the teams’ different needs from across the organization need to be assessed. What is the purpose of the changes for them, what types of controls should be in place, which risks need to be managed, and which impediments need to be removed. ‘Enablement’ is the key focus throughout, but in some cases this can be achieved with added speed, and in others with added (manual) controls. Every organizational layer has its own requirements that need to be addressed, and value can be co-created only when the practice is tailored to those specific needs. Additionally, it is common that in larger and/or highly regulated organizations there are different ‘zones’ in place, whereby the high-security zones put significantly different demands on the change enablement practice compared to ‘standard’ zones.

● At step (3), observe what happens with ideas for potential changes. Are there mechanisms in place to submit RFCs or notify the teams accountable through other means? Many of the inefficiencies in processes and procedures, as well as risks and common pitfalls are most visible at the level where the work is done. Are the teams allowed to highlight these and are they empowered to initiate and carry out the necessary changes? Are the requirements for authorization fit for purpose? What is the level of disintermediation in the organization; are unnecessary delays caused by the fact that decision-making is too far removed from where the work is done and problems are identified? Are the teams aware of the upstream and downstream dependencies between their work and that of other teams; do they know how their changes impact other teams? Is there enough flexibility to carry out emergency changes when needed or are the procedures too rigid? Do the teams take ownership of continual improvement related changes or do they expect to be told what good looks like?

● At step (4), and based on the answers to the questions above, focus on change authorization delays and other types of waste (either procedural or technical). It is very common for changes to be delayed not at the development, deployment, and release stages, but in the decision-making and approval stages (which in some organizations is called ‘on the business side’). Speeding up the deployment from a month to a week is obviously useful, but has little effect in the context of a value stream when the decision-making process itself takes many months to complete.

● At step (5) focus on the end-to-end view of changes and include all teams and roles involved from ideation to execution. Make sure the suggested approach to change enablement matches the requirements of individual value streams; do not try to design a single one-size-fits-all approach to change enablement. Propose and then agree on universal standards, (for example constraints and principles, which can be used for all types of changes regardless of their size and nature). This helps every value stream to make the most efficient use of the change enablement practice.

● At step (6) use the change enablement practice (with the principles, constraints, rules, processes, procedures, previous lessons learned, and so on) in combination with the continual improvement practice to plan for the selected changes in a consistent yet flexible manner.

## 4. Organizations and people

### 4.1 Roles, competencies, and responsibilities

The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended.

Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

#### Table 4.1 Competency codes and profiles

<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p>L</p></td><td><p><strong>Leader </strong>Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p>А</p></td><td><p><strong>Administrator </strong>Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p>C</p></td><td><p><strong>Coordinator/communicator </strong>Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p>М</p></td><td><p><strong>Methods and techniques expert </strong>Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p>Т</p></td><td><p><strong>Technical expert </strong>Providing technical (IT) expertise and conducting expertise- based assignments</p></td></tr></tbody></table>

Three roles specific to the change enablement practice may be found in organizations: change manager, change coordinator and change authority. These roles are often introduced in organizations with a large number of changes processed manually.

  

#### 4.1.1 Change manager and change coordinator roles

The change manager is typically responsible for:

*   the initial processing and verification of change requests
*   allocating changes to appropriate teams for assessment and authorization, according to the change model
*   in some instances, communicating decisions of change authorities to affected parties
*   monitoring and reviewing the activities of the teams that build and test changes
*   publishing the change schedule and ensuring that it is available as needed
*   conducting regular and ad hoc service review analyses; and initiating improvements to the practice, the change models, and the standard change procedures
*   developing the organization’s expertise in the processes and methods of the change enablement practice.

In some cases, organizations introduce an additional role of change coordinator that has similar responsibilities but a more limited scope (specific types of changes, or territory, or part of the organization).

The competency profile for these roles is MTCLA, though the importance of each of these competencies varies from activity to activity. Examples of the roles which can be involved in change enablement activities are listed in Table 4.2, together with the associated competency profiles and required skills.

  

#### 4.1.2 Change authority role

Changes require resources and introduce risks. This sometimes leads to organizations establishing complicated, and often bureaucratic, systems of change authorization, with formal committees that meet regularly to overview and authorize changes accumulated over the period. These are known as change advisory boards (CABs), and they often become bottlenecks for the organization’s value streams. They introduce delays and limit the throughput of the change enablement practice.

It is important to make sure that changes are authorized based on resource, cost, and priority considerations. This does not generally need to be a bureaucratic procedure. Change models should define the requirements and procedures for authorization, delegating the role of change authority to the appropriate level, such as development teams, technical experts, or service and product owners.

The change authority is responsible for the assessment and authorization of a change during its lifecycle (from initiation to completion). Depending on the change model, assessment and authorization may be done manually, automatically, or skipped for specific types of change.

#### 4.1.3 Other roles involved in change enablement activities

Examples of other roles involved in change enablement activities are listed in Table 4.2.  

#### Table 4.2 Examples of roles with responsibility for change enablement activities  

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Responsible roles</strong></p></td><td><p><strong>Competency profile</strong></p></td><td><p><strong>Specific skills</strong></p></td></tr><tr><td colspan="3"><p><span>Change enablement planning and optimization process</span></p></td><td></td></tr><tr><td><p>Change enablement initiation</p></td><td><ul><li>Change manager</li><li>Customer representative</li><li>Change coordinator</li><li>Product development team</li><li>Risk and compliance expert</li><li>Technical expert</li></ul></td><td><p>LACMT</p></td><td><ul><li>Good understanding of business priorities</li><li>Good understanding of dependencies in value streams, products, and services</li><li>Business impact analysis</li><li>Risk analysis</li><li>Communication skills</li></ul></td></tr><tr><td><p>Change review and planning</p></td><td><ul><li>Change coordinator</li><li>Change manager</li><li>Product development team</li><li>Product owner</li><li>Resource owner</li><li>Risk and compliance expert</li><li>Service owner</li></ul></td><td><p>TC</p></td><td><ul><li>Good knowledge of the products, including their architecture and configuration</li><li>Understanding of change models</li><li>Business impact analysis</li><li>Risk analysis</li></ul></td></tr><tr><td><p>Change model and procedure improvement initiation</p></td><td><ul><li>Change manager</li><li>Product development team</li><li>Product owner</li><li>Risk and compliance expert</li><li>Service owner</li></ul></td><td><p>TMA</p></td><td><ul><li>Good knowledge of the products, including their architecture and configuration</li><li>Understanding of change models</li><li>Business impact analysis</li><li>Risk analysis</li></ul></td></tr><tr><td><p>Change model and procedure update communication</p></td><td><ul><li>Change manager</li><li>Product owner</li><li>Service owner</li></ul></td><td><p>CT</p></td><td><p>Understanding of change models</p><p>Communication skills</p></td></tr><tr><td colspan="4"><p><span>Change lifecycle management process</span></p></td></tr></tbody></table>

<table><tbody><tr><td><p>Change registration</p></td><td><ul><li>Change coordinator</li><li>Change manager</li><li>Product development team</li><li>Product owner</li><li>Resource owner</li><li>Service owner</li></ul></td><td><p>TA</p></td><td><p>Understanding of change models and registration procedures</p></td></tr><tr><td><p>Change assessment</p></td><td><ul><li>Change coordinato</li><li>Change manager</li><li>Product development team</li><li>Product owner</li><li>Resource owner</li><li>Risk and compliance expert</li><li>Service owner</li><li>Technical expert</li></ul></td><td><p>TC</p></td><td><ul><li>Good knowledge of the products, including their architecture and configuration</li><li>Business impact analysis</li><li>Risk analysis</li></ul></td></tr><tr><td><p>Change authorization</p></td><td><ul><li>Change coordinator</li><li>Change manager</li><li>Customer representative</li><li>Product development team</li><li>Product owner</li><li>Resource owner</li><li>Risk and compliance expert</li><li>Service owner</li><li>Technical expert</li></ul></td><td><p>CTM</p></td><td><ul><li>Good knowledge of the products, including their architecture and configuration</li><li>Understanding of change models</li><li>Business impact analysis</li></ul></td></tr><tr><td><p>Change planning&nbsp;</p></td><td><ul><li>Change coordinator</li><li>Change manager</li><li>Product development team</li><li>Product owner</li><li>Resource owner</li><li>Service owner<br></li></ul></td><td><p>TAC</p></td><td><ul><li>Good knowledge of the products, including their architecture and configuration</li><li>Understanding of change models</li></ul></td></tr><tr><td><p>Change realization control</p></td><td><ul><li>Change coordinator</li><li>Change manager</li><li>Product development team</li><li>Product owner</li><li>Resource owner</li><li>Service owner</li></ul></td><td><p>ATC</p></td><td><ul><li>Good knowledge of the products, including their architecture and configuration</li><li>Understanding of change models</li></ul></td></tr><tr><td><p>Change review and closure</p></td><td><ul><li>Change coordinator</li><li>Change manager</li><li>Customer representative</li><li>Product development team</li><li>Product owner</li><li>Resource owner</li><li>Service owner</li></ul></td><td><p>TCA</p></td><td><ul><li>Good knowledge of the products, including their architecture and configuration</li><li>Business impact analysis</li></ul></td></tr></tbody></table>

  

### 4.2 Organizational structures and teams

As the change enablement practice supports different types of changes in many service value streams, various organizational structures of varying levels of formality can be used for it.

The trend towards more agile ways of working throughout the organization, not just in the domain of IT, has pushed the change enablement activities to be automated where possible. With the decrease of manual processing of changes, there is also less need for formalized structures for change enablement. Individuals and teams are increasingly more empowered to make decisions within their sphere of influence, and ad-hoc collaboration between teams and roles is encouraged whenever the changes’ impact is wider and needs assessment from several teams.

That said, an organization might have the need for formalized structures or might already have some in place, even if not performing as expected. One of these structures is the Change Advisory Board (CAB) which often morphs into a Change Approval Board in larger organizations. The initial purpose of the CAB was to assist those planning changes in ensuring that all stakeholders could provide input and be kept up to date with progress of the change or changes being planned and carried out.

Where the dependencies between teams have been minimized and these teams can work in an autonomous manner, following their own customer-value focused schedule, the need for such an advisory body is minimal. There are, of course, major changes that have an impact on several teams and should be analysed and scheduled by all those teams, but organizations should seek to minimize such instances. The fewer dependencies there are, the faster the organization can move, and the quicker value is realised.

If the organization already has a CAB in place, its effectiveness and efficiency should be thoroughly reviewed and any processes and procedures that are justified with ‘because we have always done it like this’ should be heavily scrutinized. The purpose of a CAB is to enable the planning and implementation of changes, not to create additional bureaucracy, slow things down, or complicate matters.

Even if a CAB does not exist or there is no reason to create such a permanent body (and, with modern work practices, the demand is decreasing) there might be a need to put together temporary teams of stakeholders to assess and authorize a change, oversee its deployment and release, and analyse the results. These teams should be given very clear responsibilities and accountabilities, and be fully empowered, and all the lessons learned should be shared with other teams, including for the purpose of minimizing the need for such multi-team change authorities where possible.

The structure of change authorities should also be reviewed to ensure a decentralized approach to change approvals. The closer the authority sits to the work being done and decisions made, the better. Amassing lots of decisions to higher-level authorities has few, if any upsides. It might contribute to the illusion of control, but that provides a false sense of security, slows things down, and destroys people’s desire to engage and collaborate. Empowerment is key.

Another aspect of organizational structures supporting the change enablement practice is the way non-trivial changes are managed in the organization. There could be additional practices in place, for instance project management (crucially, together with programme and portfolio management) that manage the delivery of outputs and the achievement of expected outcomes (see the project management practice guide for more details on project teams).

Change enablement needs to be linked to the continual improvement practice and the accountability and responsibility of all the teams involved should be made very clear. If there is no dedicated continual improvement team or role in place, the change enablement practice can take ownership of managing both the RFC and the more high-level ideas for potential improvements, involving the relevant stakeholders when needed.

It is important to avoid conflict between the change enablement, continual improvement, and project management practices, in terms of accountability, responsibility, resources, (delegated) rights, and constraints. The change enablement practice is there to make all of the related processes and procedures more efficient and focused on higher value, not to push everything into one pipeline where the cadence of the slowest moving part becomes the default.

The organizational structures accountable for change enablement, deployment management, and release management should be clarified and documented. The teams involved in these three practices across all value streams are very likely to need to work closely together, and the potential overlap between different roles in these practices increases in sync with the level of automation.

## 5. Information and technology

### 5.1 Information exchange

The effectiveness of the change enablement practice is based on the quality of the information used. This includes, but is not limited to, information about:

*   customers and users
*   services and their architecture and design
*   partners and suppliers, including contract and SLA information on the services they provide
*   policies and requirements which regulate service provision
*   proposed changes
*   expected benefits for the consumers and the organization
*   user stories
*   estimated time and cost of change realization
*   regulations affecting the change
*   lessons learned from similar changes in the past
*   past and ongoing changes
*   stakeholder satisfaction with the practice.

This information may take various forms. The key inputs and outputs of the change enablement practice are listed in chapter 3.

### 5.2 Automation and tooling

In most cases, the work of the change enablement practice can significantly benefit from automation. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to, the full automation of activities where technology solutions remove the need for human intervention. Table 5.1 provides a list of the key automation supporting the practice and their most common application.

#### Table 5.1 Automation solutions for change enablement practice

<table><tbody><tr><td><p><strong>Automation tools</strong></p></td><td><p><strong>Application in change enablement</strong></p></td></tr><tr><td><p>Workflow management and collaboration</p></td><td><ul><li>Support of the change models workflows</li><li>Communication and collaboration between teams</li><li>Integration of the practice’s activities in the service value streams</li></ul></td></tr><tr><td><p>Analysis and reporting</p></td><td><p>Review of records and creation of reports for individual changes as well as for periodic assessment of change models and the practice</p></td></tr><tr><td><p>Work planning and prioritization</p></td><td><p>Planning, prioritization, and assignment of tasks to teams and team members, visualisation and optimization of workload, identification and prevention of resource conflicts</p></td></tr><tr><td><p>Orchestration</p></td><td><p>Integration of multiple workflow management and collaboration tools for better visibility and closer collaboration</p></td></tr><tr><td><p>Knowledge management</p></td><td><p>Capturing and sharing of lessons learned, guidelines, and good practices</p></td></tr></tbody></table>

Detailed descriptions of how these tools support the practice's activities are outlined in Table 5.2.

#### Table 5.2 Details of automation of the change enablement activities

<table><tbody><tr><td><p><strong>Process activity</strong></p></td><td><p><strong>Means of&nbsp;</strong><strong>automation</strong></p></td><td><p><strong>Key functionality</strong></p></td><td><p><strong>Impact on the&nbsp;</strong><strong>effectiveness of the practice</strong></p></td></tr><tr><td colspan="4"><p><span>Change enablement planning and optimization process</span></p></td></tr><tr><td><p>Change enablement initiation</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Analysis and reporting tools</li><li>Work planning and prioritization tools</li><li>Orchestration systems</li><li>Knowledge management tools</li></ul></td><td><p>Analysing existing procedures, resource and role planning for processes and procedures, documenting and communicating formalized procedures</p></td><td><p>Low to medium, especially for pattern analysis and discovery</p></td></tr><tr><td><p>Change review and planning</p></td><td><p>Analysis and reporting tools</p></td><td><p>Remote collaboration, change data analysis</p></td><td><p>Medium to high, especially for high volumes of changes</p></td></tr><tr><td><p>Change model and procedure improvement initiation</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Work planning and prioritization tools</li></ul></td><td><p>Formal registration of the initiatives</p></td><td><p>Low to medium</p></td></tr><tr><td><p>Change model and procedure update communication</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Orchestration systems</li><li>Knowledge management tools</li></ul></td><td><p>Communicating updates to the affected teams</p></td><td><p>Medium to high, especially when the organization is large and the number of updates is high</p></td></tr><tr><td colspan="4"><p><span>Change lifecycle management process</span></p></td></tr><tr><td><p>Change registration</p></td><td><ul><li><span>Workflow management and collaboration tools</span><span></span></li><li>Work planning and prioritization tools<span></span></li><li>Orchestration systems</li></ul></td><td><p>Enabling and controlling workflow for changes; prioritization of backlog and workflow management; workflow visualization</p></td><td><p>Very high, especially for large volumes of changes</p></td></tr><tr><td><p>Change assessment</p></td><td><ul><li>Analysis and reporting tools</li><li>Knowledge management tools</li></ul></td><td><p>Formalization and structuring of the assessment, providing more accurate and solid data for authorization</p></td><td><p>Medium to high, especially for processing complex changes manually</p></td></tr><tr><td><p>Change authorization</p></td><td><p>Workflow management and collaboration tools</p></td><td><p>Quick and traceable remote approval of changes</p></td><td><p>High, especially for delegated change authority of high velocity changes</p></td></tr><tr><td><p>Change planning</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Work planning and prioritization tools</li></ul></td><td><p>Visualization of the planned and ongoing changes shared for all stakeholders; planning of automated standard changes</p></td><td><p>Very high, especially when many changes are being realized in parallel</p></td></tr><tr><td><p>Change realization control</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Orchestration systems</li></ul></td><td><p>Visualization and reporting for up-to- date views on the ongoing changes</p></td><td><p>Very high</p></td></tr><tr><td><p>Change review and closure</p></td><td><ul><li>W<span>orkflow management and collaboration tools</span></li><li>K<span>nowledge management tools</span></li></ul></td><td><p>Remote review and discussions; traceable formal closure of changes</p></td><td><p>Medium to high, especially when regulations require traceable records</p></td></tr></tbody></table>

Change enablement can benefit greatly from improved automation throughout the workflows and from improved use of (existing) data for weighing pre-release options and analysing post-release outputs and outcomes.

Workflow management and collaboration tools can be used in all steps of the change lifecycle management process and the change optimization process. These tools help keep track of the progress of the change as the related tasks move through and between different teams. They also support decision-making processes (for example, for change authorization) by aggregating and highlighting relevant information and making the authorization of changes a seamless process even for those stakeholders otherwise far removed from the change’s more technical activities. Additionally, these tools help to track authorization progress and highlight any delays.

Analysis and reporting tools are most useful for the change assessment and change review analysis process steps. These help to identify dependencies, and analyse the potential impact of changes and the required resources. Third parties can be involved in the analysis work as subject matter experts. The goal of using tools for this step is to gather and communicate enough data to be able to make good quality decisions about change authorization.

Work planning and prioritization tools can be leveraged according to the appropriate change model for standard, normal, and emergency changes. Once the change has been authorized, it is possible that the act of carrying out the change could have an impact on the authorization. For example, if the circumstances have changed or if the planning work has highlighted additional resource requirements, then procedures should be followed for seeking a confirmation of the authorization.

Orchestration systems are particularly useful for coordinating all the work required from different teams across the organization and from various external partners that were identified in the change planning step. While some changes only relate to software or hardware, more complex changes can involve multiple aspects at the same time, from base infrastructure to workstations and personal devices, from configuration script updates to major implementations or version updates, or from procedure updates to significant changes to value streams. It is likely that bigger organizations will have multiple workflow management tools in place for different teams; service management tools are different from software development, deployment, and release tools; infrastructure management tools are different from personal device management tools, and so on. Orchestration systems need to bring all that work together. Additionally, the handovers from change enablement to deployment management and release management should be managed in an easily trackable manner. While smaller changes could be managed as tasks on a Kanban board or items in a team’s Scrum backlog, major changes could be managed as, for example, projects and that information needs to be made available outside those tools at an appropriate level of detail. Visualization with drill-down capabilities is key for the orchestration systems.

Knowledge management tools are used throughout the service lifecycle as well as for change enablement improvement related tasks. Specifically, these are used for change review and closure, and change model update communication. Product, service, and configuration information needs to be updated, processes and procedures potentially changed, and change models and risk matrices brought up to date.

#### 5.2.1 Recommendation for the automation of change enablement

The following recommendations can help when applying automation to change enablement:

*   **Automate the value stream** Changes can originate from any practice, process, or service, and changes need to be deployed and released. When analysing the change enablement supported value streams for automation opportunities, map the inputs and outputs of related practices and their processes as well. This includes, but is not limited to deployment management, release management, problem management, service request management, project management, service configuration management, and continual improvement.
*   **Allow different workflows for different types of changes** Firstly: minor, medium, and major changes can all have different workflows starting with change registration and ending with change review and closure. Secondly: standard, normal, and emergency changes can also all have different workflows. And thirdly: changes affecting a service configuration item, the service itself, a practice, a process, or a procedure can all have different workflows. Some types of changes can have multiple authorization stages that require manual input, whereas other changes can be automated together with their deployment and release throughout all steps.
    
*   **Do not overcomplicate the workflows and business rules** While visibility of the entirety of the workflow is necessary for some roles, it is not important for many others. When different roles are pulled into the change enablement workflows and related service value streams, provide them with enough information so that they can fulfil their role, but do not overburden them with, for example, all authorization steps or change analysis workflows. Present the stakeholders whose input is required with concise information and clear requests when involving them.
    
*   **Pay attention to measurement and reporting from the beginning** The success criteria for the change, either through assessing the outputs or the outcomes, need to be defined and clearly communicated to stakeholders before the work on the change begins. Various aspects of workflow and value stream efficiency and effectiveness can and should be measured for, among other things, input into the change optimization process. When analysing value streams, the steps taken before the change is registered should also be measured for unnecessary delays or other types of waste, among other aspects. Workflow management and collaboration tools can provide vast amounts of data for change enablement metrics.
    
*   **Communications are important** While the reason for the change should be understood by all stakeholders, the progress of the change can also be important for stakeholders to identify any delays or deviations and take necessary action. Make sure that stakeholders are properly identified, and stakeholder management plans have been created for all non-trivial changes that have the chance of a medium or higher impact on people’s work.
    
*   **Pay attention to integrations** As the realization of different types of changes can be managed in different tools (for example, project management software for those changes managed as projects, automated release and deployment tools for software changes, Kanban boards for product-related changes, and so on) it might be difficult to have good visibility of the progress of work. Many tools come with integration capabilities that allow aggregating relevant information for different management purposes without requiring all teams to use the same software tools for managing their work.
    

## 6. Partners and suppliers

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services. These are often provided by third parties (see section 2.4 of *ITIL® Foundation: ITIL 4 Edition* for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the practice guides for service design, architecture management, and supplier management. Information about dependencies on third-party services is used in the change enablement practice at all steps of the change lifecycle management process. The information is also often used in the change optimization process.

### 6.1 Dependencies on third parties

RFCs can come from many sources from both inside and outside of the organization, and procedures should be created and communicated to support the initiation of RFCs by suppliers and other third parties, where applicable. When putting these procedures in place, it is useful to consider the following questions:

*   What is the easiest way for the customer to submit an RFC?
*   What does the workflow look like for service request based standard changes?
*   How do the customers submit their change requests for products, services, or procedures?
*   Will they be forced to use specialized software or can they submit it via regular channels (for example, by email)?
*   Can partners also submit RFCs in an efficient manner?
*   How are third parties connected to continual improvement activities and what are the feedback flows to ensure that submitted ideas and requests are properly responded to?

The organization may depend on various partners to assess the proposed change before it can be authorized or rejected. Again, procedures should be put in place to ensure this step doesn’t introduce delays and other types of waste.

Change authorization is often done within the organization, but where there are dependencies on third parties, they may also be involved with this step, especially when significant resources or contractual modifications are required, or when dealing with complex changes with unknown impacts. An organization usually cannot take unknown risks on another organization’s behalf.

In change planning, it is important to understand what is required in order to proceed. Consideration should be given to whether the change is actually viable, and to what resources are required for the change and which systems it will impact.

Change models should define how third parties are involved in change realization and how the organization ensures the flow of changes. This depends on the architecture and design solutions for products, services, and value streams. The optimization of the change models supporting these solutions, however, involves the change enablement practice. Often, after the correct change model has been selected, further consideration of third- party dependencies is needed during change assessment, planning, authorization, realization control, and review. Where contracts with customers and vendors can impose constraints on changes, it may be useful to include standard changes and, in general, change models, into contracts together with clearly defined costs and approval procedures for any proposed changes.

Where organizations aim to ensure the fast and effective flow of changes, they usually try to agree to close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision-making. All parties in such relationships should aim for mutual transparency and visibility of the changes that may affect the other parties (see the supplier management practice guide for more information).

### 6.2 Support from third parties

When designing the change enablement practice or planning for a specific change, it is not enough to look only at internal teams and processes. Depending on the technical architecture used for the organization’s products and services, there can exist several dependencies on the policies and procedures of third parties. Aspects like change schedules, potential resource conflicts, interdependencies between products (via APIs or similar), dependencies on platform software (for example database engines or development frameworks), and tooling compatibility should be assessed.

Similar to internal collaboration, where one team, product or service cannot ‘run ahead’ too far, the capability of suppliers needs to be considered in areas such as supporting agile development or leveraging a highly automated deployment and release environment. Historically for many organizations, the challenge has been the opposite, in that the suppliers have had more dynamic and agile practices and procedures, and their customers needed to adopt these to realise the benefits they are paying for. Within the modern technology market, an organization kicking off their digital transformation and adopting a product or service approach to co-creating value might run into problems with enterprise software providers who cannot keep up.

Another aspect of enterprise software has to do with cloud-based solutions. Previously, both minor and major updates to desktop software programs were planned and executed by the organization, following their own schedules. Nowadays, updates to cloud-based solutions can be released by the supplier automatically many times per day, and this schedule is unlikely to be under the organization’s control. If heavy dependencies are built on certain aspects of the cloud-based solutions, the supplier should be informed.

There also many additional technical layers managed by the cloud service providers that are invisible for their customers. Operating systems, networking configuration, database engines, runtime frameworks, etc. are often managed (that is configured, maintained, updated) fully by the supplier. Examples of these models include Infrastructure as a Service (IaaS), Platform as a Service (PaaS), and Software as a Service (SaaS).

## 7. Capability assessment and development

### 7.1 The practice capability levels

The practice success factors described in section 2.4 cannot be developed overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:

**Level 1** The practice is not well organized; it’s performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

**Level 2** The practice systematically achieves its purpose through a basic set of activities supported by specialised resources.

**Level 3** The practice is well defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

**Level 4** The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

**Level 5** The practice is continually improving organizational capabilities associated with its purpose. For each practice, the ITIL maturity model defines criteria for every capability level from level 2 to level 5. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to the practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well defined and organized.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_fig_7.1.png)

Figure 7.1 Design of the capability criteria

This approach results in every practice having up to 30 capability criteria based on the practice PSFs and mapped to the four dimensions of service management. The number of criteria at each level differs; the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

Table 7.1 outlines the capability criteria that are defined in the ITIL maturity model for the change enablement practice.

#### Table 7.1 Change enablement capability criteria

<table><tbody><tr><td><p><strong>PSF</strong></p></td><td><p><strong>Criterion</strong></p></td><td><p><strong>Dimension</strong></p></td><td><p><strong>Capability level</strong></p></td></tr><tr><td rowspan="12"><p>Ensuring that changes are realized in a timely and effective manner</p></td><td><p>Changes are usually realized in time and achieve the intended results</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>Change planning and management covers affected information and technology, where relevant</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>Change planning and management covers affected competencies, human resources, and organizational structures, where relevant</p></td><td><p>Organizations and people</p></td><td><p>3</p></td></tr><tr><td><p>Change planning and management covers affected third-party services and dependencies, where relevant</p></td><td><p>Partners and suppliers</p></td><td><p>3</p></td></tr><tr><td><p>Change planning and management covers affected value streams and processes, where relevant</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>Change processing and implementation are standardized, where relevant</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>Change processing and implementation are automated, where relevant</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>Change processing and implementation are integrated into the relevant value streams</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>Information about change processing and implementation is tracked and managed in an integrated information system</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>Change processing and implementation are adjusted based on ongoing feedback from affected parties</p></td><td><p>Value streams and processes</p></td><td><p>4</p></td></tr><tr><td><p>The timeliness and effectiveness of the changes are measured and reported</p></td><td><p>Value streams and processes</p></td><td><p>4</p></td></tr><tr><td><p>The timeliness and effectiveness of the changes are regularly reported and continually improved</p></td><td><p>Value streams and processes</p></td><td><p>5</p></td></tr><tr><td rowspan="7"><p>Minimizing the negative impacts of changes</p></td><td><p>The negative impact of the changes is tracked and analysed</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>When detected, the negative impact of changes is mitigated</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>The negative impact of changes is usually prevented or mitigated to an acceptable level</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>The changes are analysed to identify and prevent possible negative impact</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>Information about the anticipated and actual negative impact of changes is tracked and managed in an integrated information system</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>The minimization of the negative impact of the changes is measured and reported</p></td><td><p>Value streams and processes</p></td><td><p>4</p></td></tr><tr><td><p>The minimization of the negative impact of the changes is regularly reviewed and continually improved</p></td><td><p>Value streams and processes</p></td><td><p>5</p></td></tr><tr><td rowspan="6"><p>Ensuring stakeholder satisfaction</p></td><td><p>The stakeholders are usually satisfied with change processing and the results</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>The stakeholder satisfaction with the changes is measured and reported</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>The collection and processing of the stakeholder satisfaction data is automated, where relevant</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>The stakeholder satisfaction information is tracked and managed using an integrated information system</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>Stakeholder satisfaction with the changes is assessed within the context of the relevant value streams</p></td><td><p>Value streams and processes</p></td><td><p>4</p></td></tr><tr><td><p>The stakeholder satisfaction information is used to continually improve the processing and implementation of changes</p></td><td><p>Value streams and processes</p></td><td><p>5</p></td></tr><tr><td rowspan="9"><p>Meeting change-related governance and compliance requirements</p></td><td><p>The changes usually meet the applicable governance and compliance requirements</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>The applicable change-related governance and compliance requirements are identified and analysed where relevant</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>The management of the change-related governance and compliance requirements is aligned with the management of the governance and compliance for other practices, where relevant</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>The analysis of the change-related governance and compliance requirements includes affected information and technology</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>The analysis of the change-related governance and compliance requirements includes affected competencies, organizational structures, and people</p></td><td><p>Organizations and people</p></td><td><p>3</p></td></tr><tr><td><p>The analysis of the change-related governance and compliance requirements includes affected third-party services and dependencies</p></td><td><p>Partners and suppliers</p></td><td><p>3</p></td></tr><tr><td><p>The analysis of the change-related governance and compliance requirements includes affected value streams and processes</p></td><td><p>Value streams and processes</p></td><td><p>3</p></td></tr><tr><td><p>The compliance to the relevant requirements is measured and reported</p></td><td><p>Value streams and processes</p></td><td><p>4</p></td></tr><tr><td><p>The compliance to the relevant requirements is regularly reviewed and continually improved</p></td><td><p>Value streams and processes</p></td><td><p>5</p></td></tr></tbody></table>

These capability criteria can be used by organizations for self-assessment and improvement of the practice.

### 7.2 Capability self-assessment

A self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team in the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed.

1.  Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
2.  If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider’s employees.
3.  If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
4.  If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met; what is missing in the organization? Why? How can it affect the service consumer and the quality of the IT services? What can be done to meet the criteria that are currently missed?
5.  The same approach is applied at every next level; the practice is considered to be at the level, where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.

### 7.3 Change enablement capability development

Management practices should support the achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at the capability level 5. A higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but t comes with a cost; cost of management, automation, and training, for example. To achieve optimal performance with sufficient level of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and Table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

![](Change%20enablement%20ITIL%204%20Practice%20Guide/Change_enablement_-_fig_7.2_(1).png)

Figure 7.2 The capability development steps and levels

#### Table 7.2 The change enablement capability development steps

<table><tbody><tr><td><p><strong>Capability level</strong></p></td><td><p><strong>Define, agree, and implement</strong></p></td><td><p><strong>Comment for change enablement</strong></p></td><td><p><strong>Chapter (for recommendations)</strong></p></td></tr><tr><td rowspan="5"><p>2</p></td><td><p>Purpose and objectives</p></td><td rowspan="2"><ul><li>Key stakeholder groups and their requirements</li><li>Definition of change</li><li>Types of changes</li></ul></td><td><p>2.1</p></td></tr><tr><td><p>Scope</p></td><td><p>2.3</p></td></tr><tr><td><p>Processes and activities</p></td><td rowspan="3"><ul><li>Workflows</li><li>Change models, roles and responsibilities</li><li>Automation and information exchange</li></ul></td><td><p>3</p></td></tr><tr><td><p>Roles and responsibilities</p></td><td><p>4</p></td></tr><tr><td><p>Tools and procedures</p></td><td><p>5</p></td></tr><tr><td rowspan="3"><p>3</p></td><td rowspan="3"><p>Dependencies and integration</p></td><td><p>Integration in the service value streams</p></td><td><p>3.2</p></td></tr><tr><td><p>U<span>se of an integrated information system</span></p></td><td><p>5</p></td></tr><tr><td><p>S<span>uppliers and other parties involved in change enablement</span></p></td><td><p>6</p></td></tr><tr><td><p>4</p></td><td><p>Measurement and reporting</p></td><td><p>Metrics</p></td><td><p>2.5</p></td></tr><tr><td><p>5</p></td><td><p>Continual improvement</p></td><td><p>Regular review of the practice and change enablement capability development</p></td><td><p>2.4, 2.5, 7</p></td></tr></tbody></table>

## 8. Recommendations for practice success

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the practice guides, organizations should always follow the ITIL guiding principles:

*   focus on value
*   start where you are
*   progress iteratively with feedback
*   collaborate and promote visibility
*   think and work holistically
*   keep it simple and practical
*   optimize and automate.

In Table 8.1, recommendations for the success of the change enablement practice are linked to the relevant guiding principles affecting the approach the most. All guiding principles should be considered at all times and their value is best realized through their combination.

#### Table 8.1 Recommendations for the success of change enablement

<table><tbody><tr><td><p><strong>Recommendation</strong></p></td><td><p><strong>Comments</strong></p></td><td><p><strong>ITIL guiding principles</strong></p></td></tr><tr><td><p>Make sure the practice enables changes, rather than restricts them</p></td><td><p>Different types of changes (standard, normal, emergency) with different level of impact (small, medium, and minor) and risk require different workflows to effectively and efficiently support the service workstreams. The change enablement practice needs to adjust to different circumstances and avoid a one-size-fits-all approach.</p></td><td><ul><li>Focus on value</li><li>Think and work holistically</li></ul></td></tr><tr><td><p>Make sure the reasons for changes are understood by all stakeholders</p></td><td><p>Not all changes are straightforward, or appear as such for stakeholders. Even in instances of smaller changes, make sure the reason for the change is clearly stated, communicated, and understood.</p></td><td><ul><li>Focus on value</li><li>Collaborate and promote visibility</li></ul></td></tr><tr><td><p>Make sure the success criteria are understood by all stakeholders</p></td><td><p>Especially pertinent in case of major or complex changes where outputs can be easily confused for outcomes and the fact of a change carried out is confused with the success of that change in terms of business value.</p></td><td><ul><li>Focus on value</li><li>Think and work holistically</li><li>Collaborate and promote visibility</li></ul></td></tr><tr><td><p>Delegate authority</p></td><td><p>Change enablement requires many different types and levels of change authority, with different levels of formality and different numbers of stakeholders involved. The closer the change authority is to the work performed, the more visibility they have and the more effective and efficient the practice is.</p></td><td><ul><li>Focus on value</li><li>Think and work holistically</li><li>Collaborate and promote visibility</li><li>Keep it simple and practical</li></ul></td></tr><tr><td><p>Leverage automation capabilities as much as possible</p></td><td><p>Once the change has been authorized, any (further) delays should be avoided. There can be a lot of back-and-forth between teams as they complete their change related tasks. Automated tooling can help with workflow optimization and to minimize waste by, for example, presenting only relevant information for decision-making, visualizing the progress of changes, and preauthorizing steps based on clear criteria.</p></td><td><ul><li>Optimize and automate</li><li>Keep it simple and practical</li></ul></td></tr><tr><td><p>Clarify dependencies and design efficient integrations</p></td><td><p>Changes often have dependencies to other changes, the BAU work done in directly or indirectly impacted teams, and higher-level decision-making processes (for example, for business priorities, funding, and other resource allocation). Organizational, procedural, and technical dependencies should be clarified, which is also important for risk management, and integrations, both technical and procedural, should be designed with simplicity, efficiency, and value in mind.</p></td><td><ul><li>Focus on value</li><li>Think and work holistically</li><li>Collaborate and promote visibility</li><li>Keep it simple and practical</li></ul></td></tr><tr><td><p>Do not unnecessarily increase the complexity of changes</p></td><td><p>Inefficient and misguided risk management can sometimes become a serious hindrance to value co-creation. The idea of a CAB as a change authority approving all changes might sound appealing when changes have gone awry in the past, but this is highly unlikely to serve its stated purpose. Remove any handovers, authorizations and approval stages that are not strictly required. Involve all relevant stakeholders but don’t burden all potential stakeholders.</p></td><td><ul><li>Keep it simple and practical</li><li>Focus on value</li><li>Optimize and automate</li></ul></td></tr><tr><td><p>Avoid or remove irrelevant bureaucracy, add sought-after efficiency step by step</p></td><td><p>Past mishaps with changes might feel like an opportunity for a major redesign, introducing new layers for approvals, controls, and assessments. In many cases, the smarter way of approaching improvement is by removing inefficiencies in place step-by-step, learning from experience and adjusting to the changing context. New ways of working, including workflows, processes, and procedures cannot always be designed upfront; they emerge from tweaks to existing practices.</p></td><td><ul><li>Start where you are</li><li>Progress iteratively with feedback</li><li>Keep it simple and practical</li></ul></td></tr><tr><td><p>Don’t forget the pre-authorization stages</p></td><td><p>Many organizations celebrate speeding up changes (with the help of deployments and releases) on the technical side, moving from months to weeks or days. While this is indeed a reason to celebrate, the effects of such improvements are negligible when initial approvals still take months or years.</p></td><td><ul><li>Focus on value</li><li>Think and work holistically</li></ul></td></tr></tbody></table>

## 9. Acknowledgements

PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following people:

### Authors

Roman Jouravlev, Greg Sanker.

### Reviewers

Akshay Anand, Roy Atkinson, Sofi Fahlberg, Cheryl Grimes, Piia Karvonen, Henny Kerkvliet- Terpstra, Antonina Klentsova, Anton Lykov, Paula Määttänen, David Moskowitz, Christian F. Nissen, Mark O’Loughlin, Tatiana Orlova, Elina Pirjanti, Stuart Rance, Oleg Skrynnik, Mark Smalley.

### 2023 Revision

Antonina Douannes, Adam Griffith, Roman Jouravlev, Kaimar Karu, Olga Masalina, Avinash Singh
