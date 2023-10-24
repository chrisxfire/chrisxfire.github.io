---
title: "IT asset management: ITIL 4 Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

This guide provides practical guidance for the IT asset management practice.

## 1. About this guide

This guide provides practical guidance for the IT asset management practice. It is split into seven main sections, covering:

*   general information about the practice
*   the practice’s processes and activities and their contributions to the service value streams
*   the organizations and people involved in the practice
*   the information and technology supporting the practice
*   considerations for partners and suppliers for the practice
*   information on assessing and developing the capability of the practice
*   recommendations for succeeding in the practice.

### 1.1 ITIL® 4 qualification scheme

Selected content from this guide is examinable as a part of the following syllabuses:

*   **ITIL Practitioner** IT Asset Management
*   **ITIL Specialist** Plan, Implement and Control

Please refer to the respective syllabus documents for details.

## 2. General information

#### 2.1 Purpose and description

IT assets are increasing in number and can come in many forms. ITIL defines an IT asset as follows.

<table><tbody><tr><td><p><strong>Definition: IT asset</strong></p></td></tr><tr><td><p>Any financially valuable component, resource, or capability that could contribute to the delivery of an IT product or service. The types of IT assets have grown in recent years to include physical assets like servers, desktops, laptops, and network hardware, as well as less tangible assets such as virtual servers, cloud resources, software and software licenses, developed code, databases, information, and knowledge.</p></td></tr></tbody></table>

This definition is intentionally subjective. The ITIL adage ‘adopt and adapt’ requires that organizational context be applied. Financial value could equate to the IT asset’s purchase or replacement cost, how it contributes directly or indirectly to value co-creation, the mission criticality of the service(s) that it underpins, how it is capitalized or depreciated according to financial practices, and/or any regulatory requirements that govern how an organization must document and report the presence and use of specific IT assets.

IT assets have a clearly defined lifecycle that consists of stages such as acquisition, assignment, decommission, and disposal. It is through this lifecycle that IT assets must be managed.

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p><span>The purpose of the IT asset management practice is to plan and manage the full lifecycle of all IT assets, to help the organization:</span></p><ul><li>maximize value obtained from the IT assets through products and services</li><li>control costs and optimize the total cost of ownership of IT assets</li><li>manage risks and reduce risk and vulnerability exposure associated with IT assets</li><li>support decision-making about the purchase, re-use, retirement, and disposal of IT assets</li><li>meet regulatory and contractual requirements.</li></ul></td></tr></tbody></table>

IT asset management presents an essential value proposition for both the service consuming organization and the service providing organization.

Benefits for the service provider include:

*   improved identification, tracking, and visibility of all IT assets
*   better monitoring and management of the lifecycle of all IT assets, including usage and maintenance
    
*   optimal utilization of IT assets, including enhanced negotiability with vendors and reduction in unnecessary purchases
    
*   increased compliance with legal and regulatory requirements by maintaining accurate records of all software licenses and ensuring that they are used in accordance with terms and conditions
    
*   mitigation of the risk of security breaches through the identification of vulnerabilities and ensuring that patches and updates are applied in a timely manner
    
*   accurate and timely information about IT assets to enable informed decisions about procurement, maintenance, and retirement
    
*   increased alignment of IT investments with evolving business objectives and needs
    
*   improved customer satisfaction and loyalty.
    

Benefits for the service consumer include:

*   improved reliability and fewer disruptions resulting from performance and utilization data that can help identify and address issues before they impact service quality
*   increased cost savings through license consolidation, optimized utilization, and reductions in unnecessary hardware and software purchases
*   reduced risk of compliance-related penalties and fines
*   reduced risk of security breaches and enhanced levels of protection for the organization’s data and infrastructure
*   enhanced productivity and profitability resulting from quicker and more effective responses to customer requests about asset availability and usage
*   improved communication and collaboration between the service provider and the service consumer.

### 2.2 Terms and concepts

#### 2.2.1 Interdependence between IT assets

ITAM should be integrated with the organization's general asset management. However, there is also interdependence within the practice and among IT asset types; for example, to properly record the number of software licenses that are consumed, it is worthwhile to:

*   conduct a software inventory across all relevant environments (development and integration, test, staging, live and production, and training) and platforms (such as on-premises hardware, cloud, data, and managed datacentres)
*   consider all deployment techniques (such as automation, DevOps, continuous deployment, machine cloning or imaging, software installation, and containers)
*   collect all parameters used in the licence model.

To be successful, ITAM specializations should not be planned or managed apart from the management of other types of the organization's assets, as shown in Figure 2.1.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_2.1.png)

Figure 2.1 Example of interdependence of IT assets

The ITAM specializations shown in Figure 2.1 can include:

*   hardware asset management
*   software asset management
*   cloud asset management
*   data asset management
*   Internet of Things (IoT) asset management.

Hardware asset management and software asset management have been part of the ITAM practice since its inception. In recent years, the demand for cloud platforms has significantly reduced the volume of licences deployed on physical machines and increased the share of the budget spent on public cloud service providers (CSPs). This fundamental shift involves integrating cloud services into the ITAM practice's scope to avoid a dramatic increase in cloud expenses and software noncompliance.

Data has become a valuable asset in every organization and should be considered both as a possible standalone IT asset and as an underpinning asset for all other types of IT assets. Important issues such as data standards and data security must be considered at all stages, from planning through to disposal.

#### 2.2.2 IT asset types

IT asset types may include:

● hardware, including physical:

*   end-user devices, such as personal computers, tablets, smartphones and SIM cards
*   network and telecom equipment, such as routers, switches, load balancers, and videoconferencing and voice over-the-Internet protocol systems
    
*   datacentre hardware, such as servers, storage and backup systems, and uninterruptible power supplies
    
*   significant peripherals, such as personal printers, monitors, scanners, and multifunction printing systems
    
*   security equipment and devices, including cameras and physical access technologies
    
*   business technology, such as IoT devices and industry-specific technology (such as ATMs in banking or PLCs in manufacturing), and audio or visual equipment.
    

● software running on hardware and virtual machines in all environments (development and integration, test, staging, live and production, and training), such as:

*   operating systems
*   middleware, such as web servers, SSL certificates, enterprise service buses, and database access services
    
*   personal and server applications.
    

● cloud services which are increasingly replacing hardware and some software (depending on the service model), including:

*   infrastructure as a service (IaaS)
*   platform as a service (PaaS)
    
*   software as a service (SaaS).
    

● code, whether created through traditional application development activities or used to instantiate or modify IT assets such as infrastructure as code (IaC), is a strategic technology investment and therefore could be treated as an IT asset

● data has become the most important IT asset in many organizations due to its role in daily operational and decision-making activities. The need to secure, control, and protect data, as well as include it in continuity and recovery planning, is fundamental.

Organizations experience the impacts of data leaks, cyber-attacks, and regulations about data (such as the European general data protection regulation). Therefore, to be in a better position to face these challenges, organizations may choose to manage information and data as IT assets. This can be done by:

● managing the IT assets that contain data

● applying ITAM procedures to this data to control its lifecycle.

#### 2.2.3 IT asset register

<table><tbody><tr><td><strong></strong><p><strong>Definition: IT asset register</strong></p></td></tr><tr><td><p>A collection of information about IT assets that includes their ownership, cost, and other key characteristics. The IT asset register makes it possible to quickly understand the lifecycle stage of all IT assets.</p></td></tr></tbody></table>

The ITAM practice requires accurate asset information that should be kept in an asset register. The IT asset register is the main source of the IT asset’s data, and is created when the ITAM approach is formed and updated regularly during the IT asset’s lifecycle.

The IT asset register data structure may include:

*   entities
*   attributes
*   relationships
*   naming standards
*   lifecycle stages
*   interfaces between the IT asset register and related tools
*   role-based access.

Because the IT asset register and the CMDB often have a significant degree of commonality, the ITAM and service configuration management practices frequently have a strong working relationship through collaborative activities and perhaps even shared resources.

The data structure of the IT asset register should consider efficient tracking, labelling, inventory, monitoring and reporting, integration, and data exchange with other practices, as well as data exchange and consolidation between functional departments.

This structure generally contains, but is not limited to, the following IT asset attributes.

*   device type
*   device name
*   owner, location, and/or assigned user
*   assignee contact information
*   brand or manufacturer
*   model number
*   serial number or service tag
*   asset tag or fixed asset number
*   operating system
*   basic specifications (CPU, memory, and storage)
*   licensed software
*   purchase date and/or cost
*   warranty term or length
*   maintenance and support agreement (servicer, term or length, contract number)
*   end-of-life or planned obsolescence term date (or year)
*   status
*   services
*   applicable legislation or regulations requiring compliance
*   comments or notes.

Asset tracking can be very technology-dependent. IT asset managers should consider the capabilities and constraints of an out-of-the-box data structure, the features of any existing IT asset register and ITSM tools, and the existing naming and recording conventions for the service configuration management, service financial management, and supplier management practices. These practices are consumers of the IT asset register data and should be consulted for tool choice, data structure, and reporting.

Reconciliation keys and data synchronization rules between data repositories are essential to enable trustworthy information while optimizing human workload. The data structure should also define media libraries and support for the hardware stores.

If the IT asset register is created from scratch, then existing data (such as spreadsheets) should be organized, normalized according to the new naming conventions, and uploaded to the register database.

To maintain the IT asset register, organizations periodically run audit checks covering all IT assets, including manual or semi-automated searches for equipment on the premises and verification of the IT asset stocks in hardware stores and definitive media libraries.

To keep the IT asset register current, procedures should be established to record acquired IT assets in the register. The data could be captured from the fixed IT asset register or the IT operational expenses list provided by the service financial management practice, IT asset purchase orders, suppliers’ invoices, and delivery or reception slips. The most efficient way of achieving this is to embed IT asset register updates into purchasing and procurement procedures. Recent advances in technology integrations have automated the link between the IT asset register and financial and procurement systems.

#### 2.2.4 IT asset lifecycle and lifecycle model

<table><tbody><tr><td><p><strong>Definition: IT asset lifecycle</strong></p></td></tr><tr><td><p>The various stages in the life of an IT asset, from planning to disposal. The lifecycle consists of stages represented by the statuses and the status transitions that are permitted, based on the IT asset type.</p></td></tr></tbody></table>

The IT asset goes through the following stages in its lifecycle:

*   planning and budgeting
*   acquisition
*   assignment (install, move, add, change (IMAC), including the related creation or modification of records in the IT asset register
*   utilization, optimization, and reporting
*   decommission and the modification or removal of records in the IT asset register
*   disposal.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_2.2.png)

Figure 2.2 The IT asset lifecycle

The IT asset lifecycle must not be defined as linear or unidirectional. Specific situations or scenarios with specific IT assets or IT asset types may determine that one or more stages may be skipped, repeated, or approached ‘out of sequence’, as shown in Figure 2.3. Some examples of IT asset lifecycle stages being non-linear include:

*   an IT asset with minimal cost and risk, or one that has been sufficiently planned previously requiring little to no planning and budgeting, reporting, or auditing
*   IT assets being reassigned multiple times throughout their useful life
*   a decommissioned IT asset being placed on legal hold for an extended period before it is disposed or reassigned.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_2.3.png)

Figure 2.3 Example of a non-linear IT asset lifecycle

##### 2.2.4.1 IT asset planning

The IT asset manager understands stakeholders’ needs and plans the best method of acquiring an asset based on the market and vendor data, price, security profile, and cost model. Asset acquisition occurs through purchase, upgrade, replacement, subscription, or leasing. IT asset planning enables budgeting and timing of the asset acquisition with procurement and finance. Comprehensive planning should consider how the IT asset will be acquired, installed, maintained, and utilized.

##### 2.2.4.2 IT asset acquisition

Acquisition is triggered by an approved request for procurement. The IT asset manager or appropriate delegate reviews the request and checks the availability of the asset. In cases of shortage, asset model substitution rules will be reviewed. If the asset cannot be provided, the acquisition procedure starts.

The role of the ITAM practice is to ensure the optimal use of the existing assets and that all documentation regarding the purchase is captured and stored. This includes asset-related contracts (such as licence, maintenance, warranty, and support), invoices, proof of purchase, entitlements, licence keys, and maintenance activation information. The documents may be stored in the organization’s financial system, the definitive media library (DML), or other secure location, with reference to the specific IT asset and its location in the IT asset register or content management database.

As a result of this stage, there should be a verified proof of software or hardware purchase, licence, entitlement, or service subscription, as well as a recorded IT asset with unique identification and other required information according to the agreed model in the IT asset register. Where applicable, the IT asset should have a recorded fixed asset tag that is cross-referenced in the IT asset register.

Like other practices, ITAM uses models to enable standardization in how assets are handled within the organization. Asset types should have defined and agreed models, so that the IT asset manager and all stakeholders understand how each asset is to be assigned.

Entitlements are the purchased rights or licences to use software. Software is not sold but is licensed for use, and this is considered an asset that is expensed or capitalized by the service financial management practice.

In addition to obtaining software through procurement, organizations may also acquire software through internal application development efforts. Advantages, such as tailoring to the organization’s specific needs, should be compared with any potential disadvantages like development time and costs versus licensing costs. Cost benefit analysis (CBA) could be a beneficial approach in this situation.

##### 2.2.4.3 IT asset assignment

<table><tbody><tr><td><p><strong>Definition: IT asset assignment</strong></p></td></tr><tr><td><p>The act of delegating some or all responsibility for an IT asset to an IT asset consumer for the period of IT asset consumption or use. For some types of IT assets, they can be combined with the relevant install, move, add, change (IMAC) actions.</p></td></tr></tbody></table>

IT asset assignment includes assigning actions to the IT asset, usually IMAC actions. Asset assignment is usually triggered by an approved request for asset assignment or a detected asset information gap. The person responsible checks that an available asset or eligible substitute is in stock, then follows the asset assignment procedures. It may be governed by rules for the movement of asset stocks, bring your own device (BYOD) policies, or practical guidance about the installation and use of assets to streamline costs and risks.

Asset assignments must be logged in the IT asset register. Capturing the IT asset information at this stage of the lifecycle is crucial, as it decreases the need for dedicated verification efforts such as running inventories and audits. Also, this stage provides the most monitoring data, which is used to enforce policies, ensure controls, and verify the IT asset register data. Frequently, a fixed asset tag is affixed to physical IT assets to ease verification and auditing.

##### 2.2.4.4 IT asset utilization, optimization, and reporting

Optimizing asset utilization requires understanding contracts and pricing models. This procedure includes:

*   adapting the stock of hardware and licenses to facilitate supplies according to SLAs
*   analysing IT asset characteristics and contracts and proposing practical guidance for optimal usage: for example, adapting the installation procedure for a database engine or a virtual machine to minimize license utilization, or charging for allocated assets (such as licenses, hardware, and cloud instances) by the month to encourage their decommissioning when they are not needed any more
*   monitoring utilization for cloud assets; cloud asset costs have many variables and models, such as pay as you go, or contractual discounts based upon usage volume
*   aligning IT asset contracts with SLAs, where possible: for example, an SLA for upstream support from the supplier or partner that provides an IT asset must align with the downstream commitment or expectation with the internal service consumer, or vice versa
*   tracking and assessing the potential impacts of changes to IT assets
*   collaborating with the service configuration management practice and others to define and track IT assets’ dependencies and be able to assess risks to the services that the change of IT asset might bring (for example, changes to related contracts, budgets, terms and conditions, license utilization, policies or regulations)
*   understanding the data and security requirements of each asset type as essential for optimization.

Monitoring provides information to support optimal utilization, such as periods of inactivity, trends in usage, licence capacity issues, billing trends, and any other aspects of IT asset utilization. As part of utilization management, ITAM practitioners should monitor and action IT asset key dates, such as end of contract or support, product or model obsolescence, and expiration dates in the IT asset register (such as licences, loans, SSL certificates, warranty, contract renewal, and true-up). Based on this monitoring, they can create requests for procurement, asset decommissioning, or asset assignment to the service request management or change enablement practices.

##### 2.2.4.5 IT asset decommissioning

<table><tbody><tr><td><p><strong>Definition: IT asset decommissioning</strong></p></td></tr><tr><td><p>The act of retrieving/recovering IT assets from a consumer, particularly through uninstallation (including deletion of data according to security policy) and deciding whether the IT assets should be returned to stock or disposed of.</p></td></tr></tbody></table>

IT assets are decommissioned based on the request from the service request management or change enablement practices. Other causes could include end of loan or asset reservation, obsolete or useless IT asset identified in an inventory, or a stolen/lost IT asset. Before decommissioning, the asset change impact must be assessed, the decommissioning condition must be verified with potential corrective actions, and a decision should be made on reusing or disposing of the asset.

The decommissioning should follow the policies and procedures defined in the lifecycle model.

While decommissioning, data should be handled according to the information security policy and licenses should be recovered for re-use when applicable. Finally, the IT asset register should be updated.

##### 2.2.4.6 IT asset disposal

<table><tbody><tr><td><p><strong>Definition: IT asset disposal</strong></p></td></tr><tr><td><p>The act of permanently removing an IT asset that is no longer in use in the organization in an appropriate and documented manner.</p></td></tr></tbody></table>

The formal disposal procedure could be carried out in many forms, depending on asset type and acquisition method. An asset can be sold, returned, given, or destroyed following the regulations (for example, e-waste).

During disposal, any contracts or licenses connected to the IT asset should be terminated, including maintenance contracts, and the IT asset register and relevant financial data should be updated. Definitive media library (DML) content connected solely to the asset could be archived.

##### 2.2.4.7 IT asset lifecycle models

Each stage of the lifecycle requires different support and control activities and different types of information, depending on the type of IT asset. IT asset types may serve as a basis for creating the IT asset management approach and models.

<table><tbody><tr><td><p><strong>Definition: IT asset lifecycle model</strong></p></td></tr><tr><td><p>A detailed description of the organization's approach to the management of the IT asset lifecycle tailored for a specific IT asset type.</p></td></tr></tbody></table>

Lifecycle models should define the processes, controls, and procedures for the IT assets handling based on the IT asset type.

Typically, each IT asset type is supported by a specialized IT asset lifecycle model. IT assets are grouped into types based on their features. This includes, but is not limited to:

*   reporting cycles
*   financial significance
*   level of tangibility (from tangible hardware equipment, to intangible licenses, cloud computing capacity, services or subscriptions, and so on)
*   location (for example physically on the premises, physically in co-location or on the provider’s premises, cloud resources, licenses on own servers, and so on)
*   level of immediate control (for example hardware boxes located on the premises or in a co-location space with restricted access, virtual servers administered by own personnel or by a third-party support team)
*   longevity and rate of depreciation
*   rate of change intrinsic to the IT asset and level of formality required for changes (for example, online application subscription with continuous deployment, operating system with a three-year release cycle, or a large UPS box or some sealed device provided by government agency)
*   type of IT asset acquisition (for example an application developed in-house, a licensed application tailored and implemented as a project, a ready-to-install a licensed application, a purchased hardware box, and so on)
*   inventory and record-keeping.

IT asset lifecycle models typically include:

*   IT asset stakeholder group
*   IT asset reporting cycle
*   services dependent on the IT asset
*   IT asset utilization optimization techniques and methods
*   controls and procedures for the IT asset lifecycle stages
*   IT asset monitoring methods and procedures
*   IT asset audit and inventory methods, controls, and procedures
*   IMAC procedures
*   IT asset decommission and disposal methods, controls, and procedures
*   shared support and maintenance procedures
*   shared legal and compliance regulations, policies, and controls
*   labelling and naming conventions.

For each model, a set of controls and procedures should be created to help support the lifecycle of any individual IT asset.

Activity implementation may vary depending on IT asset types. For example:

*   The disposal of software is subject to the license agreement while the disposal of hardware is subject to electronic waste regulations.
*   The disposal of hardware or a cloud service involves the secure deletion of data contained in it but is unlikely to involve software licenses.

#### 2.2.5 Verification and audit

To meet the needs of stakeholders, the ITAM practice ensures that IT asset information is both available and accurate to support informed decision making and conclusions.

ITAM ensures that the relevant IT assets’ data is captured in the IT asset register at each stage of the lifecycle. The practice should ensure that movement and changes in IT assets are captured as early as possible. To that end, IT asset movement record keeping should be automated where possible. Capturing the IT asset data improves the reliability of the IT register data and decreases, but does not eliminate, the need for verification.

<table><tbody><tr><td><p><strong>Definition: Verification</strong></p></td></tr><tr><td><p>An activity that ensures a new or changed IT service, process, plan, or other deliverable is complete, accurate, reliable, and matches its design specification.</p></td></tr></tbody></table>

In the ITAM practice, verification is a continuous activity of identifying and correcting the gaps and deviations between the IT asset register data and the actual IT infrastructure, or data from IT assets, inventory, or discovery. This is a continual process as the actual lifecycle status is dynamic and the verification ensures consistent integrity within the IT asset register.

There are many ways that the IT asset register is maintained. They usually include some methods of data collection and remediation.

<table><tbody><tr><td><p><strong>Definitions</strong></p></td></tr><tr><td><p>Inventory (noun): Assets available for assignment. As supplier management matures, inventory in-stock will decrease as organizations rely on suppliers to deliver assets on an as-needed basis. The increased use of cloud assets and the commonality of the distributed or hybrid workforce are accelerating this trend.</p></td></tr><tr><td><p>Inventory (verb): Data collection and clean up, performed as manual tasks, to build or verify the contents of the IT asset register.</p></td></tr><tr><td><p>Discovery: Data collection and clean up, achieved through automation technology and tools, to build or verify the contents of the IT asset register. Inventory and discovery produce the location and identification of IT assets that exist within the organization, particularly those that were previously undocumented or inadequately documented in the IT asset register. In addition, discovery may produce information about the IT assets’ technical characteristics and relationships.</p></td></tr></tbody></table>

Where available, discovery can be a superior method to initially populate the IT asset register, but it requires strict definition of the types of IT assets to probe and the specific information to capture. It is not, however, best practice to solely rely on discovery to maintain a comprehensive and accurate IT asset register. Verification of the IT asset register should ideally be performed through a combination of both inventory and discovery.

The IT asset register indicates what should be found, while audit and verification via inventory and discovery reveal what is found; this occurs during the verification stage of the IT asset lifecycle. Verification is the identification and remediation of gaps between what assets should be found and what assets are actually found.

Verification is often referred to as ‘reconciliation’. Such reconciliation may:

*   trigger an investigation concerning an unknown component found in the organization’s network
*   trigger an investigation concerning a known component that has experienced a change in its lifecycle status or other information required for management
*   help to identify and remove an unapproved software that the user has installed
*   help to identify software or cloud over-deployment
*   help to identify an IT asset that was probably stolen or lost.

Since the IT asset is the source of truth for many other practices, caution should be exercised when choosing to replace any contents of the IT asset register with inventory or discovery data. A misstep can lead to a total loss of control as valid data may be indelibly overwritten by incorrect data.

<table><tbody><tr><td><p><strong>Definition: Compliance</strong></p></td></tr><tr><td><p>The act of ensuring that a standard or set of guidelines is followed, or that proper, consistent accounting or other practices are being employed.</p></td></tr></tbody></table>

Most compliance activities rely heavily on valid IT asset information resulting from verification or remediation. Some examples may include compliance with software agreements, electronic waste and recycling regulations, financial regulations, data and security regulatory requirements, and security policies. Compliance activities must focus on organizational outcomes.

To ensure compliance, an organization can conduct regular internal and external audits.

<table><tbody><tr><td><p><strong>Definition: IT assets audit</strong></p></td></tr><tr><td><p>A planned, structured, and documented inspection of an organization's IT assets, including data collection, examination, verification, and correction activities that may be initiated and upheld by internal or external parties.</p></td></tr></tbody></table>

Auditing is one of the tools of the IT asset verification lifecycle stage. Verification is a continuous background activity, while an audit is a planned verification endeavour.

Verification and auditing should become an integral part of the ITAM practice to ensure that IT asset data is valid and available for the stakeholders.

### 2.3 Scope

For the chosen types of IT assets, The ITAM practice maintains and provides:

*   trustworthy data about what the organization has in order to be able to manage it
*   means for the appropriate handling of IT assets according to policies and regulations and in consideration of applicable costs and risks
*   IT asset lifecycle integration with other practices to achieve greater efficiency and cost-effectiveness.

The way in which organizations structure their products and services, the teams that manage them, and the governance of the organization will determine the scope of ITAM.

ITAM will include numerous activities and processes, ensuring they are fit for the purpose of contributing to a variety of the organization’s value streams. ITAM’s scope must also be flexible so that it can remain aligned with and in support of the organization’s dynamic vision, strategy, drivers, goals, and objectives. Adjustment of the scope of ITAM could be triggered by many factors, such as:

*   how value is calculated
*   regulatory changes
*   organizational financial policies and procedures
*   how components need to be managed.

Therefore, ITAM must reflect organizational scopes to define which assets are within the control of the practice. This helps identify the various business, technical, contractual, legal, regulatory, and compliance requirements to be considered. It also establishes the standards and policies that are critical for successful ITAM. In addition, scoping can introduce technologies useful for optimizing and automating ITAM.

Organizations need to consider the consequences of how they decide to scope their ITAM practices, because for the chosen types of IT assets, the ITAM practice maintains and provides:

*   trustworthy data about what the organization must support and manage
*   the means for the appropriate handling of IT assets according to policies and regulations, and in consideration of applicable costs and risks
*   understanding key aspects of asset decisions in areas such as sustainability and warranty
*   IT asset lifecycle integration with other practices to achieve greater efficiency and cost effectiveness
*   coordination with suppliers or partners that provide or manage specific assets or types of assets.

ITAM’s scope of control is not just defined by the IT asset types. It must also consider the value and the benefit received by managing them, weighed against the level of resource effort needed to do so effectively. There are several factors to consider when determining the proper scope of ITAM for an organization:

*   **Financial** Determine the value of IT assets in terms of a financial benefit and how to account for them in the organization’s financial documentation. Financial characteristics can include the minimal cost of IT assets and the amount of financial loss the organization would absorb should those IT assets be lost. This should also consider the need to manage the return on investment (ROI) of IT assets, the cost of services provided through the IT assets, and the total cost of ownership (TCO) of managing the entire lifecycle of the IT assets, which also includes potential fines and fees for not managing them appropriately. The financial benefits of ITAM are cost reduction, cost control, and cost avoidance.
*   **Security** There are many IT assets that fall below minimal costs for financial concerns that still need to be managed from a security or risk perspective. Data is an excellent example because it could be described as having more explicit functional value rather than financial. Proper management requires that the organization knows what it has and where it is located; therefore, the security vulnerability of the IT asset must be considered, which is especially important for mobile IT assets.
    
*   **Legal and compliance** These are dependent upon the regulations of the organization’s industry, local, and federal legal requirements, contractual obligations with providers of the IT assets, and audit requirements. They also include the organization’s own compliance requirements because all IT assets need to be managed in compliance with these regulatory requirements, regardless of the financial or security aspects.
    
*   **Service management** Since service management is about providing value through technology-based services, IT assets are at the core of this capability. Therefore, service management itself may have enabling requirements to be met through ITAM. ITAM also supports numerous service management practices including service financial management, information security management, risk management, service continuity management, and supplier management.
    
*   **Organizational** Larger organizations may only focus on one part of the organization and expand the scope of ITAM over time. Others may, for any number of reasons, determine that certain parts of the organization are out of scope. Some others may be segregated due to industry compliance requirements. Every organization possesses a unique configuration of IT products and services, using IT assets to facilitate desired valuable outcomes. The definition of scope can influence the quality or level of value of these outcomes.
    

When considering the scope of IT assets and ITAM, it is essential to recognize resource constraints. These constraints can be people resources, technical resources, and automation capability, funding resources, skills, or other initiatives competing for the same resources, and the commitment of leadership to build and sustain an effective practice. While an extensive and comprehensive ITAM scope is attractive, and perhaps intended, ultimately the value achieved will to be limited by these constraints. The level of derived value must be measured against the level of effort and resources required and utilized.

Several activities and areas of responsibility that are not included in the ITAM practice, although they are still closely related to ITAM. These are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending upon the situation.

#### Table 2.1 Activities related to the ITAM practice described in other practice guides

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Managing configuration item (CI) attributes and relationships in the configuration management database (CMDB)</p></td><td><p>Service configuration management</p></td></tr><tr><td><p>Budgeting, accounting, and analysing financial data of IT assets in the context of the products and services</p></td><td><p>Service financial management</p></td></tr><tr><td><ul><li>Sourcing and procuring of the IT assets</li><li>Managing vendor contracts</li><li>Evaluation, selection, and implementation of tools or services to support ITAM</li><li>Applying licence models from the supplier to manage software assets accordingly</li><li>Ensuring an understanding of the shared responsibility model with a cloud service provider (CSP)</li></ul></td><td><p>Supplier management</p></td></tr><tr><td><p>Fixing IT asset technical issues</p></td><td><p>Incident management</p></td></tr><tr><td><ul><li>Securing the access to IT asset data in the IT asset register, and to the definitive media libraries (DMLs) and hardware stores</li><li>Defining procedures to handle stolen or lost IT assets</li></ul></td><td><p>Information security management</p></td></tr><tr><td><ul><li>Installing and uninstalling IT assets according to practical guidance about the installation and use of IT assets</li><li>Using hardware stores and DMLs</li></ul></td><td><p>Deployment management</p></td></tr></tbody></table>

Overall, the complexities involved in defining, managing, and evolving the scope of the ITAM practice are primarily attributed to two factors: interdependence and implementation.

#### 2.3.1 Progressive scoping of the IT asset management practice

Organizations should formalize the ITAM practice as early as possible with whatever resources available, as it will be easier to keep the IT asset information current rather than to remediate it once the organization’s digital footprint becomes more complex.

Many organizations understand the importance of comprehensive ITAM only when they already have a large and diverse collection of IT assets and asset types. For these organizations, an iterative approach is recommended in line with the ITIL 4 guiding principles, particularly focus on value and progress iteratively with feedback.

The ISO/IEC 19770-1:20171 standard suggests a progressive three-tiered approach:

1.  obtaining trustworthy data about IT assets
2.  having an integrated management of their lifecycle
3.  optimizing efficiency and cost-effectiveness.

This suggestion means that the organization may choose to structure its ITAM practice as a set of modular capabilities to be gradually activated as it is scaled up with:

*   corresponding policies (applicable to all cases or to certain types of IT assets)
*   procedures, work instructions, and responsibility matrices
*   special recommendations attached to IT asset types (for example, the purchase of software licenses, which is different from the purchase of hardware).

The scope of the ITAM practice is generally too large for a ‘one shot’ or ‘big bang’ implementation. Therefore, according to the ‘Start where you are’ and ‘Progress iteratively with feedback’ guiding principles, it is advised to define the practice as a combination of the three categories as shown in the following example.

Below is an example of a progressive scope implementation for the ITAM practice. Keep in mind that it is best to focus on value and define a scope that considers the needs of stakeholders.

**Example of progressive scope implementation for the ITAM practice**

When implementing the ITAM practice, organizations should consider the following points for the scope of each implementation step

● **What** (IT assets to be managed):

*   software
*   hardware
*   cloud services
*   associated services, such as maintenance and support
*   corresponding IT and organizational asset data.

● **Where** (parts of the organization concerned):

*   countries, regions, and sites
*   business units, IT departments, service desk, procurement, and finance or accounting department
*   external service providers, such as contractors.

● **How** (process activities carried out with related policies and corresponding roles and responsibilities):

*   to acquire and maintain complete and accurate data
*   to achieve integration with other practices
*   to optimize IT asset-related costs and risks
*   to adapt to the dynamic needs of the organization.

The idea is to build on past achievements and move forward based upon the organization’s priorities. For example, an organization may plan to expand the scope of its ITAM practice in the following small increments:

● initial scope:

*   what: PC hardware
*   where: France
*   how: consolidated IT asset register between IT and finance with weekly data verification.

● first scope expansion:

*   what: PC hardware
*   where: Morocco
*   how: consolidated IT asset register between IT and finance with weekly data verification

● second scope expansion:

*   what: most common office software on PCs
*   where: first in France and then Morocco
*   how: consolidated IT asset register between IT, finance, and software vendors with weekly data verification.

● third scope expansion

*   what: PC hardware and most common office software
*   where: first in France and then in Morocco
*   how: management of the beginning and end of the IT asset life cycle (procurement and disposal) in collaboration with procurement and finance.

The scope increments should be chosen with a balance between the stakeholders’ needs and the effort of collecting, cleaning, standardizing, and migrating existing data, which can be resource-consuming.

IT asset lifecycle types and respective models could also serve as a scope expansion unit. An organization may start the IT asset management practice with a limited scope of two IT asset types (for example hardware devices and software licenses) and then expand the scope by adding other IT asset lifecycle models.

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>Whether the adoption of the ITAM practice in an organization follows a more common iterative and progressive approach, or a less likely ‘big bang’, it should be based on the needs of the organization and other stakeholders. The practice aims to help maximize value, control costs, manage risks, make decisions, and comply with requirements. Scoping and implementation decisions should be verified against these objectives first to prevent excessive and unjustified efforts and costs.</p></td></tr></tbody></table>

### 2.4 Practice success factors

<table><tbody><tr><td><p><strong>Definition: Practice success factor</strong></p></td></tr><tr><td><p><span>A complex functional component of a practice that is required for the practice to fulfil its purpose.</span></p></td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The ITAM practice includes the following PSFs:

*   ensuring that the organization has relevant information about its IT assets throughout their lifecycle
*   ensuring that the utilization of IT assets is continually monitored and optimized.

#### 2.4.1 Ensuring that the organization has relevant information about its IT assets throughout their lifecycle

The focus of the ITAM practice is accurate IT asset data: for example, ensuring that relevant IT asset information is captured, maintained, and provided to the stakeholders when needed. Based on stakeholders’ requirements for consistently reliable information, IT asset lifecycle models can be identified.

Lifecycle models define what information should be captured, recorded, and reported to the stakeholders at each stage of the IT asset lifecycle (see Table 2.2).

#### Table 2.2 Examples of information that should be captured for two IT asset types

<table><tbody><tr><td><p><strong>Lifecycle stage</strong></p></td><td><p><strong>Physical server</strong></p></td><td><p><strong>Software license</strong></p></td></tr><tr><td><p>IT asset planning and budgeting</p></td><td><ul><li>Manufacturer product and service catalogue with prices and cost models</li><li>Organization’s server hardware catalogue</li><li>End-of-support dates</li><li>Number and impact of the incidents caused by server models</li></ul><ul><li>Teams’ feedback about server models and related services</li><li>Manufacturer announcements (strategy, commercial roadmap, mergers and acquisition)</li><li>Consolidated forecast of demand from the organization about server hardware and related maintenance</li><li>Plan and budget for server acquisition, upgrade, and replacement, and for the subscription of related services, considering server software license plan</li></ul></td><td><ul><li>Publisher product and service catalogue with prices and cost models</li><li>Organization’s software asset catalogue</li><li>End-of-support dates</li><li>Hardware compatibility lists</li><li>Teams’ and users’ feedback about software products and related services</li><li>Publisher announcements (strategy, commercial roadmap, mergers and acquisitions)</li></ul><ul><li>Consolidated forecast of demand from the organization about software and related maintenance</li><li>Plan and budget for software license acquisition, upgrade, and replacement, and for the subscription of related services</li></ul></td><td></td></tr><tr><td><p>Acquire IT asset</p></td><td><ul><li>Purchase requirements and approved requests for procurement</li><li>Available servers and parts in hardware stores</li><li>Server model substitution rules in case of shortage</li><li>Rules governing the movement of hardware stocks</li><li>Purchase orders, invoices, and delivery/reception slips</li><li>Acquisition date</li><li>Recorded server with unique identification and other required information</li><li>Bar code, IT asset register ID, serial number, SKU code</li></ul><ul><li>Recorded expenses cross referenced with the corresponding server</li><li>Server owner</li><li>Dates to be monitored (end of leasing, renewal, end of warranty)</li><li>Server-related maintenance, warranty, and support contracts with service activation information</li></ul></td><td><ul><li>Purchase requirements and approved requests for procurement</li><li>Available licenses</li><li>License/product substitution rules in case of shortage</li><li>Rules governing licence transfers</li><li>Purchase orders, invoices, and delivery/reception slips</li><li>Recorded licenses with authenticated proofs of purchase, entitlements, license activation keys, software tag, SKU code</li><li>Acquisition date</li><li>Recorded expenses cross referenced with the corresponding licenses</li></ul><ul><li>License owner</li><li>Dates to be monitored (license expiration, true up, maintenance renewal, end of support)</li><li>Software product-related license and support contracts with service activation information</li></ul></td><td></td></tr><tr><td><p>Allocate/assign IT asset</p></td><td><ul><li>Organization’s server hardware catalogue</li><li>Available servers with hardware store locations</li><li>Server model specific policies (for example, Cloud options or regarding security)</li><li>Server/parts model substitutions and stock movements</li><li>Server-related approved changes</li><li>Related server CI</li><li>Approved hardware characteristics (CPU, memory, firmware,</li><li>Server custodian and assignee</li></ul><ul><li>Server location with local contacts</li><li>Date and operator of IMAC</li><li>Dates to be monitored (agreed upgrade, proactive maintenance, return to stock)</li></ul></td><td><ul><li>Organization’s software asset catalogue</li><li>Available licenses</li><li>License activation keys and installation media</li><li>Software-related policies (for example, about BYOD)</li><li>License/product substitutions and license transfers</li></ul><ul><li>Software-related approved changes and service requests</li><li>Practical guidance about optimal installation and use of software considering license models and contracts</li><li>Related software CI</li><li>License custodian and assignee</li><li>Characteristics used to calculate license utilization (technical configuration of the platform running the software, location, user information)</li></ul><ul><li>Date and operator of IMAC</li><li>Dates to be monitored (expected installation of booked licences, end of loan)</li></ul></td><td></td></tr><tr><td><p>Optimize IT asset utilization</p></td><td><ul><li>Measured or predicted system load reports</li><li>Report on actual server utilization compared to forecasts</li><li>Requests for change to optimize hardware value for money</li><li>Servers and spare parts stock rotation reports</li><li>Feedback regarding the value for money and adequacy of server-related services</li></ul></td><td><ul><li>Measured software usage reports</li><li>Detected breach records regarding practical guidance about software installation and use</li><li>Software compliance reports</li><li>Impact analysis of server changes on software license utilization</li><li>Requests for change/service requests to get back/substitute unused or underutilized licenses</li></ul></td><td></td></tr><tr><td><p>Decommission IT asset</p></td><td><ul><li>Decommissioning date and operator</li><li>Decision (return to stock, to be disposed, transferred)</li><li>Proof of handling according to policies</li></ul></td><td><ul><li>Detected unapproved installation/usage (software piracy, blacklisted product)</li><li>Decommissioning date and operator</li><li>Decision (return to stock, to be disposed, transferred)</li></ul></td><td></td></tr><tr><td><p>Dispose IT asset</p></td><td><ul><li>Disposal date and operator</li><li>Disposal reason (obsolete, out of order, damaged, stolen)</li><li>Decision (return to lessor, resale, destruction, donation)</li><li>Proof of destruction according to e-waste regulations</li></ul></td><td><ul><li>Disposal date and operator</li><li>Decision (resale, scrapping, donation)</li></ul></td><td></td></tr></tbody></table>

For some IT asset types, an organization may decide to include IT asset lifecycle management activities in the scope of this practice, such as procurement, stock management, or transportation. Alternatively, an organization may prefer to limit its scope of the practice to maintaining the IT asset register and leave the related physical activities in the scope of other practices, including the supplier management, infrastructure and platform management, and deployment management practices. Some IT assets should be documented throughout the entire lifecycle. For others it may be adequate to only document their acquisition, decommission, and disposal.

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>IT asset information should ‘focus on value’ by being relevant to the organization’s needs. There is no benefit to including all available data in an IT asset register that proves to be irrelevant or superfluous, or in blindly following examples from publications, vendors, or other organizations. The ITAM practice is only valuable so long as the information it provides is accurate, up to date, reliable, comprehensible, easy to use, and relevant. Even high-quality data is useless if it is not relevant to the organization’s needs. The careful selection of relevant data and optimal ways to maintain it is a key component of the organization’s ITAM approach.</p></td></tr></tbody></table>

##### 2.4.1.1 Managing all IT assets across their lifecycle in synergy with related practices

The activities of collecting, managing, and providing IT asset information are not performed in isolation. Contrary to that, most of the related activities are performed in the context of the organization’s value streams, with many other practices involved. Working in the context of a value stream, people often do not distinguish between the practices they apply.

Recommendations and procedures from the change enablement, IT asset management, and service configuration management practices can be used within one practical action, for example, relocating equipment. It is important to ensure that the relevant elements of the ITAM practice are included in the organization’s value streams and consistently applied in line with the organization’s approach to ITAM.

Following the ‘optimize and automate’ guiding principle, routine tasks (discovery, inventory, utilization, data gap analysis) should be optimized and automated to streamline workloads and IT asset utilization (underused IT assets are called sleeping stock).

In line with the ‘keep it simple and practical’ guiding principle, the practice should not be implemented as a bureaucratic control system. On the contrary, it should make everyday life easier for both consumers and the service provider's teams by providing them with adequate and valuable IT asset information in a convenient and useful form. This provision of information typically involves channels managed as part of other practices (including the supplier management, and service desk, and service catalogue management practices, among others). The effective integration of practices is essential for IT asset information consumers to have a positive experience.

##### 2.4.1.2 Ensuring that IT assets and related information are protected and compliant

Special effort should be made to ensure that the IT assets’ data is up-to-date, protected, and compliant with policies, laws and regulations, and agreements. Continual verification and periodic internal audits of IT assets should be performed to ensure that IT asset data meets the requirements. Internal verification and audits also help to minimize the financial, operational, psychological, and other impacts of external audits, especially when internal procedures follow the same or similar approaches.

The required evidence to demonstrate compliance of IT assets with contracts, regulations, and policies (notably security policies and regulatory controls) should be identified and documented.

The ITAM practice should help protect the organization from stolen, lost, or misused IT assets with, for example, secure stock facilities, quick detection of missing IT assets, practical guidance about the optimal way of handling, using, and disposing of IT assets.

#### 2.4.2 Ensuring that the utilization of IT assets is continually monitored and optimized

The ITAM practice is not only about keeping asset records; it should help to continually optimize asset utilization. This is possible when relevant information about asset utilization trends in the organization is combined with a good understanding of the industry development trends and associated risks and opportunities. Initiatives such as migration to the cloud are often triggered and always supported by IT asset information. Cloud migration utilizes hardware, software, and cloud asset management; seamless migrations are impossible without all three aspects working together.

Monitoring of IT asset utilization can help to optimize contracts with vendors and suppliers, decrease IT asset ownership and utilization costs, and improve the financial performance of the organization and its services. The early detection of unused or under-utilized IT assets, redundant contracts, and excessive license pools help to eliminate unnecessary spending and technical debt.

<table><tbody><tr><td><p><strong>Definition: Technical debt</strong></p></td></tr><tr><td><p>The total rework backlog accumulated by choosing workarounds instead of systemic solutions that would take longer.</p></td></tr></tbody></table>

Although technical debt is not uncommon, its consequences are often significant for a digital organization. Some examples of IT asset-related technical debt include:

*   servers that are beyond their planned obsolescence date, may not be covered by a maintenance agreement or contract, and may be running an obsolete or unsupported operating system
*   legacy applications, developed internally or purchased externally, that support critical business services
*   software tools used by different teams yet provide redundant or overlapping functionalities.

Technical debt is often considered and incurred due to the costs associated with maintaining and upgrading software and hardware systems that have become outdated or require significant resources to maintain or migrate. An organization’s resource constraints, competing objectives, and risk appetite frequently result in a decision to delay the proper replacement of IT assets.

Effective IT asset management can help reduce technical debt by providing organizations with greater visibility into their environments and better understand the costs associated with maintaining and upgrading their IT infrastructure. This allows organizations to identify areas where systems are outdated or require significant resources to maintain, allowing them to make more informed decisions about where and when to invest, prioritize, and allocate resources to update or replace those systems. As a result, organizations can avoid accumulating additional technical debt by investing in more sustainable and efficient IT systems.

Without proper management, technical debt will require an exponentially increasing amount of resources. In addition to hardware and software cost and risk, organizations should evaluate technical debt by considering the consumption of resources that are often overlooked:

*   people and the possible continuation of undocumented knowledge and obsolete skill sets instead of learning new and emerging methods, techniques, and technologies
*   data centre space, cooling, and electrical power needed to maintain physical IT assets that could be replaced with more efficient physical assets, as well as virtualized or cloud alternatives
*   increasing risk factors, including larger attack surfaces and new threat vectors and vulnerabilities due to a lack of security protocols, patches, and updates available for obsolete hardware and software.

By reducing technical debt, organizations can avoid costly system failures and downtime, improve overall system performance, and enhance their ability to meet the evolving needs of the organization by applying resources to strategic goals and objectives instead of maintaining IT asset ‘status quo’. To achieve this, ITAM should ideally collaborate with other practices such as service financial management, information security management, and risk management.

IT asset utilization monitoring is based on data collected and analysed in conjunction with other practices, including the monitoring and event management, service financial management, service configuration management, service level management, and supplier management practices, among others.

ITAM specialists should regularly monitor the evolution of technology solutions (hardware, software, cloud, Internet of Things, and so on) and review the ITAM approach to mitigate risks and leverage the opportunities. Relevant information can come from vendors (product catalogues, standard contracts, strategy announcement, product obsolescence, mergers and acquisitions), or many other sources, such as press articles, white papers, market analysis, professional forums, and conferences. IT asset managers should discuss findings with peers and experts to understand the consequences and plan actions to take advantage of developments or avoid adverse consequences by negotiating, changing policies, or evolving the IT asset catalogue.

### 2.5 Key metrics

The effectiveness and performance of ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of their application. However, tools can differ greatly in design and quality and these differences define a tool’s potential or capability to be effective when used according to its purpose. Further guidance on metrics, key performance indicators (KPIs), and other techniques that can help with this can be found in the measurement and reporting practice guide.

Key metrics for the ITAM practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of this are given in Table 2.3.

#### Table 2.3 Examples of key metrics for the practice success factors

<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Ensuring that the organization has relevant information about its IT assets throughout their lifecycle</p></td><td><li>Stakeholder satisfaction with IT asset information</li><li>Number and impact of audit findings and non-compliances</li><li>Number and percentage of requirements for IT asset information that have not been fulfilled</li><li>Percentage of actual ITAM coverage compared to the amount planned/agreed in the organization’s ITAM approach</li></td></tr><tr><td><li>Ensuring that the utilization of IT assets is continually monitored and optimized</li></td><td><li>Dynamics of the IT asset financial performance (return of investment, value on investment, total cost of ownership)</li><li>Number and economic effect of utilization improvement recommendations implemented based on ITAM analytics</li><li>Percentage of the controlled IT assets for which utilization is monitored and analysed</li></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the ITAM practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as the goals of the value streams to which the practice contributes.

## 3. Value streams and processes

### 3.1 Processes

Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><p><strong></strong><span><strong>Definition: Process</strong></span><strong></strong></p></td></tr><tr><td><p><span>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one of more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</span></p></td></tr></tbody></table>

ITAM activities form three processes:

*   managing a common approach to ITAM
*   managing the IT asset lifecycle and records
*   verifying, auditing, and analysing IT assets.

#### 3.1.1 Managing a common approach to IT asset management

This process is focused on ensuring different elements of the organization adopt a common approach to ITAM. This supports value co-creation by enabling efficient and effective communication of outputs relating to ITAM across the organization, and making it easier for all parts of the organization to ensure they are in compliance with both internal and external requirements.

Managing a common ITAM approach includes the activities listed in Table 3.1, which transform the given inputs into outputs. These outputs become the outcomes for stakeholders as they realize value. This particular ITAM process emphasizes the ITIL 4 guiding principle of focusing on value.

#### Table 3.1 Inputs, activities, and outputs of the managing a common approach to ITAM process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>IT strategy and plans</li><li>List of prioritized IT services</li><li>Risk registers</li><li>Industry and vendor trends</li><li>Organization policies and external compliance requirements</li><li>ITAM and IT service management tool out-of-the-box features</li><li>Recognized international ITAM standards and best practices</li><li>Existing IT asset data<br></li></ul></td><td><ul><li>Analyse stakeholders' requirements and IT asset risks</li><li>Define and agree the ITAM approach</li><li>Communicate and integrate the ITAM approach into the organization's value streams</li><li>Review and adjust the ITAM approach and procedures</li></ul></td><td><ul><li>ITAM approach</li><li>IT asset register</li><li>ITAM communications and knowledge management materials</li><li>Requests for changes and implementation initiatives</li><li>ITAM approach performance reports</li></ul></td></tr></tbody></table>

Figure 3.1 shows a workflow diagram of the process.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_3.1.png)

Figure 3.1 Workflow of the managing a common approach to ITAM process

Details of the activities of the process of managing a common approach to ITAM are outlined in Table 3.2.

#### Table 3.2 Activities of the managing a common approach to ITAM process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Example</strong></p></td></tr><tr><td><p>Analyse stakeholders' requirements and IT asset risks</p></td><td><ul><li>Stakeholders in ITAM should analyse and map major hardware, software, cloud IT assets and related service expenses, IT strategy and plans (infrastructure, applications, service delivery, and so on) that are aligned with the organization’s plans, vendor trends and practices (e.g. software publishers' compliance audits, move to the cloud), and industry trends (e.g. in hardware, software, and cloud markets).</li></ul><ul><li>As a result of analysis and mapping, the most significant risks and opportunities (financial, legal, and technical) are identified and mapped with the associated types of IT assets. Appropriate proactive and reactive actions are defined, prioritized and drafted as part of the ITAM approach.</li><li>Organizations should also conduct questionnaires/surveys, workshops, interviews with ITAM stakeholders (both internal and external to the organization) with their areas of interest (e.g. cost control, security, operational efficiency) to form a categorized and prioritized list of requirements for ITAM, aligned with the risk and opportunity register from the previous step.</li></ul></td></tr><tr><td><p>Define and agree the ITAM approach, scope, data structure, and lifecycle models</p></td><td><p>Based on the results from the previous activity, stakeholders should define and agree the ITAM approach.</p><p>The approach defines the following:</p><ul><li>how critical ITAM is for the organization and stakeholders</li><li>the type of information and level of detail on the IT assets needed by stakeholders</li><li>the amount of resources the organization is ready to invest into ITAM</li><li>the amount of information to be captured and updated</li><li>how detailed the policies and procedures are</li><li>how (and if) the ITAM scope will expand</li><li>what organizational structures will support ITAM</li><li>how the IT assets tracking is organized</li><li>how often inventory is run for different groups of IT assets.</li></ul><p>The approach can be based on any of the recognized standards for ITAM, such as ISO/IEC 19770-1.</p><p>The approach typically includes:</p><ul><li>descriptions of the desired state of the ITAM practice</li><li>lists of prioritized IT asset types to be included in the scope</li><li>descriptions of the required reports, supporting information, and data captured for the IT assets</li><li>IT asset data structure and lifecycle models</li><li>IT asset policies and controls</li><li>IT asset monitoring and control procedures</li><li>IT asset verification, audit, and analysis principles and procedures</li><li>lists of technology and tools used for the ITAM practice and automation.</li></ul></td></tr><tr><td></td><td><p>Data structures used for ITAM should accommodate the continual changes in the approach and scope. The ITAM data structure is usually the structure of the IT asset register. Data structures may include entities, attributes, relationships, naming standards, lifecycle stages, interfaces between the IT asset register and related tools, role-based access, and so on. Data structures should consider efficient tracking, labelling, inventory, monitoring and reporting, integration and data exchange with other practices, and data exchange and consolidation between functional departments.</p></td></tr><tr><td></td><td><p>As part of the data structure definition, the IT asset register should be created (see section 2.2.4).</p></td></tr><tr><td></td><td><p>Based on the types of IT assets defined in the approach, lifecycle models should be defined and agreed. Each lifecycle model should define controls and procedures to support the stages in the IT asset lifecycle.</p></td></tr><tr><td></td><td><p>Lifecycle models may have different legislation and regulations to comply with, so it may differ in policies and controls.</p></td></tr><tr><td></td><td><p>The IT asset manager and involved stakeholders should define and agree ITAM policies and guidelines. They should be clear, useful, easy to apply, and supported by relevant controls, including automation.</p></td></tr><tr><td></td><td><p>Another important consideration is the alignment between ITAM policies and suppliers contracts. This is ensured in conjunction with the supplier management practice.</p></td></tr><tr><td></td><td><p><span>Examples of controls and procedures for the lifecycle stages are given in section 2.2.4.</span></p></td></tr><tr><td></td><td><p>Stakeholders should define and agree the ITAM events to be monitored, with appropriate responses, to act as an input into the monitoring and event management practice. The main focus of IT asset monitoring should be any deviations from the established controls and policies and changes in the IT asset status. Monitoring is the most important source of data for the IT asset verification. Monitoring should be automated wherever possible. Automation tools used for monitoring could also be used for some types of audits.</p></td></tr><tr><td></td><td><p>Monitoring should be defined to accompany IT assets in each stage of their lifecycle.</p></td></tr><tr><td></td><td><p><span>ITAM stakeholders should agree how the verification, audit, and analysis works for the IT assets.</span></p></td></tr><tr><td><p>Communicate and integrate the ITAM approach into the organization's value streams</p></td><td><ul><li>The defined, agreed, or updated approach, scope, lifecycle models, and procedures are communicated and discussed with the ITAM stakeholders across the organization. Stakeholders may decide the level of formality for the training on the ITAM controls and procedures. For the people involved in the supplier management daily, policies and controls may be created for a formal training as a prerequisite and periodic awareness trainings.</li><li>Some ITAM concepts deserve an effort of popularization and practical guidance to let the organization benefit from them, this includes software licenses, cloud service agreements, manufacturer's warranties, maintenance and support, and so on.</li></ul><ul><li>Implementation of the ITAM approach is carried out in conjunction with the configuration management, supplier management, change enablement, project management, organizational change management, workforce and talent management, and relationship management practices, among others.</li><li>Communication plays an important part in integrating and embedding the ITAM approach and procedures into the wider organization. IT asset managers may choose to communicate across the organization about the ITAM approach, scope plans, implementation status, improvements based on ITAM analysis, compliance audit results, and so on. For maximum benefit, they should identify appropriate timing, content, and methods for target audiences and enable easy feedback loops.</li></ul><ul><li>External communications on the ITAM procedures and controls, IT asset data requirements, and IT asset compliance controls should be prepared and published in the suppliers and partners information channels.</li></ul></td></tr><tr><td><p>Review and adjust the ITAM approach and procedures</p></td><td><p>ITAM stakeholders monitor and review the adoption, compliance, and effectiveness of the agreed ITAM approach and procedures; this is done on an event-based (IT asset-related incidents, IT asset monitoring events, compliance issues, and so on) and interval-based basis. The main input for these reviews should come from participants in the managing IT asset records process.</p><p>Adapting the approach to specific requirements can improve it or jeopardize its viability. Therefore, review participants should:</p><ul><li>check the compatibility of specific requirements with ITAM policies and internal and external regulations</li><li>evaluate the impact of the specific requirements in the four dimensions of service management (IT asset management data model and tool setup; contracts with suppliers/partners/customers; processes/procedures/work instructions; organization, team structure, people’s habits and corporate culture, and so on)</li><li>categorize the technical tools and automation implementations to be performed to meet the specific requirements (supporting out of the box, simple configuration, complex configuration, or specific development)</li><li>evaluate the potential solutions in terms of cost, benefit, and risk.</li></ul><p>Results, findings, and initiatives are used as input for continual improvement for the ITAM practice.</p></td></tr></tbody></table>

#### 3.2.1 Managing the IT asset lifecycle and records

This process is concerned with managing the organization's IT asset lifecycle. It is important that the IT asset lifecycle is properly managed to ensure that IT assets are being utilized effectively.

This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

#### Table 3.3 Inputs, activities, and outputs of the managing the IT asset lifecycle and records process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>IT asset management approach, scope, controls, procedures, and lifecycle models</li><li>IT asset register</li><li>Risk registers</li><li>Industry and vendor trends</li><li>IT asset monitoring reports</li><li>ITAM and IT service management tool</li></ul></td><td><ul><li>Analyse resources and identify IT assets</li><li>Verify IT assets and lifecycle models</li><li>Follow the lifecycle model</li><li>Manage exceptions</li><li>Review the lifecycle</li></ul></td><td><ul><li>Updated IT asset register</li><li>IT asset utilization optimization initiatives</li><li>Exception reports</li><li>IT asset lifecycle reports</li></ul></td></tr></tbody></table>

Figure 3.2 shows a workflow diagram of the process.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_3.2.png)

Figure 3.2 Workflow of the managing the IT asset lifecycle and records process

Details of the activities of the process of managing the IT asset lifecycle and records are outline in Table 3.4.

#### Table 3.4 Activities of the managing the IT asset lifecycle and records process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description and recommendations</strong></p></td></tr><tr><td><p>Analyse resources and identify IT assets</p></td><td><p>Upon request for a new IT asset, discovery of a new IT asset, or a change in the existing IT asset, the person responsible for the IT asset identifies the type of asset and checks if the type is in the scope of the ITAM practice. If it is, a respective IT asset lifecycle model is identified to follow.</p></td></tr><tr><td><p>Verify IT assets and lifecycle models</p></td><td><p>The IT asset manager reviews the selected IT asset type and lifecycle model and confirms that it is suitable for the asset.</p></td></tr><tr><td><p>Follow the lifecycle model</p></td><td><p>The IT asset manager and/or any member of the team responsible for the IT asset follows the selected model. This typically includes, with small variations depending on the starting point of the lifecycle in the case, the following:</p><ul><li>capturing and updating the IT asset data in the IT asset register at each stage of the lifecycle</li><li>monitoring an IT asset, enforcing controls, and analysing the IT asset monitoring data among relevant IT assets</li><li>ensuring ongoing IT asset register data verification and including the IT asset in the relevant IT asset audits</li><li>ensuring compliance at each stage of the IT asset lifecycle</li><li>providing up-to-date IT asset information and reports to all stakeholders, for value maximization, cost reduction, risk management, and decision making.</li></ul></td></tr><tr><td><p>Manage exceptions</p></td><td><p>If an exception occurs during the IT asset lifecycle, the IT asset manager and the team responsible handle it in line with the organization’s ITAM approach, compliance regulations, values, and established practices.Deviation from the procedures should be taken with care, ensuring compliance and maintaining controls.</p><p>Exceptions should be documented and reviewed for possible approach, scope, and lifecycle model changes, future references, and lessons learnt.</p></td></tr><tr><td><p>Review the lifecycle</p></td><td><p>Upon significant exceptions, or regularly, the IT asset manager and the team responsible should review the IT asset lifecycle models to confirm or update them based on the collected feedback, reviewed requirements, IT asset records, audit reports, and new risks and opportunities.</p></td></tr></tbody></table>

#### 3.1.3 Verifying, auditing, and analysing IT assets

Valuable stakeholder outcomes rely on accurate asset information to be readily available, secure, and consumable. Audit and verification focus on evaluating and comparing IT assets that are expected with IT assets that are found to exist. This process includes the activities shown in Table 3.5 and transforms the inputs into outputs.

#### Table 3.5 Inputs, activities, and outputs of the verifying, auditing, and analysing IT assets process

<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>ITAM approach</li><li>IT asset register</li><li>Reports from monitoring IT assets</li><li>IT asset risk registers</li><li>Internal and external compliance regulations</li></ul></td><td><ul><li>Plan audit</li><li>Collect IT asset data</li><li>Verify IT asset data</li><li>Review and analyse verification and audit outputs</li><li>Compose and communicate verification and audit reports</li></ul></td><td><ul><li>Updated IT asset register</li><li>IT asset audit reports</li><li>IT asset approach feedback</li><li>Updated IT asset risk register</li><li>Request for change</li></ul></td></tr></tbody></table>

Figure 3.3 shows a workflow diagram of the process.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_3.3.png)

Figure 3.3 Workflow for the verifying, auditing, and analysing IT assets process

Verification can be an ongoing activity of verifying and correcting the IT asset data. To achieve this, the ITAM practice should embed verification activities and controls into other practices’ procedures. For example, a support specialist can do a quick verification of a user’s desktop information using the content of the IT asset register, or an accountant can spot and report a discrepancy between IT asset data and financial data.

Also, the need for a dedicated verification effort decreases if the IT asset data is properly captured and verified along the IT asset lifecycle. Therefore, like monitoring, verification should be integrated into the IT asset lifecycle, with relevant procedures for each lifecycle stage.

Along with the constant verification activities, ITAM practitioners may need to run audits as a focused verification activity. The scope and frequency of the audits should be defined and agreed in the IT asset audit procedures:

*   audit of existing IT assets at planned and random intervals
*   audit of assets acquisition at planned and random intervals
*   audit of IT asset-related media at planned and random intervals
*   analysis and assessment of license compliance
*   vendor compliance audits.

Corrective actions based on the audit results should be addressed in the audit follow-up procedures to identify and correct IT asset data gaps.

Audit results should be used for analysing IT assets. Audit results should be formatted to allow ITAM practitioners to analyse IT asset utilization and total cost of ownership and propose changes to the overall ITAM approach, as well as the IT asset lifecycle models.

Details of the activities of the process of verifying, auditing and analysing IT assets are outlined in Table 3.6.

#### Table 3.6 Activities of the verifying, auditing, and analysing IT assets process

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Plan audit</p></td><td><p>Audits can be planned in response to some detection of unauthorized or unregistered IT assets, before or after significant technical or organizational changes, before any important milestone with a manufacturer or a software vendor, or at a planned interval.</p><p>The frequency or scope of audits should be adjusted after considering the financial stakes, risks, and detected errors. Audits should be planned where and when the most significant discrepancies could be discovered and before they penalize the organization. Automation can help increase audit frequency and scope.</p><p>Plans should exist to:</p><ul><li>run internal audits</li><li>predict the likelihood of external audits (for example software compliance) and manage them when they occur.</li></ul><p>Audit plans usually include the following:</p><ul><li>a timeframe and schedule</li><li>the IT assets and organizational units in scope of the audit, for example, considering the results of previous audits or to prepare for a probable external audit</li><li>the discovery and inventory tools and techniques used</li><li>the methods of reconciliation and verification used</li><li>the controls and compliance regulations to be checked</li><li>the reporting and communication plan</li><li>the post-audit actions to deal with detected issues, avoid their recurrence, and improve future audits.</li></ul></td></tr><tr><td><p>Collect IT asset data</p></td><td><p>Most IT asset data is collected by discovering, inventorying, and monitoring automated tools to enable comparison with the IT asset register. In special situations, discovery and inventory are run manually where automated discovery is not possible or financially viable.</p><p>The audit should verify that the assets listed in the IT asset register exist. Any discovered IT assets should be checked for the IT asset register records. This requires that collected data covers:</p><ul><li>the acquired assets and subscribed contracts identified such as procurement, finance, supplier management, resellers, software publishers, manufacturers, and so on</li><li>existing assets in all environments (not only production ones).</li></ul><p>Audit should verify that the description and technical characteristics of the assets are correct so the format of the data collection will be as close as possible to the data model of the IT asset register to enable industrial reconciliation. Therefore, data collection generally includes clean-up and normalization.</p><p>Data collection should also cover important media associated with IT assets:</p><ul><li>contractual documents (contract, proof of purchase or subscription, delivery slip, invoice, certificate of destruction in compliance with electronic waste regulations, and so on)</li><li>installation media (DVD, installation package, license activation key, and so on)</li><li>practical documentation (installation procedure, administration guide, maintenance activation contacts and instructions, vendor extranet, and so on).</li></ul><p>Similarly to other IT asset data, the media data collection should be automated as much as possible (digital contracts and other media), but it often requires manual work (physical media such as printed documents, DVDs, and so on).</p></td></tr><tr><td><p>Verify IT asset data</p></td><td><p>The last verification and audit date should be saved with the asset records to facilitate the scheduling of future audits. Any discrepancies found in the audit must be investigated and corrected, such as:</p><ul><li>IT asset records that do not match the corresponding IT asset present in the infrastructure</li><li>discovered IT assets that do not exist in the IT asset register</li><li>unauthorized IT assets</li><li>missing or existing but unregistered IT asset-related media</li><li>incorrect IT asset-related media (such as a license entitlement granted to the wrong organization, false proof of purchase, and so on).</li></ul><p>The correction of discrepancies may imply many types of actions, such as the removal of the unauthorized IT assets, the regularization of unregistered acts (acquisition, assignment, decommissioning, disposal, and so on), claims against suppliers, archiving of obsolete data, creation of a security incident record if a device appears as stolen or lost, and so on.</p></td></tr><tr><td><p>Review and analyse verification and audit findings</p></td><td><p>Results of the audit and verification should be reviewed to drive improvements and to prepare future audits.</p><p>Audit data should be used for the analysis of risks, compliance assessment, costs optimization, general trends in the IT assets utilization, and ITAM approach adoption. The risk register should be reviewed for the IT assets in the scope of the audit.</p><p>This activity may initiate many improvement techniques, some of which may require post-audit follow-up. For example:</p><ul><li>automation of repetitive tasks to avoid human error or reduce the workload of ITAM practitioners</li><li>simplification of ITAM solutions to increase their adoption</li><li>better operational integration of ITAM activities in value streams to reduce process misalignment and enable seamless customer experience</li><li>optimization of the IT asset register structure to secure the provision of the most important data</li><li>restocking the hardware stores and media libraries</li><li>education, penalties, and management awareness</li><li>recommendations for the next audits.</li></ul></td></tr><tr><td><p>Compose and communicate verification and audit reports</p></td><td><p>Based on the results of the review and analysis of verification and audit outputs, the audit report should be:</p><ul><li>formalized with concerned stakeholders to ensure they all understand and agree</li><li>distributed through the agreed communication channels</li><li>safely stored to enable future reuse for feedback or as a baseline.</li></ul><p>The owner of post-audit actions should be appointed with enough time, means and authority in order to enable achievement of approved actions, and escalation in case of difficulty.</p></td></tr></tbody></table>

### 3.2 Value stream contribution

#### 3.2.1 Service value streams

To perform certain tasks or respond to situations, organizations create service value streams. These are specific combinations of activities and practices, and each one is designed for a particular scenario.

Once designed, value streams should be subject to continual improvement.

<table><tbody><tr><td><p><strong>Definition: Value stream</strong></p></td></tr><tr><td><p>A series of steps an organization undertakes to create and deliver products and services to consumers.</p></td></tr></tbody></table>

In practice, however, many organizations apply the value stream concept after having worked for a significant span of time, sometimes for years, without value streams being managed, mapped, or understood. This means that when the importance of the concept becomes clear, the first step is to understand and map the current state or situation, and the typical flows of work, and to analyse them to identify and eliminate the non-value-adding activities and other forms of waste.

Identifying and understanding existing value streams is critical to improving organizational performance. Structuring the organization’s activities in the form of value streams allows it to have a clear picture of what it delivers and how, and to make continual improvements to its services. When combined, the organization’s value streams form an operating model which can be used to understand and improve how the organization creates value for the stakeholders.

Many organizations have been following best practice recommendations for various service management practices, such as IT asset management, service request management, incident management, change enablement, software development, and many others. IT asset management is one of the most adopted and mature practices because many organizations often formalize it early in their ITSM journey.

However, the practices have often been adopted and organized in a siloed, isolated manner: just as they were presented in the service management bodies of knowledge. In reality, a flow of work required to facilitate or enable value for a customer or other stakeholder is almost never limited to just as single practice.

#### 3.2.2 IT asset management in service value streams

Although ITAM plays a supporting role in the service provider’s service value streams, this role is extremely important. Many practices rely on IT asset information to achieve their purposes.

Table 3.7 describes how the key service value streams involve IT asset management.

#### Table 3.7 IT asset management in key service value streams

<table><tbody><tr><td><p><strong>Value stream</strong></p></td><td><p><strong>The role of IT asset information</strong></p></td></tr><tr><td><p>Creation of a new or changed product or service</p></td><td><ul><li>Assessment of the impact of the new requirements on the cost and compliance of the current services</li></ul><ul><li>Identification of the scope of required procurement, licensing, and other changes to the organization’s assets</li><li>Control and verification of the implementation of the approved changes to organization’s IT assets throughout the change lifecycle</li><li>Optimization of utilization of the IT assets with minimum impact on the live service performance and user experience</li></ul></td></tr><tr><td><p>Incident resolution</p></td><td><ul><li>Impact assessment during incident classification, including financial impact, compliance, and other aspects of the IT assets</li><li>Planning and control of the changes to IT assets required for incident resolution</li><li>Verification of the changes to IT assets made to resolve an incident</li></ul></td></tr><tr><td><p>Service request fulfilment</p></td><td><ul><li>Planning and control of the changes to IT assets required to fulfil a request</li><li>Verification of the changes to IT assets required to fulfil a request</li></ul></td></tr><tr><td><p>Ongoing operation and maintenance</p></td><td><ul><li>Detection of unauthorized changes to IT assets</li><li>Assessment events’ impact on IT assets</li><li>Assessment of impact of proposed and scheduled actions and changes on IT assets</li></ul></td></tr><tr><td><p>Continual improvement of products and services</p></td><td><ul><li>Optimization of the capacity, performance, availability, and continuity assessment and planning</li><li>Optimization of the information security assessment and planning</li><li>Support of service cost allocation, planning, and optimization</li></ul></td></tr></tbody></table>

For all value streams, the IT asset management practice provides IT asset information via the IT asset register either by maintaining it on an ongoing basis, or by gathering and publishing it on demand. It is unusual to see activities of IT asset management in the core workflow of a value stream, but many of the core activities use IT asset information. The effectiveness and efficiency of some of the value stream activities (such as impact assessment and change planning) are highly dependent on the availability and quality of IT asset information. This makes the IT asset management practice critical for many service value streams.

#### 3.2.3 Analysing a service value stream

The following are some simple and practical recommendations for service value stream analysis and mapping:

1.  **Identify the scope of the value stream analysis**  
    Service value streams can be mapped to a particular product or service or applied to most or all of them. Similarly, service value streams may differ for different consumers. For example, a service provider has different access to information about the IT assets they own, the IT assets they use as a service, and the IT assets that belong to the service consumers.
    
2.  **Define the purpose of the value stream from the business viewpoint**  
    Since stakeholders define value, it is essential that their concerns are clearly understood. In the case of IT asset management, these are usually service provider teams who require IT asset information. However, this information may also be useful for third parties involved in the management of the organization’s services. The outcomes of service value streams should be understood from the business perspective, not solely from the user perspective.
    
3.  **Walk the service value stream**  
    Consider the Lean technique of a Gemba walk. Logically walk through or directly experience the steps and the information flow as they occur in practice:
    

**a.** **Identify the workflow steps**

**b. Collect data as you walk**

**c. Evaluate the workflow steps**

Typically, the criteria for evaluation are:

*   value for the stakeholder (does the step add value for the business stakeholder?)
*   effectiveness or performance (is the step performed well?)
*   availability (are required resources available to execute the step?)
*   capacity (are required resources adequate?)
*   flexibility (are the required resources interchangeable within the step?).

**d. Map the activities and the information flows**

In an ideal situation, the flow proceeds smoothly without delays or pauses, there are no disconnections between the steps, and the workload is level with minimal (and agreed) variation.

**e. Create and review the timeline and resource level**

Map out process times and lead times for resources and workload through the workflow steps.

4**. Reflect on the value stream map (VSM)**

Identify factors that might not have been entirely apparent at first. The information previously collected is now used at this step to find waste.

5**. Create a ‘to be’ VSM**

This informs and drives improvement. The value stream should be considered holistically to ensure end-to-end efficiency and value creation, not just local improvements.

6**. Using the ‘to be’ VSM, plan improvements**

Refer to the continual improvement practice guide for a practical improvement model.

To ensure that relevant IT asset management activities are included in service value streams, the following steps can be added to the above recommendations:

During scoping (task 1), identify the IT and business services related to the value stream and the involved business stakeholders. Are they in the scope of IT asset management, and to what extent? What IT asset information may be relevant for the stakeholders?

Make sure the value stream is understood (task 2) from the perspective of the business, not only of the service provider.

*   During the service value stream walk (task 3a), identify the practices involved at every step and the IT asset information they use. What IT asset information which they may need is readily available? Is there a chance that ad-hoc IT asset analysis will be needed? Are there third parties involved in the value stream? If so, what IT asset information might they need? Can this information be shared with them, and what are the applicable information security policies?
*   During the evaluation of the workflow steps (task 3c), consider the impact of IT asset information on the effectiveness and efficiency of the value stream. Special attention should be paid to steps with low business value, low performance, and availability or capacity issues. Does IT asset management create any delays? Is the IT asset information sufficient? Is it provided in a timely and convenient way?
*   At the reflection and planning steps (tasks 4-5), ensure that the IT asset information is available throughout the value stream and its provision and use are optimized for business value.
*   Include the creation or update of IT asset lifecycle models and other elements of the IT asset management approach in the value stream improvement plans (task 6).

## 4. Organizations and people

### 4.1 Roles, competencies, and responsibilities

The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

#### Table 4.1 Competency codes and profiles

<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p>L</p></td><td><p><u>Leader</u> Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes.</p></td></tr><tr><td><p>А</p></td><td><p><u>Administrator</u> Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements.</p></td></tr><tr><td><p>C</p></td><td><p><u>Coordinator/Communicator</u>. Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns.</p></td></tr><tr><td><p>М</p></td><td><p><u>Methods and techniques expert.</u> Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement.</p></td></tr><tr><td><p>Т</p></td><td><p><u>Technical expert</u>. Providing technical (IT) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

The role accountable for all ITAM activities is usually the ITAM practice owner. The competency profile for this role in the context of ITAM is CLA, though the importance of each of these competencies varies from activity to activity.

#### 4.1.1 IT asset manager

The IT asset manager is responsible for overseeing the IT asset lifecycle with related data in their organization, for all IT assets in scope; this role may be local or global. In many organizations, the IT asset manager role is performed by a dedicated person, sometimes under a specialized job title such as software IT asset manager, hardware IT asset manager, or cloud IT asset manager.

This role is typically responsible for:

*   managing the ITAM approach
*   communicating the ITAM approach and procedures
*   integrating the ITAM approach into value streams
*   making decisions about IT asset inclusion in the scope and managing exceptions
*   ensuring the IT asset lifecycle models are followed
*   ensuring the IT asset register contains valid data
*   ensuring the organization’s IT assets are compliant
*   participating in IT asset risk management
*   liaising with the monitoring and event management practice and ensuring core IT asset events and changes are monitored
*   optimizing IT asset utilization and reporting related financial results
*   reporting on ITAM and compliance.

#### 4.1.2 IT asset custodian

The IT asset custodian can either be a team or a person who ensures the right utilization of the IT asset. They ensure that ITAM procedures are consistently applied to the IT asset throughout its lifecycle in the best interests of the IT asset owner.

#### 4.1.3 IT asset analyst

An IT asset analyst is a professional who specializes in managing an organization’s information technology (IT) assets. This includes hardware, software, cloud, and data assets. The IT asset analyst is responsible for ensuring that the organization’s IT assets are properly managed and maintained.

The primary responsibilities of an IT asset analyst may include tracking IT assets, monitoring their usage, identifying and mitigating risks, and providing recommendations for improving the management of IT assets. They may also be responsible for developing and implementing policies and procedures related to IT asset management, as well as providing training and support to end-users.

#### 4.1.4 IT asset register administrator

The IT asset administrator is responsible for analysing and providing information on assets. The IT asset administrator ensures the requisition, distribution, and information update of the assets.

#### 4.1.5 License manager

The license manager is the subject matter expert for all licensing aspects related to software and cloud products, including stock of available licences. This role collaborates with the supplier and contract manager role to ensure IT asset-related contracts (for example, maintenance and support) are appropriate in terms of cost, value balance, and compliance. Due to the complexity and variety of licence models, the role may be (and generally is, in large organizations) dedicated to a specific platform type (such as workplace or datacentre) or to a specific software publisher. In the latter case, this role is commonly combined with the software IT asset manager role.

#### 4.1.6 IT asset owner

The IT asset owner is the organization that has funded the investment in the IT asset, retains the rights to the IT asset, and sponsors the asset.

#### 4.1.7 IT asset consumer

The IT asset consumer is responsible for an IT asset during its use for service delivery or consumption. The role can be performed by a member of the service provider organization, or a customer or user.

#### 4.1.8 Other roles involved in IT asset management activities

Examples of other roles which are responsible for ITAM activities are listed in Table 4.2, together with the associated competency profiles and specific skills.

#### Table 4.2 Examples of roles with responsibility for ITAM activities

<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Responsible roles</strong></p></td><td><p><strong>Competency profile</strong></p></td><td><p><strong>Specific skills</strong></p></td></tr><tr><td><p>Managing a common approach to the ITAM process</p></td></tr><tr><td><p>Analyse stakeholders' requirements and IT asset risks</p></td><td><ul><li>IT asset manager</li><li>License manager</li><li>Procurement manager</li><li>Contracts manager</li><li>Portfolio manager</li><li>Service delivery manager</li><li>Product owner</li><li>Business analyst</li><li>Auditor</li></ul><ul><li>External consultants</li></ul></td><td><p>TCM</p></td><td><ul><li>Good understanding of the organization’s strategy, stakeholders, key services and key assets, vendor ecosystem</li><li>Understanding of IT asset risks</li><li>Expertise in IT asset compliance, licensing, procurement, and contracts management</li></ul></td></tr><tr><td><p>Define and agree the ITAM approach</p></td><td><ul><li>IT asset manager</li><li>IT asset owner</li><li>IT asset custodian</li><li>License manager</li><li>Procurement manager</li><li>Contracts manager</li><li>Service delivery manager</li><li>Product owner</li><li>Business analyst</li><li>Auditor</li><li>External consultant</li></ul></td><td><p>MTC</p></td><td><ul><li>Expertise in IT asset compliance, licensing, and technical aspects of ITAM</li><li>Understanding of procurement and contracts management</li><li>Expertise in ITAM, SAM tools</li><li>Process and workflow expertise</li><li>Risk management</li></ul></td></tr><tr><td><p>Communicate and integrate the ITAM approach into the organization's value streams</p></td><td><ul><li>IT asset manager</li><li>License manager</li></ul><ul><li>ITAM/SAM implementation project manager</li><li>Service delivery manager</li><li>Change manager</li><li>Knowledge manager</li><li>Organizational change manager</li><li>Product owner</li><li>External consultant</li></ul></td><td><p>CLM</p></td><td><ul><li>Good understanding of the organizational culture and internal stakeholders.</li><li>Good knowledge of the agreed approach.</li><li>Excellent leadership and communication skills</li></ul></td></tr><tr><td><p>Review and adjust the ITAM approach and procedures</p></td><td><ul><li>IT asset manager</li></ul><ul><li>IT asset owner</li><li>IT asset custodian</li><li>License manager</li><li>Procurement manager</li><li>Contract manager</li><li>Service delivery manager</li><li>Product owner</li><li>Business analyst</li><li>Auditor</li><li>External consultant</li></ul></td><td><p>TMCA</p></td><td><ul><li>Decision making</li><li>Good understanding of the organization’s strategy, stakeholders, key services and key assets, and vendor ecosystem</li><li>Understanding of IT asset risks</li><li>Expertise in IT asset compliance, licensing, and technical aspects of ITAM</li><li><p>Understanding of procurement and contracts management</p></li></ul></td></tr><tr><td><p>Managing the IT asset lifecycle and records process</p></td></tr><tr><td><p>Analyse resources and identify IT assets</p></td><td><ul><li>IT asset manager</li><li>IT asset owner</li><li>IT asset custodian</li><li>License manager</li><li>Procurement specialist</li><li>Contract manager</li><li>Service delivery manager</li><li>Product owner</li><li>Service desk agent</li><li>Stockroom manager</li><li>IT coordinator</li></ul></td><td><p>TCA</p></td><td><p>Good knowledge of the organization’s ITAM approach, IT asset types, and lifecycle models</p></td></tr><tr><td><p>Verify IT assets and lifecycle models</p></td><td><ul><li>IT asset manager</li><li>IT asset owner</li><li>IT asset custodian</li><li>License manager</li><li>Procurement manager</li><li>Contract manager</li><li>Service delivery manager</li><li>Product owner</li><li>IT manager</li></ul></td><td><p>TA</p></td><td><p>Good knowledge of the organization’s ITAM approach, IT asset types, and lifecycle models</p></td></tr><tr><td><p>Follow the lifecycle model</p></td><td><ul><li>IT asset manager</li><li>IT asset owner</li><li>IT asset custodian</li><li>License manager</li><li>Procurement /purchasing specialist</li><li>Contract manager</li><li>Service delivery manager</li></ul><ul><li>Product owner</li><li>Service desk agent</li><li>Stockroom manager</li><li>IT coordinator</li><li>Accountant /financial analyst</li><li>Systems administrator</li></ul><ul><li>Developer</li></ul></td><td><p>TAC</p></td><td><ul><li>Good knowledge of the organization’s ITAM approach, IT asset types, and lifecycle models</li><li>Good knowledge of the IT asset register and related procedures.</li></ul></td></tr><tr><td><p>Manage exceptions</p></td><td><ul><li>IT asset manager</li><li>IT asset owner</li><li>IT asset custodian</li><li>License manager</li><li>Service delivery manager</li><li>Product owner</li><li>Service desk agent</li><li>Stockroom manager</li><li>IT coordinator</li></ul></td><td><p>TCAM</p></td><td><ul><li>Good knowledge of the organization’s ITAM approach, IT asset types, and lifecycle models</li><li>Good knowledge of the IT asset register and related procedures.</li></ul></td></tr><tr><td><p>Review the lifecycle</p></td><td><ul><li>IT asset manager</li><li>IT asset owner</li><li>IT asset custodian</li><li>License manager</li><li>Procurement manager</li><li>Contract manager</li><li>Service delivery manager</li><li>Product owner</li><li>IT manager</li><li>Service desk agent</li><li>Stockroom manager</li><li>Accountant/financial analyst</li><li>Systems administrator</li><li>Developer</li></ul></td><td><p>TA</p></td><td><ul><li>Good knowledge of the organization’s ITAM approach, IT asset types, and lifecycle models</li><li>Understanding of IT asset risks</li><li>Expertise in IT asset compliance, licensing, and technical aspects of ITAM</li><li>Understanding of procurement and contracts management</li></ul></td></tr><tr><td><p>Verifying, auditing, and analysing IT assets</p></td></tr><tr><td><p>Plan audit</p></td><td><ul><li>IT asset manager</li><li>License manager</li><li>Compliance officer</li><li>Service desk lead</li><li>Stockroom manager</li><li>IT coordinator</li><li>Accountant/financial analyst</li><li>Auditor</li><li>Vendor representative</li></ul><ul><li>Government representative</li></ul></td><td><p>TCMA</p></td><td><ul><li>Expertise in auditing</li><li>Understanding of IT asset risks</li><li>Expertise in IT asset compliance, licensing, and the technical aspects of ITAM</li><li>Expertise in inventory and discovery tools, stocks management, and stock taking</li></ul></td></tr><tr><td><p>Collect IT asset data</p></td><td><ul><li>IT asset manager</li><li>IT asset custodian</li><li>License manager</li><li>Compliance officer</li><li>Service desk agent</li><li>Stockroom manager</li><li>IT coordinator</li><li>Accountant/financial analyst</li><li>Auditor</li></ul><ul><li>Vendor representative</li><li>Government representative</li><li>Systems administrator</li><li>Developer</li></ul></td><td><p>TA</p></td><td><ul><li>Expertise in IT asset compliance, licensing, and the technical aspects of ITAM (e.g. cloud, virtualization, data management)</li><li>Expertise in inventory and discovery tools, stocks management, and stock taking</li><li>Knowledge of the IT asset register and ITSM tools</li></ul></td></tr><tr><td><p>Verify IT asset data</p></td><td><p>IT asset manager</p><ul><li>IT asset custodian</li><li>License manager</li><li>Compliance officer</li><li>Service desk agent</li><li>Stockroom manager</li><li>IT coordinator</li><li>Accountant/financial analyst</li><li>Auditor</li><li>Vendor representative</li><li>Government representative</li><li>Systems administrator</li></ul><ul><li>Developer</li></ul></td><td><p>TA</p></td><td><ul><li>Expertise in IT asset compliance, licensing, and the technical aspects of ITAM (e.g. cloud, virtualization, data management)</li><li>Expertise in inventory and discovery tools, stocks management, and stock taking</li><li>Knowledge of the IT asset register and ITSM tools</li></ul></td></tr><tr><td><p>Review and analyse verification and audit findings</p></td><td><ul><li>IT asset manager</li><li>License manager</li><li>Compliance officer</li><li>Service desk lead</li><li>Stockroom manager</li><li>IT coordinator</li></ul><ul><li>Accountant/financial analyst</li><li>Auditor</li><li>Vendor representative</li><li>Government representative</li><li>Systems administrator</li><li>Developer</li></ul></td><td><p>TAC</p></td><td><ul><li>Expertise in IT asset compliance, licensing, and the technical aspects of ITAM (e.g. cloud, virtualization, data management)</li><li>Expertise in inventory and discovery tools, stocks management, and stock taking</li><li>Knowledge of the IT asset register and ITSM tools</li></ul></td></tr><tr><td><p>Compose and communicate verification and audit reports</p></td><td><ul><li>IT asset manager</li><li>License manager</li><li>Compliance officer</li><li>Service desk lead</li><li>Stockroom manager</li><li>IT coordinator</li><li>Accountant /financial analyst</li><li>Auditor</li><li>Vendor representative</li><li>Government representative</li></ul></td><td><p>TCAM</p></td><td><p>Communication and presentation skills, data processing skills</p></td></tr></tbody></table>

### 4.2 Organizational structures and teams

#### 4.2.1 Level of centralization

The struggle between centralization and decentralization is a common dilemma as the ITAM practice is initially formalized and evolves over time. In many cases, inadequate IT asset governance results in an ITAM practice that is initially centralized. However, many of the controls that restored order are later perceived to be an organizational constraint; this is especially true for digital organizations operating within or working towards a high-velocity environment. The next iteration of ITAM, therefore, frequently favours decentralization and higher levels of efficiency. Once consequences of this loss of control are observed though, the ITAM practice usually returns to a centralized approach, but one that is likely less severe than previously. Like a pendulum, this cycle continues, with each swing being less dramatic until an appropriate balance is achieved, as shown in Figure 4.1.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_3.4.png)

Figure 4.1 ITAM centralization versus decentralization pendulum

Healthy organizations and the needs of their stakeholders are constantly evolving. So, achieving and maintaining an effective balance between centralization and decentralization can be benefit from a continual improvement approach that monitors various factors, such as efficiency, effectiveness, and organizational scalability.

In a small organization, ITAM roles are frequently defined in a traditional hierarchy. A single IT asset manager could initially perform and later delegate administrative, analysis, and other common operational-level management tasks as the size of the organization or the quantity of its IT assets increases. Additional specializations, such as HAM, SAM, licence management, and cloud management may be necessary as complexity of the IT environment increases.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_3.5.png)

Figure 4.2 Example ITAM structure in a small organization

Digital organizations may find this traditional hierarchy could become burdensome and counterproductive. By using a shift-left approach, the lower levels in Figure 4.2 can be empowered to make decisions and take management action within an appropriately defined scope. This would result in a flatter and less pyramid-shaped organizational chart.

Large organizations are frequently structured around divisions based upon product, legal, or geographic requirements. The needs of the stakeholders within these divisions could differ significantly, based upon factors including:

*   the type of IT assets required
*   the patterns of usage for IT assets
*   applicable regulatory requirements based on industry or geography
*   culture and language
*   ways of working.

In these scenarios, each division may need a combination of its own processes, management, suppliers, and tools, and information like a separate IT asset register or inventory. This is shown in Figure 4.3.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_3.6.png)

Figure 4.3 Example ITAM structure in a large organization

Populating ITAM roles in a central team can help develop expertise and facilitate collaboration with other central functions, such as procurement, finance, and risk management. Such centralization can, however, create a distance that is detrimental to day-to-day collaboration with those who use and handle IT assets. This paradox can be managed by achieving centralization through other dimensions of service management, if the structure and culture of the organization allows it. This could include: a centralized IT asset register managed by geographically dispersed teams, a multilingual workflow engine running common processes across several time zones, the collegial governance of processes and data models to drive convergence despite the heterogeneity of implemented solutions, and so on.

Global organizations often centrally define their ITAM practice and deploy it in a decentralized manner. In such case, global convergence should be achieved considering key local aspects: the visions and goals of sponsors, process maturity, cultural shift, IT asset types and volumes, business and economic reality, gaps with convergence points covering the four dimensions of services (policies, data model, staffing), language, laws and regulations, currency and accounting systems, suppliers’ and partners’ contracts, and so on.

#### 4.2.2 Stakeholder involvement

Conversing with IT asset consumers is essential; for example, to identify the most appropriate hardware asset model or loan terms considering stakeholders’ preferences and constraints. Depending on consumer profiles and the level of centralization of ITAM in the organization, this interaction can rely on many channels: periodic online or service request closure surveys, random phone interviews, suggestion boxes at the service desk or on the portal, periodic meetings organized by the service level management practice, customer events, a selection of hardware models with a panel of users, and so on.

#### 4.2.3 Cultural aspects

The effectiveness of the ITAM practice depends on the organization’s culture, which can vary significantly from place to place depending on people's perceptions of ownership and personal responsibility. The ITIL 4 practice guides for the workforce and talent management and organizational change management practices can help enable positive and sustainable change in this area.

##### 4.2.3.1  Consciousness of financial, security, and legal stakes

People requesting and handling IT assets should understand the associated financial, security, and legal stakes for the organization. This implies constant monitoring and discussions with relevant individuals to avoid noncompliance and undesired behaviour. For example, when a free (for non-commercial usage) software is installed on a device by a user, when a machine is not returned to stock after the user has left, when a testing environment is not decommissioned from the cloud environment once the project is over, and so on.

##### 4.2.3.2 Engagement of individual responsibility without complacency

For each IT asset custodian or consumer to take their responsibility of the IT assets seriously, that responsibility should be assigned by name. Therefore, IT assets should not be assigned to organizational units but to individuals. The potential individual consequences of transgressions (negligent loss or damage, sloppiness, improper usage, software piracy) should be clearly stated in contracts of employment, pricing plans, and disciplinary procedures.

#### 4.2.4 Internal profit centre providing IT assets and related services

Technical teams handle the IT assets. The ITAM practice combines skills scattered in a fragmented way throughout the organization about technology, contracts, procurement, finance, laws, data, processes, taxes, suppliers, products, services, and so on. IT assets represent a significant portion of the organization's expenses and develop stakes that are set to grow with the digital transformation.

Organizations that have a mature ITAM practice have understood this. Consequently, they do not structure their practice around a bureaucratic entity, but as an internal provider which finances itself through the margins it generates. Internal ‘ITAM as a service’ may enable value with:

*   trustworthy data requiring minimal effort thanks to integrated processes and practical technology
*   one-stop shopping and disposal
*   transverse stock management to optimize acquisitions
*   centralized management of major solution vendors in synergy with internal stakeholders to defend their interests more forcefully
*   negotiated terms and conditions
*   attractive prices for IT assets and related services and valuation of disposed assets
*   governance of the IT asset catalogue
*   consultancy, training, and awareness about tricky aspects, such as licensing, contracts, or cost optimization
*   handling of external audits in project mode
*   simplified collaboration between IT and non-IT organizational units (finance, procurement, legal)
*   advocacy and sharing of best practices in professional associations and user clubs.

## 5. Information and technology

### 5.1 Information exchange, inputs/outputs

The effectiveness of the ITAM practice is based on the quality of the information used, such as:

*   the organization’s strategy
*   the organization’s architectures
*   the organization’s portfolios
*   stakeholders' requirements and needs for IT asset information
*   applicable regulatory requirements
*   IT asset data from vendors, suppliers, and publishers
*   technology trends
*   IT asset utilization data
*   change schedules and plans
*   programme and project plans
*   financial data
*   service financial management policies and procedures
*   service configuration data.

This information may take various forms, depending on the IT asset types, organization’s requirements, and IT asset management tooling.

### 5.2 Automation and tooling

Ensuring that IT asset data is updated at every change of status of the IT asset, automating the IT asset register, and capturing IT asset data is very important for the practice, as ITAM can easily become overburdened if these tasks are performed manually or without proper tools. Frequently, disconnected or obsolete tools must be remediated through human intervention. These manual processes can lead to tasks that are mundane, repetitive, and error-prone, and could result in consequences that increase cost and risk for the organization, such as delays at any point in the IT asset lifecycle, inventory inaccuracies, avoidable purchases, or poorly managed compliance.

Automation helps when managing the growing number of IT assets with fewer ITAM practitioners. The term automation is used in this and other ITIL publications to refer to the use of digital technology to enable, support, or enhance various activities. This includes, but is not limited to the full automation of activities where technology solutions remove the need for human intervention. Where automation is possible and effective, it may involve the solutions outlined in Tables 5.1 and 5.2.

#### Table 5.1 Automation solutions for ITAM activities

<table><tbody><tr><td><p><strong>Automation tools</strong></p></td><td><p><strong>Application of ITAM</strong></p></td></tr><tr><td><p>Accounting systems</p></td><td><ul><li>analyse stakeholders’ requirements and IT asset risks</li><li>verify IT assets and lifecycle models</li><li>follow the lifecycle model</li><li>manage exceptions</li><li>plan audit</li><li>collect IT asset data</li><li>verify IT asset data</li></ul></td></tr><tr><td><p>Analysis and reporting tools</p></td><td><ul><li>analyse stakeholders’ requirements and IT asset risks</li><li>review and adjust the ITAM approach and procedures</li><li>review the lifecycle</li><li>review and analyse verification and audit findings</li><li>compose and communicate verification and audit reports</li></ul></td></tr><tr><td><p>Geolocation and geofencing systems</p></td><td><ul><li>follow the lifecycle model</li><li>manage exceptions</li><li>verify IT asset data</li></ul></td></tr><tr><td><p>Inventory and discovery tools</p></td><td><ul><li>follow the lifecycle model</li><li>manage exceptions</li><li>collect IT asset data</li><li>verify IT asset data</li></ul></td></tr><tr><td><p>Labelling, barcode, QR code reader systems</p></td><td><ul><li>follow the lifecycle model</li><li>manage exceptions</li><li>verify IT asset data</li></ul></td></tr><tr><td><p>Procurement systems</p></td><td><p>follow the lifecycle model</p><p>manage exceptions</p></td></tr><tr><td><p>Work planning and prioritization tools</p></td><td><ul><li>plan activities to follow the lifecycle model</li><li>plan verification activities</li></ul></td></tr><tr><td><p>Workflow management and collaboration tools</p></td><td>define, agree, review, and communicate the ITAM approach</td></tr></tbody></table>

#### Table 5.2 Details of automation of the ITAM activities

<table><tbody><tr><td><p><strong>Process activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><p><strong>Key functionality</strong></p></td><td><p><strong>Impact on the effectiveness of the practice</strong></p></td></tr><tr><td colspan="4"><p>Managing a common approach to ITAM</p></td></tr><tr><td><p>Analyse stakeholders' requirements and IT asset risks</p></td><td><ul><li>Analysis and reporting tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>Risk and opportunities analysis</li><li>Value impact mapping</li><li>Collaboration and communication</li></ul></td><td><p>Medium</p></td></tr><tr><td><p>Define and agree the ITAM approach</p></td><td><ul><li>Workflow planning and prioritization tools</li><li>Workflow management and collaboration tools</li></ul></td><td><p>Workflow modelling, visualization, and mapping activities and responsibilities</p></td><td><p>Medium/high</p></td></tr><tr><td><p>Communicate and integrate the ITAM approach into the organization's value streams</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Presentation tools</li></ul></td><td><p>Support of promotion, training, and awareness</p></td><td><p>Medium</p></td></tr><tr><td><p>Review and adjust the ITAM approach and procedures</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Analysis and reporting tools</li><li>Work planning and prioritization tools</li></ul></td><td><p>Collaboration, information exchange, report creation, and distribution</p></td><td><p>Medium</p></td></tr><tr><td><p>Managing the IT asset lifecycle and records</p></td></tr><tr><td><p>Analyse resources and identify IT assets</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Accounting systems</li><li>Work planning and prioritization tools</li></ul></td><td><ul><li>Collaboration, information exchange, workflow and approval automation</li><li>Data export from external data sources</li></ul></td><td><p>Medium</p></td></tr><tr><td><p>Verify IT assets and lifecycle models</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Accounting systems</li><li>Work planning and prioritization tools</li></ul></td><td><ul><li>Collaboration, information exchange, workflow, and approval automation</li><li>Data export from external data sources</li></ul></td><td><p>High</p></td></tr><tr><td><p>Follow the lifecycle model</p></td><td><ul><li>Accounting systems</li></ul><ul><li>Inventory and discovery tools</li><li>Analysis and reporting tools</li><li>Procurement systems</li><li>Accounting systems</li><li>Workflow management and collaboration tools</li><li>Labelling, barcode, QR code reader systems</li><li>Geolocation and geofencing systems</li></ul></td><td><ul><li>IT asset register</li><li>Software IT asset management and software license optimization</li><li>Mobile device management</li><li>Assets inventory and discovery</li><li>IT asset data reconciliation with secondary and third-party data sources</li><li>Valuation and invoicing (interfaced with the IT asset register to create invoices)</li></ul><ul><li>Workflow automation</li><li>Labelling, barcoding</li><li>Geolocation and geofencing</li></ul></td><td><p>High</p></td></tr><tr><td><p>Manage exceptions</p></td><td><ul><li>Accounting systems</li><li>Inventory and discovery tools</li><li>Analysis and reporting tools</li><li>Procurement systems</li><li>Accounting systems</li><li>Workflow management and collaboration tools</li><li>Labelling, barcode, and QR code reader systems</li><li>Geolocation and geofencing systems</li></ul></td><td><ul><li>IT asset register</li><li>Software ITAM and software license optimization</li><li>Mobile device management</li><li>Assets inventory and discovery</li><li>IT asset data reconciliation with secondary and third-party data sources</li></ul><ul><li>Valuation and invoicing (interfaced with the IT asset register to create invoices)</li><li>Workflow automation</li><li>Labelling, barcoding</li><li>Geolocation and geofencing</li></ul></td><td><p>Medium to high</p></td></tr><tr><td><p>Review the lifecycle</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Analysis and reporting tools</li><li>Work planning and prioritization tools</li></ul></td><td><ul><li>Collaboration, information exchange, report creation, and distribution</li><li>Changes and projects tracking, audit trail</li></ul></td><td><p>Medium</p></td></tr><tr><td colspan="4"><p>Verifying, auditing, and analysing IT assets</p></td></tr><tr><td><p>Plan audit</p></td><td><ul><li>Accounting systems</li><li>Survey tools</li><li>Workflow management and collaboration tools</li></ul></td><td><ul><li>IT asset register</li><li>Audit actions planning and tracking</li><li>Collaboration and communications</li></ul></td><td><p>Medium</p></td></tr><tr><td><p>Collect IT asset data</p></td><td><ul><li>Accounting systems</li><li>Inventory and discovery tools</li><li>Analysis and reporting tools</li></ul></td><td><ul><li>IT asset register</li><li>Mobile device management</li><li>Assets inventory and discovery</li><li>IT asset data reconciliation with secondary and third-party data sources</li></ul><ul><li>Labelling, bar-coding</li><li>Geolocation and geofencing;</li></ul></td><td><p>High</p></td></tr><tr><td><p>Verify IT asset data</p></td><td><ul><li>Accounting systems</li><li>Inventory and discovery tools</li><li>Analysis and reporting tools</li><li>Labelling, barcode, and QR code reader systems</li><li>Geolocation and geofencing systems</li></ul></td><td><ul><li>IT asset register</li><li>Software ITAM and software license optimization</li><li>Mobile device management</li><li>Assets inventory and discovery</li><li>IT asset data reconciliation with secondary and third-party data sources</li><li>Labelling, bar-coding</li><li>Geolocation and geofencing</li></ul></td><td><p>High</p></td></tr><tr><td><p>Review and analyse verification and audit findings</p></td><td><ul><li>Workflow management and collaboration tools</li><li>Analysis and reporting tools</li></ul></td><td><p>Analysis of processing and reporting, dashboards, information visualization, decision-making support, and decision and action assignment and tracking</p></td><td><p>Medium</p></td></tr><tr><td><p>Compose and communicate verification and audit reports</p></td><td><p>Analysis and reporting tools</p></td><td><p>Reports creation and distribution, dashboards, data visualization</p></td><td><p>Medium</p></td></tr></tbody></table>

#### 5.2.1 Recommendations for the automation of IT asset management

By using the right tools and technologies, organizations can streamline their asset management processes and achieve better outcomes. Automation can help reduce manual errors, increase efficiency, and provide real-time insights into asset utilization.

*   **Design for value streams** Service value streams should address the entire IT asset lifecycle, from procurement to disposal. They should be supported by well-defined roles and responsibilities, approval processes, and escalation procedures, as well as the integration of multiple practices, such as service financial management, risk management, change enablement, service request management and service configuration management. Value streams should be optimized and evaluated for justifiable automation opportunities.
*   **Identify appropriate ITAM tooling** Select an IT asset management tool that aligns with the organization’s needs and goals but is also adequately scalable. The tool should support automating key asset management tasks such as discovery, tracking, and reporting and should be compatible with additional complementary technologies that can supplement basic functionality.
*   **Consider complementary technologies** Integrated tools, add-ons, or modules can increase the efficiency of ITAM. For example, barcode or RFID scanning technology can be used to track and manage assets, as well as to update the IT asset register, reducing manual data entry issues and saving time. Additional tools such as mobile device management, mobile application management, software metering, and deployment tools can also add management capabilities for specific technology domains.
*   **Include IT asset lifecycle models** The lifecycle of specific types of IT assets follows a pre-defined model which includes activities, information flow, controls, and communication. An automation solution should support the creation, testing, and use of such models.
*   **Consider workforce planning and reporting** Total cost of ownership (TCO) calculations should include the management time that will be required over the lifetime of a type of IT asset. This should be included in accounting, billing, charging, and reporting activities and will often aid in the analysis, feasibility, and potential justification of additional automation solutions.
*   **Utilize measurement and reporting from the start** The use of analytics and reporting tools to provide real-time insights into asset utilization, which can help identify areas where assets are being underutilized or overutilized and help optimize asset usage and related costs.
*   **Ensure that self-help capabilities are available and convenient** User-facing interfaces to request IT assets or related IMAC actions should be clear, easy to use, informative, and customizable to create a positive consumer experience and meet the needs of the organization.
*   **Consider leveraging super users** In a distributed or decentralized approach, super users or administrators can be utilized to perform routine operational-level ITAM tasks, usually for a particular type, class, or category of IT asset. Software functionality, rights, permissions, and licensing that allow for this accommodation should be both flexible and affordable.

## 6. Partners and suppliers

Partners and suppliers may support the development, management, and execution of the IT asset management practice. The potential forms of support are outlined in the following sections.

### 6.1 Integrating with IT asset management activities

A successful ITAM practice is not solely the result of the efforts of internal resources. Organizations constantly handle IT assets that are provided to them as part of third-party services. ITAM is therefore dependent upon the ability of third parties to supply most of the assets that the organization has opted to source through what ITIL 4 describes as a service relationship (see section 2.4 of *ITIL Foundation: ITIL 4 Edition* for a model of a service relationship).

Similarly, organizations’ IT assets are widely used by their service consumers. This requires effective coordination of ITAM practices between members of the service relationships ecosystem. The exact level of coordination depends on the type of service relationship. The closer the relationship and higher the trust, the more IT asset information can be shared, and management activities performed together.

<table><tbody><tr><td><p><strong>Key message</strong></p></td></tr><tr><td><p>Assets acquired and provided by the organization’s ITAM practice are frequently a complex mix of hardware, software, and cloud assets sourced through elements of integration.</p></td></tr></tbody></table>

Third parties can support the IT asset management practice; however, it is important to remember that service relationships introduce constraints and dependencies, as well as opportunities and support. When an IT asset is supplied by a third party, the level of service (time required for fulfilment, convenience, and frequency of communications, and so on) may be constrained by the supplier’s policies and operating procedures. This can conflict with user expectations and is often challenging to change or influence. In other cases, IT assets are provided directly by the service provider, but the provisioning is constrained by the supply of components or the execution of activities by a third party.

A lack of timely sourcing of IT assets can have severe consequences for many organizations, so these and other similar dependencies should be reflected in service level agreements and procedures. Communications with customers and users should be routine and transparent to establish realistic expectations and smooth request fulfilment. The supplier management practice should be also used to ensure that, where reasonably possible, third parties adjust their level of service to the needs of the organization.

Where service relationships are basic or cooperative and suppliers and partners are independent organizations with their own objectives, the organization should take steps to protect its IT assets and remain in control. These steps include the following:

*   Sign non-disclosure agreements and carefully control the exchange of sensitive IT asset data with suppliers and partners.
*   Discover conflicts of interest that may cause harm to the organization (such as an outsourced service desk that charges for its services based on the number of assets it provides to users, or a software compliance consulting mission entrusted to a supplier who is also a reseller or auditor on behalf of a software publisher).
*   Including terms in third-party service contracts about the handling of IT assets, with clear duties and responsibilities for each ITAM activity the suppliers contribute to, such as an outsourced service desk handling activities like the reception of ordered IT assets, secure storage, stock management, allocation / IMAC, detection and handling of special situations (damage, non-compliance, loss), inventory, and so on.
*   Communicating the achievements of a mature ITAM practice can help to optimize relationships with vendors and suppliers. For example, the understanding of license models and a good software compliance can discourage time-consuming vendor audits; controlling IT spending can refocus collaboration with suppliers on higher value-added topics or increase investor and customer confidence; operational activities that are free of administrative hassles can help attract talent and reduce service provider rates; and so on.

Outsourced ITAM services exist and can be helpful. However, the ultimate responsibility for an organization’s IT assets cannot be outsourced. Therefore, the organization should develop internal competencies and controls to protect its own interests and master its contractual and legal responsibilities.

### 6.2 Provision of software tools

Most software tools used for IT asset management are shared with other practices. However, implementation and use of integrated service management information systems or suites often starts with automating service request management, incident management, and service desk activities. In this case, the owner of the IT asset management practice and the managers of the teams involved in IT asset management should define requirements and interact with other teams and practices of the service provider to ensure that the required tools are procured, implemented, and used in an optimal way.

### 6.3 Consulting and advisory

Specialised suppliers who have developed expertise in IT asset management can help establish and develop the practice, adopt methods and techniques (such as automation), and initially develop IT asset lifecycle models.

## 7. Capability assessment and development

### 7.1 Practice capability levels

The practice success factors described in section 2.4 cannot be accomplished overnight. The ITIL maturity model defines the following capability levels applicable to any management practice:

**Level 1** The practice is not well organized; it is performed as initial or intuitive. It may occasionally or partially achieve its purpose through an incomplete set of activities.

**Level 2** The practice systematically achieves its purpose through a basic set of activities supported by specialised resources.

**Level 3** The practice is well defined and achieves its purpose in an organized way, using dedicated resources and relying on inputs from other practices that are integrated into a service management system.

**Level 4** The practice achieves its purpose in a highly organized way, and its performance is continually measured and assessed in the context of the service management system.

**Level 5** The practice is continually improving organizational capabilities associated with its purpose.

For each practice, the ITIL maturity model defines criteria for every capability level from level two to level five. These criteria can be used to assess the practice’s ability to fulfil its purpose and to contribute to the organization’s service value system.

Each criterion is mapped to one of the four dimensions of service management and to the supported capability level. The higher the capability level, the more comprehensive realization of the practice is expected. For example, criteria related to the practice automation are typically defined at levels 3 or higher because effective automation is only possible if the practice is well defined and organized.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_7.1.png)

Figure 7.1 The design of the capability criteria

This approach results in every practice having up to 30 capability criteria based on the practice success factors (PSFs) and mapped to the four dimensions of service management. The number of criteria at each level differs; the four dimensions are comprehensively covered starting from level 3, so this level typically has more criteria than others.

The following capability criteria are defined in the ITIL maturity model for the IT asset management practice:

#### Table 7.1 The asset management capability criteria

<table><tbody><tr><td><p>PSF</p></td><td><p>Criterion</p></td><td><p>Dimension</p></td><td><p>Capability level</p></td></tr><tr><td rowspan="8"><p>Ensuring that the organization has relevant information about its IT assets throughout their lifecycle</p></td><td><p>Key users of the IT asset information and their requirements are identified</p></td><td><p>Value streams and processes</p></td><td><p>2</p></td></tr><tr><td><p>Information about IT assets is available when needed and meets user requirements</p></td><td><p>Information and technology</p></td><td><p>2</p></td></tr><tr><td><p>Procedures for requesting and obtaining IT asset information are defined and communicated to relevant stakeholders</p></td><td><p><span>Value streams and processes</span></p></td><td><p>3</p></td></tr><tr><td><p>Responsibility for the management of IT asset information is clearly defined</p></td><td><p><span>Value streams and processes</span></p></td><td><p>3</p></td></tr><tr><td><p>IT asset information covers relevant details about third-party services</p></td><td><p>Partners and suppliers</p></td><td><p>3</p></td></tr><tr><td><p>IT asset information is managed using an integrated information system</p></td><td><p><span>Information and technology</span></p></td><td><p>4</p></td></tr><tr><td><p>The quality and availability of the IT asset information are measured and reported</p></td><td><p><span>Value streams and processes</span></p></td><td><p>4</p></td></tr><tr><td><p>The quality and availability of the IT asset information are continually reviewed and improved</p></td><td><p><span>Value streams and processes</span></p></td><td><p>5</p></td></tr><tr><td rowspan="8"><p>Ensuring that the utilization of IT assets is continually monitored and optimized</p></td><td><p>Information about IT asset utilization is gathered and analysed</p></td><td><p><span>Value streams and processes</span></p></td><td><p>2</p></td></tr><tr><td><p>Organization’s requirements for optimizing IT asset utilization are identified and agreed</p></td><td><p><span>Value streams and processes</span></p></td><td><p>3</p></td></tr><tr><td><p>Information about IT asset utilization is managed using an integrated information system</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>Relevant stakeholders know how they should optimize IT asset utilization</p></td><td><p>Organizations and people</p></td><td><p>3</p></td></tr><tr><td><p>Sourcing options are considered to optimize IT asset utilization</p></td><td><p>Partners and suppliers</p></td><td><p>3</p></td></tr><tr><td><p>Alternative technology solutions are considered to optimize IT asset utilization</p></td><td><p>Information and technology</p></td><td><p>3</p></td></tr><tr><td><p>IT asset utilization is measured and reported</p></td><td><p><span>Value streams and processes</span></p></td><td><p>4</p></td></tr><tr><td><p>IT asset utilization is regularly reviewed and continually improved</p></td><td><p><span>Value streams and processes</span></p></td><td>5</td></tr></tbody></table>

These capability criteria can be used by organizations for self-assessment and improvement of the

practice.

### 7.2 Capability self-assessment

A self-assessment can be conducted by the service provider’s internal audit team, if the service provider has one, or by the respective team of the parent organization. If there is no specialized team within the organization, the assessment can be done by a team of practice owners and managers responsible for other management practices of the service provider, or a mixed team of the service provider’s executive leaders and managers.

To perform a quick self-assessment using the capability criteria, the following rules should be followed:

1.  Start with the level 2 criteria. Based on the knowledge of your organization, answer the question, ‘Is this a valid description of our organization in MOST cases?’
2.  If the answer to the question above is ‘yes’, make a list of at least three types of material evidence that could prove the answer. These can be records, documents, interviews with business stakeholders, or service provider employees.
3.  If the answer is ‘yes’ to all criteria of level 2, this level is considered achieved. Proceed to the criteria of level 3.
4.  If not all criteria of level 2 are met, the practice is considered to be at level 1. Focus on the criteria that are not met. What is missing in the organization? Why? How can it affect service request management and fulfilment? What can be done to meet the criteria that are currently missed?
5.  The same approach is applied at every next level; the practice is considered to be at the level where all criteria are met. It is important to focus on the missing capabilities and improvement opportunities, rather than on a formal achievement of a high capability level.

### 7.3 Capability development

Management practices should support achievement of the organization’s objectives and enable creation of value for the stakeholders. Depending on the service provider’s strategy, positioning, and business and operating models, some practices may be more important and therefore require a higher level of capability. There is no organization that requires all management practices to be at capability level 5. Higher capability level provides higher assurance of the fulfilment of the practice’s purpose, but it comes at a price – the cost of management, automation, and training, for example. To achieve optimal performance with sufficient levels of assurance, organizations should define a target capability level for each management practice.

Figure 7.2 and Table 7.2 show the capability development model, which can be applied to every management practice. The structure of this publication is aligned with the development steps.

![](IT%20asset%20management%20ITIL%204%20Practice%20Guide/ITAM_figure_7.2.png)

Figure 7.2 The capability development steps and levels

#### Table 7.2 The IT asset management capability development steps

<table><tbody><tr><td><p>Capability level</p></td><td><p>Define, agree, and implement</p></td><td><p>Comment for IT asset management</p></td><td><p>Chapter (for recommendations)</p></td></tr><tr><td rowspan="5"><p>2</p></td><td><p>Purpose and objectives</p></td><td rowspan="2"><p>Key stakeholder groups</p></td><td><p>2.1</p></td></tr><tr><td><p>Scope</p></td><td><p>2.3</p></td></tr><tr><td><p>Processes and activities</p></td><td rowspan="3"><p>ITAM approach, IT asset lifecycle, and IT asset models</p></td><td><p>3</p></td></tr><tr><td><p>Roles and responsibilities</p></td><td><p>4</p></td></tr><tr><td><p>Tools and procedures</p></td><td><p>5</p></td></tr><tr><td rowspan="3"><p>3</p></td><td rowspan="3"><p>Dependencies and integration</p></td><td><p>Integration into the service value streams</p></td><td><p>3.2</p></td></tr><tr><td><p>Use of an integrated information system</p></td><td><p>5</p></td></tr><tr><td><p>Suppliers and other parties involved in the IT asset lifecycle, integration into the service value streams</p></td><td><p>6</p></td></tr><tr><td><p>4</p></td><td><p>Measurement and reporting</p></td><td><p>Metrics, KPIs, regular and ad hoc reports</p></td><td><p>2.5</p></td></tr><tr><td><p>5</p></td><td><p>Continual improvement</p></td><td><p>Regular review of the relationships, models, and the IT asset management approach</p></td><td>2.4, 2.5, 7</td></tr></tbody></table>

## 8. Recommendations for practice success

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of things that organizations might think about, not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:

*   focus on value
*   start where you are
*   progress iteratively with feedback
*   collaborate and promote visibility
*   think and work holistically
*   keep it simple and practical
*   optimize and automate.

In Table 8.1, recommendations for a successful IT asset management practice are linked to the relevant guiding principles.

#### Table 8.1 Recommendations for IT asset management success

<table><tbody><tr><td><p><strong>Recommendations</strong></p></td><td><p><strong>Comments</strong></p></td><td><p><strong>ITIL guiding principle(s)</strong></p></td></tr><tr><td><p>Focus on stakeholder value</p></td><td><p>Defining goals and objectives that are aligned with the overall business strategy will help focus processes and activities.</p></td><td><p>Focus on value</p></td></tr><tr><td><p>Create an IT asset register</p></td><td><ul><li>Start by creating an inventory of all the hardware, software, and other IT assets owned by the organization.</li><li>This will help to identify gaps or redundancies in the IT infrastructure and prioritize management efforts.</li></ul></td><td><ul><li>Start where you are</li><li>Collaborate and promote visibility</li></ul></td></tr><tr><td><p>Implement traceability</p></td><td><p>Traceability or tracking through discovery and verification allows the organization to monitor the status of assets, track changes, and identify issues.</p></td><td><ul><li>Progress iteratively with feedback</li><li>Think and work holistically</li></ul></td></tr><tr><td><p>Establish governance</p></td><td><p>Policies and procedures ensure consistency and accountability, especially for procurement processes, deployment procedures, and disposal protocols.</p></td><td><ul><li>Focus on value</li><li>Keep it simple and practical</li><li>Optimize and automate</li></ul></td></tr><tr><td><p>Train and equip staff</p></td><td><p>Training staff will help ensure consistent execution of established policies and procedures, proper use of software tools, and the management of accurate and comprehensive information.</p></td><td><ul><li>Focus on value</li><li>Collaborate and promote visibility</li><li>Optimize and automate</li></ul></td></tr><tr><td><p>Regularly review and update IT asset register</p></td><td><p>Routinely auditing IT assets can help maintain accurate records, identify errors and discrepancies, meet compliance requirements, reduce costs, and improve the organization’s security and risk management posture.</p></td><td><ul><li>Collaborate and promote visibility</li><li>Think and work holistically</li></ul></td></tr><tr><td><p>Integrate ITAM with other management practices</p></td><td><p>ITAM should not exist in a vacuum. To be truly effective, it must be integrated into service value streams with other management practices, such as service financial management, supplier management, capacity and performance management, information security management, risk management, service configuration management, and service request management.</p></td><td><ul><li>Progress iteratively with feedback</li><li>Collaborate and promote visibility</li><li>Think and work holistically</li><li><p>Optimize and automate</p></li></ul></td></tr></tbody></table>

## 9. Acknowledgements

PeopleCert is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, PeopleCert would like to thank the following people.

### Authors

Stéphane Joret

### Contributors

Andrey Boganov, Sherry Irwin, Jan Øberg

### Reviewers

Graham Heard, Roman Jouravlev

### 2023 Revision

Antonina Douannes, Adam Griffith, Roman Jouravlev, Kaimar Karu, Olga Masalina, Avinash Singh
