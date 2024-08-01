---
title: "Architecture management: ITIL 4 Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

This document provides practical guidance for architecture management practice.

## 1. About this document

It is split into five main sections, covering:

*   general information about the practice
*   The practice’s processes and activities and their roles in the service value chain
*   the organizations and people involved in the practice
*   the information and technology supporting the practice
*   considerations for partners and suppliers for the practice.

#### 1.1 ITIL® 4 qualification scheme

Selected content from this document is examinable as a part of the following syllabus:

*   **ITIL Specialist** High-velocity IT.

Please refer to the respective syllabus document(S) for details.

## 2. General information

### 2.1 Purpose and description

<table><tbody><tr><td><strong>Key message</strong></td></tr><tr><td><p>The purpose of the architecture management practice is to explain the different elements that form an organization. This practice explains how the elements interrelate to enable the organization to effectively achieve its current and future objectives. It provides the principles, standards, and tools that enable an organization to manage complex change in a structured and agile way.</p></td></tr></tbody></table>

A comprehensive architecture management practice applies to all levels of an organization’s architecture. This includes the following:

*   business architecture
*   product and service architecture
*   information systems architecture, including data and applications architecture
*   technology architecture
*   environmental architecture.

The scope of the practice is defined by an organization’s position, vision, and strategy. For example, the architecture management practice of an internal IT service provider is likely to focus on the architecture of its products, services, information systems and technology. In other cases, the lower levels of technology architecture might be excluded from the scope, if third parties provide the infrastructure and platform for the organization. This is also likely to be reflected in the IT systems architecture. However, the architecture management practice should be developed consistently at all levels of the organization, as well as at all levels of the architecture.

The architecture management practice should describe the organization’s service value system and resources of all four dimensions of service management, which are:

*   organization and people
*   information and technology
*   processes and value streams
*   suppliers and partners.

This is illustrated in Figure 2.1.

![image of Figure 2.1 shows Architecture levels and the four dimensions of service management](Architecture%20management%20ITIL%204%20Practice%20Guide/Picture1.png)

**Figure 2.1 Architecture levels and the four dimensions of service management**

The architecture management practice ensures that:

*   the organization’s current architecture is understood and mapped to the organization’s strategy
*   the target organization’s architecture is identified and agreed
*   the organization’s architecture is continually optimized to achieve the target architecture.

To meet these objectives, architects analyse the organization and describe its current architecture. The architecture is then assessed to identify optimization points that currently are or could become obstacles for the organization’s strategy realization. The target architecture is defined to resolve these obstacles. This practice allows the organization to evolve from its current architecture to the desired architecture; it also allows for ongoing course corrections, as the organization’s strategy and environment change.

### 2.2 Terms and concepts

There are several types, or levels, of architecture, that can be included within the scope of the practice. These are described in further detail below.

#### 2.2.1 Business architecture

<table><tbody><tr><td><strong>Definition: Business architecture</strong></td></tr><tr><td><p>A formalized description of how an organization uses its resources for realizing its strategy and objectives.</p></td></tr></tbody></table>

Business architecture explores how an organization’s resources are used to co-create value within the organization and with its stakeholders. Organizations use resources to create products and offer and deliver services based on these products.

#### 2.2.2 Product and service architecture

<table><tbody><tr><td><strong>Definition: Product and service architecture</strong></td></tr><tr><td><p>A formalized description of an organization's products and services, their components and inter-relationships and the principles and guidelines governing their design and evolution over time.</p></td></tr></tbody></table>

Product and service architecture provides an overview of an organization’s products and services. It also explores the interactions between the services and models that describe the structure, such as how the components fit together, and the dynamics, such as the activities, flow of resources, and interactions, of each product and service. These models can be used as templates for multiple products and services. Digital products and services are based on applications and data, as well as supporting information technologies, operational technologies and communication technologies.

#### 2.2.3 Information systems architecture

<table><tbody><tr><td><strong>Definition: Information systems architecture</strong></td></tr><tr><td><p>A formalized description of an organization's applications, data assets and data management resources. Information systems architecture shows how applications and data are interconnected and managed for the benefit of the organization.</p></td></tr></tbody></table>

Information systems use supporting infrastructure and platforms, incorporating information, operational, and communication technologies. These are described by the technology architecture.

#### 2.2.4 Technology architecture

<table><tbody><tr><td><strong>Definition: Technology architecture</strong></td></tr><tr><td><p>A formalized description of an organization's technology infrastructure, including information, operational and communication technologies, their inter-relationships and the way they support the organization's information systems.</p></td></tr></tbody></table>

#### 2.2.5 Environmental architecture

<table><tbody><tr><td><strong>Definition: Environmental architecture</strong></td></tr><tr><td><p>A formalized description of external factors impacting the organization and the drivers for change, as well as all aspects, types, and levels of environmental control and their management.</p></td></tr></tbody></table>

Organizations might find it useful to maintain an account of the environment in which they operate in, to ensure that its products and services are suitable for these environments and do not conflict with external constraints.

Environmental architecture includes: developmental, technological, business, operational, organizational, political, economic, legal, regulatory, ecological, and social influences. It helps organizations understand and manage its position within the ecosystem it operates in.

The architecture management practice includes the definition of the scope and structure of the architecture, which is based on the organization’s strategy and positioning.

### 2.3 Scope

The scope of the architecture management practice includes:

*   understanding and describing the organization’s current architecture
*   defining the target organization’s architecture and agreeing it with the relevant stakeholders
*   continual optimization of the organization to meet the target architecture
*   ensuring continual oversight of the ongoing changes to ensure they are aligned with the agreed target architecture.

There are several activities and areas of responsibility that are not included in the architecture management practice, although they are still closely related to it. These are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use un the context of value streams; they should be combined as necessary, depending on the situation.

#### Table 2.1 Activities related to the architecture management practice described in other practice guides

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Solution design (products, services, information systems and technologies)</p></td><td><p>Service design</p></td></tr><tr><td><p>Implementation of the architecture road map</p></td><td><ul><li>Project management</li><li>Change enablement</li><li>Organizational change management</li></ul></td></tr><tr><td><p>Investment decision and authorization of architecture options</p></td><td><p>Portfolio management</p></td></tr><tr><td><p>Definition of the organization’s direction and objectives</p></td><td><p>Strategy management</p></td></tr><tr><td><p>Detailed mapping of configuration items and assets</p></td><td><ul><li>Service configuration management</li><li>IT asset management</li></ul></td></tr></tbody></table>

### 2.4 Practice success factor

<table><tbody><tr><td><strong>Definition: Practice Success Factor</strong></td></tr><tr><td><p>A complex functional component of a practice that is required for the practice to fulfil its purpose.</p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective*.*

The architecture management practice includes the following PSFs:

*   ensuring that the organization's strategy is supported with a target architecture
*   ensuring that the organization's architecture is continually evolving to the target state.

#### 2.4.1 Ensuring that the organization's strategy is supported with a target architecture

The organization’s architecture should be optimized to achieve and support its strategy. This will require a target architecture model.

To develop an effective and realistic target architecture, architects need to understand the following:

*   the organization’s strategy and its current performance
*   the organization’s current architecture, benefits, and constraints
*   major pain points and its mapping to the architecture
*   the organization’s portfolios and ongoing developments
*   environmental factors and trends
*   technology trends, risks, and opportunities
*   other relevant trends and factors.

Analysing these areas will lead to an understanding of the current and desired state of the organization from the architecture perspective. Current and target architecture models can be developed based on this. The effectiveness of the architecture can be expressed in some of the following characteristics, depending on the organization’s strategy:

*   scalability
*   cost-effectiveness
*   compatibility with other organizations
*   compliance to regulations
*   agility
*   sustainability
*   security.

This is not a definitive list; other objectives can be created to ensure that the architecture is effective.

As the strategies of organizations are likely to continually evolve, architecture modelling should not be an isolated exercise. The current architecture model should be updated as the components change, and the target architecture model should be reviewed as the strategy changes. These updates initiate a review of an architecture road map (see 2.4.2).

Architecture analysis and target architecture planning are performed in close conjunction with other practices (see 2.3 for a list of these practices). It is important to ensure that the architecture models are correct, realistic, and that the understanding of the current and target architectures is shared among stakeholders. Realistic architecture planning is based on a good understanding of the current architecture, including legacy systems, constraints, vital business functions and behaviour patterns, adopted by internal and external stakeholders. It is also important to take other requirements and constraints into account, such as budgets, legislation, and so on. Finally, good knowledge of the technology landscape, including emerging technologies and industry trends, is important.

As well as a description of the target architecture, the road map should include recommendations and requirements for: taxonomy, standards, guidelines, procedures, templates and tools, which are to be used in architecturally important initiatives, such as product and service design, changes, projects, and so on. This includes integrating the recommended architecture controls into the relevant practices and value streams, to ensure that the activities of the organization adhere to the agreed development direction.  

#### 2.4.2 Ensuring that the organization's architecture is continually evolving to the target state

To ensure that an organization is evolving to the target architecture, an architecture road map is created. The road map is a collection of initiatives designed to change from the current architecture to the target architecture. Where appropriate, these initiatives can be managed as programmes or projects. Realizing the architectural changes involves several stakeholders and practices, depending on the nature of the changes. The architecture management practice ensures that the implemented changes follow the agreed road map and support the organization’s evolution to its target architecture.

<table><tbody><tr><td><strong>Key message</strong></td></tr><tr><td><p>The transition from the current architecture to the target architecture is rarely a revolution. Rather, it is an evolution enabled by a set of architectural principles, standards, and guidelines that the organization agrees to follow. Some legacy solutions may coexist with newer solutions for a significant time. Changes from the current architecture to the target architecture are always subject to portfolio decisions and careful prioritization. The architecture management practice is used to define the target architecture, and to maintain the agreed direction and pace of the architectural evolution.</p></td></tr></tbody></table>

Another important aspect of the architecture management practice activities is to ensure that the changes made to the organization’s resources, products, and services support the architecture’s evolution, by following the recommended architectural taxonomy, standards, guidelines, procedures, templates, and tools. They also should not contradict the architecture’s requirements and principles. This implies that the architecture management practice is involved in every service value stream that includes the introduction of new components, new third-party services, or other changes that affect the architecture.

### 2.5 Key metrics

The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the architecture management practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.2.  

#### Table 2.2 Example of key metrics for the practice success factors

<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Ensuring that the organization's strategy is supported with a target architecture</p></td><td><ul><li>Fulfilment of the agreed requirements for the target architecture</li><li>Number and impact of architectural constraints limiting realization of the organization’s strategy</li><li>Number and impact of strategic decisions not supported by the architecture</li><li>Completeness and quality of the target architecture, based on internal and independent assessments</li><li>Duration and impact of delays between the strategy update and the alignment of the target architecture</li></ul></td></tr><tr><td><p>Ensuring that the organization's architecture is continually evolving to the target state</p></td><td><ul><li>The number and impact of changes implemented that did not follow the agreed target architecture</li><li>Number and impact of architecturally significant changes that have not been assessed for conformance to the agreed architecture</li><li>Progress in fulfilling the architecture road map</li></ul></td></tr></tbody></table>

## 3. Value Streams and processes

### 3.1 Value stream contribution

Like any other ITIL management practice, the architecture management practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The architecture management practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which this practice contributes are:

*   engage
*   deliver and support
*   design and transition
*   improve
*   obtain/build
*   plan.

The contribution of the architecture management practice to the service value chain is shown in Figure 3.1.

![Image of Figure 3.1 shows Heat map of the contribution of the Architecture Management practice to the service Value Chain activities](Architecture%20management%20ITIL%204%20Practice%20Guide/Picture2.png)

**Figure 3.1: Heat map of the contribution of the architecture management practice to the service value chain activities**

## 3.2 Processes

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><strong>Definition: Process</strong></td></tr><tr><td><p>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</p></td></tr></tbody></table>

Architecture management activities form three processes:

*   architecture governance
*   development of a target architecture and road map
*   ongoing architectural control.

#### 3.2.1 Architecture governance

This process includes the activities listed in Table 3.1 and transforms the inputs into outputs.

#### Table 3.1 Inputs, activities, and outputs of the architecture governance process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Organization’s principles, policies and vision</li><li>Organizational strategy</li><li>Environmental factors</li><li>Organizational structure</li><li>Product and service portfolio</li><li>Programme and project portfolio</li><li>Customer portfolio</li><li>Architecture review reports</li><li>Audit reports</li></ul></td><td><ul><li>Analyse the organization and requirements</li><li>Develop and agree architecture vision</li><li>Monitor the organization’s architecture</li></ul></td><td><ul><li>Architecture vision</li><li>Architecture principles and requirements</li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![Image of Figure 3.2 shows Workflow diagram of the Architecture Governance process](Architecture%20management%20ITIL%204%20Practice%20Guide/Picture3.png)

**Figure 3.2 Workflow of the architecture governance process**

Table 3.2 provides examples of high-level descriptions of each of the activities of the architecture governance process.

#### Table 3.2 Activities of the architecture governance process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>‘Full stack’ architecture management</strong></p></td><td><p><strong>IT architecture management</strong></p></td></tr><tr><td><p>Analyse the organization and requirements</p></td><td><p>Executive leaders of the organization define the scope of the architecture management activities and appoint an architecture committee</p></td><td><p>CIO, IT architects, product owners, and business analysts review the available information regarding the organization’s vision, strategy, and requirements, and appoint an IT architecture committee</p></td></tr><tr><td><p>Develop and agree architecture vision</p></td><td><p>Architecture committee develops architecture vision for the organization and agrees the vision with the executive leaders</p></td><td><p>IT architecture committee develops the architecture vision for digital products and services, IT systems, and supporting technology and agrees the vision with CIO</p></td></tr><tr><td><p>Monitor the organization’s architecture</p></td><td><p>Based on periodic architecture review and audit reports, or on relevant exception reports, executive leaders of the organization review the effectiveness of the architecture and architecture management practice and provide input to the ‘analyse the organization and requirements’ activity</p></td><td><p>Based on periodic architecture review and audit reports, or on relevant exception reports, CIO, IT architects, product owners, and business analysts review the effectiveness of the architecture and architecture management practice and provide input to the ‘analyse the organization and requirements’ activity</p></td></tr></tbody></table>

#### 3.2.2 Development of a target architecture and road map

This process includes the activities listed in Table 3.3, and transforms the inputs into outputs.  

#### Table 3.3 Inputs, activities, and outputs of the development of a target architecture and road map process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Architecture vision</li><li>Architecture principles and requirements</li><li>Service configuration data</li><li>Asset register</li><li>Third-party contracts</li><li>Product and service portfolio</li><li>Programme and project portfolio</li><li>Customer portfolio</li></ul></td><td><ul><li>Identify requirements</li><li>Document current architecture</li><li>Develop target architecture</li><li>Design standards, frameworks, and guidelines</li><li>Design, agree, and communicate architecture road map</li></ul></td><td><ul><li>Architectural assessment report</li><li>Current architecture model</li><li>Target architecture model</li><li>Architecture controls, frameworks, and guidelines</li><li>Agreed architecture road map</li></ul></td></tr></tbody></table>

Figure 3.3 shows the workflow for the *development of a target architecture and road map* process.

![Image of Figure 3.3 shows workflow diagram of the development of a target architecture and road map process](Architecture%20management%20ITIL%204%20Practice%20Guide/Picture4.png)

**Figure 3.3 Workflow of the development of a target architecture and road map process**

Table 3.4 provides examples of high-level descriptions of each of the activities of the *development of a target architecture and road map* process.

#### Table 3.4 Activities of the development of a target architecture and road map process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>‘Full stack’ architecture management</strong></p></td><td><p><strong>IT architecture management</strong></p></td></tr><tr><td><p>Identify requirements</p></td><td><p>Architecture committee analyses the architecture vision and requirements.</p></td><td><p>IT architects analyse the IT architecture vision and requirements.</p></td></tr><tr><td><p>Document current architecture</p></td><td><p>If the current architecture in the scope of requirements has not been documented or is not up-to-date, architects explore and document current architecture at all levels, from business architecture to technology infrastructure.</p></td><td><p>If current IT architecture in the scope of requirements has not been documented or is not up-to-date, architects explore and document current IT architecture.</p></td></tr><tr><td><p>Develop target architecture</p></td><td><p>Architects, business analysts, relationship managers, and product owners review the current architecture to identify constraints and misalignment with the agreed architecture vision and develop a model for target architecture at all levels, ensuring consistency between the levels.</p></td><td><p>Architects, business analysts, and product owners review the current architecture to identify constraints and misalignment with the agreed architecture vision and develop a model for target IT architecture.</p></td></tr><tr><td><p>Design standards, frameworks, and guidelines</p></td><td><p>Based on the target architecture, architects develop supporting standards, guidelines, procedures, templates, and tools to ensure effective integration in the relevant practices and value streams. These are discussed and agreed with stakeholders, including practice owners, product owners, and others.</p></td><td><p>Based on the target IT architecture, IT architects develop supporting standards, guidelines, procedures, templates, and tools to ensure effective integration into the relevant practices and value streams. These are discussed and agreed with stakeholders, including practice owners, product owners, and others.</p></td></tr><tr><td><p>Design, agree, and communicate architecture road map</p></td><td><p>Architects identify the most critical gaps between the target and current architectures; they then propose an approach to migration and to ongoing architecture control. The road map includes controls ensuring adherence to the agreed architecture throughout the organization. This work is supported by product owners, risk managers, financial managers, and other relevant leaders and experts.</p><p>The proposed architecture road map is discussed and approved by the executive leaders. If not approved, the road map is returned to one of the previous steps.</p><p>Approved road map together with the supporting standards, frameworks, guidelines, and controls are communicated for a detailed planning and execution to the relevant teams, including programme and project managers, HR, portfolio and finance, product owners, and so on.</p></td><td><p>Architects identify the most critical gaps between the target and current architectures. They then propose an approach to migration and to ongoing architecture control. The road map includes controls ensuring adherence to the agreed architecture throughout the organization. This work is supported by product owners, risk managers, financial managers, and other relevant experts</p><p>The proposed IT architecture road map is discussed with and approved by CIO. If it is not approved, the road map is returned to one of the previous steps.</p><p>Approved road map together with supporting standards, frameworks, guidelines, and controls are communicated for detailed planning and execution to relevant teams, including programme and project managers, portfolio and finance, product owners, and so on.</p></td></tr></tbody></table>

#### 3.2.3 Ongoing architectural control

This process is focused on the implementation of the architecture road map and maintenance of the agreed architecture. It includes the activities shown in Table 3.5 and transforms the inputs into outputs.

#### Table 3.5 Inputs, activities, and outputs of the ongoing architectural control process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Agree architecture road map</li><li>Change backlog</li><li>Project plans</li><li>Product backlogs</li><li>Continual improvement register</li><li>Service configuration data</li><li>Asset register</li><li>Third-party contracts</li><li>Product and service portfolio</li></ul></td><td><ul><li>Identify architecturally significant changes and events</li><li>Check for conformance to the target architecture</li><li>Escalate non-conformance</li><li>Review progress against the architecture road map</li></ul></td><td><ul><li>Architecture (non-)conformance reports</li><li>Architecture review reports</li></ul></td></tr></tbody></table>

Figure 3.4 shows the workflow for the *ongoing architectural control* process.

![Image of Figure 3.4 shows workflow diagram of the ongoing Architecture Control process](Architecture%20management%20ITIL%204%20Practice%20Guide/Picture5.png)

**Figure 3.4 Workflow of the ongoing architectural control process**

Table 3.6 provides examples of high-level descriptions of each of the activities of the *ongoing architectural control* process.

#### Table 3.6 Activities of the ongoing architectural control process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Examples</strong></p></td></tr><tr><td><p>Identify architecturally significant changes and events</p></td><td><p>When an architecturally significant change, project, or improvement initiative is being planned, an architect is included in the approval workflow. Identification of the architectural significance is performed by the role responsible for planning, according to the agreed architecture controls. This activity is applicable to all architecturally significant initiatives, including those specifically created as part of the architecture road map.</p><p>When an architecturally significant event is identified (a design error, incorrect implementation, or a change bypassing an architecture control), it is reported to an architect for review. Identification of these events can be made by product owners, problem investigators, risk managers, auditors, and others.</p></td></tr><tr><td><p>Check for conformance to the target architecture</p></td><td><p>An architect reviews the proposed initiatives and reported events to assess conformance to the agreed target architecture model.</p><p>Initiatives that conform to the target architecture (including those triggered by the architecture road map), are approved and their processing continues in the respective value stream.</p><p>Events that conform to the to the target architecture are approved and their processing continues in the respective value stream. If the agreed approval procedure has been bypassed, the architect reports this to the relevant authority (product owner, project manager, change manager, continual improvement manager, or others).</p></td></tr><tr><td><p>Escalate non-conformance</p></td><td><p>Identified non-conformances are escalated to the relevant authorities (product owner, project manager, change authority, continual improvement manager, CIO, architecture committee, or others).</p><p>Architects provide the necessary information to identify alternative solutions that conform to the target architecture.</p></td></tr><tr><td><p>Review progress against the architecture road map</p></td><td><p>After significant changes and fixed intervals, a progress report is produced by the architects that explains the implementation and maintenance of the architecture road map. The report is communicated to the relevant stakeholders and serves as an input to the architecture governance process.</p></td></tr></tbody></table>

## 4. Organizations and people

### 4.1 Roles, competencies, and responsibilities

The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the following model shown in Table 4.1.

#### Table 4.1 Competency codes and profiles

<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p><strong>L</strong></p></td><td><p><strong>Leader</strong> Decision- making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p><strong>А</strong></p></td><td><p><strong>Administrator</strong> Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p><strong>C</strong></p></td><td><p><strong>Coordinator/communicator</strong> Coordinating multiple parties, maintaining communication between stakeholders, and running of awareness campaigns</p></td></tr><tr><td><p><strong>М</strong></p></td><td><p><strong>Methods and techniques expert</strong> Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p><strong>Т</strong></p></td><td><p><strong>Technical expert</strong> Providing technical (IT) expertise and expertise-based assignments</p></td></tr></tbody></table>

#### Table 4.2 Examples of roles with responsibility for architecture management activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Responsible roles</strong></p></td><td><p><strong>Competency profile</strong></p></td><td><p><strong>Specific skills</strong></p></td></tr><tr><td><p><strong>Architecture governance</strong></p></td></tr><tr><td><p>Analyse the organization and requirements</p></td><td><ul><li>Executive leaders</li><li>Architecture committee</li></ul><ul><li><span>Architects</span></li></ul><li>Product owners</li></td><td><p>TCA</p></td><td><ul><li>Good knowledge of the organization, its environment, portfolios, products, resources, and customers</li><li><span>Understanding of architecture management frameworks</span></li></ul></td></tr><tr><td><p>Develop and agree architecture vision</p></td><td><ul><li>Executive leaders</li><li>Architecture committee</li><li>Architects</li><li>Product owners</li></ul></td><td><p>TLMC</p></td><td><ul><li>Good knowledge of the organization, its environment, portfolios, products, resources, and customers</li><li>Strategic thinking</li><li>Leadership skills</li></ul></td></tr><tr><td><p>Monitor the organization’s architecture</p></td><td><ul><li>Executive leaders</li><li>Architecture committee</li><li>Architects</li><li>Product owners</li></ul></td><td><p>TCA</p></td><td><ul><li>Good knowledge of the organization, its environment, portfolios, products, resources, and customers</li><li>Understanding of architecture management frameworks</li><li>Strategic thinking</li></ul></td></tr><tr><td><p><strong>Development of a target architecture and road map</strong></p></td></tr><tr><td><p>Identify requirements</p></td><td><ul><li>Architects</li><li>Product owners</li><li>Resource managers</li></ul></td><td><p>TAC</p></td><td><ul><li>Analytical skills</li><li>Good understanding of the architecture vision</li></ul></td></tr><tr><td><p>Document current architecture</p></td><td><ul><li>Architects</li><li>Product owners</li><li>Resource managers</li></ul></td><td><p>TMA</p></td><td><ul><li>Good practical knowledge of the architecture’s management frameworks</li><li>Good understanding of the organization’s resources at the documented architecture level</li><li>Analytical skills</li></ul></td></tr><tr><td><p>Develop target architecture</p></td><td><ul><li>Architecture committee</li><li>Architects</li><li>Product owners</li><li>Resource managers</li></ul></td><td><p>TMC</p></td><td><ul><li>Analytical skills</li><li>Good understanding of the architecture vision</li><li>Good understanding of the current architecture’s strengths and weaknesses</li><li>Good understanding of external opportunities and threats</li></ul></td></tr><tr><td><p>Design standards, frameworks, and guidelines</p></td><td><ul><li>Architecture committee</li><li>Architects</li><li>Product owners</li><li>Resource managers</li></ul></td><td><p>TMC</p></td><td><ul><li>Analytical skills</li><li>Good understanding of the architecture vision</li><li>Good understanding of the current architecture’s strengths and weaknesses</li><li>Good understanding of external opportunities and threats</li></ul></td></tr><tr><td><p>Design, agree, and communicate architecture road map</p></td><td><ul><li>Architecture committee</li><li>Architects</li><li>Product owners</li><li>Resource managers</li></ul></td><td><p>MTCL</p></td><td><ul><li>Good understanding of organization’s capacity and constraints, understanding of business priorities</li><li>Good understanding of organization’s value streams and practices affecting the architecture</li><li>Communication and negotiation skills, presentation skills, leadership skills</li></ul></td></tr><tr><td><p><strong>Ongoing architecture control</strong></p></td></tr><tr><td><p>Identify architecturally significant changes and events</p></td><td><ul><li>Product owners</li><li>Change authorities</li><li>Project managers</li><li>Continual improvement managers</li><li>Product owners</li><li>Risk managers</li><li>Internal auditors</li></ul></td><td><p>T</p></td><td><p>Good understanding of the architectural impact of initiatives and events</p></td></tr><tr><td><p>Check for conformance to the target architecture</p></td><td><ul><li>Architects</li><li>Product owners</li><li>Architecture committee</li></ul></td><td><p>TM</p></td><td><ul><li>Good knowledge of the agreed target architecture, good understanding of the agreed architecture road map, including controls</li><li>Analytical skills</li><li>Communication skills</li></ul></td></tr><tr><td><p>Escalate non-conformance</p></td><td><ul><li>Architects</li><li>Product owners</li><li>Architecture committee</li></ul></td><td><p>CA</p></td><td><ul><li>Good knowledge of the agreed controls</li><li>Good communication skills</li></ul></td></tr><tr><td><p>Review progress against the architecture road map</p></td><td><ul><li>Architects</li><li>Product owners</li><li>Architecture committee</li></ul></td><td><p>AC</p></td><td><ul><li>Good knowledge of the architecture road map</li><li>Analytical and communication skills</li></ul></td></tr></tbody></table>

#### 4.1.1 Architect

The key practice-specific role is the architect. This role can be specialized, such as a business (or enterprise) architect, IT architect, or solution architect, depending on the practice scope.

The role of an architect is key for the architecture management practice. As described in table 4.2 above, most practice activities are performed or managed by architects.

The key competencies of an architect include:

*   understanding the business strategy, business model, and operating model of the organization and the service consumers’ organizations
*   understanding the environment in which the organization operates
*   knowledge of technologies used by the organization and of developing technologies available to the organization
*   knowledge of the organization’s portfolios: resource, product and service, customer
*   knowledge of the organization’s value streams and practices
*   expertise in architecture management frameworks, such as Zachman Framework<sup>TM</sup>, TOGAF®
*   expertise in relevant solution architecture frameworks, such as AWS, SOA, EMC, and so on.

The competence profile of an architect is TMCAL. Architects are experts in the organization’s resources and architecture management methods. However, communication and leadership skills are also important.

The responsibilities of architects within an organization may vary depending on the scope of the practice. Whereas business (enterprise) architects are key contributors to an organization’s strategic planning and business development, solution architects are focused on the architecture of specific products or systems.

It is not unusual to find dedicated job roles to fulfil the architect role. However, in smaller organizations the solution architect role is sometimes performed by product owners, and the business architect role is performed by executive leaders, usually on an ad hoc basis.

### 4.2 Organizational structures and teams

When organizations develop the architecture management practice, many find it useful to establish a team to drive architecture-related initiatives and to ensure ongoing architecture control. This is often known as the architecture committee and includes representatives from different levels and functions of the organization. Besides architects, this committee typically includes business function leaders, product owners, service designers, risk managers, portfolio managers, HR managers, and financial managers.

The architecture committee, which is sometimes called an architecture board, usually reports to the executive leadership team; the committee’s decisions affect all areas of the organization. Therefore, it is important to ensure that the committee has enough authority.

## 5. Information and technology

### 5.1 Information exchange

The effectiveness of the architecture management practice is based on the quality of the information used. This includes, but is not limited to, information about:

*   organization’s strategy
*   organization’s environment, key stakeholders
*   organization’s portfolios: resources, products and services, customers
*   service configuration and IT asset information
*   change schedule
*   programme and project portfolio
*   continual improvement register
*   organizational structure
*   technology trends.

This information may take various forms. The key inputs and outputs of the practice are listed in section 3.

### 5.2 Automation and tooling

The automation of the architecture management practice is focused around three main areas that enhance information exchange:

*   office automation tools: document, spreadsheet, and presentation tools
*   analysis and modelling tools, such as: computer-aided design, diagramming, and data modelling tools
*   Communication tools, such as: workflow, task management, and omnichannel communication systems.

Table 5.1 lists specific methods of automation relevant to each activity of the architecture management practice.

#### Table 5.1. Automation solutions for architecture management activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><p><strong>Key functionality</strong></p></td><td><p><strong>Impact on the effectiveness of the practice</strong></p></td></tr><tr><td><p><strong>Architecture governance</strong></p></td></tr><tr><td><p>Analyse the organization and requirements</p></td><td><p>Communication and collaboration tools</p><p>Analytical systems</p><p>Knowledge management tools</p></td><td><p>Collection, processing, and presentation of data from diverse sources</p></td><td><p>High</p></td></tr><tr><td><p>Develop and agree architecture vision</p></td><td><p>Communication and collaboration tools</p></td><td><p>Collaboration and information sharing</p></td><td><p>Medium</p></td></tr><tr><td><p>Monitor the organization's architecture</p></td><td><p>Communication and collaboration tools</p><p>Analytical systems</p><p>Knowledge management tools</p></td><td><p>Collection, processing, and presentation of data from diverse sources</p><p>Reporting engines</p><p>Dashboard systems</p></td><td><p>High</p></td></tr><tr><td><p><strong>Development of a target architecture and road map</strong></p></td></tr><tr><td><p>Identify and requirements</p></td><td><p>Analytical systems</p><p>Enterprise architecture management tools</p></td><td><p>Collection, processing, and presentation of data from diverse sources</p><p>Reporting engines</p></td><td><p>Medium</p></td></tr><tr><td><p>Document current architecture</p></td><td><p>Enterprise architecture management tools</p></td><td><p>Architecture mapping and analysis</p></td><td><p>High</p></td></tr><tr><td><p>Develop target architecture</p></td><td><p>Enterprise architecture management tools</p></td><td><p>Architecture mapping and analysis</p></td><td><p>High</p></td></tr><tr><td><p>Design controls, frameworks, and guidelines</p></td><td><p>Enterprise architecture management tools</p><p>Communication and collaboration tools</p><p>Workflow and task management systems</p></td><td><p>Architecture mapping and analysis</p><p>Process design</p></td><td>High</td></tr><tr><td><p>Design, agree, and communicate architecture road map</p></td><td><p>Enterprise architecture management tools</p><p>Communication and collaboration tools</p></td><td><p>Architecture mapping and analysis, road map mapping</p><p>Collaboration and information sharing</p></td><td><p>High</p></td></tr><tr><td><p><strong>Ongoing architecture control</strong></p></td></tr><tr><td><p>Identify architecturally significant changes and events</p></td><td><p>Workflow management and work planning tools, ITSM toolsets, enterprise architecture management tools</p><p>Monitoring and event management tools</p></td><td><p>Work planning, assessment and approval flows and controls</p><p>Event detection and correlation</p></td><td><p>High</p></td></tr><tr><td><p>Check for conformance to the target architecture</p></td><td><p>Enterprise architecture management tools</p></td><td><p>Architecture mapping and analysis, road map mapping</p></td><td><p>Medium</p></td></tr><tr><td><p>Escalate non-conformance</p></td><td><p>Communication and collaboration tools</p></td><td><p>Collaboration and information sharing</p></td><td><p>Medium</p></td></tr><tr><td><p>Review progress against the architecture road map</p></td><td><p>Enterprise architecture management tools</p></td><td><p>Architecture mapping and analysis, road map mapping</p></td><td><p>High</p></td></tr></tbody></table>

## 6. Partners and suppliers

The organization’s architecture should support its strategy and ensure that all components of the organization effectively contribute to its success. The architecture is not limited to the organization’s own resources. This includes the organization’s service portfolio and the way it interacts with its service consumers. However, third-party services should not be underestimated.

At the business architecture level, important trends include multi-sourcing, service integration and management (or on the other hand disintermediation). At the technology architecture level, digitization and the resulting third-party cloud services are the main trend affecting the architecture.

Both business and technology trends influence the product and service architecture. This should be reflected in the organization’s architecture and considered when planning target architectures and road maps. To address this, the architecture management practice should be conducted in close conjunction with other practices, including: portfolio management, supplier management, organizational change management, risk management, infrastructure and platform management, and of course strategy management.

## 7. Important reminder

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of things that organizations might think about, not a list of answers. When using the content of the ITIL practice guides, organizations should always follow the ITIL guiding principles:

*   focus on value
*   start where you are
*   progress iteratively with feedback
*   collaborate and promote visibility
*   think and work holistically
*   keep it simple and practical
*   optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of the *ITIL® Foundation: ITIL 4 Edition publication*.

## 8. Acknowledgements

AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

### 8.1 Authors

Pavel Demin, Roman Jouravlev

### 8.2 Reviewers

Dinara Adyrbayeva, Anton Lykov, Irina Matantseva
