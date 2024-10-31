<!-- loio619a864813584bd1a433cafac1fb0c1e -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure an SAP Fiori in the Neo Environment Job

Configure the stages of your SAP Fiori in the Neo environment job directly in the SAP Continuous Integration and Delivery service.



<a name="loio619a864813584bd1a433cafac1fb0c1e__prereq_dvs_hg3_xlb"/>

## Prerequisites

> ### Caution:  
> This pipeline has been deprecated and is no longer available for new jobs. Existing jobs will continue to work until December 31st, 2024.

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAPUI5/SAP Fiori project for the Neo environment.




<a name="loio619a864813584bd1a433cafac1fb0c1e__context_plr_4hy_q4b"/>

## Context

Depending on your configuration, the SAP Fiori in the Neo environment pipeline can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/UI5_Pipeline_Steps_ad534be.png)

> ### Note:  
> Upon the completion of your pipeline’s run, an additional *Declarative: Post Actions* stage is executed to perform finalization tasks. The outcome of the *Declarative: Post Actions* stage does not influence the success of your build.



<a name="loio619a864813584bd1a433cafac1fb0c1e__steps_yz5_sh3_xlb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in  <?sap-ot O2O class="- topic/xref " href="d748920175554221be1ba8b461ada030.xml" text="" desc="" xtrc="xref:9" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/619a864813584bd1a433cafac1fb0c1e.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . As *Pipeline*, choose *SAP Fiori in the Neo Environment*.

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

        **Actions for Configuring Additional Unit Tests**


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
        
        **Actions for Configuring the Deploy to Neo Acceptance Subaccount Step**


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
        
        Host
        
        </td>
        <td valign="top">
        
        Enter the host of your SAP BTP subaccount. See [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Subaccount ID
        
        </td>
        <td valign="top">
        
        Enter the ID of your SAP BTP subaccount.

        It’s displayed as *Technical Name* in the overview of your subaccount in the SAP BTP cockpit.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Credentials
        
        </td>
        <td valign="top">
        
        Choose *Create Credentials* and create an OAuth credential for the subaccount to in which you want to test your application. See [Configure the Deploy Credential](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio52bc22233ef84527bc409fbe748947b8).

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
        
        Enter the path to the configuration file in your repository, for example:`.app/webapp/test/univeri5/conf.js` 
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Base URL
        
        </td>
        <td valign="top">
        
        Enter the URL of the application against which the UiVeri5 tests should be executed. See [Configuring Application URLs](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/7ceeaa5e528140c48ae53b68433293ba.html).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Application Credentials
        
        </td>
        <td valign="top">
        
        \(Optional\) To authenticate your pipeline against the application, create a Basic Authentication credential of a user, who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

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
        > If you don't know the URL, you can deploy your application first. You will find the generated URL by navigating to *Subaccount*** \> ***Applications*** \> ***HTML5 Applications*** \> **Overview page of the application** \> ***Application URL*.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Credentials
        
        </td>
        <td valign="top">
        
        \(Optional\) To authenticate your pipeline against the application, create a *Basic Authentication* credential of a user, who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

        > ### Tip:  
        > Avoid using a technical user credential and create a special test user instead.

        You can access the username and password in your individual test files by using:

        ```
        
            const usernameVar=process.env.e2e_username
            const passwordVar=process.env.e2e_password
        
        ```

        Choose this credential from the dropdown list.
        
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
        
        To authenticate your pipeline against your SonarQube instance, create a *Secret Text* credential of a user, who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

        In the *Secret* text field, paste the token that was generated when creating your SonarQube project. If you are unable to retrieve your token, generate a new one. See [Generating and Using Tokens](https://docs.sonarqube.org/latest/user-guide/user-token/).

        Choose this credential from the dropdown list.
        
        </td>
        </tr>
        </table>
        
    6.  Configure the *Release* stage.

        **Actions for Configuring the Deploy to Neo Subaccount Step**


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
        
        Either switch the execution of the *Deploy to Neo Subaccount* step on or off.

        > ### Note:  
        > If the *Deploy to Neo Subaccount* step is switched off, all corresponding entry fields are deactivated.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Host
        
        </td>
        <td valign="top">
        
        Enter the host of your SAP BTP subaccount. See [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Subaccount ID
        
        </td>
        <td valign="top">
        
        Enter the ID of your SAP BTP subaccount.

        It’s displayed as *Technical Name* in the overview of your subaccount in the SAP BTP cockpit.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Credentials
        
        </td>
        <td valign="top">
        
        Choose *Create Credentials* and create an OAuth credential for the subaccount to which you want to deploy your application. See [Configure the Deploy Credential](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio52bc22233ef84527bc409fbe748947b8).

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
    > You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see  <?sap-ot O2O class="- topic/xref " href="c8314b6c8e564f42925e9d10453bd541.xml" text="" desc="" xtrc="xref:29" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/619a864813584bd1a433cafac1fb0c1e.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

4.  Choose *Create*.


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


