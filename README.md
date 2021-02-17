# Google Summer of Code 2021
Google Summer of Code (GSoC) 2021 is an international annual program run by Google for college students interested in getting a stipend to contribute to open source projects. 
Percona, a leader in open source database software and services, has been a dedicated supporter of the open source community since starting as a business in 2006, 
and has actively contributed to the community by providing bug fixes for open source projects, engineering open source software for use and redistribution, and hosting the [Percona Live Open Source Database Conferences](https://www.percona.com/live/conferences) twice a year.


Percona is participating<sup>*</sup> in the GSoC 2021, and sees it as an excellent opportunity for students to participate in the active and vibrant open source community.
Our GSoC Projects are focussed on improving Percona Monitoring and Management (PMM) , which is an open source platform for managing and monitoring MySQL, PostgresQL & MongoDB performance. It provides thorough time-based analysis for MySQL, PostgresQL & MongoDB servers to ensure that your data works as efficiently as possible.

[Visit the Google Summer of Code website to learn more.](https://summerofcode.withgoogle.com/)

1) [Google Summer of Code Timeline](https://summerofcode.withgoogle.com/how-it-works/#timeline)
2) [Google Summer of Code guides](https://developers.google.com/open-source/gsoc/resources/guide)

<sup>*</sup> Percona has applied to GSoC 2021 program, and is awaiting results for organization selection. This will be announced by Google on March. 10, 2021.


# Contact Information
You can contact Percona’s GSoC team directly via [email](mailto:gsoc@percona.com), or join our GSoC [mailing list](https://groups.google.com/forum/#!forum/percona-gsoc). The mailing list allows you to take part in project-related discussions. 

If you are a student, you can also post your interests on our [Google Group](https://groups.google.com/forum/#!forum/percona-gsoc) and we will add you to our gsoc community chat platform. This allows you to engage further in project discussions and talk to mentors directly on Slack. 

# Student Information

If you are student and are interested in participating, the following is useful information: 

## Proposal Guidelines

Before applying as a Percona contributor, we suggest you review the points below. It can help you with creating a strong proposal:

1. Please read about [Percona Monitoring and Management](https://www.percona.com/doc/percona-monitoring-and-management/index.html).
2. Read about Percona open source [software products](https://www.percona.com/software)
3. Go through the list of ideas for [GSoC 21](#percona-gsoc-2021-ideas-list)
4. Start contributing to the project and engage within the community. 
5. To understand how or what PMM does, please take a look at our [Demo](https://pmmdemo.percona.com/graph/)

## Application Template for Students

If you are planning to send us a proposal, please make sure you have addressed the following elements:

1. About you (anything you’d like to share about your background, experience, education, hobbies)
2. Project background (current state of what exists)
3. Design/description of work
4. Benefit of your work to the project users and developers
5. Deliverables
6. Scheduling
7. Other commitments (i.e., exams, part time work, holidays, lectures, etc.)
8. Community engagement (involvement, sample PRs, forum discussions, other open source involvement)

# Percona GSoC 2021 Ideas List

## Project I: Update MySQL Exporter 

### Project Description: 

PMM uses mysqld exporter for collecting mysql server metrics, our [current mysqld exporter](https://github.com/percona/mysqld_exporter) is a fork of [upstream mysqld exporter](https://github.com/prometheus/mysqld_exporter), we expect the student to take percona’s mysqld exporter and resync it with upstream projects.
    
* Good understanding of the basics of exporters is valuable. 
* Good knowledge on Git (fetch, conflict resolution) is useful because that will be the basis of the project.
* Building the new changes and verifying if current PMM functionality is not broken and everything works as expected for metrics collection. 

### Additional Info:

    Knowledge Prerequisite: Go, Git, MySQL, Exporters, PMM2
    
    Difficulty: Medium
    
    Possible Mentors: Andrii, Carlos

## Project II: PMM UI Component 

### Project Description: 

Percona Monitoring and Management (PMM) is built on top of Grafana, which has its own library of components and [design system](https://developers.grafana.com/ui/latest/index.html) that PMM uses and follows. 
In order to make these components work together with [react-final-form](https://final-form.org/react) and add new ones, PMM UI team created its own library of components.
This library lives in a platform-core package as part of [saas-ui](https://github.com/percona-platform/saas-ui) repository. This project aims to add two new React components to this library: a date picker and a time picker, which should follow the same structure of the components already there.

More resources to find inspiration: [react-time-picker](https://www.npmjs.com/package/react-time-picker), [time pickers](https://material.io/components/time-pickers), [date pickers](https://material.io/components/date-pickers) 

##### Implementation Details 
* Components should work with react-final-form
* Handle similar props as the other components in the package (e.g. name, disabled, validators, label, className, ...)
* Follow a similar layout and API of [material-ui pickers](https://material-ui.com/components/pickers)
* Follow the styles of Grafana components (@grafana/ui) using Grafana theme
* Handle light and dark themes
* Time picker component should work in both 12h and 24h format
* Both components should allow to specify the time and date format
* Both components should allow to specify the min and max date/time

### Additional Info: 
    
    Knowledge Prerequisite: React, Grafana, Git
    
    Difficulty: Medium 
    
    Possible Mentors: Tiago, Alex, Roman, Nicola

## Project III: Grafana - The Walkthrough 

### Project Description: 

PMM uses Grafana which is quite a big and complex project, We want to help our first-time users to find their way. For that, 
we want to create an interactive Grafana walkthrough for the users opening the app for the first time. For the sake of this project & timeline, to keep the scope limited, and as a proof of concept, a particular page/feature can be the focus for now.


There are many examples out there, [see 5 best examples](https://www.appcues.com/blog/the-5-best-walkthrough-examples) and [Product-walkthroughs](https://userguiding.com/blog/product-walkthroughs)

Example Pointers for implementation: https://github.com/gilbarbara/react-joyride, https://github.com/elrumordelaluz/reactour 


Instructions to setup the project on your local:


1) Start at Percona’s Grafana fork repo [here](https://github.com/percona-platform/grafana)
2) Follow the instructions to download the PMM-Server docker image [here](https://www.percona.com/doc/percona-monitoring-and-management/2.x/setting-up/server/docker.html)
3) Create a docker-compose file mounting Grafana repo into the container
4) Go to localhost (port 80) and access Grafana using admin:admin credentials


```yaml
version: "3"
services:
 pmm-server:
   container_name: pmm-server
   image:  percona/pmm-server:2
   volumes:
     - "<grafana-path>/public:/usr/share/grafana/public"
   ports:
     - 80:80
     - 443:443
     - 29000:9000
     - 9933:9933
   restart: always
```

### Additional Info: 
    
    Knowledge Prerequisite: React, Grafana, Git
    
    Difficulty: Medium 
    
    Possible Mentors: Fábio, Nicola, Roman 


## Project IV: Improve dashboard formulas by MetricsQL functionality 

### Project Description: 

PMM uses PromQL (Prometheus Query Language) in dashboards. It lets us create formulas for selecting and aggregating time series data in real time. VictoriaMetrics implements MetricsQL - query language inspired by PromQL. It is backwards compatible with PromQL, so Grafana dashboards are working the same way after switching from Prometheus to VictoriaMetrics. 
The project purpose is improving some current dashboard formulas by using MetricsQL functionality.


[Read About PromQL](https://prometheus.io/docs/prometheus/latest/querying/basics/),  
[Read about MetricsQL](https://github.com/VictoriaMetrics/VictoriaMetrics/wiki/MetricsQL) 


MetricsQL functionality that expected to be applied:

1. Range duration in functions such as rate may be omitted.
2. Replace complicated formulas with “or” operator by union(q1, ... qN) function for building multiple graphs for q1, … qN subqueries with a single query. The following queries are equivalent: union(q1, q2) and (q1, q2)
3. Use in formulas ru(freeResources, maxResources) function for returning resource utilization percentage in the range 0% - 100%. For instance, ru(node_memory_MemFree_bytes, node_memory_MemTotal_bytes) returns memory utilization over node_exporter metrics.
4. Replace complicated structure “rate or irate” by keep_last_value(q) - fills missing data (gaps) in q with the previous non-empty value. keep_next_value(q) - fills missing data (gaps) in q with the next non-empty value.
5. Replace topk by  topk_* and bottomk_* aggregate functions, which return up to K time series.


### Additional Info: 
    
    Knowledge Prerequisite: PMM2, PromQL, MetricsQL, Time Series Database
    
    Difficulty: Medium
    
    Possible Mentors: Vadim, Puneet

