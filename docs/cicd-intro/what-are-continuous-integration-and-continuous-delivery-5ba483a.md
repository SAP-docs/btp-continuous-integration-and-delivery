<!-- loio5ba483a2c97b4ad5ab0148f4a6c5a9ee -->

# What Are Continuous Integration and Continuous Delivery?

Get an overview of the continuous integration and delivery concepts.

> ### Note:  
> For more information about SAP solutions that help you apply CI/CD, see [SAP Solutions for Continuous Integration and Delivery](https://help.sap.com/docs/CICD_OVERVIEW/8cacec64ed854b2a88e9a0973e0f97a2/e9fa320181124fa9808d4446a1bf69dd.html?version=Cloud).



<a name="loio5ba483a2c97b4ad5ab0148f4a6c5a9ee__section_tbx_vrn_lhb"/>

## Continuous Integration

**Continuous integration \(CI\)** describes a software development process in which various team members integrate their contributions frequently into a single main line. Before each integration, the changes are verified through builds and automated testing. Thereby, you can detect errors as quickly as possible and prevent integration problems before completing the development.

The continuous integration process is based on several basic principles such as using version control and automating builds, tests, and deployments. For more information, see [Continuous Integration Principles](continuous-integration-principles-30b2e1d.md#loio30b2e1d48f634b03a29733c9f88ef688).

This interactive graphic shows the basic flow for continuous integration:

![The interactive graphic shows a circle that comprises the following
							actor-action combinations of the continuous integration flow. 1. The
							developer writes code and pushes the code changes into a central source
							code management system (SCM). 2. The SCM triggers the continuous
							integration (CI) server.3. The CI server runs automated builds and tests
							and sends feedback about their outcome to the developer.](images/CI_Basic_Flow_ed5a772.png)



### Continuous Integration Basic Flow

The continuous integration basic flow comprises the following steps:

1.  **The developer writes code and pushes the code changes into a central source code management system \(SCM\).**

2.  The SCM triggers the continuous integration \(CI\) server.

3.  The CI server runs automated builds and tests and sends feedback about their outcome to the developer.




### Continuous Integration Basic Flow

The continuous integration basic flow comprises the following steps:

1.  The developer writes code and pushes the code changes into a central source code management system \(SCM\).

2.  **The SCM triggers the continuous integration \(CI\) server.**

3.  The CI server runs automated builds and tests and sends feedback about their outcome to the developer.




### Continuous Integration Basic Flow

The continuous integration basic flow comprises the following steps:

1.  The developer writes code and pushes the code changes into a central source code management system \(SCM\).

2.  The SCM triggers the continuous integration \(CI\) server.

3.  **The CI server runs automated builds and tests and sends feedback about their outcome to the developer.**


As you can learn from the graphic, the basic flow for continuous integration is a cycle: As soon as the CI server has sent its feedback to the developer, the flow starts over again. The developer either corrects his or her previous code change, which must then be built and tested again, or starts working on an entirely new one.

For more information about the continuous integration process flow, see [Continuous Integration and Delivery Process Flows](continuous-integration-and-delivery-process-flows-436c92c.md#loio436c92cdb53c40f788e6d60fd8dc9615).



<a name="loio5ba483a2c97b4ad5ab0148f4a6c5a9ee__section_bjh_rrn_lhb"/>

## Continuous Delivery

The **continuous delivery \(CD\)** concept expands on the one of continuous integration. It adds the aspect that any change that has successfully passed the tests is immediately ready to be deployed to production, both from a technical and a qualitative point of view.

The following graphic shows the relation between continuous integration and continuous delivery:

  
  
**Relation Between CI and CD**

![Relation Between CI and CD](images/CD_Basic_Flow_f569690.png "Relation Between CI and CD")

The continuous delivery process makes sure that the most current version of the software product is successfully built, tested, and provided in a shippable format. Based on the release decision by the development team or delivery manager, it can be shipped to customers or deployed to production at any time.

For more information about the continuous delivery process flow, see [Continuous Integration and Delivery Process Flows](continuous-integration-and-delivery-process-flows-436c92c.md#loio436c92cdb53c40f788e6d60fd8dc9615).

