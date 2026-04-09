<!-- loioef67342af0464f3a8a34eec031c64f44 -->

# Add a Webhook in Bitbucket Cloud

Configure a webhook between your Bitbucket Cloud repository and SAP Continuous Integration and Delivery.



<a name="loioef67342af0464f3a8a34eec031c64f44__prereq_uqr_xly_ykb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a Bitbucket Cloud repository, which you've added to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

-   You've added a webhook event receiver for your repository and you have specified the UUID of your Bitbucket Cloud repository. See [Add a Repository](add-a-repository-fc55872.md).




<a name="loioef67342af0464f3a8a34eec031c64f44__context_dtd_x2n_twb"/>

## Context

A webhook with Bitbucket Cloud allows you to automate SAP Continuous Integration and Delivery builds: Whenever you push changes to your Bitbucket Cloud repository, a webhook push event is sent to the service to trigger a build of the connected job.

The following graphic illustrates this flow:

  
  
**Using Webhooks with SAP Continuous Integration and Delivery**

![Using Webhooks with SAP Continuous Integration and Delivery](images/Webhooks_e0bceaa.png "Using Webhooks with SAP Continuous Integration and
                            Delivery")

For an overview of how to create a webhook in a repository, watch the demo video in [Creating Webhooks](creating-webhooks-a273cff.md).



<a name="loioef67342af0464f3a8a34eec031c64f44__steps_etd_x2n_twb"/>

## Procedure

1.  In the *Repositories* tab in SAP Continuous Integration and Delivery, choose the Bitbucket Cloud repository for which you want to create the webhook.

    As a result, the detail view of your repository opens. The Webhook Data section provides the information you need to create a webhook in Bitbucket Cloud.

2.  In [https://bitbucket.org/](https://bitbucket.org/), navigate to the repository where you want to add the webhook.

3.  From the naviagtion pane, choose *Repository settings* \> *Webhooks*.

4.  Choose *Add webhook*.

5.  Freely choose a title for your webhook and enter the *URL* from the *Webhook Data* section in SAP Continuous Integration and Delivery, as well as the *Secret* from the *Webhook Credential* you created.

6.  Ensure that the *Active* check box is selected.

7.  In the *Trigger* section, choose *Push* to set the webhook trigger to a repository push event.

8.  Choose *Save*.


