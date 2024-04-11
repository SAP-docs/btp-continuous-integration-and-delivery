<!-- loio201ef608e14c4ca483b2184b42e17e7f -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure an SAP Fiori in the Cloud Foundry Environment Job

Configure the stages of your SAP Fiori in the Cloud Foundry environment job directly in the SAP Continuous Integration and Delivery service.



<a name="loio201ef608e14c4ca483b2184b42e17e7f__prereq_dvs_hg3_xlb"/>

## Prerequisites

> ### Caution:  
> This pipeline type is deprecated. Please use the  <?sap-ot O2O class="- topic/xref " href="7c2a049670f64993b9d67c8f84ba0969.xml" text="" desc="" xtrc="xref:1" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/201ef608e14c4ca483b2184b42e17e7f.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?>  pipeline with the mta build tool, instead. All existing jobs will be migrated automatically.

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAPUI5/SAP Fiori project for the Cloud Foundry environment. See [Create an SAP Fiori Project](https://help.sap.com/viewer/9d1db9835307451daa8c930fbd9ab264/Cloud/en-US/46664de4d6944471b6c29a0681bfd0fc.html).


> ### Note:  
> The SAP Fiori in the Cloud Foundry environment pipeline also supports HTML5 applications that don't need an own runtime infrastructure. For more information, see [Developing HTML5 Applications](https://help.sap.com/viewer/d1c8cd7a39bc4f24a0c65e2ae64d627c/1.0/en-US/00b074c1284e4520a75df52e25698522.html).



<a name="loio201ef608e14c4ca483b2184b42e17e7f__context_cpj_32y_q4b"/>

## Context

Depending on your configuration, the SAP Fiori in the Cloud Foundry environment pipeline can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/UI5_Pipeline_Steps_ad534be.png)

> ### Note:  
> Upon the completion of your pipeline’s run, an additional *Declarative: Post Actions* stage is executed to perform finalization tasks. The outcome of the *Declarative: Post Actions* stage does not influence the success of your build.



<a name="loio201ef608e14c4ca483b2184b42e17e7f__steps_yz5_sh3_xlb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in  <?sap-ot O2O class="- topic/xref " href="d748920175554221be1ba8b461ada030.xml" text="" desc="" xtrc="xref:12" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/201ef608e14c4ca483b2184b42e17e7f.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . As *Pipeline*, choose *SAP Fiori in the Cloud Foundry environment*.

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
        <td valign="top" rowspan="3">
        
         
        
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
        
        Application Name
        
        </td>
        <td valign="top">
        
        Optionally, enter a name for your application.

        > ### Note:  
        > The build prefers the application name from your MTA descriptor file over the one entered in the user interface. If you don't define an application name \(neither in the `mta.yaml` file nor in the user interface\), a default one \(`ui5application`\) is used.


        
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

        **Actions for Configuring the Additional Unit Tests Stage**


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

        **Actions for Configuring the Malware Scan Step**


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
        
    4.  Configure the *Acceptance* stage.

        **General Actions for the Acceptance Stage**


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
        
        Either switch the execution of the *Acceptance* stage on or off.
        
        </td>
        </tr>
        </table>
        
        **Actions for Configuring the Deploy to Cloud Foundry Acceptance Space Step**


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
        
        API Endpoint
        
        </td>
        <td valign="top">
        
        Enter the URL of your SAP BTP, Cloud Foundry API Endpoint. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/viewer/3504ec5ef16548778610c7e89cc0eac3/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loiof344a57233d34199b2123b9620d0bb41).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Org Name
        
        </td>
        <td valign="top">
        
        Enter the name of your Cloud Foundry organization. You can find it in the overview of your subaccount in the SAP BTP cockpit.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Space
        
        </td>
        <td valign="top">
        
        Enter the name of the Cloud Foundry space in which you want to test your application.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Deploy Type
        
        </td>
        <td valign="top">
        
        From the dropdown list, choose the deployment type \(`standard` or `blue-green`\) you want to use.

        The default deployment type is `standard`. By using the `blue-green` deployment, you can deploy your application without downtime and with reduced risk.

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
        
        Credentials
        
        </td>
        <td valign="top">
        
        To authenticate your pipeline against the Cloud Foundry API endpoint, either create a Basic Authentication or a Basic Authentication for Custom IdP credential of a user who has the appropriate permissions. The user must have the Space Developer role and be a member of the specified Cloud Foundry organization and space. See [Creating Credentials](creating-credentials-6658c81.md).

        > ### Tip:  
        > Use a technical user instead of your personal credentials.

        Choose this credential from the dropdown list.
        
        </td>
        </tr>
        </table>
        
        **Actions for Configuring the UIVeri5 Test \(Deprecated\) Step**


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
        
        > ### Note:  
        > **Please note that this step is deprecated and will be removed or replaced soon.** Even though existing tests will continue to work, we recommend that you remove the deprecated configurations. For more details, see [GitHub](https://github.com/SAP/ui5-uiveri5#readme).

        Either switch the execution of the UIVeri5 test on or off.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Configuration Path
        
        </td>
        <td valign="top">
        
        Enter the path to the configuration file in your repository, for example: `.app/webapp/test/univeri5/conf.js` 
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Base URL
        
        </td>
        <td valign="top">
        
        Enter the URL of the application against which the UiVeri5 tests should be executed. See [Configuring Application URLs](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e623e372e6174f81af2b9b8ef8f6d6d3.html).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Application Credentials
        
        </td>
        <td valign="top">
        
        \(Optional\) To authenticate your pipeline against the application, create a Basic Authentication credential of a user who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

        > ### Tip:  
        > Avoid using a technical user credential and create a special test user instead.

        Choose this credential from the dropdown list.

        > ### Note:  
        > If you chose to use application credentials, add the following code block to your `conf.js` file in your repository:
        > 
        > ```
        > //Read environment variables
        > const defaultParams = {
        >     user: process.env.TEST_USER,
        >     pass: process.env.TEST_PASS
        > };
        > ```


        
        </td>
        </tr>
        </table>
        
        **Actions for Configuring the WebdriverIO Test Step**


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
        
        > ### Note:  
        > The *WebdriverIO Test* step is available for build tool versions Node 16 and above. The WebdriverIO testing framework is no longer compatible with older Node.js versions.

        Either switch the execution of the *WebdriverIO Test* step on or off.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        npm Script
        
        </td>
        <td valign="top">
        
        Enter the name of the test script to be executed. You can find it in the `scripts` section of your `package.json` file. If you don't define a name, a default one \("`wdi5`"\) is used.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Base URL
        
        </td>
        <td valign="top">
        
        Enter the URL of the application against which the tests should be executed. See [Configuring Application URLs](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/e623e372e6174f81af2b9b8ef8f6d6d3.html).

        > ### Tip:  
        > If you don't know the URL, you can deploy your application first. You will find the generated URL by navigating to *Subaccount*** \> ***Cloud Foundry Space*** \> **Overview page of the application** \> ***Application Routes*.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Credentials
        
        </td>
        <td valign="top">
        
        \(Optional\) To authenticate your pipeline against the application, create a *Basic Authentication* credential of a user who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

        > ### Tip:  
        > Avoid using a technical user credential and create a special test user instead.

        You can access the username and password in your individual test files by using:

        ```
        
            const usernameVar=process.env.e2e_username
            const passwordVar=process.env.e2e_password
        
        ```


        
        </td>
        </tr>
        </table>
        
    5.  Configure the *Compliance* stage.

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
        
        To authenticate your pipeline against your SonarQube instance, create a *Secret Text* credential of a user who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

        In the *Secret* text field, paste the token that was generated when creating your SonarQube project. If you are unable to retrieve your token, generate a new one. See [Generating and Using Tokens](https://docs.sonarqube.org/latest/user-guide/user-token/).

        Choose this credential from the dropdown list.
        
        </td>
        </tr>
        </table>
        
    6.  Configure the *Release* stage.

        **Actions for Configuring the Deploy to Cloud Foundry Space Step**


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
        
        Either switch the execution of the *Deploy to Cloud Foundry Space* step on or off.

        > ### Note:  
        > If the *Deploy to Cloud Foundry Space* step is switched off, all corresponding entry fields are deactivated.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        API Endpoint
        
        </td>
        <td valign="top">
        
        Enter the URL of your SAP BTP, Cloud Foundry API Endpoint. See [Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/viewer/3504ec5ef16548778610c7e89cc0eac3/Cloud/en-US/350356d1dc314d3199dca15bd2ab9b0e.html#loiof344a57233d34199b2123b9620d0bb41).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Org Name
        
        </td>
        <td valign="top">
        
        Enter the name of your Cloud Foundry organization. You can find it in the overview of your subaccount in the SAP BTP cockpit.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Space
        
        </td>
        <td valign="top">
        
        Enter the name of the Cloud Foundry space to which you want to deploy your application.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Deploy Type
        
        </td>
        <td valign="top">
        
        From the dropdown list, choose the deployment type \(`standard` or `blue-green`\) you want to use.

        The default deployment type is `standard`. By using the `blue-green` deployment, you can deploy your application without downtime and with reduced risk.

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
        
        Credentials
        
        </td>
        <td valign="top">
        
        To authenticate your pipeline against the Cloud Foundry API endpoint, either create a Basic Authentication or a Basic Authentication for Custom IdP credential of a user who has the appropriate permissions. The user must have the Space Developer role and be a member of the specified Cloud Foundry organization and space. See [Creating Credentials](creating-credentials-6658c81.md).

        > ### Tip:  
        > Use a technical user instead of your personal credentials.

        Choose this credential from the dropdown list.
        
        </td>
        </tr>
        </table>
        
        **Actions for Configuring the Upload to Cloud Transport Management Step**


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
        
        Either switch the *Upload to Cloud Transport Management* stage on or off.

        > ### Note:  
        > If the *Upload to Cloud Transport Management* stage is switched off, all corresponding entry fields are deactivated.

        For more information on why and how to integrate SAP Cloud Transport Management into your continuous delivery process, see [\(Optional\) Integrate SAP Cloud Transport Management into Your Pipeline](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio0b9c5d30aff3425c96a440dce60bd9c7).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Node Name
        
        </td>
        <td valign="top">
        
        Enter the name of the node for the upload to SAP Cloud Transport Management.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Service Key
        
        </td>
        <td valign="top">
        
        To authenticate your pipeline against SAP Cloud Transport Management, create a Service Key. See [Creating Credentials](creating-credentials-6658c81.md).

        Choose this credential from the dropdown list.
        
        </td>
        </tr>
        </table>
        

    > ### Note:  
    > You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see  <?sap-ot O2O class="- topic/xref " href="c8314b6c8e564f42925e9d10453bd541.xml" text="" desc="" xtrc="xref:34" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/201ef608e14c4ca483b2184b42e17e7f.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

4.  Choose *Create*.


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


