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

-   In the repository of your project, you have a folder named `.sap_cid`, which contains a file named `config.yaml`. If you don't have this folder and file yet, create them.




<a name="loiobfe48a4b12ed41868f92fa564829f752__context_mxt_1s3_1zb"/>

## Context

SAP Continuous Integration and Delivery offers predefined CI/CD pipelines for SAP-specific development scenarios. These pipelines consist of various stages, which are tasks executed sequentially. Your own configuration of a pipeline is referred to as a 'job'.

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

7.  To enable your job, choose *ON*.

    By choosing *OFF*, you can deactivate your job without deleting its configuration.

    > ### Note:  
    > Jobs that are created in a trial account or using the Free service plan are automatically deactivated after remaining unchanged for one week. You can use this switch to reactivate them.

8.  In the *Keep logs for* text field in the *Build Retention* section, enter the number of days after which your builds are automatically deleted. Choose a range between 1 and 28 days.

9.  In the *Keep maximum* text field, enter the maximum number of builds you want to keep. If your number of builds exceeds this maximum, the oldest ones are deleted automatically. Choose a range between 1 and 99 builds.

10. From the *Configuration Mode* drop-down list, choose *Source Repository*.

11. \(Optional\) Either switch the option *Send Build Notifications via SAP Alert Notification Service* on or off.

    > ### Note:  
    > To use the *Send Build Notifications via SAP Alert Notification Service* option, you need to have enabled the SAP Alert Notification service and created a service key to authenticate your job against it. See [Initial Setup](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/initial-setup?version=Cloud) and [Credential Management](https://help.sap.com/docs/alert-notification/sap-alert-notification-for-sap-btp/credential-management?version=Cloud).

    If you turn on the *Send Build Notifications via SAP Alert Notification Service* option, provide the following information:

    1.  To authenticate your job against SAP Alert Notification service, create a Service Key credential. See [Creating Credentials](creating-credentials-6658c81.md).

        In the *Service Key* text field, enter the already created service key of your Alert Notification service instance.

        Choose this service key credential from the *Service Key* drop-down list.

    2.  \(Optional\) In the *Custom Tag* text field, add a tag to the notification.


12. To save your initial job configuration, choose *Create*.


<a name="task_igr_2xc_3bc"/>

<!-- task\_igr\_2xc\_3bc -->

## Stages Configuration \(Repository\)

Configure the stages of your job in your source repository.



<a name="task_igr_2xc_3bc__steps_ijp_spt_xbc"/>

## Procedure

In the `.sap_cid/config.yaml` file in your repository, configure the stages of your job as follows.

 > ### Tip:  
> Expand the following sections for more information.

 <a name="task_qmx_xyy_pgc"/>

<!-- task\_qmx\_xyy\_pgc -->

### \(Mandatory\) Build



## Procedure

In the `.sap_cid/config.yaml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> ---
> stages:
>   build:
>     buildTool: "mta"                                     # "mta", "npm", or "maven"
>     buildToolVersion: "MBTJ21N22"                        # depends on buildTool value; see the following table
>     buildDescriptor: "mta.yaml"
>     mavenStaticCodeChecks: {}                            # only valid if you use the "mta" or" "maven" build tool
>     npmScript: "tests_script"                            # only valid if you use the "npm" build tool 
>     npmLint:                                             # only valid if you use the "mta" or "npm" build tool
>       failOnError: true
> ```

**Details of the Build Stage Configuration**


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

`buildTool` 

</td>
<td valign="top">

The build tool you want to use. For more information, see [Supported Tools](supported-tools-5949283.md).

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`buildToolVersion` 

</td>
<td valign="top">

The build tool version you want to use. See [Supported Tools](supported-tools-5949283.md).

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`buildDescriptor` 

</td>
<td valign="top">

The relative path to the build descriptor file. If you omit this parameter, it defaults to one of the following values based on the specified build tool:

-   `mta` build tool: `"mta.yaml"`

-   `npm` build tool: `"package.json"`

-   `maven` build tool: `pom.xml`


If you use the `mta` build tool, the path must point to a file with a name that ends in `mta.yaml`.

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`mavenStaticCodeChecks` 

</td>
<td valign="top">

Either activate or deactivate the execution of Maven static code checks that verify the syntax of your Java code. Use `"{}"` to activate the checks and either use `"null"` or entirely omit the parameter to deactivate them.

</td>
<td valign="top">

You use the `mta` or `maven` build tool.

</td>
</tr>
<tr>
<td valign="top">

`npmScript` 

</td>
<td valign="top">

The build script configured in the build descriptor file.

</td>
<td valign="top">

You use the `npm` build tool.

</td>
</tr>
<tr>
<td valign="top">

`npmLint` 

</td>
<td valign="top">

Add a lint check that verifies the syntax of your JavaScript code to your job. Specify if you want the job to fail if the linting reveals any errors by setting the `failOnError` parameter either to `true` or `false`.

</td>
<td valign="top">

-   You use the `mta` or `npm` build tool.

-   Your project contains at least one JavaScript or TypeScript file.

-   Your repository includes a lint configuration file.




</td>
</tr>
</table>

\(Optional\) Enhance the functionality of your job by configuring [Additional Commands](adding-additional-commands-to-stages-c05a252.md), [Additional Credentials](adding-additional-credentials-to-stages-af2d1a2.md), and [Additional Variables](add-additional-variables-to-stages-74fe540.md).

<a name="task_yjq_nfz_pgc"/>

<!-- task\_yjq\_nfz\_pgc -->

### Additional Unit Tests



## Procedure

In the `.sap_cid/config.yaml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> ---
> stages:
>   ...
>   additionalTests:                                       # only valid if you use the "mta" or "npm" build tool
>     npmTests:
>       buildDescriptor: "package.json"
>       npmScript: "tests_script"
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

`buildDescriptor` 

</td>
<td valign="top">

The relative path to the build descriptor file. The default value for this parameter is `"package.json"`.

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`npmScript` 

</td>
<td valign="top">

Test script in the `scripts` section of your build descriptor file to be executed.

</td>
<td valign="top">

You've defined a test script in the `scripts` section of your build descriptor file.

</td>
</tr>
</table>

\(Optional\) Enhance the functionality of your job by configuring [Additional Commands](adding-additional-commands-to-stages-c05a252.md), [Additional Credentials](adding-additional-credentials-to-stages-af2d1a2.md), and [Additional Variables](add-additional-variables-to-stages-74fe540.md).

<a name="task_olp_b1b_y2c"/>

<!-- task\_olp\_b1b\_y2c -->

### Malware Scan



## Procedure

In the `.sap_cid/config.yaml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> ---
> stages:
>   ...
>   malwareScan:                                           # only valid if you use the "mta" build tool
>     scan: false
> 
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
<th valign="top">

Conditions

</th>
</tr>
<tr>
<td valign="top">

`scan` 

</td>
<td valign="top">

Enable or disable malware scanning, which scans your project files for malware and viruses. Set the value to `true` to enable or `false` to disable malware scanning.

</td>
<td valign="top">

\-

</td>
</tr>
</table>

\(Optional\) Enhance the functionality of your job by configuring [Additional Commands](adding-additional-commands-to-stages-c05a252.md), [Additional Credentials](adding-additional-credentials-to-stages-af2d1a2.md), and [Additional Variables](add-additional-variables-to-stages-74fe540.md).

<a name="task_nq3_vxc_3bc"/>

<!-- task\_nq3\_vxc\_3bc -->

### Acceptance



<a name="task_nq3_vxc_3bc__steps_zty_vp5_xbc"/>

## Procedure

In the `.sap_cid/config.yaml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> ---
> stages:
>   ...
>   acceptance:
>     cfDeploy:
>       appName: "acceptanceappname"                       # only valid if you use the "maven" or "npm" build tool; required if no application name is defined in your manifest file
>       strategy: "default"
>       apiEndpoint: "https://acceptance-endpoint.com"
>       org: "acceptance_org"
>       space: "acceptance_space"
>       credential: "my-credential"
>       mtaExtensionDescriptors:                           # optional; only valid if you use the "mta" build tool
>       - "mta_descriptor"
>     webdriverIoTests:
>       buildDescriptor: "package.json"                    # optional
>       npmScript: "wdio_script"
>       baseUrl: "https://www.test.com"
>       credential: "my-credential"                        # optional
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
<th valign="top">

Conditions

</th>
</tr>
<tr>
<td valign="top">

`appName` 

</td>
<td valign="top">

The name of your application. This paramenter is required if no application name is defined in your `manifest` file.

</td>
<td valign="top">

You use the `maven` or `npm` build tool.

</td>
</tr>
<tr>
<td valign="top">

`strategy` 

</td>
<td valign="top">

The deploy strategy you want to use.

The standard value for this parameter is `"default"`. If you use the `mta` build tool, you can also use the deployment type `"blue-green"`, which lets you deploy your application without downtime and with reduced risk.

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
<td valign="top">

For `blue-green` deployment: You use the `mta` build tool.

</td>
</tr>
<tr>
<td valign="top">

`apiEndpoint` 

</td>
<td valign="top">

The URL of your SAP BTP, Cloud Foundry API Endpoint, for example `https://api.cf.eu10.hana.ondemand.com`. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud#loiof344a57233d34199b2123b9620d0bb41).

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`org` 

</td>
<td valign="top">

The name of your Cloud Foundry organization. You can find it in the overview of your subaccount in the SAP BTP cockpit.

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`space` 

</td>
<td valign="top">

The name of the Cloud Foundry space in which you want to test your application.

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`credential` 

</td>
<td valign="top">

The name of a credential for a user who has the Space Developer role and is a member of the specified Cloud Foundry organization and space. You can choose from the following credential types:

-   Basic Authentication

-   Basic Authentication for Custom IdP

-   Certificate-Based Authentication for Custom IdP


See [Creating Credentials](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/creating-credentials?version=Cloud).

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`mtaExtensionDescriptors` 

</td>
<td valign="top">

\(Optional\) A list of relative paths to an MTA extension descriptor file \(for example, `<filename>.mtaext.yaml`\). If you want to specify more than one file, add additional items to the list.

</td>
<td valign="top">

You use the `mta` build tool.

</td>
</tr>
<tr>
<td valign="top">

`buildDescriptor` 

</td>
<td valign="top">

\(Optional\) The relative path to the build descriptor file, such as the `package.json` file, which contains your test script.

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`npmScript` 

</td>
<td valign="top">

The name of the test script in the `scripts` section of your `package.json file` to be executed.

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`baseURL` 

</td>
<td valign="top">

The URL of the application against which the tests should be executed. See [Configuring Application URLs in the Cloud Foundry CLI](https://help.sap.com/docs/btp/sap-business-technology-platform/configuring-application-urls?version=Cloud).

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`credential` 

</td>
<td valign="top">

\(Optional\) The name of a Basic Authentication credential of a user who has the appropriate permissions. See [Creating Credentials](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/creating-credentials?version=Cloud).

Use a technical user instead of your personal credentials. For more information, see [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9).

</td>
<td valign="top">

\-

</td>
</tr>
</table>

\(Optional\) Enhance the functionality of your job by configuring [Additional Commands](adding-additional-commands-to-stages-c05a252.md), [Additional Credentials](adding-additional-credentials-to-stages-af2d1a2.md), and [Additional Variables](add-additional-variables-to-stages-74fe540.md).

<a name="task_b51_wxc_3bc"/>

<!-- task\_b51\_wxc\_3bc -->

### Compliance



<a name="task_b51_wxc_3bc__steps_fpt_ms5_xbc"/>

## Procedure

In the `.sap_cid/config.yaml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> ---
> stages:
>   ...
>   compliance:
>     sonarScan:
>       mode: "SonarCloud"
>       organization: "<organization name>"                # only valid if "SonarCloud" mode is selected
>       serverUrl: "https://sonarcloud.io"                 # if cloudConnectorCredential is set, it should use http instead
>       projectKey: "<project key>"
>       tokenCredential: "<secret text credential name>"
>       cloudConnectorCredential: "<credential name>"      # only valid if "SonarQube" mode is selected
> 
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

`mode` 

</td>
<td valign="top">

The mode in which you want to analyze your application: either `"SonarCloud"` or `"SonarQube`.

</td>
<td valign="top">

You either have a running SonarCloud or SonarQube server instance.

</td>
</tr>
<tr>
<td valign="top">

`organization` 

</td>
<td valign="top">

The organization you've provided for your project.

</td>
<td valign="top">

You use the `SonarCloud` mode.

</td>
</tr>
<tr>
<td valign="top">

`serverUrl` 

</td>
<td valign="top">

The full URL to your backend system:

-   If you use the `SonarCloud` mode, enter the corresponding URL: `https://sonarcloud.io`
-   If you use the `SonarQube` mode, enter the custom URL to your Internet-facing SonarQube server.

-   If you've configured a Cloud Connector, this URL must be an HTTP URL \(not HTTPS\).



</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`projectKey` 

</td>
<td valign="top">

The project key you've provided for your project.

</td>
<td valign="top">

If you use the `SonarQube` mode: You've created a project in your SonarQube instance. For more information, see [SonarQube documentation](https://docs.sonarsource.com/sonarqube-server/latest/try-out-sonarqube/).

</td>
</tr>
<tr>
<td valign="top">

`tokenCredential` 

</td>
<td valign="top">

The token that was generated when creating your SonarQube project, which is required to authenticate your job against your SonarQube instance. If you're unable to retrieve your token, generate a new one. See [Managing Tokens \(SonarCloud documentation\)](https://docs.sonarsource.com/sonarqube-cloud/managing-your-account/managing-tokens/) or [Managing Tokens \(SonarQube server documentation\)](https://docs.sonarsource.com/sonarqube-server/latest/user-guide/managing-tokens/).

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`cloudConnectorCredential` 

</td>
<td valign="top">

\(Optional\) The name of your Cloud Connector credential. See [Creating Credentials](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/creating-credentials?version=Cloud).

</td>
<td valign="top">

-   You use the `SonarQube` mode.

-   You've configured a Cloud Connector.




</td>
</tr>
</table>

\(Optional\) Enhance the functionality of your job by configuring [Additional Commands](adding-additional-commands-to-stages-c05a252.md), [Additional Credentials](adding-additional-credentials-to-stages-af2d1a2.md), and [Additional Variables](add-additional-variables-to-stages-74fe540.md).

<a name="task_efm_wxc_3bc"/>

<!-- task\_efm\_wxc\_3bc -->

### Release



<a name="task_efm_wxc_3bc__steps_ihf_v55_xbc"/>

## Procedure

In the `.sap_cid/config.yaml` file in your repository, add the following configuration:

> ### Sample Code:  
> ```
> ---
> stages:
>   ...
>   release:
>     cfDeploy:
>       appName: "releaseappname"                          # only valid if you use the "maven" or "npm" build tool; required if no application name is defined in your manifest file
>       strategy: "default"
>       apiEndpoint: "https://release-endpoint.com"
>       org: "release_org"
>       space: "release_space"
>       credential: "my-credential"                        # optional
>       mtaExtensionDescriptors:                           # optional, only valid if you use the "mta" build tool
>       - "mta_descriptor"
>     cloudTransportManagement:                            # only valid if you use the "mta" build tool
>       nodeOperation: "export"
>       nodeName: "export_node"
>       credential: "service-key"
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
<th valign="top">

Conditions

</th>
</tr>
<tr>
<td valign="top">

`appName` 

</td>
<td valign="top">

The name of your application. This paramenter is required if no application name is defined in your `manifest` file.

</td>
<td valign="top">

You use the `maven` or `npm` build tool.

</td>
</tr>
<tr>
<td valign="top">

`strategy` 

</td>
<td valign="top">

The deploy strategy you want to use.

The standard value for this parameter is `"default"`. If you use the `mta` build tool, you can also use the deployment type `"blue-green"`, which lets you deploy your application without downtime and with reduced risk.

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
<td valign="top">

For `blue-green` deployment: You use the `mta` build tool.

</td>
</tr>
<tr>
<td valign="top">

`apiEndpoint` 

</td>
<td valign="top">

The URL of your SAP BTP, Cloud Foundry API Endpoint, for example `https://api.cf.eu10.hana.ondemand.com`. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud#loiof344a57233d34199b2123b9620d0bb41).

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`org` 

</td>
<td valign="top">

The name of your Cloud Foundry organization. You can find it in the overview of your subaccount in the SAP BTP cockpit.

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`space` 

</td>
<td valign="top">

The name of the Cloud Foundry space in which you want to test your application.

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`credential` 

</td>
<td valign="top">

The name of a credential for a user who has the Space Developer role and is a member of the specified Cloud Foundry organization and space. You can choose from the following credential types:

-   Basic Authentication

-   Basic Authentication for Custom IdP

-   Certificate-Based Authentication for Custom IdP


See [Creating Credentials](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/creating-credentials?version=Cloud).

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`mtaExtensionDescriptors` 

</td>
<td valign="top">

\(Optional\) The relative path to an MTA extension descriptor file \(for example, `<filename>.mtaext.yaml`\). If you want to specify more than one file, add additional items to the list.

</td>
<td valign="top">

You use the `mta` build tool.

</td>
</tr>
<tr>
<td valign="top">

`nodeOperation` 

</td>
<td valign="top">

The way you want to further distribute your deployable file along a transport route in SAP Cloud Transport Management:

-   `export`: Creates a transport request that is added to the queue of the nodes that follow the export node. Choose this option for lifecycles driven by SAP Cloud ALM.

-   `upload`: Creates a transport request that is added to the queue of the upload node in SAP Cloud Transport Management.


For more information, see [Integrate Cloud Transport Management into Your Job](integrate-cloud-transport-management-into-your-job-a0f029b.md).

</td>
<td valign="top">

You have configured a transport route in SAP Cloud Transport Management.

</td>
</tr>
<tr>
<td valign="top">

`nodeName` 

</td>
<td valign="top">

The name of the node to export from or upload to SAP Cloud Transport Management

</td>
<td valign="top">

\-

</td>
</tr>
<tr>
<td valign="top">

`credential` 

</td>
<td valign="top">

The name of a Service Key credential to authenticate your job against SAP Cloud Transport Management. See [Creating Credentials](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/creating-credentials?version=Cloud).

</td>
<td valign="top">

\-

</td>
</tr>
</table>

\(Optional\) Enhance the functionality of your job by configuring [Additional Commands](adding-additional-commands-to-stages-c05a252.md), [Additional Credentials](adding-additional-credentials-to-stages-af2d1a2.md), and [Additional Variables](add-additional-variables-to-stages-74fe540.md).

<a name="concept_fjn_r3v_xbc"/>

<!-- concept\_fjn\_r3v\_xbc -->

## Complete Configurations

Depending on your build tool, expand one of the following sections for a complete job configuration:

<a name="concept_frw_rnq_rgc"/>

<!-- concept\_frw\_rnq\_rgc -->

### Complete Configuration With the `mta` Build Tool

> ### Sample Code:  
> ```
> ---
> stages:
>   build:
>     buildTool: "mta"
>     buildToolVersion: "<build tool version>"
>     buildDescriptor: "mta.yaml"
>     mavenStaticCodeChecks: {}
>     npmLint:
>       failOnError: true
>   additionalTests:
>     npmTests:
>       buildDescriptor: "package.json"
>       npmScript: "<name of test script>"
>   malwareScan:
>     scan: false
>   acceptance:
>     cfDeploy:
>       strategy: "default"
>       apiEndpoint: "<URL of API endpoint>"
>       org: "<name of Cloud Foundry organization>"
>       space: "<name of Cloud Foundry space>"
>       credential: "<credential name>"
>       mtaExtensionDescriptors:                                # optional
>       - "<relative path to mta extension descriptor file>"
>     webdriverIoTests:
>       buildDescriptor: "package.json"
>       npmScript: "<name of the test script>"
>       baseUrl: "<application URL>"
>       credential: "<credential name>"                         # optional
>   compliance:
>     sonarScan:
>       mode: "SonarCloud"
>       organization: "<organization name>"
>       serverUrl: "https://sonarcloud.io"
>       projectKey: "<project key>"
>       tokenCredential: "<secret text credential name>"
>   release:
>     cfDeploy:
>       strategy: "default"
>       apiEndpoint: "<URL of API endpoint>"
>       org: "<name of Cloud Foundry organization>"
>       space: "<name of Cloud Foundry space>"
>       credential: "<credential name>"
>       mtaExtensionDescriptors:                                # optional
>       - "<relative path to mta extension descriptor file>"
>     cloudTransportManagement:
>       nodeOperation: "export"
>       nodeName: "<node name>"
>       credential: "<service key credential name>"
> ```

<a name="concept_ohx_wnq_rgc"/>

<!-- concept\_ohx\_wnq\_rgc -->

### Complete Configuration With the `npm` Build Tool

> ### Sample Code:  
> ```
> ---
> stages:
>   build:
>     buildTool: "npm"
>     buildToolVersion: "<buil tool version>"
>     npmScript: "<name of test script>"
>     buildDescriptor: "package.json"
>     npmLint:
>       failOnError: true
>   acceptance:
>     cfDeploy:
>       appName: "<application name>"                        # optional; only required if not defined in the manifest file
>       strategy: "default"
>       apiEndpoint: "<URL of API endpoint>"
>       org: "<name of Cloud Foundry organization>"
>       space: "<name of Cloud Foundry space>"
>       credential: "<credential name>"
>     webdriverIoTests:
>       buildDescriptor: "package.json"
>       npmScript: "<name of test script>"
>       baseUrl: "<application URL>"
>       credential: "<credential name>"                       # optional
>   additionalTests:
>     npmTests:
>       buildDescriptor: "package.json"
>       npmScript: "<name of test script>"
>   compliance:
>     sonarScan:
>       mode: "SonarCloud"
>       organization: "<organization name>"
>       serverUrl: "https://sonarcloud.io"
>       projectKey: "<project key>"
>       tokenCredential: "<secret text credential name>"
>   release:
>     cfDeploy:
>       appName: "<application name>"                         # optional; only required if not defined in the manifest file
>       strategy: "default"
>       apiEndpoint: "<URL of API endpoint>"
>       org: "<name of Cloud Foundry organization>"
>       space: "<name of Cloud Foundry space>"
>       credential: "credential name"
> ```

<a name="concept_bcy_ynq_rgc"/>

<!-- concept\_bcy\_ynq\_rgc -->

### Complete Configuration With the `maven` Build Tool

> ### Sample Code:  
> ```
> ---
> stages:
>   build:
>     buildTool: "maven"
>     buildToolVersion: "<build tool version>"
>     buildDescriptor: "pom.xml"
>     mavenStaticCodeChecks: {}
>   acceptance:
>     webdriverIoTests:
>       npmScript: "<name of test script>"
>       baseUrl: "<application URL>"
>       credential: "<credential name>"                       # optional
>       buildDescriptor: "package.json"
>     cfDeploy:
>       appName: "<application name>"                         # optional; only required if not defined in the manifest file
>       strategy: "default"
>       apiEndpoint: "<URL of API endpoint>"
>       org: "<name of Cloud Foundry organization>"
>       space: "<name of Cloud Foundry space>"
>       credential: "<credential name>"
>   compliance:
>     sonarScan:
>       mode: "SonarCloud"
>       organization: "<organization name>"
>       serverUrl: "https://test.com"
>       projectKey: "<project key>"
>       tokenCredential: "<secret text credential name>"
>   release:
>     cfDeploy:
>       appName: "<application name>"                         # optional; only required if not defined in the manifest file
>       strategy: "default"
>       apiEndpoint: "<URL of API endpoint>"
>       org: "<name of Cloud Foundry organization>"
>       space: "<name of Cloud Foundry space>"
>       credential: "credential name"
> ```

