<!-- loio3d5573fab2ea432cb2cab8639395e51e -->

# Configure an SAP Integration Suite Artifacts Job

Configure the stages of your SAP Integration Suite Artifacts job directly in the SAP Continuous Integration and Delivery service.



<a name="loio3d5573fab2ea432cb2cab8639395e51e__prereq_lkr_p5d_fqb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You've provisioned the Cloud Integration capability as part of SAP Integration Suite. See [Initial Setup of SAP Cloud Integration in the Cloud Foundry Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/302b47b11e1749c3aa9478f4123fc216.html).
-   You've created the *Process Integration Runtime* service instance of plan *api* and a service key to authenticate your pipeline against SAP Cloud Integration. See [Setting Up OAuth Inbound Authentication with Client Credentials Grant for API Clients, Cloud Foundry Environment](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/20e26a837a8449c4b8b934b07f71cb76.html).
-   You’ve transferred your integration artifacts from SAP Cloud Integration to a repository of your source code management system.

    Procedure:

    1.  In SAP Cloud Integration, open your integration package and choose *Artifacts*.

    2.  Choose *Actions*→ *Download*.

    3.  Save the \*.zip file to your choice of destination.

    4.  Extract the file and upload its contents into your repository.

        > ### Note:  
        > Repeat the procedure in case you make changes in your integration flow in SAP Cloud Integration.





<a name="loio3d5573fab2ea432cb2cab8639395e51e__context_okr_p5d_fqb"/>

## Context

Depending on your configuration, the SAP Integration Suite Artifacts pipeline can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/CPI_Pipeline_Stages_fd23518.png)

> ### Note:  
> Upon the completion of your pipeline’s run, an additional *Declarative: Post Actions* stage is executed to perform finalization tasks. The outcome of the *Declarative: Post Actions* stage does not influence the success of your build.



<a name="loio3d5573fab2ea432cb2cab8639395e51e__steps_pkr_p5d_fqb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in [Create a Job](https://help.sap.com/viewer/SAP-Cloud-Platform-Continuous-Integration-and-Delivery/d748920175554221be1ba8b461ada030.html). As *Pipeline*, choose *SAP Integration Suite Artifacts*.

2.  In the *Stages* tab, choose *Job Editor* from the *Configuration Mode* dropdown list.

    > ### Note:  
    > After you have configured your job, you can export the editor-based configuration information to a YAML file by pressing the YML button. Press *Edit* and switch to *Source Repository* to move from editor-based configuration to the more advanced configuration in the source repository when necessary. For more information, see [\(Optional\) Export Job Configuration Data](https://help.sap.com/viewer/99c72101f7ee40d0b2deb4df72ba1ad3/Cloud/en-US/60a76d7b5a2a46f684515b18e9cbbc08.html).

3.  In the *Stages* tab, specify the following general parameters:

    **Configuring the General Parameters of an  SAP Integration Suite Artifacts Pipeline with the Job Editor**


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
    
    Flow ID
    
    </td>
    <td valign="top">
    
    Enter the ID of your integration flow. You can find it in the overview of your integration package under *Artifacts*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Design Time Authentication
    
    </td>
    <td valign="top">
    
    To implement inbound communication with SAP Cloud Integration, use the service key credential of the *Process Integration Runtime* service instance of plan *api*.

    Choose this service key credential from the dropdown list.
    
    </td>
    </tr>
    </table>
    
4.  In the *Stages* tab, perform the following actions:

    **Configuring the Stages of an  SAP Integration Suite Artifacts Pipeline with the Job Editor**


    <table>
    <tr>
    <th valign="top">

    Stage
    
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
    
    Upload
    
    </td>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    The upload stage imports your integration flow content from your source code management system to your SAP Cloud Integration application.

    Either switch the execution of the  *Upload* stage on or off.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Flow Name
    
    </td>
    <td valign="top">
    
    Enter the name of your integration flow. You can find it in the overview of your integration package under *Artifacts*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Package ID
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter your integration package ID. You can find it in your workspace in SAP Integration Suite \(*Design* tab page\) under *Packages* -\> *Overview*.

    > ### Note:  
    > You can skip this part if the integration flow is already existing on the tenant.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Deploy
    
    </td>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    The *Deploy* stage triggers the deployment of the integration flow.

    Either switch the execution of the *Deploy* stage on or off.

    > ### Note:  
    > If you don't want to use the latest version at runtime, you can skip that part. Be aware that switching the integration test stage on would test the old features.


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="4">
    
    Integration Test
    
    </td>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    The *Integration Test* stage enables you to test your integration flow.

    Either switch the execution of the *Integration Test*stage on or off.

    > ### Tip:  
    > You can use this step to send a message to invoke the integration flow. If your integration flow is invoked automatically by a scheduler start event or a polling sender adapter, you can skip this part.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Message Body File Path
    
    </td>
    <td valign="top">
    
    \(Optional\) Specify the relative file path of your message body file, for example, `integrationsTest/messageBody`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Content Type
    
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
    
    Runtime Authentication
    
    </td>
    <td valign="top">
    
    To implement inbound communication with SAP Cloud Integration, create the *Process Integration Runtime* service instance of plan *integration-flow* and a service key. For more information, see [Creating a Service Instance for OAuth Client Credentials Grant](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/caad7a1c68c348888d9d5f5a24c13b6b.html?q=Creating%20a%20Service%20Instance%20for%20OAuth%20Client%20Credentials%20Grant.) and [Creating a Service Key for the Instance](https://help.sap.com/viewer/368c481cd6954bdfa5d0435479fd4eaf/Cloud/en-US/dcc4bfd8ba0740c7907a1bd43ed96a69.html).

    Choose this service key credential from the dropdown list.
    
    </td>
    </tr>
    </table>
    
5.  Choose *Create*.


