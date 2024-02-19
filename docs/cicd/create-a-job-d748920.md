<!-- loiod748920175554221be1ba8b461ada030 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Create a Job

Configure a job for SAP Continuous Integration and Delivery.



<a name="loiod748920175554221be1ba8b461ada030__prereq_q2l_4z1_xlb"/>

## Prerequisites

-   You have set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a repository and either a CAP, SAPUI5/SAP Fiori, SAP Cloud Integration or container-based applications project in your source code management system.




<a name="loiod748920175554221be1ba8b461ada030__steps_ibx_ckz_ykb"/>

## Procedure

1.  In the *Jobs* tab in SAP Continuous Integration and Delivery, choose :heavy_plus_sign:.

2.  In the *Create Job* pane, enter the following values:

    **Values for Creating a Job in SAP Continuous Integration and Delivery**


    <table>
    <tr>
    <th valign="top">

    Category
    
    </th>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="7">
    
    General Information
    
    </td>
    <td valign="top">
    
    Job Name
    
    </td>
    <td valign="top">
    
    Freely choose a unique name for your job.

    > ### Tip:  
    > We recommend using a name that contains both your source code management system project name and branch.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Description
    
    </td>
    <td valign="top">
    
    Enter a meaningful description for your job.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Repository
    
    </td>
    <td valign="top">
    
    Either choose a repository that you've already added to SAP Continuous Integration and Delivery or add one by choosing *Add Repository*. See [Add a Repository](add-a-repository-fc55872.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Branch
    
    </td>
    <td valign="top">
    
    Enter the branch from which you want to receive push events.

    You can also configure a continuous integration and delivery job for multiple branches in your repository. See [Configure a Multi-Branch Job](configure-a-multi-branch-job-d52d3ca.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Pipeline
    
    </td>
    <td valign="top">
    
    Choose the pipeline you want to execute. Depending on your use case, you can choose one of the following options:

    -   *Cloud Foundry Environment* for applications following the SAP Cloud Application Programming Model in the Cloud Foundry environment

    -   *SAP Fiori in the Cloud Foundry environment* for SAPUI5/SAP Fiori applications in the Cloud Foundry environment

    -   *SAP Fiori in the Neo environment* for SAPUI5/SAP Fiori applications in the Neo environment

    -   *SAP Integration Suite Artifacts* for the development of SAP Cloud Integration artifacts in the Cloud Foundry environment.

    -   *Container-Based Applications* for the development of container-based applications.


    For more information, see [Supported Pipelines](supported-pipelines-e293286.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Version
    
    </td>
    <td valign="top">
    
    If you create a new job, the latest version is selected by default. If you edit an existing job, you can change the version by choosing an option from the drop-down list.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    To enable your job, choose *ON*. If you choose *OFF*, you can deactivate your job without deleting its configuration.

    > ### Remember:  
    > Any job created using a trial account or the Free service plan will be deactivated after one week of remaining unchanged.
    > 
    > You can use this switch to activate it again at any time.


    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="2">
    
    Build Retention
    
    </td>
    <td valign="top">
    
    Keep logs for
    
    </td>
    <td valign="top">
    
    Enter the time after which your builds are automatically deleted. Choose a range between 1 and 28 days.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Keep maximum
    
    </td>
    <td valign="top">
    
    Enter the maximum number of builds you want to keep. If your number of builds exceeds this maximum, the oldest ones are deleted automatically. Choose a range between 1 and 99 builds.
    
    </td>
    </tr>
    <tr>
    <td valign="top" colspan="2">
    
    Stages
    
    </td>
    <td valign="top">
    
    Depending on the pipeline type you want to create, you’re asked for different values. For more details, see [Supported Pipelines](supported-pipelines-e293286.md).
    
    </td>
    </tr>
    </table>
    
3.  Choose *Add*.


