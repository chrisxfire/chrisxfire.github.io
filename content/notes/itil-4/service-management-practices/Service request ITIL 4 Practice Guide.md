---
title: "Service request"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# 1. Source
Axelos International (https://www.axelos.com)

# 2. Overview
<table><tbody><tr><td><strong>Key message</strong></td></tr><tr><td>The purpose of the service request management practice is to support the agreed quality of a service by handling all predefined, user-initiated service requests in an effective and user- friendly manner.</td></tr></tbody></table>

Service request management presents a significant value proposition for both the service consuming organization and the service providing organization.

Benefits for the service provider include:
* clear and structured patterns and methods of working
* reduced costs associated request handling and fulfilment
* realistic fulfilment expectations and higher resulting levels of user satisfaction
* fulfilment of SLAs with service consumers
* improved standing or reputation with the service consumer due to higher service quality and clear user expectations.

Benefits for the service consumer include:
* convenient methods of service request submission
* predictable and timely handling and fulfilment of service requests
* minimized impact to business operations
* higher employee satisfaction.

<table><tbody><tr><td><strong>Definition: Service request</strong></td></tr><tr><td>A request from a user or a user’s authorized representative that initiates a service action which has been agreed as a normal part of service delivery.</td></tr></tbody></table>

Service requests are an important type of user query and an important part of the user experience. Typically, service requests include the following:
* a request initiating a service action (performed by the service provider or jointly with the user)
* a request for information
* a request for access to a resource, service, or service offering
* feedback, compliments, or complaints.

Fulfilling service requests may include changes to services or their components, usually as standard changes. As service requests are predefined and pre-agreed as a normal part of service delivery, they should be formalized with clear, standard procedures for initiation, approval, fulfilment, and management. Some service requests have very simple workflows, such as a request for information. However, the fulfilment of other service requests, such as the onboarding of a new employee, may be complex and require contributions from many teams and systems. Regardless of the complexity, the steps to fulfil the request should be well-known and tested. This allows the service provider to agree times for fulfilment and provide clear communication of the status of the request to users.

The development and testing of the procedures are performed at the respective stages of the product and service lifecycle and involve multiple practices, such as business analysis, service design, risk management, change enablement, service catalogue management, and service level management, among others.

Some service requests require authorization, according to financial, information security, or other policies. To handle this appropriately, the service request management practice should follow these guidelines:
* service requests and their fulfilment should be standardized and automated as much as possible
* policies should be established depending on which service requests can be fulfilled with limited or no additional approvals to streamline fulfilment
* the creation, submission, and fulfilment of requests should be shifted left to the greatest extent possible by empowering users through self-service techniques, such as embedding links to appropriate forms within knowledgebase articles, portals, policy documents, frequently asked question lists, etc.
* user expectations regarding fulfilment times should be clearly set based on what the organization can deliver
* opportunities for improvement should be identified and implemented to produce faster fulfilment times and leverage automation
* policies and workflows should be included for documenting all requests and redirecting any that are incorrectly submitted as service requests, but should actually be managed as incidents or changes.

Some service requests can be completely fulfilled by automation, from submission to closure, allowing for a complete self-service experience. For example, client software installation, SaaS license allocation and access, or the provision of on-premise or IaaS virtual servers. As organizations become more digital, they will inherently seek opportunities to fulfil service requests entirely through automation.

Service requests can be practically anything that requires a controlled procedure to fulfil. This can lead a some ‘grey areas’ for what is considered to be a service request.

What an organization defines as a request will depend upon how they define their services. If the organization’s services are defined exclusively from the service provider’s perspective, there is a danger that the service provider will consider everything that they do for a consumer to be a requestable service. If the organization’s services are defined exclusively from the service consumer’s point of view, any logistical activities required for request fulfilment are likely to be masked through classifications like SOP (standard operating procedure) or IMAC (install, add, move, change). Organizations must strike an appropriate balance.

Standardized processes (i.e. risk analysis as part of change enablement) should be excluded from consideration as service requests, as well. A team that is evaluating a change is executing change enablement, not service request management. Service request management should define, optimize, and automate fulfilment procedures – not the processes of other practices.

## 2.2 Terms and concepts
The main characteristics of a service request include the following:
* It is initiated by a user or a user representative.
* It requires an action from the service provider.
* It triggers one or more actions that have an agreed upon service outcome. This means the service outcome was tested in advance, the approval flow and fulfilment flow for the request were pre- approved, people were trained, and service components were setup to fulfil it.

A service request is a normal part of service delivery, which is ‘business as usual’. This means the results and the timelines are usually predictable and well understood by the customer, users, and operational teams of the service provider. Wherever possible, service requests should be automated and accessible through multiple channels (or omni-channel) that are efficient and convenient for users, such as self- service portals, social media sites, mobile applications, links embedded within knowledgebase articles, live agent chat, artificially intelligent chatbots, and email to ticket conversion.

Service requests, and their fulfilment, may impact service quality, as well as the service or consumer experience. They can support service utility when service actions are a key form of service interaction. Service requests can also facilitate moving to a higher service level. They can be used to request additional standard functionality or utility to an existing service. Service requests can initiate the maintenance of service components where the service provider’s monitoring and event management capability is limited, and the monitoring of service components is delegated to users.

Service requests are a form of user query and a way to initiate certain predefined activities significant to service experience. The same activities may be initiated differently, and although technical operations may be identical, their role in the user experience would be different, as shown in Table 2.1.

##### Table 2.1 Examples of using different records and workflows involving the same operating procedures
<table><tbody><tr><td><strong>Example</strong></td><td><strong>Records</strong></td><td><strong>Management pr</strong><strong>actices</strong></td></tr><tr><td>A user monitors the status of a printer. When the printer signals ‘low toner’, the user requests toner refill. The service provider’s technician replaces the toner cartridge. Except for the replacement procedure, printing is not interrupted.</td><td>Service request</td><td>Service desk<p>Service request management</p><p>Infrastructure and platform management</p></td></tr><tr><td>IA printer communicates its status and events to the operations team. When a ‘low toner’ event occurs, the service provider’s technician replaces the toner cartridge. Except for the replacement procedure, printing is not interrupted.</td><td>Event</td><td>Monitoring and event management<p>Infrastructure and platform management</p></td></tr><tr><td>In this case, something has gone wrong in the above scenarios. The ‘low toner’ status is not reported in time (the cartridge is not replaced in time, or is replaced incorrectly). The printing is interrupted. Users report the situation to the service provider. The service provider’s technician replaces the toner cartridge. Printing is restored.</td><td>Incident</td><td>Service desk<p>Incident management</p><p>Infrastructure and platform management</p></td></tr></tbody></table>

Similarly, service requests may initiate changes. These are usually standard changes, but can sometimes trigger a normal change. The need for change is defined by the change typology adopted by the organization. There is mandatory correlation between service requests and changes. For example, moving an employee from one desk to another within the office is likely to be managed as a service request; whether it needs a change or multiple changes, depends upon the technical impact of the move and the criteria for changes agreed by the organization as part of the change enablement practice. Some service requests of this type may need one or more changes while others would be fulfilled without the change enablement practice involved.

Frequently, the lifecycle of a service request proceeds through a series of common phases or stages that include:
* submission
* assessment and assignment
* fulfilment
* progress-tracking and potential escalation
* closure and evaluation
* follow-up
* review and analysis.

This service request lifecycle always utilizes multiple practices. A typical value stream to fulfil a service request is likely to involve:
* service desk: to process the user query
* service request management: to route and guide the request fulfilment
* infrastructure and platform management: to perform the necessary technical operations
* release management: to make the service components available to users
* change enablement: to coordinate the necessary changes
* information security management: to provide or modify access.

Other practices may be integrated, as needed. The synergies and procedures for fulfilling every type of service request are documented within service request models.

#### 2.2.1 Service request models
**Definition: Service request model**  
A repeatable predefined approach to the fulfilment of a particular type of service requests.

Service request models are usually produced during product and service design. The models are tested and deployed to operations along with other components of the service. The service request management practice is involved at all stages to ensure that the models are realistic and accepted by everyone engaged or participating in their management and execution. The continual improvement of products and services may include the improvement of the related service request models.

Service request models describe the conditions and procedures for service request fulfilment, covering all four dimensions of service management:
* procedures and workflows, including possible options and decisions
* roles and teams responsible (usually as a RACI matrix)
* automation and tools used
* third parties involved in and supporting agreements.

As service requests are initiated by users or their representatives, they should be available to users in a convenient and actionable way. The most common approach is to include the available service requests in user-facing views of the organization’s service catalogue. Management of the catalogue is within the scope of the service catalogue management practice, but information for it is provided by the service request management practice.

#### 2.2.2 Request catalogue
**Definition: Request catalogue**  
A view of the service catalogue, providing details on service requests for existing and new services, which is made available to the user.

Usually, the following information about the available service requests is documented in a request catalogue:
* service(s) to which a service request belongs, directly or indirectly
* prerequisites/conditions for a service request invitation
* information required to initiate the request
* approval workflow, if applicable
* target fulfilment time
* other relevant information.

What the organization defines to be service requests must be contained within the request catalogue. Requests in the request catalogue are not necessarily services. They can be a request for action to be taken directly or indirectly relative to a service.

The service request catalogue view is expected to be tailored for service level agreements (SLAs) that are applicable to the user accessing the view, so that all information reflects the conditions and targets agreed for the user. The more relevant the information in the request catalogue is, the more efficient the service request fulfilment will be, and the higher the user satisfaction. Refer to the service catalogue management practice guide for more information about customizing catalogue views.

## 2.3 Scope
The scope of the service request management practice includes:
* managing service request models
* processing service requests submitted by users or their representatives
* managing the fulfilment of service requests according to the agreed models
* reviewing and continually improving request processing and fulfilment performance.

There are several activities and areas of responsibilities that are not included in the service request management practice, although they are closely related to service request management. They are listed in Table 2.2, along with references to the practices in which they can be found. Management practices should be combined to form service value streams, as described in section 3.2.  

##### Table 2.2 Activities related to the service request management practice described in other practice guides
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Practice guide</strong></td></tr><tr><td>Resolving incidents</td><td>Incident management</td></tr><tr><td>Communicating with users</td><td>Service desk</td></tr><tr><td>Management and realization of changes to products and services</td><td>Change enablement<p>Deployment management</p><p>Release management</p></td></tr><tr><td>Monitoring services and technology</td><td>Monitoring and event management</td></tr><tr><td>Ongoing management and implementation of improvements</td><td>Continual improvement</td></tr><tr><td>Management of request catalogue</td><td>Service catalogue management</td></tr><tr><td>Management and provision of access to services</td><td>Information security management</td></tr><tr><td>Creating service request models</td><td>Service design</td></tr></tbody></table>

## 2.4 Practice success factors
<table><tbody><tr><td><strong>Definition: Practice success factors</strong></td></tr><tr><td>A complex functional component of a practice that is required for the practice to fulfil its purpose.</td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity as it includes components from all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The service request management practice includes the following PSFs:
* ensuring that the service request fulfilment procedures for all services are optimized
* ensuring that all service requests are fulfilled according to the agreed procedures and to user satisfaction.  
    

#### 2.4.1 Ensuring that the service request fulfilment procedures for all services are optimized
The development of the service request procedures should be integrated early into the product and service lifecycle management. The service request practice should contribute to business analysis, architecture management, and service design activities. Depending on the decisions that are made at those stages, a service may be optimized for a no-request operation or include multiple requests available to users as a part of normal consumption. In the first case, generic requests, such as compliments, complaints, or how-to requests are still available to service users. In the second case, there may be various requests specific to service utility. The fulfilment of these requests becomes an important contributor to service quality. Service requests can also be a differentiator between different levels of service offerings. For example, more requests may be available to users of higher trims of the service.

It is important to identify, document, and test service request fulfilment procedures and assign responsibilities for the activities. It is equally important to ensure that requests are correctly described in a request catalogue and that the catalogue is available to the users who should be able to initiate the requests. This is achieved in conjunction with the service catalogue management practice.

Service request fulfilment procedures should be subject to continual improvement based on the monitoring of fulfilment performance and user satisfaction. One way to optimize the fulfilment procedures is to automate them wherever reasonably possible. This applies to the most popular and routine requests that have limited variations in fulfilment workflows. Tailored, complex, and rare requests should be automated only after careful consideration to ensure that the costs and risks of automation are justified.

Service request fulfilment procedures are documented within the service request models, along with resources, responsibilities, and other relevant information.

#### 2.4.2 Ensuring that all service requests are fulfilled according to the agreed procedures and to user satisfaction
If the fulfilment procedures are optimized and documented, and responsibilities are clear, service requests are easy to plan and fulfil. Statistics on every type of request can help to optimize resource planning and to ensure the timely processing of all requests. Unlike incidents, service requests do not need to be fulfilled urgently; they allow for more comfortable planning and should be completed within an agreed timeframe.

Requests may require a review after fulfilment. The review can be limited to a satisfaction survey or include a detailed internal review (usually necessary if something went wrong, or user satisfaction is low).

## 2.5 Key metrics
The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the service request management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the service request practice to the effectiveness and efficiency of those value streams. The key metrics are listed in Table 2.3.

##### Table 2.3 Key metrics for service request management
<table><tbody><tr><td><strong>Practice success factors</strong></td><td><strong>Key metrics</strong></td></tr><tr><td>Ensuring that the service request fulfilment procedures for all services are optimized</td><td>Completeness of the service request catalogue; number and percentage of service requests that are not supported with fulfilment procedures<p>Number and percentage of service requests that could not be fulfilled by following the agreed procedure due to errors/inefficiencies in the procedure</p><p>Satisfaction of the team members fulfilling the requests with instructions provided</p><p>Average time and cost needed to fulfil requests (by types/models)</p><p>Percentage of service requests with fully or largely automated fulfilment (number, percentage in the catalogue, percentage in total number, and fulfilment time)</p></td></tr><tr><td>Ensuring that all service requests are fulfilled according to the agreed procedures and to user satisfaction</td><td>Number and percentage of requests fulfilled according to the SLA<p>Impact of incidents caused by the incorrect fulfilment of service requests</p><p>User satisfaction with request fulfilment</p><p>Number and percentage of requests fulfilled with deviations from the agreed procedures</p></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make them easier to use for the ongoing management of value streams and for the periodic assessment and continual improvement of the service request management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

# 3. Value streams and processes
## 3.1 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><strong>Definition: Process</strong></td></tr><tr><td>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</td></tr></tbody></table>

Service request management activities form two processes:
* service request fulfilment control
* service request review and optimization.

#### 3.1.1 Service request fulfilment control
This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

##### Table 3.1 Inputs, activities, and outputs of the service request fulfilment control process
<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Service request queries</td><td>Request categorization</td><td>Fulfilled service requests</td></tr><tr><td>Service request models</td><td>Service request model initiation and control</td><td>Fulfilment actions records and reports</td></tr><tr><td>Service level agreements</td><td>Ad hoc fulfilment control</td><td>User satisfaction surveys</td></tr><tr><td>Fulfilment actions records and reports</td><td>Fulfilment review</td><td></td></tr></tbody></table>

Figure 3.1 shows a workflow diagram of the process.

Figure 3.1 Workflow of the service request fulfilment control process:  
![Figure 3.1 Workflow of the service request fulfilment control process](Service%20request%20ITIL%204%20Practice%20Guide/ITIL_Service_Request_3_1.jpg)

The process may vary depending on the service request model. Table 3.2 provides an example of variations.

##### Table 3.2 Service request fulfilment control process activities
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Manual or incomplete service request model</strong></td><td><strong>Highly automated service request model</strong></td></tr><tr><td>Request categorization</td><td>All the prerequisites for the service request and user eligibility are checked in a completely or partially manual fashion. Missing information or paperwork is requested from the user.<p>The service desk agent chooses the appropriate service request model.</p></td><td>In a highly automated environment, a service request is automatically checked for all the prerequisites. If additional information or paperwork is needed, the system contacts the user and asks for the missing prerequisites.<p>An appropriate model and set of automated procedures are chosen based on the service request characteristics.</p></td></tr><tr><td>Service request model initiation and control</td><td>The service desk agent may need to manually select the right support team or specialists, according to the service request model. The assigned teams follow the service request fulfilment procedures defined within the model.<p>If necessary, additional approvals are obtained, according to the service request procedures.</p><p>In some cases, several service request tasks need to be fulfilled. Manual assignment and control by the service desk agent is needed, as well as notifications to the user.</p><p>Responsible teams fulfil the entire service request or specific tasks.</p><p>If necessary, the responsible team updates the relevant configuration items.</p><p>Upon fulfilment, the service request is routed to fulfilment review.</p></td><td>Request fulfilment according to the chosen service request model is initiated and the system controls the flow of procedures and scripts invoked to fulfil the request.<p>Upon fulfilment, the service request is routed to fulfilment review.</p></td></tr><tr><td>Ad hoc fulfilment control</td><td>There are cases when fulfilment of a service request requires some non-standard/tailored work, or there are some new circumstances that were not taken into consideration when the service request was planned.<p>When following the procedure will not produce the desired result, the service request is routed for an ad hoc fulfilment.</p><p>Ad hoc fulfilment is an exception and should be treated as such.</p><p>A decision should be made about whether to act upon the exception or simply deny the fulfilment. This decision is usually defined by the service request model and the way the model handles exceptions.</p><p>Regardless of the decision made, details of a case should become an input into the service request model review and optimization process, so that this case is well-defined and added to the model, or additional checks are categorized and added to triage, to sort such cases out of the model.</p></td><td>N/A</td></tr><tr><td>Fulfillment review</td><td>Service request fulfillment is checked according to the service request model.<p>The fulfilment review should be described by the service request model. The fulfilment review may contain some procedures to check to what extent the fulfilment has produced the desired result.</p><p>The fulfilment review may also involve collecting user feedback and measuring user satisfaction.</p><p>The reports and record of the fulfilment review serve as inputs into the service request review and optimization process.</p></td><td>N/A</td></tr></tbody></table>

#### 3.1.2 Service request review and optimization
The process is focused on the continual improvement of service request models, including their management and execution. It is recommended to perform this process regularly or when trigged by user survey results. This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

##### Table 3.3 Inputs, activities, and outputs of the service request review and optimization process
<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td>Current service request models<p>User survey results</p><p>Related changes and change models</p><p>Policies and regulatory requirements</p><p>Service catalogue</p><p>Service level agreements</p><p>IT asset information</p><p>CMDB</p><p>Capacity and performance information</p></td><td>Service request records and reports analysis<p>Service request model improvement initiation</p><p>Service request model update communication</p></td><td>Updated service request model<p>Updated service request procedures and working instructions</p></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

Figure 3.2 Workflow of the service request review and optimization process:  
![Figure 3.2 Workflow of the service request review and optimization process](Service%20request%20ITIL%204%20Practice%20Guide/ITIL_Service_Request_3_2.jpg)

Table 3.4 provides a description of the process activities.

##### Table 3.4 Activities of the service request review and optimization process
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Description</strong></td></tr><tr><td>Service request records and reports analysis</td><td>The service request practice owner, together with the service owners and other relevant stakeholders, perform a review of the selected service requests and related metrics over the period and/or relevant repeating changes from the change enablement practice. They identify opportunities for new service request models and/or improvement of current service request models.</td></tr><tr><td>Service request model improvement initiation</td><td>The service request practice owner registers the improvement initiatives, which are submitted for processing with the involvement of the continual improvement and/or change enablement practice(s).<p>If testing does not confirm the effectiveness of the proposed service request model, it is returned for further analysis.</p></td></tr><tr><td>Service request model update communication</td><td>If the service request model is successfully updated, it is communicated to the relevant stakeholders. This is usually done by the service request practice owner or the service owner.</td></tr></tbody></table>

## 3.2 Value stream contribution
#### 3.2.1 Service value streams
To perform certain tasks or respond to situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario.

Once designed, value streams should be subject to continual improvement.

<table><tbody><tr><td><strong>Definition: Value stream</strong></td></tr><tr><td>A series of steps an organization undertakes to create and deliver products and services to consumers.</td></tr></tbody></table>

In practice, however, many organizations apply the value stream concept after having worked for a significant span of time, sometimes for years, without value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the current state or ‘as is’ situation, the de-facto flows of work, and to analyze them to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding existing value streams is critical to improving organizational performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services. When combined, the organization’s value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations have been following best practice recommendations for various service management practices, such as service request management, incident management, change enablement, software development, and many others. Service request management is one of the most adopted and mature practices because many organizations often formalize it early in their ITSM journey.

However, the practices have often been adopted and organized in a siloed, isolated manner, just as they were presented in the service management bodies of knowledge. In reality, a flow of work required to facilitate or enable value for a customer or other stakeholder is almost never limited to just as single practice.  

## 3.2.2 Service request management in the service value streams
##### 3.2.2.1 Service request fulfilment value stream
The majority of the service requests received by a service provider cannot be fulfilled solely by the service request management practice. Section 3.1.1 described the activities of request fulfilment control; however, the real-life workflow may include the activities outlined in Table 3.5, which are described within other management practices:

<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Practice</strong></td></tr><tr><td>User query registration and triage</td><td>Service desk</td></tr><tr><td>Request categorization</td><td><strong>Service request management</strong><br>Service catalogue management</td></tr><tr><td>Service request model initiation and control</td><td><strong>Service request management</strong></td></tr><tr><td>Request fulfilment according to the model</td><td>One or more of the following:<br>Change enablement<br>Deployment management<br>Release management<br>Service desk<br>Infrastructure and platform management<br>Software development and management<br>Supplier management<br>Workforce and talent management<br>Knowledge management<br>Service financial management</td></tr><tr><td>Ad hoc fulfilment control</td><td><strong>Service request management</strong></td></tr><tr><td>Ad hoc request fulfilment</td><td>One or more of the following:<br>Change enablement<br>Deployment management<br>Release management<br>Service desk<br>Infrastructure and platform management<br>Software development and management<br>Supplier management<br>Workforce and talent management<br>Knowledge management<br>Service financial management</td></tr><tr><td>Fulfilment review</td><td><strong>Service request management </strong>Knowledge management<br>Continual improvement</td></tr></tbody></table>

The service request management practice is core to this value stream, but it is not adequate to complete the entire value stream and ensure value co-creation.

ITIL 4 recommends that organizations examine how they perform work and map all the value streams they can identify. This enables a current state analysis that can identify any barriers or constraints within the workflow, as well as any non-value-adding activities, i.e. waste. Wasteful activities should be eliminated to increase productivity and reduce costs.

Opportunities to increase value-adding activities can be found across the service value chain. These may be new activities or modifications to existing activities, which can make the organization more productive. Value stream optimization may include process automation and/or the adoption of emerging technologies and ways of working to gain efficiencies or enhance user experience.

Value streams should be defined by organizations for all of their products and services. Depending upon the organization’s strategy, value streams can be redefined to react to changing demand and other circumstances, or remain stable for a significant period of time. In any case, they should be continually reviewed and improved to ensure that the organization achieves its objectives in an optimal way.  

##### 3.2.2.2 Service request management in other service value streams
The primary value stream involving service request management is described in section 3.2.2.1. Unlike most other practices, service request management is rarely involved in other value streams.

As defined in section 2.2, service requests:
* are initiated by a user or a user’s authorized representative;
* require an action from the service provider;
* trigger one or more actions that have an agreed upon service outcome. This means the service outcome was tested in advance, the approval flow and fulfilment flow for the request were pre- approved, people were trained, and service components were setup to fulfil it.

Some predefined actions can be initiated by events in the service infrastructure, or be a part of a regular service maintenance – although sometimes the same actions are needed to fulfil a service request, these are different service value streams that do not involve the service request management practice.

The only other service value streams where the service request management practice may contribute, are related to initial design or feedback-based improvement of services and of the related service request models:

Design and development of a new service may involve both the definition of service requests that will be available to the users, as well as of the service request models to ensure effective fulfilment of the requests. The service request management practice can be involved in design, planning, and testing of these request models.

Similarly, request fulfilment review provides an input into continual improvement which may include redesign of the existing or creation of new request models as part of the improvement of the respective products and services. The service request management practice can be involved in design, planning, and testing of these request models.  

### 3.2.3 Analyzing a service value stream
##### 3.2.3.1 The key steps of a service value stream analysis
The following are some simple and practical recommendations for service value stream analysis and mapping:
* **Identify the scope of the value stream analysis**Service value streams can be mapped to a particular product or service or applied to most or all of them. Similarly, service value streams may differ for different consumers; for example, service requests can be fulfilled and communicated differently for internal and external customers, for B2B and B2C products, or for services based on products that are developed in-house or sourced externally.
* **Define the purpose of the value stream from the business standpoint**  
    Since stakeholders define value, it is essential that their concerns are clearly understood. With service request management, the primary stakeholder may be the request initiator or benefactor; however, there are certainly other interested parties to consider. For example, since requests can have financial and/or information security implications, maintaining compliance will require that these aspects are documented and relevant stakeholders are informed. The outcomes of service value streams should be comprehended from the business perspective, not solely from the user perspective.
    
* **Do the service value stream walk**  
    Logically walk through or directly experience the steps and the information flow as they occur in practice (consider the Lean technique of Gemba walk):
    

**a. Identify the workflow steps**

**b. Collect data as you walk**

**c. Evaluate the workflow steps**

Typically, the criteria for evaluation are:

1.  value for the stakeholder (does the step add value for the business stakeholder?)
2.  effectiveness or performance (is the step performed well?)
3.  availability (are required resources available to execute the step?)
4.  capacity (are required resources enough?)
5.  flexibility (are the required resources interchangeable within the step?).

**d. Map the activities and the information flows** In an ideal situation, the flow proceeds smoothly without delays or pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

**e. Create and review the timeline and resource level** Map out process times and lead times for resources and workload through the workflow steps.

* **Reflect on the value stream map (VSM)** Identify factors that might not have been entirely apparent at first. The information previously collected is now used at this step to find the waste.
* **Create a ‘to be’ VSM** This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.
* **Using the ‘to be’ VSM, plan improvements** Refer to the continual improvement practice guide for a practical improvement model.

##### 3.2.3.2 Service request management considerations in a service value stream analysis
To ensure that relevant service request management activities are included in service value streams, the following steps can be added to the above recommendations:
* During scoping (task 1), identify the IT and business services related to the value stream and the involved business stakeholders.
* Make sure the value stream is understood (task 2) from the standpoint of the business, not only of the service provider.
* During the service value stream walk (task 3a), identify other practices involved in the handling or processing of service requests at every step. Which practices provide required information (configuration data, asset data, previously identified solutions, agreed timeline for fulfilment, and so on)? What if fulfilling the service request requires one or more changes? What if fulfilling the service request involves third parties?
* During the workflow steps evaluation (task 3c), evaluate the step’s impact on the fulfilment of a request. Special attention should be paid to steps with low business value, low performance, and availability or capacity issues. It is not unusual to find steps which serve some internal control or bureaucratic purposes but delay request fulfilment.
* At the reflection and planning steps (tasks 4-5), ensure that the service request management flow is optimized for business value throughout the stream, not only within the service request management practice activities.
* Include creation or update of service request models (see section 2.3.2) in the value stream improvement plans (task 6).

# 4. Organizations and people
### 4.1 Roles, competencIes, and responsibilities
The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended.

Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized by a competency profile based on the model shown in Table 4.1.

##### Table 4.1 Competency codes and profiles
<table><tbody><tr><td><strong>Competency code</strong></td><td><strong>Competency profile (activities and skills)</strong></td></tr><tr><td>L</td><td><strong>Leader</strong> Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</td></tr><tr><td>A</td><td><strong>Administrator </strong>Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvement</td></tr><tr><td>C</td><td><strong>Coordinator/communicator </strong>Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</td></tr><tr><td>M</td><td><strong>Methods and techniques expert </strong>Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</td></tr><tr><td>T</td><td><strong>Technical expert</strong> Providing technical (subject matter) expertise and conducting expertise-based assignments</td></tr></tbody></table>

There are no specialist roles specific to the service request management practice. The role of request initiator can be fulfilled by any user or authorized user representative; it does not require special skills or competencies. The key activities of the service request management processes described above are typically performed by the service provider’s technical specialists, service owners, and/or user support agents, but there are little to no competency profiles that are specific to the practice. However, it is essential to establish and maintain effective cooperation and the efficient transfer/tracking of tasks between members of different teams involved in the handling and fulfilment of requests.

Examples of other roles which can be involved in the service request management activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

##### Table 4.2 Examples of roles with responsibility for service request management activities
<table><tbody><tr><td><strong>Activity</strong></td><td><strong>Responsible roles</strong></td><td><strong>Competency profile</strong></td><td><strong>Specific skill</strong><strong>s</strong></td></tr><tr><td><em>Service request fulfilment control process</em></td><td></td><td></td><td></td></tr><tr><td>Request categorization</td><td>User support agent<br>Product owner<br>Service owner<br>Technical specialist</td><td>CTM</td><td>Good knowledge of the organization's products and services<p>Knowledge of service catalogue, SLAs, request models</p></td></tr><tr><td>Service request model initiation and control</td><td>User support agent<br>Service owner<br>Technical specialist</td><td>CAT</td><td>Good knowledge of the service request models and of the service provider organization</td></tr><tr><td>Ad hoc fulfilment control</td><td><p>Service owner<br>Technical team leader<br></p></td><td>CTA</td><td>Good knowledge of products, services, and SLAs<p>Understanding of business needs<br>Authoring to assign resources and plan ad hoc work</p></td></tr><tr><td>Fulfilment review</td><td>Service owner<br>Practice owner<br>Practice manager/coordinator</td><td>MCT</td><td>Good knowledge of products, services, and SLAs<p>Understanding of business needs</p><p>Good knowledge of the service request models and of the service provider organization.</p></td></tr><tr><td><em>Service request and review optimization process</em></td><td></td><td></td><td></td></tr><tr><td>Service request records and reports analysis</td><td>Product owner<br>Service owner<br>Practice owner<br>Practice manager/coordinator</td><td>TM</td><td>Good knowledge of the service and products and service request models</td></tr><tr><td>Service request model improvement initiation</td><td>Practice owner<br>Practice manager/coordinator<br>Product owner<br>Service owner<br>Resource owner<br>ITSM tool consultant</td><td>TCA</td><td>Good knowledge of the service, products, and service request models<p>Good knowledge of available tools and methods</p></td></tr><tr><td>Service request model update communication</td><td>Practice owner<br>Practice manager/coordinator<br>Product owner<br>Service owner<br>Resource owner</td><td>C</td><td>Understanding the service request models<p>Communication skills</p></td></tr></tbody></table>

### 4.2 Organizational structures and teams
It is unusual to see dedicated organizational structures for the service request management practice. This practice is integrated into the daily operational activities of service delivery and facilitated by a team or technicians that are defined in advance within the service request model definition. Usually, the same team structures are used for service request management and incident management. Typically, a service desk acts as the initial point of capturing, reviewing, and actioning or escalating service requests. Please refer to the ITIL 4 service desk practice guide for more information.

However, in situations where services include service requests as part of the service utility, and demand is very high, dedicated teams can be formed to process and fulfil all or some specific types of service requests. In many cases, automation can decrease the need for such teams and improve overall service quality.

# 5. Information and technology
## 5.1 Information exchange
The effectiveness of the service request management practice is based on the quality of the information used. This information includes, but is not limited to, information about:
* Customers, users, and key stakeholders, including service request initiators and any reviewers and/ or approvers
* services, along with the associated service request models and entries in the request catalogue
* partners and suppliers, including information about the services they provide
* policies and requirements which regulate service provision
* stakeholder satisfaction with the practice.

This information may take various forms. The key inputs and outputs of the practice are listed in the value streams and processes section of this guide.

## 5.2 Automation and tooling
The service request management practice can significantly benefit from automation. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to the full automation of activities where technology solutions remove the need for human intervention. Table 5.1 provides a list of the key automation supporting the practice and their most common application.

##### Table 5.1 Automation solutions for the service request management practice
<table><tbody><tr><td><strong>Automation tools</strong></td><td><strong>Application in service request management</strong></td></tr><tr><td>Workflow management and collaboration tools</td><td>Handling of service requests from initiation to fulfilment and review Design, communication, application, and control of service request models</td></tr><tr><td>Monitoring and event management tools</td><td>Support of service request model execution and control<br>Support of ad hoc request fulfilment</td></tr><tr><td>Publishing tools</td><td>Communication of new and improved service request models</td></tr><tr><td>Social media</td><td>Communication of new and improved service request models</td></tr><tr><td>Analysis and reporting tools</td><td>Practice measurement and reporting</td></tr><tr><td>Work planning and prioritization tools</td><td>Planning and tracking of improvement initiatives</td></tr></tbody></table>

Detailed descriptions of how these tools support the practice’s activities are outlined in Table 5.2.

##### Table 5.2 Details of automation of the service request management activities
<table><tbody><tr><td><strong>Process activity</strong></td><td><strong>Means of automation</strong></td><td><strong>Key functionality</strong></td><td><strong>Impact on the e</strong><strong>ffectives of the practice</strong></td></tr><tr><td><em>Service request fulfilment control</em></td><td></td><td></td><td></td></tr><tr><td>Request categorization</td><td>Workflow management and collaboration tools</td><td>Request catalogue management<br>Work assignment<br>Pre-defined routing</td><td>High</td></tr><tr><td>Service request model initiation and control</td><td>Workflow management and collaboration tools</td><td>Work assignment<br>Predefined routing<br>Collaboration, task</td><td>High</td></tr><tr><td>Ad hoc fulfilment control</td><td>Workflow management and collaboration<br>Monitoring and event management tools</td><td>Monitoring work progress<br>Communications<br>Notifications, escalation</td><td>Medium to high</td></tr><tr><td>Fulfilment review</td><td>Workflow management and collaboration tools</td><td>Communication and collaboration<br>Reporting and analytics</td><td>Medium</td></tr><tr><td><em>Service request and review optimization</em></td><td></td><td></td><td></td></tr><tr><td>Service request records and reports analysis</td><td>Analysis and reporting tools</td><td>Statistical analysis of service request workloads and flows</td><td>High</td></tr><tr><td>Service request model improvement initiation</td><td>Workflow management and collaboration tools</td><td>Backlog and workflow management and visualization<br>Communication and collaboration</td><td>Medium to high</td></tr><tr><td>Service request model update communication</td><td>Content management tools<br>Social media<br>Workflow management and collaboration tools</td><td>Mail<br>Push notifications<br>Web portal<br>Awareness posts</td><td>High</td></tr></tbody></table>

#### 5.2.1 Recommendations for automation of service request management
The following recommendations can help when applying automation to service request management:
* **Design for value streams** Some service requests can be fulfilled by one team - potentially the service desk. Others require coordinated actions from multiple groups within and outside the IT service provider. Automation of the full value stream, from request submission to successful fulfilment, rather than just of the initial categorization, is an important requirement. Value streams should be supported by the integration of multiple practices, including service desk, change enablement, release management, knowledge management, and others.
* **Include service request models** Service requests follow a pre-defined model which includes activities, information flow, controls, and communications. An automation solution should allow for the creation, testing, and use of such models.
* **Consider workforce planning and reporting** Service request fulfilment includes standardized and well-known activities performed by pre-assigned roles. The required work time can therefore be planned and reported with sufficient precision, which in turn can be used for accounting, reporting, and billing or charging. If this is applicable for the service provider, make sure that time and labour costs are included both in the service request models and in all financial calculations.
* **Utilize measurement and reporting from the beginning** Creating visibility of the request fulfilment workload and tracking the status of service requests and user satisfaction is essential for understanding the current state of the service request management practice and improving and developing this capability over time. Making this information available via dashboards and analytical reports should be considered a requirement.
* **Ensure that self-help capabilities are available and convenient** Some service requests can be fulfilled by users. User-facing interfaces should be clear, easy to use, informative, and customizable to meet the needs of the organization and the specific requirements of different types of service requests.
* **Consider leveraging super-users** If the organization is likely to involve super users in the fulfilment of any requests, ensure that the software functionality, rights and permissions, and licensing allow for this accommodation to be both affordable and flexible.

# 6. Partners and suppliers
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the practice guides for service design, architecture management, and supplier management.

The following sections describe how third parties can support the service request management practice; however, it is important to remember that service relationships introduce constraints and dependencies, as well as opportunities and support. When the fulfilment of a service request is performed by a third party, the level of service time required for fulfilment, convenience and frequency of communications and so on) may be constrained by the supplier’s policies and operating. This can conflict with user expectations and is often challenging to change or influence. In other cases, service requests are fulfilled by the service provider, but the fulfilment is constrained by the supply of components, or the execution of activities by a third party. These and other similar dependencies should be reflected in service level agreements and procedures. Communications with customers and users should be routine and transparent to establish realistic expectations and smooth request fulfilment. The supplier management practice should also be used to ensure that, where reasonably possible, third parties adjust their level of service to the needs of the organization.

Partners and suppliers may support the development, management, and execution of the service request management practice. The potential forms of support are outlined in the following sections.

### 6.1 Performing service request management activities
Some service request management activities can be largely or completely performed by a specialized supplier. Due to the characteristics of service requests, such as being pre-defined, pre-approved, and predictable, it is common for organizations to outsource all or part of service request management. It is important to ensure effective integration of third parties in the request-related workflows and information exchange, as well as their adherence to relevant policies. Service request management has a direct impact on user satisfaction and the use of third parties can have both positive and negative impacts on the value of the service.

Service request models should define how third parties are involved in service request fulfilment and how the organization ensures effective collaboration. This will depend on the architecture and design solutions for products, services, and value streams. Nonetheless, the optimization of service request models supporting these solutions will involve the service request management practice.

Defined standard interfaces may become an easy way to communicate conditions and requirements for a supplier to become a part of the organization’s ecosystem. The description of such interfaces may include rules of data exchange, tools, and processes that will create a common language in a multi- vendor environment.

#### 6.1.1 Service integration and management
Service integration and management (SIAM) refers to an approach whereby organizations manage and integrate multiple suppliers in a value stream. SIAM can be delivered using different models, although the basic concept, that the delivery of outsourced products and services is managed by a single entity, regardless of the number of vendors, remains the same.

There are four main models in this area (Figure 6.1). Organizations must consider the best model for their circumstances in order to transition to a more coordinated service-supplier landscape:
* Retained service integration: Where the retained organization manages all vendors and coordinates the service integration and management function itself.
* Single provider: Where the vendor provides all services as well as the service integration and management function.
* Service guardian: Where a vendor provides the service integration and management function, and one or more delivery functions, in addition to managing other vendors.
* Service integration as a service: Where a vendor provides the service integration and management function and manages all the other suppliers, even though the vendor does not deliver any services to the organization.

SIAM is increasing in importance, owing to a variety of factors:
* Vendors increasingly specialize in niche areas, which has led to an increased number of vendors working with a single typical organization.
* The commodification of some types of service component means that vendors can be regularly replaced by other vendors to leverage a better pricing or service experience.
* The increasing complexity of technology products and services means using multiple vendors to support the organization.

When an organization chooses a SIAM approach, it should regard the approach as a strategic imperative and tender SIAM contracts separately from individual vendor contracts. A clear organizational structure, with an appropriate governance and management model, is also required.

Figure 6.1 Service integration models:  
![Figure 6.1 Service integration models](Service%20request%20ITIL%204%20Practice%20Guide/ITIL_Service_Request_6_1.jpg)

Where organizations aim to ensure a fast and effective service request management practice, they usually try to agree to close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision-making. Refer to the supplier management practice guide for more information.

## 6.2 Provision of software tools
Most software tools used for service request management are shared with other practices. However, implementation and use of integrated service management information systems or suites often starts with automating service request management (and service desk) activities. In this case, the owner of the service request management practice and the managers of the teams involved in service request management should define requirements and interact with other teams and practices of the service provider to ensure that the required tools are procured, implemented, and used in an optimal way.

## 6.3 Consulting and advisory
Specialized suppliers who have developed expertise in service request management can help establish and develop the practice, adopt methods and techniques (such as automation), and initially develop service request models.

# 7. Capability assessment and development
## 7.1 The practice capability levels
The practice success factors described in section 2.4 cannot be accomplished overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:
**Level 1** The practice is not well organized; it is performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

**Level 2** The practice systematically achieves its purpose through a basic set of activities supported by specialized resources.

**Level 3** The practice is well defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

**Level 4** The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

**Level 5** The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level two to level five. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to the practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well defined and organized.

Figure 7.1 The design of the capability criteria:  
![Figure 7.1 The design of the capability criteria](Service%20request%20ITIL%204%20Practice%20Guide/ITIL_Service_Request_7_1.jpg)

This approach results in every practice having up to 30 capability criteria based on the practice success factors (PSFs) and mapped to the four dimensions of service management. The number of criteria at each level differs; the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

Table 7.1 outlines the capability criteria that are defined in the ITIL maturity model for the service request management practice.  

##### Table 7.1 Service request management capability criteria
<table><tbody><tr><td><strong>PSF</strong></td><td><strong>Criterion</strong></td><td><strong>Dimensions</strong></td><td><strong>Capability level</strong></td></tr><tr><td>Ensuring that the service request fulfilment procedures for all services are optimized</td><td>Service request fulfilment procedures are defined and agreed for the key user-facing services</td><td>Value streams and processes</td><td>2</td></tr><tr><td></td><td>Responsibilities for request fulfilment are clearly defined</td><td>Value streams and processes</td><td>3</td></tr><tr><td></td><td>Service request fulfilment procedures are aligned with relevant standards and approaches adopted by the organization</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>The effectiveness of the service request fulfilment procedures is monitored and evaluated</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>Service request fulfilment procedures are regularly reviewed and continually improved</td><td>Value streams and processes</td><td>5</td></tr><tr><td>Ensuring that all service requests are fulfilled according to the agreed procedures and to user satisfaction</td><td>Service requests are usually fulfilled within agreed service levels</td><td>Value streams and processes</td><td>2</td></tr><tr><td></td><td>User satisfaction with fulfilment of service requests is measured and reported</td><td>Value streams and processes</td><td>2</td></tr><tr><td></td><td>The competencies requires to fulfil and manage service requests are identified, and qualified human resources are available</td><td>Organizations and people</td><td>3</td></tr><tr><td></td><td>Communication and other technology solutions to fulfil and manage service requests are identified and implemented</td><td>Information and technology</td><td>3</td></tr><tr><td></td><td>Third-party services required to fulfil and manage service requests are identified and available</td><td>Partners and suppliers</td><td>3</td></tr><tr><td></td><td>The effectiveness, efficiency, and user satisfaction with request fulfilment are measured and assessed in the context of the value streams</td><td>Value streams and processes</td><td>4</td></tr><tr><td></td><td>Request fulfilment is regularly reviewed and continually improved</td><td>Value streams and processes</td><td>5</td></tr></tbody></table>

These capability criteria can be used by organizations for self-assessment and improvement of the practice.

## 7.2 Capability self-assessment
The self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team within the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed:

1.  Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
2.  If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider employees.
3.  If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
4.  If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met. What is missing in the organization? Why? How can it affect service request management and fulfilment? What can be done to meet the criteria that are currently missed?
5.  The same approach is applied at every next level; the practice is considered to be at the level where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.

## 7.3 Service request management capability development
Management practices should support achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at capability level 5. Higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but it comes at a price: the cost of management, automation, and training, for example. To achieve optimal performance with sufficient levels of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

Figure 7.2 The capability development steps and levels:  
![Figure 7.2 The capability development steps and levels](Service%20request%20ITIL%204%20Practice%20Guide/ITIL_Service_Request_7_2.jpg)

##### Table 7.2 The service request management capability development steps
<table><tbody><tr><td><strong>Capability level</strong></td><td><strong>Define, agree, and implement</strong></td><td><strong>Comment for service request management</strong></td><td><strong>Chapter (for recommendation</strong><strong>s)</strong></td></tr><tr><td>2</td><td>Purpose and objectives<br><span>Scope</span></td><td>Key stakeholder groups</td><td>2.1<br>2.3</td></tr><tr><td></td><td>Process and activities<p>Roles and responsibilities</p><p>Tools and procedures</p></td><td>Workflows; service request models; service request catalogue; roles and responsibilities; automation and information</td><td>3<br>4<br>5</td></tr><tr><td>3</td><td>Dependencies and integration</td><td>Use of an integrated information system<br>Suppliers and other parties involved in service request management</td><td>5<br>6</td></tr><tr><td>4</td><td>Measurement and reporting</td><td>Metrics</td><td>2.5</td></tr><tr><td>5</td><td>Continual improvement</td><td>Regular review of the practice and the progress of the development of the capability</td><td>2.4, 2.5, 7</td></tr></tbody></table>

# 8. Recommendations for practice success
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:
* focus on value
* start where you are
* progress iteratively with feedback
* collaborate and promote visibility
* think and work holistically
* keep it simple and practical
* optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of *ITIL Foundation: ITIL 4 Edition*.

Table 8.1 outlines recommendations for the success of the service request management practice, linked to the relevant guiding principles.

##### Table 8.1 Recommendations for the success of service request management
<table><tbody><tr><td><strong>R</strong><strong>ecommendations</strong></td><td><strong>Comments</strong></td><td><strong>ITIL guiding principles</strong></td></tr><tr><td>Focus on value for users</td><td>The practice should enable users to use IT services and enable business value; it should not be used solely to delegate the IT maintenance responsibilities of users.</td><td>Focus on value</td></tr><tr><td>Ensure clear and user-friendly interfaces and procedures</td><td>Service request management is an important touchpoint in the service relationship. It impacts the overall user experience as well as the image of the service provider.</td><td>Collaborate and promote visibility<br>Keep it simple and practical</td></tr><tr><td>Consider monitoring and event management for maintenance-focused events</td><td>Where possible, use monitoring to detect the need for regular maintenance, rather than delegate it to users. Allow users to focus on using the services, not on servicing the technology.</td><td>Focus on value<br>Optimize and automate</td></tr><tr><td>Focus on the service value stream</td><td>The fulfillment of service requests may involve other management practices such as: change enablement, deployment management, release management, information security management, and others. Manage the end-to-end service value stream, ensuring that the flow is seamless for both users and IT teams,</td><td>Think and work holistically<br>Focus on value</td></tr><tr><td>Start with the most popular service requests</td><td>If complete and current service and request catalogues do not yet exist, start with the most popular requests received by the service desk. Understand and optimize their fulfilment, then proceed to the second most popular, and so on</td><td>Start where you are<br>Progress iteratively with feedback</td></tr><tr><td>Include feedback capturing in all service request models</td><td>Continually capture and analyze user feedback and improve the service request models accordingly. Use service request management to demonstrate a commitment to continual improvement</td><td>Progress iteratively with feedback</td></tr></tbody></table>

# 9. Acknowledgements
PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following people.

#### Authors
Miroslav Hlohovsky, Don Page, Robert Pinnington

#### Reviewers
Dinara Adyrbayeva, Cheryl Grimes, Roman Jouravlev, Georges Kemmerling, Henny Kerkvliet, Niels Loader, Anton Lykov, Paulo Tourinho

#### 2023 Revision
David Cannon, Antonina Douannes, Peter Farenden, Adam Griffith, Roman Jouravlev, Kaimar Karu, Barclay Rae, Stuart Rance, Nicola Reeves
