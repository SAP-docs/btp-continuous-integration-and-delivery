<!-- loio4c26bfbeb6444805a933ca48a470b217 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure an SAP Fiori for ABAP Platform Job

Create an SAP Continuous Integration and Delivery job for SAP Fiori projects for the ABAP platform.



<a name="loio4c26bfbeb6444805a933ca48a470b217__prereq_dvs_hg3_xlb"/>

## Prerequisites

> ### Restriction:  
> This pipeline only works for on-premises scenarios.

-   You've set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You're assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAP Fiori project for the ABAP platform.

-   You've set up the SAP Cloud Connector to secure communication between SAP Continuous Integration and Delivery and the ABAP system.

-   You've installed the SAP component SAP\_UI 7.53 or higher on your ABAP system. See [Software Component SAP\_UI](https://help.sap.com/docs/ABAP_PLATFORM_NEW/6f3c61a7a5b94447b80e72f722b0aad7/35828457ed26452db8d51c840813f1bb.html?version=202009.002).

-   You've enabled the OData service to load data to the SAPUI5 ABAP repository. See [Using an OData Service to Load Data to the SAPUI5 ABAP Repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).

-   You have the S\_DEVELOP authorization to perform operations in your SAPUI5 ABAP repository. See [Using an OData Service to Load Data to the SAPUI5 ABAP Repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).




<a name="loio4c26bfbeb6444805a933ca48a470b217__context_cpj_32y_q4b"/>

## Context

SAP Continuous Integration and Delivery offers predefined CI/CD pipelines for SAP-specific development scenarios. These pipelines consist of various stages, which are tasks executed sequentially. Your own configuration of a pipeline, including the stages you activate, is referred to as a 'job'.

Depending on your configuration, your job for SAP Fiori for ABAP platform scenarios can include the following stages:

> ### Tip:  
> Hover over the arrow shapes for a brief description of each stage.

![](images/ABAP_Platform_Stages_216f127.png)

After your job has completed its execution, an additional stage called **Declarative: Post Actions** is executed to perform final tasks. The outcome of this stage does not affect whether your build is considered successful.

For an overview of how to configure a job in SAP Continuous Integration and Delivery, have a look at the demo video in [Configuring Jobs](configuring-jobs-e293286.md).



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

    > ### Tip:  
    > We recommend a name that contains both the name and the branch of your project in your source code management system.

2.  In the *Description* text field, enter a meaningful description for your job.

3.  Choose the *Repository* text field to open the *Select Repository* pop-up.

    Either choose your repository from the list or choose *Add Repository* to add your project repository to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

4.  In the *Branch* text field, enter the branch from which you want to receive push events.

    You can also configure a job for multiple branches in your repository. See [Configure a Multi-Branch Job](configure-a-multi-branch-job-d52d3ca.md).

5.  From the *Pipeline* drop-down list, choose *SAP Fiori for ABAP platform*.


<a name="task_e3q_vpt_lfc"/>

<!-- task\_e3q\_vpt\_lfc -->

## Build Retention



<a name="task_e3q_vpt_lfc__steps_hst_yw3_1zb"/>

## Procedure

1.  In the *Keep logs for* text field, enter the number of days after which your builds are automatically deleted. Choose a range between 1 and 28 days.

2.  In the *Keep maximum* text field, enter the maximum number of builds you want to keep. If your number of builds exceeds this maximum, the oldest ones are deleted automatically. Choose a range between 1 and 99 builds.


<a name="task_iyj_xpt_lfc"/>

<!-- task\_iyj\_xpt\_lfc -->

## Stages



<a name="task_iyj_xpt_lfc__steps_gzm_5x3_1zb"/>

## Procedure

From the *Configuration Mode* drop-down list, choose *Job Editor*.

> ### Note:  
> We recommend configuring SAP Continuous Integration and Delivery jobs using its job editor. You can, however, also configure them in your source repository. See [Configuring Jobs in Your Repository](configuring-jobs-in-your-repository-af397b1.md).

The following sections correspond to the stages of your SAP Fiori for the ABAP platform job. Open them for more information.

<a name="task_rdl_1qt_lfc"/>

<!-- task\_rdl\_1qt\_lfc -->

### Build

In the **Build** stage, your application is packaged into a deployable archive. This stage is mandatory and executed with every build.



<a name="task_rdl_1qt_lfc__steps_mdt_l12_d1c"/>

## Procedure

1.  From the *Build Tool Version* drop-down list, choose the build tool version you want to use. See [Supported Tools](supported-tools-5949283.md).

    If you don’t define a build tool version, the latest one is used by default. See [Supported Tools](supported-tools-5949283.md).

2.  Either activate or deactivate the execution of a *Lint Check* that verifies the syntax of your JavaScript code.

    > ### Note:  
    > For the *Lint Check*, your project must contain at least one JavaScript or TypeScript file, and your repository must include a lint configuration file.

    If you want your build to fail if the lint check reveals any errors, check the *Fail on Error* checkbox.

3.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](adding-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](adding-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_dmn_5st_lfc"/>

<!-- task\_dmn\_5st\_lfc -->

### Additional Unit Tests

In the **Additional Unit Tests** stage, the tests you've implemented are executed.



<a name="task_dmn_5st_lfc__steps_kqz_wc2_d1c"/>

## Procedure

1.  Either activate or deactivate the execution of the *Additional Unit Tests* stage.

2.  In the *npm Script* text field, enter the name of the test script in the `scripts` section of your `package.json` file to be executed.

3.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](adding-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](adding-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_oxk_wr2_mfc"/>

<!-- task\_oxk\_wr2\_mfc -->

#### \(Optional\) Configure the Additional Unit Tests Stage

Add [Karma](https://github.com/SAP/karma-ui5), a tool that helps you test your SAPUI5 project, to your project's configuration.



<a name="task_oxk_wr2_mfc__context_pxk_wr2_mfc"/>

## Context

The following steps will introduce you to Karma, a tool that helps you test your SAPUI5 project.



## Procedure

1.  Add the following Karma dependencies to your project:

    ```
    npm install --save-dev karma karma-ui5 karma-chrome-launcher karma-coverage
    ```

2.  Add the following Karma script to your `package.json`:

    ```
    {
        (...)
        "scripts": {
            (...)
            "test": "karma start"
        }
    }
    ```

3.  To load and test the project, add a file called `karma.conf.js` to the same folder as your `package.json` file.

4.  Add the following minimal configuration to your `karma.conf.js` file:

    ```
    module.exports = function(config) {
        config.set({
            frameworks: ["ui5"],
            ui5: {
                configPath: "ui5-mock.yaml" // change to ui5.yaml if ui5-mock.yaml does not exist.
            },
            browsers: ["ChromeHeadless"],
            customLaunchers: {
                ChromeHeadlessCustom: {
                    base: 'ChromeHeadless',
                    flags: ['--window-size=1920,1080']
                }
            },
            browserConsoleLogOptions: {
                level: "error"
            },
            singleRun: true,
            proxies: {
                '/base/webapp/resources': 'http://127.0.0.1:' + config.port + '/resources',
                '/base/webapp/test-resources': 'http://127.0.0.1:' + config.port + '/test-resources'
            }
        });
    };
    ```

    The `ui5` property is configured using `configPath`, which loads the default SAPUI5 resources. If a mock server is later added to the project, the `configPath` should be updated to `ui5-mock.yam`l. See [Installing MockServer](https://help.sap.com/docs/SAP_FIORI_tools/17d50220bcd848aa854c9c182d65b699/253805578f04461a9741983a630ce4f1.html?locale=en-USstate%3DPRODUCTION).

5.  To validate your configuration, run the new test script:

    ```
    npm run test
    ```

6.  In the console log, you can see that the ChromeHeadless browser is now connected, but as you haven’t added a test plan, yet, no tests were executed.

    To add unit and integration tests to your project, refer to the [SAPUI5 Overview and Testing Strategy Guide](https://sapui5.hana.ondemand.com/sdk/#/topic/ab134ef3932c4b42898c79c10341e8b5).


<a name="task_vbq_xst_lfc"/>

<!-- task\_vbq\_xst\_lfc -->

### Malware Scan

In the **Malware Scan** stage, your project files are scanned for malware and viruses.



<a name="task_vbq_xst_lfc__steps_djz_bpb_p1c"/>

## Procedure

Either activate or deactivate the execution of the *Malware Scan* stage.

<a name="task_azd_ftt_lfc"/>

<!-- task\_azd\_ftt\_lfc -->

### Compliance

In the **Compliance** stage, automated code quality and security checks are executed.



<a name="task_azd_ftt_lfc__steps_ih5_542_d1c"/>

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

8.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](adding-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](adding-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_vsb_jtt_lfc"/>

<!-- task\_vsb\_jtt\_lfc -->

### Release

In the **Release** stage, the changes are released to the targets you've defined.



## Procedure

1.  Either activate or deactivate the execution of the *Release* stage.

2.  To authenticate your job against the ABAP system, create a Basic Authentication credential of a user who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

    > ### Tip:  
    > Use a technical user instead of your personal credentials. For more information, see [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9).

    Choose this credential from the *Credentials* drop-down list.

3.  Choose the *Cloud Connector* you configured for your ABAP system from the drop-down list.

4.  In the *ABAP Platform Endpoint* text field, enter the URL of your ABAP server using the HTTP protocol \(`http://<host:port>`\).

5.  In the *ABAP Package* text field, enter the name of the ABAP package to which you want to upload your application.

6.  In the *Application Name* text field, enter a name for your application.

7.  \(Optional\) In the *Application Description* text field, enter a meaningful description for your application.

8.  From the *Configuration Mode of Transport Request ID* drop-down list, choose one of the following options:

    -   *Job Editor*: Enter the transport request ID of an open CTS+ transport in your ABAP system in the *Transport Request ID* text field that appears if you choose this option.
    -   *File in Source Repository*: Enter the transport request ID in a file called `.pipeline/transportRequestID` in your source repository. You might need to create this file first.
    -   *Git Commit Message*: Enter the label `Transport Request:` and the transport request ID in the body of a Git HEAD commit message, for example: `TransportRequest: AH7K900034`.

9.  \(Optional\) Enhance the functionality of your job by configuring [*Additional Commands*](adding-additional-commands-to-stages-c05a252.md), [*Additional Credentials*](adding-additional-credentials-to-stages-af2d1a2.md), and [*Additional Variables*](add-additional-variables-to-stages-74fe540.md).


<a name="task_ef1_pb5_lfc"/>

<!-- task\_ef1\_pb5\_lfc -->

## Build Notifications



<a name="task_ef1_pb5_lfc__prereq_vbc_2v2_d1c"/>

## Prerequisites

You've enabled the SAP Alert Notification service and created a service key to authenticate your job against it. See [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) and [Credential Management](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/credential-management?version=Cloud).



<a name="task_ef1_pb5_lfc__context_l43_lv2_d1c"/>

## Context

If you enable build notifications in SAP Continuous Integration and Delivery, your job automatically sends notifications about build events to SAP Alert Notification service for SAP BTP. The Alert Notification service lets you manage your build notifications and consume them through a channel of your choice. For more information, see [SAP Alert Notification Service for SAP BTP](https://help.sap.com/docs/alert-notification?version=Cloud).



<a name="task_ef1_pb5_lfc__steps_w2g_gw2_d1c"/>

## Procedure

Either switch the option *Send Build Notifications via SAP Alert Notification Service* on or off.

If you turn on the *Send Build Notifications via SAP Alert Notification Service* option, provide the following information:

1.  To authenticate your job against SAP Alert Notification service, create a Service Key credential. See [Creating Credentials](creating-credentials-6658c81.md).

    In the Service Key text field, enter the already created service key of your Alert Notification service instance.

    Choose this service key credential from the *Service Key* drop-down list.

2.  \(Optional\) In the *Custom Tag* text field, add a tag to the notification.


