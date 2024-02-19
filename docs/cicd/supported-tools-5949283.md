<!-- loio5949283e74cf4735ae59de4a4d3a9773 -->

# Supported Tools

Learn more about the tools and tool versions supported by SAP Continuous Integration and Delivery.



<a name="loio5949283e74cf4735ae59de4a4d3a9773__section_u2h_ngp_wwb"/>

## Supported Source Code Management Tools

SAP Continuous Integration and Delivery supports the following source code management tools:

-   GitHub
-   GitLab
-   Azure Repos
-   Bitbucket Server
-   Bitbucket Cloud



<a name="loio5949283e74cf4735ae59de4a4d3a9773__section_dlv_5gp_wwb"/>

## Supported Build Tools

The following table shows which build tools and build tool versions are used in which SAP Continuous Integration and Delivery development scenario.

> ### Note:  
> In you are using a deprecated build tool version, please update your job configurations and switch to the latest one. The deprecation of a build tool version with an estimated end-of-support date is announced in [What's New for SAP Continuous Integration and Delivery](what-s-new-for-sap-continuous-integration-and-delivery-8d3bf2e.md).

**Supported Build Tools and Build Tool Versions in CI/CD Pipelines**


<table>
<tr>
<th valign="top">

Build Tool

</th>
<th valign="top">

Parameter

</th>
<th valign="top">

Supported Version

</th>
<th valign="top">

Development Scenario

</th>
<th valign="top">

Documentation

</th>
</tr>
<tr>
<td valign="top">

Cloud MTA Build Tool \(MBT\)

</td>
<td valign="top">

`mta`

</td>
<td valign="top">

-   `MBTJ8N18` \(MBT with Java 8 and Node 18\)

-   `MBTJ11N18` \(MBT with Java 11 and Node 18\)

-   `MBTJ11N20` \(MBT with Java 11 and Node 20\)

-   `MBTJ17N18` \(MBT with Java 17 and Node 18\)

-   `MBTJ17N20` \(MBT with Java 17 and Node 20\)

-   `MBTJ19N18` \(MBT with Java 19 and Node 18\)




</td>
<td valign="top">

Use this build tool for developing the following applications:

-   [Cloud Foundry Environment](cloud-foundry-environment-7c2a049.md)

-   [SAP Fiori in the Cloud Foundry Environment](sap-fiori-in-the-cloud-foundry-environment-8887fe3.md)

-   [SAP Fiori in the Neo Environment](sap-fiori-in-the-neo-environment-1302e9a.md)




</td>
<td valign="top">

See [Cloud MTA Build Tool \(MBT\).](https://sap.github.io/cloud-mta-build-tool/) 

</td>
</tr>
<tr>
<td valign="top">

Node.js

</td>
<td valign="top">

`npm`

</td>
<td valign="top">

-   `N18` \(Node 18\)

-   `N20` \(Node 20\)




</td>
<td valign="top">

Use this build tool for developing the following applications:

-   [Cloud Foundry Environment](cloud-foundry-environment-7c2a049.md)

-   [SAP Fiori for the ABAP Platform](sap-fiori-for-the-abap-platform-5a4ec31.md)




</td>
<td valign="top">

See [Node.js.](https://nodejs.org/en/docs/) 

</td>
</tr>
<tr>
<td valign="top">

Maven

</td>
<td valign="top">

`maven`

</td>
<td valign="top">

-   `MVNJ11` \(Maven with Java 11\)

-   `MVNJ17` \(Maven with Java 17\)




</td>
<td valign="top">

Use this build tool for developing [Cloud Foundry Environment](cloud-foundry-environment-7c2a049.md) applications.

</td>
<td valign="top">

See [Maven.](https://maven.apache.org/index.html) 

</td>
</tr>
<tr>
<td valign="top">

Docker

</td>
<td valign="top">

\-

</td>
<td valign="top">

\-

</td>
<td valign="top">

Use this build tool for developing [Container-Based Applications](container-based-applications-1097039.md).

</td>
<td valign="top">

See [Docker.](https://docs.docker.com/) 

</td>
</tr>
</table>



<a name="loio5949283e74cf4735ae59de4a4d3a9773__section_qcq_zgp_wwb"/>

## Supported Testing Tools

The following table shows which testing tools and testing tool versions are used in which SAP Continuous Integration and Delivery development scenario.

**Supported Testing Tools and Versions in CI/CD Pipelines**


<table>
<tr>
<th valign="top">

Testing Tool

</th>
<th valign="top">

Supported Tool Version

</th>
<th valign="top">

Development Scenario

</th>
</tr>
<tr>
<td valign="top">

SonarQube

</td>
<td valign="top">

sonar-scanner CLI. 4.7

</td>
<td valign="top">

Use this testing tool for developing the following applications:

-   [Cloud Foundry Environment](cloud-foundry-environment-7c2a049.md)

-   [SAP Fiori in the Cloud Foundry Environment](sap-fiori-in-the-cloud-foundry-environment-8887fe3.md)

-   [SAP Fiori in the Neo Environment](sap-fiori-in-the-neo-environment-1302e9a.md)

-   [SAP Fiori for the ABAP Platform](sap-fiori-for-the-abap-platform-5a4ec31.md)




</td>
</tr>
<tr>
<td valign="top">

wdi5

</td>
<td valign="top">

Chromium v114

</td>
<td valign="top">

Use this testing tool for developing the following applications:

-   [Cloud Foundry Environment](cloud-foundry-environment-7c2a049.md)

-   [SAP Fiori in the Cloud Foundry Environment](sap-fiori-in-the-cloud-foundry-environment-8887fe3.md)

-   [SAP Fiori in the Neo Environment](sap-fiori-in-the-neo-environment-1302e9a.md)




</td>
</tr>
</table>

