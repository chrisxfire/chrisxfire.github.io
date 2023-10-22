---
title: "Service continuity management"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# 1. About this document

It is split into five main sections, covering:
* general information about the practice
* the practice’s processes and activities and their roles in the service value chain
* the organizations and people involved in the practice
* the information and technology supporting the practice
* considerations for partners and suppliers for the practice

## **1.1 ITIL® 4 Qualification scheme**

Selected content of this document is examinable as a part of the following syllabus:
* **ITIL Specialist** High-Velocity IT

Please refer to the relevant syllabus document for details.

# 2. General information

## **2.1 Purpose and description**

**Key Message**: The purpose of the service continuity management practice is to ensure that the availability and performance of a service are maintained at sufficient levels in case of a disaster. The practice provides a framework for building organizational resilience with the capability of producing an effective response that safeguards the interests of key stakeholders and the organization’s reputation, brand, and value-creating activities.</p></td></tr></tbody></table>

<table><tbody><tr><td><p><strong>Definition: Disaster</strong></p></td></tr><tr><td><p>A sudden unplanned event that causes great damage or serious loss to an organization. To be classified as a disaster, the event must match certain business-impact criteria that are predefined by the organization.</p></td></tr></tbody></table>

The service continuity management practice helps to ensure a service provider’s readiness to respond to high-impact incidents which disrupt the organization’s core activities and/or credibility.

Ensuring service continuity is becoming more important and difficult. The service continuity management practice is increasingly important in the context of digital transformation, because the role of digital services is growing across industries. Major outages of services may have disastrous effects on organizations that, in the past, focused on non-technological disasters.

Wider use of cloud solutions and wider integration with partners’ and service consumers’ digital services are creating new critical dependencies that are more difficult to control. Partners and service consumers usually invest in high-availability and high-continuity solutions, but a lack of integration and consistency between organizations creates new vulnerabilities that need to be understood and addressed.

The service continuity management practice, in conjunction with other practices (including the availability management, capacity and performance management, information security management, risk management, service design, relationship management, architecture management, and supplier management practices, among others), ensures that the organization’s services are resilient and prepared for disastrous events.

The concept of risk is central to the service continuity management practice. This practice usually mitigates high-impact, low-probability risks which cannot be totally prevented (because some risk factors are not under the organization’s control, such as natural disasters).

In the simplest terms, this practice is much like the incident management practice, except that the potential for damage is much higher and it may threaten the service provider’s ability to create value.

The service continuity management practice is closely related to, and in some context may be merged with, the availability management practice within the service value system (SVS). It is also closely related to, and may be incorporated into, the business continuity management practice in a corporate context.

In a service economy, every organization’s business is service-driven and digitally enabled. This may lead to a full integration of the disciplines because the business continuity management practice is concerned with the continuity of digital services and service management. This integration is possible and useful where digital transformation has led to the removal of the borders between ‘IT management’ and ‘business management’ (see ITIL® 4: High-Velocity IT for more on this topic).

## **2.2 Terms and concepts**

<table><tbody><tr><td><p><strong>Definition: Service continuity</strong></p></td></tr><tr><td><p>The capability of the service provider to continue service operation at acceptable predefined levels following a disaster event or disruptive incident.</p></td></tr></tbody></table>

For internal service providers, the main objective of the service continuity management practice is to support the overall business continuity management practice by ensuring that, through managing the risks that could affect IT services, the service provider can always provide the relevant agreed service levels.

For external service providers, service continuity management equals business continuity management.

Business continuity professionals are also interested in dealing with such business crises as adverse media attention or disruptive market events. However, in this practice guide, the scope of the service continuity management practice is limited to operational risks.

### **2.2.1 Disaster (or disruptive incident or crisis)**

ISO defines a disaster as ‘a situation with a high level of uncertainty that disrupts the core activities and/or credibility of an organization and requires urgent action’<sup>1</sup>.

It is usually a good idea to explicitly define the list of events which are considered to be disasters. Doing so helps when developing a proper set of service continuity plans, which ensures organizational readiness for disruptive events.

A list of disasters generally includes:
* cyber attacks
* electricity outages
* failures of strategic partners
* fires
* floods
* key personnel unavailability
* large-scale IT infrastructure failures (such as data-centre failures)
* natural disasters.

Defining those events which are not disasters is equally important. Usually, the service continuity management practice does not cover:
* **Minor failures**. Failures should be considered minor or major based on business impact. It is important to consider factors such as the service actions that are affected, the scale of failure, time of failure, and so on<sup>2</sup>.
* Strategic, political, market, or industry events.

To successfully recover from a disaster, a service provider should define the service continuity requirements. Service continuity requirements include:
* recovery time objective (RTO)
* recovery point objective (RPO)
* minimum service continuity levels (see Figure 2.1).

![](Service%20continuity%20management%20ITIL%204%20Practice%20Guide/Figure_2.1_Service_continuity_requirements_RTO_RPO_minimum_target_service_level.png)

Figure 2.1 Service continuity requirements: RTO, RPO, minimum target service level

### **2.2.2 Recovery time objective**

<table><tbody><tr><td><p><strong>Definition: Recovery time objective</strong></p></td></tr><tr><td><p>The maximum period of time following a service disruption that can elapse before the lack of business functionality severely impacts the organization. This represents the maximum agreed time within which a product or an activity must be resumed, or resources must be recovered.</p></td></tr></tbody></table>

The main factors that should be considered in estimating the RTO are:
* the reduction in a service provider’s ability to deliver services and the costs associated with this reduction
* Service level agreement fines and regulatory judgments
* losses associated with diminished competitive advantage and reputation.

Business continuity professionals also use the term ‘maximum tolerable period of disruption/maximum acceptable outage (MAO)’ and distinguish them from the RTO.

ISO 22301:2012 provides the following definitions:
* MAO The time it would take for adverse impacts, which might arise as a result of not providing a product/service or performing an activity, to become unacceptable.
* RTO The period of time following an incident within which a product or an activity must be resumed, or resources must be recovered.

Following this logic, the RTO should be less than the MAO by an amount which accounts for the organizational risk appetite<sup>3</sup>. The MAO should be identified during business impact analysis. RTO should be defined during the development of service continuity plans.

### **2.2.3 Recovery point objective**

<table><tbody><tr><td><p><strong>Definition: Recovery point objective</strong></p></td></tr><tr><td><p>The point to which the information that is used by an activity must be restored in order to enable the activity to operate effectively upon resumption.</p></td></tr></tbody></table>

RPO defines the period of time of acceptable data loss. If the RPO is 30 minutes, there should be at least one backup 30 minutes prior to a disruptive event so that, when the service is recovered, the data from the time 30 minutes or less prior to the disruptive event will be available when service delivery is resumed.

The main factors that should be considered in estimating the RPO are:
* criticality of the service that used the data
* criticality of the data
* data-production rate.

For example, an online shop takes 100 orders per hour. Executives say that losing 200 orders would be unacceptable. Therefore, the RPO is 2 hours.

The RPO defines the requirement for backup frequency. Backup management must ensure the availability of recent backup copy in case of disaster.

### **2.2.4 Minimum target service level**

<table><tbody><tr><td><p><strong>Definition: Minimum target service level</strong></p></td></tr><tr><td><p>The level of service which is acceptable to the service provider to achieve its objectives during a disruption<sup>4</sup>.</p></td></tr></tbody></table>

While recovering from a disaster, a service provider should usually provide the service at some minimum target service level. Even though there are no specific requirements from the customer, achieving a minimum service level can help to minimize losses.

The minimum target service level is usually defined in terms of:
* list of specific service actions and functionality points that should available to the users during a disruption
* limited number of users or specific group of users who should have access to the service during a disruption
* limited number of transactions per time period that users should be able to process during a disruption.

### **2.2.5 Business impact analysis**

<table><tbody><tr><td><p><strong>Definition: Business impact analysis</strong></p></td></tr><tr><td><p>A key activity in the practice of service continuity management that identifies vital business functions (VBFs) and their dependencies. These dependencies may include suppliers, people, other business processes, and IT services. Business impact analysis defines the recovery requirements for IT services. These requirements include RTOs, RPOs, and minimum target service levels for each IT service.</p></td></tr></tbody></table>

Business impact analysis (BIA) is a process of analysing activities and the effect that a disruption might have on them<sup>5</sup>.

According ISO 22301, business impact analysis should include:
* identifying activities that support the provision of products and services
* assessing the impacts over time of not performing these activities
* setting prioritized timeframes for resuming these activities at a specified minimum acceptable levels, considering the time within which the impacts of not resuming them would become unacceptable
* identifying dependencies and supporting resources for these activities, including suppliers, outsource partners, and other relevant interested parties.

### **2.2.6 Service continuity/disaster recovery plans**

<table><tbody><tr><td><p><strong>Definition: Service continuity</strong></p></td></tr><tr><td><p>A set of clearly defined plans related to how an organization will recover from a disaster and return to a pre-disaster condition, considering the four dimensions of service management.</p></td></tr></tbody></table>

Service continuity plans guide the service provider when responding, recovering, and restoring a service to normal levels following disruption.

Service continuity plans usually include:
* Response plan This defines how the service provider initially reacts to a disruptive event in order to prevent damage, such as in cases of fire or cyber-attack.
* Recovery plan This defines how the service provider recovers the service in order to achieve the RTO and RPO.
* Plan of returning to normal operations This defines how the service provider resumes normal operations following recovery. For example, if an alternative data centre has been in use, then this phase will bring the primary data centre back into operation and restore the ability to invoke IT service continuity plans again.

In many a case, there is also a need for business continuity planning. Business continuity plans may include:
* emergency response to interface with all emergency services and activities
* evacuation plan to ensure the safety of personnel
* crisis management and public relations plan plans for the command and control of different crises and the management of the media and public relations
* security plan showing how all aspects of security will be managed on all home sites and recovery sites
* communication plan showing how all aspects of communication will be handled and managed with all relevant areas and parties involved during a major incident.

These plans are usually developed as part of the business continuity management practice.

## **2.3 Scope**

The service continuity management practice includes the following areas:
* performing BIA to quantify the impact of service unavailability to the service provider and service consumers
* developing service continuity strategies (and integrating them into the business continuity management strategy, if relevant). This should include elements of risk mitigation measures as well as the selection of appropriate, comprehensive recovery options
* developing and managing service continuity plans (and providing a clear interface to business continuity plans, if relevant)
* performing exercises and testing the service continuity plans invocation in case of disaster.

There are several activities and areas of responsibility that are not included in the service continuity management practice, although they are still closely related to service continuity management. These are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

### **Table 2.1 Activities related to the service continuity management practice described in other practice guides**

<table><colgroup data-width="601"><col><col></colgroup><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice Guide</strong></p></td></tr><tr><td><p>Communicating with customers to align the customer’s business continuity strategy and plans with service provider’s service continuity strategy and plans</p></td><td><p>Relationship management</p></td></tr><tr><td><p>Negotiating and agreeing customer requirements for service continuity</p></td><td><p>Service level management</p></td></tr><tr><td><p>Designing service continuity solutions as a part of the service model</p></td><td><p>Service design</p></td></tr><tr><td><p>Aligning service continuity solutions with business architecture</p></td><td><p>Architecture management</p></td></tr><tr><td><p>Identifying risks associated with service continuity</p></td><td><p>Risk management</p></td></tr><tr><td><p>Establishing and managing contracts with suppliers and partners</p></td><td><p>Supplier management</p></td></tr><tr><td><p>Monitoring the availability of services</p></td><td><p>Monitoring and event management</p></td></tr><tr><td><p>Justifying new service continuity solutions</p></td><td><p>Portfolio management</p></td></tr><tr><td><p>Implementing risk mitigation measures and changing the IT infrastructure in order to ensure resilience</p></td><td><p>Project management, change control</p></td></tr><tr><td><p>Managing and implementing improvements on an ongoing basis</p></td><td><p>Continual improvement</p></td></tr></tbody></table>

### **2.3.1 The line between availability and continuity**

The line between the service continuity and availability management practices is subtle. Both practices involve the concept of risk and work to identify and prepare for events that threaten to disable services. For both practices, either an understanding of VBFs and risk assessments or a BIA of service failures is required. Ultimately, both practices ensure the organization's resistance to failures.

Some organizations prefer not to separate the management of availability and continuity. However, there are some differences between the two practices, outlined in Table 2.2, that should be considered when designing a service management system.

### **Table 2.2 Distinction between Availability Management and Service continuity management**

<table><tbody><tr><td><p><strong>Availability Management</strong></p></td><td><p><strong>Service Continuity Management</strong></p></td></tr><tr><td><p>Focus on high-probability risks</p></td><td><p>Focus on high-impact risks (emergencies, disasters)</p></td></tr><tr><td><p>More proactive</p></td><td><p>More reactive</p></td></tr><tr><td><p>Reduces the likelihood of unwanted events</p></td><td><p>Reduces the impact of unwanted events</p></td></tr><tr><td><p>Focus on technical solutions</p></td><td><p>Focus on organizational measures</p></td></tr><tr><td><p>Optimization</p></td><td><p>Creating redundancy</p></td></tr><tr><td><p>Not a part of the corporate function</p></td><td><p>Often a part of the corporate function</p></td></tr><tr><td><p>Business as usual</p></td><td><p>Exceptional circumstances</p></td></tr><tr><td><p>MTRS, MTBF, MTBSI</p></td><td><p>RTO, RPO</p></td></tr></tbody></table>

The service continuity management practice does not cover minor or short-term failures that do not seriously impact the organization. It focuses on risks associated with significant damage, regardless of how likely or unlikely they are to occur. Often, these are emergency situations: fires, floods, power outages, data centre failures, and so on. Although the availability management practice does not ignore the negative impacts of failures on the service provider and consumer, minor interruptions of individual components are also considered in the process.

There is a tension between the objectives of the practices. The availability management practice works with statistics and analyzes trends; continuity management is concerned with how to respond to disruptive events.

Availability planning focuses on fulfilling current and future agreed requirements and avoiding deviations. The availability management practice finds and eliminates single points of failure; the countermeasures that are implemented are generally proactive and they reduce the likelihood of unwanted events. The service continuity management practice focuses on planning to manage the serious consequences of disruptive events. Backup sites, transitioning to alternative methods of service provision, and recovery procedures all reduce damage, but generally do not impact the probability of an incident.

### **2.3.2 Incident management**

The activities of the incident management practice are very similar to those of the service continuity management practice. However, the incident management practice focuses on failures which do not threaten the organization’s resilience, whereas the service continuity management practice focuses on high-impact failures which can prevent the organization from resuming service delivery.

Again, the line between these two practices is subtle and should be clearly defined in terms of impact to the service provider and service consumers. At the same time, in some cases (usually in small, single-site service providers) service continuity activities may be performed as a part of major incident management.

When service continuity plans are in place and managed separately from incident management activities, there should be a clear criterion for triggering service continuity procedures. When assessing the business impacts of an incident, support specialists should determine whether the major incident may lead to a disaster and inform the crisis management group so that they can make a decision about invocation.

<table><tbody><tr><td><p><strong>Definition: Invocation</strong></p></td></tr><tr><td><p>The act of declaring that a service provider’s service continuity plans must be enacted in order to continue service delivery.</p></td></tr></tbody></table>

### **2.3.3 The role of the service continuity practice when managing risks**

The concept of risk is central to the service continuity management practice. This practice generally focuses on mitigating high-impact, low-probability risks which cannot be totally prevented.

In order to mitigate risks, this practice focuses on minimizing expected losses so that, when disasters happen, they do not cause significant damage.

To ensure readiness regarding disruptive events, the service continuity management practice needs information about risks, which can be obtained through the risk management practice.

An effective service continuity management practice can contribute significantly to the organization’s risk management. A large number of risk-mitigation measures are related in some way to service-continuity options.

## **2.4 Practice success factors**

<table><tbody><tr><td><p><strong>Definition: Practice success factor</strong></p></td></tr><tr><td><p>A complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The service continuity management practice includes the following PSFs:
* developing and managing service continuity plans
* mitigating service continuity risks
* ensuring awareness and readiness.

### **2.4.1 Developing and managing service continuity plans**

To effectively respond to and recover from disasters, a service provider needs service continuity plans, which should reflect the chosen service continuity strategies. The service continuity strategies should be selected with respect to the service continuity requirements, which are identified during BIA.

Therefore, in order to develop and manage service continuity plans, the service provider should first perform BIA, then select the proper set of service continuity requirements, then define the service continuity strategy.

The Business Continuity Institute (BCI) defines the following continuity strategies<sup>6</sup>:
* diversification
* replication
* standby
* post-incident acquisition
* do nothing
* subcontracting

These are not one-time activities, so long as the service continuity requirements and the context of the service provider are changing; for example, when a service provider begins delivering their service to a new consumer. This event is a trigger for re-performing the BIA and updating the service continuity strategies. If there are no significant changes for a long period, BIA is generally performed once or twice a year and synchronized with risk assessment cycles. For more detail on BIA, refer to section 3.2.2.

### **2.4.1.1 Continuity plans**

BCI introduces three levels in the response and recovery planning structure: strategic, tactical, and operational<sup>7</sup>, as shown in Table 2.3.

### **Table 2.3 Levels in the response and recovery planning structure**

<table><colgroup data-width="607"><col><col></colgroup><tbody><tr><td><p><strong>Level</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Strategic</p></td><td><p>How executives make decisions about recovery process, communicate with external parties (including media, if relevant), and deal with any situations that are not covered in service continuity plans</p></td></tr><tr><td><p>Tactical</p></td><td><p>How management coordinates the recovery process in order to ensure the appropriate allocation of resources according to priorities (current business priorities, seasonal changes, and so on) and manage conflicts between the planning and recovery teams</p></td></tr><tr><td><p>Operational</p></td><td><p>How teams perform recovery activities, including responding to disruptive events, recovering to pre-defined levels of service, and/or providing alternative facilities to continue operations</p></td></tr></tbody></table>

Depending on the scale of the organization and whether the service provider is internal or external, there may be different solutions for structuring the plans; the responsible body may also vary.

Depending on the type of service provider and the scale of the organization, the structure of the service continuity plans may be more or less complex. Some common structures are outlined in Table 2.4.

### **Table 2.4 Continuity plans structure options**

<table><colgroup data-width="598"><col><col><col></colgroup><tbody><tr><td></td><td><p><strong>Small-scale organisation</strong></p></td><td><p><strong>Large-scale organisation</strong></p></td></tr><tr><td><p>Internal service provider</p></td><td><ul><li>In an IT department of a small-scale organization, there may not be any service continuity plans. All continuity arrangements may be managed as a part of business continuity management.</li><li>Specific IT service continuity activities may be performed as part of the incident management practice.</li></ul></td><td><ul><li>Strategic: a crisis management plan performed by executives. It is usually part of the business continuity plan.</li><li>Tactical: a number of plans, each one covering a product, service, business unit, site, or location, each with its own recovery team. Tactical IT department activities may be included in the business continuity plan, but they are more commonly designed as separate related plans.</li><li>Operational: a number of detailed procedures for specific recovery activities (such as restoring application data from a backup). Other departments may have their own specific operational instructions as a part of continuity plans.</li></ul></td></tr><tr><td><p>External service provider</p></td><td><p>All levels (strategic, tactical, operational) might be implemented as a single plan with a single team covering all aspects of response and recovery.</p></td><td><p>The description of continuity plans levels is similar to above, but the service provider is accountable for all levels.</p></td></tr></tbody></table>

Service continuity plans should cover the stages outlined in Table 2.5 following a disaster.

### **Table 2.5 Stages of response and recovery**

<table><colgroup data-width="612.0002"><col><col><col><col></colgroup><tbody><tr><td><p><strong>Stage</strong></p></td><td><p><strong>Response</strong></p></td><td><p><strong>Recover</strong></p></td><td><p><strong>Restore</strong></p></td></tr><tr><td><p>Plan</p></td><td><p>Response plan</p></td><td><p>Recovery plan</p></td><td><p>Plan of returning to normal operations</p></td></tr><tr><td><p>Content</p></td><td><ul><li>Events and scenarios which should trigger service continuity plans</li><li>Crisis management group contacts</li><li>Procedure for initial response and minimizing potential losses. There generally are procedures for specific scenarios (such as fires or power outages)</li><li>Documented criteria for choosing a recovery option (if relevant)</li><li>Communication procedures, including communications with customers, partners, and employees</li><li>Documented triggers for invocation</li></ul></td><td><ul><li>Recovery team members contacts</li><li>Guidelines for coordinating recovery teams</li><li>Detailed description of recovery procedures</li><li>Guidelines for monitoring and sharing information across the organization</li><li>Escalation procedures</li></ul></td><td><ul><li>Documented criteria to return to normal operations</li><li>Detailed descriptions of returning-to-normal-operations procedures</li><li>Instructions for restoring recovery site (if relevant)</li></ul></td></tr></tbody></table>

Plans should be clear, concise, and action oriented. Generally, they should exclude information that does not directly apply to the recovery teams that use them. Procedures should be time-based and include information about possible delays and interrelations between plans and teams.

For details about the organizational structure of response and recovery, see section 4.2.

Plans should be clear, concise, and action oriented. Generally, they should exclude information that does not directly apply to the recovery teams that use them. Procedures should be time-based and include information about possible delays and interrelations between plans and teams.

For details about the organizational structure of response and recovery, see section 4.2.

### **2.4.2 Mitigating service continuity risks**

The service continuity management practice includes the definition and management of controls to manage a wide range of risks. For this, it is used in conjunction with the risk management practice and other risk-focused practices (such as the capacity and performance management, availability management, and information security management practices). Agreed availability controls should be implemented through the service design, software development and management, and infrastructure and platform management practices<sup>8</sup>.

The service continuity options outlined in Table 2.6 may be designed and implemented as a part of the overall risk mitigation plan.

### **Table 2.6 The four dimensions of the service continuity management practice**

<table><colgroup data-width="612"><col><col></colgroup><tbody><tr><td><p><strong>Service Management Dimension</strong></p></td><td><p><strong>Service Continuity Measures</strong></p></td></tr><tr><td><p>Organizations and people</p></td><td><ul><li>Managing people during disasters</li><li>Using alternative sites and facilities</li></ul></td></tr><tr><td><p>Information and technology</p></td><td><ul><li>Physical security</li><li>Resilient telecommunication network</li><li>Data protection in operation: using RAID arrays, SAN, and so on to ensure the availability of data</li><li>Data backup</li><li>Fault-tolerant applications</li><li>Monitoring to provide prompt alerts</li></ul></td></tr><tr><td><p>Partners and suppliers</p></td><td><ul><li>Reciprocal agreements</li><li>Outsourcing services to multiple providers</li><li>Fire detection systems or suppression systems as a service</li></ul></td></tr><tr><td><p>Processes and value streams</p></td><td><ul><li>Manual operations and alternative methods of service delivery</li><li>Plans and procedures for response and recovery (service continuity plans)</li></ul></td></tr></tbody></table>

If BIA of a service indicates an earlier and higher impact, more preventive measures need to be adopted. If the initial impact is lower and develops slowly, a more economically effective approach is to invest in continuity and recovery countermeasures.

When choosing service continuity measures, the effectiveness and efficiency of each option should be assessed<sup>9</sup>. It is also important to continually control and validate their ongoing effectiveness and efficiency.

* **Effectiveness** According to risk management principles, the effects of a service continuity measure should be assessed and compared to the expected losses of the disruptive event.
* **Efficiency** The cost of the service continuity measure should be assessed and compared to the benefit. The benefit is calculated by estimating the reduction in the probability of the disruptive event occurring after the measure is implemented and multiplying it by the expected impact to the service provider and customers if the event occurs. This value, in terms of cost, should be compared to the cost of the measure’s implementation. Cost benefit analysis can be used here.

### **2.4.3 Ensuring awareness and readiness**

Recovery plans that have not been tested, often do not work as intended, if at all. Testing is therefore a critical part of service continuity management and the only way of ensuring that the selected strategy, implemented measures, and plans are actually working.

Testing service continuity plans is the way to check and increase readiness. By regularly revising the plans and procedures, recovery teams discover flaws and inefficiencies, then update the service continuity plans in order to reflect their findings.

BCI defines the following types of exercises<sup>10</sup>:
* walkthrough
* table-top exercises
* command-post exercises
* live
* test

The key characteristics and the purpose of each type, according the BCI Good practice Guidelines 2013, are outlined in Table 2.7.

### **Table 2.7 Exercise types**

<table><colgroup data-width="612.000306000136"><col><col><col></colgroup><tbody><tr><td><p><strong>Exercise Type</strong></p></td><td><p><strong>Key Characteristics</strong></p></td><td><p><strong>Purpose</strong></p></td></tr><tr><td><p>Walkthrough</p></td><td><ul><li>Discussion-based exercises</li></ul></td><td><ul><li>Allowing recovery team members to meet for the first time</li><li>Exploiting improvement opportunities</li></ul></td></tr><tr><td><p>Table-top exercises</p></td><td><ul><li>Discussion based on a given scenario</li></ul></td><td><p>Improving knowledge of the plans</p></td></tr><tr><td><p>Command-post exercises</p></td><td><ul><li>Recovery team members are given information</li></ul></td><td><p>Testing communication, decision making, and coordination</p></td></tr><tr><td><p>Live</p></td><td><ul><li>The most realistic way to test plans</li></ul></td><td><p>Testing the ability to achieve RTO, RPO, and minimum target service levels in case of a disruptive event</p></td></tr><tr><td><p>Test</p></td><td><ul><li>It is usually applied to specific hardware or software, such as restoring application data from backup</li></ul></td><td><p>Testing service component recovery when there is a higher risk of failure</p></td></tr></tbody></table>

Exercises should be conducted at planned intervals and when there are significant changes which may impact the recovery. The higher the possible impact of service outage, the higher the frequency of exercising should be.

Exercising is not only a way of ensuring readiness, it is an improvement opportunity. So it is generally a good idea to analyze the findings made during the testing and overall recovery team performance, then produce exercise reports that include findings and recommendations.

## **2.5 Key metrics**

The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other tools that can assist with this can be found in the measurement and reporting practice guide.

Key metrics for the service continuity management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.8.

### **Table 2.8 Example metrics for practice success factors**

<table><colgroup data-width="595"><col><col></colgroup><tbody><tr><td><p><strong>Practice Success Factor</strong></p></td><td><p><strong>Example Metrics</strong></p></td></tr><tr><td><p>Developing and managing service continuity plans</p></td><td><ul><li>Percentage of products and services with clearly documented continuity requirements</li><li>Percentage of (critical) products and services with documented service continuity plans</li><li>Timely updating of service continuity plans</li></ul></td></tr><tr><td><p>Mitigating service continuity riskRatio between actual losses and expected losses</p></td><td><ul><li>RTO achievement (real disasters and exercises)</li><li>RPO achievement (real disasters and exercises)</li><li>Percentage of effective continuity measures</li><li>Ratio between actual losses and expected losses</li></ul></td></tr><tr><td><p>Ensuring awareness and readiness</p></td><td><ul><li>Percentage of exercises and awareness sessions that were performed on schedule</li><li>Percentage of services for which continuity plans are tested in a given time period (usually last 6 months)</li></ul></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the service continuity management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

# 3. Value streams and processes

## **3.1 Value stream contribution**

Like any other ITIL management practice, service continuity management contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The service continuity management practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which the practice contributes are:
* deliver and support
* design and transition
* improve
* obtain/build
* plan

The contribution of the service continuity management practice to the service value chain is shown in Figure 3.1.

![Figure 3.1 Heat map of the contribution of the service continuity management practice to value chain activities](Service%20continuity%20management%20ITIL%204%20Practice%20Guide/Service_value_stream_service_continuity_management.png)

## **3.2 Processes**

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><p><strong>Definition: Process</strong></p></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

Service continuity management activities form five processes:
* governance of service continuity management
* business impact analysis
* developing and maintaining service continuity plans
* testing service continuity plans
* response and recovery.

### **3.2.1 Governance of service continuity management**

This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

### **Table 3.1 Input, activities, and outputs of the governance of service continuity management**

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Business impacts analysis report(s)</li><li>Risks register(s)</li><li>Customer requirements</li><li>Regulatory requirements</li><li>Risk appetite</li><li>StandardsAwareness and exercise programme development</li></ul></td><td><ul><li>Scope definition</li><li>Policy setting</li><li>Awareness and exercise programme development</li></ul></td><td><ul><li>Service continuity policy</li><li>Documented roles and responsibilities</li><li>Awareness and exercise programme</li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![Figure 3.2 Workflow for the governance of service continuity management](Service%20continuity%20management%20ITIL%204%20Practice%20Guide/Figure_3.2_continuity_management.png)

These activities may be carried out with varying levels of formality by many people in the organization. Table 3.2 describes these activities further.

### **Table 3.2 Activities of service continuity management**

<table><colgroup data-width="595"><col><col></colgroup><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Scope definition</p></td><td><p>Defining the service continuity management practice’s scope ensures clarity regarding which situations and areas of the organization it covers.</p><p>Organizational scope may be limited by products and services, sites and locations, customers, and so on. Products and services which are legacy or will be terminated soon are usually excluded from the scope, as are non-critical, low-margin products and services.</p><p>The costs of implementing a service continuity management practice can be high. Therefore, if a service provider initiates a service continuity management programme, some services, products, or sites might initially be excluded as part of a staged implementation.</p><p>Many different techniques can be used to define the practice’s scope, including cost benefit analysis, SWOT analysis, PESTLE analysis, and so on.</p><p>When defining scope, organizations should consider:</p><ul><li>previous business impact analysis report(s)</li><li><p>existing risks register(s)</p></li><li><p>customer requirements</p></li><li>regulatory requirements.</li></ul><p>It is also important to define the practice’s scope in terms of disasters.</p></td></tr><tr><td><p>Policy setting</p></td><td><p>Policy setting includes:</p><ul><li>Documenting the scope.</li><li>Assigning roles and responsibilities. If the service provider only initiates a service continuity programme, there will be no organizational structure to support any service continuity plans. In other cases, the organizational structures of response and recovery teams are usually the part of the service continuity policy.</li><li>Defining the general approach to service continuity management. Service continuity policies should clarify the available resources and limitations that should be considered during BIA.</li><li>Policies should be established and communicated as soon as possible so that all stakeholders involved in or affected by the service continuity management practice are aware of the scope, the limitations, and their responsibilities.</li><li>The scope and policies should be regularly revised (usually once a year). Revision may be triggered by disruptive events (especially any not covered by plans), a new service, a new customer, or a new relationship with a partner.</li></ul></td></tr><tr><td><p>Awareness and exercise programme development</p></td><td><p>Testing is a critical part of the overall service continuity management practice: it is the only way of ensuring that the selected strategy, measures, and plans are working.</p><p>Education, awareness training, and exercises should be planned to ensure that all parts of the practice (site, team member, service, or CI) are tested at least once a year.</p><p>Exercise programme should ensure testing all four dimensions of service management:</p><p><strong>Organizations and people:</strong></p><ul><li>The right people with the right skills</li><li>Recovery team members’ knowledge and experience</li><li>Staff are aware of service continuity plans</li></ul><p><strong>Information and technology:</strong></p><ul><li>required equipment works</li><li>required data is available</li></ul><p><strong>Partners and suppliers:</strong></p><ul><li>readiness of third parties involved in response and recovery to meet service continuity requirements</li></ul><p><strong>Processes and value streams:</strong></p><ul><li>procedures are correct, consistent, and manageable</li></ul></td></tr></tbody></table>

### **3.2.2 Business impact analysis**

This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

### **Table 3.3 Inputs, activities, and outputs of the business impact analysis process**

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Service documentation</li><li>Risk assessment reports</li><li>Financial data of loss of VBFs</li><li>Major incident reports</li><li>Service models</li><li>Risk management policy</li><li>Risk appetite</li><li>Regulatory requirements</li></ul></td><td><ul><li>VBF identification</li><li>Analysis of the consequences of disruption</li><li>VBF interdependencies identification</li><li>Determination of the service continuity requirements</li></ul></td><td><ul><li>Priority list of VBFs</li><li>Documented impacts from a loss of VBFs</li><li>Documented VBF interdependencies</li><li>Business impact analysis report</li></ul></td></tr></tbody></table>

Figure 3.3 shows a workflow diagram of the process

![Figure 3.3 Workflow of the business impact analysis process](Service%20continuity%20management%20ITIL%204%20Practice%20Guide/Figure_3.3_Workflow_of_the_business_impact_analysis_process.png)

These activities may be carried out with varying levels of formality by many people in the organization. Table 3.4 outlines these activities further.

### **Table 3.4 Activities of the business impact analysis process**

<table><colgroup data-width="596"><col><col></colgroup><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>VBF identification</p></td><td><ul><li>VBF refers to the part of a service that is critical to the success of the service provider and/or customers. It is important that the VBFs are recognized and documented to provide the appropriate focus and resources allocation.</li><li>Many different techniques can be used to identify risks, including brainstorming, interviews with stakeholders (including customers and users), analysis of the service documentation, and so on.</li><li>If the service provider has an established risk management practice, information about risk assessments might be useful for understanding the most critical areas.</li></ul></td></tr><tr><td><p>Analysis of the consequences of disruption</p></td><td><p>When VBFs are identified, the impacts of disruption should be determined. This impact could be a ‘hard’ impact that can be precisely identified, such as financial loss, or a ‘soft’ impact, such as a tarnished reputation or loss of competitive advantage.</p><p>The following forms of loss proposed by FAIR10F11 might be considered:</p><ul><li>Productivity: the reduction in a service provider’s ability to deliver services</li><li>Response: expenses associated with managing a loss event</li><li>Replacement: the intrinsic value of an asset, the expense associated with replacing lost or damaged assets (for example, purchasing a replacement server)</li><li>SLA fines and regulatory judgments: legal or regulatory actions levied against the service provider</li><li>Competitive advantage: losses associated with diminished competitive advantage.</li><li>Reputation: losses associated with an external perception of the service provider</li></ul><p>Impacts may change over time. A service provider and customers may be able to function without a particular service or VBF for a short period of time, but over time the impacts may increase until the service provider or customers can no longer operate.</p><p>One of the key outputs from a BIA exercise is a graph of the anticipated losses of an IT service or specific VBF over time. This graph is then used to drive the service continuity strategies and plans.</p><p>Losses due to service outages more commonly grow exponentially over time. Along with losses related to the reduction in an organization’s ability to generate its primary value proposition, there are also threats of fines, judgements, and reputational damage.</p></td></tr><tr><td><p>VBF interdependencies identification</p></td><td><p>The interdependencies between VBF and service components and key internal and external resources should be identified and documented.</p><p>To do this, the service provider may use service and configuration models if a configuration management database is in place. Component failure impact analysis (CFIA) may also be a useful technique. CFIA can be used for identifying single points of failure, existing redundancies, and so on.</p></td></tr><tr><td><p>Determination of the service continuity requirements</p></td><td><p>Based on the analysis of the consequences of disruption and the identified interdependencies, the service provider should determine service continuity requirements for each service or VBF within the scope of service continuity management, including:</p><ul><li>recovery time objective(s)</li><li>recovery point objective(s)</li><li>minimum target service level(s)</li></ul></td></tr></tbody></table>

### **3.2.3 Developing and maintaining service continuity plans**

This process includes the activities listed in Table 3.5 and transforms the inputs into outputs.

### **Table 3.5 Inputs, activities, and outputs of the developing and maintaining service continuity plans process**

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Business impact analysis report(s)</li><li>Existing controls</li><li>Information about available resources</li><li>Consumer’s continuity plans</li><li>Service continuity policy</li></ul></td><td><ul><li>Service continuity strategy development</li><li>Service continuity plans development</li><li>Initial testing of service continuity plans</li></ul></td><td><ul><li>New and updated controls</li><li>Service continuity strategies</li><li>Service continuity plans</li></ul></td></tr></tbody></table>

Figure 3.4 shows a workflow diagram of the process.

![Figure 3.4 Workflow of the developing and maintaining service continuity plans process](Service%20continuity%20management%20ITIL%204%20Practice%20Guide/Figure_3.4_Workflow_of_the_developing_and_maintaining_service_continuity_plans_process.png)

These activities may be carried out with varying levels of formality by many people in the organization. Table 3.6 outlines these activities further.

### Table 3.6 Activities of the developing and maintaining service continuity plans process

<table><colgroup data-width="596"><col><col></colgroup><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Service continuity strategy development</p></td><td><ul><li>Based on the BIA report(s) the service provider should determine an appropriate and cost-effective set of service continuity strategies.</li><li>For processes and services with earlier and higher impacts, more preventive measures should be adopted. For processes and services where the impact is lower and takes longer to develop, greater emphasis should be placed on recovery measures.</li></ul></td></tr><tr><td><p>Service continuity plans development</p></td><td><ul><li>Based on the service continuity policy and strategies, the service provider should develop and maintain service continuity plans.</li><li>Where services or recovery team members have changed, it is essential that plans are updated. Plans may also be updated following exercise or actual recovery.</li></ul></td></tr><tr><td><p>Initial testing of service continuity plans</p></td><td><p>Before publishing, service continuity plans should be tested. The methods of initial testing are similar to ongoing exercising.</p></td></tr></tbody></table>

### **3.2.4 Testing service continuity plans**

This process includes the activities listed in Table 3.7 and transforms the inputs into outputs.

### **Table 3.7 Inputs, activities, and outputs of the testing service continuity plans process**

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Awareness and exercise programme</li><li>Service continuity plans</li></ul></td><td><ul><li>Performing exercises</li><li>Service continuity audit</li></ul></td><td><ul><li>Exercise report(s)</li><li>Requirements for new and updated controls</li><li>Request for change of policy or plans</li><li>Audit reports</li></ul></td></tr></tbody></table>

Figure 3.5 shows a workflow diagram of the process.

![Figure 3.5 Workflow of the testing service continuity plans process](Service%20continuity%20management%20ITIL%204%20Practice%20Guide/figure_3.5_service_continuity_management.png)

These activities may be carried out with varying levels of formality by many people in the organization. Table 3.8 outlines these activities further.

### **Table 3.8 Activities of the testing service continuity plans process**

<table><colgroup data-width="595"><col><col></colgroup><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Performing exercises</p></td><td><ul><li>Exercises should be conducted at planned intervals and when significant changes may impact recovery. The higher the possible impact of a service outage is, the higher the frequency of exercising should be.</li><li>Exercising and testing are not only ways of ensuring readiness; they are also improvement opportunities. It is generally a good idea to analyze the results of testing and the overall recovery team performance, then produce exercise reports that include outcomes and recommendations.</li><li>Exercise reports might include requirements for new or updated existing controls or request for change of service continuity plan.</li><li>If exercise is failed, the schedule of following exercises is updated in order to re-perform the failed exercise as soon as possible.</li></ul></td></tr><tr><td><p>Service continuity audit</p></td><td><ul><li>Service continuity audits ensure that BIA, service continuity strategies and plans remain appropriate and relevant as the environment changes. Audits are usually carried out on a scheduled basis, but may be triggered by failed exercise or failed recovery.</li><li>Audits may be carried out internally, or by third parties. The output of the audit may identify a need to implement new or updated controls or adjust service continuity policy or plans.</li></ul></td></tr></tbody></table>

### **3.2.5 Response and recovery**

This process includes the activities described in Table 3.9 and transforms inputs into outputs.  

### **Table 3.9 Inputs, activities, and outputs of the response and recovery process**

<table><tbody><tr><td><strong>Key inputs</strong></td><td><strong>Activities</strong></td><td><strong>Key outputs</strong></td></tr><tr><td><ul><li>Service continuity plans</li><li>Incident record(s)</li></ul></td><td><ul><li>Invocation</li></ul><ul><li>Executing service continuity plans</li></ul></td><td><ul><li>Recovery report(s)</li></ul><ul><li><span>Requirements for new and updated controls</span></li></ul><ul><li>Request for change plans</li></ul></td></tr></tbody></table>

Figure 3.6 shows a workflow diagram of the process.

![Figure 3.6 Workflow of the response and recovery process.](Service%20continuity%20management%20ITIL%204%20Practice%20Guide/Figure_3.6_service_continuity_management.png)

These activities may be carried out with varying levels of formality by many people in the organization. Table 3.10 outlines these activities further.

### **Table 3.10 Activities of the response and recovery process**

<table><colgroup data-width="595"><col><col></colgroup><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Invocation</p></td><td><p>Invocation is an act of declaring that an organization’s continuity arrangements need to be put into effect in order to continue delivering key products and services12.</p><p>This decision on invocation is typically made by a ‘crisis management’ team (within the strategic level of the organization’s structure13), accounting for the:</p><ul><li>Potential impact of the service outage</li><li>Likely duration of the service outage</li><li>Time of day/month/year</li></ul><p>Crisis management teams may decide not to invoke service continuity plans if the risks are low.</p><p>In cases of invocation, crisis management teams should also:</p><ul><li>Decide which recovery options the service provider is going to use (if several options are available)</li><li>Define the scope of the invocation (services, products, sites, locations, and so on)</li></ul><p>Invocation is the ultimate test of service continuity plans. If the preparatory work has been completed and plans have been developed and tested, then invocation should be straightforward. If the plans have not been tested, failures can be expected.</p></td></tr><tr><td><p>Executing service continuity plans</p></td><td><p>Once invocation happens, all of the involved recovery teams should perform service continuity procedures. Recovery is likely to be a time of high activity, involving long hours for many individuals. This must be recognized and managed by the recovery team coordinators on a tactical level.</p><p>A disruption could occur at any time, so it is essential that guidance on the invocation process is readily available to key staff in and away from the office.</p><p>The recovery process generally includes the following stages:</p><ul><li>Response: responding to a disruptive event in order to prevent damage, such as in cases of fire or cyber-attack.</li><li>Recovery: Resuming service delivery according RTO, RPO, and minimum target service levels.</li><li>Returning to normal operations.</li></ul></td></tr></tbody></table>

# 4. Organizations and people

## **4.1 Roles, competencies, and responsibilities**

The ITIL practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

#### **Table 4.1 Competency codes and profiles**

<table><colgroup data-width="597"><col><col></colgroup><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p><strong>L</strong></p></td><td><p><strong>Leader </strong>Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p><strong>A</strong></p></td><td><p><strong>Administrator </strong>Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p><strong>C</strong></p></td><td><p><strong>Coordinator/communicator </strong>Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p><strong>M</strong></p></td><td><p><strong>Methods and techniques expert </strong>Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p><strong>T</strong></p></td><td><p><strong>Technical expert </strong>Providing technical (IT) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

Examples of the roles involved in the service continuity management practice are listed in Table 4.2, together with the associated competency profiles and specific skills.

#### **Table 4.2 Examples of roles with responsibility for service continuity management activities**

<table><colgroup data-width="613"><col><col><col><col></colgroup><tbody><tr><td><p><strong>Process Activity</strong></p></td><td><p><strong>Responsible Roles</strong></p></td><td><p><strong>Competency Profile</strong></p></td><td><p><strong>Specific Skil</strong>ls</p></td></tr><tr><td colspan="4"><span>Governance of service continuity management process</span></td></tr><tr><td><p>Scope definition</p></td><td><p>Steering committee</p></td><td><p>MC</p></td><td><p>Visibility across PESTLE factors influencing the organization</p></td></tr><tr><td><p>Policy setting</p></td><td><p>Steering committee</p></td><td><p>MCL</p></td><td><ul><li>Awareness of organization‑specific documentation requirements</li><li>Ensuring ongoing engagement of managers to ensure clarity and the ongoing realization of service continuity policies</li></ul></td></tr><tr><td><p>Awareness and exercise programme development</p></td><td><p>Continuity administrator</p></td><td><p>ACM</p></td><td><ul><li>Knowledge of exercise types and recovery teams’ structures</li><li>Enabling communication channels</li></ul></td></tr><tr><td colspan="4"><span>Business impact analysis process</span></td></tr><tr><td><p>VBF identification</p></td><td><ul><li>Service or product owner</li><li>Relationship manager</li><li>Service designer</li><li>Customer</li></ul></td><td><p>CM</p></td><td><ul><li>Business analysis</li><li>Good knowledge of the service consumer’s business</li><li>Good knowledge of products, including their architecture and configuration</li></ul></td></tr><tr><td><p>Analysis of the consequences of disruption</p></td><td><ul><li>Service or product owner</li><li>Relationship manager</li><li>Customer</li></ul></td><td><p>MC</p></td><td><ul><li>Good knowledge of the service consumer’s business</li><li>Ability to systematically apply qualitative and quantitative risk analysis tools</li><li>Professional competencies and visibility over PESTLE factors that influence the service</li></ul></td></tr><tr><td><p>VBF interdependencies identification</p></td><td><ul><li>Service or product owner</li><li>Service designer</li><li>Technical expert</li><li>Architecture management expert</li></ul></td><td><p>MT</p></td><td><p>Good knowledge of products, including their architecture and configuration</p></td></tr><tr><td><p>Determination of the service continuity requirements</p></td><td><ul><li>Service or product owner</li><li>Continuity administrator</li></ul></td><td><p>MTC</p></td><td><ul><li>Good understanding of recovery process</li><li>Understanding of service continuity policy</li></ul></td></tr><tr><td colspan="4"><span>Developing and maintaining service continuity plans process</span></td></tr><tr><td><p>Service continuity strategies development</p></td><td><ul><li>Continuity administrator</li><li>Service designer</li><li>Technical expert</li></ul></td><td><p>TM</p></td><td><ul><li>Good understanding of service continuity options</li><li>Awareness of existing controls</li><li>Awareness of technology available on the market</li></ul></td></tr><tr><td><p>Service continuity plans development</p></td><td><ul><li>Continuity administrator</li><li>Technical expert</li></ul></td><td><p>MTA</p></td><td><ul><li>Excellent documentation skills</li><li>Excellent logical skills</li><li>Good understanding of interdependencies of service components</li><li>Good understanding of technology</li></ul></td></tr><tr><td><p>Initial testing of service continuity plans</p></td><td><ul><li>Continuity administrator</li><li>Response and recovery coordinators and team members</li></ul></td><td><p>CATL</p></td><td><ul><li>Coordination and communication</li><li>Excellent knowledge of service continuity plans</li><li>Understanding of technology used as part of service continuity strategy</li></ul></td></tr><tr><td colspan="4"><span>Testing service continuity plans process</span></td></tr><tr><td><p>Performing exercises</p></td><td><ul><li>Continuity administrator</li><li>Response and recovery coordinators and team members</li></ul></td><td><p>CATL</p></td><td><ul><li>Coordination and communication</li><li>Excellent knowledge of service continuity plans</li><li>Understanding of technology used as part of service continuity strategy</li></ul></td></tr><tr><td><p>Service continuity audit</p></td><td><p>Internal or external auditors (as mandated and on behalf of the board of directors)</p></td><td><p>CAMT</p></td><td><ul><li>Audit management techniques</li><li>Command of common audit practices</li><li>Assured auditor integrity, objectivity, and independence</li></ul></td></tr><tr><td colspan="4"><span>Response and recovery process</span></td></tr><tr><td><p>Invocation</p></td><td><p>Crisis management group</p></td><td><p>LC</p></td><td><ul><li>Excellent understanding of service provider’s and consumers’ risks</li><li>Understanding of consumer context</li><li>Coordination and communication</li></ul></td></tr><tr><td><p>Executing service continuity plans</p></td><td><ul><li>Crisis management group</li><li>Continuity administrator</li><li>Response and recovery coordinators and team members</li></ul></td><td><p>CATL</p></td><td><ul><li>Coordination and communication</li><li>Excellent knowledge of service continuity plans</li><li>Understanding of technology used as part of service continuity strategy</li></ul></td></tr></tbody></table>

## **4.2 Organizational structures and teams**

Disasters are high-impact events, so responses must be very quick; the coordination of response and recovery activities requires flexibility. Therefore, the business-as-usual structure is not relevant for disasters.

During the recovery process, the organizational structure is generally based around the levels of continuity plans. The levels of organizational structure for response and recovery are outlined in Table 4.3.

### **Table 4.3 Organizational structure for response and recovery**

<table><colgroup data-width="611"><col><col><col></colgroup><tbody><tr><td><p><strong>The level of continuity plans</strong></p></td><td><p><strong>Organizational Level</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Strategic</p></td><td><p>Executive level</p></td><td><p>This includes senior management/executives, who have overall authority and control within the organization and who are responsible for crisis management and liaising with other departments, divisions, organizations, the media, regulators, emergency services, and so on.</p></td></tr><tr><td><p>Tactical</p></td><td><p>Coordination level</p></td><td><p>Typically one level below the executive group, this group is responsible for coordinating the overall recovery effort within the organization.</p></td></tr><tr><td><p>Operational</p></td><td><p>Specialist level</p></td><td><p>A series of service recovery teams that are responsible for executing plans within their own areas and for liaising with staff, customers, and third parties. Within IT, recovery teams should be grouped by services and products.</p></td></tr></tbody></table>

# 5. Information and technology

## **5.1 Information exchange, inputs/outputs**

The effectiveness of the service continuity management practice is based on the quality of the information used. This information can include:
* consumer’s business processes
* services and their architecture and design
* partners and suppliers and information on the services they provide
* regulatory requirements regarding service continuity
* technology and services available on the market that may be relevant for service continuity arrangements

The key inputs and outputs of the practice are listed in section 3.

Service continuity plans are the core of the practice. They should be up to date and available for all involved parties.

## **5.2 Automation and tooling**

Especially in large-scale organizations, the service continuity practice should be automated. Where this is possible and effective, it may involve the solutions outlined in Table 5.1.

### **Table 5.1 Automation solutions for service continuity management activities**

<table><colgroup data-width="611.99694000612"><col><col><col><col></colgroup><tbody><tr><td><p><strong>Process activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><p><strong>Key Functionality</strong></p></td><td><p><strong>Impact on the effectiveness of the practice</strong></p></td></tr><tr><td colspan="4"><p>Governance of service continuity management process</p></td></tr><tr><td><p><span>Scope definition</span></p><p>Policy Setting</p></td><td><p><span>Knowledge management tools and document repositories</span></p></td><td><p><span>Service continuity policies, including the scope of the programme, guidelines, and roles and responsibilities, need to be easily accessible by the service provider staff, regulators, and external stakeholders, such as customer representatives</span></p></td><td><p><span>Low</span></p></td></tr><tr><td><p><span>Awareness and exercise programme development</span></p></td><td><p><span>Business continuity planning tools</span></p></td><td><p><span>Service continuity administrators, service owners, and recovery team members should have access to the exercise schedule and information about the scope of the exercise in which they are involved</span></p></td><td><p><span>Medium</span></p></td></tr><tr><td colspan="4"><span>Business impact analysis process</span></td></tr><tr><td><p><span>VBF identification</span></p></td><td><p><span>Service catalogue, CMDB, BPM tools</span></p></td><td><p><span>To identify VBFs, the service analyst should have access to information about the service components and actions. BPM tools may provide information about the consumer’s processes and operations supported by the service</span></p></td><td><p><span>High</span></p></td></tr><tr><td><p><span>Analysis of the consequences of disruption</span></p></td><td><ul><li><span>Business continuity planning tools</span></li><li><span></span>analytical tools,</li><li><span></span>risk assessment tools, incident management tools</li></ul></td><td><p><span>Analysis can be underpinned by a variety of management systems data, such as incident reports and information about realized risks. Analysts may also use modelling tools to forecast expected losses in case of service or specific VBF outages.</span></p></td><td><p><span>High</span></p></td></tr><tr><td><p><span>VBF interdependencies identification</span></p></td><td><p><span>Business continuity planning tools, CMDB, analytical tools</span></p></td><td><p><span>Analysts may use service and configuration models to identify key service and VBF interdependencies.</span></p></td><td><p><span>High</span></p></td></tr><tr><td><p><span>Determination of the service continuity requirements</span></p></td><td><p><span>Business continuity planning tools, service catalogue</span></p></td><td><p><span>Continuity administrator, service owners and recovery team members should have access to service continuity requirements.</span></p></td><td><p><span>Low</span></p></td></tr><tr><td colspan="4"><span>Developing and maintaining service continuity plans process</span></td></tr><tr><td><p><span>Service continuity strategies development</span></p></td><td><p><span>Business continuity planning tools, CMDB, change initiation and control tools</span></p></td><td><ul><li><span>Determining existing controls and resilience measures</span></li><li><span>Initiating changes that should be implemented as a part of service continuity strategy realization</span></li></ul></td><td><p><span>Medium</span></p></td></tr><tr><td><p><span>Service continuity plans development</span></p></td><td><p><span>Business continuity planning tools, document control tools</span></p></td><td><p><span>Control of expiry dates, version control, and archiving of documents</span></p></td><td><p><span>Low to high, depending on the volume of documents to manage</span></p></td></tr><tr><td><p><span>Initial testing of service continuity plans</span></p></td><td colspan="3"><p><span>See ‘performing exercises’</span></p></td></tr><tr><td colspan="4"><span>Testing service continuity plans process</span></td></tr><tr><td><p><span>Performing exercises</span></p></td><td><p><span>Conferencing tools, monitoring tools, technology management, and system administration tools</span></p></td><td><p><span>All involved parties should be able to communicate and collaborate, have ongoing understanding of current situation and manage service components in order to execute service continuity plans.</span></p></td><td><p><span>High</span></p></td></tr><tr><td><p><span>Service continuity audit</span></p></td><td><p><span>Knowledge management tools and document repositories</span></p></td><td><p><span>The auditors should have access to the service continuity documentation, including plans, exercise programmes, exercise reports, and recovery reports.</span></p></td><td><p><span>Medium</span></p></td></tr><tr><td><p><span><strong>Response and recovery process</strong></span></p></td></tr><tr><td><p><span>Invocation</span></p></td><td><ul><li><span>Monitoring tools</span><span></span></li></ul><ul><li>emergency notification</li><li><span>conferencing tools</span></li><li>incident management tools</li></ul></td><td><p><span>Crisis management group must be able to get information about event and instantly direct response and recovery process.</span></p></td><td><p><span>High</span></p></td></tr><tr><td><p><span>Executing service continuity plans</span></p></td><td><ul><li><span>Conferencing tools,</span><span><br>emergency management tools</span></li><li><span>monitoring tools</span></li><li><span>technology management and system administration tools,</span></li><li><span>incident management tools</span></li></ul></td><td><p><span>All involved parties should be able to communicate and collaborate, have an ongoing understanding of the current situation, and manage service components in order to execute service continuity plans</span></p></td><td><p><span>High</span></p></td></tr></tbody></table>

# 6. Partners and suppliers

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL® Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the practice guides for service design, architecture management, and supplier management.

Partners and suppliers may provide critical products and service components. The service provider needs to negotiate and agree service continuity requirements with partners and suppliers in order to meet service continuity requirements.

Partners and suppliers may also provide continuity services and solutions, such as backup site, on-demand computing, disaster recovery as a service, and so on. In these cases, they should also be involved in service continuity plan development, testing, and execution.

# 7. Important reminder

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:
* focus on value
* start where you are
* progress iteratively with feedback
* collaborate and promote visibility
* think and work holistically
* keep it simple and practical
* optimize and automate

More information on the guiding principles and their application can be found in section 4.3 of ITIL® Foundation: ITIL 4 Edition.

# 8. Acknowledgments

AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

## **8.1 Authors**

Pavel Demin

## **8.2 Reviewers**

Dinara Adyrbai, Roman Jouravlev

## References

1\. ISO 22300:2012

2\. See the availability management practice guide for details.

3\. BCI Good practice guidelines 2013

4\. ISO 22301:2012

5\. BCI Good practice guidelines 2013

6\. BCI Good practice guidelines 2013

7\. BCI Good practice guidelines 2013

8\. Risk management practice

9\. For details see Risk management practice.

10\. BCI Good practice guidelines 2013

11\. An Introduction to Factor Analysis of Information Risk (FAIR)

12\. ISO 22301:2012

13\. See 4.2 for details
