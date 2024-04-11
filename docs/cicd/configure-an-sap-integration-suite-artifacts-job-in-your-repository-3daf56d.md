<!-- loio3daf56d952c74c10b0be810d082e68ab -->

# Configure an SAP Integration Suite Artifacts Job in Your Repository

Configure the stages of your SAP Integration Suite Artifacts job in your source management system.



<a name="loio3daf56d952c74c10b0be810d082e68ab__prereq_jsb_3gc_clb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You've provisioned the Cloud Integration capability as part of SAP Integration Suite. See [Initial Setup of SAP Cloud Integration in Cloud Foundry Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/302b47b11e1749c3aa9478f4123fc216.html).
-   You've created the *Process Integration Runtime* service instance of plan *api* and a service key to authenticate your pipeline against SAP Cloud Integration. For more information, see [Setting Up OAuth Inbound Authentication with Client Credentials Grant for API Clients, Cloud Foundry Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/20e26a837a8449c4b8b934b07f71cb76.html).
-   You have write permission for the repository in which your project sources reside.

-   You’ve transferred your integration artifacts from SAP Cloud Integration to a repository of your source code management system.

    Procedure:

    1.  In SAP Integration Suite, open your integration package and choose *Artifacts*.

    2.  Choose *Actions*→ *Download*.

    3.  Save the \*.zip file to your choice of destination.

    4.  Extract the file and upload its content into your repository.

        > ### Note:  
        > Repeat the procedure in case you make changes in your integration flow in SAP Cloud Integration.


-   In the repository of your project, you have a folder named `.pipeline`, which contains a file named `config.yml`. If you don't have this folder and file, yet, create them. In the `config.yml` file, add the following initial configuration:

    ```
    # Project configuration
    general:
    
    # Stage configuration
    stages:
    
    # Step configuration
    steps:
    ```




<a name="loio3daf56d952c74c10b0be810d082e68ab__context_okr_p5d_fqb"/>

## Context

Depending on your configuration, the SAP Integration Suite Artifacts pipeline can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/CPI_Pipeline_Stages_fd23518.png)



## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in  <?sap-ot O2O class="- topic/xref " href="d748920175554221be1ba8b461ada030.xml" text="" desc="" xtrc="xref:9" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/3daf56d952c74c10b0be810d082e68ab.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . As *Pipeline*, choose *SAP Integration Suite Artifacts*.

2.  In the *Stages* tab, choose *Source Repository* from the *Configuration Mode* dropdown list.

3.  Choose *Create*.

4.  In your `.pipeline/config.yml` file, configure the general parameters of your job as follows:

    > ### Note:  
    > If you have already created your job in the job editor, you can export the editor-based configuration information to a YAML file by pressing the YML button. In this case you can skip the following steps and paste the configuration content directly in your `config.yml` file. For more information, see [Export Job Configuration Data](export-job-configuration-data-60a76d7.md).

    **General Parameters**

    > ### Sample Code:  
    > ```
    > # Project configuration
    > general:
    >   cpiApiServiceKeyCredentialsId: "<cpi-api>" 
    >   integrationFlowId: "<MyFirstIntegrationFlow>"
    > 
    > ```

    **Details of the General Parameters Configuration**


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
    
    `cpiApiServiceKeyCredentialsId` 
    
    </td>
    <td valign="top">
    
    To authenticate your pipeline against an integration flow endpoint, use the service key from the *Process Integration Runtime* service instance of plan *api*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `integrationFlowId` 
    
    </td>
    <td valign="top">
    
    Enter the ID of your integration flow. You can find it in the overview of your integration package under *Artifacts*.
    
    </td>
    </tr>
    </table>
    
5.  Configure the **stages** of your job as follows:

    **Upload, Deploy and Integration Test Stages**

    > ### Sample Code:  
    > ```
    > # Stages configuration
    > stages: 
    >   uploadStage: 
    >     enable: true #(default: false) 
    >   deployStage: 
    >     enable: true #(default: false) 
    >   integrationTestStage: 
    >     enable: true #(default: false)
    > 
    > ```

    **Details of the Upload, Deploy and Integration Test Stage**


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
    
    `uploadStage` 
    
    </td>
    <td valign="top">
    
    The *Upload* stage imports your integration flow content from your source management system to your SAP Cloud Integration application.

    Enable or disable the Upload stage by choosing either`enable: true`  or`enable: false`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployStage` 
    
    </td>
    <td valign="top">
    
    The *Deploy* stage triggers the deployment of the integration flow.

    Enable or disable the Deploy stage by choosing either`enable: true`  or`enable: false`.

    > ### Note:  
    > If you don't want to use the latest version at runtime, you can skip that part. Be aware that enabling the integration test stage would test the old features.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `integrationTestStage` 
    
    </td>
    <td valign="top">
    
    The *Integration Test* stage enables you to test your integration flow.

    Enable or disable the Integration Test  stage by choosing either`enable: true` or`enable: false`.

    > ### Tip:  
    > You can use this step to send a message to invoke the integration flow. If your integration flow is invoked automatically by a scheduler start event or a polling sender adapter, you can skip this part.


    
    </td>
    </tr>
    </table>
    
6.  Configure the **steps** of your configuration as follows:

    > ### Sample Code:  
    > ```
    > # Steps configuration
    > steps: 
    >   integrationArtifactUpload: 
    >     packageId:  "<cpipackage>"  
    >     integrationFlowName: "<flow1>" 
    >   integrationArtifactTriggerIntegrationTest: 
    >     contentType:  "<application/x-www-form-urlencoded>"     # optional, has to be specified when a messageBodyPath is defined
    >     messageBodyPath:  "<integrationsTest/messageBody>"      # optional
    >     iFlowServiceKeyCredentialsId: <cpikey-inflow>
    > 
    > ```

    **Details of the Step Configuration**


    <table>
    <tr>
    <th valign="top">

    Step
    
    </th>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="2">
    
    `integrationArtifactUpload` 
    
    </td>
    <td valign="top">
    
    `packageId` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter your integration package ID. You can find it in SAP Integration Suite, navigate to your workspace \(*Design* tab page\) and choose *Packages* -\> *Overview*.

    > ### Note:  
    > You can skip this part if the integration flow is already existing on the tenant.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `integrationFlowName` 
    
    </td>
    <td valign="top">
    
    Enter the name of your integration flow. You can find it in the overview of your integration package under *Artifacts*.
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="3">
    
    `integrationArtifactTriggerIntegrationTest` 
    
    </td>
    <td valign="top">
    
    `contentType` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Define the content type of the message body file. Enter a custom file type or choose between:

    -   `application/xml` 
    -   `application/json`
    -   `text/plain`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `messageBodyPath` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Specify the relative file path of your message body file, for example, `integrationsTest/messageBody`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `iFlowServiceKeyCredentialsId` 
    
    </td>
    <td valign="top">
    
    To implement inbound communication with SAP Cloud Integration, create the *Process Integration Runtime* service instance of plan *integration-flow* and a service key. For more information, see [Creating a Service Instance for OAuth Client Credentials Grant](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/caad7a1c68c348888d9d5f5a24c13b6b.html?q=Creating%20a%20Service%20Instance%20for%20OAuth%20Client%20Credentials%20Grant.) and [Creating a Service Key for the Instance](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/dcc4bfd8ba0740c7907a1bd43ed96a69.html).
    
    </td>
    </tr>
    </table>
    
7.  Commit and push your configuration.




<a name="loio3daf56d952c74c10b0be810d082e68ab__result_vgz_szy_cpb"/>

## Results

Depending on your configuration, your complete `config.yml` file should look as follows:

> ### Sample Code:  
> ```
> # Project configuration
> general:
>   cpiApiServiceKeyCredentialsId: "<cpi-api>" 
>   integrationFlowId: "<MyFirstIntegrationFlow>"
> 
> # Stage configuration
> stages:
>   uploadStage: 
>     enabled: true #(default: false) 
>   deployStage: 
>     enabled: true #(default: false) 
>   integrationTestStage: 
>     enabled: true #(default: false) 
> 
> 
> # Steps configuration
> steps: 
>   integrationArtifactUpload: 
>     packageId:  "<cpipackage>"   
>     integrationFlowName: "<flow1>"  
>   integrationArtifactTriggerIntegrationTest: 
>     contentType: "<application/x-www-form-urlencoded>"     # optional, has to be specified when a messageBodyPath is defined
>     messageBodyPath: "<integrationsTest/messageBody>"      # optional 
>     iFlowServiceKeyCredentialsId: "<myIFlowServiceKey>"
> 
> ```

