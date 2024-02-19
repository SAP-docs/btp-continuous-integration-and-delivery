<!-- loio79f26e6123cf451c9f70b461ba0ac5d4 -->

# Configure an SAP Cloud Application Programming Model Job in Your Repository

Configure the stages of your SAP Cloud Application Programming Model job in your source code management system.



<a name="loio79f26e6123cf451c9f70b461ba0ac5d4__prereq_jsb_3gc_clb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have a CAP project with the recommended files and folders structure. For how to start a CAP project with the recommended files and folders structure, see [Getting Started](https://cap.cloud.sap/docs/get-started/).

-   You have write permission for the repository in which your project sources reside.

-   In the repository of your project, you have a folder named `.pipeline`, which contains a file named `config.yml`. If you don't have this folder and file yet, create them.




<a name="loio79f26e6123cf451c9f70b461ba0ac5d4__context_qhy_gvr_cpb"/>

## Context

Depending on your configuration, the SAP Cloud Application Programming Model pipeline can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/Cloud_SDK_Pipeline_Stages_2d26d26.png)



<a name="loio79f26e6123cf451c9f70b461ba0ac5d4__steps_w2s_rgc_clb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in [Create a Job](create-a-job-d748920.md). As *Pipeline*, choose *SAP Cloud Application Programming Model*.

2.  In the *Stages* tab, choose *Source Repository* from the *Configuration Mode* dropdown list.

3.  Choose *Create*.

4.  In your `config.yml` file in your repository, add the following initial configuration:

    ```
    # Project configuration
    general:
      buildTool: "mta"                                  # "mta", "npm", or "maven" (default: "mta")
    
    service:
      buildToolVersion: "MBTJ11N14"                     # depends on buildTool value, see table below
    
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
    >     cfApiEndpoint: "<YOUR SAP BTP, CLOUD FOUNDRY ENVIRONMENT API ENDPOINT>" 
    >     cfOrg: "<NAME OF YOUR CLOUD FOUNDRY ORGANIZATION>"
    >     cfSpace: "<NAME OF YOUR CLOUD FOUNDRY SPACE>"                               
    >     cfCredentialsId: "<NAME OF YOUR CEDENTIAL>"
    >     npmExecuteEndToEndTests: true                                          # true, if you want to execute end-to-end acceptance tests using WebdriverIO (default: false)
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
    
    `npmExecuteEndToEndTests` 
    
    </td>
    <td valign="top">
    
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
    >     cfApiEndpoint: "<YOUR SAP BTP, CLOUD FOUNDRY ENVIRONMENT API ENDPOINT>"  
    >     cfOrg: "<NAME OF YOUR CLOUD FOUNDRY ORGANIZATION>"
    >     cfSpace: "<NAME OF YOUR CLOUD FOUNDRY SPACE>"                            
    >     cfAppName: "<NAME OF YOUR APPLICATION>"   
    >     cfCredentialsId: "<NAME OF YOUR CEDENTIAL>"
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
    >     runScript: "<wdio>"             # enter the name of the test script to be executed (you can find it in the scripts section of your package.json file) (default: "wdio")                      
    >     baseUrl: "<BASE URL>"           # enter the URL from the Application Routes section of your application from your SAP, BTP subaccount                       														      								
    >     credentialsId: "<ID OF YOUR CREDENTIAL TO AUTHENTICATE AGAINST THE TEST APPLICATION>"  # tip: avoid using a technical user credential and create a special test user instead 
    > 
    > # Compliance stage steps 
    >   sonarExecuteScan:
    >     serverUrl: "<SONARQUBE SERVER URL>"                                                    # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
    >     organization: "<SONARCLOUD ORGANIZATION>"                                              # only relevant for the SonarCloud configuration mode
    >     projectKey: "<SONARQUBE PROJECT KEY>"                                                  # project key that you provided for your SonarQube project                                   
    >     sonarTokenCredentialsId: "<SONARQUBE CREDENTIAL>"                                      # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
    > 
    > # Release stage steps 
    >   cloudFoundryDeploy:                                                                      # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true
    >     mtaDeployParameters: "-f --version-rule ALL"
    >     
    >   tmsUpload:                                                                               # only relevant, if you set the tmsUpload parameter in the Release stage to true
    >     nodeName: "<NAME OF THE NODE FOR THE UPLOAD TO SAP CLOUD TRANSPORT MANAGEMENT>"
    >     credentialsId: "<ID OF YOUR CREDENTIAL TO AUTHENTICATE AGAINST SAP CLOUD TRANSPORT MANAGEMENT>" 
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
    
7.  Commit and push your configuration.




<a name="loio79f26e6123cf451c9f70b461ba0ac5d4__result_vgz_szy_cpb"/>

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
>     cloudFoundryDeploy: true                                                # true, if you want to deploy to Cloud Foundry acceptance space. If you set this parameter to true, the cloudFoundryDeploy step is mandatory
>     cfApiEndpoint: "<YOUR SAP BTP, CLOUD FOUNDRY ENVIRONMENT API ENDPOINT>" # for example, "https://api.cf.eu10.hana.ondemand.com"
>     cfOrg: "<NAME OF YOUR CLOUD FOUNDRY ORGANIZATION>"
>     cfSpace: "<NAME OF YOUR CLOUD FOUNDRY SPACE>"                           # the Cloud Foundry space, in which you want to execute uiVeri5 tests
>     cfAppName: "<NAME OF YOUR APPLICATION>"
>     cfCredentialsId: "<NAME OF YOUR CEDENTIAL>"
>     npmExecuteEndToEndTests: true                                          # true, if you want to execute end-to-end acceptance tests (default: false)
> 
>   Compliance:
>     sonarExecuteScan: false                                                 # true, if you want to integrate continuous inspection of code quality (default: false). If you set this parameter to true, the sonarExecuteScan step is mandatory
>      
>   Release:
>     cloudFoundryDeploy: true                                                # true, if you want to deploy to Cloud Foundry. If you set this parameter to true, the CloudFoundryDeploy step is mandatory
>     cfApiEndpoint: "<YOUR SAP BTP, CLOUD FOUNDRY ENVIRONMENT API ENDPOINT>" # for example, "https://api.cf.eu10.hana.ondemand.com"
>     cfOrg: "<NAME OF YOUR CLOUD FOUNDRY ORGANIZATION>"
>     cfSpace: "<NAME OF YOUR CLOUD FOUNDRY SPACE>"                           # the Cloud Foundry space, to which you want to deploy your application
>     cfAppName: "<NAME OF YOUR APPLICATION>"    
>     cfCredentialsId: "<NAME OF YOUR CEDENTIAL>"
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
>     runScript: "<wdio>"             # enter the name of the test script to be executed (you can find it in the scripts section of your package.json file) (default: "wdio")                      
>     baseUrl: "<BASE URL>"           # enter the URL from the Application Routes section of your application from your SAP, BTP subaccount                       														      								
>     credentialsId: "<ID OF YOUR CREDENTIAL TO AUTHENTICATE AGAINST THE TEST APPLICATION>"  # tip: avoid using a technical user credential and create a special test user instead 
> 
> 
> # Compliance stage steps 
>   sonarExecuteScan:
>     serverUrl: "<SONARQUBE SERVER URL>"                                          # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
>     organization: "<SONARCLOUD ORGANIZATION>"                                    # only relevant for the SonarCloud configuration mode
>     projectKey: "<SONARQUBE PROJECT KEY>"                                        # project key that you provided for your SonarQube project                                      
>     sonarTokenCredentialsId: "<SONARQUBE CREDENTIAL>"                            # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
> 
> # Release stage steps 
>   cloudFoundryDeploy:                                                            # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true
>     mtaDeployParameters: "-f --version-rule ALL"
>     
>   tmsUpload:                                                                     # only relevant, if you set the tmsUpload parameter in the Release stage to true
>     nodeName: "<NAME OF THE NODE FOR THE UPLOAD TO SAP CLOUD TRANSPORT MANAGEMENT>"
>     credentialsId: "<ID OF YOUR CREDENTIAL TO AUTHENTICATE AGAINST SAP CLOUD TRANSPORT MANAGEMENT>"
> 
> ```

