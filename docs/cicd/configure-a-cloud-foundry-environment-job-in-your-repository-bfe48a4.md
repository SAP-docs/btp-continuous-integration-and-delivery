<!-- loiobfe48a4b12ed41868f92fa564829f752 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure a Cloud Foundry Environment Job in Your Repository

Configure the stages of your Cloud Foundry Environment job in your source code management system.



<a name="loiobfe48a4b12ed41868f92fa564829f752__prereq_jsb_3gc_clb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have a CAP project with the recommended files and folders structure. For how to start a CAP project with the recommended files and folders structure, see [Getting Started](https://cap.cloud.sap/docs/get-started/).

-   You have write permission for the repository in which your project sources reside.

-   In the repository of your project, you have a folder named `.pipeline`, which contains a file named `config.yml`. If you don't have this folder and file yet, create them.




<a name="loiobfe48a4b12ed41868f92fa564829f752__context_qhy_gvr_cpb"/>

## Context

Depending on your configuration, the Cloud Foundry Environment pipeline can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/Cloud_SDK_Pipeline_Stages_2d26d26.png)



<a name="loiobfe48a4b12ed41868f92fa564829f752__steps_w2s_rgc_clb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in  <?sap-ot O2O class="- topic/xref " href="d748920175554221be1ba8b461ada030.xml" text="" desc="" xtrc="xref:9" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/bfe48a4b12ed41868f92fa564829f752.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . As *Pipeline*, choose *Cloud Foundry Environment*.

2.  In the *Stages* tab, choose *Source Repository* from the *Configuration Mode* dropdown list.

3.  Choose *Create*.

4.  In your `config.yml` file in your repository, add the following initial configuration:

    ```
    # Project configuration
    general:
      buildTool: "mta"                                  # "mta", "npm", or "maven" (default: "mta")
    
    service:
      buildToolVersion: "MBTJ11N14"                     # depends on buildTool value, see table below
      cloudConnectors:                                  # optional, only relevant if you enable Compliance stage with "SonarQube" mode           
        sonarExecuteScan: 
          credentialId: "<name of your cloud connector credential>"
    
    # Stage configuration
    stages:
    
    # Step configuration
    steps:
    ```

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
    
    Choose the build tool \( `"mta"` , `"npm"` or `"maven"`\) you want to use.

    If you don't define a build tool, a default one \(`"mta"`\) is used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `buildToolVersion` 
    
    </td>
    <td valign="top">
    
    Choose the build tool version you want to use. For more information, see [Supported Tools](supported-tools-5949283.md).

    If you don't define a build tool version, a default one \(`MBTJ11N14`\) is used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cloudConnectors` 
    
    </td>
    <td valign="top">
    
    \(Optional\) If you want to enable the Compliance stage with SonarQube mode, you can additionally connect to on-premise systems using Cloud Connector. See [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

    In the `credentialId` field, Enter the ID of your cloud connector credential. See [Creating Credentials](creating-credentials-6658c81.md).
    
    </td>
    </tr>
    </table>
    
5.  In your `.pipeline/config.yml` file, configure the **stages** of your job as follows:

    **Build and Test**

    > ### Sample Code:  
    > ```
    > # Stage configuration
    > stages:
    >   Build:
    >     mavenExecuteStaticCodeChecks: false    # true, if you want to execute static code checks (default: false)
    >     npmExecuteLint: false                  # true, if you want to run a lint check that verifies the syntax of your JavaScript code (default: false)
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
    
    **Additional Unit Tests**

    > ### Sample Code:  
    > ```
    >   Additional Unit Tests:
    >      karmaExecuteTests: false   # true, if you want to execute the Karma Test Runner (default: false) 
    >      npmExecuteScripts: false   # true, if you want to execute test scripts that are defined in step npmExecuteScripts (default: false)
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

    -   You configure the scripts to be executed in the `npmExecuteScripts` step configuration.



    
    </td>
    </tr>
    </table>
    
    **Acceptance**

    > ### Sample Code:  
    > ```
    >   Acceptance:
    >     cloudFoundryDeploy: true                                               # true, if you want to deploy to Cloud Foundry test space (default: false)
    >     cfApiEndpoint: "<your SAP BTP, Cloud Foundry environment API endpoint>" 
    >     cfOrg: "<name of your Cloud Foundry organization>"
    >     cfSpace: "<name of your Cloud Foundry space>"                               
    >     cfCredentialsId: "<name of your cedential>"
    >     deployType: "standard"
    >     npmExecuteEndToEndTests: true                                          # true, if you want to execute end-to-end acceptance tests using WebdriverIO (default: false)
    > 
    > ```

    **Details of the Acceptance Stage**


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
    
    To trigger the deployment of your application, specify the relevant parameters in the `cloudFoundryDeploy` step configuration.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cfApiEndpoint` 
    
    </td>
    <td valign="top">
    
    Enter the URL of your SAP BTP, Cloud Foundry API Endpoint. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/viewer/3504ec5ef16548778610c7e89cc0eac3/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loiof344a57233d34199b2123b9620d0bb41).

    For example: `https://api.cf.eu10.hana.ondemand.com`.
    
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
    
    `cfCredentialsId` 
    
    </td>
    <td valign="top">
    
    Enter the ID of your credential to authenticate against the Cloud Foundry API Endpoint. See [Creating Credentials](creating-credentials-6658c81.md).

    > ### Tip:  
    > Use a technical user instead of your personal credentials.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployType` 
    
    </td>
    <td valign="top">
    
    Enter the deployment type \(`"standard"` or `"blue-green"`\) you want to use.

    The default deployment type is `"standard"`. By using the `"blue-green"` deployment, you can deploy your application without downtime and with reduced risk.

    > ### Remember:  
    > Before you use the blue-green deployment, please increase the memory quota for the Cloud Foundry runtime in your subaccount. Proceed as follows:
    > 
    > 1.  In the SAP BTP cockpit, navigate to your subaccount.
    > 
    > 2.  From the navigation pane, choose *Entitlements*.
    > 
    > 3.  \(Optional\) If there is no entry for the Cloud Foundry runtime, choose **Configure Entitlements** and **Add Service Plans**.
    > 
    > 4.  \(Optional\) In the popup, choose *Cloud Foundry Runtime*. Under *Available Service Plans*, select the checkbox *MEMORY* and choose *Add 1 Service Plan*.
    > 
    > 5.  Use *\+* to add quota for the *Cloud Foundry Runtime* service plan to the subaccount.
    > 
    > 
    > For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/5ba357b4fa1e4de4b9fcc4ae771609da.html).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `npmExecuteEndToEndTests` 
    
    </td>
    <td valign="top">
    
    > ### Note:  
    > The ***npmExecuteEndToEndTests*** step is available for build tool versions Node 16 and above. The WebdriverIO testing framework is no longer compatible with older Node.js versions.

    Specify the relevant parameters in the ***npmExecuteEndToEndTests*** step configuration to enable WebdriverIO test execution.
    
    </td>
    </tr>
    </table>
    
    **Compliance**

    > ### Sample Code:  
    > ```
    >   Compliance:
    >     sonarExecuteScan: false                                              # true, if you want to integrate continuous inspection of code quality (default: false). If you set this parameter to true, the sonarExecuteScan step is mandatory
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



    
    </td>
    </tr>
    </table>
    
    **Release**

    > ### Sample Code:  
    > ```
    >   Release:
    >     cloudFoundryDeploy: false                                                # true, if you want to deploy to Cloud Foundry (default: false)
    >     cfApiEndpoint: "<your SAP BTP, Cloud Foundry environment API endpoint>"  
    >     cfOrg: "<name of your Cloud Foundry organization>"
    >     cfSpace: "<name of your Cloud Foundry space>"                            
    >     cfAppName: "<name of your application>"   
    >     deployType: "standard"
    >     cfCredentialsId: "<name of your Cloud Foundry space>"
    >     tmsUpload: false                                                         # true, if you want to upload your artifact to SAP Cloud Transport Management (default: false)
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
    
    To deploy a productive branch of your project to the SAP BTP, Cloud Foundry environment, specify the relevant parameters in the `cloudFoundryDeploy` step configuration.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cfApiEndpoint` 
    
    </td>
    <td valign="top">
    
    Enter the URL of your SAP BTP, Cloud Foundry API Endpoint. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/viewer/3504ec5ef16548778610c7e89cc0eac3/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loiof344a57233d34199b2123b9620d0bb41).

    For example: `https://api.cf.eu10.hana.ondemand.com`.
    
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
    
    Enter the name of the Cloud Foundry space to which you want to deploy your application.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cfAppName` 
    
    </td>
    <td valign="top">
    
    Enter the name of your Cloud Foundry Application.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cfCredentialsId` 
    
    </td>
    <td valign="top">
    
    Enter the ID of your credential to authenticate against the Cloud Foundry API Endpoint.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployType` 
    
    </td>
    <td valign="top">
    
    Enter the deployment type \(`"standard"` or `"blue-green"`\) you want to use.

    The default deployment type is `"standard"`. By using the `"blue-green"` deployment, you can deploy your application without downtime and with reduced risk.

    > ### Remember:  
    > Before you use the blue-green deployment, please increase the memory quota for the Cloud Foundry runtime in your subaccount. Proceed as follows:
    > 
    > 1.  In the SAP BTP cockpit, navigate to your subaccount.
    > 
    > 2.  From the navigation pane, choose *Entitlements*.
    > 
    > 3.  \(Optional\) If there is no entry for the Cloud Foundry runtime, choose **Configure Entitlements** and **Add Service Plans**.
    > 
    > 4.  \(Optional\) In the popup, choose *Cloud Foundry Runtime*. Under *Available Service Plans*, select the checkbox *MEMORY* and choose *Add 1 Service Plan*.
    > 
    > 5.  Use *\+* to add quota for the *Cloud Foundry Runtime* service plan to the subaccount.
    > 
    > 
    > For more information, see [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/5ba357b4fa1e4de4b9fcc4ae771609da.html).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `tmsUpload` 
    
    </td>
    <td valign="top">
    
    To upload your artifact to SAP Cloud Transport Management, specify the relevant parameters in the `tmsUpload` step configuration.
    
    </td>
    </tr>
    </table>
    
6.  Configure the **steps** of your configuration as follows:

    > ### Sample Code:  
    > ```
    > # Steps configuration
    > steps:
    > # Init stage step 
    >   artifactPrepareVersion:
    >     versioningType:
    >       "cloud_noTag"                 # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
    >                                     # or "library" for maven. In this case, the version needs to be set in the pom.xml file
    > # Build stage step 
    >   npmExecuteLint:
    >     failOnError: false              # true, if you want your pipeline to fail, if the lint check reveals any errors
    > 
    > # Test stage step 
    >   npmExecuteScripts:                # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
    >     runScripts: 
    >       - "test"                      # list of script names in your package.json file to be executed 
    >   
    > # Acceptance stage steps 
    >   cloudFoundryDeploy: false         # true, if you want to deploy to Cloud Foundry test space (default: false)
    >   npmExecuteEndToEndTests:          # only relevant, if you set the npmExecuteEndToEndTests parameter in the Accepance stage to true
    >     runScript: "<wdi5>"             # enter the name of the test script to be executed (you can find it in the scripts section of your package.json file) (default: "wdi5")                      
    >     baseUrl: "<base url>"           # enter the URL from the Application Routes section of your application from your SAP, BTP subaccount                       														      								
    >     credentialsId: "<id of your credential to authenticate against the test application>"  # tip: avoid using a technical user credential and create a special test user instead 
    > 
    > # Compliance stage steps 
    >   sonarExecuteScan:
    >     serverUrl: "<sonarqube server url>"                                                    # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
    >     organization: "<sonarcloud organization>"                                              # only relevant for the SonarCloud configuration mode
    >     projectKey: "<sonarqube project key>"                                                  # project key that you provided for your SonarQube project                                   
    >     sonarTokenCredentialsId: "<sonarqube credential>"                                      # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
    > 
    > # Release stage steps 
    >   cloudFoundryDeploy:                                                                      # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true
    >     mtaDeployParameters: "-f --version-rule ALL"
    >     
    >   tmsUpload:                                                                               # only relevant, if you set the tmsUpload parameter in the Release stage to true
    >     nodeName: "<name of the node for the upload to SAP Cloud Transport Management>"
    >     credentialsId: "<id of your credential to authenticate against SAP Cloud Transport Management>" 
    >  
    > ```

    > ### Note:  
    > If you chose to use credentials in the `npmExecuteEndToEndTests` Acceptance stage step, you can access the username and password in your individual test files by using:
    > 
    > ```
    > 
    >     const usernameVar=process.env.e2e_username
    >     const passwordVar=process.env.e2e_password
    > 
    > ```

    **Details of the Step Configuration**


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
    
    Optionally, configure additional parameters for the `mavenExecuteStaticCodeChecks` in the **Additional Unit Tests** stage to fit the needs of your project.
    
    </td>
    <td valign="top">
    
    You've set the `mavenExecuteStaticCodeChecks` parameter in the `Additional Unit Tests` stage to `true`.
    
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
    
    You've set the `npmExecuteLint` parameter in the **Build** stage to `true`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `npmExecuteScripts` 
    
    </td>
    <td valign="top">
    
    Define additional test scripts from your `package.json` file to be executed in the **Additional Unit Tests** stage.
    
    </td>
    <td valign="top">
    
    You've set the `npmExecuteScripts` parameter in the **Additional Unit Tests** stage to `true`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `npmExecuteEndToEndTests` 
    
    </td>
    <td valign="top">
    
    Define additional WebdriverIO tests to be executed in the **Acceptance** stage.
    
    </td>
    <td valign="top">
    
    You've set the `npmExecuteEndToEndTests` parameter in the **Acceptance** stage to `true`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sonarExecuteScan` 
    
    </td>
    <td valign="top">
    
    Define code quality and security checks to be executed in the **Compliance** stage.
    
    </td>
    <td valign="top">
    
    You've set the `sonarExecuteScan` parameter in the **Compliance** stage to `true`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cloudFoundryDeploy` 
    
    </td>
    <td valign="top">
    
    Define the Cloud Foundry space to which you want to deploy.
    
    </td>
    <td valign="top">
    
    You've set the `cloudFoundryDeploy` parameter in the **Release** stage to `true`.
    
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
    
    You've set the `tmsUpload` parameter in the **Release** stage to `true`.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see  <?sap-ot O2O class="- topic/xref " href="c8314b6c8e564f42925e9d10453bd541.xml" text="" desc="" xtrc="xref:20" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/bfe48a4b12ed41868f92fa564829f752.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

7.  Commit and push your configuration.




<a name="loiobfe48a4b12ed41868f92fa564829f752__result_vgz_szy_cpb"/>

## Results

Depending on your configuration, your complete `config.yml` file should look as follows:

> ### Sample Code:  
> ```
> # Project configuration
> general:
>   buildTool: "mta"                         # "mta", "npm", or "maven"
> 
> service:
>   buildToolVersion: "MBTJ11N14"            # depends on buildTool value
>   cloudConnectors:                         # optional, only relevant if you enable Compliance stage with "SonarQube" mode           
>     sonarExecuteScan: 
>       credentialId: "<name of your cloud connector credential>"
> 
> # Stages configuration
> stages:
>   Build:
>     mavenExecuteStaticCodeChecks: false    # true, if you want to execute static code checks to verify the syntax of your Java code
>     npmExecuteLint: false                  # true, if you want to run a lint check that verifies the syntax of your JavaScript code
> 
>   Additional Unit Tests:
>     karmaExecuteTests: false               # true, if you want to execute the Karma Test Runner (default: false)
>     npmExecuteScripts: false               # true, if you want to execute test scripts that are defined in step npmExecuteScripts
> 
>   Acceptance:
>     cloudFoundryDeploy: true                                               # true, if you want to deploy to Cloud Foundry test space (default: false)
>     cfApiEndpoint: "<your SAP BTP, Cloud Foundry environment API endpoint>" 
>     cfOrg: "<name of your Cloud Foundry organization>"
>     cfSpace: "<name of your Cloud Foundry space>"                               
>     cfCredentialsId: "<name of your cedential>"
>     deployType: "standard"
>     npmExecuteEndToEndTests: true                                          # true, if you want to execute end-to-end acceptance tests using WebdriverIO (default: false)
> 
>   Compliance:
>     sonarExecuteScan: false                                                 # true, if you want to integrate continuous inspection of code quality (default: false). If you set this parameter to true, the sonarExecuteScan step is mandatory
>      
>   Release:
>     cloudFoundryDeploy: true                                                # true, if you want to deploy to Cloud Foundry. If you set this parameter to true, the CloudFoundryDeploy step is mandatory
>     cfApiEndpoint: "<your SAP BTP, Cloud Foundry environment API endpoint>" # for example, "https://api.cf.eu10.hana.ondemand.com"
>     cfOrg: "<name of your Cloud Foundry organization>"
>     cfSpace: "<name of your Cloud Foundry space>"                           # the Cloud Foundry space, to which you want to deploy your application
>     cfAppName: "<name of your application>"    
>     cfCredentialsId: "<name of your cedential>"
>     deployType: "standard"
>     tmsUpload: true                                                         # true, if you want to upload your artifact to SAP Cloud Transport Management. If you set this parameter to true, the tmsUpload step is mandatory
> 
> # Steps configuration
> steps:
> # Init stage step 
>   artifactPrepareVersion:
>     versioningType: 
>       "cloud_noTag"                                                         # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
>                                                                             # or "library" for maven. In this case, the version needs to be set in the pom.xml file
> # Build stage step 
>   npmExecuteLint:
>     failOnError: false                                                      # true, if you want your pipeline to fail, if the lint check reveals any errors
> 
> # Test stage step 
>   npmExecuteScripts:                                                        # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
>     runScripts:
>         - "test"                                                            # list of script names in your package.json file to be executed 
> 
> # Acceptance stage steps 
>   cloudFoundryDeploy: false         # true, if you want to deploy to Cloud Foundry test space (default: false)
>   npmExecuteEndToEndTests:          # only relevant, if you set the npmExecuteEndToEndTests parameter in the Accepance stage to true
>     runScript: "<wdi5>"             # enter the name of the test script to be executed (you can find it in the scripts section of your package.json file) (default: "wdi5")                      
>     baseUrl: "<base url>"           # enter the URL from the Application Routes section of your application from your SAP, BTP subaccount                       														      								
>     credentialsId: "<id of your credential to authenticate against the test application>"  # tip: avoid using a technical user credential and create a special test user instead 
> 
> 
> # Compliance stage steps 
>   sonarExecuteScan:
>     serverUrl: "<sonarqube server url>"                                          # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
>     organization: "<sonarcloud organization>"                                    # only relevant for the SonarCloud configuration mode
>     projectKey: "<sonarqube project key>"                                        # project key that you provided for your SonarQube project                                      
>     sonarTokenCredentialsId: "<sonarqube credential>"                            # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
> 
> # Release stage steps 
>   cloudFoundryDeploy:                                                            # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true
>     mtaDeployParameters: "-f --version-rule ALL"
>     
>   tmsUpload:                                                                     # only relevant, if you set the tmsUpload parameter in the Release stage to true
>     nodeName: "<name of the node for the upload to SAP Cloud Transport Management>"
>     credentialsId: "<id of your credential to authenticate against SAP Cloud Transport Management>"
> 
> ```

<a name="loio0b9c5d30aff3425c96a440dce60bd9c7"/>

<!-- loio0b9c5d30aff3425c96a440dce60bd9c7 -->

## \(Optional\) Integrate SAP Cloud Transport Management into Your Pipeline

Upload your artifact to SAP Cloud Transport Management to implement a continuous delivery process for your project.



<a name="loio0b9c5d30aff3425c96a440dce60bd9c7__prereq_jst_qjl_3fb"/>

## Prerequisites

-   You have access to the SAP Cloud Transport Management service. See [Provide Access to SAP Cloud Transport Management](https://help.sap.com/viewer/7f7160ec0d8546c6b3eab72fb5ad6fd8/Cloud/en-US/13894bed9e2d4b25aa34d03d002707f9.html).

-   You have set up the SAP Cloud Transport Management service. See [Set Up the Environment to Transport Content Archives directly in an Application](https://help.sap.com/viewer/7f7160ec0d8546c6b3eab72fb5ad6fd8/Cloud/en-US/8d9490792ed14f1bbf8a6ac08a6bca64.html).

-   You’ve created a destination in the Cloud Foundry environment for each productive subaccount to which you want to transport an archive. See [Create Transport Destinations](https://help.sap.com/viewer/7f7160ec0d8546c6b3eab72fb5ad6fd8/Cloud/en-US/c9905c142cf14aea86fe2451434faed9.html).


> ### Note:  
> In the following procedure, we assume a 2-stage landscape that consists of a development and production subaccount. However, it’s also valid for landscapes with more stages, if you define the additional nodes within the transport route accordingly.



<a name="loio0b9c5d30aff3425c96a440dce60bd9c7__context_ejk_yxj_kfb"/>

## Context

With **Build** and **Deploy** stages only, your pipeline only deploys to one space in the Cloud Foundry or subaccount in the Neo environment. A full-fledged continuous delivery process, however, requires a staged landscape with several spaces or subaccounts \(for example, development and production or development, test, and production\). With SAP Cloud Transport Management, you can define nodes and routes for such a staged landscape. For more information, see [Use the Transport Landscape Wizard](https://help.sap.com/viewer/7f7160ec0d8546c6b3eab72fb5ad6fd8/Cloud/en-US/f14192ede8ac4603955b572537d6bec2.html).

When combining SAP Continuous Integration and Delivery and SAP Cloud Transport Management, after being built, the artifact is deployed to your space or subaccount and, in an additional step in the job, uploaded to SAP Cloud Transport Management. The export of the multitarget application archive \(MTAR\) triggers its transport along the transport route you’ve defined. When it has reached the import queue of the production node, the release manager manually triggers its import to the production node in the user interface of SAP Cloud Transport Management.

The following graphic shows this procedure:

  
  
**Integration of SAP Cloud Transport Management**

![Integration of the Transport Management Service](images/TMS_Integration_a844e6e.png "Integration of SAP Cloud Transport Management")

Working with the integration of SAP Cloud Transport Management comprises the following steps:

1.  Push your code changes to your source code management system or manually trigger a new build in SAP Continuous Integration and Delivery.

2.  SAP Continuous Integration and Delivery builds, tests, and deploys your changes, and uploads them to SAP Cloud Transport Management. The artifact appears in the import queue.

3.  Validation tests are executed on the application deployed in your QA node.

4.  The release manager approves the import by selecting the transport to be imported.

5.  The application is released to the production node.


To integrate SAP Cloud Transport Management into SAP Continuous Integration and Delivery, perform the following tasks:

<a name="task_zvp_q25_blb"/>

<!-- task\_zvp\_q25\_blb -->

### Create the Service Key Credential

Create the Service Key credential for SAP Cloud Transport Management.



<a name="task_zvp_q25_blb__steps_cgp_z25_blb"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount in which you’ve created an instance for SAP Cloud Transport Management.

2.  From the navigation area, choose <span class="SAP-icons-V5"></span> *Spaces* and select your space in which you’ve created the Cloud Transport Management instance.

3.  From the navigation area, choose <span class="SAP-icons-V5"></span> *Services* \> *Instances*.

4.  Choose the name of your service instance.

5.  From the navigation area, choose :key: *Service Keys*.

6.  Copy the entire service key.

7.  In SAP Continuous Integration and Delivery, create a new Service Key credential and paste the copied service key into the respective text field. See [Creating Credentials](creating-credentials-6658c81.md).

8.  When creating a job, use the newly created Service Key credential in the *Upload to Cloud Transport Management* stage.

    For the *Node Name*, see the following section.


<a name="task_rdg_pn5_blb"/>

<!-- task\_rdg\_pn5\_blb -->

### Create the Transport Nodes and Route

Create nodes for your spaces or subaccounts, connect them through a transport route, and provide the respective data to SAP Continuous Integration and Delivery.



<a name="task_rdg_pn5_blb__steps_g3s_sn5_blb"/>

## Procedure

1.  In SAP Cloud Transport Management, create a node for each of your development and production spaces or subaccounts. See [Create Transport Nodes](https://help.sap.com/viewer/7f7160ec0d8546c6b3eab72fb5ad6fd8/Cloud/en-US/f71a4d5550cd453ea824d5b5c677969d.html).

2.  Connect the nodes through a transport route. See [Create Transport Routes](https://help.sap.com/viewer/7f7160ec0d8546c6b3eab72fb5ad6fd8/Cloud/en-US/dddb74937a014aea8d3d76d740180597.html).

3.  In your job configuration in SAP Continuous Integration and Delivery, enter the name of your development node in the *Upload to SAP Cloud Transport Management* stage.

4.  When you've finished your job creation, choose *Add*.


