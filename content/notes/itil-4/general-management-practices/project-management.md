---
title: project management
date: 2023-10-20T00:00:00-06:00
draft: true
weight: 1
---


April 30, 2020
49 min read

ITIL
ITIL4 Practice Guides
Project management: ITIL 4 Practice Guide
38 Likes
This document provides practical guidance for the project management practice.

Table of Contents
1. 
About this document
It is split into five main sections, covering:

general information about the practice
the practices processes and activities and their role in the service value chain
the organizations and people involved in the practice
the information and technology supporting the practice
considerations for partners and suppliers for the practice.
1.1 ITIL® 4 qualification scheme
Selected content from this document is examinable as a part of the following syllabus:

ITIL Leader – Digital and IT Strategy
Please refer to the syllabus document for details.

2. 
General information
2.1 Purpose and Description
Key message

The purpose of the project management practice is to ensure that all projects in the organization are successfully delivered. This is achieved by planning, delegating, monitoring, and maintaining control of all aspects of a project, and ensuring motivation for the people involved.

ITIL architect's note
When the architecture of ITIL 4 was designed, it seemed a revolutionary decision to include the project management practice in the scope of ITIL. The ability to manage projects effectively is important to every organization, especially if it is good at tailoring various methods to its needs and environment. Therefore, project management was added. However, as we were working through details of the practices, we came to a conclusion that this is not enough, as projects should never be managed in isolation; they should contribute to a greater purpose defined by an organization and/or a programme. As a result, this practice guide covers project and programme management; the purpose of the practice can be updated to the following:

The purpose of the programme and project management practice(s) is to ensure that all projects in the organization are successfully delivered and contribute to creation of value for stakeholders of the organization and its programmes.
The practice is referred to as PPM (programme and project management) in this guide; in the sections and paragraphs focused on project management or programme management specifically, we used specific terms referring to projects or programmes.
We hope that this expansion of the scope will prove to be valuable for the practitioners, and we plan to reflect it in the next editions of ITIL Foundation and other ITIL publications with references to project management.
Programme and project management play an integral part in planning and introducing changes to an organization while optimizing the use of resources, accounting for risks, and linking changes to achieve the expected value.

A programme may be comprised of projects across different areas of the organization. For example, the launch of a new product or service may rely on projects running in the sales, marketing, distribution, and IT departments, all of which are focused on delivering the outcome required by the programme. A programme can be a standalone programme, but more often it forms part of a portfolio (see the portfolio management practice guide for more information).

A project is typically focused on delivering a specific output; a programme’s focus is on the outcomes and benefits of enabling value for the organization and other stakeholders. Programmes usually last longer than individual projects.

Both programmes and projects are distinguished from ongoing operations (often called ‘business as usual’) as they:

introduce significant changes
are temporary structures
bring risks and opportunities above and beyond the normality of business as usual.
2.2 Terms and Concepts
An important element of a profession is a body of knowledge that is distinctive to the professional group. For the past 50 years, project management associations around the world have made serious attempts to conduct themselves as professional associations and spent a considerable time and effort in developing bodies of knowledge (BoKs) and their associated certification programmes.

A BoK is a resource; providing the concepts, functions, and activities that make up the professional standards and provides key information to successful delivery of that profession’s core functions. In this case, the core function is programme and project management.

All project management BoKs describe how projects should be directed, managed, and delivered, however they all differ in terminology and lifecycle, which is why it is important to understand which BoK is behind the project that is driving the change. The main project management BoKs are the APM body of knowledge (APMBoK®), and the PMI body of knowledge (PMBoK®), although there are others to do with change management (CMBoK) and cybersecurity (CYBoK).

In this practice guide, key terms and definitions are based on AXELOS PPM BoKs and methods, including:

PRINCE2®
PRINCE2 Agile®
Managing Successful Projects®
P3O®.
2.2.1 Programme
Definition: Programme

A temporary, flexible structure created to coordinate, direct, and oversee the implementation of a set of related projects and activities in order to deliver outcomes and benefits related to the organization’s strategic objectives.

The focus of programmes is to deliver outcomes and benefits rather than outputs or products. A programme coordinates the projects within its boundaries and is more concerned with stakeholder engagement, communication, and direction when compared to projects.

The programme endeavours to gradually deliver changes in organizational capabilities through the related projects that run under its category. A group of projects structured around distinct step changes in capability and benefit delivery is called a 'tranche'. These gradual changes allow the organization to realize benefits during the programme rather than waiting for the whole programme to end.

The typical lifecycle or transformational flow of a programme is described in Managing Successful Programmes (MSP). This is shown in Figure 2.1.

Image of Figure 2.1 shows MSP transformation workflow

Figure 2.1 MSP transformational flow

2.2.2 Project
Definition: Project

A temporary structure that is created for the purpose of delivering one or more products according to an agreed business case.

The focus of projects is to deliver outputs (products or other deliverables) within defined parameters of time, cost, and quality. By doing so, those outputs are of value to the organization.

These outputs also allow the organization to realize benefits, but, in traditional (waterfall) projects, those benefits are primarily driven-out after the projects are completed.

The typical lifecycle of a traditional linear (waterfall) project as described in Managing Successful Projects with PRINCE2® is shown in Figure 2.2.

Image of Figure 2.2 represents PRINCE2 project management processes

Figure 2.2 PRINCE2 project management processes

An Agile approach works similarly to a programme but in a highly compressed timeframe. The agile delivery is planned in increments, and it is expected that benefits are generated at the deployment of each increment. Therefore, the organization receives its benefits as early as possible.

The typical lifecycle of an Agile project as described in PRINCE2 Agile® is shown in Figure 2.3.

Image of Figure 2.3 shows the PRINCE Agile project management processes

Figure 2.3 PRINCE2 Agile Project Management Process

2.2.3 Agile
The term ‘agile’ is very broad and is viewed in many different ways within the agile community. There is a set of well-known frameworks referred to as ‘Agile methods’, and there are also well-known behaviours, concepts, and techniques that are recognized as characterizing the agile way of working. However, there is no single definition of agile that accurately encapsulates them all, although the Agile Manifesto1, which is shown in Figure 2.4, comes quite close.

Image of Figure 2.4 shows the Agile Manifesto 2001

Figure 2.4 The Agile Manifesto 2001

Agile became so popular because it helped to address the new demands being placed on how software was delivered. It needed to be produced more frequently while retaining a specified level of quality to meet the demands of the digital age. (For more on agile software development see the software development and management practice guide and ITIL® 4: High-velocity IT, section 4.2).

In contrast to the traditional methods of delivery, the Agile phases are shorter, more iterative, and incremental. There is also a move to achieve early delivery of benefits by deploying products at the earliest opportunity, as described in Figure 2.5.

Image of Figure 2.5 shows Agile versus Waterfall

Figure 2.5 Agile versus waterfall

On the left of figure 2.5, the incremental Agile approach allows for multiple deployments throughout the project. The waterfall delivery on the right tends to allow for a single delivery at the end of the project.

2.2.4 Traditional (waterfall)
‘Waterfall’ was the first software development methodology, inherited from the manufacturing and construction industry where you can or cannot afford to iterate (after you have built a tower or a bridge you cannot go back to "improve" the foundation). However, because software is prone to frequent change, waterfall is not always the best solution.

Waterfall is often mentioned alongside Agile, but the two approaches contrast each other. The main difference between them is that waterfall doesn't react well to frequent changes, which is why it acquires a bad reputation in the software development community, where frequent changes are normal.

During the waterfall approach, a project is completed in distinct stages (see Figure 2.5) and moved step by step towards the ultimate release to the customer, business, or consumer. There is a big design upfront and then the plan is executed in a linear fashion with the hope of no changes in the designs.

In the Agile space, there is enough design upfront to get the project moving, with the absolute knowledge that the design will evolve and that change is inevitable. With the digitization of many aspects of organizations, Agile methods are being successfully applied to many digital solutions, not just software development. These include digital marketing, publishing, and other content-related activities, digital infrastructure, and digital communications. Non-digital projects that are focused on flexible, evolving resources (organizations, communities, partnerships, knowledge) also benefit from this Agile approach.

2.2.5 Holistic approach
The project management practice is not limited to managing the progress of projects; it should contribute to value co-creation and the overall strategy of an organization. In order to achieve this, the project management approach of the organization should be holistic. PRINCE2 describes seven key aspects of project management that should be addressed continually as part of the practice. They are known as seven PRINCE2 themes, and are outlined in Table 2.1.

Table 2.1 PRINCE2 key themes
Theme

Purpose

Answers the question

Business case

To establish mechanisms to judge whether the project is (and remains) desirable, viable, and achievable as a means to support decision-making in its (continued) investment.

Why?

Organization

To define and establish the project’s structure of accountability and responsibilities.

Who?

Quality

To define and implement the means by which the project will verify that products are fit for purpose.

What?

Plans

To facilitate communication and control by defining the means of delivering the products.

How?

How much?

When?

Risk

To identify, assess, and control uncertainty and, as a result, improve the ability of the project to succeed.

What if?

Change

To identify, assess, and control any potential and approved changes to the project baselines.

What is the impact?

Progress

To establish mechanisms to monitor and compare actual achievements against those planned, provide a forecast for the project objectives and the project’s continued viability, and control any unacceptable deviations.

Where are we now?

Where are we going?

Should we carry on?

2.2.6 Tailoring
An organization usually develops an approach to PPM based on one or more BoKs, methods, and frameworks. Regardless of the selected sources of best practice, organizations should tailor their guidance to suit the organization’s specific needs, capabilities, and constraints. Tailoring is an ongoing activity that is usually done through interval-based and event-based reviews of the PPM approach (see section 3.2.1).

2.2.7 Directing, managing, and delivering
There are three key levels of control in the PPM practice: direction, management, and delivery. In programmes and projects, these three layers have ‘air-gaps’ between them in order to allow the levels of management to exercise control without micro-managing the layer below. These ‘air-gaps’ are constructed with a controlled connectivity between the layers so that each layer can work within the parameters laid down by the layer above. This is known as management by exception, where only exceptions to those parameters are brought to the attention of the upper layer for a decision. Figure 2.6 shows an example of this approach.

Image of Figure 2.6 represents Directing, managing projects and delivering products in an organization

Figure 2.6 Directing, managing projects, and delivering products in an organization

2.2.8 Managing programmes
To manage a programme successfully, it requires:

leadership
vision
focus on value.
2.2.8.1 Leadership
Programmes translate the strategic objectives of the organization into specific purposes and objectives for individual projects. Leading and directing a programme provides the bridge between strategic objectives, business operations, and project delivery. Therefore, the key principles for effective leadership includes:

the ability to create a compelling vision portraying a beneficial future and communicate it to a range of stakeholders
empowered decision-making, giving individuals the autonomy to fulfil their roles effectively
visible commitment and authority
relevant skills and experience to provide active management.
2.2.8.2 Vision
A vision is a picture of a better future and is the vital focus and enabler for the acceptance, motivation, and activity alignment of the large community of stakeholders involved in any programme. The vision statement encapsulates the vision and is used to communicate a high-level impression of the desired ‘to-be’ state. A good vision statement:

is written as a future state: a snapshot of the organization in the future
can be easily understood by a wide variety of stakeholders
is written for the broadest groupings of stakeholders as the target audience
describes a compelling future
matches the degree of the transformational change with the boldness of the vision conveyed
avoids target dates, unless the vision is truly time-dependent
is sufficiently flexible
is short and memorable.
2.2.8.3 Focus on value
Value drives many aspects of programme management, which means it is the centre of programme management; programmes are primarily driven by the need to enable value by delivering benefits.

Definition: Benefit

A measurable improvement resulting from an outcome perceived as an advantage by one or more stakeholders.

Figure 2.7 illustrates the extent of the impact of benefits management within a programme.

Image of Figure 2.7 show the extent of the impact of Benefits management within a programme

Figure 2.7 The extent of the impact of benefits management within a programme

2.2.9 Directing projects
To direct a project successfully, the duties of a project board include:

Accountability The project board is accountable to programme or corporate management for the success or failure of the project within the constraints defined in a project mandate.
Unified direction This is about teamwork at project board level. While each project board member has accountability for satisfying the interests of a particular stakeholder category, it is crucial that a cohesive overall direction for the project is agreed and communicated.
Effective delegation Project board members must delegate effectively using the PRINCE2 organization structure and controls designed for this purpose. A key feature of the method in this respect is the implementation of management stages: delegating the day-to-day management of the project to the project manager on a stage-by-stage basis. The project board defines the framework for how projects will be executed to ensure consistency across the enterprise.
Cross-functional integration The project management team is a temporary, almost always cross-functional, structure that is set up with specific responsibility for the project. Project board members must ensure that this is recognized and respected in the functional or line management organizations and that the project board’s authority is not undermined.
Commitment of resources Project board members are responsible for committing the resources necessary for the successful completion of the project. It is an important criterion that, collectively, they should be able to deliver all the resources required for the success of the project.
Effective decision-making The project board makes the key decisions in the project. Decision-making is the means by which control is exerted, and PRINCE2 provides an optimized framework for this purpose.
Support for the project manager The project manager is the focus of the day-to-day management of the project, which is often a busy and stressful role. The project board can relieve some of this stress and remove some of the obstacles by demonstrating visible and sustained support for the project manager.
Effective communication The project manager must ensure communication is timely and effective, both within the project and with the key external stakeholders.
2.2.10 Managing projects
Managing projects under an Agile approach requires a slightly different style compared with a waterfall project method. In traditional projects, the project manager is much more central to the decision-making process on a day-to-day basis. Whereas in an Agile situation, the team is empowered to make decisions within set parameters, and the project manager facilitates the evolution of the products rather than directs the work.

To enable collaboration and self-organization, a project manager should:

trust the team to deliver and not be as involved
leave the team to work independently and not stifle their creativity
trust the people who know best to deliver the right solution
ensure that the project board understands exactly what ‘empowerment’ means so that the team will be supported and not overruled
involve the team in release planning for a truly honest view of what can be released and when
focus on having a stable team to drive innovation and the right solution
insist on customer involvement all the way through and that they deliver input when required
ensure that the team recognises that the customer is fully integrated into the team so that they deliver the business need.
To maintain transparency and communication, a project manager should:

clearly communicate the product vision to the team so that they know what they are building and why
deliver something frequently that the customer/user can relate to in order to get fast feedback
ensure the whole team, including the customer, is involved in the vision to gain maximum motivation
ensure the team has a minimum viable product that is truly a ‘minimum’
ensure the project board and senior stakeholders understand MoSCoW prioritization techniques so that their expectations can be set early
engage with and understand the project stakeholders to avoid misunderstandings
understand and communicate the benefits and any threats to them so that the team does not fixate on products alone
ensure the needs of the customer representative are being met and that the evolving solution meets the business need.
To maintain a healthy and inspiring work environment, a project manager should:

work with the team managers to ensure the team bonds well
make sure the team is trained in Scrum and has a good grounding in Agile delivery
ensure the team knows what type of Agile approach is being used so that it can be tailored appropriately
be clear about the delivery process with the stakeholders so as to set their expectations properly
collaborate with product owners
ensure the team is set up to make releases on demand so that the technical infrastructure does not get the way of release delivery
ensure the team is co-located as much as possible to promote collaboration and communication
ensure the team understands the role of the ‘servant leader’ so that they understand the difference between coaching and direction.
To successfully plan, monitor, and control, a project manager should:

attend the daily stand-ups to know the status of the project
focus on removing problems so that there are no blockers for the work
make sure retrospectives are held frequently to improve delivery
make sure the team knows ‘what to fix’ versus ‘what to flex’ to maximize the value to the business
ensure the project information/reports (team boards) are intelligible to enable progress tracking
ensure project level requirements are prioritized as soon as possible to assist in focusing on the business need
use product-based planning and link the products to benefits so that the right outputs are created at the right time with a view to delivering benefits early
agree the reporting metrics to have confidence that progress is reported correctly
synchronize sprint teams across the project to keep the interfaces relevant
ensure the teams are not continually deferring the ‘difficult’ stuff to later sprints to avoid the integrity of the evolving solution becoming compromised.
2.2.11 Delivering products in an Agile environment
The delivery of products in an Agile environment relies on considering two major aspects that are inextricably linked:

what to fix and what to flex
prioritization and timeboxing/sprints.
2.2.11.1 What to fix and what to flex
Image of Figure 2.8 shows a diagram that represents Applying Tolerances to a project,  such as what to Fix and what to Flex

Figure 2.8 Applying tolerances to a project

Table 2.2 demonstrates PRINCE2 Agile views.

Table 2.2 How PRINCE2 Agile views tolerances for the six aspects of a project
Aspect

Tolerance guidance

Summary

Time

Zero tolerance for all extra time on all levels of plan.

Fix
Cost

Zero tolerance for all extra cost on all levels of plan.

Fix
Risk

Zero tolerance for risks above the level that the project board decides must be escalated. Tolerances may be used for risks that are below this level.

Fix & flex
Scope

Not everything the project aims to create is of equal importance, so they can be prioritized.
Zero tolerance for those products that are essential.
Tolerances may be used for products that are desirable but not essential.
Fix & flex
Quality

Not all acceptance criteria and quality criteria are of equal importance, so they can be prioritized.
Project product description: zero tolerance for the customer’s quality expectations and acceptance criteria that are essential.
Tolerances may be used for the customer’s quality expectations and acceptance criteria that are desirable but not essential.
Product descriptions (in general): zero tolerance for the quality criteria that are essential.
Tolerances may be used for the quality criteria that are desirable but not essential.
Fix & flex
Benefits

Zero tolerance for the level that is defined as ‘minimum viability’ in the business case.
Tolerances may be used above the level that is defined as ‘minimum viability’ in the business case.
Fix & flex
2.2.11.2 Prioritization and timeboxing/sprints
Having decided what to fix and what to flex, the team needs to apply prioritization to those aspects they are going to flex in order to remain within the set timeframes.

Prioritization may be based on the MoSCoW technique. The rules are quite specific:

Must have requirements will provide the minimum viable product, which can be guaranteed to be delivered. This can be achieved by ensuring that no more than 60% of the effort in the timeframe is allocated to must have requirements.
Should have requirements are important but not vital. The business may find it difficult if these are left out. It may necessitate and leave them with a costly workaround.
Could have requirements are even less important and can be seen as a wish list with far fewer consequences on the end solution if left out. It is recommended that up to 20% of the effort of the timeframe be allocated to this category, providing a 20% tolerance for the timeframe.
Won’t have (this time) requirements are the requirements that the project team has agreed will not be delivered in this particular timeframe. This does not mean they will never be delivered as they may be available later in the project in a different category.
With the priorities set, the team may now carry out the detailed planning at the timebox or sprint planning level, bearing in mind the percentages allocated to the various MoSCoW priorities. The timebox is a fixed period of time (usually between 2 to 4 weeks) during which a number of iterations are carried out by the developers with the sole intent of delivering as much as possible in that period. However, the first care is to deliver the must have requirements followed by the ‘shoulds’ and then the ‘coulds’. If time is running low, the business decides which of the ‘coulds’ will be abandoned first so that the higher priority requirements can be accommodated. This means that the business must adopt a new mindset regarding what it will and will not receive. However, as they are complicit in the delivery, nothing will come as a surprise.

2.3 Scope
The PPM practice draws on the abilities of the managers to plan, monitor, and control all aspects of a programme or project and motivate all those involved to achieve the objectives on time and to the specified cost, quality, and performance. This is achieved by:

defining and continually aligning the project management approach with the stakeholders
ensuring the project management approach is adopted and embedded in the organization
directing projects
managing projects
continually reviewing the practice for improvements.
There are several activities and areas of responsibility that are not included in the PPM practice, although they are still closely related to programme and project management. These are listed in Table 2.3, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

Table 2.3 Activities related to the PPM practice described in other practice guides
Activity	Practice guide
Establishing and managing contracts with suppliers and partners participating in projects	Supplier management
Creating and changing resources and products within projects	Service design

Change enablement

Release management

Deployment management

Software development and management

Infrastructure and platform management

Workforce and talent management
Managing and implementing improvements	Continual improvements
Managing organizational changes	Organizational change management
Managing project risks	Risk management
Optimizing project portfolios	Portfolio management
2.4 Practice success factors
Definition: Practice success factor
A complex functional component of a practice that is required for the practice to fulfil its purpose.

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The PPM practice includes the following PSFs:

establishing and maintaining an effective approach to programme and project management across the organization
ensuring the successful realization of programmes and projects.
2.4.1 Establishing and maintaining an effective approach to programme and project management across the organization
Establishing the use of best practice for programmes and projects within the organization is relatively easy. A champion must select the most appropriate methods that fit the culture and style of the organization and then attract the investment required for the training, tools, and techniques that will be required for practitioners to operate the methods successfully.

Maintaining the approaches may become more complex as time passes, the organizational changes and the drivers for change within the organization adapt to external forces. This can challenge current approaches if they have not been adjusting. In order for this to happen, the methods and approaches to programme and project management need to be assessed as part of the general ongoing assessment of the health of the organization as a whole.

Maturity models, such as P3M3, can be used to assess the currency of the methods, tools and techniques as well as competence of the project management professionals in an organization, so that they stay aligned with the developing needs and aspirations of the organization. The reports from these assessments should be used to correct or adjust any area that appears to fall short of delivering the service expected of that method.

Any changes to existing standards must be notified to the practice community along with any education or briefings; this is so that the latest thinking transitions over previous versions are seamless and the methods grow and evolve naturally.

2.4.2 Ensuring the successful realization of programmes and projects
Project and programme success is predominantly about benefit delivery. A post implementation review may point out a few failings in the technical delivery that should be addressed before trying the project a second time. Learning from experience is important, therefore reviews, embedding lessons, and feedback are essential.

Ensuring consistency in the delivery of programmes and projects requires an observance of the guidance, as well as the application of project/programme assurance to ensure the guidance is followed. However, this does not always culminate in a successful delivery if the benefits are not forthcoming. Therefore, assurance needs to be more holistic in its approach than just checking against a guide or standard. Projects are also about people: those providing the requirements and resources, creating the products, and agreeing the investment. These stakeholders need to be satisfied that the project is delivering to the best of its ability on behalf of others.

There are many reasons why projects might fail, this can include: setting unrealistic expectations, poor methodology and requirements, inadequate resources, poor project management, and untrained team members. However, these things can be avoided by adopting effective practices and project management techniques that will help to establish a clear understanding of expectations and processes between all the stakeholders.

Generally, there is a simple set of five rules that can help prevent projects failing:

begin with the end in mind: start with a clear project scope
build a project plan: visualize everything that needs to be done on a timeline
do not be so connected to the plan: things can change and so does the plan
check, update, and monitor: check the timeline for progress, update the timeline with actual performance, monitor the use of your resources
keep an eye on the quality: you cannot retrofit quality and poor quality delivers poor benefits.
It is also important to look for signs showing that the project may be in trouble. Some of them could be:

team morale starts to decline
quality of outputs starts to deteriorate
lack of communication.
In organizations that embrace Agile, the ITIL guiding principles provide a useful extension to the five rules above:

focus on value
start where you are
progress iteratively with feedback
collaborate and promote visibility
think and work holistically
keep it simple and practical
optimize and automate.
2.5 Key metrics
The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide

Key metrics for the PPM practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.4.

Table 2.4 Examples of key metrics for the practice success factors
Practice success factors

Key metrics

Establishing and maintaining an effective approach to programme and project management across the organization

Stakeholders’ satisfaction with the PPM approach
Stakeholders’ satisfaction with the benefits provided by programmes and projects
Number and impact of deviations from the agreed approach
Number and impact of project or programme failures because of the approach’s ineffectiveness
Alignment of the PPM approach with relevant industry standards and best practices
Ensuring the successful realization of programmes and projects

Number and percentage of projects being completed on time and budget
Percentage of benefits realized from each project and programme
Stakeholders’ satisfaction with the benefits provided by programmes and projects
Stakeholders’ satisfaction with the progress and management of programmes and projects
3. 
Value Streams and processes
3.1 Value streams contribution
Like any other ITIL management practice, the PPM practice contributes to multiple value streams. It is important to remember that a value stream is never formed of a single practice. The PPM practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which the practice contributes are:

design and transition
obtain/build.
The contribution of the PPM practice to the service value chain is shown in Figure 3.1.

Image of Figure 3.1 shows heat map of the Contribution of the PPM Practice to Value Chain process

Figure 3.1 Heat map of the contribution of the PPM practice to value chain activities

3.2 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

Definition: Process

A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into outputs. Processes define the sequence of actions and their dependencies.

The PPM practice activities form five major processes:

managing the organization’s approach to PPM
directing projects
managing projects
managing product delivery.
3.2.1 Managing the organization’s approach to PPM
This process is focused on defining, agreeing, communicating, and promoting an organization-wide common approach to programme and project management. It includes the activities listed in Table 3.1 and transforms the inputs into outputs.

Table 3.1 Inputs, activities, and outputs of the managing a common approach to PPM process
Key inputs

Activities

Key outputs

Organization’s strategy
Stakeholders’ requirements for PPM
Budgetary/financial considerations and related information
Organization’s portfolio approach
Legal requirements, considerations, and related information
Organization’s services, customers, and partners and suppliers information
Develop and agree the PPM approach
Communicate and embed the PPM approach
Review and adjust the PPM approach
Updated PPM approach and procedures
PPM knowledge articles, training, and awareness materials
Figure 3.2 shows a workflow diagram of the process

Image of Figure 3.2 shows workflow of the Managing a Common Approach to PPM process

Figure 3.2 Workflow of the managing a common approach to PPM process


Table 3.2 provides examples of the process activities.

Table 3.2 Activities of the managing a common approach to PPM process
Activity

Example

Develop and agree the PPM approach

The PPM approach defines how the organization delivers change through programmes and projects.

There are various models that can be used to assist an organization in the delivery of change, and these can be found in the TSO publication Portfolio, Programme and Project Offices (2013).

However, the three main functional areas that are common to all models is that they provide the following services:

decision support
delivery support
centre of excellence.


Decision support

This has a focus on supporting management decision-making and may align with strategy, prioritization, benefits management, dashboard reporting, management information, and provision of oversight, scrutiny, and challenge. These are key services at the portfolio level but rely on supporting information from the programmes and projects.



Delivery support

This functional area focuses on supporting the delivery of change and these services may be delivered through a central flexible resource pool of delivery staff with capacity planning and HR processes. The delivery staff within the resource pool may be programme or project resources deployed to support specific programmes or projects as they are launched. Alternatively, they may be internal programme or project specialists who are employed at programme or project start-up to ensure a fast-track or consistent start-up process is being used, or even to assist the programme or project manager in the development and delivery of the programme or project.



Centre of excellence

This functional area focuses on the development of standard methods and processes, developing consistent working practices and ensuring they are deployed appropriately and well. It may include capability support through training and coaching, internal consultancy (in tailoring the standards and guidance), knowledge management, tools support and independent assurance. The function generally exists within a portfolio office but may have evolved as a separate independent CoE office.

The approach should be defined and agreed between the stakeholders, and then defined in more detail in the following workflows and procedures:

managing programmes
directing projects
managing projects
managing product delivery.
Communicate and embed the PPM approach

The agreed approach and procedures are communicated and discussed with the PPM stakeholders across the organization. To educate the involved teams and embed the approach and procedures, PMO may choose to run trainings and knowledge sharing events. Stakeholders may decide the level of formality for the trainings for different groups. For the people involved in the PPM practice daily, policies and controls may be created for a formal training as a prerequisite and periodic awareness trainings.
External communications on the PPM approach and procedures should be prepared and published in the agreed channels to onboard the third parties involved in programmes and projects.
Review and adjust the PPM approach

PPM stakeholders monitor and review the adoption, compliance, and effectiveness of the agreed sourcing strategy and procedures. This is done on event-based (project failure or project-related incidents, conflicts, crises, complaints, and so on) and interval-based basis. The resulting findings and initiatives are used as input for continual improvement.

3.2.2 Directing projects
The purpose of the directing projects process is to enable the project board to be accountable for the project's success by making key decisions and exercising overall control while delegating the day-to-day management of the project to the project manager. This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

Table 3.3 Inputs, activities, and outputs of the directing projects process
Key inputs

Activities

Key outputs

The organization’s PPM approach
Project brief
Project product description
Business case
Stage or exception plan
Authorize initiation
Authorize the project
Authorize a stage or exception plan
Give ad hoc direction
Authorize project closure
Approved project brief, business case, and stage or exception plan
Lessons learnt
Risk register
Approved product descriptions
User acceptance documents
Project reports
Figure 3.3 shows a workflow diagram of the process

Image of Figure 3.3 shows workflow of the  Directing Projects process

Figure 3.3 Workflow of the directing projects process

Table 3.4 describes the activities of the process.

Activity

Description

Authorize initiation

The project board is provided with enough information to conclude that the project looks viable (or not). They then review and authorize the project manager to carry out more detailed research, or reject the initiation.

Authorize the project

The project board now has a full and worthwhile business case, an achievable delivery plan, and analysis of the key risks to review. On this information they may or may not authorize the project manager to start delivering the project.

Authorize a stage or exception plan

At pre-determined intervals throughout the project (usually at the end of each increment) the project board will need to re-evaluate the validity of the project based on an updated business case, delivery plan, and risk and issue situation. On this information they may or may not authorize the project manager to continue delivering the project.
An exception will require further scrutiny to ensure the remedial actions are likely to be effective and do not jeopardize the project further.
An exception review may serve as an input into the PPM approach review.
Give ad hoc direction

The project board may review and offer informal guidance or respond to requests for advice at any time during the project.
Analysis of this escalation may serve as an input into the PPM approach review.
Authorize project closure

The controlled close of a project is as important as the controlled start. There must be a point when the objectives of the original and current versions of the project initiation documentation and delivery plan are reviewed and assessed to understand whether the objectives have been met. Lessons learnt should be logged, and the analysis of the project may serve as an input into the PPM approach review.

3.2.3 Managing projects
The purpose of the managing projects process is to enable the project manager to be responsible for the day-to-day tasks of running the project on behalf of the project board. This process includes the activities listed in Table 3.5 and transforms the inputs into outputs.

Table 3.5 Inputs, activities, and outputs of the managing projects process
Key inputs

Activities

Key outputs

Organization’s project management approach and procedures
Programme plan
Lessons learnt
Project mandate
Project product description
Starting up a project
Initiating a project
Controlling a stage
Managing a stage boundary
Closing a project
Business case
Project brief
Stage plan
Project team
Project plan
Project status reports
Lessons learnt
Risk register
Figure 3.4 shows a workflow diagram of the process.

Image of Figure 3.4 shows the workflow process for Managing Projects

Figure 3.4 Workflow of the managing projects process

Table 3.6 Activities of the managing projects process
Activity

Example

Starting up a project

To ensure that the prerequisites for initiating a project are in place by answering the question ‘Do we have a viable and worthwhile project?’

Initiating a project

To establish solid foundations for the project, enabling the organization to understand the work that needs to be done to deliver the project product before committing to a significant spend.

Controlling a stage

To assign work to be done, monitor such work, deal with issues, report progress to the project board, and take corrective actions to ensure the management stage remains within tolerance.
Lessons learnt from this activity may serve as an input into the PPM approach review.
Managing a stage boundary

To enable the project manager to provide the project board with sufficient information to be able to review the success of the current stage, approve the next stage plan, review the updated delivery plan, and confirm the viability of the business case.
Lessons learnt from this activity may serve as an input into the PPM approach review.
Closing a project

To provide a fixed point at which the acceptance of the project product is confirmed and recognize the objectives have been met.
Lessons learnt from this activity may serve as an input into the PPM approach review.
3.2.4 Managing product delivery
The purpose of the managing product delivery process is to enable the solution development teams to create an evolving solution in accordance with the business priorities and staying within the timeframes, costs, and quality stipulated by the business. Table 3.7 includes the activities in the process and transforms the inputs into outputs.

Table 3.7 Inputs, activities, and outputs of the managing product delivery process
Key inputs

Activities

Key outputs

Organization’s project management approach and procedures
Work packages
Project backlog
User stories
Product description
Accept a work package
Execute a work package
Deliver a work package
Delivered and accepted work package
Lessons learnt
Proposed improvements
Figure 3.5 shows a workflow diagram of the process.

Image of Figure 3.5 shows the workflow Managing Product Delivery process

Figure 3.5 Workflow of the managing product delivery process

Table 3.8 provides examples of the process activities.

Activity

Example

Accept a work package

Before a work package is allocated to a team, there should be agreement between the project manager and team leader as to what is to be delivered.

Execute a work package

The work is executed and monitored according to the requirements in the work package.
The team performs an analysis of the execution, logs the lessons learnt, and proposes improvements to the process or PPM approach.
Deliver a work package

Just as the work package was accepted from the project manager, the notification of its completion must be returned to the project manager.

The work packages described in the table may take the form of a traditional work package: a set of information about one or more required products collated by the project manager to pass responsibility for work or delivery formally to a team manager or team member.

Under an Agile approach, the work packages may take a slightly different form but with the same desired outcomes. In this case they will be discreet timeboxes or sprints with associated products to be completed within the timebox or sprint according to the business priorities of those products.

4. 
Organizations and people
4.1 Roles, competencies, and responsibilities
The practice guides do not describe the roles of practice owners or managers that should exist for all practices. They focus instead on specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

Table 4.1 Competency codes and profiles
Competency code

Competency profile (activities and skills)

L

Leader Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes

А

Administrator Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements

C

Coordinator/Communicator Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns

М

Methods and techniques expert Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement

Т

Technical expert Providing technical (IT) expertise and conducting expertise-based assignments

The role accountable for all PPM activities is usually the practice owner. The competency profile for this role is CLA, though the importance of each of these competencies varies from activity to activity. Examples of other roles which are responsible for PPM activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

Table 4.2 Examples of the roles involved in PPM activities
Process activity

Responsible roles

Competency profile

Specific skills

Managing the organization’s approach to PPM
Develop and agree the PPM approach

PMO head
Portfolio manager
Programme manager
Project manager
Scrum master
Agile coach
Business analyst
External consultant
LMTC

Good knowledge of the organization, its services, market, stakeholders, culture, nature of the changes, and projects
Expertise in project management approaches, methods, and BoKs, both waterfall and agile
Expertise in building processes, workflows, and procedures
Communication and coordination
Communicate and embed the PPM approach and procedures

PMO head
Portfolio manager
Programme manager
Project manager
Business analyst
External consultant
Organizational change manager
Knowledge manager
HR manager
CLM

Good understanding of the organizational culture and internal stakeholders
Good knowledge of the agreed approach and procedures
Excellent leadership and communication skills
Review and adjust the PPM approach and procedures

PMO head
Portfolio manager
Programme manager
Project manager
Scrum master
Agile coach
Business analyst
External consultant
LMC

Decision making
Good knowledge of the organization, its services, market, stakeholders, culture, nature of the changes, and projects
Expertise in project management approaches, methods, and BoKs, both waterfall and agile
Directing a project	
Authorize initiation
Authorize the projectAuthorize a stage or exception plan
Give ad hoc direction
Authorize project closure

PMO head
Portfolio manager
Programme manager
Project board member
Customer representative
Senior user
Product owner
Project sponsor
LC

Decision making
Stakeholder management
Value assessment
Good knowledge of the organization, its services, market, stakeholders, culture, nature of the changes, and projects
Managing projects	
Starting up a project
Initiating a project
Controlling a stage
Managing a stage boundary
Closing a project
Managing product delivery
Project manager
Scrum master
Agile coach
Project team member
Scrum team member
External consultant
Project coordinator
Service delivery manager
Business analyst
MCT

Expertise in project management approaches, methods, and BoKs, both waterfall and agile
Communication skills
Stakeholder management
Resources management
Subject matter knowledge
Accept a work package
Execute a work package
Deliver a work package
Scrum team member
Scrum master
Agile coach
Development team member
Product owner
Business analyst
TMC

Technical knowledge
Subject matter knowledge
Work package/task assessment
Resource and time management
Teamwork, communication, and collaboration skills
Agile methods knowledge
4.1.1 Programme manager
The responsibilities of the programme manager typically include:

day-to-day management of the programme, including taking the programme forward from appointment, supervising, and controlling and closing the programme
being the day-to-day agent on behalf of the programme sponsors, ensuring the successful delivery of the new capability
planning and designing the programme and proactively monitoring its overall progress, resolving issues, and initiating corrective action where appropriate
developing and implementing the programme’s governance framework
effectively coordinating the projects and their interdependencies
managing and resolving any risks and other issues that may arise
maintaining the overall integrity and coherence of the programme and developing and maintaining the programme environment to support each individual project within it
managing the programme’s budget and monitoring the expenditures and costs against benefits as the programme progresses
facilitating the appointment of individuals to the project delivery teams
ensuring that the delivery of outputs or services from the projects meets programme requirements in line with the programme blueprint, and is to the appropriate quality, on time, and within budgets
facilitating the development of the blueprint with input and approval of the relevant stakeholders
managing the blueprint and ensuring that the capabilities delivered are aligned with it
managing the performance of the programme team
maximizing the efficient allocation of resources and skills across the projects within the programme
managing internal and external suppliers to the programme
managing communications with stakeholders
initiating extra activities and other management interventions where gaps in the programme are identified or issues arise
reporting on the progress of the programme at regular intervals to the programme sponsors.
The skillset of a programme manager is more focused on decision-making and business management.

4.1.2 Project manager
The project manager is the single focus for the day-to-day management of a project. This person has the authority to run the project on behalf of the project board within the constraints laid down by the project board. The role of the project manager must not be shared.

The skills needed for a project manager are more ‘hard-skills’, oriented to execute some responsibility or some activity in different areas of knowledge.

The project manager’s professionalism is based on the proficiency in the following competency areas:

management control
benefits management
financial management
stakeholder engagement
risk management
organizational governance
resource management.
The project manager is responsible for the work in the managing projects and managing product delivery process. The project manager also delegates responsibility for the managing product delivery process to the team manager(s).

As the single focus for the day-to-day management of a project, there are many different aspects to the project manager role, some of which are shown in Figure 4.1.

Image of Figure 4.1 shows the facets of the project manager role

Figure 4.1 The facets of the project manager role

4.1.3 Team manager
The team manager’s prime responsibility is to ensure that the products are produced to an appropriate quality, as defined by the project manager, and adheres to the set timescale and cost accepted by the project board. The team manager is accountable to, and takes direction from, the project manager.

4.1.4 Scrum master
The Scrum master serves the product owner in several ways, including:

ensuring that the goals, scope, and product domain are well understood by everyone on the Scrum team
finding techniques for effective product backlog management
helping the Scrum team understand the need for clear and concise product backlog items
understanding product planning in an empirical environment
ensuring the product owner knows how to arrange the product backlog to maximize value
understanding and practising agility
facilitating scrum events as requested or needed.
The Scrum master serves the development team in several ways, including:

coaching the development team in self-organization and cross-functionality
helping the development team to create high-value products
removing impediments to the development team’s progress
facilitating Scrum events as requested or needed
coaching the development team in organizational environments in which Scrum is not yet fully adopted and understood.
The Scrum master serves the organization in several ways, including:

leading and coaching the organization in its Scrum adoption
planning Scrum implementations within the organization
helping employees and stakeholders understand Scrum and practical product development
causing a change that increases the productivity of the Scrum team
working with other Scrum masters to increase the effectiveness of the application of Scrum in the organization.
4.2 Organizational structures and teams
The structure of project teams may vary from project to project, and depends heavily on the approach taken for project management.

In PRINCE2, there are nine roles which are defined with specific responsibilities. They relate to project direction, project management, and project delivery; although in the case of project delivery, PRINCE2 only refers to the team manager and not the members of the delivery team. The roles are listed below:

project board
executive
senior user
senior supplier
project manager
team manager
project assurance
change authority
project support.
Please refer to the Managing Successful Projects with PRINCE2® for the detailed description of the roles.

Agile approaches have a more simplified roles list that usually includes a team member, team manager (e.g. Scrum master), product owner, and sometimes business analyst. It also does not have a project manager role.

The structure of the team should be decided for each project based on the organization’s approach to project management and scale and complexity of the project.

5. 
Information and technology
5.1 Information exchange, inputs/outputs
The effectiveness of the PPM practice is based on the quality of the information used. This information includes, but is not limited to, information about:

customers, users, and other project stakeholders
the product of project, user, and customer requirements
the organization’s approach to change and projects
the market environment and consumer groups
services and their architecture and design
the partners and suppliers used in the project, including contracts on the services they provide
the organization’s strategy, portfolio, and programmes.
This information may take various forms, depending on the nature of the projects. The key inputs and outputs of the practice are listed section 3.

5.2 Automation and tooling
In some cases, the PPM practice can significantly benefit from automation. Where this is possible and effective, it may involve the solutions outlined in Table 5.1.

Table 5.1 Automation solutions for PPM activities
Process activity

Means of automation

Key functionality

Impact on the effectiveness of the practice

Managing the organization’s approach to PPM

Develop and agree the PPM approach

Collaboration and communication tools
Mind mapping and brainstorming tools
Workflow modelling and visualization tools, communication and collaboration tools
Collaboration, information exchange
Workflow modelling, visualization, activities, and responsibilities mapping
Medium

Communicate and embed the PPM approach

Communication and collaboration tools, presentation tools, portals

Support of promotion, training, and awareness

Medium

Review and adjust the PPM approach

Collaboration and communication tools, reporting tools, visualization tools

Collaboration, information exchange, report creation and distribution, dashboarding

Medium

Directing projects

Authorize initiation

Communication and collaboration tools
Workflow automation tools
Collaboration and remote work, dashboarding
Business process, workflow, and approval automation
High

Authorize the project

Communication and collaboration tools
Workflow automation tools
Collaboration and remote work, dashboarding
Business process, workflow, and approval automation
High

Authorize a stage or exception plan

Communication and collaboration tools
Workflow automation tools
Reporting tools
Documentation tools
Collaboration and remote work
Business process, workflow, and approval automation
Reports creation and publishing, dashboarding
Documents depository and archive
High

Give ad hoc direction

Communication and collaboration tools

Collaboration and remote work

Low

Authorize project closure

Communication and collaboration tools
Workflow automation tools
Reporting tools
Documentation tools
Collaboration and remote work
Business process, workflow, and approval automation
Reports creation and publishing, dashboarding
Documents depository and archive
High

Managing projects

Starting up a project

Communication and collaboration tools
Documentation tools
Workflow automation tools
Reporting tools
Collaboration and remote work
Documents depository and archive
Business process, workflow, and approval automation
Reports creation and publishing, dashboarding
High

Initiating a project

Communication and collaboration tools
Documentation tools
Workflow automation tools
Project management tools
Collaboration and remote work
Documents depository and archive
Business process, workflow, and approval automation
Scope, statement of work, backlog, tasks assignment, risks, timeframe control
High

Controlling a stage

Communication and collaboration tools
Documentation management tools
Workflow automation tools
Reporting and distribution tools
Project management tools
Collaboration and remote work
Documents depository and archive
Business process, workflow, and approval automation
Reports creation and publishing, dashboarding
Scope, work breakdown structure, schedule, resources, budget management, risks, task assignment and control
Backlog management, task assignment and Kanban boards, sprints management, user stories/epic management
Retrospective and risks and lessons learnt logging
High

Managing a stage boundary

Communication and collaboration tools
Documentation management tools
Workflow automation tools
Reporting tools
Project management tools
Budget management tools
Collaboration and remote work
Documents depository and archive
Business process, workflow, and approval automation
Reporting, dashboarding, data visualization
Scope, statement of work, backlog, tasks assignment, risks, timeframe control
Costs consolidation, budget management and reporting, financial analysis
High

Closing a project

Communication and collaboration tools
Workflow automation tools
Reporting tools
Documentation tools
Collaboration and remote work
Business process, workflow, and approval automation
Reports creation and publishing, dashboarding
Documents depository and archive
Retrospective and risks and lessons learnt logging
High

Managing product delivery

Accept a work package

Communication and collaboration tools
Workflow automation tools
Backlog management tools
WBS management tools
Collaboration and remote work
Business process, workflow, and approval automation
Backlog items /work packages /tasks assignment and control
High

Execute a work package

Communication and collaboration tools
Workflow automation tools
Collaboration and remote work
Workflow and approval automation
High

Deliver a work package

Communication and collaboration tools
Workflow automation tools
Reporting tools
Collaboration and remote work
Workflow and approval automation
Reports creation and publishing, dashboarding, automated notifications
High

6. 
Partners and suppliers
Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). This means that organizations use suppliers in their projects for the resources in all four dimensions of service management. This includes, but is not limited to, supplier’s products and services, competencies and expertise, tools and data, market presence, strategic relationships, and so on.

Where organizations aim to ensure fast and effective project management, they usually try to agree close cooperation with their partners and suppliers, removing formal bureaucratic barriers in communication, collaboration, and decision-making (see the supplier management practice guide for more information).

External resources involved in the projects should be properly integrated and onboarded to align the approach, teamwork assumptions, culture, communication channels, and tools. Relationships with the suppliers should be constantly monitored and managed, with conflicts, exceptions and issues resolved as soon as possible. Exceptions should be used for review of the supplier agreements, both formal and informal, and re-alignment.

Where appropriate, parties should agree on how the project deliverables will be defined and how the acceptance and handover procedures will work. The definition of the work package should be central to this.

The practice-specific roles and teams described in section 4.1 are sometimes outsourced. Usually, outsourcing is easier if the organization has its own project management centre of excellence (e.g. PMO) and is used to integrate external project management specialists into the project teams. Outsourcing can also benefit if the supplier shares the same approach and processes in managing projects.

Organizations switch from outsourcing the function or process in the overall project management to outsourcing a specific competency. This way, the organization gets knowledge and experience it lacks but retains decision-making, control, and responsibility for the project within the organization.

7. 
Important reminder
Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:

focus on value
start where you are
progress iteratively with feedback
collaborate and promote visibility
think and work holistically
keep it simple and practical
optimize and automate.
More information on the guiding principles and their application can be found in section 4.3 of ITIL Foundation: ITIL 4 Edition.

8. 
Acknowledgements
AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

8.1 Authors
Richard Rose.

8.2 Contributors
Raymundo Sanchez Tico, Mauricio Corona.

8.3 Reviewers
John Edmonds, Allan Thomson, Michael Macgregor, Dinara Adyrbai, Roman Jouravlev, Erika Flora.

References
https://agilemanifesto.org/
[Accessed 30
th
April 2020]   
