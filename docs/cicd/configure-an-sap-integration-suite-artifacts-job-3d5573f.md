<!-- loio3d5573fab2ea432cb2cab8639395e51e -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure an SAP Integration Suite Artifacts Job

Create an SAP Continuous Integration and Delivery job for SAP Integration Suite artifacts.



<a name="loio3d5573fab2ea432cb2cab8639395e51e__prereq_lkr_p5d_fqb"/>

## Prerequisites

-   You've set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You’re assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You've provisioned the Cloud Integration capability as part of SAP Integration Suite. See [Initial Setup of SAP Cloud Integration in the Cloud Foundry Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/302b47b11e1749c3aa9478f4123fc216.html).

-   You've created the *Process Integration Runtime* service instance of plan *api* and a service key to authenticate your pipeline against SAP Cloud Integration. See [Setting Up OAuth Inbound Authentication with Client Credentials Grant for API Clients, Cloud Foundry Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/20e26a837a8449c4b8b934b07f71cb76.html).

-   You’ve transferred your integration artifacts from SAP Cloud Integration to a repository of your source code management system:

    1.  In SAP Cloud Integration, open your integration package and choose *Artifacts*.

    2.  Choose *Actions*→ *Download*.

    3.  Save the `*.zip` file to your choice of destination.

    4.  Extract the file and upload its contents into your repository.


    > ### Note:  
    > Repeat this procedure if you make changes to your integration flow in SAP Cloud Integration.




<a name="loio3d5573fab2ea432cb2cab8639395e51e__context_okr_p5d_fqb"/>

## Context

SAP Continuous Integration and Delivery offers predefined CI/CD pipelines for SAP-specific development scenarios. These pipelines consist of various stages, which are tasks executed sequentially. Your own configuration of a pipeline, including the stages you activate, is referred to as a 'job'.

Depending on your configuration, your job for SAP Integration Suite artifacts can include the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/CPI_Pipeline_Stages_fd23518.png)

After your job has completed its execution, an additional stage called **Declarative: Post Actions** is executed to perform final tasks. The outcome of this stage does not affect whether your build is considered successful.

For an overview of how to configure a job in SAP Continuous Integration and Delivery, have a look at the demo video in [Configuring Jobs](configuring-jobs-e293286.md).



<a name="loio3d5573fab2ea432cb2cab8639395e51e__steps_pkr_p5d_fqb"/>

## Procedure

In the *Jobs* tab in SAP Continuous Integration and Delivery, choose :heavy_plus_sign:.

 > ### Tip:  
> The following sections correspond to the *Create Job* pane in SAP Continuous Integration and Delivery. Open them for more information.

 <a name="task_fm1_bll_nfc"/>

<!-- task\_fm1\_bll\_nfc -->

## General Information



<a name="task_fm1_bll_nfc__steps_mq1_3lh_1zb"/>

## Procedure

1.  In the *Job Name* text field, enter a unique name for your job.

    > ### Tip:  
    > We recommend a name that contains both the name and the branch of your project in your source code management system.

2.  In the *Description* text field, enter a meaningful description for your job.

3.  Choose the *Repository* text field to open the *Select Repository* pop-up.

    Either choose your repository from the list or choose *Add Repository* to add your project repository to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

4.  In the *Branch* text field, enter the branch from which you want to receive push events.

    You can also configure a job for multiple branches in your repository. See [Configure a Multi-Branch Job](configure-a-multi-branch-job-d52d3ca.md).

5.  From the *Pipeline* drop-down list, choose *SAP Integration Suite Artifacts*.


<a name="task_bkf_nll_nfc"/>

<!-- task\_bkf\_nll\_nfc -->

## Build Retention



<a name="task_bkf_nll_nfc__steps_hst_yw3_1zb"/>

## Procedure

1.  In the *Keep logs for* text field, enter the number of days after which your builds are automatically deleted. Choose a range between 1 and 28 days.

2.  In the *Keep maximum* text field, enter the maximum number of builds you want to keep. If your number of builds exceeds this maximum, the oldest ones are deleted automatically. Choose a range between 1 and 99 builds.


<a name="task_x1d_pll_nfc"/>

<!-- task\_x1d\_pll\_nfc -->

## Stages



<a name="task_x1d_pll_nfc__steps_gzm_5x3_1zb"/>

## Procedure

From the *Configuration Mode* drop-down list, choose *Job Editor*.

> ### Note:  
> We recommend configuring SAP Continuous Integration and Delivery jobs using its job editor. You can, however, also configure them in your source repository. See [Configuring Jobs in Your Repository](configuring-jobs-in-your-repository-af397b1.md).

The following sections correspond to the stages of your SAP Integration Suite Artifacts job. Open them for more information.

<a name="task_byv_tll_nfc"/>

<!-- task\_byv\_tll\_nfc -->

### General Parameters



## Procedure

1.  In the *Flow ID* text field, enter the ID of your integration flow. You can find it in the overview of your integration package under *Artifcats*.

2.  From the *Design Time Authentication* drop-down list, choose the service key credential of the **Process Integration Runtime** service instance of plan **api**.


<a name="task_mt1_vll_nfc"/>

<!-- task\_mt1\_vll\_nfc -->

### Upload

In the **Upload** stage imports the integration flow content from your source code management system to your SAP Cloud Integration application.



## Procedure

1.  Either activate or deactivate the **Upload** stage.

2.  \(Optional\) In the *Package ID* text field, enter your integration package ID. You can find it in your workspace in SAP Integration Suite \(*Design* tab page\) under *Packages* \> *Overview*.

    > ### Note:  
    > You can skip this part if the integration flow is already set up on the tenant.

3.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](adding-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](adding-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_kds_vll_nfc"/>

<!-- task\_kds\_vll\_nfc -->

### Deploy

The **Deploy** stage triggers the deployment of the integration flow.



## Procedure

1.  Either activate or deactivate the **Deploy** stage.

    > ### Note:  
    > If you prefer not to use the latest version at runtime, you can skip this stage. However, be aware that enabling the **Integration Test** stage will result in testing the old features.

2.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](adding-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](adding-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_i4m_wll_nfc"/>

<!-- task\_i4m\_wll\_nfc -->

### Integration Test

The **Integration Test** stage allows you to test your integration flow.



## Procedure

1.  Either activate or deactivate the **Integration Test** stage.

    > ### Note:  
    > You can use this stage to send a message that triggers the integration flow. However, if your integration flow is automatically triggered by a scheduler start event or a polling sender adapter, you can skip this stage.

2.  \(Optional\) To define the content type of the message body file, either enter a custom file type in the *Content Type* text field or choose one of the options from the drop-down list.

3.  \(Optional\) In the *Message Body File Path*, specify the relative file path of your message body file, for example `integrationTest/messageBody`.

4.  To implement inbound communication with SAP Cloud Integration, create the **Process Integration Runtime** service instance of plan**integration-flow** and a service key.

    Choose this service key credential from the *Runtime Authentication* drop-down list.

5.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](adding-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](adding-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_ptx_zlh_1zb"/>

<!-- task\_ptx\_zlh\_1zb -->

## Build Notifications



<a name="task_ptx_zlh_1zb__prereq_vbc_2v2_d1c"/>

## Prerequisites

You've enabled the SAP Alert Notification service and created a service key to authenticate your job against it. See [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) and [Credential Management](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/credential-management?version=Cloud).



<a name="task_ptx_zlh_1zb__context_l43_lv2_d1c"/>

## Context

If you enable build notifications in SAP Continuous Integration and Delivery, your job automatically sends notifications about build events to SAP Alert Notification service for SAP BTP. The Alert Notification service lets you manage your build notifications and consume them through a channel of your choice. For more information, see [SAP Alert Notification Service for SAP BTP](https://help.sap.com/docs/alert-notification?version=Cloud).



<a name="task_ptx_zlh_1zb__steps_w2g_gw2_d1c"/>

## Procedure

Either switch the option *Send Build Notifications via SAP Alert Notification Service* on or off.

If you turn on the *Send Build Notifications via SAP Alert Notification Service* option, provide the following information:

1.  To authenticate your job against SAP Alert Notification service, create a Service Key credential. See [Creating Credentials](creating-credentials-6658c81.md).

    In the Service Key text field, enter the already created service key of your Alert Notification service instance.

    Choose this service key credential from the *Service Key* drop-down list.

2.  \(Optional\) In the *Custom Tag* text field, add a tag to the notification.


