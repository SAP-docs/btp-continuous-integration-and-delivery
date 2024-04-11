<!-- loio4f6185c3282b4e998fd7d1b202b14615 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure an SAP Fiori in the Neo Environment Job in Your Repository

Configure the stages of your SAP Fiori in the Neo environment job in your repository.



<a name="loio4f6185c3282b4e998fd7d1b202b14615__prereq_vmv_pl3_xlb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAPUI5/SAP Fiori project for the Neo environment.




<a name="loio4f6185c3282b4e998fd7d1b202b14615__context_hnt_5hy_q4b"/>

## Context

Depending on your configuration, the SAP Fiori in the Neo environment pipeline can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/UI5_Pipeline_Steps_ad534be.png)



<a name="loio4f6185c3282b4e998fd7d1b202b14615__steps_sdl_ql3_xlb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in  <?sap-ot O2O class="- topic/xref " href="d748920175554221be1ba8b461ada030.xml" text="" desc="" xtrc="xref:9" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/4f6185c3282b4e998fd7d1b202b14615.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . As *Pipeline*, choose *SAP Fiori in the Neo Environment*.

2.  In the *Stages* tab, choose *Source Repository* from the *Configuration Mode* dropdown list.

    > ### Note:  
    > If you have already configured your job in the job editor, you can export the editor-based configuration information to a YAML file by pressing the YML button. Press *Edit* and switch to *Source Repository*. For more information, see [Export Job Configuration Data](export-job-configuration-data-60a76d7.md).

3.  Choose *Create*.

4.  In the repository in which your project sources reside, create a new file named `.pipeline/config.yml`.

5.  Copy the following content into your `.pipeline/config.yml`file:

    ```
    # Project configuration
    general:
      buildTool: "mta"    
    
    service: 
      buildToolVersion: "MBTJ11N14"     
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
    
    Enter `"mta"` as build tool. For more information on the Cloud MTA Build Tool \(MBT\), see [Cloud MTA Build Tool](https://sap.github.io/cloud-mta-build-tool/).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `buildToolVersion` 
    
    </td>
    <td valign="top">
    
    Enter the build tool version you want to use. For more information, see [Supported Tools](supported-tools-5949283.md).

    If you don't define a build tool version, a default one \(`"MBTJ11N14"`\) is used.
    
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
    
6.  Configure the **stages** of your job as follows:

    > ### Note:  
    > You can freely choose which stages to add to your pipeline.

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
    
    **Malware Scan**

    > ### Sample Code:  
    > ```
    >   Malware Scan: 
    >       malwareExecuteScan: true     # true, if you want your pipeline to execute malware scanning (default: false) 
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
    
    **Acceptance**

    > ### Sample Code:  
    > ```
    >   
    > 
    >   Acceptance:
    >     npmExecuteEndToEndTests: true              # true, if you want to execute end-to-end acceptance tests using WebdriverIO
    >     neoDeploy: true                            # true, if you want to deploy to a Neo test subaccount (default: false)
    >     neo:
    >       account: "<account>"
    >       host: "<host>" 
    >       credentialsId: "<credential-id>"         # enter an OAuth credential
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
    
    `npmExecuteEndToEndTests` 
    
    </td>
    <td valign="top">
    
    > ### Note:  
    > The ***npmExecuteEndToEndTests*** step is available for build tool versions Node 16 and above. The WebdriverIO testing framework is no longer compatible with older Node.js versions.

    Specify the relevant parameters in the ***npmExecuteEndToEndTests*** step configuration to enable WebdriverIO test execution.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `neoDeploy` 
    
    </td>
    <td valign="top">
    
    Enable or disable the **neoDeploy** stage by choosing either `true` or `false`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `neo` 
    
    </td>
    <td valign="top">
    
    Specify the relevant parameters in the ***neo*** step configuration to deploy your test application to the SAP BTP, Neo environment.

    For adapting the values in brackets, have a look at the following hints:

    -   The ID of your SAP BTP subaccount is displayed as *Technical Name* in the overview of your subaccount in the SAP BTP cockpit.

    -   To find the host of your SAP BTP subaccount, see [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).

    -   For the deploy credential, create an OAuth credential for the subaccount to which you want to deploy your application. See [\(Optional\) Configure the Deploy Credential](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio52bc22233ef84527bc409fbe748947b8).



    
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
    >     neoDeploy: true                                                           # true, if you want to deploy to the Neo environment (default:false)
    >     neo: 
    >       account: "<account>"
    >       host: "<host>" 
    >       credentialsId: "<credential-id>"                                        # enter an OAuth credential
    >     tmsUpload: true                                                           # true, if you want to upload your artifact to SAP Cloud Transport Management (default: false)
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
    
    `neoDeploy` 
    
    </td>
    <td valign="top">
    
    Enable or disable the **neoDeploy** stage by choosing either `true` or `false`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `neo` 
    
    </td>
    <td valign="top">
    
    Specify the relevant parameters in the ***neo*** step configuration to deploy your application to the SAP BTP, Neo environment.

    For adapting the values in brackets, have a look at the following hints:

    -   The ID of your SAP BTP subaccount is displayed as *Technical Name* in the overview of your subaccount in the SAP BTP cockpit.

    -   To find the host of your SAP BTP subaccount, see [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).

    -   For the deploy credential, create an OAuth credential for the subaccount to which you want to deploy your application. See [\(Optional\) Configure the Deploy Credential](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio52bc22233ef84527bc409fbe748947b8).



    
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
    
7.  Configure the **steps** of your configuration as follows:

    > ### Sample Code:  
    > ```
    > # Steps configuration
    >  steps: 
    > # Init stage step 
    >   artifactPrepareVersion: 
    >     versioningType: "cloud_noTag"     # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter
    > 
    >   npmExecuteLint: 
    >     failOnError: false                # true, if you want your pipeline to fail, if the lint check reveals any errors
    > 
    > # Test stage step 
    >   npmExecuteScripts:                  # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
    >     runScripts: 
    >       - "test"                        # list of script names in your package.json file to be executed 
    > 
    > # Acceptance stage steps 
    >   npmExecuteEndToEndTests:            # only relevant, if you set the npmExecuteEndToEndTests parameter in the Accepance stage to true
    >     runScript: "<wdi5"               # enter the name of the test script to be executed (you can find it in the scripts section of your package.json file) (default: "wdi5")                      
    >     baseUrl: "<BASE URL>"             # enter the URL from the Application Routes section of your application from your SAP, BTP subaccount                       														      								
    >     credentialsId: "<ID OF YOUR CREDENTIAL TO AUTHENTICATE AGAINST THE TEST APPLICATION>"  # tip: avoid using a technical user credential and create a special test user instead  
    >   neoDeploy:                          # only relevant, if you set the NeoDeploy parameter in the Accepance stage to true
    >  
    >     neo:
    >       credentialType: "<SecretFile>"  # enter the credential type
    > 
    > # Complaince stage steps 
    >   sonarExecuteScan:
    >     serverUrl: "<SONARQUBE SERVER URL>"                                                    # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
    >     organization: "<SONARCLOUD ORGANIZATION>"                                              # only relevant for the SonarCloud configuration mode
    >     projectKey: "<SONARQUBE PROJECT KEY>"                                                  # project key that you provided for your SonarQube project                                   
    >     sonarTokenCredentialsId: "<SONARQUBE CREDENTIAL>"                                      # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
    > 
    > # Release stage steps 
    >   tmsUpload:                          # only relevant, if you set the tmsUpload parameter in the Release stage to true
    >     nodeName: "<NAME OF THE NODE FOR THE UPLOAD TO SAP CLOUD TRANSPORT MANAGEMENT>"
    >     credentialsId: "<ID OF YOUR CREDENTIAL TO AUTHENTICATE AGAINST SAP CLOUD TRANSPORT MANAGEMENT>"
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
    
    Define additional test scripts from your `package.json` file to be executed in the `Additional Unit Tests` stage.
    
    </td>
    <td valign="top">
    
    You've set the `npmExecuteScripts` parameter in the `Additional Unit Tests` stage to `true`.
    
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
    
    `tmsUpload` 
    
    </td>
    <td valign="top">
    
    Define the SAP Cloud Transport Management node to which you want to upload your artifact.

    For adapting the values in brackets, have a look at the following hints:

    -   For more information on why and how to integrate SAP Cloud Transport Management into your continuous delivery process, see[\(Optional\) Integrate SAP Cloud Transport Management into Your Pipeline.](https://help.sap.com/viewer/99c72101f7ee40d0b2deb4df72ba1ad3/Cloud/en-US/4f6185c3282b4e998fd7d1b202b14615.html#loio0b9c5d30aff3425c96a440dce60bd9c7).

    -   To authenticate your pipeline against SAP Cloud Transport Management, create a Service Key. See [Creating Credentials](creating-credentials-6658c81.md).



    
    </td>
    <td valign="top">
    
    You've set the `tmsUpload` parameter in the `Release` stage to `true`.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see  <?sap-ot O2O class="- topic/xref " href="c8314b6c8e564f42925e9d10453bd541.xml" text="" desc="" xtrc="xref:23" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/4f6185c3282b4e998fd7d1b202b14615.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

8.  Commit and push your configuration.




<a name="loio4f6185c3282b4e998fd7d1b202b14615__result_vgz_szy_cpb"/>

## Results

Depending on your configuration, your complete `config.yml` file should look as follows:

> ### Sample Code:  
> ```
> # Project configuration
> general:
>   buildTool: "mta"        
> 
> service: 
>   buildToolVersion: "MBTJ11N14"     
>   cloudConnectors:                                  # optional, only relevant if you enable Compliance stage with "SonarQube" mode           
>     sonarExecuteScan: 
>       credentialId: "<name of your cloud connector credential>"
> 
> # Stages configuration
> stages:
>   Build:
>     npmExecuteLint: true                    # true, if you want to run a lint check that verifies the syntax of your JavaScript code (default: false)
> 
>   Additional Unit Tests:
>      karmaExecuteTests: false               # true, if you want to execute the Karma Test Runner (default: false) 
>      npmExecuteScripts: true                # true, if you want to execute test scripts that are defined in step npmExecuteScripts (default: false)
> 
>   Malware Scan: 
>      malwareExecuteScan: true               # true, if you want your pipeline to execute malware scanning (default: false) 
>   
>   Acceptance:
>     npmExecuteEndToEndTests: true           # true, if you want to execute end-to-end acceptance tests using WebdriverIO
>     neoDeploy: true                         # true, if you want to deploy to a Neo test subaccount (default: false)
>     neo:
>       account: "<account>"
>       host: "<host>" 
>       credentialsId: "<credential-id>"      # enter an OAuth credential
> 
>   Compliance: 
>     sonarExecuteScan: false                 # true, if you want to integrate continuous inspection of code quality (default: false). If you set this parameter to true, the sonarExecuteScan step is mandatory
> 
>   Release:
>     neoDeploy: true                         # true, if you want to deploy to a Neo subbacount (default:false)
>     neo: 
>       account: "<account>"
>       host: "<host>" 
>       credentialsId: "<credential-id>"      # OAuth credential
>     tmsUpload: true                         # true, if you want to upload your artifact to SAP Cloud Transport Management (default: false)
> 
>  steps: 
> # Init stage step 
>   artifactPrepareVersion: 
>     versioningType: "cloud_noTag"           # or "cloud", if you want your pipeline to write Git tags. In this case, you need to add the gitHttpsCredentialsId parameter    
> 
>   npmExecuteLint: 
>     failOnError: false                      # true, if you want your pipeline to fail, if the lint check reveals any errors
> 
> # Test stage step 
>   npmExecuteScripts:                        # only relevant, if you set the npmExecuteScripts parameter in the Additional Unit Tests stage to true
>     runScripts: 
>       - "test"                              # list of script names in your package.json file to be executed 
> 
> # Acceptance stage steps 
>   npmExecuteEndToEndTests:                  # only relevant, if you set the npmExecuteEndToEndTests parameter in the Accepance stage to true
>     runScript: "<wdi5>"                     # enter the name of the test script to be executed (you can find it in the scripts section of your package.json file) (default: "wdi5")                      
>     baseUrl: "<base url>"                   # enter the URL from the Application Routes section of your application from your SAP, BTP subaccount                       														      								
>     credentialsId: "<ID OF YOUR CREDENTIAL TO AUTHENTICATE AGAINST THE TEST APPLICATION>"  # tip: avoid using a technical user credential and create a special test user instead  
>   neoDeploy:                                # only relevant, if you set the NeoDeploy parameter in the Accepance stage to true
>  
>     neo:
>       credentialType: "<SecretFile>"        # enter the credential type
> 
> # Complaince stage steps 
>   sonarExecuteScan:
>     serverUrl: "<SONARQUBE SERVER URL>"                                                    # "https://sonarcloud.io" for SonarCloud and custom URL to your internet-facing SonarQube server for SonarQube
>     organization: "<SONARCLOUD ORGANIZATION>"                                              # only relevant for the SonarCloud configuration mode
>     projectKey: "<SONARQUBE PROJECT KEY>"                                                  # project key that you provided for your SonarQube project                                      
>     sonarTokenCredentialsId: "<SONARQUBE CREDENTIAL>"                                      # credential of type "Secret Text", containing the token that was generated when creating your SonarQube project
>  
> # Release stage steps 
>   tmsUpload:                                                                               # only relevant, if you set the tmsUpload parameter in the Release stage to true
>     nodeName: "<NAME OF THE NODE FOR THE UPLOAD TO SAP CLOUD TRANSPORT MANAGEMENT>"
>     credentialsId: "<ID OF YOUR CREDENTIAL TO AUTHENTICATE AGAINST SAP CLOUD TRANSPORT MANAGEMENT>"
> ```

<a name="loio708413d4c586409489cbb17d1fbe1e5c"/>

<!-- loio708413d4c586409489cbb17d1fbe1e5c -->

## Enable the Build and Additional Unit Tests Stages

Set up the **Build** and **Additional Unit Tests** stages of your SAP Fiori in the Neo environment job.



<a name="loio708413d4c586409489cbb17d1fbe1e5c__prereq_dvs_hg3_xlb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your repository, you have an SAPUI5/SAP Fiori project for the Neo environment.




## Context

The **Build** and **Additional Unit Tests** stages of an SAPUI5 module are controlled by the `package.json` and `Gruntfile.js` files. For projects that are based on the Cloud Foundry environment, these files are expected in each HTML5 module defined in the `mta.yaml` file.

> ### Note:  
> **Prepare Your Project** is also relevant if you want your pipeline to execute the **Build** task only.



## Procedure

1.  Make sure that the following dependencies and scripts are defined in the `package.json` file:

    ```
    {
        (...)
        "devDependencies": {
            (...)
            "@sap/grunt-sapui5-bestpractice-build": "^1.4.1",
            "@sap/grunt-sapui5-bestpractice-test": "^2.0.1"
        },
        "scripts": {
            (...)
            "test": "grunt unit_and_integration_tests"
        }
    }
    ```

2.  Make sure that the `Gruntfile.js` file contains the following calls for the registration of tasks:

    ```
    module.exports = function(grunt) {
        "use strict";
        grunt.loadNpmTasks("@sap/grunt-sapui5-bestpractice-build");
        grunt.registerTask("default", [
            "clean",
            "lint",
            "build"
        ]);
        grunt.loadNpmTasks("@sap/grunt-sapui5-bestpractice-test");
        grunt.registerTask("unit_and_integration_tests", ["test"]);
        grunt.config.merge({
            coverage_threshold: {
                statements: <THRESHOLD>,
                branches: <THRESHOLD>,
                functions: <THRESHOLD>,
                lines: <THRESHOLD>
            }
        });
    };
    ```

    For `<THRESHOLD>`, enter the percentage of your code that you want to cover with tests.

    > ### Note:  
    > If the defined threshold isn’t met, the build breaks.


<a name="loio52bc22233ef84527bc409fbe748947b8"/>

<!-- loio52bc22233ef84527bc409fbe748947b8 -->

## \(Optional\) Configure the Deploy Credential

If you want your pipleline to execute the **Deploy** task, create an OAuth credential for the subaccount to which you want to deploy your application.



<a name="loio52bc22233ef84527bc409fbe748947b8__prereq_ltt_3qk_ylb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You’ve enabled the Solutions Lifecycle Management service.




<a name="loio52bc22233ef84527bc409fbe748947b8__steps_txg_rxn_blc"/>

## Procedure

1.  In the SAP BTP cockpit, navigate to the subaccount in the Neo environment to which you want to deploy your application.

2.  In the navigation area, choose :shield: *Security* \> *OAuth*.

3.  In the *Platform API* tab, choose *Create API Client*.

4.  In the *Description* text field, enter a name for your API client.

5.  Select *Solutions Lifecycle Management*.

6.  Choose *Save*.

7.  Remember the *Client ID* and *Client Secret*.

    > ### Caution:  
    > Both *Client ID* and *Client Secret* are only displayed once. You can't retrieve them later.

8.  Use this *Client ID* and *Client Secret* to create a new OAuth credential in SAP Continuous Integration and Delivery. See [Creating Credentials](creating-credentials-6658c81.md).


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


