<!-- loioe452155b949042baacab18db17295546 -->

# Add a Webhook in GitLab

Configure a webhook between your GitLab repository and SAP Continuous Integration and Delivery.



<a name="loioe452155b949042baacab18db17295546__prereq_xzc_ygr_qpb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a GitLab repository, which you've added to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

-   You've added a webhook event receiver for your repository and you know the secret from your webhook credential. See [Add a Repository](add-a-repository-fc55872.md).




<a name="loioe452155b949042baacab18db17295546__context_zmm_grr_qpb"/>

## Context

A webhook with GitLab allows you to automate SAP Continuous Integration and Delivery builds: Whenever you push changes to your GitLab repository, a webhook push event is sent to the service to trigger a build of the connected job.

The following graphic illustrates this flow:

  
  
**Using Webhooks with SAP Continuous Integration and Delivery**

![Using Webhooks with SAP Continuous Integration and Delivery](images/Webhooks_e0bceaa.png "Using Webhooks with SAP Continuous Integration and
                            Delivery")

For an overview of how to create a webhook in a repository, watch the demo video in [Creating Webhooks](creating-webhooks-a273cff.md).



<a name="loioe452155b949042baacab18db17295546__steps_bgk_4rr_qpb"/>

## Procedure

1.  In the *Repositories* tab in SAP Continuous Integration and Delivery, choose the GitLab repository for which you want to create a webhook.

2.  In the detail view of your repository, choose *Webhook Data*.

    As a result, the *Webhook Data* pop-up opens. This pop-up provides the information you need to create a webhook in GitLab.

3.  In your project in GitLab, go to the *Settings* tab.

4.  From the navigation pane, choose *Webhooks*.

5.  Enter the *URL* from the *Webhook Data* pop-up in SAP Continuous Integration and Delivery and the *Secret token* from the *Webhook Credential* you created.

6.  In the *Trigger* section, choose *Push events*.

7.  Choose *Enable SSL verification*.

8.  Choose *Add webhook*.


