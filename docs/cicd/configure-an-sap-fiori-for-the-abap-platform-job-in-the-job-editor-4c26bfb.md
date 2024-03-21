<!-- loio4c26bfbeb6444805a933ca48a470b217 -->

# Configure an SAP Fiori for the ABAP Platform Job in the Job Editor

Configure the stages of your SAP Fiori for the ABAP platform job directly in the SAP Continuous Integration and Delivery service.



<a name="loio4c26bfbeb6444805a933ca48a470b217__prereq_dvs_hg3_xlb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAPUI5/SAP Fiori project for the ABAP platform. See [Create an SAP Fiori Project](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/46664de4d6944471b6c29a0681bfd0fc.html).

-   You have configured the SAP Cloud Connector to ensure secure communication between SAP Continuous Integration and Delivery and the ABAP system.

-   You have installed the SAP component SAP\_UI 7.53 or higher on your ABAP system. See [Software Component SAP\_UI](https://help.sap.com/docs/ABAP_PLATFORM_NEW/6f3c61a7a5b94447b80e72f722b0aad7/35828457ed26452db8d51c840813f1bb.html?version=202009.002).

-   You have enabled the OData service to load data to the SAPUI5 ABAP repository. See [Using an OData Service to Load Data to the SAPUI5 ABAP Repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).

-   You have the S\_DEVELOP authorization to perform operations in your SAPUI5 ABAP repository. See [Using an OData Service to Load Data to the SAPUI5 ABAP Repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).




<a name="loio4c26bfbeb6444805a933ca48a470b217__context_cpj_32y_q4b"/>

## Context

Depending on your configuration, the SAP Fiori for the ABAP platform pipeline can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/ABAP_Platform_Stages_216f127.png)

> ### Note:  
> Upon the completion of your pipeline’s run, an additional *Declarative: Post Actions* stage is executed to perform finalization tasks. The outcome of the *Declarative: Post Actions* stage does not influence the success of your build.



<a name="loio4c26bfbeb6444805a933ca48a470b217__steps_yz5_sh3_xlb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in [Create a Job](create-a-job-d748920.md). As *Pipeline*, choose *SAP Fiori for ABAP platform*.

2.  In the *Stages* tab, choose *Job Editor* from the *Configuration Mode* dropdown list.

    > ### Note:  
    > After you have configured your job, you can export the editor-based configuration information to a YAML file by pressing the YML button. Press *Edit* and switch to *Source Repository* to move from editor-based configuration to the more advanced configuration in the source repository when necessary. For more information, see [\(Optional\) Export Job Configuration Data](https://help.sap.com/viewer/99c72101f7ee40d0b2deb4df72ba1ad3/Cloud/en-US/60a76d7b5a2a46f684515b18e9cbbc08.html).

3.  In the *Stages* tab, perform the following actions:

    1.  Configure the *Build* stage.

        **Actions for Configuring the Build Stage**


        <table>
        <tr>
        <th valign="top">

        Step
        
        </th>
        <th valign="top">

        Parameter
        
        </th>
        <th valign="top">

        Action
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="2">
        
         
        
        </td>
        <td valign="top">
        
        State
        
        </td>
        <td valign="top">
        
        Either switch the execution of the *Build* stage on or off.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Build Tool Version
        
        </td>
        <td valign="top">
        
        Choose the build tool version you want to use. For more information, see [Supported Tools](supported-tools-5949283.md).

        If you don't define a build tool version, the latest one is used by default.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Lint Check
        
        </td>
        <td valign="top">
        
        State
        
        </td>
        <td valign="top">
        
        Either switch the execution of the *Lint Check* step on or off.

        The lint check verifies the syntax of your JavaScript code.

        If you want your build to fail if the *Lint Check* reveals any errors, check the *Fail on Error* checkbox.
        
        </td>
        </tr>
        </table>
        
    2.  Configure the *Additional Unit Tests* stage.

        **Actions for Configuring the Additional Unit Tests**


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
        
        State
        
        </td>
        <td valign="top">
        
        Either switch the execution of the *Additional Unit Tests* stage on or off. If you switch it on, make sure that you have a `package.json` file on the root level, which points to the test sources that should be executed.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        npm Script
        
        </td>
        <td valign="top">
        
        \(Optional\) If in your `package.json` file, you have a `scripts` section, specify the name of the test script to be executed.
        
        </td>
        </tr>
        </table>
        
    3.  Configure the *Malware Scan* stage.

        **Actions for Configuring the Malware Scan Stage**


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
        
        State
        
        </td>
        <td valign="top">
        
        Either switch the execution of the *Malware Scan* stage on or off.
        
        </td>
        </tr>
        </table>
        
    4.  Configure the *Compliance* stage.

        **Actions for Configuring the Compliance Stage**


        <table>
        <tr>
        <th valign="top">

        Step
        
        </th>
        <th valign="top">

        Parameter
        
        </th>
        <th valign="top">

        Action
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="7">
        
        SonarQube Scan
        
        </td>
        <td valign="top">
        
        State
        
        </td>
        <td valign="top">
        
        Either switch the execution of the *SonarQube Scan* step on or off.

        This step enables you to integrate code quality and security analysis into your pipeline. If you choose to enable the *SonarQube Scan* step, make sure you have a running SonarQube server instance. See [SonarQube](https://www.sonarqube.org/). You can also use the public offering - SonarCloud.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Mode
        
        </td>
        <td valign="top">
        
        Select the mode in which you want to analyze your application. The following options are displayed in a dropdown list:

        -   `SonarCloud`
        -   `SonarQube` 


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Cloud Connector
        
        </td>
        <td valign="top">
        
        \(Optional\) If you chose the SonarQube mode, you can additionally connect to on-premise systems using Cloud Connector. See [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

        From the dropdown list, either choose credentials that you've already defined in [Creating Credentials](creating-credentials-6658c81.md) or create new ones by choosing *Create Credentials*.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        URL
        
        </td>
        <td valign="top">
        
        Enter the full URL to your backend system:

        -   For the `SonarCloud` mode, choose the URL from the dropdown list

        -   For the `SonarQube` mode, enter the custom URL to your internet-facing SonarQube server


        Before configuring the next parameters, make sure that you have created a project in your SonarQube instance. For more information, see the [SonarQube documentation](https://docs.sonarqube.org/latest/setup/get-started-2-minutes/).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Organization
        
        </td>
        <td valign="top">
        
        Enter the organization that you provided for your project.

        > ### Note:  
        > This step is only mantadory for the `SonarCloud` mode.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Project Key
        
        </td>
        <td valign="top">
        
        Enter the project key that you provided for your project.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        SonarQube Token Credentials
        
        </td>
        <td valign="top">
        
        To authenticate your pipeline against your SonarQube instance, create a *Secret Text* credential of a user, who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

        In the *Secret* text field, paste the token that was generated when creating your SonarQube project. If you are unable to retrieve your token, generate a new one. See [Generating and Using Tokens](https://docs.sonarqube.org/latest/user-guide/user-token/).

        Choose this credential from the dropdown list.
        
        </td>
        </tr>
        </table>
        
    5.  Configure the *Release* stage.

        **Actions for Configuring the Release Stage**


        <table>
        <tr>
        <th valign="top">

        Step
        
        </th>
        <th valign="top">

        Parameter
        
        </th>
        <th valign="top">

        Action
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="9">
        
        Upload to ABAP
        
        </td>
        <td valign="top">
        
        State
        
        </td>
        <td valign="top">
        
        Either switch the execution of the *Upload to ABAP* step on or off.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Upload Credentials
        
        </td>
        <td valign="top">
        
        To authenticate your pipeline against your ABAP system, create a Basic Authentication credential of a user, who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

        > ### Tip:  
        > Use a technical user instead of your personal credentials.

        Choose this credential from the dropdown list.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Cloud Connector
        
        </td>
        <td valign="top">
        
        Choose the Cloud Connector you configured for your ABAP system before.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        ABAP Platform Endpoint
        
        </td>
        <td valign="top">
        
        Enter the URL of your ABAP server using the HTTP protocol `(http://<host:port>)`.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        ABAP Package
        
        </td>
        <td valign="top">
        
        Enter the name of the ABAP package you want to upload your application to.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Application Name
        
        </td>
        <td valign="top">
        
        Enter a name for your application.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Application Description
        
        </td>
        <td valign="top">
        
        Enter a meaningful description for your application.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Configuration Mode of Transport Request ID
        
        </td>
        <td valign="top">
        
        Choose one of the following options to configure the transport request ID:

        -   *Job Editor:* Enter the transport request ID in the text field that appears if you choose this option.

        -   *File in Source Repository:* Enter the transport request ID in a file called `.pipeline/transportRequestID` in your source repository. You might need to create this file first.

        -   *Git Commit Message:* Enter the label `Transport Request:` and the transport request ID in the body of a Git HEAD commit message, for example: `TransportRequest: AH7K900034`.



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Transport Request ID
        
        </td>
        <td valign="top">
        
        Enter the transport request ID of an open CTS+ transport in your ABAP system.
        
        </td>
        </tr>
        </table>
        

    > ### Note:  
    > You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see [Advanced Pipeline Configuration](advanced-pipeline-configuration-c8314b6.md).

4.  Choose *Create*.


<a name="loio642bcb08b27c4d7ab5008aa277225189"/>

<!-- loio642bcb08b27c4d7ab5008aa277225189 -->

## \(Optional\) Configure the Additional Unit Test Stage

Before running the **Additional Unit Tests** stage in your job, add the test configuration to your project.



<a name="loio642bcb08b27c4d7ab5008aa277225189__prereq_fgb_ctn_blb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery.

-   In your repository, you have an SAPUI5/SAP Fiori project. See [Create an SAP Fiori Project](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/46664de4d6944471b6c29a0681bfd0fc.html).




<a name="loio642bcb08b27c4d7ab5008aa277225189__steps_kmn_qtn_blb"/>

## Procedure

1.  Make sure that the following dependencies and scripts are part of your `package.json` file:

    ```
    {
        (...)
        "devDependencies": {
            (...)
            "karma": "^5.0.4",
            "karma-chrome-launcher": "^3.1.0",
            "karma-coverage": "^2.0.2",
            "karma-ui5": "^2.1.0"
        },
        "scripts": {
            (...)
            "test": "karma start",
        }
    }
    ```

2.  To describe that the tests should use a custom web driver launcher to connect to a remote Chrome browser, add a file named `karma.conf.js` to the same folder as your `package.json` file.

3.  Add the following minimal configuration to your `karma.conf.js` file:

    ```
     ```
     module.exports = function(config) {
         config.set({
            frameworks: ["ui5"],
            ui5: {
               url: "https://ui5.sap.com"
            },
            browsers: ["ChromeHeadless"],
            browserConsoleLogOptions: {
               level: "error"
            },
            singleRun: true
         });
     };
     ```
    
    ```

4.  To report the coverage and see the coverage data in the logs, add the following additional configuration to the file:

    ```
    ```
    module.exports = function(config) {
      config.set({
    
        frameworks: ["ui5"],
        ui5: {
          url: "https://ui5.sap.com"
        },
        preprocessors: {
    			"{webapp,webapp/!(test)}/!(mock*).js": ["coverage"]
    		},
        coverageReporter: {
                includeAllSources: true,
                reporters: [
                    {
                        type: "html",
                        dir: "coverage"
                    },
                    {
                        type: "text"
                    }
                ],
        check: {
           each: {
                   statements: <THRESHOLD>,
                   branches: <THRESHOLD>,
                   functions: <THRESHOLD>,
                   lines: <THRESHOLD>
                    }
                }
            },
         reporters: ["progress", "coverage"],
    
        browsers: ["ChromeHeadless"],
        browserConsoleLogOptions: {
             level: "error"
        },
        singleRun: true
      });
    };
    ```					
    ```

    For `<THRESHOLD>`, enter the percentage of your code that you want to cover with tests. If the defined threshold isn’t met, the build breaks.


