<!-- loio6b64174935494479807ef160da56f897 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# <TEST\>Configure a Cloud Foundry Environment Job

Create an SAP Continuous Integration and Delivery job for SAP Fiori and SAP Cloud Application Programming Model projects in the Cloud Foundry environment.



<a name="loio6b64174935494479807ef160da56f897__prereq_acj_vkh_1zb"/>

## Prerequisites

-   You've set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You're assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAP Fiori or SAP Cloud Application Programming Model project.




<a name="loio6b64174935494479807ef160da56f897__context_mxt_1s3_1zb"/>

## Context

SAP Continuous Integration and Delivery offers predefined CI/CD pipelines for SAP-specific development scenarios. These pipelines consist of various stages, which are tasks executed sequentially. Your own configuration of a pipeline, including the stages you activate, is referred to as a 'job'.

Depending on your configuration, your job for Cloud Foundry Environment scenarios can include the following stages:

> ### Tip:  
> Hover over the arrow shapes for a brief description of each stage.

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

The following sections correspond to the stages of your Cloud Foundry Environment job. Open them for more information.

<a name="task_h1p_jx3_1zb"/>

<!-- task\_h1p\_jx3\_1zb -->

### Build



<a name="task_h1p_jx3_1zb__steps_mdt_l12_d1c"/>

## Procedure

1.  From the *Build Tool* drop-down list, choose the build tool you want to use.

    If you don’t define a build tool, a default one \(`mta`\) is used.

2.  From the *Build Tool Version* drop-down list, choose the build tool version you want to use. See [Supported Tools](supported-tools-5949283.md).

    If you don’t define a build tool version, a default one \(`MBTJ11N14`\) is used.

3.  **If you use the `mta` or `maven` build tool:** Either activate or deactivate the execution of *Maven Static Code Checks* that verify the syntax of your Java code.

4.  **If you use the `mta` or `maven` build tool:** Either activate or deactivate the execution of a *Lint Check* that verifies the syntax of your JavaScript code.

    If you want your build to fail if the lint check reveals any errors, check the *Fail on Error* checkbox.

5.  > ### Restriction:  
    > This step doesn't apply to the  <?sap-ot O2O class="- topic/xref " href="019ed685a19b4efab4f7df0e108d1697.xml" text="" desc="" xtrc="xref:13" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/6b64174935494479807ef160da56f897.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>  pipeline.

    \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](add-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](add-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_ny5_lx3_1zb"/>

<!-- task\_ny5\_lx3\_1zb -->

### Additional Unit Tests



<a name="task_ny5_lx3_1zb__steps_kqz_wc2_d1c"/>

## Procedure

1.  Either activate or deactivate the execution of the *Additional Unit Tests* stage.

2.  In the *npm Script* text field, enter the name of the test script in the `scripts` section of your `package.json` file to be executed.

3.  > ### Restriction:  
    > This step doesn't apply to the  <?sap-ot O2O class="- topic/xref " href="019ed685a19b4efab4f7df0e108d1697.xml" text="" desc="" xtrc="xref:17" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/6b64174935494479807ef160da56f897.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>  pipeline.

    \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](add-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](add-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_fzk_nx3_1zb"/>

<!-- task\_fzk\_nx3\_1zb -->

### Acceptance



<a name="task_fzk_nx3_1zb__steps_cnq_xd2_d1c"/>

## Procedure

1.  Either activate or deactivate the execution of the *Acceptance* stage.

    By switching on the *Acceptance* stage, you activate the *Deploy to Cloud Foundry Space* step.

2.  In the *API Endpoint* text field, enter the URL of your SAP BTP, Cloud Foundry API Endpoint. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud#loiof344a57233d34199b2123b9620d0bb41).

3.  In the *Org Name* text field, enter the name of your Cloud Foundry organization. You can find it in the overview of your subaccount in the SAP BTP cockpit.

4.  In the *Space* text field, enter the name of the Cloud Foundry space in which you want to test your application.

5.  From the *Deploy Type* drop-down list, select the deployment type you want to use.

    By using `blue-green` deployment, you can deploy your application without downtime and with reduced risk.

    > ### Remember:  
    > Before using blue-green deployment, increase the memory quota for the Cloud Foundry runtime in your subaccount as follows:
    > 
    > 1.  In the SAP BTP cockpit, navigate to your subaccount.
    > 
    > 2.  From the navigation pane, choose *Entitlements*.
    > 
    > 3.  Depending on if there already is an entry for the Cloud Foundry runtime, choose one of the following options:
    > 
    >     -   If there is no entry for the Cloud Foundry runtime, choose *Configure Entitlements* and *Add Service Plans*.
    > 
    >     -   If there already is an entry for the Cloud Foundry runtime, choose *Cloud Foundry Runtime*. Under *Available Service Plans*, select the checkbox *MEMORY* and choose *Add 1 Service Plan*.
    > 
    > 
    > 4.  Choose *\+* to add quota for the *Cloud Foundry Runtime* service plan to your subaccount.
    > 
    > For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts?version=Cloud).

6.  To authenticate your job against the Cloud Foundry API endpoint, create a Basic Authentication credential of a user who has the appropriate permissions. The user must have the Space Developer role and be a member of the specified Cloud Foundry organization and space. See [Creating Credentials](creating-credentials-6658c81.md).

    Use a technical user instead of your personal credentials. For more information, see [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9).

    Choose this credential from the *Credentials* drop-down list.

7.  > ### Restriction:  
    > The WebdriverIO Test step is available for build tool versions Node 16 and above. The WebdriverIO testing framework is no longer compatible with older Node.js versions.

    Either activate or deactivate the execution of the *WebdriverIO Test* step.

    If you activate the *WebdriverIO Test* step, provide the following information:

    1.  In the *npm Script* text field, enter the name of the test script in the `scripts` section of your `package.json` file to be executed.

        If you don't define a name, a default one \(`wdi5`\) is used.

    2.  In the *Base URL* text field, enter the URL of the application against which the tests should be executed. See [Configuring Application URLs in the Cloud Foundry CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/configuring-application-urls?version=Cloud).

        > ### Tip:  
        > If you don't know the URL, you can deploy your application first. You will find the generated URL by navigating to *Subaccount*** \> ***Cloud Foundry Space*** \> **Overview page of the application** \> ***Application Routes*.

    3.  \(Optional\) To authenticate your pipeline against the application, create a Basic Authentication credential of a user who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

        Use a technical user instead of your personal credentials. For more information, see [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9).

        Choose this credential from the *Credentials* drop-down list.

        You can access the username and password in your individual test files by using the following variables:

        ```
            const usernameVar=process.env.e2e_username
            const passwordVar=process.env.e2e_password
        ```



<a name="task_fbc_4x3_1zb"/>

<!-- task\_fbc\_4x3\_1zb -->

### Compliance



<a name="task_fbc_4x3_1zb__steps_ih5_542_d1c"/>

## Procedure

1.  Either activate or deactivate the execution of the *SonarQube Scan* step, which adds code quality and security analysis to your job.

    For the *SonarQube Scan* step, you either need a running SonarQube server or SonarCloud instance. See [https://www.sonarsource.com/products/sonarqube/](https://www.sonarsource.com/products/sonarqube/).

2.  From the *Mode* drop-down list, select the mode in which you want to analyze your application.

3.  **If you use the `SonarQube` mode:** To connect to on-premises systems using [Cloud Connector](https://help.sap.com/docs/connectivity/sap-btp-connectivity-cf/cloud-connector?version=Cloud), in the *Select Credentials* pop-up, either choose credentials that you've already defined or create new ones by choosing *Create Credentials*. See [Creating Credentials](creating-credentials-6658c81.md).

4.  In the *URL* text field, enter the full URL to your backend system as follows:

    -   If you use the `SonarCloud` mode, choose the corresponding URL from the dropdown list.

    -   If you use the `SonarQube` mode, enter the custom URL to your internet-facing SonarQube server.

        If you've configured a Cloud Connector, this URL must be an HTTP URL \(not HTTPS\).

        > ### Note:  
        > Before configuring the following parameters, make sure that you've created a project in your SonarQube instance. For more information, see the [SonarQube documentation](https://docs.sonarsource.com/sonarqube/latest/try-out-sonarqube/).


5.  **If you use the `SonarCloud` mode:** In the *Organization* text field, enter the organization that you've provided for your project.

6.  In the *Project Key* text field, enter the project key that you've provided for your project.

7.  To authenticate your pipeline against your SonarQube instance, create a Secret Text credential of a user who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

    In the *Secret text* field, paste the token that was generated when creating your SonarQube project. If you are unable to retrieve your token, generate a new one. See [Generating and Using Tokens](https://docs.sonarsource.com/sonarqube/latest/user-guide/user-account/generating-and-using-tokens/).

    Choose this credential from the *SonarQube Token Credentials* drop-down list.

8.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](add-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](add-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_ujs_px3_1zb"/>

<!-- task\_ujs\_px3\_1zb -->

### Release



<a name="task_ujs_px3_1zb__steps_sb5_ct2_d1c"/>

## Procedure

1.  Either activate or deactivate the execution of the *Deploy to Cloud Foundry Space* step.

    If you turn on the *Deploy to Cloud Foundry Space* step, provide the following information:

    1.  In the *API Endpoint* tex field, enter the URL of your SAP BTP, Cloud Foundry API Endpoint. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud#loiof344a57233d34199b2123b9620d0bb41).

    2.  In the *Org Name* text field, enter the name of your Cloud Foundry organization. You can find it in the overview of your subaccount in the SAP BTP cockpit.

    3.  In the *Space* text field, enter the name of the Cloud Foundry space to which you want to deploy your application.

    4.  From the *Deploy Type* drop-down list, select the deployment type you want to use.

        By using `blue-green` deployment, you can deploy your application without downtime and with reduced risk.

        > ### Remember:  
        > Before using blue-green deployment, increase the memory quota for the Cloud Foundry runtime in your subaccount as follows:
        > 
        > 1.  In the SAP BTP cockpit, navigate to your subaccount.
        > 
        > 2.  From the navigation pane, choose *Entitlements*.
        > 
        > 3.  Depending on if there already is an entry for the Cloud Foundry runtime, choose one of the following options:
        > 
        >     -   If there is no entry for the Cloud Foundry runtime, choose *Configure Entitlements* and *Add Service Plans*.
        > 
        >     -   If there already is an entry for the Cloud Foundry runtime, choose *Cloud Foundry Runtime*. Under *Available Service Plans*, select the checkbox *MEMORY* and choose *Add 1 Service Plan*.
        > 
        > 
        > 4.  Choose *\+* to add quota for the *Cloud Foundry Runtime* service plan to your subaccount.
        > 
        > For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts?version=Cloud).

    5.  To authenticate your job against the Cloud Foundry API endpoint, create a Basic Authentication credential of a user who has the appropriate permissions. The user must have the Space Developer role and be a member of the specified Cloud Foundry organization and space. See [Creating Credentials](creating-credentials-6658c81.md).

        Use a technical user instead of your personal credentials. For more information, see [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9).

        Choose this credential from the *Credentials* drop-down list.


2.  Either switch the *Cloud Transport Management* step on or off.

    For more information on why and how to integrate SAP Cloud Transport Management into your continuous delivery process, see Integrate SAP Cloud Transport Management into Your Pipeline.

    If you turn on the *Cloud Transport Management* step, provide the following information:

    1.  From the *Transport Operation* drop-down list, select the action you want to execute to further distribute your deployable file along a transport route in SAP Cloud Transport Management:

        -   *Export from:* Create a transport request that is added to the queue of the nodes that follow the export node. Choose this option for lifecycles driven by SAP Cloud ALM.

        -   *Upload to:* Create a transport request that is added to the queue of the upload node in SAP Cloud Transport Management.


    2.  In the *Node Name* text field, enter the name of the node for the export from or upload to SAP Cloud Transport Management.

    3.  To authenticate your job against SAP Cloud Transport Management, create a Service Key credential. See [Creating Credentials](creating-credentials-6658c81.md).

        Choose this credential from the *Service Key* dropdown list.


3.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](add-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](add-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


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


