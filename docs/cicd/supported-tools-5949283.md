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

-    <?sap-ot O2O class="- topic/xref " href="7c2a049670f64993b9d67c8f84ba0969.xml" text="" desc="" xtrc="xref:2" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="8887fe3c5445442b915d3c066c010d75.xml" text="" desc="" xtrc="xref:3" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="1302e9ae408b4dc38d7109c75db9aa75.xml" text="" desc="" xtrc="xref:4" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 




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

-    <?sap-ot O2O class="- topic/xref " href="7c2a049670f64993b9d67c8f84ba0969.xml" text="" desc="" xtrc="xref:6" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="5a4ec31140e74970866fcd776cd856f1.xml" text="" desc="" xtrc="xref:7" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 




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

Use this build tool for developing  <?sap-ot O2O class="- topic/xref " href="7c2a049670f64993b9d67c8f84ba0969.xml" text="" desc="" xtrc="xref:9" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>  applications.

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

Use this build tool for developing  <?sap-ot O2O class="- topic/xref " href="10970393828c46498806d1b322cf05a4.xml" text="" desc="" xtrc="xref:11" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

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

-    <?sap-ot O2O class="- topic/xref " href="7c2a049670f64993b9d67c8f84ba0969.xml" text="" desc="" xtrc="xref:13" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="8887fe3c5445442b915d3c066c010d75.xml" text="" desc="" xtrc="xref:14" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="1302e9ae408b4dc38d7109c75db9aa75.xml" text="" desc="" xtrc="xref:15" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="5a4ec31140e74970866fcd776cd856f1.xml" text="" desc="" xtrc="xref:16" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 




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

-    <?sap-ot O2O class="- topic/xref " href="7c2a049670f64993b9d67c8f84ba0969.xml" text="" desc="" xtrc="xref:17" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="8887fe3c5445442b915d3c066c010d75.xml" text="" desc="" xtrc="xref:18" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 

-    <?sap-ot O2O class="- topic/xref " href="1302e9ae408b4dc38d7109c75db9aa75.xml" text="" desc="" xtrc="xref:19" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/5949283e74cf4735ae59de4a4d3a9773.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> 




</td>
</tr>
</table>

