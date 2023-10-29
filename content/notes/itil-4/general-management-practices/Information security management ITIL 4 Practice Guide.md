---
title: "Information security management"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# 1. Source
Axelos International (https://www.axelos.com)

# 2. Overview
**Key Message**: The purpose of the information security management practice is to protect the information needed by the organization to conduct its business. This includes understanding and managing risks to the confidentiality, integrity, and availability of information, as well as other aspects of information security such as authentication and non-repudiation.

Information security is becoming an increasingly important but difficult task. The information security management practice is increasingly important in the context of digital transformation. This is due to the growth of digital services across industries, where information security breaches might have a major effect on an organization’s business. The wider use of cloud solutions and the wider integration with partners’ and service consumers’ digital services creates new critical dependencies, with limited ability to control how information is collected, stored, shared, and used. Partners and service consumers are in the same situation, and usually invest in data protection and information security solutions. However, a lack of integration and consistency between organizations creates new vulnerabilities, which need to be understood and addressed. The information security management practice in conjunction with other practices (including: availability management, capacity and performance management, information security management, risk management, service design, relationship management, architecture management, supplier management and other practices) ensures that an organization’s products and services meet the required level of information security for all involved parties.

The information security management practice is considered by many organizations to be a specialized branch of wider security management. In a service economy, every organization’s business is service-driven and digitally-enabled. This may lead to a closer integration of the disciplines, as security management focuses more on the security of digital services and information. This integration is both possible and useful where digital transformation has led to the removal of the borders between ‘IT management’ and ‘business management’ (see *ITIL*<sup><em>®</em></sup>*4: High-velocity IT* for more on this topic).

## 2.2 Terms and concepts
### 2.2.1 Security characteristics
The information security management practice helps to ensure the confidentiality, integrity, and availability of the information needed to conduct business, with several activities and controls needed to preserve these characteristics. Additionally, the information security management practice is often concerned with authentication and non-repudiation.

**Confidentiality** — The prevention of information being disclosed or made available to unauthorized entities.

Confidentiality is the first thing that many people think of when they consider information security. People and organizations want to ensure that their secrets remain secret, and that their personal or business information is not misused.

**Availability** — A characteristic of information that ensures it is able to be used when needed.

If the information is not available when and where it is needed, then the organization is unable to conduct its business.

The availability management practice considers many aspects of service availability. However, the information security management practice is mostly concerned with the availability of information.

**Integrity** — An assurance that information is accurate and can only be modified by authorized personnel and activities.

Incorrect information may be worse than not having any information at all. For example, if a bank incorrectly believes that a customer has a large amount of money in their account and allows them to withdraw this, the bank might suffer from a significant loss.

**Authentication** — Verification that a characteristic or attribute which appears or is claimed to be true, is in fact true.

Authentication is used to establish the identity of people and things. For example:
* Usernames and passwords are often used to authenticate people, although more rigorous authentication using biometrics and security tokens is often preferred.
* Certificates and encryptions may be used by web sites to provide authentication.

**Non-repudiation** — Providing undeniable proof that an alleged event happened, or an alleged action was performed, and that this event or action was performed by a particular entity.

Non-repudiation has been used in business transactions since before the existence of IT systems and services. Traditionally, a signature would be used, and if a higher level of proof was needed then this signature might be notarized. Information security relies on non-repudiation so that transactions can occur. This is essential to preserve the integrity of information.

#### 2.2.2 Assets, threats, threat actors, and vulnerabilities
**Asset** — An <strong>asset</strong> is anything that has value to an organization.

Assets may include hardware, software, networking, information, people, business processes, services, organizations, buildings, or anything else that is valuable to an organization. The information security management practice helps to protect assets so that the organization can conduct its business.

</strong></p></td></tr><tr><td><p>A threat is any potential event that could have a negative impact on an asset.</p></td></tr><tr><td><p>A threat actor is any person or organization that poses a threat.</p></td></tr><tr><td><p>A vulnerability is any weakness in an asset or control that could be exploited by a threat.</p></td></tr><tr><td><p>These terms are related in the following way: Threat actors exploit vulnerabilities to have an impact on assets.</p></td></tr></tbody></table>

#### 2.2.2.1 Threat and vulnerability assessments
A **threat assessment** is used to identify potential threats, so that the organization can take appropriate action. This assessment may involve reviewing historical information about previous attacks on the organization, recent attacks against other similar organizations, or simply predicting potential threats that could emerge in the future. The output of a threat assessment is a list of threats that the organization needs to consider in its planning. Threat assessments can be performed on a regular basis and as a check when planning changes.

A **vulnerability assessment** is used to identify vulnerabilities in a specific environment, service, or configuration item. This typically involves compiling a list of potential vulnerabilities and using tools to test each component in the environment, to see if that vulnerability exists. Vulnerability assessments can be performed on a regular basis, and as a check during the deployment of infrastructure or applications. There are many tools available to support vulnerability assessments and many suppliers can perform vulnerability assessments as a service.

### 2.2.3 Risk management terms
The information security management practice utilizes several risk management terms and concepts. These terms are also described in the risk management practice.

The risk management terms are defined in Table 2.1.

### Table 2.1 Risk management terms
<table><tbody><tr><td><p><strong>Risk management term</strong></p></td><td><p><strong>Definition</strong></p></td></tr><tr><td><p>Risk</p></td><td><p>A possible event that could cause harm or loss, or make it more difficult to achieve objectives. It can also be defined as an uncertainty of the outcome, and can be used in the context of measuring the probability of positive outcomes as well as negative outcomes.</p></td></tr><tr><td><p>Control</p></td><td><p>The means of managing a risk, ensuring that a business objective is achieved, or that a process is followed.</p></td></tr><tr><td><p>Risk treatment</p></td><td><p>Actions taken to treat a risk. Risk treatment options are:</p><p>Risk avoidance: preventing the risk by not performing the risky activity</p><p>Risk modification: implementing controls to reduce the likelihood or impact of the risk</p><p>Risk sharing: reducing the impact by passing some of the risk to a third party</p><p>Risk retention: intentionally deciding to accept the risk because it is below an acceptable threshold (and within the risk appetite of the organization).</p></td></tr><tr><td><p>Residual risk</p></td><td><p>The risk that remains after the application of controls</p></td></tr></tbody></table>

## 2.3 Scope
The purpose of the information security management practice, as described in section 2.1, is to “protect the information needed by the organization to conduct its business”. This information may be stored and processed on information systems, but equally it may be recorded on paper, or communicated in speech. This practice is concerned with the confidentiality, integrity, and availability of this information, regardless of where and how it is stored and processed. Although the focus is on information, this practice is concerned with all four dimensions of service management.

Each organization must define the scope of its information security management practice, which will typically include:
* IT systems and services
* IT infrastructure and platforms
* software and applications
* network infrastructure, including: IT networks, voice, wireless, and so on.
* client devices, such as phones, laptops, and tablets, including: all hardware, firmware, software, and applications
* IoT devices, which typically have network connectivity and processing capabilities and might also have sensors and actuators which interact with the physical world
* physical infrastructure, such as: buildings, data centres, or manufacturing facilities
* business processes
* people, including understanding the risks they pose and how these risks are managed
* partners and suppliers who play a part in the provision, management, or support of services
* data and information, whether it is stored, processed, or communicated, and the format it is in.

Within this scope, the information security management practice should ensure that:
* assets that need to be protected are identified
* risks that could impact these assets are identified and analyzed
* appropriate measures are taken to manage these risks
* monitoring and continual improvement are in place to ensure that information security risks continue to be appropriately managed.

Some important aspects of the information security management practice are described in other practice guides. These are listed in Table 2.2, along with references to the practices in which they can be found.

### Table 2.2 Activities related to the information security management practice described in other practice guides
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice</strong></p></td></tr><tr><td><p>Strategic communication with customers, sponsors, regulators, and governance body</p></td><td><p>Relationship management</p><p>Organizational change management</p></td></tr><tr><td><p>Operational communication with users</p></td><td><p>Service desk</p></td></tr><tr><td><p>Establishing and maintaining contracts with suppliers</p></td><td><p>Supplier management</p></td></tr><tr><td><p>Designing and implementing products and services</p></td><td><p>Service design</p><p>Software development and management</p><p>Infrastructure and platform management</p><p>Service validation and testing</p><p>Deployment management</p><p>Release management</p></td></tr><tr><td><p>Monitoring, to detect potential security incidents</p></td><td><p>Monitoring and event management</p></td></tr></tbody></table>

## 2.4 Practice success factors
Practice success factor

A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The information security management practice includes the following PSFs:
* developing and managing information security policies and plans
* mitigating information security risks
* exercising and testing information security management plans
* embedding information security into all aspects of the service value system.

### 2.4.1 Developing and managing information security policies and plans
Organizations develop and maintain information security policies and plans to sustain the required level of information security. These plans apply to everyone within the organization and might involve service consumers, suppliers, and partners. Therefore, an awareness and understanding of the applicable policies and plans should be sustained across the organization.

An organization should understand the internal and external requirements of information security, to develop and manage its policies and plans. An assessment of how these requirements affect an organization’s resources, products, services, and practices can then be performed, and the correct information security controls implemented. This activity will be continuously performed; due to the changing nature of both the information security requirements and the context of the organization. Changes in requirements and the sufficiency of policies and plans should be continually reviewed, on an interval-based and event-based basis. Improvements should be initiated based on these reviews.

Information security management policies and plans may address the following aspects:
* an overall information security management practice approach
* use and misuse of IT assets
* access control
* password control
* communications and social media
* malware protection
* information classification
* remote access
* suppliers’ access to an organization’s information and resources
* intellectual property
* record management and retention
* personal data protection
* other relevant aspects of information security.

To ensure the effective management of information security, organizations might establish a formal information security management system, which follows relevant standards such as ISO/IEC 27001<sup>1</sup>.

### 2.4.2 Mitigating information security risks
The information security management practice includes the identification, analysis, and management of information security risks.

The identification of information security risks includes identifying all assets that are within the scope of the service value system, and then identifying risks to those assets. This can be supported by threat and vulnerability assessments, architecture and design reviews, and many other techniques.

The analysis of information security risks includes ascertaining the likelihood of each information security risk, and the potential impact of that risk. The data provided can evaluate the cost, benefit, and ROI of potential controls.

The management of information security risks includes defining and managing the controls, which manage the wide range of risks that might impact information security. This is performed in conjunction with risk management and other risk-focused practices, such as capacity and performance management, availability management, and service continuity management practices. The agreed information security controls are often implemented as part of other practices, such as service design, software development and management, infrastructure and platform management, architecture management, service request management, continual improvement, workforce and talent management depending on the nature of the control.

The established policies and plans should drive behaviour and implement controls to maintain a balance between:
* Prevention – ensuring that security incidents don’t occur
* Detection – rapidly and reliably detecting incidents that can’t be prevented
* Correction – recovering from incidents after they are detected.

More preventative countermeasures should be adopted if risk analysis indicates an earlier and greater impact on the service. If the initial impact is smaller and takes longer to develop, a more economically effective approach would be to invest in detection and correction countermeasures.

Controls may involve any of the four dimensions of service management. For example:
* organization and people controls such as training, policies, or separation of duties
* value stream and process controls such as backup, patch management, or peer review
* information and technology controls such as firewalls, encryption, or anti-virus software
* partner and supplier controls such as contractual requirements, process audits, or third-party certification.

When choosing an information security countermeasure, the effectiveness and efficiency of each option should be assessed. The effectiveness and efficiency of information security countermeasures must be continually controlled and validated.

### 2.4.3 Exercising and testing information security management plan
Experience has shown that untested plans do not work as intended, if it works at all. Therefore, testing is a critical part of the overall information security management practice. It is the only way to ensure that the plans and controls work in practice.

The information security plans and controls should be tested to improve its readiness and ability. Regular testing will result in the discovery of flaws and inefficiencies. The findings could then be used to update the information security plans and controls.

Exercises should be conducted at planned intervals and when significant changes occur in the policies, plans, and controls. The greater the impact of an information security incident, the more often the exercises should occur.

### 2.4.4 Embedding information security into all aspects of the service value system
The information security management practice must be embedded into every part of the service value system.

#### 2.4.4.1 Guiding principles
When using the ITIL guiding principles, it is important to consider this practice. For example:
* focus on value: value can be realized through an improvement in the quality of information
* collaborate and promote visibility: also high-level consider information confidentiality.

#### 2.4.4.2 Governance
Governance is essential for an effective information security management practice. Even the smallest organization needs to establish the governance of this practice to:
* establish the organization’s attitude to this practice
* define high-level requirements for this practice
* communicate high-level requirements to management
* monitor the organization to ensure that these requirements are being met.

2.4.4.3 Service value chain and value streams

Every value stream should include appropriate information security management practice activities. Usually, these will be embedded within the steps of the value stream and at multiple points in the service value chain.

For example, consider a value stream that creates a new or significantly changed service:
* acknowledge and document the service requirements (engage)
    * this step will include documenting service requirements for information security
* decide whether to invest in the new service (plan)
    * in this step, consider the information security issues that could pose a risk to the organization
* design the new service to meet customer requirements (design and transition)
    * this step will include designing and architecting to meet security requirements
* build, configure, or buy service components (obtain/build)
    * each component will need to be built, configured, or specified to meet security requirements
* deploy service components in preparation for launch (design and transition)
    * deployment should be secure, to ensure components haven’t been tampered with
* release new service to customers and users (deliver and support).
    * users and IT staff may require training, including security training, as part of the release.

#### 2.4.4.4 Practices
Every practice needs to include aspects of information security management. This could relate to any of the four dimensions of service management.

Processes defined by a practice might need to include this practice’s activities. For example, the deployment process might need to include checks to ensure that the software components are untampered.

Roles defined by the practices might need to include skills and competences from this practice. For example, a software developer might need the ability to design software that meets defined security standards.

Information and technology used by a practice must meet security requirements and often require embedded security controls. For example, a tool used for information exchange in the incident management practice might need to be confidential, so staff can see their organization’s incidents but not those of other organizations.

Partners and suppliers that support a practice must meet the organization’s information security requirements. For example, a partner that provides service continuity arrangements might need to provide assurance that their staff do not make use of data that was provided to them as part of a continuity test.

#### 2.4.4.5 Continual improvement
The information security management practice, like every other practice, requires continual improvement. In a world of increasing threats and increasing dependency on IT services, it is essential to constantly monitor and improve information security.

All improvement activities, even those that have no specific information security management practice content, should be assessed for their potential impact on information security. This assessment should be a routine part of any improvement activity.

## 2.5 Key metrics
The effectiveness and performance of ITIL practices should be assessed within the context of the value streams that each practice contributes to. As with the performance of any tool, the practice performance can only be assessed within the context of its application. However, tools can differ greatly in quality; and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance metrics (KPIs), and other techniques that can assist with this can be found in the measurement and reporting practice guide.

Key metrics for the information security management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of this are given in Table 2.3.

### Table 2.3 Example of key metrics for the practice success factors
<table><tbody><tr><td><p><strong>Practice success factor</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Developing and managing information security policies and plans</p></td><td><p>Percentage of products and services with clearly documented information security requirements</p><p>Percentage of products and services with documented information security plans</p><p>Updating information security plans in a timely manner</p></td></tr><tr><td><p>Mitigating information security risks</p></td><td><p>Number and percentage of information security risks for which analysis and evaluation have been performed</p><p>Number and percentage of information security risks where the residual risk has been reduced to an acceptable level by implementing controls</p></td></tr><tr><td><p>Exercising and testing information security management plans</p></td><td><p>Number and percentage of information security management plans that have been tested in the previous 12 months</p><p>Number of improvement actions identified as a result of testing information security management plans</p></td></tr><tr><td><p>Embedding information security in all aspects of the service value system</p></td><td><p>The governing body has discussed information security management at least once in the previous three months</p><p>Number and percentage of value streams that include specific steps and activities for information security</p><p>Number and percentage of practices that include specific steps and activities in its process flows and role definitions for information security</p><p>Number and percentage of improvement activities that include a security assessment</p></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the information security management practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as the goals of the value streams to which the practice contributes.

# 3. Value Streams and processes
## 3.1 Value streams contribution
Like any other ITIL management practice, the information security management practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The information security management practice combines with other practices to provide high-quality services to consumers. The information security management practice contributes to all activities of the service value chain.

The contribution of the information security management practice to the service value chain is shown in Figure 3.1.

![Image of Figure 3.1 Heat map of the contribution of the Information Security Management practice to Value Chain activities](Information%20security%20management%20ITIL%204%20Practice%20Guide/Picture1.png "Figure 3.1 Heat map of the contribution of the information security management practice to value chain activities**")

## 3.2 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

**Process** — <span>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</span>

Many information security management practice activities are embedded into processes from other practices. For example:
* designing security into new and changed IT services is part of the service design practice
* integrating security controls into applications is part of the software development and management practice
* ensuring that people are entitled to use a service before granting them access is part of the service request management practice.

The information security management practice forms two processes:
* security incident management
* audit and review.

### 3.2.1 Security incident management
There are many different types of security incidents. This ranges from a single client device that is impacted by a virus, to an attack that causes critical damage to a national infrastructure, or a major breach of highly sensitive information.

Minor security incidents are typically managed in the same way as any other incident, following the incident handling and resolution process described in the ITIL incident management practice guide. More significant security incidents might require specialist management, which can be based on the process described here.

Each organization should define a criteria to determine whether an incident requires specialist security incident management or can be managed using the normal incident handling and resolution process.

This process includes the following activities listed in Table 3.1 and transforms the following inputs into outputs.

### Table 3.1 Inputs, activities, and outputs of the security incident management process
<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><p>Information security policy</p><p>Service and asset information</p><p>Monitoring and event tools</p><p>Security incident and event management (SIEM) tools</p><p>Escalations from service desk</p><p>Known good sources of data and applications</p></td><td><p>Preparation</p><p>Detection and reporting</p><p>Triage and analysis</p><p>Containment and recovery</p><p>Post-incident activity</p></td><td><p>Incident response plans</p><p>Supplier contracts</p><p>Incident notification to regulators, governance bodies, or other relevant parties</p><p>Restored information and services</p><p>Incident reports</p><p>Improvement suggestions<br></p></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process

![Image of Figure 3.2 shows Workflow of the Security Incident Management process](Information%20security%20management%20ITIL%204%20Practice%20Guide/Picture2.png "Figure 3.2 Workflow of the security incident management process**")

These activities might be performed with varying levels of formality by many people within the organization.

Table 3.2 provides examples of the process activities.

### Table 3.2 Activities of the security incident management process
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Example</strong></p></td></tr><tr><td><p>Preparation</p></td><td><p>Before a security incident occurs, the organization must perform actions to prepare for potential future security incidents. This includes:</p><ul><li>defining and communicating the policies and procedures for security incident management</li><li><span>identifying critical services and assets for which specific response plans may be needed</span></li><li><span>agreeing communication that will occur during a security incident, including communications with: governing bodies, regulators, law enforcement, press, customers, internal staff, users, suppliers, and any other affected stakeholders</span></li><li><span>defining how security incidents and breaches will be reported</span></li><li><span>identifying threats and vulnerabilities that need to be managed</span></li><li><p>engaging partners and suppliers to provide products and services that may be needed to support specific scenarios</p></li><li><span>testing incident response plans.</span></li></ul></td></tr><tr><td><p>Detection and escalation</p></td><td><ul><li>Information security incidents might be: detected by monitoring tools, supported by correlation tools, and supported by security incident and event management (SIEM) tools. Incidents may also be detected by people; these may be reported to the service desk, or to a security incident response team, depending on who has detected the incident and the nature of the incident.</li></ul><ul><li>The incident is escalated to the appropriate person or team, depending on the specific incident response plan. This may involve assembling a computer security incident response team (CSIRT).</li></ul><ul><li>If required, an initial notification is sent to the appropriate regulatory or governance authorities.</li></ul></td></tr><tr><td><p>Triage and analysis</p></td><td><ul><li>Evidence might need to be preserved for possible use in future court proceedings. To prevent contamination, forensic data must be collected before any analysis is performed.</li></ul><ul><li>The nature and severity of the security incident is ascertained by examining systems, endpoints, applications, log files, and so on.</li></ul><ul><li>If required then further notification may be sent to regulatory or governance authorities, when the nature and severity of the incident are understood.</li></ul></td></tr><tr><td><p>Containment and recovery</p></td><td><ul><li>The impacted systems and services are isolated from the internet and/or from the rest of the organization. This enables further analysis to occur, which simultaneously limits the risk of further damage.</li></ul><ul><li>If possible, then services might be restored using alternative systems.</li></ul><ul><li>After analysis is complete, the impacted systems are shutdown, storage is wiped, and the systems rebuilt from well-known and reliable sources.</li></ul><ul><li>Business processes are considered to be recovered when this can be performed without threat of another incident, or further damage from the original incident.</li></ul></td></tr><tr><td><p>Post-incident activity</p></td><td><p>Systems and services are monitored to ensure that the threat has been removed. Lessons learned analysis is performed to identify improvement opportunities. An incident report is created and shared as appropriate.</p></td></tr></tbody></table>

#### 3.2.2 Audit and review
Audit and reviews are regularly performed and follow a schedule. It might also be triggered by a major incident, or by the findings from a threat assessment or vulnerability assessment.

This process includes the activities listed in Table 3.3, and transforms the following inputs into outputs.

### Table 3.3 Inputs, activities, and outputs of the audit and review process
<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Business process information</li></ul><ul><li>Threat assessment information</li></ul><ul><li>Service and asset information</li></ul><ul><li>External standard(s)</li></ul><ul><li>Current controls</li></ul><ul><li>Vulnerability assessment information</li></ul></td><td><ul><li>Identify changes to business, technology, or threat environment</li></ul><ul><li>Identify missing controls</li></ul><ul><li>Assess control effectiveness</li></ul><ul><li>Create audit report</li></ul></td><td><ul><li>Improvement suggestions</li></ul><ul><li>Audit report</li></ul></td></tr></tbody></table>

Figure 3.3 Workflow of the audit and review process

![Image of Figure 3.3 shows Workflow of the Audit and Review process](Information%20security%20management%20ITIL%204%20Practice%20Guide/Picture3.png "Figure 3.3 shows a workflow diagram of the process.**")

These activities might be performed by internal or external auditors. Many organizations perform internal audits and implement improvements. External auditors can then perform a more formal audit.

Table 3.4 provides examples of the process activities.

### Table 3.4 Activities of the audit and review process
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Example</strong></p></td></tr><tr><td><p>Identify changes to business, technology, or threat environment</p></td><td><ul><li>Business processes are assessed to identify changes that could impact information security requirements.</li></ul><ul><li>Technology is assessed to identify new or changed technology, as well as technology that has become obsolete, and changes in vulnerabilities related to technology. This assessment considers all technology used by the organization, not just information technology (IT).</li></ul><ul><li>Changes to the threat environment are identified by a threat assessment.</li></ul></td></tr><tr><td><p>Identify missing controls</p></td><td><ul><li>The business, technology, and threat environments are analyzed, and recommended controls are identified. Most organizations use a standard such as ISO/IEC 27002 or NIST 800-53 as a beginning for a list of suggested controls that should be in place.</li></ul><li>The output of a vulnerability assessment might also identify missing controls</li><li><span>The list of recommended controls is compared to the existing controls and improvements are recommended.</span></li></td></tr><tr><td><p>Assess control effectiveness</p></td><td><p>Each existing control is assessed to identify potential vulnerabilities in how it has been implemented. These vulnerabilities could relate to the scope of the control, such as whether it has been deployed everywhere it should be. It could also relate to the configuration of the control, such as whether it provides the appropriate level of protection.</p><p>The method used to assess effectiveness depends on the type of control. For example:</p><ul><li>Evaluate technical controls using a vulnerability assessment.</li><li>Evaluate policy and process controls by reviewing records and interviewing staff.</li><li>Review access rights by comparing directory information with records of granted access requests.</li><li>analyze the value of training by testing staff knowledge.</li><li>Ensure third parties and suppliers have undergone an appropriate evaluation by a formal assessment body.</li><li>Identify ineffective controls by assessing the output of a vulnerability assessment.</li></ul><p>New and improved controls are recommended based on the findings from this effectiveness assessment.</p></td></tr><tr><td><p>Create audit report</p></td><td><p>An audit report is created based on the findings from the earlier stages. This report includes high-level information that can be provided to the governing body of the organization, as well as detailed recommendations for new and improved controls.</p></td></tr></tbody></table>

# 4. Organizations and people
## 4.1 Roles, competencies, and responsibilities
The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

### Table 4.1 Competency codes and profiles
<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p>L</p></td><td><p><strong>Leader </strong>Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p>A</p></td><td><p><strong>Administrator</strong> Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p>C</p></td><td><p><strong>Coordinator/communicator</strong> Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p>M</p></td><td><p><strong>Methods and techniques expert</strong> Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p>T</p></td><td><p><strong>Technical expert</strong> Providing technical (IT) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

### 4.1.1 Chief information security officer role
Many organizations have a board member who is responsible for the information security management practice. This role is usually called a chief information security officer (CISO).

The CISO is typically responsible for:
* establishing the overall information security strategy for the organization, based on an understanding of the organizations business strategy, and the information security risks that might impact this
* ensuring that the organization takes a balanced approach to information security, which provides sufficient protection without having an adverse impact on the ability to conduct business
* strategic communication about information security to the board, and to other stakeholders such as regulators, law enforcement, press, customers, suppliers, and partners
* developing the information security policies and procedures
* overseeing the staff responsible for all other aspects of information security, including:
    * developing, testing, and improving processes, especially for security incident management
    * selecting, testing, and deploying security products such as firewalls or anti-virus software
    * defining standards and guidelines for procuring, developing, testing, deploying and the ongoing management of infrastructure and applications that have security implications, such as servers, operating systems, SaaS products, in-house applications, middleware, and client devices
    * operational activities such as security event monitoring, and routine management of security products.

### 4.1.2 Other roles involved in information security management
Examples of other roles that can be involved in the information security management practice are listed in Table 4.2 below, together with the associated competency profiles and specific skills.

### Table 4.2 Examples of roles with responsibility for information security management activities
| Process                              | Activity                                                        | Responsible Roles                                                                                                     | Competency Profile | Specific Skills                                                                                                                                                                                                                      |
| ------------------------------------ | --------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------- | ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Security incident management process | Preparation                                                     | CISO <br /> Information security manager <br /> Security analyst <br /> CSIRT team member                             | LMCT               | Organizational knowledge <br /> Policy and process development                                                                                                                                                                       |
| Security incident management process | Detection and reporting                                         | Security analyst <br /> Technical analyst <br /> Service desk agent                                                   | CAT                | Recognizing security incidents and appropriately categorizing it <br /> Assembling a team and communicating clearly                                                                                                                  |
| Security incident management process | Triage and analysis                                             | CISO <br /> Information security manager <br /> Forensics specialist <br /> Security analyst <br /> Technical analyst | TMA                | Business prioritization <br /> Forensic data preservation <br /> Technical understanding of services and their components <br /> Analysis of complex systems and information sources                                                 |
| Security incident management process | Containment and recovery                                        | Information security manager <br /> Security analyst <br /> Technical analyst                                         | TCM                | Technical understanding of services and their components <br /> Evaluation and selection of alternative courses of action in complex environments <br /> Communication and coordination with multiple stakeholders                   |
| Security incident management process | Post-incident activity                                          | CISO <br /> Information security manager <br /> Security analyst                                                      | CTL                | Communication and coordination with multiple stakeholders <br /> Technical understanding of services and their components <br /> Prioritization of improvement opportunities                                                         |
| Audit and review process             | Identify changes to business, technology, or threat environment | CISO <br /> Information security manager                                                                              | TMC                | Understanding of business processes and priorities <br /> Understanding of current and emerging technologies <br /> Understanding of current and emerging threats                                                                    |
| Audit and review process             | Identify missing controls                                       | Information security manager <br /> Information Security auditor <br /> Security analyst                              | TM                 | Understanding of applicable security standards, including detailed understanding of security controls <br /> Technical understanding of services and their components <br /> Analytical skills                                       |
| Audit and review process             | Assess control effectiveness                                    | Information security manager <br /> Information Security auditor <br /> Security analyst                              | TMC                | Understanding of applicable security standards, including detailed understanding of security controls <br /> Technical understanding of services and their components <br /> Communication and audit skills <br /> Analytical skills |
| Audit and review process             | Create audit report                                             | Information security manager <br /> Information Security auditor <br /> Security analyst                              | TCA                | Evaluating and prioritizing improvement opportunities <br /> Communicating with a wide range of stakeholders, including senior management                                                                                            |

### 4.1.3 Security competence for all roles
Everyone within an organization has some responsibility for the information security management practice. Every role should include some security management requirements. Those who are aware of their information security management practice capabilities can contribute to:
* **Preventing** information security incidents and breaches by following all required policies, implementing required controls, and noticing and reporting vulnerabilities
* **Detecting** information security incidents and breaches by noticing and reporting the unusual behaviour of technology, people, or suppliers
* **Correcting** information security incidents and breaches by following the required processes and procedures when incidents occur.

People can also contribute to each of these in a negative way, if they don’t have the appropriate skills, competence, and motivation. There are many things that can be done to help ensure that everyone in the organization contributes to information security in a positive way.

### 4.1.3.1 Security awareness training
Security awareness training should help staff recognize risks and take the appropriate actions. The training typically includes issues such as:
* user authentication, password safety, multifactor and biometrics
* secure web browsing and use of social media
* appropriate use of email, phones, and other communication channels
* endpoint security, including phones, tablets, laptops, use of removable media, personal devices, and so on
* remote and mobile working, including use of public Wi-Fi
* social engineering, phishing, and identity theft
* malware, including: viruses, ransomware, keyloggers, adware, spyware, and so on.
* advanced persistent threats
* personally identifiable information (PII) and data privacy
* classification and appropriate handling of information and other assets
* security incident reporting and management
* understanding relevant parts of the organization’s information security policies and controls.

Security awareness training should be held regularly, as well as for new staff. Some organizations have annual refresher training that covers the entire required material. Other organizations deliver more regular training that only covers part of the material in each training event, but include everything needed over the course of a year.

#### 4.1.3.2 Security requirements in every job description
Every job description should include appropriate security activities. Some of these activities will be generic and the same for everyone. Others will be specific to the role that staff have within the organization.

#### 4.1.3.3 Regular reinforcement of security information
Regular reinforcement of security information ensures that security is at the forefront of the staffs’ mind at critical moments. This reinforcement can be in the form of posters, screen savers, emails, management briefings, or any other method that is appropriate to the organization’s culture.

## 4.2 Organizational structures and teams
In organizations with a dedicated IT department, the role of the CISO is usually outside of IT, to ensure that the scope of the practice is not simply restricted to IT. Typically, the CISO will have a number of direct reports, who are able to develop policies and processes, perform security audits and provide information security guidance to other staff.

Many organizations have a dedicated IT security team, that provides expertise across the whole of the organization, but it is also important to have information security expertise in other IT teams. For example:
* Service architects and service designers must be able to architect and design secure IT services. They must possess enough knowledge and understanding to perform much of the work themselves, even if they might require assistance from specialist security staff.
* Application developers must be able to write secure code. This requires an understanding of secure coding practices and of common mistakes to avoid.
* Service desk staff must be able to recognize security incidents, and take appropriate action based on the organization’s security policy and security incident response plans.
* All staff must be aware of their responsibility to detect common security attacks and know how they should react to these attacks.

# 5. Information and technology
## 5.1 Information exchange
The effectiveness of information security management is based on the quality of the information used. This information includes, but is not limited to, information about:
* consumer’s business processes
* services, its architecture, and design
* partners and suppliers, and information on the services they provide
* regulatory requirements regarding information security
* technology and services available on the market, which might be relevant to information security
* security standards and best practices.

This information may take various forms. The key inputs and outputs of the practice are listed in section 3.

## 5.2 Automation and tooling
In some cases, the information security management practice can benefit from automation. Where this is possible and effective, it may involve the solutions outlined in Table 5.1.

### Table 5.1 Automation solutions for information security management activities
<table><tbody><tr><td><p><strong>Process activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><p><strong>Key functionality</strong></p></td><td><p><strong>Impact on the effectiveness of the practice</strong></p></td><td></td></tr><tr><td><p><strong>Security incident management process</strong></p></td><td></td></tr><tr><td><p>Preparation</p></td><td><p>Knowledge management tools and document repositories</p></td><td><p>Documenting and communicating policies, procedures, and incident response plans</p></td><td><p>Medium to very high, depending on the size and complexity of the organization</p></td></tr><tr><td></td><td><p>Service catalogue and configuration management database (CMDB)</p></td><td><p>Identifying critical services and assets</p></td><td><p>Very high</p></td><td></td></tr><tr><td><p>Detection and reporting</p></td><td><p>Monitoring tools</p></td><td><p>Detecting possible security incidents</p></td><td><p>Essential</p></td></tr><tr><td></td><td><p>Security incident and event management (SIEM) and correlation tools</p></td><td><p><span>Analysing data and detecting possible security incidents</span></p></td><td><p><span>Medium to very high, depending on the complexity of the services, applications and infrastructure</span></p></td><td></td></tr><tr><td></td><td><p><span>Intrusion detection systems (IDS) and intrusion prevention systems (IPS)</span></p></td><td><p><span>Detecting attacks, and responding with automated actions</span></p></td><td><p><span>High</span></p></td><td></td></tr><tr><td><p>Triage and analysis</p></td><td><p>Data forensic tools</p></td><td><p>Preserving evidence that may be needed in court proceedings</p></td><td><p>Could be anything from low to essential, depending on the legal and regulatory environment</p></td></tr><tr><td></td><td><p><span>SIEM or log analysis tools</span></p></td><td><p><span>Analysing security events</span></p></td><td><p><span>Very high</span></p></td><td></td></tr><tr><td><p>Containment and recovery</p></td><td><p>Backup and recovery tools</p></td><td><p>Recovering data after a security event</p></td><td><p>Essential</p></td></tr><tr><td></td><td><p><span>Definitive media library</span></p></td><td><p><span>Secure source of software and applications for use in recovery</span></p></td><td><p><span>Very high</span></p></td><td></td></tr><tr><td><p>Post-incident activity</p></td><td><p>Continual improvement register</p></td><td><p>Logging and tracking improvement suggestions</p></td><td><p>High</p></td></tr><tr><td></td><td><p>Knowledge management tools and document repositories</p></td><td><p>Documenting and communicating incident information and lessons learned</p></td><td><p><span>Medium</span></p></td><td></td></tr><tr><td><p>Audit and review process</p></td><td></td></tr><tr><td><p>Identify changes to business, technology, or threat environment</p></td><td><p>Process maps and process mapping tools</p></td><td><p>Documenting and communicating business processes</p></td><td><p>High</p></td></tr><tr><td></td><td><p><span>Service catalogue and configuration management database (CMDB)</span></p></td><td><p>I<span>dentifying new or changed technology</span></p></td><td><p><span>High</span></p></td><td></td></tr><tr><td><p>Identify missing controls</p></td><td><p>Security audit tools or questionnaires</p><p>Vulnerability assessment tools</p></td><td><p>Identify possible controls that might be needed</p></td><td><p>High</p></td></tr><tr><td><p>Assess control effectiveness</p></td><td><p>Security audit tools or questionnaires</p><p>Vulnerability assessment tools</p></td><td><p>Compare existing controls to good practice</p></td><td><p>High</p></td></tr><tr><td><p>Create audit report</p></td><td><p>Knowledge management tools and document repositories</p></td><td><p>Documenting and communicating audit report</p></td><td><p>Medium</p></td></tr><tr><td></td><td><p><span>Continual improvement register</span></p></td><td><p><span>Logging and tracking improvement suggestions</span></p></td><td><p><span>High</span></p></td><td></td></tr></tbody></table>

# 6. Partners and suppliers
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of *ITIL Foundation: ITIL 4 Edition* for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the ITIL practice guides for supplier management and service level management.

Partners and suppliers might provide critical products and service components. The service provider needs to negotiate and agree information security requirements with partners and suppliers to meet information security requirements.

Partners and suppliers might also provide information security services and solutions, such as: vulnerability assessments, threat assessments, security incident management, provision of security relevant infrastructure or applications, and so on. In this case, they should also be involved in the testing and reviewing of these services and solutions.

If suppliers have access to the organization’s network, servers, or other resources, it could be a security breach. This risk needs to be identified and controlled. Typically, this is controlled with:
* network isolation: preventing the supplier from accessing more sensitive parts of the network
* strong authentication and encryption: preventing the supplier from accessing sensitive data and systems
* contractual terms with regular audits: ensuring the supplier understands what is expected of them and meets these expectations.

# 7. Important reminder
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:
* focus on value
* start where you are
* progress iteratively with feedback
* collaborate and promote visibility
* think and work holistically
* keep it simple and practical
* optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of the *ITIL® Foundation: ITIL 4 Edition*.

# 8. Acknowledgements
AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following:

## 8.1 Authors
Stuart Rance, Ana Cecilia Perez, Mauricio Corona

## 8.2 Reviewers
Dinara Adyrbayeva, Pavel Demin

## References
1.  https://www.iso.org/obp/ui/#iso:std:iso-iec:27001:ed-2:v1:en (Accessed 3rd February 2020)This definition is different from the one used for the availability management practice. Service availability is defined differently from the availability of information.
