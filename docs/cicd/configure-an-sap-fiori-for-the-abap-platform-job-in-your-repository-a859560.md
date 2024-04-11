<!-- loioa859560bca4149488f8e94e9c9a9adad -->

# Configure an SAP Fiori for the ABAP Platform Job in Your Repository

Configure the stages of your SAP Fiori for the ABAP platform job in your repository.



<a name="loioa859560bca4149488f8e94e9c9a9adad__prereq_vmv_pl3_xlb"/>

## Prerequisites

> ### Restriction:  
> This pipeline only works for on-premises scenarios.

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAPUI5/SAP Fiori project for the ABAP platform. See [Create an SAP Fiori Project](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/46664de4d6944471b6c29a0681bfd0fc.html).

-   You have configured the SAP Cloud Connector to ensure secure communication between SAP Continuous Integration and Delivery and the ABAP system.

-   You have installed the SAP component SAP\_UI 7.53 or higher on your ABAP system. See [Software Component SAP\_UI](https://help.sap.com/docs/ABAP_PLATFORM_NEW/6f3c61a7a5b94447b80e72f722b0aad7/35828457ed26452db8d51c840813f1bb.html?version=202009.002).

-   You have enabled the OData service to load data to the SAPUI5 ABAP repository. See [Using an OData Service to Load Data to the SAPUI5 ABAP Repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).

-   You have the S\_DEVELOP authorization to perform operations in your SAPUI5 ABAP repository. See [Using an OData Service to Load Data to the SAPUI5 ABAP Repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).




<a name="loioa859560bca4149488f8e94e9c9a9adad__context_ift_r2y_q4b"/>

## Context

Depending on your configuration, the SAP Fiori for the ABAP platform pipeline can comprise the following stages:

![](images/ABAP_Platform_Stages_216f127.png)



<a name="loioa859560bca4149488f8e94e9c9a9adad__steps_sdl_ql3_xlb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in  <?sap-ot O2O class="- topic/xref " href="d748920175554221be1ba8b461ada030.xml" text="" desc="" xtrc="xref:12" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/a859560bca4149488f8e94e9c9a9adad.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . As *Pipeline*, choose *SAP Fiori for ABAP platform*.

2.  In the *Stages* tab, choose *Source Repository* from the *Configuration Mode* dropdown list.

    > ### Note:  
    > If you have already configured your job in the job editor, you can export the editor-based configuration information to a YAML file by pressing the YML button. Press *Edit* and switch to *Source Repository*. For more information, see [Export Job Configuration Data](export-job-configuration-data-60a76d7.md).

3.  Choose *Create*.

4.  In the Git repository in which your project sources reside, create a new file named `.pipeline/config.yml`.

5.  Copy the following content into your `config.yml` file:

    ```
    # Project configuration
    general:
      buildTool: "npm"
    
    service: 
      buildToolVersion: "N14"           
      cloudConnectors:
        transportRequestUploadCTS:
          credentialId: "<CredentialID>"
        sonarExecuteScan:                                   # optional, only relevant if you enable Compliance stage with "SonarQube" mode           
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
    
    Enter `"npm"` as build tool.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `buildToolVersion` 
    
    </td>
    <td valign="top">
    
    Enter the build tool version you want to use. For more information, see [Supported Tools](supported-tools-5949283.md).

    If you don't define a build tool version, a default one \(`"N14"`\) is used.
    
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
    
6.  Configure the **stages** of your job as follows:

    **Build and Test**

    > ### Sample Code:  
    > ```
    > # Stages configuration
    > stages:
    >   Build:
    >     npmExecuteLint: true                  # true, if you want to run a lint check that verifies the syntax of your JavaScript code (default: false)
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
    
    **Additional Unit Tests**

    > ### Sample Code:  
    > ```
    >   Additional Unit Tests:
    >      karmaExecuteTests: false  # true, if you want to execute the Karma Test Runner (default: false) 
    >      npmExecuteScripts: true   # true, if you want to execute test scripts that are defined in step npmExecuteScripts (default: false)
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
    
    **Malware Scan**

    > ### Sample Code:  
    > ```
    >   Malware Scan: 
    >      malwareExecuteScan: true   # true, if you want your pipeline to execute malware scanning (default: false) 
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


    .
    
    </td>
    </tr>
    </table>
    
    **Release**

    > ### Sample Code:  
    > ```
    > Release:
    >     transportRequestUploadCTS: true                                           # true, if you want to upload your application to the ABAP platform
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
    
7.  Configure the **steps** of your configuration as follows:

    > ### Sample Code:  
    > ```
    > # Steps configuration
    >  steps: 
    > # Init stage step 
    >   artifactPrepareVersion: 
    >     versioningType: "cloud_noTag"       # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
    > 
    >   npmExecuteLint: 
    >     failOnError: false                  # true, if you want your pipeline to fail, if the lint check reveals any errors
    > 
    > # Test stage step 
    >   npmExecuteScripts:                    # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
    >     runScripts: 
    >       - "test"                          # list of script names in your package.json file to be executed 
    > 
    > # Complaince stage steps 
    >   sonarExecuteScan:
    >     serverUrl: "<SONARQUBE SERVER URL>"                                                    # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
    >     organization: "<SONARCLOUD ORGANIZATION>"                                              # only relevant for the SonarCloud configuration mode
    >     projectKey: "<SONARQUBE PROJECT KEY>"                                                  # project key that you provided for your SonarQube project                                   
    >     sonarTokenCredentialsId: "<SONARQUBE CREDENTIAL>"                                      # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
    > 
    > # Release stage steps 
    >   transportRequestUploadCts:                                                               # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true 
    >     endpoint: "<http://host:port>"                                                         # the URL of your ABAP server using the HTTP protocol (http://<host:port>)
    >     uploadCredentialsId: "<ABAP CREDENTIAL>"                                               # credential of type "Basic Authentication" to authenticate your pipeline against your ABAP system
    >     abapPackage: "<ABAP PACKAGE NAME>"                                                     # the name of the ABAP package you want to upload your application to
    >     applicationName: "<NAME>"                                                              # the name of your application
    >     applicationDescription: "<DESCRIPTION>"                                                # a description for your application
    >     transportRequestId: "<TRNSPORT REQUEST ID>"                                            # the transport request ID of an open CTS+ transport in your ABAP system
    > 
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
    > You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see  <?sap-ot O2O class="- topic/xref " href="c8314b6c8e564f42925e9d10453bd541.xml" text="" desc="" xtrc="xref:19" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/a859560bca4149488f8e94e9c9a9adad.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

8.  Commit and push your configuration.




<a name="loioa859560bca4149488f8e94e9c9a9adad__result_vgz_szy_cpb"/>

## Results

Depending on your configuration, your complete `config.yml` file should look as follows:

> ### Sample Code:  
> ```
> # Project configuration
> general:
>   buildTool: "npm"     
> 
> service: 
>   buildToolVersion: "N14"           
>   cloudConnectors:
>     transportRequestUploadCTS:
>       credentialId: "<CredentialID>"
>     sonarExecuteScan: 
>       credentialId: "<CredentialID>"      # optional, only relevant if you enable Compliance stage with "SonarQube" mode                 
> 
> # Stages configuration
> stages:
>   Build:
>     npmExecuteLint: true                  # true, if you want to run a lint check that verifies the syntax of your JavaScript code (default: false)
>   
>   Additional Unit Tests:
>      karmaExecuteTests: false             # true, if you want to execute the Karma Test Runner (default: false) 
>      npmExecuteScripts: true              # true, if you want to execute test scripts that are defined in step npmExecuteScripts (default: false)
> 
>   Malware Scan: 
>      malwareExecuteScan: true             # true, if you want your pipeline to execute malware scanning (default: false) 
>  
>   Compliance:
>     sonarExecuteScan: false              # true, if you want to integrate continuous inspection of code quality (default: false). If you set this parameter to true, the sonarExecuteScan step is mandatory
> 
>   Release:
>     cloudFoundryDeploy: true              # true, if you want to deploy to Cloud Foundry. If you set this parameter to true, the CloudFoundryDeploy step is mandatory
>     cfApiEndpoint: "<YOUR SAP BTP, CLOUD FOUNDRY ENVIRONMENT API ENDPOINT>" # for example, https://api.cf.eu10.hana.ondemand.com
>     cfOrg: "<NAME OF YOUR CLOUD FOUNDRY ORGANIZATION>"
>     cfSpace: "<NAME OF YOUR CLOUD FOUNDRY SPACE>"
>     cfCredentialsId: "<NAME OF YOUR CEDENTIAL>"
>     tmsUpload: true                       # true if you want to upload your artifact to SAP Cloud Transport Management. If you set this parameter to true, the tmsUpload step is mandatory
> 
> # Steps configuration
>  steps: 
> # Init stage step 
>   artifactPrepareVersion: 
>     versioningType: "cloud_noTag"         # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
> 
>   npmExecuteLint: 
>     failOnError: false                    # true, if you want your pipeline to fail, if the lint check reveals any errors
> 
> # Test stage step 
>   npmExecuteScripts:                      # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
>     runScripts: 
>       - "test"                            # list of script names in your package.json file to be executed
> 
> # Complaince stage steps 
>   sonarExecuteScan:
>     serverUrl: "<SONARQUBE SERVER URL>"                                                    # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
>     organization: "<SONARCLOUD ORGANIZATION>"                                              # only relevant for the SonarCloud configuration mode
>     projectKey: "<SONARQUBE PROJECT KEY>"                                                  # project key that you provided for your SonarQube project                                      
>     sonarTokenCredentialsId: "<SONARQUBE CREDENTIAL>"                                      # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
> 
> # Release stage steps 
>   transportRequestUploadCts:                                                               # only relevant, if you set the cloudFoundryDeploy parameter in the Release stage to true 
>     endpoint: "<http://host:port>"                                                         # the URL of your ABAP server using the HTTP protocol (http://<host:port>)
>     uploadCredentialsId: "<ABAP CREDENTIAL>"                                               # credential of type "Basic Authentication" to authenticate your pipeline against your ABAP system
>     abapPackage: "<ABAP PACKAGE NAME>"                                                     # the name of the ABAP package you want to upload your application to
>     applicationName: "<NAME>"                                                              # the name of your application
>     applicationDescription: "<DESCRIPTION>"                                                # a description for your application
>     transportRequestId: "<TRNSPORT REQUEST ID>"                                            # the transport request ID of an open CTS+ transport in your ABAP system
> 
> 
> ```

<a name="loio642bcb08b27c4d7ab5008aa277225189"/>

<!-- loio642bcb08b27c4d7ab5008aa277225189 -->

## \(Optional\) Configure the Additional Unit Test Stage

Before running the **Additional Unit Tests** stage in your job, add the Karma test configuration to your project.



<a name="loio642bcb08b27c4d7ab5008aa277225189__prereq_fgb_ctn_blb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery.

-   In your repository, you have an SAPUI5/SAP Fiori project. See [Create an SAP Fiori Project](https://developers.sap.com/tutorials/appstudio-fioriapps-create.html).




<a name="loio642bcb08b27c4d7ab5008aa277225189__context_sgy_rjw_1bc"/>

## Context

The following steps will introduce [Karma](https://github.com/SAP/karma-ui5), a plugin to help test your SAPUI5 project.



<a name="loio642bcb08b27c4d7ab5008aa277225189__steps_kmn_qtn_blb"/>

## Procedure

1.  Append the following Karma dependencies to your project:

    ```
    npm install --save-dev karma karma-ui5 karma-chrome-launcher karma-coverage
    ```

2.  Append the following Karma script to your `package.json`:

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

    The `ui5` property is configured using `configPath`, which loads the default SAPUI5 resources. If a mock server is later added to the project, the `configPath` should be updated to `ui5-mock.yaml`. See [Installing MockServer](https://help.sap.com/docs/SAP_FIORI_tools/17d50220bcd848aa854c9c182d65b699/253805578f04461a9741983a630ce4f1.html?locale=en-USstate%3DPRODUCTION).

5.  To validate your configuration, run the new test script:

    ```
    npm run test
    ```

    In the console log, you can see that the ChromeHeadless browser is now connected, but as you haven’t added a test plan, yet,no tests were executed.




<a name="loio642bcb08b27c4d7ab5008aa277225189__postreq_sjr_ylw_1bc"/>

## Next Steps

To add unit and integration tests to your project, refer to the [SAPUI5 Overview and Testing Strategy Guide](https://sapui5.hana.ondemand.com/sdk/#/topic/ab134ef3932c4b42898c79c10341e8b5).

