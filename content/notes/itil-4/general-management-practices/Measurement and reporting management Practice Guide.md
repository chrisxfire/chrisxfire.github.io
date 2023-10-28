---
title: "Measurement and reporting management: Practice Guide"
date: 2023-10-21T00:00:00-06:00
draft: true
weight: 1
---

# 1. Source
Axelos International (https://www.axelos.com)

# 2. Overview
<table><tbody><tr><td><strong>Key message</strong></td></tr><tr><td>The purpose of the measurement and reporting practice is to support good decision-making and continual improvement by decreasing the levels of uncertainty. This is achieved through the collection of relevant data on various managed objects and the valid assessment of this data in an appropriate context. Managed objects include, but are not limited to, products and services, practices and value chain activities, teams and individuals, suppliers and partners, and the organization as a whole.</td></tr></tbody></table>

Many of these managed objects are connected, as are their respective metrics and indicators. For example, to set clear objectives for the measurement and reporting practice, it is important to understand the organizational objectives. These can be based on areas such as customer/market relevance and operational excellence. It is important to clarify the relationship between higher-level and lower-level objectives.

Key performance indicators (KPIs) can be agreed based on these objectives, against which success can be measured. In many cases, it is convenient to define critical success factors (CSFs) for each objective and then define KPIs for the CSFs, for more granular and transparent measurement and assessment.

## 2.2 Terms and concepts
### 2.2.1 Measurement
<table><tbody><tr><td><strong>Definition: Measurement</strong></td></tr><tr><td>A means of decreasing uncertainty based on one or more observations that are expressed in quantifiable units.</td></tr></tbody></table>

This definition of ‘measurement’ has two important aspects. Firstly, the result of measurement is defined in numeric values, an observation which provides a definitive answer on exactly how good or bad things are. Secondly, measurements aim to reduce the uncertainty of an object’s state.

#### 2.2.1.1 Why measure?
Measurement is not the only aid to successful management. Many management challenges can be addressed with leadership, communication, design, intuition, and other means. It is not true that ‘we cannot manage what we do not measure’.

Measurements provide information that can be used to make decisions and pinpoint issues, which can be tackled with management efforts and assure a reliable foundation for motivation.

Measurements have no intrinsic value. They only become valuable when applied in a management context. Measurements can help with four management tasks<sup>1</sup>:
* **Influencing behaviour** By defining measurable targets, an organization sets the direction for activities and expectations for outcomes. Each objective should have one or more indicators to enable the assessment of progress.
* **Justifying changes** Any improvement initiative (or any change) requires justification. Metrics that display negative trends or deviations from target values are quantitative arguments for change.
* **Validating decisions** Measurements help to ensure that activities have been completed, staff work towards targets, and decisions yield the desired outcomes.
* **Intervening** Metrics, especially leading indicators (see section 2.2.2.5), are triggers for corrective actions.

The most common measurement categories are:
* **Performance** What is achieved by the managed object?
* **Maturity** Does the object have necessary capabilities to fulfil its purpose?
* **Compliance** Does the object comply with internal and/or external requirements?

#### 2.2.1.2 Methods of measurement
There are two common methods of measurement:
* calculations based on data from tracking and monitoring tools
* surveys.

Information systems provide objective information about managed objects. However, this information is often entered manually and can therefore be inaccurate. ‘Obtained from an information system’ does not always mean ‘reliable’.

Information based on surveys is more subjective, but some metrics can only be obtained by surveying people. For example, understanding and improving the quality of a service is impossible without considering the subjective users’ perspective.

### 2.2.2 Metrics
<table><tbody><tr><td><strong>Definition: Metric</strong></td></tr><tr><td>A measurement or calculation that is monitored or reported for management and improvement.</td></tr></tbody></table>

Metric data can be collected technically or procedurally; regardless of the source and collection methods, metrics always describe a management object. Typical management objects relevant to most ITIL practitioners are services, practices, configuration items, and service management activities.

Different metrics describe different aspects of a management object. For example, practice metrics can refer to practice’s effectiveness, efficiency, productivity, or conformance.

It is essential to combine metrics of different types in order to build a holistic measurement system. This enables a multidimensional view of the task at hand. The reverse is also true: the absence of a certain type of metric in a measurement system can cause some characteristics of a management object to be left unmeasured.

#### 2.2.2.1 Effectiveness metrics
These metrics indicate the degree to which an activity (or a group of interrelated activities) fulfils its purpose and achieves its objectives. For ITIL practices, these metrics can be derived from practice purpose statements and practice success factors (PSFs).

<table><tbody><tr><td><p><strong>Tip</strong></p></td></tr><tr><td><p>The metric examples in section 2.5 of the ITIL practice guides are mapped to PSFs, which are described in section 2.4.</p></td></tr></tbody></table>

#### 2.2.2.2 Efficiency metrics
These metrics describe how an organization utilizes resources to perform activities and manage products and services. An example of an efficiency metric for the change enablement practice is the percentage of changes implemented by the first attempt, with no re-work required.

#### 2.2.2.3 Productivity metrics
These metrics describe the amount of work that is performed and the resulting outputs. These metrics can also be described as the ‘throughput’ of a practice. An example of a productivity metric for the problem management practice is its productivity index, which could be defined as (N + C) / (O + C), where N is the number of new problems registered but not closed within a period, O is the total number of problems open at the end of the period, and C is the number of problems processed and closed within the period. This indicates how many problems go through the practice pipeline within a period compared to the number of problems accumulated from past periods.

#### 2.2.2.4 Conformance metrics
These metrics are of interest mostly to managed object owners and governing bodies. An example of a conformance metric for the service level management practice could be the percentage of service reports delivered to customers on time.

For a classification of metrics applicable to organization’s resources in the four dimensions of service management, refer to section 4.3 of ITIL® 4: Direct, Plan and Improve.

#### 2.2.2.5 Lagging and leading metrics
Lagging metrics report what has already been achieved. For example, ‘the percentage of user requests processed on time was 87%.’ These metrics provide useful information to managers and customers, but there is limited ability to influence them. A practitioner cannot directly change the timeliness of request handling; they can only organize an activity that yields the desired outcome.

Leading metrics help to predict what is likely to happen in the future. Leading indicators are often difficult to measure, but fairly easy to influence. For example, a manager can alter the speed of service desk staff’s reaction to incoming calls by increasing resources or by adjusting the queue-handling rules. These efforts can be measured with such indicators as ‘an average number of requests per specialist’, or ‘a percentage of requests moved into the in-progress state over a period’. These leading indicators are not informative to the customer or users but improving them can positively impact the user experience.

### 2.2.3 Key performance indicators
Metrics are useful when they support decision-making by indicating important aspects of a managed object; in other words, when they serve as indicators. The most important indicators are known as key performance indicators (KPIs).

<table><tbody><tr><td><p><strong>Definition: Indicator</strong></p></td></tr><tr><td>A metric that is used to assess and manage something.</td></tr><tr><td><strong>Definition: </strong><span><strong>Key performance indicator</strong></span></td></tr><tr><td>An important metric used to evaluate the success in meeting an objective.</td></tr><tr><td><strong>Definition: Performance</strong></td></tr><tr><td><p>A measure of what is achieved or delivered by a system, person, team, practice, or service.</p></td></tr></tbody></table>

A metric is only a KPI when it is crucial for the assessment of an object’s state. The management context differentiates metrics that indicate key information and those that are supplementary. Indicators are ‘key’ when they describe the most important properties of an object or the factors that significantly affect those properties (for example, a factor which describes the severity of a bottleneck).

KPIs help to assess the state of an object in terms such as ‘good’ or ‘bad’, ‘acceptable’ or ‘unacceptable’. A metric can only be used as a KPI if it has an agreed target value and a tolerance (acceptable deviation from the target value).

The majority of indicators used for services and practices also have a ‘target trend’: they should either rise or decline. For example, the timeliness of completing changes should increase, and time-to-market (TTM) should decrease. In these examples, the bands of tolerance are mono-directional. If the target trend of an indicator is growth, then its tolerance will be lower than the target value.

To use metrics as KPIs, it is important to:
* identify the key metrics
* define target values and trends
* define tolerances.

#### 2.2.3.1 KPIs and behaviour
KPIs can motivate individuals, driving positive results. However, setting targets for individuals can also drive undesirable behaviours; for example, service desk staff might be pressured to keep calls short, which can negatively impact customer satisfaction and resolution times.

Operational KPIs should ideally be set for teams, not individuals. This means that there can be some flexibility in the targets and behaviours allowed to the team as a whole. Individuals will need specific guidelines for their performance, but these should be within the team’s objectives and all targets should be set in the context of enabling value for the organization. Focus on value, not on micro-objectives.

### 2.2.4 Reports
Information based on measurement is usually presented as reports or dashboards. Reports are supposed to support decision-making, so they should be relevant to their recipients and the topic.

Reports and dashboards should make it easy for the stakeholder to see what needs to be done and take action.

A good report or dashboard should answer two main questions:
* where are we compared to the agreed targets?
* what prevents us from achieving better results?

To support decision-making, reports usually include data analysis, such as a comparison of:
* current metrics’ values with targets
* current metrics’ values with past values
* different (relevant) current metrics.

Reports can also describe possible causes of the current state, highlight risks, suggest corrective and preventive actions, and other recommendations.

Depending on the purpose and content, reports can be either operational or analytical in style.

#### 2.2.4.1 Operational reports
Operational reports are created to monitor performance, identify deviations, and initiate corrective actions to support operations.

Operational reports are fact-based, including calculations, comparisons, correlations, and so on. These may include events and incidents statistics, service outage information, the percentage of tasks performed according to agreed targets, correlations between quality and amount of work performed, and so on. Such data can often be collected automatically (through workflow management systems, monitoring tools, and other means of automation).

If automated, operational reports can be produced promptly and often (daily or multiple times per day). This makes operational reports sources of very recent data.

A dashboard is an operational report with the following key properties:
* It displays only the most relevant data.
* All data is presented on a single screen.
* It is accessible online (in contrast to paginated reports, which are usually distributed through email or on paper).

Data on dashboards can be updated in real time, by schedules, or on demand. This means that recent information about managed objects can be available whenever it is needed. Historical data may become unavailable, or have limited availability, as dashboards update.

#### 2.2.4.2 Analytical reports
Analytical reports reveal hidden problems or bottlenecks, then identify possible causes and improvement opportunities. Unlike operational reports, which are mostly focused on facts and their interpretation, analytical reports deal with data analysis, trends and their explanations, and deep investigations into what is happening and how it can be influenced by managers.

Such reports are usually produced by skilled analysts, who can be employees or external consultants. Depending on scope of the assessment, an analytical report can be run within several days to a few months. For this reason, analytical reports are created much less often than operational ones and support decisions for longer, sometimes for over a year.

Analytical reports are usually paginated and published in a designated area or sent to relevant stakeholders. They may be subject to a formal approval process before they are used to guide management decisions and further actions.

## 2.3 Scope
For the agreed managed objects, the measurement and reporting practice includes:
* defining a measurement and reporting approach
* ensuring that the agreed approach is followed across the organization
* consistently integrating measurement and reporting activities into the organization’s value streams
* maintaining sufficient quality of the management reporting, meeting the organization’s needs and requirements
* continually reviewing and optimizing measurements and reports across the organization.

There are several activities and areas of responsibility that are not included in the measurement and reporting practice, although they are still closely related to measurement and reporting. These are listed in Table 2.1, along with references to the practices in which they can be found. It is important to remember that ITIL practices are merely collections of tools to use in the context of value streams; they should be combined as necessary, depending on the situation.

### Table 2.1 Activities related to the measurement and reporting practice described in other practice guides
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Practice guide</strong></p></td></tr><tr><td><p>Communicating with stakeholders in order to clarify goals and reporting requirements</p></td><td><ul><li>Relationship management</li><li>Service desk</li><li>Supplier management</li></ul></td></tr><tr><td><p>Producing reports on practices, products, services, relationships, initiatives, and resources</p></td><td><p>All practices</p></td></tr><tr><td><p>Measurement-based incentives planning and realization</p></td><td><p>Workforce and talent management</p></td></tr><tr><td><p>The ongoing management and implementation of improvements</p></td><td><p>Continual improvement</p></td></tr></tbody></table>

## 2.4 Practice success factors
<table><tbody><tr><td><strong>Definition: Practice success factor</strong></td></tr><tr><td>A complex functional component of a practice that is required for the practice to fulfil its purpose.</td></tr></tbody></table>

A practice success factor (PSF) is more than a task or activity, as it includes components of all four dimensions of service management. The nature of the activities and resources of PSFs within a practice may differ, but together they ensure that the practice is effective.

The measurement and reporting practice includes the following PSFs:
* ensuring that measurements are driven by objectives
* ensuring the quality and availability of measurement data
* ensuring effective reporting to support decision-making.

#### 2.4.1 Ensuring that measurements are driven by objectives
Measurements are only valuable when they help managers achieve their objectives. Useful measurements are linked to objectives.

The planning and evaluation model, shown in Figure 2.1 and described in section 4.2.2.1 of ITIL® 4: Direct, Plan and Improve, illustrates the direct connection between the purpose, objectives, indicators, and metrics of a managed object.

![Image of Figure 2.1 shows planning and evaluation model - coloured shapes in a row horizontally each with a word on them - Purpose, Objectives, Indicators and Metric, with two sperate vertical lines at each end saying Define and Evaluate](Measurement%20and%20reporting%20management%20Practice%20Guide/Picture1.png "**Figure 2.1 Planning and evaluation model**")

There are several steps involved in forming a measurement and evaluation system based on a purpose and a set of objectives. These steps are universally applicable to any managed object, whether it is a service, practice, project, or a resource<sup>2</sup>.

#### 2.4.1.1 Step 1: Define the objectives
The first step is the most important. It is defining objectives and agreeing what the measurement and evaluation system will be used for. All following steps depend on the quality of the objective-setting.

Objectives are typically based on the agreed purpose of the managed object and ensuring that the purpose will be fulfilled.

For a project or another one-off activity, defining objectives is usually simple because projects are normally undertaken to achieve a particular outcome. Moreover, in many organizations projects require formal justification, due diligence, and a written explanation; they must be formally accepted by an authoritative body, such as a board of directors.

For practices, products, and services, objectives are normally linked to one of the four types of indicators: effectiveness, conformance, efficiency, or productivity. Objectives should also be SMART. For example, a purpose statement could be ‘ensuring IT service quality by completing changes on time and maintaining minimal levels of IT risk’. A related SMART objective could be ‘90% of changes being made on time by the end of the year.’

#### 2.4.1.2 Step 2: Identify success factors
Most objectives require further decomposition for effective management and measurement. If this is the case, defining success factors usually helps.

A success factor describes a condition or characteristic that must be achieved for something to be considered successful.

For example, success factors related to an ITIL practice are called practice success factors (PSFs). Every ITIL practice guide describes PSFs of the practice in section 2.4.

Identifying success factors is a distinct stage of project planning and risk management activities. There are no common rules for smaller-scale activities; some organizations systematically identify success factors, and others disregard them altogether and map indicators directly to the objectives.

#### 2.4.1.3 Step 3: Select metrics and measurement tools
At this step, metrics are selected for the identified objectives and success factors. Metric classifications help to ensure the completeness of the measurement system. If objectives and success factors are properly defined, metrics should not be difficult to identify.

Metrics should be selected with regard to the measurement tools available. Technology capabilities can seriously limit what can be measured. Sometimes, it is possible to compensate for technical limitations with organizational measures, such as by gathering data manually, but manual solutions are more expensive and normally provide delayed and less accurate data.

#### 2.4.1.4 Step 4: Form a system of key performance indicators
The next step is to define KPIs based on the selected metrics. This involves picking the most important metrics and establishing target values, trends, and thresholds for each of them based on the agreed objectives and success factors.

The resulting system of KPIs must be balanced. The system should be able to identify, for example, whether some aspects of an object’s state are being ignored in favour of others (for example, if quality is neglected in pursuit of speed). Table 2.1 outlines some example KPIs for the change enablement practice.

### Table 2.1 Example KPIs for the change enablement practice
<table><tbody><tr><td><p><strong>KPI</strong></p></td><td><p><strong>Unit</strong></p></td><td><p><strong>Target trend </strong></p></td><td><p><strong>Target value</strong></p></td><td><p><strong>Threshold value</strong></p></td></tr><tr><td><p>Percentage of changes completed on time</p></td><td><p>%</p></td><td><p>Upward</p></td><td><p>90</p></td><td><p>50</p></td></tr><tr><td><p>Percentage of emergency changes</p></td><td><p>%</p></td><td><p>Downward</p></td><td><p>5</p></td><td><p>10</p></td></tr><tr><td><p>Percentage of changes completed on the first attempt</p></td><td><p>%</p></td><td><p>Upward</p></td><td><p>98</p></td><td><p>90</p></td></tr></tbody></table>

#### 2.4.1.5 Step 5: Aggregate the measurement data
The final step is selecting an aggregation algorithm to calculate the final score.

Aggregating KPIs can be difficult because they are often expressed in different units and may have different target trends. To eliminate these differences, KPIs are often transformed into percentage ratings using the following formula:

![](Measurement%20and%20reporting%20management%20Practice%20Guide/Formula.png)

where K is the actual value of the metric, T is the target value, and M is the threshold.

This formula helps to express various metrics in normalized percentage ratings. Their values can be grouped into zones:
* a green zone representing achieved target (100%)
* a yellow zone representing performance between threshold and target values
* a red zone for performance below the threshold (0%).

This is shown in Figure 2.2.  

![Image of Figure 2.2 shows a coloured-coded aggregate normalized KPI rating](Measurement%20and%20reporting%20management%20Practice%20Guide/Picture2.png "**Figure 2.2 Colour-coded normalized rating**")

Normalized KPIs can be aggregated to produce a performance scorecard. This usually involves assigning weights according to each KPI’s relative importance. The performance scorecard provides a structured visualization of the measurement and evaluation results that can enable decision-making.

There are multiple approaches to aggregating KPIs, including weighted arithmetic average, multiplication, dynamic weights, and others.

#### 2.4.1.6 Summary
So, there are five steps:
* define the objectives
* identify success factors
* select metrics and measurement tools
* form a system of key performance indicators
* aggregate the measurement data.

These steps are universally applicable to any managed object, whether it is a service, practice, project, or a resource. It is also possible to use this method to create an organization-wide measurement and evaluation system.

The example below illustrates how the described approach could be applied to a measurement and assessment of a service.

<table><tbody><tr><td colspan="2"><strong></strong><span><strong>Example: Measuring and assessing a ‘Company’s website’ service</strong></span></td></tr><tr><td><p><strong>Step</strong></p></td><td><p><strong>Example outputs</strong></p></td></tr><tr><td><p>1. Set the objectives</p></td><td><p>“Ensure and support service quality level of 100%”</p></td></tr><tr><td><p>2. Identify success factors</p></td><td><p>Identify customer quality characteristics requirements based on the user’s actions and agreed service level:</p><ul><li>User authentication should not take longer than 5 seconds</li><li>Website should not be unavailable for more than 15 hours a month</li><li>A single downtime cannot be longer than 4 hours</li></ul></td></tr><tr><td><p>3. Select metrics and measurement tools</p></td><td><p>Based on the measurement tools available, select the following metrics:</p><ul><li>K1: percentage of authentication requests processed on time of the total number of authentication requests, %</li></ul><ul><li>K2: total unavailability duration in a month, hours</li><li>K3: longest duration of a single downtime in a month, hours.</li></ul></td></tr><tr><td><p>4. Form a system of KPIs</p></td><td><p>Based on agreed service levels, define the target and threshold values to form a system of KPIs:</p><ul><li>K1: Target T1 = 95%, Threshold M1 = 80%</li><li>K2: Target T2 = 5 hours, Threshold M2 = 15 hours</li><li>K3: Target T3 = 2 hours, Threshold M3 = 4 hours.</li></ul></td></tr><tr><td><p>5. Aggregate the measurement data</p></td><td><p>Based on the KPIs create a performance scorecard and choose the aggregation algorithm to calculate the final score.</p></td></tr></tbody></table>

### 2.4.2 Ensuring the quality and availability of measurement data
Without data, there are no reports. If data is incomplete, inaccurate, or inconsistent, poor decisions might be made. Ensuring data quality and availability is a critical part of the measurement and reporting practice. High-quality data should be intrinsically good, contextually appropriate for the task, clearly represented, and accessible to the data consumer:
* **Intrinsically good** includes the accuracy, objectivity, believability, and reputation of the data source.<sup>3</sup>
* **Contextually appropriate** data is useful and valuable in the given context. It includes completeness, relevancy, timeliness, and volume.
* **Clearly** represented data is understandable, consistent, and interpretable.
* **Accessible data** is available to the designated consumers and can be accessed as agreed.

The measurement and reporting practice is primarily focused on ensuring the contextual and representational quality of measurement information.

The practice also defines requirements for monitoring and measurement tools (see section 3.2.1) and the gathering and processing of data required for reports (see section 3.2.2) in order to ensure quality in all four areas. However, intrinsic quality of the data is ensured by other practices (monitoring and event management, service desk, all practices keeping records used as data sources); accessibility of the information is ensured by the availability management and information security management practices.

### 2.4.3 Ensuring effective reporting to support decision-making
To ensure that reports help with decision-making, reports should be designed to answer the following questions:
* **Who is the report consumer?** The report consumer is the manager whose decisions will be supported by the report. This person is the main source of requirements.
* **What is the purpose of the report?** What decisions it is supposed to support?
* **Who will generate and work with the report?**  
    The answer can influence how the report will be delivered, who will have access to it, and on which devices and media the report will be used.
* **How will the report be used?** The answer to this question informs what data should be included in the report, how often it should be generated, and which interactive capabilities it should have.
* **What data should the report contain?** The answer to this question helps to identify the KPIs that should be included in the report, supplementary data that is needed, time periods that the report should span, data sources that contain the required data, and the way data will be obtained from different sources.
* **How will the report data be structured and displayed?** Many techniques can be used to structure and display data. These include:
    * grouping KPIs to present the report in logical blocks, each of which addresses a certain topic
    * aggregating several KPIs to indicate overall success, thereby helping to identify where more work is needed
    * defining how the report will help to identify bottlenecks by grouping data based on analytical attributes, such as by region or service
    * choosing proper visualization techniques, such as tables, charts, or diagrams.

## 2.5 Key metrics
The effectiveness and performance of the ITIL practices should be assessed within the context of the value streams to which each practice contributes. As with the performance of any tool, the practice’s performance can only be assessed within the context of its application. However, tools can differ greatly in design and quality, and these differences define a tool’s potential or capability to be effective when used according to their purpose.

Key metrics for the measurement and reporting practice are mapped to its PSFs. They can be used as KPIs in the context of value streams to assess the contribution of the practice to the effectiveness and efficiency of those value streams. Some examples of key metrics are given in Table 2.3.

### Table 2.3 Examples of key metrics for the practice success factors
<table><tbody><tr><td><p><strong>Practice success factors</strong></p></td><td><p><strong>Key metrics</strong></p></td></tr><tr><td><p>Ensuring that measurements are driven by objectives</p></td><td><p>Percentage of objectives covered by measurement and evaluation systems and reports</p></td></tr><tr><td><p>Ensuring the quality and availability of measurement data</p></td><td><ul><li>Data-to-errors ratio</li><li>Percentage of reports produced without data errors</li><li>Data time-to-value (TTV)</li><li>Report consumers’ satisfaction with data quality</li></ul></td></tr><tr><td><p>Ensuring effective reporting to support decision-making</p></td><td><ul><li>Percentage of reports generated automatically</li><li>Timely report generation</li><li>Reporting on consumer satisfaction</li></ul></td></tr></tbody></table>

The correct aggregation of metrics into complex indicators (see 2.4.1) will make it easier to use the data for the ongoing management of value streams, and for the periodic assessment and continual improvement of the measurement and reporting practice. There is no single best solution. Metrics will be based on the overall service strategy and priorities of an organization, as well as on the goals of the value streams to which the practice contributes.

## 3.1 Value streams contribution
Like any other ITIL management practice, the measurement and reporting practice contributes to multiple value streams. It is important to remember that a value stream is never formed from a single practice. The measurement and reporting practice combines with other practices to provide high-quality services to consumers. The main value chain activities to which the practice contributes are:
* plan
* improve
* design and transition
* engage
* obtain/build
* deliver and support.

The contribution of the measurement and reporting practice to value chain activities can be seen in Figure 3.1.

![Image of Figure 3.1 shows heat map of the contribution of the measurement and reporting practice to Value Chain activities](Measurement%20and%20reporting%20management%20Practice%20Guide/Picture3.png "**Figure 3.1 Heat map of the contribution of the measurement and reporting practice to value chain activities**")

## 3.2 Processes
Each practice may include one or more processes and activities that may be necessary to fulfil the purpose of that practice.

<table><tbody><tr><td><strong>Definition: Process</strong></td></tr><tr><td>A set of interrelated or interacting activities that transform inputs into outputs. A process takes one or more defined inputs and turns them into defined outputs. Processes define the sequence of actions and their dependencies.</td></tr></tbody></table>

The measurement and reporting practice forms two processes:
* designing the measurement and reporting system
* reporting and evaluating.

### 3.2.1 Designing the measurement and reporting system
This process includes the activities shown in Table 3.1 and transforms the inputs into outputs.

### Table 3.1 Inputs, activities, and outputs of the designing the measurement and reporting system process
<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Purpose and objectives</li><li>Success factors</li><li>Measurement tools and capabilities</li><li>Available data</li><li>SLRs/SLAs and contracts</li><li>Existing report(s)/actual performance</li><li>Reporting requirements</li></ul></td><td><ul><li>Developing metrics and measurement methods</li><li>Forming KPI scorecards</li><li>Designing report templates and reporting policy</li></ul></td><td><ul><li>Metrics</li><li>Measurement requirements</li><li>Measurement methods</li><li>KPI scorecard(s)</li><li>Report template(s)</li><li>Reporting policy</li></ul></td></tr></tbody></table>

![Image of Figure 3.2 show a workflow diagram of the Measurement and Reporting systems process](Measurement%20and%20reporting%20management%20Practice%20Guide/Picture4.png "**Figure 3.2 Workflow of the designing the measurement and reporting system process**")

These activities may be carried out with varying levels of formality by many people in the organization. Table 3.2 gives some examples of the process activities.

### Table 3.2 Activities of the designing the measurement and reporting system process
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Developing metrics and measurement methods</p></td><td><p>Based on the purpose, objectives, and success factors of the managed object, metrics and measurement methods are developed. See section 2.4.1.3 for details.</p></td></tr><tr><td><p>Forming KPI scorecards</p></td><td><p>Target values and thresholds are established based on the most important metrics. See section 2.4.1.4 for details.</p></td></tr><tr><td><p>Designing report templates and reporting policy</p></td><td><p>To support decision-making, data should be presented clearly and concisely, usually as reports or dashboards.</p><p>Specific reporting requirements may be introduced by the customer or the organization. Developed reports must comply with them.</p><p>A reporting policy should also be developed. This includes:</p><ul><li>the targeted audience(s) and specific tailored views</li><li>requirements for the data structure and the reports’ parameters</li><li>agreement on what to measure and report</li><li>definitions of all terms and boundaries</li><li>the methods of calculations</li><li>reporting schedules</li><li>access to reports and the medium to be used</li><li>interface and usability requirements (sorting, filtering, links to related reports and detailed data, forecasting, and so on)</li><li>meetings scheduled to review and discuss reports.</li></ul></td></tr></tbody></table>

#### 3.2.1.1 Reporting and evaluation
This process includes the activities listed in Table 3.3 and transforms the inputs into outputs.

### Table 3.3 Inputs, activities, and outputs of the reporting and evaluation process
<table><tbody><tr><td><p><strong>Key inputs</strong></p></td><td><p><strong>Activities</strong></p></td><td><p><strong>Key outputs</strong></p></td></tr><tr><td><ul><li>Measurements</li><li>Monitoring data</li><li>Report template</li><li>Reporting policy</li></ul></td><td><ul><li>Data gathering and processing</li><li>Data analysis and reporting</li><li>Report evaluation and decision-making</li></ul></td><td><ul><li>Operational reports</li><li>Analytical reports</li><li>Improvement initiatives</li></ul></td></tr></tbody></table>

Figure 3.3 shows a workflow diagram of the process.

![Image of Figure 3.3 show workflow diagram of the Reporting and Evaluation process](Measurement%20and%20reporting%20management%20Practice%20Guide/Picture6.png "**Figure 3.3 Workflow of the reporting and evaluation process**")

These activities may be carried out with varying levels of formality by many people in the organization. Table 3.4 provides examples of the process activities.

### Table 3.4 Activities of the reporting and evaluation process
<table><tbody><tr><td><p><strong>Activity</strong></p></td><td><p><strong>Description</strong></p></td></tr><tr><td><p>Data gathering and processing</p></td><td><ul><li>Measurement data is gathered with multiple tools, including service management, monitoring, reporting, investigation, and discovery systems.</li><li><span>Data can also be collected through a manual or semi-manual procedures, such as customer and user surveys. The accuracy and integrity of the data should always be maintained.</span>It is also important for staff to document their compliance activities, to update logs and records. Ongoing communication about the benefits of performing administrative tasks is crucial because it directly impacts data and KPI accuracy. Tying these administrative tasks to job performance can alleviate this issue.</li><li><p>The gathered data then needs to be processed. This activity begins the transformation of raw data into information packaged and formatted for the target audience. This usually involves sorting, ordering (such as by time series), normalizing, mapping, labelling, grouping, and correlating. Report-generating technologies are typically used at this stage. The data is also typically formatted to provide an end-to-end perspective on the overall performance of a service or process.</p></li><li><span>The outputs can be final or used to create more sophisticated reports in the next step.</span></li></ul></td></tr><tr><td><p>Data analysis and reporting</p></td><td><p>Data analysis transforms information into knowledge about the current situation, how it is affecting the organization, and how it relates to goals and objectives. Key questions can be answered based on the data analysis.</p><p>A common incorrect assumption is that the automated processing, reporting, and monitoring tools perform the analysis. Too often, people observe a trend and neglect to ask key questions, such as what does it mean and how does it impact the organization?</p><p>Data analysis involves making judgements and answering the questions like:</p><ul><li>Are targets met?</li><li>Are there any clear trends, positive or negative?</li><li>Are we operating according to plan?</li><li>Are any changes needed to improve the situation?</li><li>Are there underlying problems?</li></ul><p>Without analysis, reports are merely information. With analysis come knowledge and improvement opportunities.</p><p>The information should be presented in a format that is understandable and targeted, provides value, and informs decision-making. The report should emphasize areas where the recipient needs to act.</p></td></tr><tr><td><p>Report evaluation and decision-making</p></td><td><p>The knowledge, combined with previous experience, enables informed decision-making about optimizing, improving, and correcting services and processes.</p><p>There are four management tasks that measurements can help with:</p><ul><li>influencing behaviour</li><li>justifying changes</li><li>validating decisions</li><li>intervening with corrective actions.</li></ul><p>Improvement proposals should then be assessed, prioritized, approved, and planned as a part of the continual improvement practice.</p></td></tr></tbody></table>

## 4.1 Roles, competencies, and responsibilities
The practice guides do not describe the practice management roles such as practice owner, practice lead, or practice coach. They focus instead on the specialist roles that are specific to each practice. The structure and naming of each role may differ from organization to organization, so any roles defined in ITIL should not be treated as mandatory, or even recommended. Remember, roles are not job titles. One person can take on multiple roles and one role can be assigned to multiple people.

Roles are described in the context of processes and activities. Each role is characterized with a competency profile based on the model shown in Table 4.1.

### Table 4.1 Competency codes and profiles
<table><tbody><tr><td><p><strong>Competency code</strong></p></td><td><p><strong>Competency profile (activities and skills)</strong></p></td></tr><tr><td><p><strong>L</strong></p></td><td><p><strong>Leader </strong>Decision-making, delegating, overseeing other activities, providing incentives and motivation, and evaluating outcomes</p></td></tr><tr><td><p><strong>A</strong></p></td><td><p><strong>Administrator </strong>Assigning and prioritizing tasks, record-keeping, ongoing reporting, and initiating basic improvements</p></td></tr><tr><td><p><strong>C</strong></p></td><td><p><strong>Coordinator/communicator </strong>Coordinating multiple parties, maintaining communication between stakeholders, and running awareness campaigns</p></td></tr><tr><td><p><strong>M</strong></p></td><td><p><strong>Methods and techniques expert </strong>Designing and implementing work techniques, documenting procedures, consulting on processes, work analysis, and continual improvement</p></td></tr><tr><td><p><strong>T</strong></p></td><td><p><strong>Technical expert </strong>Providing technical (subject matter) expertise and conducting expertise-based assignments</p></td></tr></tbody></table>

Examples of roles which can be involved in the measurement and reporting practice are listed in Table 4.2, together with the associated competency profiles and specific skills.

### Table 4.2 Examples of roles with responsibility for measurement and reporting activities
| Activity | Responsible Roles | Competency Profile | Specific Skills |

 |
| --- | --- | --- | --- |

**Designing the measurement and reporting system**
Developing metrics and measurement methods
* Subject matter expert (process manager, service manager, functional manager, HR professional),
* Quality manager
MT
* Understanding the purpose, objectives, and success factors of the managed object
* Basic knowledge of the measurement and evaluation method
* Metrics development skills
* Understanding of measurement methods and monitoring techniques
Forming KPI scorecards
* Subject matter expert
* Quality manager
* Reporting manager
M
* Understanding of how metrics are interrelated
* Basic knowledge of measurement and assessment method
* Basic math skills
* Experience with spreadsheets
* KPI development skills
Designing report templates and reporting policy
* Subject matter expert
* Quality manager
* Reporting manager
* Analytics tool administrator
MT
* Understanding of the report's customer, users, and related tasks
* Basic visual design skills
* Understanding of data-structuring and presentation techniques
* Understanding of the decision-making process
* Experience with tools for analytics
**Reporting and evaluation**
Data gathering and processing
* Analyst
* Reporting manager
* Analytics tool administrator
* Subject matter expert
AT
* Analytical skills
* Experience with tools for analytics
* Experience with spreadsheets
Data analysis and reporting
* Analyst
* Reporting manager
* Analytics tool administrator
* Subject matter expert
* Quality manager
MT
* Understanding of the measurement object’s and its context
* Communication skills
Report evaluation and decision-making
* Senior manager
* Team leader
* Subject matter expert
* Quality manager
LM
* Excellent understanding of the measurement object and its context
* Communication skills
* Writing skills
* Good business judgement

## 4.2 Organizational structures and teams
The measurement and reporting practice underpins everything the organization does to enable value co-creation, and it is therefore everyone’s responsibility. For example, practice managers should measure and assess practices in order to improve their effectiveness and efficiency; service and product managers need to provide service quality reports to customers in order to enable improvement.

Practical aspects of the measurement system development and the ongoing management of the measurement and reporting approach are often delegated to the quality management team, if there is a dedicated team in the organization.

## 5.1 Information exchange, inputs/outputs
The effectiveness of the measurement and reporting practice is based on the quality of the information used. This information includes, but is not limited to, information about:
* organization’s objectives of various levels
* organization’s portfolios and service offerings
* external reporting requirements
* infrastructure monitoring data
* application monitoring data
* business transaction monitoring data
* service management records (incidents, changes, and so on)
* customer and user feedback.

Information which is gathered and processed is primarily used for producing reports but might be valuable in a variety of cases, such as audits, quality management, continual improvement, service validation, and so on. Therefore the measurement and reporting practice should be concerned about the quality of data (see section 2.4.2).

Metrics are usually presented as reports or dashboards, which are intended to support good decision-making. They should be relevant to the recipients of the information and related to the required topic. Reports and dashboards should make it easy for the recipient to see what needs to be done and then take action.

The content, structure, and representation of information in reports directly impact the efficiency of decision-making. To support the decision-making process, reports should include not only the measured data, but also the result of processing, and sometimes data analysis, including:
* targets vs actual values, to detect deviations from and assessment of the current state
* KPI behavior over time, to identify trends and dynamics
* comparing and correlating KPIs, to analyze trends and identify bottlenecks.

The key inputs and outputs of the practice are listed in section 3.

## 5.2 Automation and tooling
In most cases, the measurement and reporting practice can significantly benefit from automation. Where this is possible and effective, it may involve the solutions outlined in Table 5.1.  

### Table 5.1 Automation solutions for measurement and reporting activities
<table><tbody><tr><td><p><strong>Process activity</strong></p></td><td><p><strong>Means of automation</strong></p></td><td><p><strong>Key functionality</strong></p></td><td><p><strong>Impact on the effectiveness of the practice</strong></p></td></tr><tr><td colspan="4"><strong>Designing the measurement and reporting system</strong></td><td></td></tr><tr><td><span>Designing the measurement and reporting system</span></td><td rowspan="2"><ul><li>Spreadsheets</li><li><span>Visualization tools (such as mind maps)</span></li></ul></td><td rowspan="2"><ul><li>Listing and visualizing metric interrelations</li><li>Balancing metrics and choosing an aggregation method</li></ul></td><td>Low</td><td></td></tr><tr><td><span>Forming KPI scorecards</span></td><td>Medium</td><td></td></tr><tr><td><p>Designing report templates and reporting policy</p></td><td><p>Reporting and dashboarding tools, service portals, and apps</p></td><td><p>Designing reports and dashboard templates</p></td><td><p>Low to high, depending on the volume of services, processes, and stakeholders</p></td></tr><tr><td colspan="4"><strong>Reporting and evaluation</strong></td><td></td></tr><tr><td><p>Data gathering and processing</p></td><td><p>Infrastructure and platform built-in monitoring tools, service management tools, monitoring tools, reporting tools, investigation and discovery tools, and others</p></td><td><p>Active and reactive monitoring, data gathering, and processing</p></td><td><p>High</p></td></tr><tr><td><p>Data analysis and reporting</p></td><td><p>Spreadsheets, reporting and dashboarding tools, advanced analytics tools, service portals and apps, and email and other communication tools, including social media</p></td><td><ul><li>Data manipulation (sorting, filtering, and so on)</li><li>Report presentation</li></ul></td><td><p>Low to high, depending on the volume of services, processes, and stakeholders</p></td></tr><tr><td><p>Report evaluation and decision-making</p></td><td><p>Spreadsheets, reporting and dashboarding tools, advanced analytics tools, service portals</p><p>CIR</p></td><td><ul><li>Accessing and viewing reports and dashboards</li><li>Logging initiatives to the CIR</li></ul></td><td><p>Medium</p></td><td></td></tr></tbody></table>

Very few services are delivered using only an organization’s own resources. Most, if not all, depend on other services, often provided by third parties outside the organization (see section 2.4 of ITIL Foundation: ITIL 4 Edition for a model of a service relationship). Relationships and dependencies introduced by supporting services are described in the ITIL practice guides for service design, architecture management, and supplier management.

Suppliers and partners provide services to the organization and contribute to the organization’s value streams. Related third-party contracts, services, and relationships are therefore objects for measurement and evaluation.

Suppliers might also play a significant role in measurement and reporting, enhancing the organization’s capabilities with data management, reporting, and analytics. The development of reporting and dashboarding tools and apps for advanced analytics made external measurement and reporting services very popular. Also, there are many built-in monitoring tools, built-in reporting and analytics functionalities within service management tools, and others that are available as a part of vendors’ service offerings.

Most of the content of the practice guides should be taken as a suggestion of areas that an organization might consider when establishing and nurturing their own practices. The practice guides are catalogues of topics that organizations might think about, not a list of answers. When using the content of the practice guides, organizations should always follow the ITIL guiding principles:
* focus on value
* start where you are
* progress iteratively with feedback
* collaborate and promote visibility
* think and work holistically
* keep it simple and practical
* optimize and automate.

More information on the guiding principles and their application can be found in section 4.3 of *ITIL Foundation: ITIL 4 Edition.*

AXELOS Ltd is grateful to everyone who has contributed to the development of this guidance. These practice guides incorporate an unprecedented level of enthusiasm and feedback from across the ITIL community. In particular, AXELOS would like to thank the following people.

## 8.1 Authors
Pavel Demin, Dmitriy Isaychenko.

## 8.2 Contributors
Nikolay Butrimovich, Roman Jouravlev.

## 8.3 Reviewers
Erika Flora, Graham Heard, Anton Lykov, Irina Matantseva.

## References
1.  For more on the four reasons for measurement, see ITIL® 4: Direct, Plan and Improve, section 4.1.3Organizations measure their activities, resources (in all four dimensions of service management), and products and services.
2.  https://www.linkedin.com/pulse/five-steps-build-kpi-scorecard-almost-anything-dmitry-isaychenko/ (Accessed 16th April 2020)
3.  Richard Y. Wang and Diane M. Strong, ‘Beyond Accuracy: What Data Quality Means to Data Consumers’ Journal of Management Information Systems, Vol. 12, No. 4 (Spring, 1996), pp. 5-33 https://www.jstor.org/stable/40398176
