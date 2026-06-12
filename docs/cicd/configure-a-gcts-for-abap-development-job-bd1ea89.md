<!-- loiobd1ea890e70f4ec78fb19cd94473f733 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure a gCTS for ABAP Development Job

Create an SAP Continuous Integration and Delivery job for ABAP development using the Git-Enabled Change and Transport System \(gCTS\).



## Prerequisites

-   You've set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You're assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have configured gCTS on the source and target ABAP System. See [Configuring Git-Enabled Change and Transport System](https://help.sap.com/docs/ABAP_PLATFORM_NEW/4a368c163b08418890a406d413933ba7/26c9c6c5a89244cb9506c253d36c3fda.html).

-   You have a repository in gCTS. See [Create Git Repositories on an ABAP System](https://help.sap.com/docs/ABAP_PLATFORM_NEW/4a368c163b08418890a406d413933ba7/4ca031d6cbee4569873e9b85a4aeb4a0.html).

-   You have configured the SAP Cloud Connector to ensure secure communication between SAP Continuous Integration and Delivery and the ABAP system. See [Configuration](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/configuration?version=Cloud).




## Context

SAP Continuous Integration and Delivery offers predefined CI/CD pipelines for SAP-specific development scenarios. These pipelines consist of various stages, which are tasks executed sequentially. Your own configuration of a pipeline, including the stages you activate, is referred to as a 'job'.

The gCTS for ABAP Development pipeline supports ABAP projects that use the [Git-enabled Change and Transport System \(gCTS\)](https://help.sap.com/docs/ABAP_PLATFORM_NEW/4a368c163b08418890a406d413933ba7/f319b168e87e42149e25e13c08d002b9.html), which manages ABAP change and transport processes using Git as the version-control system. The pipeline streamlines and automates key development steps, including deploying ABAP content to a target ABAP system, running ABAP Unit tests, performing ABAP Test Cockpit \(ATC\) checks, and rolling back to the previous commit if quality issues occur.

Depending on your configuration, your job for ABAP Development scenarios using gCTS can include the following stages:

> ### Tip:  
> Hover over the arrow shapes for a brief description of each stage.

![](images/gCTS_Pipeline_Steps_0928547.png)



## Procedure

In the *Jobs* tab in SAP Continuous Integration and Delivery, choose :heavy_plus_sign:.

 > ### Tip:  
> The following sections correspond to the *Create Job* pane in SAP Continuous Integration and Delivery. Open them for more information.

 <a name="task_hhz_4pt_lfc"/>

<!-- task\_hhz\_4pt\_lfc -->

## General Information



<a name="task_hhz_4pt_lfc__steps_mq1_3lh_1zb"/>

## Procedure

1.  In the *Job Name* text field, enter a unique name for your job.

2.  In the *Description* text field, enter a meaningful description for your job.

3.  Choose the *Repository* text field to open the *Select Repository* pop-up.

    Either choose your repository from the list or choose *Add Repository* to add your project repository to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

4.  In the *Branch* text field, enter the branch from which you want to receive push events.

    You can also configure a job for multiple branches in your repository. See [Configure a Multi-Branch Job](configure-a-multi-branch-job-d52d3ca.md).

5.  From the *Pipeline* drop-down list, choose *gCTS for ABAP Development*.


<a name="task_e3q_vpt_lfc"/>

<!-- task\_e3q\_vpt\_lfc -->

## Build Retention



<a name="task_e3q_vpt_lfc__steps_hst_yw3_1zb"/>

## Procedure

1.  In the *Keep logs for* text field, enter the number of days after which your builds are automatically deleted. Choose a range between 1 and 28 days.

2.  In the *Keep maximum* text field, enter the maximum number of builds you want to keep. If your number of builds exceeds this maximum, the oldest ones are deleted automatically. Choose a range between 1 and 99 builds.


<a name="task_cxl_rcp_43c"/>

<!-- task\_cxl\_rcp\_43c -->

## Connection Details



## Procedure

1.  In the *Target ABAP System Client* text field, enter the client number of the target ABAP system \(for example, `100`\).

2.  In the *Target ABAP System URL* text field, enter the HTTPS URL or \(if you use an on-premises system with the Cloud Connector\) HTTP URL of the ABAP system’s endpoint \(for example, `https://<host>:<port>`\).

3.  In the *ABAP System Credential* drop-down list, either choose your existing credential for connecting to the ABAP system or create a new one choosing :heavy_plus_sign:.

4.  \(If you use an on-premises system\) In the *Cloud Connector* drop-down list, either select an existing Cloud Connector configuration or create a new one choosing :heavy_plus_sign:.

5.  In the *gCTS Repository ID* text field, enter the ID of the gCTS repository you want the pipeline to work with. This is the repository identifier as configured in the gCTS app.

    > ### Note:  
    > The *gCTS Repository ID* is not necessarily the repository name in SAP Continuous Integration and Delivery.


<a name="task_iyj_xpt_lfc"/>

<!-- task\_iyj\_xpt\_lfc -->

## Stages



<a name="task_iyj_xpt_lfc__steps_gzm_5x3_1zb"/>

## Procedure

1.  The *Deploy* stage is mandatory in the *gCTS for ABAP Development* pipeline and executed with every pipeline run.

    Optionally, you can add a *Rollback to Previous Commit on Failure* by selecting the respective check box. If deploying the current commit to the target ABAP system fails, the previously active commit is deployed again.

2.  If you want to add ABAP Test Cockpit \(ATC\) checks to your job, choose :heavy_plus_sign: next to *Run ATC Checks*.

    Optionally, you can add a *Rollback to Previous Commit on Failure* by selecting the respective check box. If the ATC checks detect any errors, the deployment is automatically reverted to the last successful commit.

3.  If you want to add ABAP unit tests to your job, choose :heavy_plus_sign: next to *Run ABAP Unit Tests*.

    Optionally, you can add a *Rollback to Previous Commit on Failure* by selecting the respective check box. If the ABAP unit tests detect any errors, the deployment is automatically reverted to the last successful commit.


