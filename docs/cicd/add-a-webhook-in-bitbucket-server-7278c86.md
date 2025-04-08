<!-- loio7278c86cdf694baf8b4e77b9bb1e1346 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add a Webhook in Bitbucket Server

Configure a webhook between your Bitbucket Server repository and SAP Continuous Integration and Delivery.



<a name="loio7278c86cdf694baf8b4e77b9bb1e1346__prereq_uqr_xly_ykb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a Bitbucket Server repository, which you've added to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

-   You've added a webhook event receiver for your repository and you know the secret from your webhook credential. See [Add a Repository](add-a-repository-fc55872.md).




## Context

A webhook with Bitbucket Server allows you to automate SAP Continuous Integration and Delivery builds: Whenever you push changes to your Bitbucket Server repository, a webhook push event is sent to the service to trigger a build of the connected job.

The following graphic illustrates this flow:

  
  
**Using Webhooks with SAP Continuous Integration and Delivery**

![Using Webhooks with SAP Continuous Integration and Delivery](images/Webhooks_e0bceaa.png "Using Webhooks with SAP Continuous Integration and
                            Delivery")

For an overview of how to create a webhook in a repository, watch the demo video in [Creating Webhooks](creating-webhooks-a273cff.md).



## Procedure

1.  In the *Repositories* tab in SAP Continuous Integration and Delivery, choose the Bitbucket Server repository for which you want to create a webhook.

2.  In the detail view of your repository, choose *Webhook Data*.

    As a result, the *Webhook Data* pop-up opens. This pop-up provides the information you need to create a webhook in Bitbucket Server.

3.  In your repository in Bitbucket Server, choose :gear:.

4.  Choose *Webhooks* \> *Create webhook*.

5.  Freely choose a name for your webhook and enter the *URL* from the *Webhook Data* pop-up in SAP Continuous Integration and Delivery. Enter the *Secret* from the *Webhook Credential* you created.

6.  In the *Events* field, choose *Repository push*.

7.  Ensure that the *Active* check box is selected.

8.  Choose *Create*.


