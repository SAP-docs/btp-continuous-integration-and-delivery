<!-- loio8e596c0c03a440c4b271516b59b179b6 -->

# Lifespan of Pipeline Versions

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

