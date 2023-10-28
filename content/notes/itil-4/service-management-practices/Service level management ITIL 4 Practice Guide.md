---
title: "Service level management"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# 1. Source
Axelos International (https://www.axelos.com)

# 2. Overview
**Key Message**: The purpose of the service level management practice is to set clear business-based targets for service levels, and to ensure that delivery of services is properly assessed, monitored, and managed against these targets.</p></td></tr></tbody></table>

The service level management practice helps to set and manage a shared view of the quality of services between the service provider and the service consumer, aimed at all key stakeholders on both sides. This shared view is usually described in an agreement document, which may be written in various levels of formality. This applies to both the expected and actual service quality, from initial contact to the present, and covers service offerings and proposed value throughout the entirety of the service relationship. The service level management practice also includes monitoring and evaluation of the actual service quality and continual improvement of the services and agreements. Figure 2.1 illustrates the key activities of the practice.

![Image of Figure 2.1 Key activities of service level management practices](Service%20level%20management%20ITIL%204%20Practice%20Guide/Figure-2.1-Key-Activities-SL-MP.png "**Figure 2.1 Key activities of the service level management practice**")

## 2.2 Terms and concepts
<table><tbody><tr><td><p><strong>Definition: Service quality</strong></p></td></tr><tr><td><p>The totality of a service’s characteristics that are relevant to its ability to satisfy stated and implied needs.</p></td></tr></tbody></table>

In order to manage the quality of services, organizations usually define metrics. These metrics provide a formal definition of the service level of a particular service.

<table><tbody><tr><td><p><strong>Definition: Service level</strong></p></td></tr><tr><td><p>One or more metrics that define expected or achieved service quality.</p></td></tr></tbody></table>

To define and manage the service level, it is common to agree on relevant metrics and target values, as well as the approach to the measurement, evaluation, reporting, and improvement of the achieved service level. This is usually completed with the use of service level agreements (SLAs).

<table><tbody><tr><td><p><strong>Definition: Service level agreement</strong></p></td></tr><tr><td><p>A documented agreement between a service provider and a customer that identifies both services required and the expected level of service.</p></td></tr></tbody></table>

Note: An SLA can have a variety of forms and levels of formality, and the involvement of customers in its definition can also differ from case to case. In a wider sense, an SLA can be defined as:

A description of the target service level and the approach to its monitoring, measurement, and reporting, used by a service provider to monitor and manage the quality of its services.

It can also be called a public (or external) specification of a service level, as it is usually communicated to customers and users. This does not mean that customers are always involved in the definition of the service level. In the case of mass delivery and consumption, where services are delivered to thousands or millions of consumers in a pre- defined, out-of-the-box manner, customers usually have to either accept the service levels defined by the service provider, or not use the service at all.

In some instances, not all of the characteristics of service quality can be agreed upon, measured, and controlled in a formalized way. This means that the scope of the service level which is controlled is always smaller than the scope of the service quality it aims to formalize. Any aspects of the service quality that cannot be included in the service level can instead be supported through the collection of feedback. This adds a subjective perspective to validate the measured characteristics of the services. A combination of service level measurements and sufficient feedback from relevant stakeholders will provide a more holistic view of service quality and helps to define and co-create value for the service consumer. It also helps to prevent the so-called watermelon effect for service reporting, where all metrics look ‘green’ from the outside, while on the inside the consumer’s perception of the service is ‘red’.

To make sure that the service level management practice is focused on value, it is important to combine the definition and control of the measurable service level with the collection and analysis of relevant feedback. This becomes especially important when customers have not been involved in the definition of the service level, as described in the note above.

### 2.2.1 Utility and warranty
<table><tbody><tr><td><p><strong>Definition: Utility</strong></p></td></tr><tr><td><p>The functionality offered by a product or service to meet a particular need. Utility can be summarized as ‘what the service does’ and can be used to determine whether a service is ‘fit for purpose’. To have utility, a service must either support the performance of the consumer or remove constraints from the consumer. Many services do both.</p></td></tr></tbody></table>

<table><tbody><tr><td><p><strong>Definition: Warranty</strong></p></td></tr><tr><td><ul><li>Assurance that a product or service will meet agreed requirements. Warranty can be summarized as ‘how the service performs’ and can be used to determine whether a service is ‘fit for use’. Warranty often relates to service levels aligned with the needs of service consumers.</li><li>This may be based on a formal agreement, or it may be a marketing message or brand image. Warranty typically addresses such areas as the availability of the service, its capacity, levels of security, and continuity. A service may be said to provide acceptable assurance, or ‘warranty’, if all defined and agreed conditions are met.</li></ul></td></tr></tbody></table>

It is possible to assume from the definition that the service quality (and service level) only refers to the warranty and warranty requirement. This is not the case. The management of service quality and service level should be holistic and focused on value. To this end, all relevant characteristics of a service should be managed, including associated metrics, areas of perception, and feedback. The habit of separating the management of functional and non-functional characteristics of services (from the definition of requirements to the evaluation of the quality that has been achieved) comes from the separation of the development and operations teams. The separation of these characteristics and teams typically leads to a fragmented and very formal understanding of service quality.

To summarize, service quality includes both the functional and non-functional characteristics of services and therefore so should the service level.

### 2.2.2. Financial viability of services
It is quite common to limit the formal liability of the service provider to the agreed service level, rather than the implied or expected service quality. However, a sustainable service relationship is only possible if the agreed service level is constantly achieved and, most importantly, customers and users are satisfied. This satisfaction is based on their service experience and includes both agreed and implied service quality. Because of this, service providers often aim to exceed the agreed service level to make sure that their users and customers are satisfied. However, service provision is often budgeted based on the agreed service level, and extra efforts result in extra costs for the provider.

To maintain an effective service relationship, services should be financially viable for both service providers and service consumers. This is usually a key concern of sponsors:
* Sponsors of service consumption (as defined in ITIL Foundation: ITIL 4 Edition) require an optimal price of the service for the service consumer.
* Sponsors of service provision (a role authorizing budget for service provision) require an optimal cost of service provision.

These roles can be performed by different people in different scenarios:

When internal service providers are subsidized by the wider organization, the sponsor of both the provision and the consumption can be the owner of the IT budget. When a commercial service is provided to external consumers, the service provision budget is typically owned by sponsors on the service provider’s side, and the sponsor of the service consumption is the person authorizing it on the consumer’s side. It should be noted that, although these are the most common roles of sponsors, other combinations of roles are also possible.

Regardless of the service relationship model, the service level management practice contributes to the financial viability of services by managing customers’ and users’ expectations and agreeing on service levels that satisfy the requirements of sponsors. It also supports service design and budgeting, with information on the expected gap between the agreed service level and the expected service quality, and on any need for a dedicated budget to address this gap.

## 2.3 Scope
The scope of the service level management practice includes:
* Tactical and operational communications with customers regarding expected, agreed, and actual service quality, as well as their service experience. This includes the collection of feedback
* Negotiating, entering, and maintaining SLAs with customers.
* Understanding the design and architecture of services and dependencies between services and other configuration items.
* Continual review of achieved service levels versus agreed and expected service levels.
* Initiating service improvements, including improvements to agreements, monitoring, and reporting.

There are a number of activities and areas of responsibility that are not included in the service level management practice, although they are still closely related to it. These are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

### Table 2.1 Activities related to the service level management practice described in other practice guides
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Strategic communications with customers and sponsors</p></td><td><p>Relationship management</p></td></tr><tr><td><p>Operational communications with users</p></td><td><p>Service desk</p></td></tr><tr><td><p>Establishing and managing of contracts with suppliers and partners</p></td><td><p>Supplier management</p></td></tr><tr><td><p>Identification and documentation of services</p></td><td><p>Service catalogue management</p></td></tr><tr><td><p>Design of products and services</p></td><td><p>Service design</p></td></tr><tr><td><p>Analysis of innovation opportunities and new requirements for services outside of existing utility and warranty options</p></td><td><p>Business analysis</p></td></tr><tr><td><p>Design and control of financial models for commercial service delivery</p></td><td><p>Service financial management</p></td></tr><tr><td><p>Ongoing management and implementation of improvements</p></td><td><p>Continual improvement</p></td></tr><tr><td><p>Implementation of changes to products and services</p></td><td><p>Change enablement, project management, and other practices</p></td></tr><tr><td><p>Monitoring technology, team and supplier performance</p></td><td><p>Monitoring and event management</p></td></tr></tbody></table>

## 2.4 Practice success factors
A practice success factor (PSF) is more than a task or activity; it includes components from all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

<table><tbody><tr><td><p><strong>Definition: Practice Success Factor</strong></p></td></tr><tr><td><p>A complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

The service level management practice includes the following PSFs:
* Establishing a shared view of target service levels with customers.
* Overseeing how the organization meets the defined service levels through the collection, analysis, storage, and reporting of the relevant metrics for the identified services.
* Performing service reviews to ensure that the current set of services continues to meet the needs of the organization and its customers.
* Capturing and reporting on improvement opportunities, including performance against defined service levels and stakeholder satisfaction.

### 2.4.1 Establishing a shared view of target service levels with customers
Interactions with customers vary significantly across different service relationship models; for example, between internal and external service provisions; between large organizations and between individuals; and between tailored and out-of-the-box services. The latter has the strongest effect on the approach to establishing a shared view of target service levels with customers.

<table><tbody><tr><td><p><strong>Service: tailored or ‘out of the box'?</strong></p></td></tr><tr><td><p>‘Tailored service’ here means that there is a significant flexibility in target service levels that should be agreed before service delivery and consumption start. On the other hand, an ‘out-of-the-box’ service has one or more pre-defined service levels to choose from, without much flexibility.</p></td></tr></tbody></table>

When a service provider and a customer establish a shared view of a tailored service, they usually discuss customer needs and expectations, aiming to create a service specification that would satisfy all stakeholders, including:
* The customers, users, and sponsors of service consumption on the consumer side.
* The service delivery teams and the service provision sponsors on the provider side.

If the service being discussed has not been created yet, it should involve service architects and service designers, as well as business analysts and service development teams. However, these teams may not be needed if the services have already been designed and are currently available to customers.

Usually, the scope of the service quality being discussed is narrowed with every step in the process, from the outlining of consumer needs, to the agreement of the SLA. For example:
* When customers express their expectations to the service provider, they only partially represent the needs of the organization.
* When customers and service provider representatives agree on the service requirements (based on the communicated expectations), the scope of what is being discussed is narrowed again.
* Finally, after the service provider creates a description of a service level that can be delivered with the required level of assurance and liability, the scope becomes even narrower (Figure 2.2).

For out-of-the-box services, available service levels are usually pre-defined by the service provider based on a mixture of market and business intelligence. For example:
* Consumer needs are explored and analyzed by the marketing and business analysis teams of the service provider. These are likely to be different from the needs of any single given consumer.
* The service provider’s architects and designers create a service and supporting service quality specification, based on assumptions made about the consumer’s needs. This does not usually meet all of the captured needs of the consumer.
* Some of the characteristics of the specification are then announced to potential consumers as service offerings (sometimes with different service levels, such as gold, silver, bronze, and so on.)

* Finally, some components of the announced offering are affirmed in a formally agreed SLA (Figure 2.3).

All metrics that are defined as an agreed service level should have a clear approach to measurement and reporting. For tailored services, defining this approach can be a part of the initial target service level negotiation. For out-of-the-box services, available metrics and means of measurement are usually pre-defined during service design, with measurement and reporting tools integrated into the service.

The term ‘service level’ can be defined in multiple ways with various levels of formality. However, it is possible to identify key aspects of service quality that are typically discussed and agreed upon. Table 2.2 lists these aspects and provides examples of metrics that may be included in the agreed (or implied) service level.

![Image of Figure 2.2 showing tailored services from customer needs to SLAs](Service%20level%20management%20ITIL%204%20Practice%20Guide/Figure-2.2-Tailored-Services.png "**Figure 2.2 Tailored services: from customer needs to SLA**")

![Image Figure 2.3 showing the Out of box services from customer needs to SLAs](Service%20level%20management%20ITIL%204%20Practice%20Guide/Figure-2.3-Out-of-box-svc.png "**Figure 2.3 Out-of-the-box services: from consumer needs to SLA**") 

### Table 2.2 Key aspects of service quality and examples of service level metrics
<table><tbody><tr><td><p><strong>Service quality aspect</strong></p></td><td><p><strong>Examples of service level metrics</strong></p></td></tr><tr><td><p>Functionality</p></td><td><p>Completeness of the functions available<br>Correctness of the functions operations<br>Integrated functionality index</p></td></tr><tr><td><p>Availability</p></td><td><p>Maximum duration of service outage<br>Total time of unavailability<br>Percentage of availability<br>Mean time between system incidents (MTBSI)</p></td></tr><tr><td><p>Performance</p></td><td><p>Mean time of service action execution</p><p>Response time</p><p>Number and percentage of incidents related to execution and response time<br>Service throughput</p></td></tr><tr><td><p>Timeliness</p></td><td><p>Number and percentage of incidents related to service actions completed after the agreed deadline</p></td></tr><tr><td><p>User support</p></td><td><p>Timeliness of support request processing</p><p>Quality of support request processing</p></td></tr><tr><td><p>Accuracy</p></td><td><p>Number and impact of errors in the data and information</p></td></tr><tr><td><p>User experience (UX)</p></td><td><p>Number and frequency of user errors</p><p>Number and frequency of returns to a previous step (for example, back-button usage)<br></p><p>Number and frequency of interface help requests</p><p>Number and percentage of interrupted service actions (quitting the interface without completing a service action)</p></td></tr></tbody></table>

In some cases, organizations include metrics of the outcomes of service consumption in the scope of the measured service level. It can be done by an outcome-based description of service functionality or by introducing a new aspect of measurement. This approach requires a strong cooperative relationship between the service provider and service consumer.

Despite the best efforts to capture and meet expectations, the agreed service level usually differs from the expectations that the service should meet, sometimes quite significantly. It is typically not possible to achieve an ideal situation where everything is agreed in advance to the complete and mutual satisfaction of all stakeholders.

Nevertheless, it is very important for the success of the service relationship that the service provider and consumer have a shared view of the service quality. This can be ensured by applying the ITIL guiding principles, as shown in Table 2.3. Please note that the guiding principles should be applied to the whole service level management practice, so Table 2.3 should only be used as an example.

### Table 2.3 Application of the ITIL guiding principles in establishing a shared view of target service levels
<table><tbody><tr><td><p><strong>ITIL principle</strong></p></td><td><p><strong>Application</strong></p></td></tr><tr><td><p>Focus on value</p></td><td><p>Focus on outcomes for the service consumer organization and on user experience more than on technical details and associated metrics.</p></td></tr><tr><td><p>Start where you are</p></td><td><p>Base your agreements on previous experience as well as the current relationship between the service provider and consumer. If there is a sufficient level of trust based on the history of the relationship, agreements can be focused on outcomes and implied promises, rather than on formal obligations. Consider using industry benchmarks if no previous experience is available.</p></td></tr><tr><td><p>Progress iteratively with feedback</p></td><td><p>Acknowledge that not all relevant characteristics of service quality will be understood and/or achieved from the beginning, and that expectations and requirements will continually change. Be ready for continual review of the agreed service level based on achievements and feedback.</p></td></tr><tr><td><p>Collaborate and promote visibility</p></td><td><p>Involve relevant stakeholders (such as key users) in the discussion. Discuss the agreed service level with those it will affect and inform them of any constraints to establish realistic expectations. Also, provide sufficient operational transparency to promote a sense of ownership and manage expectations.</p></td></tr><tr><td><p>Think and work holistically</p></td><td><p>Do not focus on only a few service quality characteristics, but make sure to cover utility and warranty. Consider outcomes required as well as the components of service offerings (goods/access resources/service actions).</p></td></tr><tr><td><p>Keep it simple and practical</p></td><td><p>Do not try to put everything in the agreement but focus on what matters and what can be realistically measured and managed.</p></td></tr><tr><td><p>Optimize and automate</p></td><td><p>Periodically review the agreements. Optimize their structure and content to reflect the needs of stakeholders and remove excess content. Consider the provision of dashboards and other forms of automated SLA reporting.</p></td></tr></tbody></table>

### 2.4.2 Overseeing how the organization meets the defined service levels
When a shared understanding of the target service level is established, and actual service delivery has started, the service provider should control the actual quality of the services from three main perspectives:
* **Achieved service level** Against the agreed service level, based on agreed measurements.
* **User satisfaction with the service** Based on impromptu feedback, transaction-based feedback and periodic surveys.
* **Customer satisfaction with the service** Based on periodic discussions, surveys, or real-time scanning of the customer sentiment on social media.

Data from these sources should be collected, stored, analyzed, and the resulting information reported to relevant stakeholders on both the provider’s and consumer’s sides. These may include (but are not limited to):
* Consumer stakeholders:  
    sponsors  
    customers  
    users

* Provider stakeholders:  
    roles/teams responsible for the customer relationship  
    product and service owners  
    leads of the teams involved in the delivery of the service  
    representatives of suppliers/partners involved in service delivery.

The most common means of providing service achievement information is through regular interval-based reporting, combined with event-based reports for service outages and other significant events. However, in some cases it is better to provide an interface for ongoing monitoring of a service level and, where applicable, user satisfaction. This helps to increase visibility of the service quality and transparency of the service relationship.

Service level dashboards can be used to present the current status of service(s) to service provider teams, users, or customers. Note that the format and scope of the information presented may differ depending on the intended audience.

The service level management practice does not include the design and execution of the collection of service level data. This is done using the service design, monitoring and event management, and measurement and reporting practices. The service level management practice is focused on making sense out of the data collected. It then focuses on communicating and reviewing the data with stakeholders, starting with the customers.

### 2.4.3 Performing service reviews
The aim of service reviews is to establish a shared view of the achieved service quality and value enabled by the service, and to initiate necessary service improvements, where appropriate. In commercial service relationships, service reviews can also be a prerequisite for invoicing the consumer or a trigger to adjust bills.

Service reviews can be interval-based or event-based. Interval-based reviews take place regularly at agreed time periods. The intervals depend on factors such as previous satisfaction with the service; the number of changes introduced to the service since the last review; and likelihood of changes to service expectations/requirements. However, interval-based service reviews do not usually occur more than once a month, and do not work effectively if performed at intervals of longer than three months.

Event-based service reviews may be triggered by events such as a major incident, a request for a significant change in the service, or a change in the business needs/requirements of the service.

Service reviews do not need to be conducted as formal meetings; however, this is a common method when dealing with tailored services, especially those provided to internal consumers. For out-of-the-box services, a service review can take many different forms, especially those which are provided to external consumers.

For example, a service provider can perform a monthly review of the services provided to all or some of its consumers. This review can be grouped by specific criteria or individually selected. The service provider would use data from its achieved service level in combination with user feedback over the same period, alongside other data, such as revenue from, and costs of, the service provision, to assess the service. At the same time, service consumers would perform their own service reviews to assess the outcomes, costs, and risks of service consumption over the same or a different period of time. Service providers and service consumers may share the inputs and outputs of their service reviews. Generally, it is better if both parties coordinate their reviews to promote a sustainable and happy service relationship.

Regardless of the form the review takes and whether it occurs jointly or separately, service reviews are a very important part of the service provision and consumption. Moreover, there is a direct correlation between the quality of the review and the resulting quality of the services and stakeholder satisfaction. Aside from the other benefits they provide, service reviews are also the main source of service improvement opportunities.

### 2.4.4 Capturing and reporting on improvement opportunities
The service level management practice includes the identification of improvement opportunities and the initiation of service improvements. These improvements may aim to correct actual service quality (so that it meets the agreed service level) or to improve user and customer satisfaction with the service. Improvements can also be initiated in areas such as the practice’s processes, tools, or other resources, with the aim to improve the practice and associated customer experience.

When improvements are triggered by customer or user feedback as well as by joint service reviews, it is important to ensure the transparency of improvement plans, progress, and results for customers and users. This is in accordance with the ITIL guiding principle of collaborating and promoting visibility.

All practice-related improvements should follow the model used by the organization performing the improvement (see section 4.6 of ITIL Foundation: ITIL 4 Edition for an overview of the continual improvement model, and the continual improvement practice guide for more detailed guidance). Most service improvement initiatives are owned by a person who is accountable for the product or service (for example, the product owner or the service owner).

It is important to make sure that service improvements are not only initiated but also effectively implemented. An approach to implementing improvements is described in the continual improvement practice guide. Nonetheless, it is vital to use multiple practices in the context of value streams, to maintain the momentum of the continual improvement of services.

## 2.5 Key metrics
The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the service level management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.4.

### Table 2.4 Examples of key metrics for the practice success factors
<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Establishing a shared view of target service levels with customers</p></td><td><ul><li>Customer satisfaction with SLA content</li><li>Percentage of SLAs that are overdue for review<br>Percentage of service-related operations</li></ul><ul><li>(incidents, changes, etc.) without an agreed target level</li></ul></td></tr><tr><td><p>Overseeing how the organization meets the defined service levels</p></td><td><ul><li>Percentage of SLAs with a service level measurement approach defined</li><li>Percentage of services with regular SLA reports produced</li><li>Percentage of services/SLAs with dashboards for service level monitoring</li><li><p>Percentage of services with satisfaction data that has been systematically collected</p></li></ul></td></tr><tr><td><p>Performing service reviews</p></td><td><ul><li>Customer satisfaction with service reporting</li><li>Percentage of services/customers/SLAs with regular service review scheduled</li><li>Customer satisfaction with service reviews</li></ul></td></tr><tr><td><p>Capturing and reporting on improvement opportunities</p></td><td><ul><li>Average service quality index over last three months/average service quality index over last 12 months</li><li>Service improvement productivity index<sub><em>a</em></sub></li></ul></td></tr></tbody></table>

*a*(N+C)/(O+C) – see the measurement and reporting practice guide for explanation and examples.

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the service level management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

# 3. Value streams and processes
## 3.1 Value streams contribution
Like any other ITIL management practice, the service level management practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The service level management practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which the practice contributes are:
* plan
* engage
* improve.

The contribution of the service level management practice to the service value chain is shown in Figure 3.1.

## 3.2 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

![Image of Figure 3.1 showing Heat Map of contribution of service level management practice to value chain activities](Service%20level%20management%20ITIL%204%20Practice%20Guide/Figure-3.1-Heat-Map-SLM.jpg "**Figure 3.1 Heat map of the contribution of the service level management practice to value chain activities**")

<table><tbody><tr><td><p><strong></strong><span><strong>Definition: Process</strong></span></p></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs.<br>A process takes one or more defined inputs and turns them into defined outputs.<br>Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

Service level management activities form two processes:
* **Management of SLAs** This process is focused on agreements and their lifecycle.
* **Oversight of service levels and service quality** This process ensures continual service improvement based on a good understanding of service quality.

### 3.2.1 Management of SLAs
This process includes the activities listed in Table 3.1, and transforms the inputs into outputs.

### Table 3.1 Inputs, activities, and outputs of the management of SLAs
<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Customer requirements</li><li>Service catalogue</li><li>Service specifications</li></ul><ul><li>Service models and configuration models</li><li>Agreements with suppliers and partners</li><li>User and customer feedback Improvement plans and registers Financial information</li></ul></td><td><ul><li>Definition of customer requirements</li><li>Viability analysis Drafting an SLA SLA negotiation</li><li>SLA communication and enablement</li><li>SLA review</li><li>SLA prolongation SLA withdrawal</li></ul></td><td><ul><li>Service level requirements (documented)</li><li>Draft SLAs</li><li>Signed SLAs</li><li>Onboarding communications</li><li>Change requests</li><li>Withdrawn SLAs</li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![Image of Figure 3.2 showing workflow for management SLAs](Service%20level%20management%20ITIL%204%20Practice%20Guide/Figure-3.2-Workflow-management-SLAs.png "**Figure 3.2 Workflow for management of SLAs**")

This process may vary, depending on the type of service or service relationship model to which it is applied. Table 3.2 provides an overview of these variations.

### Table 3.2 Activities of the SLA management process
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Out-of-the-box pre-defined services</strong></p></td><td><p><strong>Tailored services</strong></p></td></tr><tr><td><p>Definition of customer requirements</p></td><td><p>These are based on the existing service catalogue with clearly defined options for service levels. The customers select the most appropriate options/combinations for the services that they need. Service provider representatives from a customer-facing team help to navigate the catalogue to find the most relevant services and service levels.</p></td><td><ul><li>Customers communicate their requirements for services based on their business needs. They may refer to the existing catalogue, but usually the requirements are not limited to pre-defined options.</li><li>Service provider representatives from a customer-facing or business analysis team, or product and service owners, are involved in documenting the requirements.</li></ul></td></tr><tr><td><p>Viability analysis</p></td><td><p>A quick check of resource availability is performed to confirm that the defined requirements can be fulfilled. This activity follows pre-defined patterns and may be fully automated. This leads to confirmation of service requirements or an adjustment, if necessary.</p></td><td><ul><li>A manual or semi-automated analysis of resource requirements may be needed to define whether it is possible to fulfil these requirements, and how much it would cost. A quote with estimated costs/price and a timeline for fulfilment is the main output.</li><li>This analysis should include agreements with the service provider’s suppliers and partners to make sure that they would support the required service level.</li></ul></td></tr><tr><td><p>Drafting an SLA</p></td><td><p>A standardized SLA is drafted for the customer to review and confirm. It may be fully or largely automated.</p></td><td><p>The service designer, service owner, and relationship manager take part in drafting an agreement based on the viability analysis. It is recommended that existing services and specifications be used as building blocks, but this work is still likely to require expert knowledge and collaboration between people.</p></td></tr><tr><td><p>SLA negotiation</p></td><td><p>The customer reviews the draft SLA and accepts its terms and conditions or returns it for analysis. If it is returned or the customer needs assistance, a service provider representative from a customer-facing team may guide the customer through the draft SLA and answer questions. In other cases, this activity may be fully automated. The acceptance of the SLA is formally confirmed by the customer.</p></td><td><p>The customer and service provider representatives (which may include the service owner, relationship manager, service designer, and others) discuss the draft SLA and negotiate changes where needed, or accept it for sign-off. If not accepted, the draft is returned for viability analysis. It may take several iterations to agree on an acceptable version. When the draft is agreed, it is formally confirmed by the parties.</p></td></tr><tr><td><p>SLA communication and enablement</p></td><td><ul><li>When the SLA is confirmed by the parties, the service provider initiates the required changes and communications to make the agreed services available for the user. The changes and onboarding communications may be fully or largely automated.</li><li>These changes and communications are triggered by the service level management practice but need other practices to be fulfilled.</li></ul></td><td><ul><li>When the SLA is confirmed by the parties, the service provider initiates the required changes and communications to make the agreed services available for the user. This may require significant manual and automated changes to all types of the provider’s resources and may also require changes to the consumer resources. In some cases, this will lead to an implementation project or programme.</li><li>These changes and communications are triggered by the service level management practice but need other practices to be fulfilled.</li></ul></td></tr><tr><td><p>SLA review</p></td><td><p>A formal review of the SLA may be interval-based or triggered by an event (such as a customer request, policy change, service review, or organizational change). Where reviews are interval-based, and both the customer and provider are happy with the SLA’s content and terms and conditions, the SLA is usually confirmed for prolongation. If the customer requirements have changed, the process may start again with the definition of requirements. Finally, if the service is no longer needed, SLA withdrawal is initiated.</p></td><td><ul><li>A formal review of the SLA may be interval-based or triggered by an event (such as a customer request, policy change, service review, or organizational change).</li></ul><ul><li>First reviews after initial SLA negotiation may lead to improvements to the SLA wording, with no changes required to the service. Regardless of whether the wording is changed, the amended SLA goes for prolongation. If the customer requirements have changed, the process may start again with the definition of requirements. Finally, if the service is no longer needed, SLA withdrawal is initiated.</li><li>SLA reviews are performed by the customer (sponsor and key users may be involved), together with service provider representatives (typically the service owner and/or relationship manager).</li></ul></td></tr><tr><td><p>SLA prolongation</p></td><td><p>If the SLA is confirmed for prolongation, it may require communications and changes (for example, prolongation of supporting contracts with suppliers). This may be fully or partially automated.</p></td><td><p>These changes and communications are triggered by the service level management practice but need other practices to be fulfilled.</p></td></tr><tr><td><p>SLA withdrawal</p></td><td><ul><li>When the SLA is confirmed for withdrawal, the service provider initiates the required changes and communications to make the agreed services unavailable for the user. The changes and offboarding communications may be fully or partially automated.</li><li>These changes and communications are triggered by the service level management practice but need other practices to be fulfilled.</li></ul></td><td><ul><li>When the SLA is confirmed for withdrawal, the service provider initiates the required changes and communications to make the agreed services unavailable for the user.</li><li>This may require significant manual and automated changes to all types of the provider’s resources and may also require changes to the consumer’s resources. In some cases, this will lead to an offboarding project or programme. These changes and communications are triggered by the service level management practice but need <u>other practices to be fulfilled.</u></li></ul></td></tr></tbody></table>

### 3.2.2 Oversight of service levels and service quality
This process is focused on the monitoring and review of the service levels and service quality, rather than the SLA documents. SLAs are used extensively in this process, depending on the quality and completeness of the agreed service level information. In some cases, however, agreements are high level and vague, and service quality is monitored and assessed based on data that is less structured and less objective.

Whichever way the process is carried out, the service provider needs to monitor and analyze both the measured service level data and feedback from users and customers to better understand service quality.

This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

### Table 3.3 Inputs, activities, and outputs of the oversight of service levels and service quality
| **Key inputs** | **Activities** | **Key outputs** |
| --- | --- | --- |
* Service performance data SLA
* User and customer feedback, including compliments and complaints
* Service improvement plan
* Customer and user satisfaction surveys
* Ongoing service quality monitoring
* Service review
* Service quality reporting
* Service quality dashboards and reports for various stakeholder
* Service improvement initiatives

Figure 3.3 shows a workflow diagram of the process.

![Image of Figure 3.3 Workflow of service level and service quality oversight](Service%20level%20management%20ITIL%204%20Practice%20Guide/Figure-3.3-Workflow-SL-SQ-oversight.png "**Figure 3.3 Workflow of service level and service quality oversight**")

The oversight process may vary, depending on the level of formalization of the target service level for the services to which it is applied. Table 3.4 provides an overview of these variations.

### Table 3.4 Activities of the service level and quality oversight process
| **Activity** | **High level of formalization (detailed SLA)** **Low level of formalization (implied service level and high-level agreement)**

 |
| --- | --- | --- |

Customer and user satisfaction survey
The service provider runs regular satisfaction surveys collecting feedback from users and customers. The format and regularity of the surveys may be formally agreed by the parties. The service owners and relationship managers of the service provider evaluate the feedback and include it in the scope of service review.
Service provider continually collects information from the users and customers to ensure that they are satisfied with the services and to identify improvement opportunities. The surveys include aspects of the service quality that have not been formally agreed or documented. This helps to maintain awareness of the expectations and how the services are perceived; such information should be continually and carefully reviewed.

The service owners and relationship managers of the service provider evaluate the feedback and include it in the scope of the service review.
Ongoing service quality monitoring
* The service provider monitors the performance of resources used to deliver services (this work involves many practices) and collects data relevant for the services as defined in the SLA. Simultaneously, impromptu feedback is collected from users and other relevant stakeholders. The service owners and relationship managers of the service provider monitor the services to ensure that they are delivered as agreed.
* Some of the service quality data may be available for users and customers on a dashboard in an agreed format, so that they can also monitor service quality.
Regular and impromptu feedback is collected from users and other relevant stakeholders. This is combined with resource performance data and compared with technical specifications and benchmarks, as defined by the service provider.

Service owners, product owners, and relationship managers of the service provider monitor the service to ensure that all systems work as intended.

  
 |
| Service review 
The service owner conducts a review of service quality over a designated period of time, or in relation to an event. The service owner involves relevant stakeholders from the service provider (product owners, leads of technical teams, relationship managers, supplier managers, etc.) and, where possible, customers. The key outputs are internal service quality reports and improvement initiatives.
* Customers conduct a review of service quality, involving key users and, where possible, service provider representatives.
* The main outputs are a service value report for sponsors and other consumer stakeholders, and improvement initiatives to be discussed with the service provider. These initiatives serve as inputs for the service reviews of the provider.
* The service reviews of the customers and provider may be conducted jointly and may lead to joint improvement initiatives. This is usual for tailored services of either level of formalization, but relatively rare for out-of-the-box mass market services.
Service quality reporting
The service provider produces reports and dashboards demonstrating service level achievements and satisfaction levels for customers and other agreed recipients. These are communicated by a previously agreed means.
* The service provider produces reports (and sometimes dashboards) demonstrating satisfaction levels and selected service level achievements (commonly accepted in the industry and relevant for user satisfaction).
* These are communicated by a previously agreed means.

Service level management activities are performed by the service provider and service consumer, as described in Tables 3.2 and 3.4. They may involve suppliers and partners. These activities are also supported (and sometimes fully or partially automated) by a number of tools and technologies. All are described in the following sections.

# 4. Organizations and people
The ITIL practices do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

### Table 4.1 Competency codes and profiles 
| **Competency code** | **Competency profile (activities and skills)**L **Leader** Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes

 |
| A 
**Administrator**. This role focuses on administrative skills. Activities associated with this role include the assignment and prioritization of tasks, record keeping, ongoing reporting, and basic improvement initiatives. 

 |
| C 
**Coordinator/communicator** This role focuses on communication and coordination skills. Activities associated with this role include the coordination of multiple parties, communication between stakeholders, and the running of awareness campaigns.

 |
| M 
**Methods and techniques expert**  This role focuses on consulting skills and expertise in work methods. Activities associated with this role include the design and implementation of work techniques, the documentation of procedures, consulting on processes, work analysis, and continual improvement.

 |
| T 
**Technical expert** This role focuses on technical (IT) expertise and expertise-based assignments.

The role accountable for all service level management activities is usually the service owner. The competency profile for this role in the context of the service level management practice is CLA, though the importance of each of these competencies varies from activity to activity. Examples of the roles which are responsible for service level management activities are listed in Table 4.2, together with the associated competency profiles.

### Table 4.2 Examples of roles with responsibility for service level management activities
| **Activity****Management of  SLAs process** | **Responsible roles** | **Competency profile** | **Specific skills** |
| --- | --- | --- | --- |
* Definition of customer requirements
* Relationship manager
* Service architect
* Service designer
* Service owner

 | Customer | CTA 
* Good knowledge of the service consumer’s business
* Good knowledge of the service provider’s portfolio
* Communication and coordination
* Viability analysis
* Service architect
* Service designer
* Service owner
* Supplier manager
* Technical expert
Product owner

 | TC 
* Business analysis
* Risk analysis
* Good knowledge of the service provider’s portfolio
Drafting an SLA
* Relationship manager
* Service designer
* Service owner

 | CAT 
* Good knowledge of the service provider’s portfolio
* Good knowledge of the products, including their architecture and configuration
* Business analysis
SLA negotiation
* Customer
* Relationship manager
* Service owner

 | CA 
* Communication and negotiation
* Good knowledge of the product, including its architecture and configuration
SLA communication and enablement
* Product owner
* Project manager
* Service desk agent
    
* Service owner
* Supplier manager
CAT
* Management and coordination
* Communication skills

 |
| SLA review 
* Customer
* Relationship manager
* Service designer
* Service owner

 | CA 
* Analytical skills Understanding of the services
* Understanding of the consumer context
* Knowledge of the agreements and expectations
SLA prolongation
* Account manager
* Service owner
* Technical expert
    
CA
* Coordination and communication
* Knowledge of the agreements and expectations
SLA withdrawal
* Account manager
* Service owner
* Technical expert
    
CAT
* Good knowledge of the product, including its architecture and configuration
* Knowledge of the agreements
* Management and coordination
Customer and user satisfaction survey
* Account management
* Product Owner
* Relationship manager
* Service owner

 | CA 
* Knowledge of the agreements and expectations
* Understanding of the consumer context
* Communication

 |
| Ongoing service quality monitoring 
* Product owner
* Service owner
* Supplier manager
    
* Technical expert
    

 | TC 
* Analytical skills
* Knowledge of the agreements and expectations
* Understanding of the consumer context
* Good knowledge of the product, including its architecture and configuration
Service review
* Customer

* Product owner
* Relationship manager
* Service owner
* Supplier manager
* Technical expert

 | CT 
* Analytical skills
* Knowledge of the agreements and expectations
* Understanding of the consumer context
* Good knowledge of the product, including its architecture and configuration
* Management and coordination
    

 |
| Service quality reporting 
* Customer
* Relationship manager
* Service owner

 | CA 
* Knowledge of the agreements and expectations
* Understanding of the consumer context
* Communication and negotiation

### 4.1.1 Service owner role
The most important role in the service level management practice is the service owner.

The service owner is accountable for the end-to-end management of a specific IT service. The service owner’s accountability for a specific service is independent of where the underpinning technology components, services, or competencies reside. Service ownership is critical to service management. It is possible to combine this role with that of product owner. In some cases, it is combined with the role of account manager or relationship manager, especially if the service is created or tailored for a specific consumer or group of consumers. The service owner has the following responsibilities (the responsibilities associated with the service level management practice are given in italics):
* ensuring that the ongoing provision of services meets agreed customer requirements
* understanding and translating customer requirements into service designs and draft SLAs
* ensuring consistent and appropriate communication with customers for service-related enquiries and issues
* assisting in defining service models and assessing the impact of new services or changes to existing services
* identifying opportunities for service improvements, discussing these with the customer, and starting improvement initiatives
* liaising with the appropriate stakeholders throughout the service value streams
* soliciting required data and reports for analysis and to facilitate effective service monitoring and performance
* representing the service across the organization
* understanding the service (components etc.)
* serving as the point of escalation (notification) for major incidents relating to the service
* controlling changes to the service
* conducting service reviews
* ensuring that information about the service (in the service catalogue and other records) is accurate and up to date
* negotiating SLAs relating to the service
* identifying improvement opportunities and initiating and driving improvements to the service.

The service owner is responsible for the continual improvement and management of change affecting the service for which they are accountable. The service owner is a primary stakeholder in all the underlying ITIL practices which enable and support the service they own.

## 4.2 Organizational structures and teams
Although the roles of product owner, service owner, account manager, and relationship manager may be supported with formal positions and job descriptions, it is not common to see a dedicated organizational structure for the service level management practice. Some organizations create committees (service committees, service quality committees, etc.) focused on the strategic and tactical management of service provision. These committees may include service reviews in their agendas, usually at a high level, such as ‘services for private clients’ or ‘services in the North American region’. Similarly, when organizations provide services to external consumers, they are likely to have dedicated customer-facing teams (sales teams, account managers, etc.) focused on the relationship management practice and often heavily involved in service level management activities.

# 5. Information and technology
## 5.1 Information exchange: inputs and outputs
The effectiveness of the service level management practice is based on the quality of the information used. This includes, but is not limited to, information about:
* customers and users
* services (their architecture and design)
* partners and suppliers, including contract and SLA information on the services they provide
* policies and requirements which regulate service provision
* ongoing service delivery, including:
    * Information about the current operational status of services
    * information about incidents
    * information about planned and ongoing changes
    * information about user and customer satisfaction
    * information about the financial status of service delivery (costs, revenue, overdue bills, and so on.)  
* the status of service improvements.

This information may take various forms, depending on the service relationship (internal or external service provision, tailored or out-of-the-box services, etc.). The key inputs and outputs of the practice are listed in section 3.

# 5.2 Automation and tooling
In some cases, the work of the service level management practice can significantly benefit from automation (see section 3 for more details). Where this is the case, and automation is possible and effective, it may involve the solutions outlined in Table 5.1.

### Table 5.1 Automation solutions for service level management activities
<table><tbody><tr><td><p><strong>Process activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><p><strong>Key functionality</strong></p></td><td><p><strong>Impact on the effectiveness of the practice</strong></p></td></tr><tr><td><p>Management of SLAs process</p></td><td><p>Management of SLAs process</p></td><td><p>Management of SLAs process</p></td></tr><tr><td><p>Definition of customer requirements</p></td><td><p>Service catalogue and service portals</p></td><td><p>Selection of services and service level option to order</p></td><td><p>Very high where the volume of standardized services is high</p></td></tr><tr><td><p>Viability analysis</p></td><td><p>Configuration management database (CMDB), service models, availability and capacity monitoring and management tools, and asset management tools</p></td><td><p>Control of availability and capacity of resources needed to provide the requested services</p></td><td><p>Very high where the volume of standardized services is high</p></td></tr><tr><td><p>Drafting an SLA</p></td><td><p>Contracting tools and service portals</p></td><td><p>Drafting of a quote/SLA</p></td><td><p>High where the volume of standardized services is high, especially if ordered over the internet</p></td></tr><tr><td><p>SLA negotiation</p></td><td><p>Contracting tools, and service portals and apps</p></td><td><p>Selection of alternative options</p></td><td><p>Medium</p></td></tr><tr><td>SLA communication and enablement</td><td><p>Change initiation and control tools, email and other communication channels, billing and payment tools, asset management tools, including licence control, work management tools, user support tools, knowledge management tools, and document repositories</p></td><td><p>Change initiation, asset re-allocation, task assignment, billing and payment processing, training and communication, user support, providing a definitive source of agreed service levels</p></td><td><p>High where the volume of standardized services is high, especially if delivered digitally</p></td></tr><tr><td><p>SLA review<br>SLA prolongation<br>SLA withdrawal</p></td><td><p>Document control tools</p></td><td><p>Control of expiry dates, version control, and archiving of documents</p></td><td><p>Low to high, depending on the volume of documents to manage</p></td></tr><tr><td><p>Oversight of service levels and service quality process</p></td><td><p>Oversight of service levels and service quality process</p></td><td><p>Oversight of service levels and service quality process</p></td><td><p>Oversight of service levels and service quality process</p></td></tr><tr><td><p>Customer and user satisfaction survey</p></td><td><p>Survey tools, analytical tools, communication systems, and social media</p></td><td><p>Distribution and promotion of surveys, collection of feedback, processing of the data, publication of the findings</p></td><td><p>Very high, especially where the number of respondents is high</p></td></tr><tr><td><p>Ongoing service quality monitoring</p></td><td><p>Infrastructure and application monitoring and reporting tools, built-in user behaviour monitoring tools, dashboarding and reporting tools, advanced analytics tools, survey and satisfaction monitoring tools, user portals and apps, and social media</p></td><td><p>Collection of system and service health data, collection of user and customer feedback, processing and analysis, and dashboard and report design and presentation</p></td><td><p>High where the volume of standardized services is high, especially if delivered digitally</p></td></tr><tr><td><p>Service review</p></td><td><p>Reporting tools, contracting tools, and service portals and apps</p></td><td><p>Report presentation, SLA prolongation, and logging of improvement initiatives</p></td><td><p>Low to medium, depending on the volume of standardized services</p></td></tr><tr><td><p>Service quality reporting</p></td><td><p>Reporting and dashboarding tools, service portals and apps, email and other communication tools, and social media</p></td><td><p>Report presentation</p></td><td><p>Low to high, depending on the volume of standardized services and which stakeholders must be reported to</p></td></tr></tbody></table>

# 6. Partners and suppliers
Very few services are delivered using only an organization’s own resources. Many organizations depend on services provided by third parties (see section 2.4 of ITIL 4 Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the practice guides for service design, architecture management, and supplier management. Information about dependencies on third-party services is used in the service level management practice as part of service design information, primarily for the activity of viability analysis. It is also used in improvement planning, especially where service levels have not been met and significant improvements are required.

The service level management practice is one of the practices that enables ownership of the services provided by an organization, and therefore it is rare to see it outsourced.

However, some service level management activities may be delegated in certain cases.

Some activities can provide outsourcing opportunities. A third party may act as an agent of the service provider, offering services on its behalf. In this capacity, the third party may collect customer requirements, draft and negotiate SLAs, take part in SLA communication and enablement by initiating onboarding, and take part in SLA review, prolongation, and withdrawal. These can be applied to highly standardized services, especially those delivered in high volumes.

Another opportunity to delegate the service level management practice to a third party is in service integration and management (SIAM), where a supplier’s (integrator’s) service management practices largely replace those of the service provider. However, it is unusual to see this level of delegation.

At the same time, using external or outsourced resources as part of an organization’s service level management practice is a very common situation. These may include people, automation tools, and supporting services such as satisfaction surveys and other data collection services. Nonetheless, service ownership and oversight remain a responsibility of the organization.

# 7. Important reminder
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of things that organizations might think about, not a list of answers. When using the content of the ITIL Practice guides, organizations should always follow the ITIL guiding principles:
* focus on value
* start where you are
* progress iteratively with feedback
* collaborate and promote visibility
* think and work holistically
* keep it simple and practical
* optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of *ITIL Foundation: ITIL 4 Edition*.

# 8. Acknowledgements
Axelos Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, Axelos would like to thank the following people.

## 8.1 Authors
Dmitriy Isaychenko, Roman Jouravlev.

## 8.2 Reviewers
Akshay Anand, Pavel Demin, Sofi Fahlberg, Piia Karvonen, Antonina Klentsova, Mark O’Loughlin, Anton Lykov, Paula Määttänen, Christian F. Nissen, Tatiana Orlova, Elina Pirjanti, Stuart Rance.
