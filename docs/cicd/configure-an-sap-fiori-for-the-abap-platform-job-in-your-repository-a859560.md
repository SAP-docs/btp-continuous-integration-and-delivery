<!-- loioa859560bca4149488f8e94e9c9a9adad -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure an SAP Fiori for the ABAP Platform Job in Your Repository

Configure the stages of your SAP Fiori for the ABAP platform job in your repository.



<a name="loioa859560bca4149488f8e94e9c9a9adad__prereq_vmv_pl3_xlb"/>

## Prerequisites

> ### Restriction:  
> This pipeline only works for on-premises scenarios.

-   You've set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You're assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAPUI5/SAP Fiori project for the ABAP platform. See [Create an SAP Fiori Project](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/46664de4d6944471b6c29a0681bfd0fc.html).

-   You have configured the SAP Cloud Connector to ensure secure communication between SAP Continuous Integration and Delivery and the ABAP system.

-   You have installed the SAP component SAP\_UI 7.53 or higher on your ABAP system. See [Software Component SAP\_UI](https://help.sap.com/docs/ABAP_PLATFORM_NEW/6f3c61a7a5b94447b80e72f722b0aad7/35828457ed26452db8d51c840813f1bb.html?version=202009.002).

-   You have enabled the OData service to load data to the SAPUI5 ABAP repository. See [Using an OData Service to Load Data to the SAPUI5 ABAP Repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).

-   You have the S\_DEVELOP authorization to perform operations in your SAPUI5 ABAP repository. See [Using an OData Service to Load Data to the SAPUI5 ABAP Repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).




<a name="loioa859560bca4149488f8e94e9c9a9adad__context_mxt_1s3_1zb"/>

## Context

SAP Continuous Integration and Delivery offers predefined CI/CD pipelines for SAP-specific development scenarios. These pipelines consist of various stages, which are tasks executed sequentially. Your own configuration of a pipeline, including the stages you activate, is referred to as a 'job'.

Depending on your configuration, your job for ABAP platform scenarios can include the following stages:

> ### Tip:  
> Hover over the arrow shapes for a brief description of each stage.

![](images/UI5_Pipeline_Steps_ad534be.png)

Configuring jobs in your repository involves the initial job creation and configuration in the SAP Continuous Integration and Delivery job editor as well as the stages and steps configuration in your source repository.

> ### Tip:  
> Expand the following sections for more information.

<a name="task_l2k_cwc_3bc"/>

<!-- task\_l2k\_cwc\_3bc -->

## Initial Configuration \(Job Editor\)

Create a job in the SAP Continuous Integration and Delivery job editor.



<a name="task_l2k_cwc_3bc__steps_frk_3wc_3bc"/>

## Procedure

1.  In the *Jobs* tab in SAP Continuous Integration and Delivery, choose :heavy_plus_sign:.

2.  In the *Job Name* text field, enter a unique name for your job.

    > ### Tip:  
    > We recommend a name that contains both the name and the branch of your project in your source code management system.

3.  In the *Description* text field, enter a meaningful description for your job.

4.  Choose the *Repository* text field to open the *Select Repository* pop-up.

    Either choose your repository from the list or choose *Add Repository* to add your project repository to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

5.  In the *Branch* text field, enter the branch from which you want to receive push events.

    You can also configure a job for multiple branches in your repository. See [Configure a Multi-Branch Job](configure-a-multi-branch-job-d52d3ca.md).

6.  From the *Pipeline* drop-down list, choose *SAP Fiori for ABAP platform*.

7.  Skip the *Version* drop-down list.

    If you create a new job, the latest version is selected by default. If you edit an existing job, you can change the version by choosing an option from the drop-down list.

8.  To enable your job, choose *ON*.

    By choosing *OFF*, you can deactivate your job without deleting its configuration.

    > ### Note:  
    > Jobs that are created in a trial account or using the Free service plan are automatically deactivated after remaining unchanged for one week. You can use this switch to reactivate them.

9.  In the *Keep logs for* text field in the *Build Retention* section, enter the number of days after which your builds are automatically deleted. Choose a range between 1 and 28 days.

10. In the *Keep maximum* text field, enter the maximum number of builds you want to keep. If your number of builds exceeds this maximum, the oldest ones are deleted automatically. Choose a range between 1 and 99 builds.

11. From the *Configuration Mode* drop-down list, choose *Source Repository*.

12. \(Optional\) Either switch the option *Send Build Notifications via SAP Alert Notification Service* on or off.

    > ### Note:  
    > To use the *Send Build Notifications via SAP Alert Notification Service* option, you need to have enabled the SAP Alert Notification service and created a service key to authenticate your job against it. See [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) and [Credential Management](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/credential-management?version=Cloud).

    If you turn on the *Send Build Notifications via SAP Alert Notification Service* option, provide the following information:

    1.  To authenticate your job against SAP Alert Notification service, create a Service Key credential. See [Creating Credentials](creating-credentials-6658c81.md).

        In the *Service Key* text field, enter the already created service key of your Alert Notification service instance.

        Choose this service key credential from the *Service Key* drop-down list.


13. To save your initial job configuration, choose *Create*.


<a name="task_igr_2xc_3bc"/>

<!-- task\_igr\_2xc\_3bc -->

## Stages Configuration

Configure the stages of your job in your source repository.



<a name="task_igr_2xc_3bc__steps_ijp_spt_xbc"/>

## Procedure

In the `config.yml` file in your repository, configure the stages of your job as follows.

 > ### Tip:  
> Expand the following sections for more information.

 <a name="task_y5f_mxc_3bc"/>

<!-- task\_y5f\_mxc\_3bc -->

### Initial Configuration



<a name="task_y5f_mxc_3bc__steps_oqd_sm5_xbc"/>

## Procedure

In the Git repository in which your project sources reside, create a new file named `.pipeline/config.yml`. In this file, add the following project configuration:

> ### Sample Code:  
> ```
> # Project configuration
> general:
>   buildTool: "npm"
> 
> service: 
>   buildToolVersion: "N18"           
>   cloudConnectors:
>     transportRequestUploadCTS:
>       credentialId: "<CredentialID>"
>     sonarExecuteScan:                                                                           # optional, only relevant if you enable Compliance stage with "SonarQube" mode           
>       credentialId: "<name of your cloud connector credential>"
> 
> # Stage configuration
> stages:
> 
> # Step configuration
> steps:
> ```

**Details of the Project Configuration**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`buildTool` 

</td>
<td valign="top">

Enter `"npm"` as build tool.

</td>
</tr>
<tr>
<td valign="top">

`buildToolVersion` 

</td>
<td valign="top">

Enter the build tool version you want to use. If you don't define a build tool version, a default one is used. For more information, see [Supported Tools](supported-tools-5949283.md).

</td>
</tr>
<tr>
<td valign="top" rowspan="2">

`cloudConnectors` 

</td>
<td valign="top">

For `transportRequestUploadCTS`, enter the name of your Cloud Connector credential in the `credentialId` field.

To authenticate your pipeline against your ABAP system, create a credential of type Cloud Connector in SAP Continuous Integration and Delivery. See [Creating Credentials](creating-credentials-6658c81.md).

</td>
</tr>
<tr>
<td valign="top">

\(Optional\) For `sonarExecuteScan`, enter the name of your Cloud Connector credential in the `credentialId` field.

If you want to enable the Compliance stage with SonarQube mode, you can additionally connect to on-premise systems using Cloud Connector. See [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

</td>
</tr>
</table>

<a name="task_x4x_nxc_3bc"/>

<!-- task\_x4x\_nxc\_3bc -->

### Build and Test Stage



<a name="task_x4x_nxc_3bc__steps_fvt_qxc_3bc"/>

## Procedure

In the `.pipeline/config.yml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> # Stages configuration
> stages:
>   Build:
>     npmExecuteLint: true                                                                        # true, if you want to run a lint check that verifies the syntax of your JavaScript code (default: false)
> ```

**Details of the Build and Test Stage**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Conditions

</th>
</tr>
<tr>
<td valign="top">

`npmExecuteLint` 

</td>
<td valign="top">

Run a lint check to verify the syntax of your JavaScript code.

By default, this stage executes linting with a general-purpose configuration. It doesn’t fail through lint findings but warns you against potential errors in the programming style.

</td>
<td valign="top">

You have at least one JavaScript or TypeScript file in your project.

</td>
</tr>
</table>

<a name="task_gcp_5xc_3bc"/>

<!-- task\_gcp\_5xc\_3bc -->

### Additional Unit Tests



<a name="task_gcp_5xc_3bc__steps_gbf_xn5_xbc"/>

## Procedure

In the `.pipeline/config.yml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
>   Additional Unit Tests:
>      karmaExecuteTests: false                                                                   # true, if you want to execute the Karma Test Runner (default: false) 
>      npmExecuteScripts: true                                                                    # true, if you want to execute test scripts that are defined in step npmExecuteScripts (default: false)
> ```

**Details of the Additional Unit Tests Stage**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Conditions

</th>
</tr>
<tr>
<td valign="top">

`karmaExecuteTests` 

</td>
<td valign="top">

Execute the [Karma Test Runner](http://karma-runner.github.io/latest/index.html).

</td>
<td valign="top">

 

</td>
</tr>
<tr>
<td valign="top">

`npmExecuteScripts` 

</td>
<td valign="top">

Execute additional test scripts from your `package.json` file.

</td>
<td valign="top">

-   You've defined test scripts in the `scripts` section of your `package.json`.

-   You configure the scripts to be executed in the `npmExecuteScripts` step configuration.




</td>
</tr>
</table>

<a name="task_v5j_c5p_ybc"/>

<!-- task\_v5j\_c5p\_ybc -->

#### Configure the Additional Unit Tests Stage

Before running the Additional Unit Tests stage in your job, add the Karma test configuration to your project.



<a name="task_v5j_c5p_ybc__context_m4x_m5p_ybc"/>

## Context

The following steps introduce [Karma](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fgithub.com%2FSAP%2Fkarma-ui5), which is a plugin that helps test your SAP Fiori project.



<a name="task_v5j_c5p_ybc__steps_ndy_p5p_ybc"/>

## Procedure

1.  Append the following Karma dependencies to your project:

    ```
    npm install --save-dev karma karma-ui5 karma-chrome-launcher karma-coverage
    ```

2.  Append the following Karma script to your `package.json` file:

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
                configPath: "ui5-mock.yaml". // change to ui5.yaml if ui5-mock.yaml does not exist.
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

    > ### Note:  
    > The `ui5` property is configured using `configPath`, which loads the default SAPUI5 resources. If a mock server is later added to the project, the `configPath` should be updated to `ui5-mock.yaml`. See [Installing MockServer](https://help.sap.com/docs/SAP_FIORI_tools/17d50220bcd848aa854c9c182d65b699/253805578f04461a9741983a630ce4f1.html?locale=en-USstate%3DPRODUCTION).

5.  To validate your configuration, run the new test script:

    ```
    npm run test
    ```

    In the console log, you can see that the ChromeHeadless browser is now connected, but as you haven’t added a test plan, yet, no tests were executed.




<a name="task_v5j_c5p_ybc__postreq_uwd_jvp_ybc"/>

## Next Steps

To add unit and integration tests to your project, refer to the [SAPUI5 Overview and Testing Strategy Guide](https://sapui5.hana.ondemand.com/sdk/#/topic/ab134ef3932c4b42898c79c10341e8b5).

<a name="task_nq3_vxc_3bc"/>

<!-- task\_nq3\_vxc\_3bc -->

### Malware Scan



<a name="task_nq3_vxc_3bc__steps_zty_vp5_xbc"/>

## Procedure

In the `.pipeline/config.yml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
>   Malware Scan: 
>      malwareExecuteScan: true                                                                   # true, if you want your pipeline to execute malware scanning (default: false)
> ```

**Details of the Malware Scan Stage**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`malwareExecuteScan` 

</td>
<td valign="top">

Enable or disable the **Malware Scan** stage by choosing either `true` or `false`.

> ### Note:  
> In the basic configuration, the **Malware Scan** stage is switched on by default.



</td>
</tr>
</table>

<a name="task_b51_wxc_3bc"/>

<!-- task\_b51\_wxc\_3bc -->

### Compliance



<a name="task_b51_wxc_3bc__steps_fpt_ms5_xbc"/>

## Procedure

In the `.pipeline/config.yml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
>   Compliance:
>     sonarExecuteScan: false                                                                     # true, if you want to integrate continuous inspection of code quality (default: false). If you set this parameter to true, the 
>                                                                                                 # sonarExecuteScan step is mandatory
> ```

**Details of the Compliance Stage**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Conditions

</th>
</tr>
<tr>
<td valign="top">

`sonarExecuteScan` 

</td>
<td valign="top">

Integrate continuous code quality and security analysis into your pipeline.

</td>
<td valign="top">

-   You have a running SonarQube server instance. For more information, see [SonarQube](https://www.sonarqube.org/). You can also use the public offering - SonarCloud.

-   To connect to your SonarQube instance, you have specified the relevant parameters in the `sonarExecuteScan` step configuration.


.

</td>
</tr>
</table>

<a name="task_efm_wxc_3bc"/>

<!-- task\_efm\_wxc\_3bc -->

### Release



<a name="task_efm_wxc_3bc__steps_ihf_v55_xbc"/>

## Procedure

In the `.pipeline/config.yml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> Release:
>     transportRequestUploadCTS: true                                                             # true, if you want to upload your application to the ABAP platform
> ```

**Details of the Release Stage**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Description

</th>
<th valign="top">

Conditions

</th>
</tr>
<tr>
<td valign="top">

`transportRequestUploadCTS` 

</td>
<td valign="top">

Upload your application to the ABAP platform.

</td>
<td valign="top">

You have specified the relevant parameters in the `transportRequestUploadCTS` step configuration.

</td>
</tr>
</table>

<a name="task_zsg_xxc_3bc"/>

<!-- task\_zsg\_xxc\_3bc -->

## Steps Configuration



<a name="task_zsg_xxc_3bc__steps_mjk_pv5_xbc"/>

## Procedure

In the `.pipeline/config.yml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> # Steps configuration
>  steps: 
> # Init stage step 
>   artifactPrepareVersion: 
>     versioningType: "cloud_noTag"                                                               # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
> 
>   npmExecuteLint: 
>     failOnError: false                                                                          # true, if you want your pipeline to fail, if the lint check reveals any errors
> 
> # Test stage step 
>   npmExecuteScripts:                                                                            # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
>     runScripts: 
>       - "test"                                                                                  # list of script names in your package.json file to be executed 
> 
> # Complaince stage steps 
>   sonarExecuteScan:
>     serverUrl: "<SONARQUBE SERVER URL>"                                                         # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
>     organization: "<SONARCLOUD ORGANIZATION>"                                                   # only relevant for the SonarCloud configuration mode
>     projectKey: "<SONARQUBE PROJECT KEY>"                                                       # project key that you provided for your SonarQube project                                   
>     sonarTokenCredentialsId: "<SONARQUBE CREDENTIAL>"                                           # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
> 
> # Release stage steps 
>   transportRequestUploadCts:                                                                    # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true 
>     endpoint: "<http://host:port>"                                                              # the URL of your ABAP server using the HTTP protocol (http://<host:port>)
>     uploadCredentialsId: "<ABAP CREDENTIAL>"                                                    # credential of type "Basic Authentication" to authenticate your pipeline against your ABAP system
>     abapPackage: "<ABAP PACKAGE NAME>"                                                          # the name of the ABAP package you want to upload your application to
>     applicationName: "<NAME>"                                                                   # the name of your application
>     applicationDescription: "<DESCRIPTION>"                                                     # a description for your application
>     transportRequestId: "<TRNSPORT REQUEST ID>"                                                 # the transport request ID of an open CTS+ transport in your ABAP system
> ```

**Details of the Steps Configuration**


<table>
<tr>
<th valign="top">

Step

</th>
<th valign="top">

Description

</th>
<th valign="top">

Condition

</th>
</tr>
<tr>
<td valign="top">

`artifactPrepareVersion` 

</td>
<td valign="top">

Prepare and potentially update the artifact version before building the artifact.

</td>
<td valign="top">

You've set the `npmExecuteLint` parameter in the `Additional Unit Tests` stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`npmExecuteLint` 

</td>
<td valign="top">

Define whether your pipeline should fail, if the lint check reveals any errors.

</td>
<td valign="top">

You've set the `npmExecuteLint` parameter in the `Additional Unit Tests` stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`npmExecuteScripts` 

</td>
<td valign="top">

Define additional test scripts from your `package.json` file to be executed in the `Additional Unit Tests` stage.

</td>
<td valign="top">

You've set the `npmExecuteScripts` parameter in the `Additional Unit Tests` stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`sonarExecuteScan` 

</td>
<td valign="top">

Define code quality and security checks to be executed in the `Compliance` stage.

</td>
<td valign="top">

You've set the `sonarExecuteScan` parameter in the `Compliance` stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`transportRequestUploadCTS` 

</td>
<td valign="top">

Define the ABAP system to which you want to release your application in the `Release` stage.

</td>
<td valign="top">

You've set the `transportRequestUploadCts` parameter in the `Release` stage to `true`.

</td>
</tr>
</table>

> ### Note:  
> You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see [Enhancing Jobs](enhancing-jobs-d581ab5.md).

<a name="concept_fjn_r3v_xbc"/>

<!-- concept\_fjn\_r3v\_xbc -->

## Result: Complete Configuration

Depending on your configuration, your complete `.pipeline/config.yml` file should look as follows:

> ### Sample Code:  
> ```
> # Project configuration
> general:
>   buildTool: "npm"     
> 
> service: 
>   buildToolVersion: "N18"           
>   cloudConnectors:
>     transportRequestUploadCTS:
>       credentialId: "<CredentialID>"
>     sonarExecuteScan: 
>       credentialId: "<CredentialID>"                                                            # optional, only relevant if you enable Compliance stage with "SonarQube" mode                 
> 
> # Stages configuration
> stages:
>   Build:
>     npmExecuteLint: true                                                                        # true, if you want to run a lint check that verifies the syntax of your JavaScript code (default: false)
>   
>   Additional Unit Tests:
>      karmaExecuteTests: false                                                                   # true, if you want to execute the Karma Test Runner (default: false) 
>      npmExecuteScripts: true                                                                    # true, if you want to execute test scripts that are defined in step npmExecuteScripts (default: false)
> 
>   Malware Scan: 
>      malwareExecuteScan: true                                                                   # true, if you want your pipeline to execute malware scanning (default: false) 
>  
>   Compliance:
>     sonarExecuteScan: false                                                                     # true, if you want to integrate continuous inspection of code quality (default: false). If you set this parameter to true, the 
>                                                                                                 # sonarExecuteScan step is mandatory
> 
>   Release:
>   transportRequestUploadCTS: false                                                              # true, if you want to upload your artifact to CTS
> 
> # Steps configuration
>  steps: 
> # Init stage step 
>   artifactPrepareVersion: 
>     versioningType: "cloud_noTag"                                                               # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
> 
>   npmExecuteLint: 
>     failOnError: false                                                                          # true, if you want your pipeline to fail, if the lint check reveals any errors
> 
> # Test stage step 
>   npmExecuteScripts:                                                                            # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
>     runScripts: 
>       - "test"                                                                                  # list of script names in your package.json file to be executed
> 
> # Complaince stage steps 
>   sonarExecuteScan:
>     serverUrl: "<SONARQUBE SERVER URL>"                                                         # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
>     organization: "<SONARCLOUD ORGANIZATION>"                                                   # only relevant for the SonarCloud configuration mode
>     projectKey: "<SONARQUBE PROJECT KEY>"                                                       # project key that you provided for your SonarQube project                                      
>     sonarTokenCredentialsId: "<SONARQUBE CREDENTIAL>"                                           # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
> 
> # Release stage steps 
>   transportRequestUploadCts:                                                                    # only relevant, if you set the transportRequestUploadCTS parameter in the Release stage to true 
>     endpoint: "<http://host:port>"                                                              # the URL of your ABAP server using the HTTP protocol (http://<host:port>)
>     uploadCredentialsId: "<ABAP CREDENTIAL>"                                                    # credential of type "Basic Authentication" to authenticate your pipeline against your ABAP system
>     abapPackage: "<ABAP PACKAGE NAME>"                                                          # the name of the ABAP package you want to upload your application to
>     applicationName: "<NAME>"                                                                   # the name of your application
>     applicationDescription: "<DESCRIPTION>"                                                     # a description for your application
>     transportRequestId: "<TRNSPORT REQUEST ID>"                                                 # the transport request ID of an open CTS+ transport in your ABAP system
> ```

