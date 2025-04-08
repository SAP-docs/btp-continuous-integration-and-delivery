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

-   `MBTJ11N18` \(MBT with Java 11 and Node 18\)

-   `MBTJ11N20` \(MBT with Java 11 and Node 20\)

-   `MBTJ17N18` \(MBT with Java 17 and Node 18\)

-   `MBTJ17N20` \(MBT with Java 17 and Node 20\)

-   `MBTJ17N22` \(MBT with Java 17 and Node 22\)

-   `MBTJ19N18` \(MBT with Java 19 and Node 18\)

-   `MBTJ21N18` \(MBT with Java 21 and Node 18\)

-   `MBTJ21N20` \(MBT with Java 21 and Node 20\)

-   `MBTJ21N22` \(MBT with Java 21 Node 22\)




</td>
<td valign="top">

Use this build tool for developing the following applications:

-   [Cloud Foundry Environment](configure-a-cloud-foundry-environment-job-6bd27c0.md#loio6bd27c07ee3b428f9ad5a2e89084f3a3)

-   [SAP Fiori in the Neo Environment](configure-an-sap-fiori-in-the-neo-environment-job-619a864.md#loio619a864813584bd1a433cafac1fb0c1e)




</td>
<td valign="top">

See [Cloud MTA Build Tool \(MBT\).](https://sap.github.io/cloud-mta-build-tool/) 

</td>
</tr>
<tr>
<td valign="top">

npm

</td>
<td valign="top">

`npm`

</td>
<td valign="top">

-   `N18` \(Node 18\)

-   `N20` \(Node 20\)

-   `N22` \(Node 22\)




</td>
<td valign="top">

Use this build tool for developing the following applications:

-   [Cloud Foundry Environment](configure-a-cloud-foundry-environment-job-6bd27c0.md#loio6bd27c07ee3b428f9ad5a2e89084f3a3)

-   [SAP Fiori for the ABAP Platform](configure-an-sap-fiori-for-the-abap-platform-job-4c26bfb.md#loio4c26bfbeb6444805a933ca48a470b217)




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

-   `MVNJ21` \(Maven with Java 21\)




</td>
<td valign="top">

Use this build tool for developing [Cloud Foundry Environment](configure-a-cloud-foundry-environment-job-6bd27c0.md#loio6bd27c07ee3b428f9ad5a2e89084f3a3) applications.

</td>
<td valign="top">

See [Maven.](https://maven.apache.org/index.html) 

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

-   [Cloud Foundry Environment](configure-a-cloud-foundry-environment-job-6bd27c0.md#loio6bd27c07ee3b428f9ad5a2e89084f3a3)

-   [SAP Fiori in the Neo Environment](configure-an-sap-fiori-in-the-neo-environment-job-619a864.md#loio619a864813584bd1a433cafac1fb0c1e)

-   [SAP Fiori for the ABAP Platform](configure-an-sap-fiori-for-the-abap-platform-job-4c26bfb.md#loio4c26bfbeb6444805a933ca48a470b217)




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

-   [Cloud Foundry Environment](configure-a-cloud-foundry-environment-job-6bd27c0.md#loio6bd27c07ee3b428f9ad5a2e89084f3a3)

-    <?sap-ot O2O class="- topic/xref " href="1302e9ae408b4dc38d7109c75db9aa75.xml" text="" desc="" xtrc="xref:14" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> [SAP Fiori in the Neo Environment](configure-an-sap-fiori-in-the-neo-environment-job-619a864.md#loio619a864813584bd1a433cafac1fb0c1e)




</td>
</tr>
</table>

