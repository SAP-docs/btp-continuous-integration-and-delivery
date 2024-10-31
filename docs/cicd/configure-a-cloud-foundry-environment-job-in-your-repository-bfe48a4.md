<!-- loiobfe48a4b12ed41868f92fa564829f752 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure a Cloud Foundry Environment Job in Your Repository

Configure the stages of your Cloud Foundry Environment job in your source code management system.



<a name="loiobfe48a4b12ed41868f92fa564829f752__prereq_jsb_3gc_clb"/>

## Prerequisites

-   You've set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You're assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAP Fiori or SAP Cloud Application Programming Model project with the recommended files and folders structure.

    For how to start a CAP project with the recommended files and folders structure, see [Getting Started in a Nutshell](https://cap.cloud.sap/docs/get-started/in-a-nutshell).

-   You have write permission for the repository in which your project sources reside.

-   In the repository of your project, you have a folder named `.pipeline`, which contains a file named `config.yml`. If you don't have this folder and file yet, create them.




<a name="loiobfe48a4b12ed41868f92fa564829f752__context_mxt_1s3_1zb"/>

## Context

SAP Continuous Integration and Delivery offers predefined CI/CD pipelines for SAP-specific development scenarios. These pipelines consist of various stages, which are tasks executed sequentially. Your own configuration of a pipeline, including the stages you activate, is referred to as a 'job'.

Depending on your configuration, your job for Cloud Foundry Environment scenarios can include the following stages:

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

6.  From the *Pipeline* drop-down list, choose *Cloud Foundry Environment*.

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

In the `config.yml` file in your repository, add the following project configuration:

> ### Sample Code:  
> ```
> # Project configuration
> general:
>   buildTool: "mta"                                                # "mta", "npm", or "maven" (default: "mta")
> 
> service:
>   buildToolVersion: "MBT17N18"                                    # depends on buildTool value, see the following table
>   stages:
>     Acceptance:                                                   # optional, only relevant if you enable Acceptance stage
>       cfCredentialsId: "<name of your Cloud Foundry credential for the Acceptance stage>"
>     Release:                                                      # optional, only relevant if you enable Release stage with Cloud Foundry deployment activated
>       cfCredentialsId: "<name of your Cloud Foundry credential for the Release stage>"
>   cloudConnectors:                                                # optional, only relevant if you enable Compliance stage with "SonarQube" mode           
>     sonarExecuteScan: 
>       credentialId: "<name of your cloud connector credential>"
> 
> # Stages configuration
> stages:
> 
> # Steps configuration
> steps:
> 
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

Choose the build tool you want to use.

If you don't define a build tool, a default one is used.

</td>
</tr>
<tr>
<td valign="top">

`buildToolVersion`

</td>
<td valign="top">

Choose the build tool version you want to use. For more information, see [Supported Tools](supported-tools-5949283.md).

If you don't define a build tool version, a default one is used.

</td>
</tr>
<tr>
<td valign="top">

`cfCredentialsId`

</td>
<td valign="top">

\(Optional\) If in the Acceptance or Release stage of your job, you want to deploy to Cloud Foundry, enter the ID of your credential to authenticate against the Cloud Foundry API endpoint. See [Creating Credentials](creating-credentials-6658c81.md).

> ### Tip:  
> Use a technical user instead of your personal credentials.



</td>
</tr>
<tr>
<td valign="top">

`cloudConnectors`

</td>
<td valign="top">

\(Optional\) If you want to enable the Compliance stage with SonarQube mode, you can additionally connect to on-premises systems using Cloud Connector.

For `credentialId`, enter the ID of your Cloud Connector credential. See [Creating Credentials](creating-credentials-6658c81.md).

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
>     mavenExecuteStaticCodeChecks: false                                                         # true, if you want to execute static code checks (default: false)
>     npmExecuteLint: false                                                                       # true, if you want to run a lint check that verifies the syntax of your JavaScript code (default: false)
> 
> 
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

`mavenExecuteStaticCodeChecks`

</td>
<td valign="top">

Execute static code checks for Maven-based modules to verify the syntax of your Java code.

</td>
<td valign="top">

-   You've configured `mta` or `maven` as `buildTool` in the project configuration.

-   You have a `pom.xml` file in the root directory of your project.



</td>
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
>      npmExecuteScripts: false                                                                   # true, if you want to execute test scripts that are defined in step npmExecuteScripts (default: false)
> 
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

Execute the [Karma Test Runner](https://karma-runner.github.io/latest/index.html).

</td>
<td valign="top">

\-

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

-   You configure the scripts to be executed in the `npmExecuteScripts` step configuration \(see [Step Configuration section](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-your-repository?version=Cloud#step-configuration)\).



</td>
</tr>
</table>

<a name="task_nq3_vxc_3bc"/>

<!-- task\_nq3\_vxc\_3bc -->

### Acceptance



<a name="task_nq3_vxc_3bc__steps_zty_vp5_xbc"/>

## Procedure

In the `.pipeline/config.yml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
>   Acceptance:
>     cloudFoundryDeploy: true                                                                    # true, if you want to deploy to Cloud Foundry test space (default: false)
>     cfApiEndpoint: "<your SAP BTP, Cloud Foundry environment API endpoint>" 
>     cfOrg: "<name of your Cloud Foundry organization>"
>     cfSpace: "<name of your Cloud Foundry space>"
>     cfAppName: "<name of your application>"                                                     # only relevant for npm and maven build tools
>     deployType: "standard"                                                                      # only relevant for mta build tool
>     npmExecuteEndToEndTests: true                                                               # true, if you want to execute end-to-end acceptance tests using WebdriverIO (default: false)
> 
> ```

**Details of the Acceptance Stage**


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

`cloudFoundryDeploy`

</td>
<td valign="top">

To trigger the deployment of your application, specify the relevant parameters in the `cloudFoundryDeploy` step configuration \(see [Step Configuration section](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-your-repository?version=Cloud#step-configuration)\).

</td>
</tr>
<tr>
<td valign="top">

`cfApiEndpoint`

</td>
<td valign="top">

Enter the URL of your SAP BTP, Cloud Foundry API Endpoint, for example `https://api.cf.eu10.hana.ondemand.com`. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud#loiof344a57233d34199b2123b9620d0bb41).

</td>
</tr>
<tr>
<td valign="top">

`cfOrg`

</td>
<td valign="top">

Enter the name of your Cloud Foundry organization. You can find it in the overview of your subaccount in the SAP BTP cockpit.

</td>
</tr>
<tr>
<td valign="top">

`cfSpace`

</td>
<td valign="top">

Enter the name of the Cloud Foundry space in which you want to test your application.

</td>
</tr>
<tr>
<td valign="top">

`cfAppName`

</td>
<td valign="top">

\(Only relevant if you use the `npm` or `maven` build tool\) Enter the name of your Cloud Foundry application.

</td>
</tr>
<tr>
<td valign="top">

`cfCredentialsId`

</td>
<td valign="top">

\(Optional\) If in the Acceptance or Release stage of your job, you want to deploy to Cloud Foundry, enter the ID of your credential to authenticate against the Cloud Foundry API endpoint. See [Creating Credentials](creating-credentials-6658c81.md).

> ### Tip:  
> Use a technical user instead of your personal credentials.



</td>
</tr>
<tr>
<td valign="top">

`deployType`

</td>
<td valign="top">

Use the deployment type `standard`.

If you use the `mta` build tool, you can also use the deployment type `blue-green`, which lets you deploy your application without downtime and with reduced risk.

> ### Remember:  
> Before you use the blue-green deployment, please increase the memory quota for the Cloud Foundry runtime in your subaccount. Proceed as follows:
> 
> 1.  In the SAP BTP cockpit, navigate to your subaccount.
> 
> 2.  From the navigation pane, choose *Entitlements*.
> 
> 3.  \(Optional\) If there is no entry for the Cloud Foundry runtime, choose *Configure Entitlements* and *Add Service Plans*.
> 
> 4.  \(Optional\) In the popup, choose *Cloud Foundry Runtime*. Under *Available Service Plans*, select the checkbox *MEMORY* and choose *Add 1 Service Plan*.
> 
> 5.  Use *\+* to add quota for the *Cloud Foundry Runtime* service plan to the subaccount.
> 
> For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts?version=Cloud).



</td>
</tr>
<tr>
<td valign="top">

`npmExecuteEndToEndTests`

</td>
<td valign="top">

> ### Note:  
> The`npmExecuteEndToEndTests` step is available for build tool versions Node 16 and above. The WebdriverIO testing framework is no longer compatible with older Node.js versions.

Specify the relevant parameters in the `npmExecuteEndToEndTests` step configuration to enable WebdriverIO test execution \(see [Step Configuration section](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-your-repository?version=Cloud#step-configuration)\).

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

-   You have a running SonarQube server instance. For more information, see [SonarQube](https://www.sonarsource.com/products/sonarqube/). You can also use the public offering SonarCloud.

-   To connect to your SonarQube instance, you specify the relevant parameters in the `sonarExecuteScan` step configuration \(see [Step Configuration section](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-your-repository?version=Cloud#step-configuration)\).




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
>   Release:
>     cloudFoundryDeploy: false                                                                   # true, if you want to deploy to Cloud Foundry (default: false)
>     cfApiEndpoint: "<your SAP BTP, Cloud Foundry environment API endpoint>"  
>     cfOrg: "<name of your Cloud Foundry organization>"
>     cfSpace: "<name of your Cloud Foundry space>"                            
>     cfAppName: "<name of your application>"                                                     # only relevant for npm and maven build tools
>     deployType: "standard"
>     tmsExport: false                                                                            # true, if you want to export your artifact in SAP Cloud Transport Management (default: false)
> 
> ```

**Details of the Release Stage**


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Action

</th>
</tr>
<tr>
<td valign="top">

`cloudFoundryDeploy`

</td>
<td valign="top">

To deploy a productive branch of your project to the SAP BTP, Cloud Foundry environment, specify the relevant parameters in the `cloudFoundryDeploy` step configuration \(see [Step Configuration section](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-your-repository?version=Cloud#step-configuration)\).

</td>
</tr>
<tr>
<td valign="top">

`cfApiEndpoint`

</td>
<td valign="top">

Enter the URL of your SAP BTP, Cloud Foundry API Endpoint, for example `https://api.cf.eu10.hana.ondemand.com`. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud#loiof344a57233d34199b2123b9620d0bb41).

</td>
</tr>
<tr>
<td valign="top">

`cfOrg`

</td>
<td valign="top">

Enter the name of your Cloud Foundry organization. You can find it in the overview of your subaccount in the SAP BTP cockpit.

</td>
</tr>
<tr>
<td valign="top">

`cfSpace`

</td>
<td valign="top">

Enter the name of the Cloud Foundry space in which you want to test your application.

</td>
</tr>
<tr>
<td valign="top">

`cfAppName`

</td>
<td valign="top">

\(Only relevant if you use the `npm` or `maven` build tool\) Enter the name of your Cloud Foundry application.

</td>
</tr>
<tr>
<td valign="top">

`cfCredentialsId`

</td>
<td valign="top">

\(Optional\) If in the Acceptance or Release stage of your job, you want to deploy to Cloud Foundry, enter the ID of your credential to authenticate against the Cloud Foundry API endpoint. See [Creating Credentials](creating-credentials-6658c81.md).

> ### Tip:  
> Use a technical user instead of your personal credentials.



</td>
</tr>
<tr>
<td valign="top">

`deployType`

</td>
<td valign="top">

Use the deployment type `standard`.

If you use the `mta` build tool, you can also use the deployment type `blue-green`, which lets you deploy your application without downtime and with reduced risk.

> ### Remember:  
> Before you use the blue-green deployment, please increase the memory quota for the Cloud Foundry runtime in your subaccount. Proceed as follows:
> 
> 1.  In the SAP BTP cockpit, navigate to your subaccount.
> 
> 2.  From the navigation pane, choose *Entitlements*.
> 
> 3.  \(Optional\) If there is no entry for the Cloud Foundry runtime, choose *Configure Entitlements* and *Add Service Plans*.
> 
> 4.  \(Optional\) In the popup, choose *Cloud Foundry Runtime*. Under *Available Service Plans*, select the checkbox *MEMORY* and choose *Add 1 Service Plan*.
> 
> 5.  Use *\+* to add quota for the *Cloud Foundry Runtime* service plan to the subaccount.
> 
> For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts?version=Cloud).



</td>
</tr>
<tr>
<td valign="top">

`tmsExport`

</td>
<td valign="top">

If you connect your job with SAP Cloud ALM to access the SAP Cloud Transport Management functionality, use `tmsExport`. Specify the relevant parameters in the `tmsExport` step configuration \(see [Step Configuration section](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-your-repository?version=Cloud#step-configuration)\).

For more information, see [Integrate Cloud Transport Management into Your Job](integrate-cloud-transport-management-into-your-job-a0f029b.md).

</td>
</tr>
<tr>
<td valign="top">

`tmsUpload`

</td>
<td valign="top">

If you connect your job with SAP Cloud Transport Mangagement, you can choose between two transport operations: `tmsExport` or `tmsUpload`. See [Integrate Cloud Transport Management into Your Job](integrate-cloud-transport-management-into-your-job-a0f029b.md).

> ### Note:  
> You can either use `tmsExport` or `tmsUpload`. Configuring both transport operations is not valid.

Specify the relevant parameters in the `tmsExport` step configuration \(see [Step Configuration section](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-your-repository?version=Cloud#step-configuration)\).

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
> steps:
> # Init stage step 
>   artifactPrepareVersion:
>     versioningType:
>       "cloud_noTag"                                                                             # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
>                                                                                                 # or "library" for maven. In this case, the version needs to be set in the pom.xml file
> # Build stage step 
>   npmExecuteLint:
>     failOnError: false                                                                          # true, if you want your pipeline to fail, if the lint check reveals any errors
> 
> # Test stage step 
>   npmExecuteScripts:                                                                            # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
>     runScripts: 
>       - "test"                                                                                  # list of script names in your package.json file to be executed 
>   
> # Acceptance stage steps 
>   cloudFoundryDeploy: false                                                                     # true, if you want to deploy to Cloud Foundry test space (default: false)
>   npmExecuteEndToEndTests:                                                                      # only relevant, if you set the npmExecuteEndToEndTests parameter in the Accepance stage to true
>     runScript: "<wdi5>"                                                                         # enter the name of the test script to be executed (you can find it in the scripts section of your package.json file) (default: "wdi5")                      
>     baseUrl: "<base url>"                                                                       # enter the URL from the Application Routes section of your application from your SAP, BTP subaccount                       														      								
>     credentialsId: "<id of your credential to authenticate against the test application>"       # tip: avoid using a technical user credential and create a special test user instead 
> 
> # Compliance stage steps 
>   sonarExecuteScan:
>     serverUrl: "<sonarqube server url>"                                                         # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
>     organization: "<sonarcloud organization>"                                                   # only relevant for the SonarCloud configuration mode
>     projectKey: "<sonarqube project key>"                                                       # project key that you provided for your SonarQube project                                   
>     sonarTokenCredentialsId: "<sonarqube credential>"                                           # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
> 
> # Release stage steps 
>   cloudFoundryDeploy:                                                                           # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true
>     mtaDeployParameters: "-f --version-rule ALL"
>   
>  tmsExport:                                                                                     # only relevant, if you set the tmsExport parameter in the Release stage to true
>     nodeName: "<name of the node to export from in SAP Cloud Transport Management>"
>     credentialsId: "<id of your credential to authenticate against SAP Cloud ALM or SAP Cloud Transport Management>" 
> 
>  tmsUpload:                                                                                     # only relevant, if you set the tmsUpload parameter in the Release stage to true
>     nodeName: "<name of the node for the upload to SAP Cloud Transport Management>"
>     credentialsId: "<id of your credential to authenticate against SAP Cloud Transport Management>"
> ```

> ### Note:  
> If you chose to use credentials in the `npmExecuteEndToEndTests` step in the Acceptance stage, you can access the username and password in your individual test files by using:
> 
> ```
> 
>     const usernameVar=process.env.e2e_username
>     const passwordVar=process.env.e2e_password
> 
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

\-

</td>
</tr>
<tr>
<td valign="top">

`mavenExecuteStaticCodeChecks`

</td>
<td valign="top">

Optionally, configure additional parameters for the `mavenExecuteStaticCodeChecks` in the Additional Unit Tests stage to fit the needs of your project.

</td>
<td valign="top">

You've set the `mavenExecuteStaticCodeChecks` parameter in the Additional Unit Tests stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`npmExecuteLint`

</td>
<td valign="top">

Define whether your pipeline should fail if the lint check reveals any errors.

</td>
<td valign="top">

You've set the `npmExecuteLint` parameter in the Build stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`npmExecuteScripts`

</td>
<td valign="top">

Define additional test scripts from your `package.json` file to be executed in the Additional Unit Tests stage.

</td>
<td valign="top">

You've set the `npmExecuteScripts` parameter in the Additional Unit Tests stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`npmExecuteEndToEndTests`

</td>
<td valign="top">

Define additional WebdriverIO tests to be executed in the Acceptance stage.

</td>
<td valign="top">

You've set the `npmExecuteEndToEndTests` parameter in the `Acceptance` stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`sonarExecuteScan`

</td>
<td valign="top">

Define code quality and security checks to be executed in the Compliance stage.

</td>
<td valign="top">

You've set the `sonarExecuteScan` parameter in the Compliance stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`cloudFoundryDeploy`

</td>
<td valign="top">

Define additional deploy parameters.

</td>
<td valign="top">

You've set the `cloudFoundryDeploy` parameter in the Release stage to `true`.

</td>
</tr>
<tr>
<td valign="top">

`tmsExport`

</td>
<td valign="top">

Define the SAP Cloud Transport Management node from which you want to export your artifact.

</td>
<td valign="top">

You've set the`tmsExport` parameter in the Release stage to `true`.

For more information on the integration with SAP Cloud Transport Management, see [Integrate Cloud Transport Management into Your Job](integrate-cloud-transport-management-into-your-job-a0f029b.md).

</td>
</tr>
<tr>
<td valign="top">

`tmsUpload`

</td>
<td valign="top">

Define the SAP Cloud Transport Management node to which you want to upload your artifact.

</td>
<td valign="top">

You've set the `tmsUpload` parameter in the Release stage to `true`.

For more information on the integration with SAP Cloud Transport Management, see [Integrate Cloud Transport Management into Your Job](integrate-cloud-transport-management-into-your-job-a0f029b.md).

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
>   buildTool: "mta"                                                                              # "mta", "npm", or "maven"
> 
> service:
>   buildToolVersion: "MBTJ11N14"                                                                 # depends on buildTool value
>   stages:
>     Acceptance:                                                                                 # optional, only relevant if you enable Acceptance stage
>       cfCredentialsId: "<name of your Cloud Foundry credential for the Acceptance stage>"
>     Release:                                                                                    # optional, only relevant if you enable Release stage with Cloud Foundry deployment activated
>       cfCredentialsId: "<name of your Cloud Foundry credential for the Release stage>"
>   cloudConnectors:                                                                              # optional, only relevant if you enable Compliance stage with "SonarQube" mode           
>     sonarExecuteScan: 
>       credentialId: "<name of your cloud connector credential>"
> 
> # Stages configuration
> stages:
>   Build:
>     mavenExecuteStaticCodeChecks: false                                                         # true, if you want to execute static code checks to verify the syntax of your Java code
>     npmExecuteLint: false                                                                       # true, if you want to run a lint check that verifies the syntax of your JavaScript code
> 
>   Additional Unit Tests:
>     karmaExecuteTests: false                                                                    # true, if you want to execute the Karma Test Runner (default: false)
>     npmExecuteScripts: false                                                                    # true, if you want to execute test scripts that are defined in step npmExecuteScripts
> 
>   Acceptance:
>     cloudFoundryDeploy: true                                                                    # true, if you want to deploy to Cloud Foundry test space (default: false)
>     cfApiEndpoint: "<your SAP BTP, Cloud Foundry environment API endpoint>" 
>     cfOrg: "<name of your Cloud Foundry organization>"
>     cfSpace: "<name of your Cloud Foundry space>"
>     deployType: "standard"
>     npmExecuteEndToEndTests: true                                                               # true, if you want to execute end-to-end acceptance tests using WebdriverIO (default: false)
> 
>   Compliance:
>     sonarExecuteScan: false                                                                     # true, if you want to integrate continuous inspection of code quality (default: false). If you set this parameter to true,
>                                                                                                 # the sonarExecuteScan step is mandatory
>      
>   Release:
>     cloudFoundryDeploy: true                                                                    # true, if you want to deploy to Cloud Foundry. If you set this parameter to true, the CloudFoundryDeploy step is mandatory
>     cfApiEndpoint: "<your SAP BTP, Cloud Foundry environment API endpoint>"                     # for example, "https://api.cf.eu10.hana.ondemand.com"
>     cfOrg: "<name of your Cloud Foundry organization>"
>     cfSpace: "<name of your Cloud Foundry space>"                                               # the Cloud Foundry space, to which you want to deploy your application
>     cfAppName: "<name of your application>"
>     deployType: "standard"
>     tmsUpload: true                                                                             # true, if you want to upload your artifact to SAP Cloud Transport Management. If you set this parameter to true, the tmsUpload
>                                                                                                 # step is mandatory
> 
> # Steps configuration
> steps:
> # Init stage step 
>   artifactPrepareVersion:
>     versioningType: 
>       "cloud_noTag"                                                                             # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
>                                                                                                 # or "library" for maven. In this case, the version needs to be set in the pom.xml file
> # Build stage step 
>   npmExecuteLint:
>     failOnError: false                                                                          # true, if you want your pipeline to fail, if the lint check reveals any errors
> 
> # Test stage step 
>   npmExecuteScripts:                                                                            # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
>     runScripts:
>         - "test"                                                                                # list of script names in your package.json file to be executed 
> 
> # Acceptance stage steps 
>   cloudFoundryDeploy: false                                                                     # true, if you want to deploy to Cloud Foundry test space (default: false)
>   npmExecuteEndToEndTests:                                                                      # only relevant, if you set the npmExecuteEndToEndTests parameter in the Accepance stage to true
>     runScript: "<wdi5>"                                                                         # enter the name of the test script to be executed (you can find it in the scripts section of your package.json file) (default: "wdi5")                      
>     baseUrl: "<base url>"                                                                       # enter the URL from the Application Routes section of your application from your SAP, BTP subaccount                       														      								
>     credentialsId: "<id of your credential to authenticate against the test application>"       # tip: avoid using a technical user credential and create a special test user instead 
> 
> 
> # Compliance stage steps 
>   sonarExecuteScan:
>     serverUrl: "<sonarqube server url>"                                                         # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
>     organization: "<sonarcloud organization>"                                                   # only relevant for the SonarCloud configuration mode
>     projectKey: "<sonarqube project key>"                                                       # project key that you provided for your SonarQube project                                      
>     sonarTokenCredentialsId: "<sonarqube credential>"                                           # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
> 
> # Release stage steps 
>   cloudFoundryDeploy:                                                                           # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true
>     mtaDeployParameters: "-f --version-rule ALL"
>     
>   tmsExport:                                                                                    # only relevant, if you set the tmsExport parameter in the Release stage to true
>     nodeName: "<name of the node to export from in SAP Cloud Transport Management>"
>     credentialsId: "<id of your credential to authenticate against SAP Cloud ALM or SAP Cloud Transport Management>"
> ```

