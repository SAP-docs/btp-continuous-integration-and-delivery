<!-- loioe3efb69ba94c43309ae5c3f9ea8832ee -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add a Webhook in Azure Repos

Configure a webhook between your Azure Repos repository and SAP Continuous Integration and Delivery.



<a name="loioe3efb69ba94c43309ae5c3f9ea8832ee__prereq_uqr_xly_ykb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a Azure Repos repository, which you've added to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

-   You've added a webhook event receiver for your repository and you know the secret from your webhook credential. See [Add a Repository](add-a-repository-fc55872.md).




## Context

A webhook with Azure Repos allows you to automate SAP Continuous Integration and Delivery builds: Whenever you push changes to your Azure Repos repository, a webhook push event is sent to the service to trigger a build of the connected job.

The following graphic illustrates this flow:

  
  
**Using Webhooks with SAP Continuous Integration and Delivery**

![Using Webhooks with SAP Continuous Integration and Delivery](images/Webhooks_e0bceaa.png "Using Webhooks with SAP Continuous Integration and
                            Delivery")

For an overview of how to create a webhook in a repository, watch the demo video in [Creating Webhooks](creating-webhooks-a273cff.md).



## Procedure

1.  In the *Repositories* tab in SAP Continuous Integration and Delivery, choose the Azure Repos repository for which you want to create a webhook.

2.  In the detail view of your repository, choose *Webhook Data*.

    As a result, the *Webhook Data* pop-up opens. This pop-up provides the information you need to create a webhook in Azure Repos.

3.  In your project in Azure Repos, go to the *Project settings* tab.

4.  Choose *Service hooks* and :heavy_plus_sign:*Create subscription*.

5.  In the *Service* section, choose *Web hooks* and choose *Next*.

6.  In the *Trigger* section, choose and configure the *Code pushed* event. Enter the target repository and branch to which you want to push your code changes and choose *Next*.

7.  In the *Settings* section, enter the *URL* and *Basic authentication username* from the *Webhook Data* pop-up in SAP Continuous Integration and Delivery. For *Basic authentication password*, enter the *Secret* from the *Webhook Credential* you created.

8.  Choose *Finish*.


