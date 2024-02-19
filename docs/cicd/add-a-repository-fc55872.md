<!-- loiofc55872ed1f04e7fb78bdee01a977d5a -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add a Repository

Add your repository to SAP Continuous Integration and Delivery.



<a name="loiofc55872ed1f04e7fb78bdee01a977d5a__prereq_q2l_4z1_xlb"/>

## Prerequisites

-   You have set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a repository and either a CAP, SAPUI5/SAP Fiori, SAP Cloud Integration or container-based applications project in your source code management system.




<a name="loiofc55872ed1f04e7fb78bdee01a977d5a__context_gwt_flv_znb"/>

## Context

To let SAP Continuous Integration and Delivery build, test, and deploy your sources, you need to connect the service with the repository in which they reside. If you additionally create a webhook between your repository and SAP Continuous Integration and Delivery, the service receives push events that automatically trigger the jobs connected to this repository.

The following graphic shows the connection between your repository and SAP Continuous Integration and Delivery:

  
  
**Relation between Your Repository and SAP Continuous Integration and Delivery**

![Relation between Your Repository and SAP Continuous Integration and Delivery](images/Repositories_6796338.png "Relation between Your Repository and SAP Continuous Integration and
                            Delivery")



<a name="loiofc55872ed1f04e7fb78bdee01a977d5a__steps_hwt_flv_znb"/>

## Procedure

1.  In the *Repositories* tab in SAP Continuous Integration and Delivery, choose :heavy_plus_sign:.

2.  In the *Add Repository* pane, enter the following values:

    **Values for Adding a Repository to SAP Continuous Integration and Delivery**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Name
    
    </td>
    <td valign="top">
    
    Freely choose a unique name for your repository.

    > ### Tip:  
    > We recommend using a name that refers to the actual repository in your source code management system.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Clone URL
    
    </td>
    <td valign="top">
    
    Enter the URL, which should be used for cloning this repository.

    For internet-facing Git repositories, the Clone URL must be an HTTPS URL.

    Please make sure your Clone URL doesn't include any passwords.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Credentials
    
    </td>
    <td valign="top">
    
    If your repository is private, you need Basic Authentication credentials to let SAP Continuous Integration and Delivery clone the sources. From the dropdown list, either choose credentials that you've already defined in [Creating Credentials](creating-credentials-6658c81.md) or create new ones by choosing *Create Credentials*.

    If your repository isn't private, leave this field empty.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Cloud Connector
    
    </td>
    <td valign="top">
    
    If you host your source code management system in your internal network, you need the Cloud Connector to securely connect to SAP BTP. See [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html). From the dropdown list, either choose credentials that you've already defined in [Creating Credentials](creating-credentials-6658c81.md) or create new ones by choosing *Create Credentials*.

    When using the Cloud Connector, the Clone URL must be an HTTP URL \(not HTTPS\).

    If you don't host your source code management system in your internal network, leave this field empty.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > SAP Continuous Integration and Delivery can handle submodules in your Git repository. Please make sure, however, to only use relative paths, for example:
    > 
    > -   For the same repository, but another branch: `./`
    > 
    > -   For another repository in the same organization: `../anotherRepo`
    > 
    > -   For a repository in another organization: `../../anotherOrg/anotherRepo`
    > 
    > 
    > If your submodule configuration contains a domain \(for example, `https://github.com/myOrg/myRepo`\), a warning is shown in the log and the submodule is not checked out.

3.  If you want to receive events from your source code management system through webhooks for triggering builds, you need a webhook event receiver. It's added to your repository by default. You can, however, also remove it by choosing *Remove*.

    > ### Note:  
    > You can only establish webhooks between SAP Continuous Integration and Delivery and the repositories of the source code management systems listed in [Creating Webhooks](creating-webhooks-a273cff.md).

    If you want to add a webhook event receiver for your repository, enter the following values in the *Webhook Event Receiver* section of the *Add Repository* pop-up:

    **Values for Adding a Webhook Event Receiver for Your Repository**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    Type
    
    </td>
    <td valign="top">
    
    From the dropdown list, choose your source code management system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Webhook Credential
    
    </td>
    <td valign="top">
    
    From the dropdown list, choose one of the following options:

    -   Choose a credential that you've already defined in [Creating Credentials](creating-credentials-6658c81.md).

    -   Choose *Create Credentials* at the bottom of the dropdown list to create a new credential.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    To enable your webhook event receiver, choose *ON*. If you choose *OFF*, webhook events received for this repository don't trigger any jobs.
    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > If you choose *Bitbucket Cloud* in the *Type* field, a *Bitbucket Cloud Repository UUID* parameter appears.
    > 
    > You can find the UUID of your Bitbucket Cloud repository by navigating to your repository settings in [https://bitbucket.org/](https://bitbucket.org/). From the navigation pane, choose *Repository details* and, from the *Advanced* section, copy the whole UUID including the curly brackets.

4.  Choose *Add*.


**Related Information**  


[Communication Security: Git Repositories](git-repositories-2568687.md#loio25686879a3a740ec9c5d01c6070c3610 "Find out about secure network communication between SAP Continuous Integration and Delivery and Internet-facing and corporate Git repositories.")

