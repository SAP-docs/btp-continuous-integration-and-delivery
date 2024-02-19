<!-- loio6b64174935494479807ef160da56f897 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# <TEST\>Configure a Cloud Foundry Environment Job

Create an SAP Continuous Integration and Delivery job for SAP Fiori and SAP Cloud Application Programming Model projects in the Cloud Foundry environment.



<a name="loio6b64174935494479807ef160da56f897__prereq_acj_vkh_1zb"/>

## Prerequisites

-   You have set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You are assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAP Fiori or SAP Cloud Application Programming Model project.




<a name="loio6b64174935494479807ef160da56f897__context_mxt_1s3_1zb"/>

## Context

Depending on your configuration, your Cloud Foundry Environment job can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/UI5_Pipeline_Steps_ad534be.png)



## Procedure

In the *Jobs* tab in SAP Continuous Integration and Delivery, choose :heavy_plus_sign:.

 > ### Note:  
> The following sections correspond to the *Create Job* pane in SAP Continuous Integration and Delivery. Open them for more information.

 <a name="task_yhq_dlh_1zb"/>

<!-- task\_yhq\_dlh\_1zb -->

## General Information



<a name="task_yhq_dlh_1zb__steps_mq1_3lh_1zb"/>

## Procedure

1.  In the *Job Name* text field, enter a unique name for your job.

    > ### Tip:  
    > We recommend a name that contains both the name and the branch of your project in your source code management system.

2.  In the *Description* text field, enter a meaningful description for your job.

3.  Choose the *Repository* text field to open the *Select Repository* pop-up.

    Either choose your repository from the list or choose *Add Repository* to add your project repository to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

4.  In the *Branch* text field, enter the branch from which you want to receive push events.

    You can also configure a job for multiple branches in your repository. See [Configure a Multi-Branch Job](configure-a-multi-branch-job-d52d3ca.md).

5.  From the *Pipeline* drop-down list, choose *Cloud Foundry Environment*.

6.  Skip the *Version* drop-down list.

    If you create a new job, the latest version is selected by default. If you edit an existing job, you can change the version by choosing an option from the drop-down list.

7.  To enable your job, choose *ON*.

    By choosing *OFF*, you can deactivate your job without deleting its configuration.

    > ### Note:  
    > Jobs that are created in a trial account or using the Free service plan are automatically deactivated after remaining unchanged for one week. You can use this switch to reactivate them.


<a name="task_itb_zlh_1zb"/>

<!-- task\_itb\_zlh\_1zb -->

## Build Retention



<a name="task_itb_zlh_1zb__steps_hst_yw3_1zb"/>

## Procedure

1.  In the *Keep logs for* text field, enter the number of days after which your builds are automatically deleted. Choose a range between 1 and 28 days.

2.  In the *Keep maximum* text field, enter the maximum number of builds you want to keep. If your number of builds exceeds this maximum, the oldest ones are deleted automatically. Choose a range between 1 and 99 builds.


<a name="task_zrm_zlh_1zb"/>

<!-- task\_zrm\_zlh\_1zb -->

## Stages



<a name="task_zrm_zlh_1zb__steps_gzm_5x3_1zb"/>

## Procedure

From the *Configuration Mode* drop-down list, choose *Job Editor*.

> ### Note:  
> We recommend configuring SAP Continuous Integration and Delivery jobs using its Job Editor. You can, however, also configure them in your source repository. See Configuring Jobs in Your Repository.

> ### Note:  
> The following sections correspond to the stages of your Cloud Foundry Environment job. Open them for more information.

<a name="task_h1p_jx3_1zb"/>

<!-- task\_h1p\_jx3\_1zb -->

### Build

<a name="task_ny5_lx3_1zb"/>

<!-- task\_ny5\_lx3\_1zb -->

### Additional Unit Tests

<a name="task_gns_mx3_1zb"/>

<!-- task\_gns\_mx3\_1zb -->

### Malware Scan

<a name="task_fzk_nx3_1zb"/>

<!-- task\_fzk\_nx3\_1zb -->

### Acceptance

<a name="task_fbc_4x3_1zb"/>

<!-- task\_fbc\_4x3\_1zb -->

### Compliance

<a name="task_ujs_px3_1zb"/>

<!-- task\_ujs\_px3\_1zb -->

### Release

<a name="task_ptx_zlh_1zb"/>

<!-- task\_ptx\_zlh\_1zb -->

## Build Notifications

