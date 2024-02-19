<!-- loioe293286b06df426ab1cfa235332a2606 -->

# Supported Pipelines

Learn more about the CI/CD pipelines supported by SAP Continuous Integration and Delivery.

At the moment, SAP Continuous Integration and Delivery supports predefined CI/CD pipelines for different use cases:

-   [**Cloud Foundry Environment**](cloud-foundry-environment-7c2a049.md)

    Configure a CI/CD pipeline for the development of applications that follow the SAP Cloud Application Programming Model in the Cloud Foundry environment.

-   [**SAP Fiori in the Cloud Foundry Environment**](sap-fiori-in-the-cloud-foundry-environment-8887fe3.md)

    Configure a CI/CD pipeline for the development of SAPUI5/SAP Fiori applications in the Cloud Foundry environment.

-   [**SAP Fiori in the Neo Environment**](sap-fiori-in-the-neo-environment-1302e9a.md)

    Configure a CI/CD pipeline for the development of SAPUI5/SAP Fiori applications in the Neo environment.

-   [**SAP Fiori for the ABAP Platform**](sap-fiori-for-the-abap-platform-5a4ec31.md)

    Configure a CI/CD pipeline for the development of SAPUI5/SAP Fiori applications for the ABAP platform.

-   [**SAP Integration Suite Artifacts**](sap-integration-suite-artifacts-019ed68.md)

    Configure a CI/CD pipeline for the development of SAP Cloud Integration artifacts in the Cloud Foundry environment. See [SAP Cloud Integration](https://help.sap.com/viewer/product/CLOUD_INTEGRATION/Cloud/en-US).

-   [**Container-Based Applications**](container-based-applications-1097039.md)

    Configure a CI/CD pipeline for the development of container-based applications.

-   [**Kyma Runtime**](kyma-runtime-ffe4113.md)

    Configure a CI/CD pipeline for the development of applications that follow the SAP Cloud Application Programming Model in the Kyma runtime.




<a name="loioe293286b06df426ab1cfa235332a2606__section_rg2_mmx_g5b"/>

## Lifespan of Pipeline Versions

A new version of a pipeline triggers the deprecation of the previous one, and leads to the deprecated version being sunsetted.

New jobs must use the latest pipeline version. For existing jobs, we strongly recommend that you upgrade them to the latest pipeline version whenever a new version is available.

A pop-up informs you about outdated pipeline versions. Your CI/CD pipeline can have the following states:

**States of Pipeline Versions**


<table>
<tr>
<th valign="top">

State

</th>
<th valign="top">

Description

</th>
<th valign="top">

Additional Information

</th>
</tr>
<tr>
<td valign="top">

Active

</td>
<td valign="top">

This is the most recent pipeline version.

</td>
<td valign="top">

The deprecation of an active pipeline version is announced in [What's New for SAP Continuous Integration and Delivery](what-s-new-for-sap-continuous-integration-and-delivery-8d3bf2e.md).

</td>
</tr>
<tr>
<td valign="top">

Deprecated

</td>
<td valign="top">

This is not the most recent version.

You can still trigger builds of your jobs in this version, but you should switch your existing configurations to the latest version.

</td>
<td valign="top">

Jobs using a deprecated pipeline version are marked with a small yellow warning icon.

If you navigate to your job with a deprecated pipeline version, a message indicating the upcoming end-of-support date appears below the version information.

</td>
</tr>
<tr>
<td valign="top">

Sunsetted

</td>
<td valign="top">

This version is no longer supported.

You cannot trigger builds of your jobs anymore and existing jobs using this version do not work. However, you can still switch your pipeline to the most recent version.

</td>
<td valign="top">

Jobs using a sunsetted pipeline version are marked with a small red error icon.

> ### Note:  
> About 3 months after the end-of-support date, the stage parameters in the *Stages* tab of your job are not shown anymore. Instead, a **Download Pipeline Configuration** button is provided. You can use it to export your entire configuration data into a JSON file.



</td>
</tr>
</table>

