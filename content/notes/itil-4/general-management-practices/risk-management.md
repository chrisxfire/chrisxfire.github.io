---
title: risk management
date: 2023-10-20T00:00:00-06:00
draft: true
weight: 1
---


January 10, 2020
36 min read

ITIL
ITIL4 Practice Guides
Risk management: ITIL 4 Practice Guide
27 Likes
This document provides practical guidance for the risk management practice.

Table of Contents
1. 
About this document
It is split into five main sections, which cover:

general information about risk management
the processes and activities of risk management and their roles in the service value chain
the organizations and people involved in risk management
the information and technology supporting risk management
considerations for partners and suppliers for risk management.
1.1 ITIL® 4 Qualification scheme
Selected content of this document is examinable as a part of the following syllabuses:

ITIL Specialist: Create, deliver and support
ITIL Specialist: Direct, plan, improve.
2. 
General information
2.1 Purpose and description
The purpose of the risk management practice is to ensure that the organization understands and effectively handles risks. Managing risk is essential to ensuring the ongoing sustainability of an organization and co-creating value for its customers. Risk management is an integral part of all organizational activities and therefore central to the organization’s service value system (SVS).

Risk management is performed at all levels of the organization. Strategic risk management considers long-term risks that may impact the ability of the organization to perform its mission. Programme and project risk management considers risks that may affect medium-term goals and objectives. Operational risk management is focused on short-term goals and objectives. Risk management at each of these levels must be based on direction from the governors of the organization.

The ITIL definition of a service specifically identifies that managing risks on behalf of service consumers is an essential part of every service.

Service

A means of enabling value co-creation by facilitating outcomes that customers want to achieve, without the customer having to manage specific costs and risks.

Every service removes some risks from the service consumer, but also imposes additional risks on the service consumer. The service provider must understand and manage these risks in a controlled manner. The balance between the risks removed and the risks imposed, is part of the value proposition of the service.

The risk management practice provides an organization with the resources required to identify and manage risks efficiently and effectively, across all four dimensions of service management.

2.2 Terms and concepts
2.2.1 Risk
Risk

A possible event that could cause harm or loss, or make it more difficult to achieve objectives. Can also be defined as uncertainty of outcome, and can be used in the context of measuring the probability of positive outcomes as well as negative outcomes.

Risk is normally avoided because of its association with threats. Although this is generally true, risk is also associated with opportunity.

Any uncertain outcome is a risk. When the risk is negative the uncertain outcome would result in harm or loss. Yet, when the risk is positive the uncertain outcome would result in benefits to one or more stakeholders. For example, an organization may invest in a new service, in the expectation that it will attract customers and generate revenue. However, a positive outcome is not guaranteed, instead the outcome is uncertain or a risk. Positive risks are sometimes called opportunities.

The failure to take opportunities can be a risk. An organization that does not invest in its services or in developing its customer relationships will not retain its market position. The environment in which organizations operate is constantly evolving, and the failure to evolve can pose a risk to the organization.

2.2.2 Risk capacity
Risk capacity is defined by the governance of the organization. Risk management activities must ensure that risks remain below the risk capacity.

If the level of risk in an organization is too high, then this could have a major impact on the organization’s ability to continue operating. The risk capacity of an organization is the maximum amount of risk that the organization can tolerate and is often based on factors such as damage to reputation, assets, and so on.

2.2.3 Risk appetite
Risk appetite is defined by the governance of the organization and is used to facilitate decision- making and risk management activities.

Some organizations choose to take significant risks to make significant gains. Other organizations prefer to take few risks, but this also reduces their opportunities. The risk appetite of an organization is the amount of risk that the organization is willing to accept. This should always be less than the risk capacity of the organization.

2.2.4 Risk register
It is important to keep a record of identified risks, that records the risk’s current status and history. This record is known as a risk register. Each entry in the risk register shows the history and status of a single risk. Typically, this will include the following information (but this can vary depending on the needs of the organization):

unique ID
category (to group similar types of risk)
description
probability
impact
overall rating or score
owner
treatment
updated rating or score after treatment (residual risk)
action date (s).
An organization may have more than one risk register depending on the size and structure of the organization, and the number and types of risks that are being managed.

2.2.5 Risk owner
The risk owner may not be responsible for the actions needed to manage the risk, but they must ensure that these actions are appropriate and that they are actually taken.

Every risk must have an assigned owner who is accountable for ensuring that the risk has been understood and appropriately managed. The risk owner should be assigned as soon as the risk has been identified and should be documented in the risk register.

2.2.6 Risk treatment
Sometimes it is possible to eliminate a risk, but this is unusual. After the probability and the impact of the risk has been understood, the risk owner must agree on a suitable way to treat the risk. Actions that can be taken to treat a risk are shown in Table 2.1

Table 2.1 Risk treatment options
Treatment

Description

Example

Risk avoidance

Prevent the risk by not performing the risky activity

Avoid the risk of an investment failing to deliver the expected value, by rejecting the business case proposing the investment

Risk modification (or risk reduction)

Implement controls to reduce the likelihood or impact of the risk

Encrypt sensitive information when it is transmitted on the network to reduce the likelihood of it being intercepted

Risk sharing

Reduce the impact by passing some of the risk to a third party

Take out insurance against fire, or against a cyber attack

Risk retention (or risk acceptance)

Intentionally decide to accept the risk because it is below an acceptable threshold (and within the risk appetite of the

organization)

Accept the risk of an investment failing to deliver the expected value, by accepting the business case proposing the investment

When dealing with positive risks (opportunities), the terms are usually expressed slightly differently. Risk avoidance becomes risk exploitation and risk reduction becomes risk enhancement. However, the term risk modification covers both positive and negative risks.

2.2.7 Control
Control

The means of managing a risk, ensuring that a business objective is achieved, or that a process is followed.

Risk modification requires implementation of controls to reduce the likelihood or impact of a risk.

A control can be based on technology, for example a firewall or a resilient network configuration, but it can also be related to any of the other dimensions of service management. Some examples of controls for each dimension are shown in Table 2.2

Table 2.2 Example controls
Domain

Example controls

Organizations and people

Clear desk policy
Security awareness training
Information and technology

Network firewall
Audit records
Suppliers and partners

Contractual requirements for the supplier to be certified to a quality management system standard
Regular audit of supplier activities
Value streams and processes

Evaluation of changes before deployment
Reference checks during employee recruitment
2.2.8 Residual risk
Risk treatment does not usually eliminate a risk completely. Therefore, after the application of controls, it is necessary to perform a new risk assessment. This is to understand the new likelihood and impact and to then calculate the residual risk. The organization could then choose to apply more controls to further reduce the risk. Alternatively, the organization could accept the residual risk which should be documented in the risk register and communicated to the interested stakeholders, in the same way as any other retained risk.

2.3 Scope
The scope of risk management is very broad. Most activities and all people within an organization, have some role to play in risk management. The service provider must understand and manage the many risks that are relevant to each service and to each customer. Many of the management practices described in ITIL 4 require risk management as part of their activities. These include:

project management
information security management
portfolio management
problem management
incident management
service continuity management
continual improvement
service level management.
There are several activities and areas of responsibility not included in the risk management practice, although they are still closely related to the management of risk. These are listed in Table 2.3, along with references to the practice guides in which they can be found. It is important to remember that the ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

Table 2.3 Activities related to the risk management practice that are described in other practice guides
Activity

Practice guide

Management of specific risks

All practices

Implementation of changes to mitigate risks

Organizational change management

Change enablement

Release management

Deployment management

Software development and management 

Service validation and testing 

Infrastructure and platform management 

Workforce and talent management

Project management

Costs control, financial evaluation of risks and risk mitigation options

Service financial management

Definition of vision and strategic objectives for risk management

Strategy management

2.3.1 Project management
A significant part of project management is managing project risks. Every project should be analysed in terms of alignment with strategic objectives, costs, risks, benefits, and progress. This should result in the creation of a project risk register, which is maintained throughout the project lifecycle and used to ensure that project risks are appropriately managed.

Some project risks may need to be managed outside the project and for this purpose may be included on other risk registers.

2.3.2 Information security management
The purpose of information security management is to protect the information needed by the organization to conduct its business. This includes understanding and managing risks that relate to the confidentiality, integrity, and availability of information, as well as other aspects of information security such as authentication (ensuring someone is who they claim to be) and non- repudiation (ensuring that someone cannot deny that they took an action).This means that risk management plays a very large part in the information security management practice. Ideally this should not be separate from other aspects of risk management. An organization may choose to keep a risk register for information security management, but any significant information security risks should also appear on an organizational risk register. Some of these information security risks may be owned and managed by information security managers, service owners, or practice owners, but others will need to be escalated to senior management as they could pose an existential threat to the organization.

Information security management usually creates and manages many controls and maintains these as the threats and vulnerabilities evolve.

2.3.3 Portfolio management
The organization’s portfolio can be mapped to an underlying portfolio of managed risks. When service management is effective, products and services in the service catalogue and pipeline represent opportunities to create and capture value for customers, the organization, and other stakeholders. Otherwise, those products and services can represent threats, due to the possibility of failure associated with the demand patterns they attract, the commitments they require, and the costs they generate. Strategy implementation often requires changing the product and service portfolio and managing the associated risks.

2.3.4 Problem management
Problem management is mostly about risk management. The purpose of the problem management practice is to reduce the likelihood and impact of incidents, by identifying the actual and potential causes of incidents and managing the workarounds and known errors.

A potential cause of incidents is a risk and reducing the likelihood and impact of this is a risk management activity. ITIL 4 Foundation notes that ‘problem management activities can be organized as a specific case of risk management: they aim to identify, assess, and control risks in any of the four dimensions of service management. It is useful to adopt risk management tools and techniques for problem management’.

ITIL treats problem management differently to other aspects of risk management. This is due the nature and frequency of problems, and the resources needed to manage them. However, it would be acceptable for an organization to treat all problems as risks and to manage these problems in exactly the same way as other risks.

2.3.5 Incident management
The actions taken when attempting to diagnose and resolve incidents can lead to risks. The actions taken when managing major incidents can involve significant risk to both the service provider and the service consumer. This means that everyone involved needs to use risk management practices to ensure that they understand what risks are involved, so that these can be managed appropriately.

2.3.6 Service continuity management
Service continuity management is a control that is used to manage a wide range of risks that might impact the availability or performance of services. An effective service continuity management practice can make a significant contribution to risk management.

2.3.7 Continual improvement
Continual improvement prioritizes and manages improvement opportunities. Risk management considers positive risks, which are often called opportunities, as well as negative risks.

Many organizations consider management of all positive risks to be a continual improvement activity, and only use risk management for negative risks. As a result, the risk register only includes negative risks, and the continual improvement register includes positive risks. This is a perfectly acceptable approach, so long as all risks are managed.

2.3.8 Service level management
Service level management is concerned with ensuring that service levels are achieved. This includes identifying and managing any risks that might impact service levels and reporting these risks to customers and other stakeholders who may need to be consulted or informed.

Good service level reporting includes the identification of risks that may impact the service in the future, and explanations of how these risks will be managed. Often, the risk management will require input from, or actions by, the customers and users.

2.4 Practice success factors
Practice Success Factor (PSF)
A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity; it includes components from all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The risk management practice includes the following PSFs:

establishing governance of risk management
nurturing a risk management culture and identifying risks
analysing and evaluating risks
treating, monitoring, and reviewing risks.
2.4.1 Establishing governance of risk management
All risk management activities require a clear understanding of the organization’s risk capacity and risk appetite. These cannot be defined by practitioners; they are critical aspects of organizational governance. This means that risk management is dependent on the overall governance of the organization.

If this governance is not provided, then practitioners need to respond and ensure that accountability for this is taken by the board of management (or equivalent). If risk management is performed without governance, then it will be difficult to make decisions based on the long-term needs of the organization.

Some risks pose an existential threat to the organization. These risks should be owned by the governing body of the organization. Ideally, the governance of risk management should be regularly discussed in board meetings. Moreover, risk capacity, risk appetite, and strategic risks should also be discussed, agreed, and regularly reviewed in board meetings.

2.4.2 Nurturing a risk management culture and identifying risks
After a risk has been identified, the organization can record it in a risk register and manage it. Yet identifying risks can be extremely difficult as there is no simple process or procedure for identifying risks and most organizations have a large number of unknown risks.

The methods that can help to identify risks are discussed in section 3.2.1, but the most important management activity to support this is nurturing a risk management culture. Everyone in the organization should take responsibility for identifying and reporting any risks that they discover. This requires a culture where people feel safe to identify mistakes made by themselves and others, without fear of reprisal. Therefore, managers and leaders need to nurture an open and honest culture.

Employees will anticipate potential problems when risk management is embedded within the culture of the organization. The employees can then consider how to mitigate the risk and whether they are working on strategic initiatives or routine operational tasks.

2.4.3 Analysing and evaluating risks
The analysis of risks involves understanding the likelihood and potential impact of each risk. The analysis can be qualitative or quantitative.

2.4.3.1 Qualitative risk analysis
Qualitative risk analysis uses a simple scale, such as high, medium or low to distinguish between different levels of likelihood and impact. Qualitative risk analysis will often utilize a table, which is used to derive an overall risk level from the levels of impact and likelihood, as shown in Figure 2.1.


Figure 2.1 Example matrix for qualitative risk analysis

The output of this risk analysis determines the level of risk which is documented in a risk register and used to decide the required risk treatment. In the example in figure 2.1, a risk that has a medium likelihood and a high impact would be rated as a high risk. This result is specific to the organization and cannot be compared with risk analysis from a different organization.

Some organizations use a five point scale, rather than the simple three point scale (high, medium or low) illustrated in Figure 2.1, but the approach is still the same.

2.4.3.2 Quantitative risk analysis
Quantitative risk analysis considers the risk impact on a financial basis, as well as on other numerical bases. The likelihood is considered a probability. This risk analysis supports calculations that can be used in a business case, to justify investments that may be needed to manage the risk.

Annual rate of occurrence (ARO)
The probability that a specific risk will occur in a single year.
Single loss expectancy (SLE)
The expected financial loss due to a risk, each time that a risk occurs.
Annualized loss expectancy (ALE)
The expected financial loss due to a risk, averaged over a one-year period. ALE is calculated by multiplying the single loss expectancy (SLE) by the annual rate of occurrence (ARO).
The annual rate of occurrence is calculated based on the expectations of how frequent the risk is likely to occur. For example, an event that is expected to occur once every fifty years has an ARO of 2%.

The SLE is calculated based on the average cost incurred if the risk happened. This is usually expressed in financial terms, but in some organizations, it may be expressed in other measurable ways, such as sales lost.

The ALE is calculated by multiplying the SLE by the ARO. The result can then be compared to the cost of controls, so that a decision can be made on how much to invest in managing the specific risk.

2.4.3.3 Combining qualitative and quantitative risk analysis
Quantitative risk analysis is considerably more time-consuming than qualitative risk analysis, so the two are often combined to optimize the time spent analysing data. This involves performing a qualitative risk analysis of every identified risk. Then, a quantitative risk analysis is performed for those risks that exceed a certain threshold for the level of risk and the cost of mitigation. For example, the organization’s risk management policy may state that low rated risks will be managed using controls if the cost of the controls is below £5,000. Quantitative risk analysis will be performed if the cost of the controls is higher than £5,000.

2.4.4 Treating, monitoring, and reviewing risks
Every risk must be treated in the same way. Even if a decision is made to accept a risk, this does not mean that no action will be taken. An accepted risk should be documented, communicated to relevant stakeholders, and reviewed regularly to ensure that changes to the probability, impact, or cost of controls are considered.

When a decision is made to manage a risk, suitable controls need to be designed and implemented. These controls must be maintained to ensure that they remain relevant, and that they are properly implemented to provide the agreed level of protection. For example, if the organization has a clear desk policy, then it is important to communicate this to all staff that may be in a position to leave papers on desks, with regular reinforcement and audits. Similarly, a control that requires all computers to run up-to-date antivirus software must have the technology in place to identify any computers that are not up-to-date.

Some aspects of defining controls will be described in section 3.2.1, but treating, monitoring, and reviewing risks requires the right balance across all four dimensions of service management. It is not just a process issue.

2.5 Key Metrics
The effectiveness and performance of ITIL practices should be assessed within the context of the value streams that each practice contributes to. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the risk management practice are mapped to its practice success factors. They can be used as KPIs in the context of value streams in order to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of this are given in Table 2.4.

Table 2.4 Examples of key metrics for the practice success factors
Practice success factors

Key metrics

Establishing governance of risk management

Time since risk appetite and risk capacity were last reviewed and updated.
Percentage of strategic risks with clearly documented likelihood, impact, owner, treatment plan, and next action date.
Nurturing a risk management culture and identifying risks

Percentage of employees who say they feel free to identify risks and mistakes in anonymous surveys
Number of risks identified by people who do not work in specific risk management roles.
Analysing risks

Percentage of risks on the risk register with clearly documented likelihood, impact, and owner.
Treating, monitoring, and reviewing risks

Percentage of risks on the risk register with clearly documented treatment plan and next action date
Percentage of risks on the risk register that have been reviewed in the last six months
Percentage of controls that have been subject to a control review and audit within the last six months.
The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the risk management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as the goals of the value streams to which the practice contributes.

3. 
Value Streams and processes
3.1 Value streams contribution
Like any other ITIL management practice, the risk management practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The risk management practice combines with other practices to provide high-quality services to consumers. The practice makes a significant contribution to all of the value chain activities.

The contribution of the risk management practice to the service value chain is shown in Figure 3.1.

3.2 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

Process

A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.


Figure 3.1 Heat map of the contribution of the risk management practice to value chain activities

Risk management activities form three processes:

governance of risk management
risk identification, analysis, and treatment
risk monitoring and review.
3.2.1 Governance of risk management
This process includes the activities listed in Table 3.1 and transforms the following inputs into outputs.

Table 3.1 Inputs, activities, and outputs of the governance of the risk management process
Key inputs

Activities

Key outputs

Environmental factors (PESTLE)
Competitive environment
Threat environment
Regulatory requirements
Organization strategy
Analyse the environment
Document risk capacity and risk appetite
Document risk management policy
Provide direction to management
Monitor the organization
Risk capacity
Risk appetite
Risk management policy
Budget for risk management
Direction provided to management
Figure 3.2 Shows a workflow process



Figure 3.2 Workflow of the governance of the risk management process

Many of the governance activities required for a successful risk management are not specific to the risk management practice. These activities are required by the governing body in order to govern the organization.

Table 3.2 Activities of the governance of the risk management process
Activity

Example

Analyse the environment

This activity is not specific to risk management. The governing body analyses:

The PESTLE factors that constrain and influence the organization (political, economic, social, technical, legal, and environmental)
Regulatory requirements
The competitive environment
The threat environment.
Based on these, and other factors, they set the overall organization strategy, which includes the strategy for risk management.

This activity is usually scheduled, typically once a year, but may also be triggered by any event which could impact the organization’s strategy.

Document risk capacity and risk appetite

Based on the analysis of the environment, the culture of the organization, and the organization’s strategy.

The governing body establishes and documents the risk capacity and risk appetite of the organization.

Document risk management policy

The risk management policy specifies the approach to be taken to identify, analyse, and manage risks. This may include the adoption of specific standards and guidelines, such as ISO 31000. Creation of this policy requires specialist knowledge of risk management, but the decisions and authorization remain with the governing body.

The governing body allocates a budget for risk management, which must be sufficient to support the requirements of the policy.

Provide direction to management

This activity is not specific to risk management (but the specific direction to be provided is about risk management).

The governing body shares the risk capacity, risk appetite and risk management policy as appropriate, and ensures that management throughout the organization are aware of their responsibilities in relation to risk management.

Monitor the organization

This activity is not specific to risk management, although there may be a specific risk management aspect to it.

The governing body reviews audit reports, and monitors the organization, to ensure that risk management is proceeding according to their intentions. If there are any significant deviations, this may trigger a requirement to analyse the environment and review risk capacity, appetite, and policy.

3.2.2 Risk identification, analysis, and treatment
This process includes the activities listed in Table 3.3, and transforms the inputs into outputs.

Table 3.3 Inputs, activities, and outputs of the risk identification, analysis, and treatment process
Key inputs

Activities

Key outputs

Risk management policy
Risk appetite
Budget for risk management
Existing risk register(s)
Service portfolio
Service models
Risks identified as part of other activities
Standards and frameworks
Threat assessment and vulnerability assessment services from third parties
Risk identification
Risk analysis and evaluation
Risk treatment

Updated risk register(s)
New and updated controls
Figure 3.3 shows a workflow diagram of the process.


Figure 3.3 Workflow of the risk identification, analysis, and treatment process

These activities may be performed by many people in the organization, with varying levels of formality. This is shown in Table 3.4.

Table 3.4 Activities of the risk identification, analysis, and treatment process
Activity

Description

Risk identification

Risk identification activities are focused on a specific scope of control. Risk identification for a project will consider project risks, risk identification for a service will consider risks to the service, and so on.

Risk identification may be performed on a regular schedule, or may be triggered by an event such as a security breach, a new service, or entering a relationship with a new partner.

There are many different techniques that can be used to identify risks, including:

Review of previous risk registers
Analysis of the service portfolio and service models
Brainstorming
Tabletop exercises to consider specific scenarios
Interviews with stakeholders, including customers, users, technical staff, and so on
Threat assessments and vulnerability assessments, which can be carried out by a third party if resources and skills are not available internally
Checklists based on standards and best practices
Risks that have been identified by other parts of the organization
Risks posted to a suggestion box or an anonymous email account
Information about risks that have been identified by vendors, partners, or other organizations
Output of technical tools, such as firewall logs or reports from intrusion detection systems
Service level reports, showing trends and potential failures to meet agreed quality of services
Each risk that is identified is assigned an owner, who is accountable for ensuring that the risk is understood, and appropriate action is taken.
Risks and risk owners are documented in a risk register
Risk analysis and evaluation

The likelihood and potential impact of each risk is analysed, using either qualitative or quantitative methods as specified by the risk management policy.
Based on this analysis, and the organization’s risk appetite, each risk is evaluated to decide what level of time and budget should be used to manage the risk.
The risk owner either does this analysis and evaluation themselves, or delegates it and reviews the findings.
The risk register is updated with the output of the risk analysis and evaluation.
Risk treatment

A risk treatment option is chosen for each risk.
If the risk is accepted, then this decision must be documented and communicated to appropriate stakeholders
Selection of controls for managing each risk may be based on the risk management policy, on standards and best practices, or may be designed specifically for the situation.
Risk treatment may require design, investment, development, testing, deployment, and other activities. These should all be managed to ensure that the risk treatment is fully implemented as agreed by the risk owner.
The risk register is updated to show the risk treatment, including dates of implementation where relevant.
3.2.3 Risk monitoring and review
This process includes the activities listed in Table 3.5, and transforms the following inputs into outputs.

Table 3.5 Inputs, activities, and outputs of the risk monitoring and review process

Key inputs

Activities

Key outputs

Risk management policy
Risk register(s)
Threat and vulnerability assessment services
Control assessments and evaluation
Risk audits and reviews
Updated risk register(s)
Audit reports
Requirements for new and updated controls
Figure 3.4 shows a workflow diagram of the risk monitoring and review process



Figure 3.4 Workflow of the risk monitoring and review process

Table 3.6 Activities of the risk monitoring and review process
Activity

Example

Control assessment and evaluation

Control assessment and evaluation ensures that controls have been fully and correctly implemented, and that they are still fit for purpose, and able to provide the level of risk management that is required.
This activity should be performed on a regular basis, which in a high-risk environment may be weekly or even daily. It may also be triggered by an event such as a security incident, a new or changed service, or entering a relationship with a new partner.
Control assessment analyses the extent to which one or more controls have been implemented. For example, by auditing computers to establish that they have the correct version of anti-virus software installed, or by inspecting offices to see that the clear desk policy is being adhered to.
Control evaluation analyses the continuing relevance of the control to determine whether it is still fit for purpose. For example, by determining that the risk the control is intended to modify still exists.
Control assessment and evaluation is often performed for a specific subset of controls. Some controls may need to be reviewed every day, but others may need to be reviewed much less frequently.
The assessment and evaluation may result in updates to risk registers, identification of a need for new or updated controls, or a need for a risk audit.
Risk audit

Audits ensure that risk management remains appropriate and relevant as the environment changes.
Audits are usually performed on a scheduled basis, but may be triggered by an event such as a security incident, or entering a relationship with a new partner.
Audits may be performed internally, or by third parties. The output of the audit may identify a need to implement new or updated controls, and will provide an input to the ‘monitor the organization’ activity of the ‘governance of risk management’ process.
4. 
Organizations and people
4.1 Roles, competencies, and responsibilities
The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended.

Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

Table 4.1 Competency codes and profiles
Competence code

Competency profile (activities and skills)

L

Leader Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes

A

Administrator Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements

C

Coordinator/communicator Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns

M

Methods and techniques expert Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement

T

Technical expert Providing technical (IT) expertise and conducting expertise- based assignments


Examples of roles involved in risk management are listed in Table 4.2 below.

Table 4.2 Examples of roles with responsibility for risk management activities
Activity

Responsible roles

Competency profile

Specific skills

Process: Governance of risk management

Analyse the environment

Risk management committee (on behalf of the board of directors)

MC

Visibility across PESTLE factors influencing the organization

Document risk capacity and risk appetite

Risk management committee

MC

Ability to define concise and holistic and objective systems of risk indicators

Document risk management policy

Risk management committee

MCL

Awareness of organization specific documentation requirements.

Provide direction to management

Risk management committee,

Budgeting committee

LC

Enabling communication channels; ensuring ongoing engagement of managers to ensure clarity, and ongoing realisation of risk management policies.

Monitor the organization

Risk management committee

CAM

Visibility over organization performance metrics

Process: Risk identification, analysis, and treatment

Risk identification

Subject matter expert,

Service or Product owner

MTC

Professional competencies and visibility over PESTLE factors that influence the object in scope of risk assessment

Risk analysis and evaluation

Subject matter expert (the risk owner)

TML

Ability to systematically apply qualitative and quantitative risk analysis tools and draw conclusions

Risk treatment

Risk owner, cyber security project managers

CAM

Project management practices

Process: Risk monitoring and review

Control assessments and evaluation

Risk owners, Risk management committee delegates

MTCA

Awareness of existing controls and control maintenance requirements as set out in the risk management policies

Risk audits and reviews

Audit committee or external auditors (as mandated and on behalf of the board of directors)

CAMT

Audit management techniques

Command of common audit practices

Assured auditor integrity, objectivity and independence

4.2 Organizational structures and teams
The risk management practice is one of the practices, that underpins everything that the service provider does to enable value co-creation. Therefore, the practice is everyone’s responsibility, within their scope of control.

In a commercial enterprise, the board of directors (or another top-level governing body) is ultimately accountable before the organization’s stakeholders, for implementing an adequate and satisfactory risk management framework. The ongoing development of the risk management framework is usually delegated to one or more of the risk management committees and is under the board’s oversight.

The risk management framework established by the risk management committee defines the risk analysis method, scope, and objects. Role descriptions, such as identification and monitoring, can be contained within the framework even for operational line staff, depending on the organizational design risk management activities. The key goal of the governing body is to ensure that all tiers of management in the service provider organization, implement the risk management framework within their scopes of control.

5. 
Information and technology
5.1 Information exchange, inputs/outputs
The effectiveness of the risk management practice is based on the quality of the information used. This information includes, but is not limited to, information about:

the risks that the risk owners own
raising a new risk record
an easily identifiable and objective risk importance
forecasted and appropriately assigned tasks.
This information may take various forms. The key inputs and outputs of the practice are listed in section 3.

5.2 Automation and tooling
In most cases, the risk management practice can significantly benefit from automation (see the value streams and processes section of this guide for details on when this is applicable). Where this is possible and effective, it may involve the solutions outlined in Table 5.1.

Table 5.1 Automation solutions for risk management activities
Process activity

Means of automation

Key functionality

Impact on the effectiveness of the practice

Process: Governance of risk management

Analyse the environment

Service portfolios, service catalogue, service models

Knowledge management tools and document repositories

Provide information about the environment in which services are delivered and consumed

High

Document risk capacity and risk appetite

Knowledge management tools and document repositories

.	
Medium

Document risk management policy

Knowledge management tools and document repositories

Risk management framework, including the policy, guidelines, existing and prospective controls, as well as the risk register needs to be easily accessible by the service provider staff; external stakeholders, such as customer representatives and regulators should also have adequate visibility over the framework

Medium

Provide direction to management	Email and other communication channels, Knowledge Management tools and document repositories	
Risk management framework, including the policy, guidelines, existing and prospective controls, as well as the risk register needs to be easily accessible by the service provider staff; external stakeholders, such as customer representatives and regulators should also have adequate visibility over the framework

High
Monitor the organization	Email and other communication channels 	
Risk management framework, including the policy, guidelines, existing and prospective controls, as well as the risk register needs to be easily accessible by the service provider staff; external stakeholders, such as customer representatives and regulators should also have adequate visibility over the framework

High
Process: Risk identification, analysis, and treatment

Risk identification	
Infrastructure and application monitoring and reporting tools, built- in user behaviour monitoring tools, dashboarding and reporting tools, advanced analytics tools, survey and satisfaction monitoring tools, user portals and apps, social media

Service management tools provide operational and analytical signals on the risks changing their parameters. Risk owners should apply those in the course of their risk management responsibilities

High
Risk analysis and evaluation 	
Knowledge management tools and document repositories, service models, CMDB, analytical tools

Depending on the nature of the identified or updated risk, analysis can be underpinned by a variety of management systems data. Risk owner ensures that analysis and evaluation decisions are informed

High
Risk treatment	Change initiation and control tools	
Risk countermeasures, whether one-off or ongoing, technical, organizational or otherwise, should be implemented in a controlled manner, ensured by existing change management and project management tools

Medium
Process: Risk monitoring and review

Control assessments and evaluation

Knowledge management tools and document repositories

The assessors should have access to the risk management framework including the risk register, although risk management culture within the organization must be observed through non- automated interactions.

Medium

Risk audits and reviews	Knowledge management tools and document repositories	
The auditors should have access to the risk management framework including the risk register, although risk management culture within the organization must be observed through non-automated interactions.

Medium
6. 
Partners and suppliers
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the ITIL practices for supplier management and service level management.

Partners and suppliers to the service provider can generate and mitigate new risks to the service provision and change profiles of the existing ones. The service provider needs to be aware of the latter, when onboarding new partners and suppliers.

It is also crucial that the risk management frameworks for the parties are mutually aligned, and appropriate communication channels are established between respective risk owners. For example, a failure within a supplier managed infrastructure segment needs to trigger the response for the service provider risk mitigation. Risk identification and proper signalling must be built into the service model, with a supplier, and regularly tested.

Although the actual risk mitigation activities are likely to be covered by the other practices’ processes, it is the risk management practice that covers the risk management framework alignment among the parties. The practice also ensures that the parties invest the appropriate amount of effort into risk identification and analysis.

Where organizations aim to ensure fast and effective risk management practice, they usually try to agree to close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision-making. All parties in such relationships should aim for mutual transparency and visibility of the changes that may affect the other parties (see the supplier management practice guide for more information).

7. 
Important reminder
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of things that organizations might think about, not a list of answers. When using the content of the ITIL Practice guides, organizations should always follow the ITIL guiding principles:

focus on value
start where you are
progress iteratively with feedback
collaborate and promote visibility
think and work holistically
keep it simple and practical
optimize and automate.
More information on the guiding principles and their application can be found in section 4.3 of the ITIL® Foundation: ITIL 4 Edition publication.

8. 
Acknowledgements
AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following:

8.1 Authors
Stuart Rance, Konstantin Naryzhny

8.2 Reviewers
Roman Jouravlev

