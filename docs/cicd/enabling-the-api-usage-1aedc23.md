<!-- loio1aedc23d3d8a4802b66f4a3bb795030e -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Enabling the API Usage

Allow other SAP BTP services to access SAP Continuous Integration and Delivery.



<a name="loio1aedc23d3d8a4802b66f4a3bb795030e__prereq_hjd_4p2_ykb"/>

## Prerequisites

-   You’re an administrator of your global account and subaccount on SAP BTP.

-   You've set up your global account and subaccount on SAP BTP. See [Getting Started in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/b328cc89ea14484d9655b8cfb8efb508.html).

-   You've enabled SAP Continuous Integration and Delivery in your SAP BTP enterprise account. See [Enabling the Service](enabling-the-service-c8ed09d.md).

-   You've assigned the **default** service plan of the **Continuous Integration & Delivery** service to your subaccount. See [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts).




## Procedure

1.  In your subaccount in the SAP BTP cockpit, choose <span class="SAP-icons-V5"></span> *Services* \> *Service Marketplace* from the navigation pane.

2.  In the *Foundation / Cross Services* category, choose *Continuous Integration & Delivery*.

3.  Choose *Create*.

4.  From the *Plan* drop-down list, choose the *default* plan for *Instances*.

5.  Choose your *Runtime Environment* from the respective drop-down list.

    > ### Note:  
    > If you use the *Cloud Foundry* runtime environment, you need to enable your space, first. See [Manage Allowed Spaces](managing-settings-0181fc5.md#loio0181fc51422e459fa79e717d433f94d4__section_s4k_nlv_qwb).

6.  In the *Instance Name* text field, enter a name for your instance.

7.  Choose *Next*.

8.  In the text field, specify the role parameter for the API usage of your service instance in JSON format. Choose one of the following options:

    -   `{ "role" : "developer" }` for the Developer role

    -   `{ "role" : "administrator" }` for the Administrator role


    For an overview of the role permissions, see [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

    > ### Note:  
    > If you don’t specify a role for the API usage of your service instance, it is assigned the Administrator role by default.

9.  Choose *Create*.

10. Depending on which runtime environment you chose, proceed as follows:

    -   For the Cloud Foundry environment, create a service key. For more information, see [Service Keys](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-keys-in-cloud-foundry?version=Cloud).

    -   For other environments, create a service binding. For more information, see [Creating Service Bindings in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-bindings-in-other-environments?version=Cloud).





<a name="loio1aedc23d3d8a4802b66f4a3bb795030e__postreq_xds_35s_swb"/>

## Next Steps

To try out and use the SAP Continuous Integration and Delivery API, see [Using the API](using-the-api-9819fa1.md).

