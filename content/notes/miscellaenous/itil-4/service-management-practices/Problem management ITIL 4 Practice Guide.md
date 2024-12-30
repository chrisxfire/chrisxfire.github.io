---
title: "Problem management: ITIL 4 Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

This guide provides practical guidance for the problem management practice.

## 1. About this guide

It is split into seven main sections, covering:

*   general information about the practice
*   the practice’s processes and activities and their roles in the service value chain
*   the organizations and people involved in the practice
*   the information and technology supporting the practice
*   considerations for partners and suppliers for the practice.
*   information on assessing and developing the capability of the practice
*   recommendations for succeeding in the practice.  
    

#### 1.1 ITIL® 4 qualification scheme

Selected content from this guide is examinable as a part of the following syllabuses:

*   **ITIL Specialist** Create, Deliver and Support
*   **ITIL Specialist** Problem Management
*   **ITIL Specialist** Monitor, Support, and Fulfil

Please refer to the respective syllabus documents for details.  

## 2. General information

### 2.1 Purpose and description

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>The purpose of the problem management practice is to reduce the likelihood and impact of incidents by identifying actual and potential causes of incidents, and managing workarounds and known errors.</p></td></tr></tbody></table>

No product or service is perfect. Every product has errors which can cause incidents. Errors may originate in any of the four dimensions of service management. For example, a mistake in a third-party contract is as likely to cause an incident as a technical component failure. Many errors are identified and resolved during design, development, or testing before a product goes live, and don’t affect the service. However, some errors will remain undiscovered and proceed to the live environment, and these may cause incidents.

The increasing complexity of the business and technology environment adds to uncertainty. As more combinations of digital and business products, services, and workflows are created, there is a greater chance of these leading to incidents, despite each individual element being well-known, thoroughly tested, and safe-to-fail.

The problem management practice is adopted and developed by service providers to ensure that errors in the live environment are identified, analysed, and, where required and possible, removed or fixed.

This practice is beneficial for both IT service providers and their service consumers. Benefits for service providers include:

*   increased reliability of IT services
*   reduced losses and costs caused by IT service unavailability or degradation
*   fulfilment of the service quality targets
*   reduced technical debt
*   more even and predictable utilization of IT support resources.
    
    Benefits for service consumers include:
    
*   increased reliability of business operations and business services
*   reduced business risks

*   reduced losses caused by business service unavailability
*   better image due to uninterrupted business services.

#### 2.2 Terms and concepts

Errors that may cause (or have already caused) incidents are called problems.

<table><tbody><tr><td><strong>Definition: Problem</strong></td></tr><tr><td>A cause, or potential cause, of one or more incidents.</td></tr></tbody></table>

Problem management has three distinct phases, shown in Figure 2.1.

![](Problem%20management%20ITIL%204%20Practice%20Guide/ITIL_Problem_management_2_1.jpg)

Figure 2.1 The three phases of the problem management practice

The key features of each phase are described in Table 2.1

###### **Table 2.1 Key features of the problem management phases**

<table><colgroup data-width="1250"><col><col><col><col><col></colgroup><tbody><tr><td></td><td><strong>What is known at the beginning of the phase</strong></td><td><strong>Purpose of the phase</strong></td><td><strong>Output of the phase</strong></td><td><strong>Performed by</strong></td></tr><tr><td>Problem identification</td><td>There are incidents which are likely to have a common, currently unknown underlying error<br>or<br>There are vulnerabilities in our products and services, which may cause incidents</td><td>Assessment of potential impact of the errors and vulnerabilities, to decide whether they are worth an investigation</td><td>Registered, initially described and classified problems</td><td>Many teams, including technical, support, operations, development, supplier managers and others</td></tr><tr><td>Problem control</td><td>Registered, initially described and classified problems</td><td>Investigation and analysis of the problems, to understand their current and potential impact.<br>Identification of the most suitable owner for each error</td><td>Discovered and assessed errors in products and services, assigned to their owners</td><td>Technical teams<br>or<br>Product/service teams<br>Often multiple teams working together</td></tr><tr><td>Error control</td><td>Discovered and assessed errors in products and services, assigned to their owners</td><td>Identification of the best course of action for the known errors.<p>Planning and implementation of problem solutions<br>or<br>periodic control of the known errors; planning, communication and implementation of the problem workarounds.</p></td><td>Problem solutions (systemic and/or workarounds)<br>or<br>Solutions for incidents caused by the problems<br>Solved problems</td><td>Assigned technical teams or specialists</td></tr></tbody></table>

Not every problem goes through all three phases. Some can be dismissed at the identification phase (as duplicates, or due to low impact on the products and services). Others may be closed at the problem control stage because their impact has changed during the investigation, and they need no further attention.

Each phase has its own timeline.

Problem identification is a relatively quick workflow, although it can be preceded by a long period of data collection and processing.

In the problem control phase, service providers can influence the speed of investigation by assigning additional resources or by prioritizing the investigation over other tasks. However, the speed is also influenced by the difficulty of the investigation. Problem control can take minutes, hours, days, or weeks, though service providers usually try to limit the time of investigation to keep it cost efficient.

The timeline of error control timeline can vary significantly. When there is a known problem solution to be implemented, the implementation can be planned with high certainty, but still may take a long time. If there is no reasonable way to resolve the problem, it may remain open for long time, especially if there are effective ways to mitigate its impact. In this case the problem remains open and undergoes periodic reviews to confirm or change the course of action.

##### 2.2.1 Problem identification  

There are two main approaches to problem identification: reactive or proactive.

A reactive approach is focussed on investigating the causes of incidents that have already happened. This approach begins by analysing the symptoms and then proceeds to the causes. It aims to prevent incidents recurring, and may also contribute to the resolution of open incidents.

A proactive approach is focussed on identifying problems before they cause incidents, assessing the related risks, and optimizing the response with the aim of minimizing the probability and/or the impact of incidents. Proactive problem identification and is based on information about vulnerabilities and errors in the live environment which became known from sources other than incident management.

The information sources include:

*   vendors providing information on vulnerabilities in their products
*   developers, designers, or testers discovering errors in live versions while working with subsequent versions
*   user and specialist communities sharing their experiences of other organizations
*   monitoring of the infrastructure discovering deviations in systems performance that do not yet qualify as incidents
*   technical audits and other assessments.

<table><tbody><tr><td><strong>Reactive or proactive?</strong></td></tr><tr><td>Problem identification is always reactive to problems: it does not prevent them from occuring the first time. The proactive/reactive distinction refers to how problem identification and investigation relates to incidents:<p>- proactive problem management helps to prevent incidents from occurring the first time.<br>- reactive problem management helps to prevent incidents from recurring and may help to resolve open incidents.</p></td></tr></tbody></table>

Problem identification leads to the registration of a problem record. The problem records include information on the initial categorization and initial assessment of the business impact and urgency.

The purpose of problem categorization is to identify the team or specialist who will be responsible for the problem investigation. Therefore, categories usually reflect how the IT service provider teams are organized. In product-focused organizations, where teams with mixed technical expertise are formed around products, categorization may be based on the product or service catalogue. In more traditional organizations with teams formed based on the technical domain (applications, networks, databases, and so on), categorization is also likely to be based on the technical domains. Some problems occur outside of technical domains and may be related to other dimensions of service management:

*   value streams and processes (errors in procedures, processes, value streams)
*   organizations and people (lack of knowledge, unclear responsibilities, errors in incentives schemes)
*   partners and suppliers (errors in contracts, unclear responsibilities, lack of due diligence).

It is important to remember that initial categorization is likely to change at the problem control phase: many problems are found in overlaps of different technical domains, or different products and services. The purpose of categorization is to identify the team most suitable for leading the investigation, not performing 100% of the related activities.

Impact and urgency are important inputs for problem prioritization. The initial assessment of the business impact and urgency will differ for problems that are identified proactively or reactively.

The business impact of problems that are identified through available information about incidents can be estimated based on:

*   the individual impact of the incidents
*   the number and frequency of the incidents
*   trends in the occurrence of incidents
*   the expected change of the impact due to business cycles (for example, seasonal business activities).

The urgency of the problem investigation in such cases depends on the availability and effectiveness of incident resolutions. If the incidents have no effective resolution, and the problem needs to be investigated for the incidents to be solved, the urgency of the problem investigation is based on the agreed time to resolve the incidents, and the problem investigation will be initially focused on finding the cause(s) of the incidents and an acceptable resolution for those incidents. If the incidents have an effective resolution, and their impact is effectively minimized through the incident management practice, the urgency of the problem investigation is lower, and this may lower the problem priority at the problem control phase.

The business impact of problems identified proactively is estimated based on the expected effect of the problem on IT and business services. This requires a good understanding of the business and IT architecture and dependencies of the IT products and services on the components identified as bearing an error.

The urgency of these problems is estimated based on the forecasted probability and proximity of incident occurrence, and the possible business impact of these incidents.

A detailed description of the problem identification processes is provided in sections 3.1.1 and 3.1.2.

##### 2.2.2 Problem control  

Registered problems are accepted for analysis based on their initial categorization, business impact and urgency.

If a problem has been assigned to a team which has sufficient resources to start working on the investigation without delays, the team should begin the problem investigation. Details of the problem control process are provided in section 3.1.3.

However, the team may have other tasks waiting in a backlog, including other problems identified and assigned earlier. Resources, on the other hand, are always limited, and so is the number of tasks the teams can perform simultaneously. This is where prioritization is needed.

<table><tbody><tr><td><strong>Definitions</strong></td></tr><tr><td><strong>Prioritization</strong><br>The action of selecting which tasks to work on first when it is impossible to assign resources to all tasks in the backlog.<p><strong>Task priority</strong><strong><br></strong>The importance of a task relative to other tasks. Tasks with a higher priority should be worked on first. Priority is defined in the context of all tasks in a backlog.</p></td></tr></tbody></table>

Prioritization is a tool for assigning tasks to people in the context of a team. If an incident is handled by multiple teams, it will be prioritized within each team depending on resource availability, target resolution time, and estimated processing time. If several tasks need to be performed by different teams working in parallel, each team will be prioritizing their own task.

*   Prioritization is needed only when there is a resource conflict. Where there are sufficient resources to process every task within the time constraints, prioritization is unnecessary.
*   In each team, all types of tasks (including problems) should await prioritization and assignment in a single backlog, together with other tasks (planned and unplanned).
*   Visualization tools, such as Kanban, and Lean principles, such as the limiting of work in progress, are useful for effective prioritization.

The following are some specific guidelines on the prioritization of problems:

*   The target completion time for problem control is defined based on the problem impact and urgency assessed at the problem identification phase. They may be reassessed as new relevant information is discovered by problem investigation.
*   The target completion time for problem control is different from the target resolution time. The target resolution time for problems can only be planned after the problem control phase is completed, as it is based on the understanding of the error(s) and available ways to fix them. It is also possible that the problem control phase concludes that there is no need or reasonable way to fix the problem.
*   Problems should be prioritized within a single backlog which includes all tasks assigned to the team.
*   Problem investigation may require the creation of multiple tasks related to one problem for several teams to work in parallel. These tasks are created by the team which leads the problem investigation, they should include target completion time and sufficient supporting information.
*   In many cases, a temporary team combining different competencies is created to start problem investigation. This is often more effective than assigning parallel tasks to different teams, especially if the problem is likely to be in an overlap of areas of expertise and responsibilities. This technique is known as swarming.

<table><tbody><tr><td><strong>Definition: Swarming</strong></td></tr><tr><td>A technique for solving various complex tasks. In swarming, multiple people with different areas of expertise work together on a task until it becomes clear which competencies are the most relevant and needed.</td></tr></tbody></table>

During the problem control phase, one or more of the following is done, based on the results of problem investigation:

*   Previously unknown errors are identified, assessed, and assigned to a relevant team for error control.
*   Proactively identified errors are assessed and assigned to a relevant team for error control.
*   Recommendations for incident resolution based on an understanding of the causes are developed, recorded, and communicated to the relevant teams. These can be systemic resolutions or workarounds for incidents.
*   Problems with significantly low impact and probability and problems that have been identified mistakenly are documented and closed.

<table><tbody><tr><td><strong>Definition: Workaround</strong></td></tr><tr><td>A solution that reduces or eliminates the impact of an incident or problem for which a full resolution is not yet available. Some workarounds reduce the likelihood of incidents.</td></tr></tbody></table>

Note that workarounds for incidents derived from problem analysis usually do not reduce the likelihood of incidents. Instead, they help to resolve incidents quicker and better when they occur. Workarounds that may help to prevent incidents are more likely to be identified at the error control stage.

Problems that have not been dismissed at the problem control phase are assigned the status of ‘known error’.

<table><tbody><tr><td><strong>Definition: Known error</strong></td></tr><tr><td>A problem that has been analysed but has not been resolved.</td></tr></tbody></table>

##### 2.2.3 Error control

When a problem has been analysed (meaning the errors in the products have been localized and their impact on services has been assessed), it should be continually managed until resolved or closed without resolution.

Problem records may be closed only if one of the following conditions is met:

*   The problem is solved: the risk of incidents associated with the problem is removed or decreased to an acceptable level.
*   The problem no longer affects the organization.

If an error in the organization’s products still has significant impact and probability of related incidents, but does not have an acceptable resolution, it should remain open and be regularly reviewed.

Note that although ‘known error’ is the state of a problem, some organizations prefer to have separate records for problem control and error control. In these cases, the problem record may be closed when problem analysis is complete, and the following activities may be registered in a related known error record. The above conditions for closure apply to known errors, whether it is a separate record or a status of a problem record.

Many known errors remain open for a long time if they cannot be efficiently resolved, and they keep affecting services. In these cases, the organization may focus on maximizing the effectiveness and efficiency of incident handling (sometimes to the level of fully automated detection and resolution), but the problem records should remain open and periodically reviewed.

The above approach to error control is valid where the costs of problem resolution may be higher than the costs of living with known errors and effective incident management. This is typical for problems associated with third-party components, especially where the third party is unresponsive, or the components are no longer supported. Conversely, where components are available for improvement and can be improved (especially software under the organization’s own control), known errors should be quickly removed.

Known errors are a part of an organization’s technical debt and should be removed, where reasonably practicable.

<table><tbody><tr><td><strong>Definition: Technical debt</strong></td></tr><tr><td>The total rework backlog accumulated by choosing workarounds instead of systemic solutions that would take longer.</td></tr></tbody></table>

Error control ensures that the organization has sufficient up-to-date information about all the known errors in its products, including their statuses and their impacts on services.

Error control optimizes problem resolution so that its costs and side-effects are balanced by its positive effects. Reviewing known errors periodically helps to identify changes in circumstances (such as business impacts, the availability of a permanent solution and the associated costs, and resource availability) that may trigger the re-assessment of the error and initiate its resolution.

The key outputs of error control are improvement initiatives and change requests, which initiate the resolution of problems. Some resolutions fix the errors in configuration items and other product components. Others may introduce permanent workarounds: changes to the product configuration which do not fix the error, but reduce the likelihood of incidents to an acceptable minimum. The associated problem records may then be closed, but it is important to keep the knowledge about the errors available. This knowledge may be extremely valuable for future service design and planning of changes.

Permanent workarounds are normally used for components that the organization cannot fix (legacy systems, engineering infrastructure provided by third parties, and so on) but the use of permanent workarounds to prevent incidents increases the organization’s technical debt and should be avoided wherever possible.

To summarize, possible types of problem mitigation are listed in Table 2.2.

###### Table 2.2 Approaches to problem mitigation

<table><tbody><tr><td><strong>Mitigation approach</strong></td><td><strong>Applicability</strong></td><td><strong>Effect</strong></td></tr><tr><td>Full permanent fix of the errors found.<br>Problem record is closed.</td><td>Recommended approach for all CIs and other product components under the organization’s full control.<p>Highly recommended for software developed by the organization.</p></td><td>Incidents are prevented, side- effects are minimized, and the quality of services is improved in the short-, mid-, and long-term perspectives.</td></tr><tr><td>Permanent workaround isolating the errors.<br>Problem record may be closed or remain open.<br></td><td>May be recommended for CIs that cannot be fixed (third-party and/or legacy systems).</td><td>Incidents are prevented for the current product configuration; future designs and changes should consider the workarounds and may be limited by them.</td></tr><tr><td>Solutions are provided to optimize incident management. Problem record remains open.</td><td>Applicable to low-impact problems with very high costs for available permanent fixes or with no available fixes.</td><td>Incidents recur, but their impact is minimized. The known error should be periodically reviewed to ensure that recommended incident solutions are effective and there is still no permanent problem solution available.</td></tr></tbody></table>

##### 2.2.4 Problem models

Different sources and types of problem may require different approaches to problem identification and control. For example, one or more of the following problem types may require a special approach to the problem management practice. These can be problems in:

*   Information and technology  
    \- software  
    \- hardware  
    \- data, including that which is sensitive
*   Value streams and processes  
    \- procedures  
    \- processes and ways of working
*   Partners and suppliers  
    \- third-party components  
    \- contracts and agreements
*   Organizations and people  
    \- skills and competencies  
    \- training
*   The service consumer’s resources.

To optimize the handling and resolution of these and other types of problems, service providers define problem models. Problem models help to manage problems effectively and efficiently, often with better results because of the application of relevant proven and tested methods.

<table><tbody><tr><td><strong>Definition: Problem model</strong></td></tr><tr><td>A repeatable approach to the management of a particular type of problem.</td></tr></tbody></table>

The creation and use of problem models are important activities in the problem management practice. They are described in section 3.1.4.

### 2.3 Scope

The scope of the problem management practice includes:

*   the identification and analysis of problems, including the analysis and control of known errors
*   the initiation of changes to fix or reduce the impact of problems
*   the ownership and co-ordination of problem resolution
*   providing information about problems to the relevant stakeholders
*   monitoring of known errors and continual improvement of workarounds.

There are several activities and areas of responsibility that are not included in the problem management practice, although they are still closely related to problems. These are listed in Table 2.3, along with references to the practice guides in which they can be found.

###### Table 2.3 Activities related to the problem management practice described in other practice guides

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Practice guide</strong></td></tr><tr><td>Incident resolution</td><td>Incident management</td></tr><tr><td>Control and implementation of changes initiated to fix the problems</td><td>Change enablement<p>Deployment management</p><p>Infrastructure and platform management</p><p>Release management</p><p>Software development and management</p><p>Other practices</p></td></tr><tr><td>Risk assessment and control</td><td>Risk management</td></tr><tr><td>Detection and control of errors in products before deployment to the live environment</td><td>Deployment management<p>Service design</p><p>Service validation and testing</p><p>Software development and management</p></td></tr><tr><td>Communication of workarounds for incidents to users</td><td>Service desk</td></tr></tbody></table>

#### 2.4 Practice success factors

<table><tbody><tr><td><strong>Definition: Practice success factors</strong></td></tr><tr><td>A complex functional component of a practice that is required for the practice to fulfil its purpose.</td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The problem management practice includes the following PSFs:

*   identifying and understanding the problems and their impact on services
*   optimizing problem resolution and mitigation.  
    

##### 2.4.1 Identifying and understanding the problems and their impact on services

Organizations should understand the errors in their products because they may cause incidents and affect service quality and customer satisfaction. The problem management practice ensures problem identification and thus contributes to the continual improvement of products and services. This is more effective if performed proactively rather than reactively.

Organizations starting out with problem management usually begin with reactive problem identification based on repeating and major incidents. The next steps in capability development include proactive problem identification and expanding the scope of problem management beyond the information and technology dimension. More information on the problem management capability levels can be found in section 7.3.

It is important to find the right balance between the accessibility and effectiveness of problem identification. Although problems can, and should, be identified in many areas of the service provider’s organization (by developers, support teams, technical specialists and others) it is important to ensure that there is accurate and sufficient information about identified problems, and that they are assigned correctly.

This balance can be achieved by appropriate training, or by assigning responsibility for problem identification to people in each relevant team.

<table><tbody><tr><td><strong>Who can register a problem?</strong></td></tr><tr><td>There are several approaches to assigning responsibility for problem registration. One approach is to encourage every practitioner, analyst or specialist to initiate and register problems. This would increase the number of improvements and improve the visibility of the errors in the organization’s products.<p>However, this approach can be limiting and frustrating where an individual wants to raise a problem but is unable to easily do so. This may also significantly increase the number of registered problems that are not actively worked on, or that are incorrectly categorized. To prevent this, some organizations prefer to make one or more roles responsible for the initial filtering and registering of potential problems.</p><p>This approach may be effective as long as the individuals carrying out these roles have sufficient resources and authority, and can process information from various sources consistently and transparently.</p><p>Organizations can combine different approaches to balance the scope, throughput, and efficiency of problem identification.</p></td></tr></tbody></table>

It should be accepted that in some cases problems will be incorrectly identified, categorized, or assigned. Blame should not be apportioned for these mistakes, but instead this should lead to analysis and improvement of the problem models and problem identification guidelines.

Teams should understand the value of problem management for their product or technology domain, and eventually for the organization. Problem management should be treated as an important form of risk management and of continual improvement. If these practices are formalized in the organization, problem management should follow their recommendations and be aligned with them in the context of the organization’s service value system.

##### 2.4.2 Optimizing problem resolution and mitigation

When problems have been identified, they should be handled effectively and efficiently. It is rarely possible to fix (remove) all problems in all organization’s products, but identification without resolution is significantly less valuable for the organization and its customers. A balanced approach should be defined for problem mitigation, considering the associated costs, risks, and impacts on the service quality. It is important to make decisions about problem resolution or mitigation based on the business impact of different scenarios, rather than purely technical considerations.

As problem investigation and resolution may require significant resources, it is important to maintain awareness and support of the practice at all levels of the service provider.

Some organizations find it useful to have and share across the teams a list of the most important open problems. This is a simple yet effective way to:

*   demonstrate management attention to the problems
*   raise awareness of the prioritized problems across the service provider
*   involve people from different teams in suggesting ideas and solutions
*   keep track of the status and progress of the problem investigation and resolution
*   keep business stakeholders informed and maintain their interest and support.  
    

### 2.5 Key metrics

Key metrics for the problem management practice are mapped to its PSFs. The key metrics are listed in Table 2.4.

The practice metrics should be applied to a specific context such as type of problems, services, technical domain, or periods of time.

The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which the practices contribute. The context of the business and the value streams is important when defining whether the practice’s performance is considered good or not. This is why this practice guide cannot recommend universal key performance indicators for problem management: the target values for each metric can only be defined in the organization’s context.  

###### Table 2.4 Key metrics of problem management

<table><tbody><tr><td><strong>Practice success factors</strong></td><td><strong>Key metrics</strong></td></tr><tr><td>Identifying and understanding the problems and their impact on services</td><td>Number and impact of problems identified over the period<p>Number and impact of incidents that are not associated with known errors</p><p>Number and impact of incidents that require urgent problem investigation</p></td></tr><tr><td>Optimizing problem resolution and mitigation</td><td>Number and impact of incidents prevented by problem resolution<p>Number and impact of incidents resolved with solutions provided by problem investigation</p><p>Number and impact of known errors that remain open</p></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the problem management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

**Note**: A useful metric for problem management was proposed by D. Isaychenko and P. Demin1. They called it a problem management performance index (PPI):  
*PPI = N+R ÷ O+C* \[0;1\] ↑

Where  
*R* is the total number of problems resolved during the reporting period;  
*O* is the total number of problems that were open at the end of the period;  
N is the number of problems logged during the period and still open by the end of the period;  
*C* is the total number of problems closed during the period. *C* includes actually resolved problems and problems that were closed without being resolved. . To avoid accidental distortions, both R and C do not include problems logged by mistake, such as duplicates or unintentional logging, which are those problems that were closed without any actual processing.  
PPI increases with new logged problems as well as with resolved ones. This demonstrates and can be used to stimulate both problem identification and resolution.

<sup>1</sup>[https://www.tsoshop.co.uk/product/9780113318377/Metrics-based-Service-Management-PDF](https://www.tsoshop.co.uk/product/9780113318377/Metrics-based-Service-Management-PDF)

## 3. Value streams and processes

#### 3.1 Processes  

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><strong>Definition: Process</strong></td></tr><tr><td>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</td></tr></tbody></table>

Problem management activities form four processes:

*   proactive problem identification
*   reactive problem identification
*   problem control
*   error control.  
    

##### 3.1.1 Proactive problem identification

This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

###### Table 3.1 Inputs, activities, and outputs of the proactive problem identification process

<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Error information from vendors and suppliers Information about potential errors submitted by specialist teams<br>Information about potential errors submitted by external user and professional communities<br>Information about potential errors submitted by users<p>Monitoring data</p><p>Service configuration data</p></td><td>Review of the submitted information<p>Problem registration</p><p>Initial problem categorization and assignment</p></td><td>Problem records<p>Feedback to the problem initiator</p></td></tr></tbody></table>

Figure 3.1 shows a workflow diagram of the process.  

![](Problem%20management%20ITIL%204%20Practice%20Guide/ITIL_Problem_management_3_1.jpg)

Figure 3.1 Workflow of the proactive problem identification process

Proactive problem identification is used to identify potential errors in the organization’s products based on sources other than incident records. Proactive problem identification and control can be considered and performed as a form of risk management which is focused on the vulnerabilities in the organization’s product: it includes the identification, assessment, and analysis of the vulnerabilities and the associated risks.

Possible sources of information about errors in an organization’s products are listed in Table 3.2.

###### Table 3.2 Sources of information for proactive problem identification

<table><tbody><tr><td><strong>Source</strong></td><td><strong>Examples of information</strong></td></tr><tr><td>Service designers, software developers, architects, and other teams working on the next versions of CIs and other components</td><td>Errors in the current live versions discovered during work on the subsequent versions<p>Errors in the versions currently being deployed to the live environment that have been identified during testing but have not been fixed</p></td></tr><tr><td>Vendors of software and other CIs</td><td>Errors in the current live versions of the vendor’s systems and components</td></tr><tr><td>User and professional communities</td><td>Errors by other organizations using the same versions of systems and components</td></tr><tr><td>Monitoring data</td><td>Suspicious trends and deviations in the performance of services and CIs</td></tr><tr><td>Users</td><td>Vulnerabilities in the services being used</td></tr></tbody></table>

Where possible, proactive problem identification should focus on key systems and components which have the highest potential impact on the organization and its customers.

However, indications of errors in other systems should not be neglected. In complex technical environments designed for high availability, incidents may have multiple causes which are often the result of improbable combinations of improbable factors. Seemingly unimportant errors in non-core systems can contribute to serious incidents. Proactive problem identification should include the careful assessment of the probability and impact of the identified vulnerabilities. Table 3.3 provides a description of the process activities.

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Description</strong></td></tr><tr><td>Review of the submitted information</td><td>Depending on the source and the subject, the submitted information is reviewed by a specialist or a specialist group. The review includes checks for duplicates, applicability, common sense, and ongoing incidents potentially related to the submitted information.</td></tr><tr><td>Problem registration</td><td>If the need for problem control is confirmed, a problem record is registered. This can be done by a dedicated role or by a wider group of specialist roles.</td></tr><tr><td>Initial problem categorization and assignment</td><td>The person registering a problem performs the initial categorization. The information usually includes some of the following (if known or reasonably assumed):<br>- source<br>- description<br>- associated CIs and/or CI classes<br>- estimated impact and probability of incidents<br>- associated and potentially affected services<br>- impact on the organization and customers.<p>Based on the initial categorization, the problem is assigned to a specialist group responsible for the associated CI, service, or product. Where applicable and expected, the problem initiator may be notified about the problem registration.</p></td></tr></tbody></table>

#####   
3.1.2 Reactive problem identification

This process includes the activities listed in Table 3.4, and transforms the inputs into outputs.

###### Table 3.4 Inputs, activities, and outputs of the reactive problem identification process

<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Information about ongoing incidents<p>Incident records and reports</p><p>Monitoring data</p><p>Service configuration data</p><p>Service level agreements (SLAs)</p></td><td>Problem registration<p>Initial problem categorization and assignment</p></td><td>Problem records</td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![](Problem%20management%20ITIL%204%20Practice%20Guide/ITIL_Problem_management_3_2.jpg)

Figure 3.2 Workflow of the reactive problem identification process

Reactive problem identification uses information about past and ongoing incidents to investigate their causes. It can be triggered by an ongoing incident investigation that could not identify the nature of the incident; in this case, problem identification and control may be urgent. The incident management and problem management practices are used within a single value stream and are likely to involve the same (or overlapping) resources, including teams, tools, and procedures.

When based on the analysis of past incidents, problem identification may include statistical analysis, impact analysis, and trend analysis from various perspectives. The aim is to identify groups of incidents with possible common causes and significant total business impact.

This process varies slightly depending on the trigger. The variations are illustrated in Table 3.5.  

###### Table 3.5 Activities of the reactive problem identification process

<table><tbody><tr><td><strong>Ac</strong><strong>tivity</strong></td><td><strong>Triggered by ongoing incident</strong></td><td><strong>Triggered by incident records analysis</strong></td></tr><tr><td>Problem registration</td><td>The team working on the incident identifies the need for problem investigation. In some cases, a problem record is linked to one or more incident records for tracking the investigation. It may be especially important where multiple incidents in numerous locations are being handled by different teams and require a coordinated problem investigation, or where problem investigation will be done by a dedicated team.<p>In other cases, the team working with the incident may continue investigating the incident’s causes and document the problem after the incident is resolved. The problem may still need to be registered, especially if the causes of the incident were not removed during incident resolution and new incidents may arise from the same problem.</p></td><td>A specialist team responsible for a system, service, or product performs regular reviews of the incident records associated with their area of responsibility. If they detect a reason for a problem investigation, they register a problem record. These reasons may include:<br>- a high number of similar incidents<br>- a high percentage of incidents resolved after the target resolution time<br>- major incidents<br>- availability below the target level.</td></tr><tr><td>Initial problem categorization and assignment</td><td>When registering a problem, the person doing so performs initial categorization. This usually includes some of the following (if known or reasonably assumed):<br>- description<br>- associated CIs and/or CI classes<br>- estimated impact and probably of incidents<br>- associated and potentially affected services<br>- impact on the organization and customers.<p>If the problem is registered before the problem investigation, the problem is assigned to the appropriate specialist group.</p><p>If the problem is registered after the problem investigation, the information includes the steps made, the results, and the current status of the problem. If the problem is not solved at the time of registration, it is assigned to the appropriate group.</p></td><td>When registering a problem, the person doing so performs initial categorization. This usually includes some of the following (if known or reasonably assumed):<br>- description<br>- associated incidents and their solutions<br>- associated CIs and/or CI classes<br>- estimated impact and probability of future incidents<br>- associated and potentially affected services<br>- impact on the organization and customers<br>- estimated impact and probability of incidents.<p>Based on initial categorization, the problem is assigned to a specialist group, responsible for the associated CI, service, or product.</p></td></tr></tbody></table>

#####   
3.1.3 Problem control

This process focuses on the investigation of the problem. It includes the activities shown in Table 3.6 and transforms the inputs into outputs.

<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Problem records<p>Service configuration data</p><p>Technical information about CIs, products, and services</p><p>Incident records</p><p>Monitoring data</p></td><td>Problem investigation<p>Known error communication</p></td><td>Problem records<p>Known errors</p><p>Incident solutions</p></td></tr></tbody></table>

Figure 3.3 shows a workflow diagram of the problem control process.

![](Problem%20management%20ITIL%204%20Practice%20Guide/ITIL_Problem_management_3_3.jpg)

Figure 3.3 Workflow of the problem control process

Table 3.7 provides examples of the process activities.

######   
Table 3.7 Activities of the problem control process

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Description</strong></td></tr><tr><td>Problem investigation</td><td>The specialist team assigned to the problem investigates the possible causes of the incident and/or verifies the reported errors in the CIs and the organization’s other resources. . The methods and procedures vary depending on how the problem has been identified. For problems identified reactively, localization starts with understanding which CIs may have errors causing past or ongoing incidents. For most problems identified proactively, CIs or CI classes would have been identified during their registration. After the problem is localized to the level of CIs, further diagnostics may be needed to identify errors within the suspicious CIs. This and the following activities may be performed by different teams (teams re-assigned based on the problem localization). If the reported problem is irrelevant to the organization (for example, a publicly reported vulnerability in software that does not affect the versions used by the organization), the problem record may be closed. If the investigated problem is relevant to the organization, it is assigned the known error status for further control and resolution. Actions and results of the investigations are recorded in the problem records.</td></tr><tr><td>Known error communication</td><td>The results of problem investigation are communicated to the problem initiator and relevant teams. . These may include product development teams, technical specialists, the service desk team, users, and suppliers. If there are ongoing incidents associated with the problem that is being investigated, the results of the problem localization are communicated to the incident investigation teams. It is possible that understanding the errors is enough to define an incident resolution. In this case, a recommended solution for the incident should be registered in the problem records and communicated to the teams working with the incident.</td></tr></tbody></table>

To investigate problems, organizations use various analysis techniques. These may include:

*   root cause analysis techniques, such as 5 Whys, Kepner and Fourie, and fault tree analysis
*   impact analysis techniques, such as component failure impact analysis and business impact analysis
*   risk analysis techniques.

It is important to remember that the concept of a single root cause has a very limited applicability in complex evolving environments. Quite often, incidents are caused by improbable combinations of improbable factors. This means that investigation of problems (especially identified reactively) should not be limited to the identification of the first possible cause of incidents. Problem investigation should always consider all four dimensions of service management.

#####   
3.1.4 Error control  

This process focuses on the monitoring and control of the status of the known errors (problems that are analysed but not resolved) and their resolution. It helps to ensure that the negative impacts of the known errors on services are understood and minimized; the solutions for related incidents are effective; and the mitigation approach for the known error is valid, effective, and efficient.

This process includes the activities shown in Table 3.8 and transforms the inputs into outputs.

######   
Table 3.8 Inputs, activities, and outputs of the error control process

<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Problem records<p>Service configuration data</p><p>Technical information about CIs, products, and services</p><p>Incident records</p><p>Monitoring data</p><p>Knowledge management data</p></td><td>Problem solution development<p>Problem resolution initiation</p><p>Known error monitoring and review<br>Problem closure</p></td><td>Problem records<p>Problem models</p><p>Change requests</p><p>Improvement initiatives</p><p>Problem solutions</p></td></tr></tbody></table>

Figure 3.4 shows a workflow diagram of the process.

![](Problem%20management%20ITIL%204%20Practice%20Guide/ITIL_Problem_management_3_4.jpg)

Figure 3.4 Workflow of the error control process

######   
Table 3.9 Activities of the error control process

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Example</strong></td></tr><tr><td>Problem solution development</td><td>The team (assigned or re-assigned based on the problem investigation) looks for a way to solve the problem. This includes defining an approach to the mitigation (see Table 2.1) and development of the actual solution within the selected approach. If there is no viable solution for the problem, the supporting information is recorded and the error goes to periodic review.</td></tr><tr><td>Problem resolution initiation</td><td>In most cases, problem resolution requires change. The responsible team submits change requests, following the organization’s procedures for change initiation and implementation. In other cases, required actions are not classified as changes and can be initiated and performed following other procedures. Either way, the team initiates the actions required for the defined (and, if needed, approved) problem resolution. This initiation may need to be supported with relevant justification (including financial, risk, compliance, technical, and other considerations).</td></tr><tr><td>Known error monitoring and review</td><td><strong>If a solution is approved for the known error</strong><strong><br></strong><strong><br></strong>The implementation of the solution is controlled and confirmed using pre-agreed criteria. This is usually done by the team that initiated the resolution, or another pre-agreed role, such as problem manager.<br>For reactively identified problems, this can be done based on the change in incident dynamics (related incidents are resolved or prevented). For proactively identified problems, resolution control is based on the success of the initiated changes and may include a period of monitoring any service that might have been affected by the errors.<br>If the resolution of the problem is unconfirmed, the team returns to the problem solution development step of the process.<br><strong><br></strong><strong>If no viable solution is found for the known error</strong><strong><br></strong><strong><br></strong>An assigned specialist team should monitor the known error. This is usually the team responsible for the CI, service, or product with which the known error is associated. The team monitors the status of the known error as defined in the mitigation strategy. Monitored parameters may include:<br>- the dynamics of the associated incidents<br>- the effectiveness of the incident solutions<br>- the effectiveness of the problem workarounds<br>- changes in the statuses of the resources needed to solve a problem (budget, updates from the vendor, specialists, new infrastructure, and so on).<p>The team should conduct problem reviews periodically (in line with the agreed mitigation approach) or based on outstanding monitoring results.</p><p>If the review confirms that the mitigation approach is valid and up to date (the problem exists, the impact assessment is up to date, incident solutions are effective, the problem workaround is effective, and no viable problem fix is available), then known error monitoring continues.</p><p>If the mitigation approach becomes invalid, the problem solution development activity is initiated to review and redefine the mitigation approach. This may include developing and implementing a problem solution or updating the incident solutions for any associated incidents.</p><p>If the problem no longer exists (for example, it has been removed with planned software or hardware updates or by decommissioning the affected CIs), problem closure is initiated.</p><p>If the problem demonstrated a new pattern that suggests the amendment or creation of a problem model, a problem model is documented and communicated as part of the problem review activity.</p><p>Problem records are updated with monitoring data.</p></td></tr><tr><td>Problem closure</td><td>The specialist (or team) acting as a problem manager/coordinator, reviews the results and formally closes the problem record.<p>If the resolution is confirmed, they document the resolution control results and formally close the problem record.</p><p>Closed problem records should be available as part of the organization’s knowledge base, especially if there is a chance that similar problems may recur.</p></td></tr></tbody></table>

###   
3.2 Value stream contribution

#####   
3.2.1 Service value streams  

To perform certain tasks or respond to particular situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario. Once designed, value streams should be subject to continual improvement.

<table><tbody><tr><td><strong>Definition: Value stream</strong></td></tr><tr><td>A series of steps an organization undertakes to create and deliver products and services to consumers.</td></tr></tbody></table>

In practice, however, many organizations come to use of the value stream concept after having worked for a while (sometimes for years) without the value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the ‘As Is’ situation, the de-facto flows of work, and to analyse them in order to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding the existing value streams is critical to improving organization’s performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services.

Combined, organizations’ value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations follow best practice recommendations for various service management practices, such as incident management, change enablement, software development, and many others. Problem management is one of the most adopted and developed practices.

However, the practices have often been adopted and organized in a siloed, isolated manner, just as they were presented in the service management bodies of knowledge. In reality, a flow of work required to create or restore value for a customer or another stakeholder is almost never limited to one practice.

#####   
3.2.2 Problem management in service value streams

Problem management is likely to be involved in several service value streams. The most obvious one is the restoration of normal operations in case of an incident. This service value stream is not limited to the incident management practice, but involves many other practices, including problem management.

###### Table 3.10 Practices in the service value stream restoring normal operation after an incident

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Practice</strong></td></tr><tr><td>Incident detection</td><td>Service desk (for user-reported incidents)<br>or<br>Monitoring and event management</td></tr><tr><td>Incident registration<br>Incident classification</td><td>Incident management</td></tr><tr><td>Incident diagnosis</td><td>Incident management<p>Knowledge management<br><strong><br>Problem management</strong></p></td></tr><tr><td>Incident resolution</td><td>Incident management and one or more of:<br><strong>Problem management</strong><p>Change enablement</p><p>Software development and management</p><p>Service validation and testing</p><p>Deployment management</p><p>Release management</p><p>Service desk</p><p>Infrastructure and platform management</p><p>Supplier management</p></td></tr><tr><td>Incident closure</td><td>Incident management<p>Service desk</p><p>Monitoring and event management</p><p><strong>Problem management</strong></p><p>Knowledge management</p><p>Business relationship management</p></td></tr></tbody></table>

In this value stream, the problem management practice may be used to:

*   provide information about currently open problems
*   provide information about previously identified solutions for similar incidents
*   urgently investigate the causes of the incident(s) and find ways to resolve the incident(s)
*   capture information about the incident(s) to update knowledge about errors, symptoms, and resolutions. Similarly, problem management may be involved in other value streams, including:
*   design, development and implementation of new and changed products and services
*   routine operations of IT systems.

In all cases, the practice is involved for the same purposes listed above: providing previously identified solutions and other relevant information or capturing information about new problems.

There is no single operating model fitting all organizations. Different solutions work for different organizations, involving different value streams which in turn involve different management practices.

#####   
3.2.3 Analysing a service value stream

###### 3.2.3.1 The key steps of a service value stream analysis

The following are some simple and practical recommendations for service value stream analysis and mapping.

**Identify the scope of the value stream analysis**

Value streams can be mapped to a particular product or service or applied to most or all of them. Value streams may differ for different consumers; for example, incidents can be solved and communicated differently for internal and external customers, or for B2B and B2C products, or for services based on products developed inhouse or sourced externally.

**Define the purpose of the value stream from the business standpoint**  
Make sure the stakeholder’s concerns are clearly understood, since they are the ones defining value. In the case of problem management, it is usually the service owners who need to ensure that service reliability meets the agreed requirements; however, there are usually other interested parties. For example, internal users may be unable to provide normal service to a business customer because of the incident, and the value of the value stream should be considered from the business perspective, not solely from the user perspective.

**Do the service value stream walk**  

Walk or directly experience the steps and information flow as they go in practice (consider the Lean technique of Gemba walk):

**a. Identify the workflow steps**

**b. Collect data as you walk**

**c. Evaluate the workflow steps**Typically, the criteria for evaluation are:

*   value for the stakeholder (does the step add value for the business stakeholder?)
*   effectiveness or performance (is the step performed well?)
*   availability (are required resources available to execute the step?)
*   capacity (are required resources enough?)
*   flexibility (are the required resources interchangeable within the step?).

**d. Map the activities and the information flows** In an ideal situation, the flow goes smoothly without delays and pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

**e. Create and review the timeline and resource level** Map out process times and lead times for resources and workload through the workflow steps.

**Reflect on the value stream map (VSM)** Identify factors that might not have been entirely apparent at first. The information collected is used at this step to find the waste.

**Create a ‘to be’ VSM** This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

**Using the ‘to be’ VSM, plan improvements** Refer to the continual improvement practice guide for a practical improvement model.

######   
3.2.3.2 Problem management considerations in a service value stream analysis

To ensure that relevant problem management activities are included in service value streams, the following steps can be added to the above recommendations.

*   At the scoping step (1), identify the IT and business services related to the value stream and the involved business stakeholders. For example, should the problem management practice be involved in the investigation of problems causing business service incidents, or should it be limited to problems in IT services?

*   Make sure the value stream is understood (step 2) from the standpoint of the business, not only of the service provider.

*   During the service value stream walk (3a), identify other practices involved in dealing with problems at every step. Which practices provide required information (configuration data, asset data, financial information, agreed timelines for the service restoration…)? How are changes initiated if required for problem resolution? What if a resolution initiates a project? How are third parties involved in problem investigation and error control? How information about vulnerabilities in third-party products is obtained from the suppliers?
*   During the workflow steps evaluation (3c), evaluate the step’s impact on the business value. Special attention should be paid to steps with low business value, low performance, and availability or capacity issues. It is not unusual to find steps which serve some internal control or bureaucratic purposes but delay the incident resolution.
*   At the reflection and planning steps (4-5), ensure that the problem management processes are optimized for business value throughout the stream, not only at the within the problem management practice.
*   Consider including the creation or updating of problem models (see section 2.2.4) in the value stream improvement plans (step 6).

## 4. Organizations and people

### 4.1 Roles, competencies, and responsibilities

The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended.

Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

######   
Table 4.1 Competency codes and profiles

<table><tbody><tr><td><strong>Competency code</strong></td><td><strong>Competency profile (activities and skills)</strong></td></tr><tr><td>L</td><td><strong>Leader</strong> Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</td></tr><tr><td>A</td><td><strong>Administrator</strong> Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</td></tr><tr><td>C</td><td><strong>Coordinator/communicator </strong>Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</td></tr><tr><td>M</td><td><strong>Methods and techniques expert</strong> Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</td></tr><tr><td>T</td><td><strong>Technical expert</strong> Providing technical (subject matter) expertise and conducting expertise-based assignments</td></tr></tbody></table>

Two practice-specific roles may be found in organizations: problem manager and problem coordinator.

These roles are often introduced in organizations where the number of problems is high. In other organizations, problem management activities are coordinated by a person or a team responsible for the CIs, service, or product with which the problem is associated; this may be the resource owner, service owner, or product owner respectively.  

##### 4.1.1 Problem manager role

Where a dedicated problem manager role is defined, it is usually assigned to specialists combining good knowledge of the organization’s products (architecture, configurations, and interdependencies) with solid analytical and leadership skills (the ability and authority to coordinate teamwork and provide good risk management). The competency profile for this role is CLMT.

This role is usually responsible for managing and coordinating the specialist activities in the problem management processes, including:

*   conducting and coordinating problem registration based on the submitted information
*   the initial categorization of the problems
*   coordinating problem investigation and solution implementation control
*   coordinating the communication with the teams responsible for incident resolution and change implementation
*   developing and communicating problem models, where applicable
*   coordinating known error monitoring and review
*   the formal problem closure.

#####   
4.1.2 Problem coordinator role

In more complex organizations, some responsibilities for the problem management practice may be delegated to the problem coordinator. The problem coordinator focuses on routine problem management activities, such as the review of submitted information about possible problems, problem review, and problem closure.

Examples of other roles which can be involved in the problem management activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

######   
Table 4.2 Examples of roles with responsibility for problem management activities

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Responsible roles</strong></td><td><strong>Competency profile</strong></td><td><strong>Specific skill</strong>s</td></tr><tr><td><em>Proactive problem identification process</em></td><td></td><td></td><td></td></tr><tr><td>Review of the submitted information</td><td>CI owner<p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p></td><td>T</td><td>Good knowledge of the product, including its architecture and configuration</td></tr><tr><td>Problem registration</td><td>CI owner<p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p></td><td>TA</td><td>Knowledge of the registration tools and procedures</td></tr><tr><td>Initial problem categorization and assignment</td><td>CI owner<p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p></td><td>TAC</td><td>Good knowledge of the product, service architecture, and business impact Understanding of the responsibilities and competencies across the teams</td></tr><tr><td><em>Reactive problem identification process</em></td><td></td><td></td><td></td></tr><tr><td>Problem registration</td><td>CI owner<p>Incident manager</p><p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p></td><td>TA</td><td>Knowledge of the registration tools and procedures</td></tr><tr><td><em>Problem control process</em></td><td></td><td></td><td></td></tr><tr><td>Problem investigation</td><td>CI owner<p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p><p>Supplier</p><p>Technical specialist</p></td><td>CT</td><td>Good knowledge of the product, service architecture, and business impact.<br>Good knowledge of diagnostic, investigation, and analysis methods and tools.</td></tr><tr><td>Known error communication</td><td>CI owner<p>Incident manager</p><p>Problem coordinator</p><p>Problem manager</p></td><td>TC</td><td>Understanding of stakeholders and responsibilities<br>Knowledge of the communication tools and procedures</td></tr><tr><td><em>Error control process</em></td><td></td><td></td><td></td></tr><tr><td>Problem solution development</td><td>CI owner<p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p><p>Supplier</p><p>Technical specialist</p></td><td>TMC</td><td>Good knowledge of the product and service architecture, configuration, and technical details<br>Creativity<br>Systems thinking</td></tr><tr><td>Problem resolution initiation</td><td>CI owner<p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p><p>Supplier</p><p>Technical specialist</p></td><td>CT</td><td>No specific skills required</td></tr><tr><td>Known error monitoring and review</td><td>CI owner<p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p><p>Supplier</p><p>Technical specialist</p></td><td>TAC</td><td>Good knowledge of the product and service architecture and business impact</td></tr><tr><td>Problem closure</td><td>CI owner<p>Problem coordinator</p><p>Problem manager</p><p>Product owner</p><p>Service owner</p></td><td>TCA</td><td>Good knowledge of the product, service architecture, and business impact</td></tr></tbody></table>

### 4.2 Organizational structures and teams

It is unusual to see a dedicated organizational structure for the problem management practice, although the role of problem manager is sometimes associated with a formal job title. This is typical for organizations with complex bureaucracy and a significant number of problems to manage. Many organizations find it useful to form temporary teams to investigate high-impact problems and/or to develop solutions.

In product-focused organizations, problem management job titles and roles are not typically adopted. Instead, this practice is integrated in the day-to-day activities of the product development and management teams. It is automated wherever possible.

Problem management is a cross-functional collaborative practice, and requires support and participation from a range of teams and people across an organization. As such, if there is a specialized position or team fully dedicated to problem management, they become responsible for leading problem management activities and involving other teams in the practice. Problem management relies on information from, and the participation of, all teams within a service provider, and often also of its suppliers and customers. An example of a coordinating activity that may be performed by the dedicated problem manager is organizing a swarm (a temporary team assembled on a short notice to investigate a problem).

## 5. Information and technology

### 5.1 Information exchange

The effectiveness of the problem management practice is based on the quality of the information used. This information includes, but is not limited to, information about:

*   products and services and their architecture and design, including configuration information
*   customers and users
*   partners and suppliers, including contract and SLA information on the services they provide
*   ongoing and past incidents
*   planned, ongoing, and past changes
*   a third-party’s products and components, including vulnerabilities and incidents.

This information may take various forms. The key inputs and outputs of the practice are listed in section 3.

### 5.2 Automation and tooling

The problem management practice can significantly benefit from automation. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to the full automation of activities where technology solutions remove the need for human intervention. Table 5.1 provides a list of the key automation supporting the practice and their most common application.

######   
Table 5.1 Automation solutions for the problem management practice

<table><tbody><tr><td><strong>Automation tools</strong></td><td><strong>Application in problem management</strong></td></tr><tr><td>Workflow management and collaboration tools</td><td>Reactive problem identification (analysis of incident records)<p>Management of problem and known error records</p><p>Support of collaboration during problem investigation and resolution</p><p>Support of problem impact analysis and root cause analysis (through records of other management practices, including incidents and changes)</p></td></tr><tr><td>Monitoring and event management tools</td><td>Proactive problem identification<p>Support of trend analysis for problem impact assessment</p><p>Monitoring of the effectiveness of the resolution</p></td></tr><tr><td>Service configuration management tools</td><td>Problem categorization and investigation</td></tr><tr><td>Analysis and reporting tools</td><td>Problem investigation<br>Practice measurement and reporting</td></tr><tr><td>Knowledge management tools</td><td>Retrieving, managing, and communicating known solutions for incidents and problems</td></tr></tbody></table>

Detailed descriptions of how these tools support the practice’s activities are outlined in Table 5.2.

######   
Table 5.2 Details of automation of the problem management activities

<table><tbody><tr><td><strong>Process activity</strong></td><td><strong>Means of automation</strong></td><td><strong>Key functionality</strong></td><td><strong>Impact on the effectiveness of the prac</strong><strong>tice</strong></td></tr><tr><td><em>Proactive problem identification process</em></td><td></td><td></td><td></td></tr><tr><td>Review of the submitted information</td><td>Monitoring and event management tools<p>Workflow management and collaboration tools</p></td><td>Collection and overview of information from various sources, including data analysis and team collaboration</td><td>High</td></tr><tr><td>Problem registration</td><td>Workflow management and collaboration tools</td><td>Management of problem records integrated with other service management data</td><td>High</td></tr><tr><td>Initial problem categorization and assignment</td><td>Workflow management and collaboration tools<p>Service configuration management tools</p></td><td>Management of problem records integrated with other service management data, backlog management, communication, and collaboration support</td><td>High</td></tr><tr><td><em>Reactive problem identification process</em></td><td></td><td></td><td></td></tr><tr><td>Problem registration</td><td>Workflow management and collaboration tools</td><td>Machine-learning-based problem identification based on analysis of past and ongoing incidents<br>Management of problem records integrated with other service management data<br></td><td>High</td></tr><tr><td>Initial problem categorization and assignment</td><td>Workflow management and collaboration tools<p>Service configuration management tools</p></td><td>Management of problem records integrated with other service management data, backlog management, communication, collaboration support, and CI impact assessment</td><td>High</td></tr><tr><td>Problem control process</td><td></td><td></td><td></td></tr><tr><td>Problem investigation</td><td>Analysis and reporting tools<p>Service configuration management tools</p></td><td>Dependencies analysis, what-if analysis, cause and-effect analysis, and modelling</td><td>High</td></tr><tr><td>Known error communication</td><td>Workflow management and collaboration tools</td><td>Communication and collaboration support</td><td>Medium</td></tr><tr><td><em>Error control process</em></td><td></td><td></td><td></td></tr><tr><td>Problem solution development</td><td>Analysis and reporting tools<br>Service configuration management tools</td><td>Solution design and validation</td><td>Medium to very high, depending on the solution architecture</td></tr><tr><td>Problem resolution initiation</td><td>Workflow management and collaboration tools</td><td>Communication and collaboration support</td><td>Medium</td></tr><tr><td>Known error monitoring and review</td><td>Monitoring and event management tools<p>Workflow management and collaboration tools</p></td><td>Collection and overview of information from various sources, data analysis, and team collaboration<p>Verification that known errors exist and workarounds work</p><p>Creating and linking knowledge articles to known errors</p></td><td>Medium to high</td></tr><tr><td>Problem closure</td><td>Workflow management and collaboration tools</td><td>Communication and collaboration support, automatic posts into collaboration tools</td><td>Medium</td></tr></tbody></table>

##### 5.2.1 Recommendations on automation of problem management

The following recommendations can help when applying automation to problem management:

*   **Distinguish between problem control and error control** Whether problems and known errors are different objects or different statuses of the same object in the automation tool, make sure they support clear separation between investigation (problem control) and periodic review and resolution (error control).
*   **Ensure integration with other practices** At the least, it should be possible to link problem records to incident records, change records, configuration items, and services.
*   **Ensure integration with knowledge base(s)** At the least, information about errors and related recommendations (symptoms of possible incidents, workarounds) should be available. Consider integration (and automated analysis) of the vendors’ and suppliers’ knowledge bases, bug reports, release notes and so on. If applicable, capture information shared by other users of the same third-party products about their experience, problems and resolutions.
*   **Pay attention to measurement and reporting from the beginning** Ensure visibility of the problem management status and progress, including the four processes (reactive and proactive identification, problem control and error control).
*   **Leverage machine learning capabilities** Problem identification based on incident records or on monitoring data; cause-effect analysis; impact analysis, search for resolutions, and other activities of the problem management practice can be automated with the use of machine learning (ML). Effective use of ML requires high-quality data and effective integration with various sources of information. If used properly, it can significantly improve the problem management practice.
*   **Automate monitoring of known errors** For known errors requiring periodic control, the conditions of the control can be defined for automated monitoring. For example, if the error is expected to be resolved after a software update is released by a vendor, it is possible to automate monitoring of the updates and notification (or assignment) to a relevant specialist. If a resolution has been applied and a certain type of incident is supposed to be prevented by the resolution, incident monitoring can automatically reassign the problem for further investigation (if the incidents occur), or for review and closure (if the incidents do not occur for an agreed period of time).

## 6. Partners and suppliers

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the ITIL practices for service design, architecture management, and supplier management. Information about dependencies on third-party services is used in all problem management processes.

Partners and suppliers may support the development, management, and execution of the problem management practice. The forms of support include the following:

*   **Performing problem management activities** Some problem management activities can be largely or completely performed by a specialized supplier. Third parties are often involved in problem investigation and resolution. It is important to ensure effective integration of these third parties in the problem-related workflows and information exchange, as well as their adherence to relevant policies.
    
    Problem models should define how third parties are involved in problem control and how the organization ensures effective collaboration with them. This depends on the architecture and design solutions for products, services, and value streams. Quite often, after the correct model is selected for a problem, further consideration of third-party dependencies is needed within the processes of problem and error control.
    
    The problem management practice often discovers errors in third-party products used by the organization. The possibility of solving these errors, and the effectiveness of the solution, depends on multiple factors, including:
    

*   the architecture of the solution
*   the flexibility of the supplier
*   the importance of the service relationship with the organization for the supplier
*   the contract terms and conditions.

It is important to understand how the organization depends on third-party components and how it aims to estalish effective and efficient collaboration with its key suppliers and partners around many activities, including those of the problem management practice.

Where organizations aim to ensure fast and effective problem management, they usually try to agree close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision-making (see the supplier management practice guide for more information).

*   **Provision of software tools** Most software tools used for problem management are shared with other practices. Problem management is never the first management practice to be automated and rarely one of the most important; this sometimes results in problem management requirements being deprioritized, and the practice affected by ineffective or partial use of software tools. It is important to ensure that specific requirements such as the aggregation of problem information from different sources, cross-team collaboration, or changeable impact and categorization, are met by the software tools.
*   **Consulting and advisory** Specialized suppliers who have developed expertise in problem management can help to establish and develop the practice, adopt methods and techniques (such as swarming or ‘5 Why’ analysis), and initially develop the problem models.

## 7. Capability assessment and development

### 7.1 The practice capability levels

The practice success factors described in section 2.4 cannot be developed overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:

**Level 1** The practice is not well organized; it’s performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

**Level 2** The practice systematically achieves its purpose through a basic set of activities supported by specialized resources.

**Level 3** The practice is well defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

**Level 4** The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

**Level 5** The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level 2 to level 5. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to the automation of practices are typically defined at levels 3 or higher because effective automation is only possible if the practice is well defined and organized.

![](Problem%20management%20ITIL%204%20Practice%20Guide/ITIL_Problem_management_7_1.jpg)

Figure 7.1 Design of the capability criteria

This approach results in every practice having up to 30 capability criteria based on the practice PSFs and mapped to the four dimensions of service management. The number of criteria at each level differs; the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

Table 7.1 outlines the capability criteria that are defined in the ITIL maturity model for the problem management practice.

######   
Table 7.1 Problem management capability criteria

<table><tbody><tr><td><strong>PSF</strong></td><td><strong>Criterion</strong></td><td><strong>Dimension</strong></td><td><strong>Capability level</strong></td></tr><tr><td>Identifying and understanding the problems and their impact on services</td><td>The causes of important incidents are identified and investigated</td><td>Value streams and processes</td><td>2</td></tr><tr><td></td><td>The errors in products and services, which might lead to incidents, are identified and investigated</td><td>Value streams and processes</td><td>2</td></tr><tr><td></td><td>Problem identification and control address the errors in technology solutions</td><td>Information and technology</td><td>3</td></tr><tr><td></td><td>Problem identification and control address the errors within the organization</td><td>Organizations and people</td><td>3</td></tr><tr><td></td><td>Problem identification and control address the errors in third-party services and dependencies</td><td>Partners and suppliers</td><td>3</td></tr><tr><td></td><td>Problem identification and control address the errors in value streams, processes, and other workflows</td><td>Value streams and processes</td><td>3</td></tr><tr><td></td><td>Problem identification and control are integrated into value streams</td><td>Value streams and processes</td><td>3</td></tr><tr><td></td><td>Problem identification and control information is tracked and managed using an integrated information system</td><td>Information and technology</td><td>3</td></tr><tr><td></td><td>The competencies required to identify and investigate problems are identified and qualified human resources are available</td><td>Organizations and people</td><td>3</td></tr><tr><td></td><td>Problem identification and control are integrated across the organization’s supply network</td><td>Partners and suppliers</td><td>4</td></tr><tr><td></td><td>The effectiveness of problem identification and control is measured and reported</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>The effectiveness of problem identification and control is regularly reviewed and continually improved</td><td>Value streams and processes</td><td>5</td></tr><tr><td>Optimizing problem resolution and mitigation</td><td>Where reasonably possible, errors in products and services are fixed</td><td>Value streams and processes</td><td>2</td></tr><tr><td></td><td>Where errors cannot be fixed, they are controlled and mitigated</td><td>Value streams and processes</td><td>2</td></tr><tr><td></td><td>When error resolutions are considered, they address the technology solutions</td><td>Information and technology</td><td>3</td></tr><tr><td></td><td>When error resolutions are considered, they address the organization and competencies</td><td>Organizations and people</td><td>3</td></tr><tr><td></td><td>When error resolutions are considered, they address third-party services and dependencies</td><td>Partners and suppliers</td><td>3</td></tr><tr><td></td><td>When error resolutions are considered, they address value streams, processes, and other workflows</td><td>Value streams and processes</td><td>3</td></tr><tr><td></td><td>Information about known errors is tracked and managed using an integrated information system</td><td>Information and technology</td><td>3</td></tr><tr><td></td><td>Known errors are regularly reviewed and the relevant information is updated</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>The effectiveness of the error control is measured and reported</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>The effectiveness of the error control is regularly reviewed and continually improved</td><td>Value streams and processes</td><td>5</td></tr></tbody></table>

These capability criteria can be used by organizations for self-assessment and improvement of the practice.

###   
7.2 Capability self-assessment

The self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team in the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed.

1.  Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
2.  If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider’s employees.
3.  If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
4.  If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met; what is missing in the organization? Why? How can it affect the quality of the IT products and services? What can be done to meet the criteria that are currently missed?
5.  The same approach is applied at every next level; the practice is considered to be at the level at which all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.

### 7.3 Problem management capability development

Management practices should support the achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability, however achieving the highest capability level should never be the aim for all practices. There is no organization that requires all management practices to be at capability level 5. A higher capability level provides higher assurance of the fulfilment of a practice’s purpose, but this also comes with an increase in costs (for instance for management, automation, or training). To achieve optimal performance with a sufficient level of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

![](Problem%20management%20ITIL%204%20Practice%20Guide/ITIL_Problem_management_7_2.jpg)

Figure 7.2 The capability development steps and levels

###### Table 7.2 The problem management capability development steps

<table><tbody><tr><td><strong>C</strong><strong>apability level</strong></td><td><strong>Define, agree, and implement</strong></td><td><strong>Comment for problem management</strong></td><td><strong>Chapter (for recommendation</strong>s)</td></tr><tr><td>2</td><td>Purpose and objectives<br>Scope</td><td>Key sources of problem identification</td><td>2.1<br>2.3</td></tr><tr><td></td><td>Process and activities<br>Roles and responsibilities<br>Tools and procedures</td><td>Workflows; problem identification; investigation and resolutions; roles and responsibilities</td><td>2.2, 3.1<br>4<br>5</td></tr><tr><td>3</td><td>Dependencies and integration</td><td>Automation and information exchange, use of an integrated service management system</td><td>5</td></tr><tr><td></td><td></td><td>Suppliers and other parties involved in problem management</td><td>6</td></tr><tr><td>4</td><td>Measurement and reporting</td><td>Metrics</td><td>2.5</td></tr><tr><td>5</td><td>Continual improvement</td><td>Regular review of the practice and the problem management capability development</td><td>2.4, 2.5, 7</td></tr></tbody></table>

## 8. Recommendations for practice success

### 8.1 Problem management is a practice, not just a set of activities

Successful problem management requires a combination of people with relevant skills, effective automation, and effective cooperation between internal teams and with third parties.

A common misconception is that problem management is an administrative process, whereas in fact it needs collaboration across the teams, enabled by management involvement and support.

Problem management is a business-led practice, which supports quality, efficiency, risk reduction and creation of business value.

###   
8.2 Getting started

Start where you are and progress iteratively with feedback. There is no need to cover all types of problems in all products from day one. Use the capability criteria (see section 7.2) as guidance. Start identifying problems in the most critical products and services and then develop the capabilities and expand the scope to increase business value from the practice.

It is important consider the who the right person or people are to drive the practice development:

*   Do they understand the value and definition of problem management?
*   Do they have the right skills for the relevant phases of the practice?
*   What do they need from the leadership to support the practice and ensure that it is understood across the organization?

###   
8.3 Making problem management work

Once the first problems have been identified, it is useful to look at data on the backlog, identify links with incidents and changes, look at other relevant activities happening in the organization, and seek out feedback from users on what is really affecting them. Context is important to fully understand the problems.

Business value is the key driver for problem investigation and resolution. Management support is often needed to approve investment or resource allocation. This requires a clear definition of the risks, opportunities, costs and benefits, not simply the technical issues. Problem management should be able to present this information clearly and simply to the decision makers.

Visibility and transparency of problems and their impact is also recommended. The more people across an organization can see what the top problems are, the more chances that their previous experience may be useful for the investigation and resolution.

A simple way to test whether problem management is working is to check if the prioritized list of problems is known and agreed upon by key stakeholders, particularly the leadership team.

###   
8.4 Demonstrating value to the organization

It is not uncommon for organizations to have defined and implemented a problem management workflow, and yet still not be able to demonstrate its business value. This highlights the fact that success in problem management requires focus on people, collaboration, and business focus, as much as on process and technology.

Although there are useful metrics that can be used to evaluate the performance of the practice (see section 2.5), its value should be articulated in business terms:

*   Showing the decrease in costs and losses from the reduction of incidents and service interruptions
*   Identifying the reduced risk levels associated with the prevention of incidents and resolution of problems
*   Demonstrating improvements in customer/user satisfaction ratings due to reduced interruptions and improved service quality
*   Highlighting the quality improvements in service delivery and performance achieved through problem resolution
*   Showing the return on investments in upgrades, legacy removals, replacements, resource changes, and use of external services.

It is important to show the value of problem management to the organization in order to maintain support and investment in the practice.

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:

*   focus on value
*   start where you are
*   progress iteratively with feedback
*   collaborate and promote visibility
*   think and work holistically
*   keep it simple and practical
*   optimize and automate.

Table 8.1 outlines recommendations for the success of the problem management practice, linked to the relevant guiding principles.

######   
Table 8.1 Recommendations for the success of problem management

<table><tbody><tr><td><strong>Recommendation</strong></td><td><strong>Comments</strong></td><td><strong>ITIL guiding principles</strong></td></tr><tr><td>Start logging problems, now</td><td>This starts to build up data<p>This also gets people to think about long term problems and remove barriers to getting them raised and fixed. They might, for example, be concerned that they will have to take on the problem, and so not log it.</p></td><td>Start where you are<p>Keep it simple and practical</p></td></tr><tr><td>Think carefully about getting the right people in problem roles</td><td>The people doing problem management roles and tasks need to have the right skills and attributes for the relevant phases<p>This includes</p><p>Data analytics, reporting, trends analytics, information presentation<br>Risk analysis, business case analysis<br>Project management, leadership, influencing and communications skills</p></td><td>Focus on value<p>Think and work holistically</p><p>Keep it simple and practical</p></td></tr><tr><td>Problem management is not an administrative function</td><td>Some administrative skills are required to manage work and promote issues, but this is not the main function or value of problem management<p>Problem management wont simply work by itself, particularly when starting the practice; this needs drive and focus</p></td><td>Think and work holistically<p>Keep it simple and practical</p></td></tr><tr><td>The problem manager or problem team won’t fix all the problems</td><td>Problems need to be owned and acted upon by the whole business/team/department.<p>Problem management facilitates (business) fixes rather than delivering all (technical) fixes</p><p>Those raising problems are not necessarily the same as those who will fix them</p></td><td>Collaborate and promote visibility<p>Keep it simple and practical</p></td></tr><tr><td>Prioritize problems in order of value to the organization</td><td>Risk, opportunity, cost and quality should drive prioritization not technical or team focus.<p>Problems should be highlighted in business terms for approval/decision on action</p></td><td>Focus on value<p>Keep it simple and practical</p></td></tr><tr><td>Publish a list of top business problems</td><td>Transparency of current high priority problems ensures focus and shared goals<p>Everyone should know the list of top problems</p><p>Open visibility also helps to use the cumulative experience across a team to speed up ideas and actions for resolution</p></td><td>Focus on value<p>Collaborate and promote visibility</p><p>Keep it simple and practical</p></td></tr><tr><td>Problem Management needs a swarming approach</td><td>Problems will often be raised through the tiered support model, but this is not always effective when collaboration and management support is needed<p>All technical teams should be expected to participate in collaborative problem-solving activities and swarm teams</p></td><td>Focus on value<p>Collaborate and promote visibility</p></td></tr><tr><td>SLAs don’t apply to problems, but problem management improves service quality</td><td>Problems are not predictable and don’t always follow a linear process path<p>Problem management should be measured and appreciated as a contributor to business value, for reporting</p><p>Problem management can also be used to drive improvement targets for incident reduction</p></td><td>Focus on value<p>Progress iteratively with feedback</p><p>Start where you are</p><p>Keep it simple and practical</p></td></tr><tr><td>Get user/customer input on their problems</td><td>It is essential to get end user feedback on their problems (which also might not be defined or logged)<p>It is also beneficial to get an external view on what really matters to the business</p></td><td>Progress iteratively with feedback<p>Focus on value</p><p>Keep it simple and practical</p></td></tr><tr><td>Use AI and automation tools where possible</td><td>AI can interrogate data to identify trends<p>For example, AI and RPA can be used to remove repeat and underlying issues</p></td><td>Optimize and automate</td></tr></tbody></table>

## 9. Acknowledgements

PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following people.

##### authors

Barry Corless, Roman Jouravlev, Andrew Vermes

##### reviewers

James Ainsworth, Akshay Anand, Sofi Fahlberg, Michael G. Hall, Steve Harrop, Piia Karvonen, Anton Lykov, Paula Määttänen, Caspar Miller, Christian F. Nissen, Mark O’Loughlin, Tatiana Orlova, Elina Pirjanti, Stuart Rance

##### 2023 revision

David Cannon, Antonina Douannes, Peter Farenden, Adam Griffith, Roman Jouravlev, Kaimar Karu, Barclay Rae, Stuart Rance, Nicola Reeves
