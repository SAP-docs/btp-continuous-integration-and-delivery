<!-- loio090d4aaa9628426b91c90e8284213040 -->

# Add a Webhook in GitHub

Configure a webhook between your GitHub repository and SAP Continuous Integration and Delivery.



<a name="loio090d4aaa9628426b91c90e8284213040__prereq_uqr_xly_ykb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a GitHub repository, which you've added to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

-   You've added a webhook event receiver for your repository and you know the secret from your webhook credential. See [Add a Repository](add-a-repository-fc55872.md).




## Context

A webhook with GitHub allows you to automate SAP Continuous Integration and Delivery builds: Whenever you push changes to your GitHub repository, a webhook push event is sent to the service to trigger a build of the connected job.

The following graphic illustrates this flow:

  
  
**Using Webhooks with SAP Continuous Integration and Delivery**

![Using Webhooks with SAP Continuous Integration and Delivery](images/Webhooks_e0bceaa.png "Using Webhooks with SAP Continuous Integration and
                            Delivery")



## Procedure

1.  In the *Repositories* tab in SAP Continuous Integration and Delivery, choose the GitHub repository for which you want to create a webhook.

2.  In the detail view of your repository, choose *Webhook Data*.

    As a result, the *Webhook Data* pop-up opens. This pop-up provides the information you need to create a webhook in GitHub.

3.  In your project in GitHub, go to the *Settings* tab.

4.  From the navigation pane, choose *Webhooks*.

5.  Choose *Add webhook*.

6.  Enter the *Payload URL* and the *Content type* from the *Webhook Data* pop-up in SAP Continuous Integration and Delivery, as well as the *Secret* from the *Webhook Credential* you created.

7.  On the same page, choose *Just the push event*.

8.  Ensure that the *Active* check box is selected.

9.  Choose *Add webhook*.


