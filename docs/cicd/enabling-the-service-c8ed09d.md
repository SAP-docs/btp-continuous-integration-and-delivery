<!-- loioc8ed09df9ebd4556ae2375feac829c24 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Enabling the Service

Enable SAP Continuous Integration and Delivery in the SAP BTP cockpit.



<a name="loioc8ed09df9ebd4556ae2375feac829c24__prereq_gbn_5zg_vdb"/>

## Prerequisites

> ### Note:  
> If you are using this service as part of SAP Build Code, follow the [SAP Build Code Initial Setup](https://help.sap.com/docs/build_code/d0d8f5bfc3d640478854e6f4e7c7584a/07698d7c31284e4db370acdf017cfd14.html?version=SHIP) instructions instead.

-   You've set up your global account and subaccount on SAP BTP in the Cloud Foundry environment. See [Getting Started in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/b328cc89ea14484d9655b8cfb8efb508.html).

-   You’re an administrator of your global account and subaccount on SAP BTP.

-   **Customers:** You use the CPEA \(Cloud Platform Enterprise Agreement\) license model. See [What Is the Consumption-Based Commercial Model](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7047eb4a15a84ac7be3c8612179e6d1f.html).

    **Partners:** You have a Test, Demonstration, and Development License. See [SAP Partner Licensing Services](https://partneredge.sap.com/en/partnership/licenses/tdd.html).

-   You've assigned the **default \(Application\)** \(service technical name: `cicd-app`\) service plan of the **Continuous Integration & Delivery** service to your subaccount. See [Configure Entitlements and Quotas for Subaccounts](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts).




<a name="loioc8ed09df9ebd4556ae2375feac829c24__steps_dlx_5n2_sdb"/>

## Procedure

1.  In your subaccount in the SAP BTP cockpit, choose <span class="SAP-icons-V5"></span> *Services* \> *Service Marketplace*.

2.  In the *Foundation / Cross Services* category, choose *Continuous Integration & Delivery*.

    > ### Note:  
    > If in the *Service Marketplace*, you can’t see the *Continuous Integration & Delivery* tile, you might need to add the required entitlements to your subaccount. See [Configure Entitlements and Quotas from Your Global Account](https://help.sap.com/docs/btp/sap-business-technology-platform/configure-entitlements-and-quotas-for-subaccounts?version=Cloud#configure-entitlements-and-quotas-from-your-global-account).

3.  In the detail view of SAP Continuous Integration and Delivery, choose *Create*.

    As a result, the *New Instance or Subscription* pop-up window opens.

4.  From the *Service* drop-down list, select *Continuous Integration & Delivery*.

5.  From the *Plan* drop-down list, select one of the following options:

    -   *Subscription: default*

    -   *Subscription: free*

        The free service plan is part of the free tier model for SAP BTP. It provides you access to learn, develop, and implement integrations and extensions in your enterprise account without time restrictions.

        > ### Restriction:  
        > When using the free plan, the following limitations apply:
        > 
        > -   You can only create two jobs.
        > 
        > -   You can only run one build at a time.
        > 
        > -   Jobs that remain unchanged for more than one week are deactivated automatically. You can still reactivate them if you want to use them after this time.
        > 
        > -   The amount of computing hours is limited to 10 hours in a rolling period of 30 days.
        > 
        > Once you've reached the limits of the free plan, you can upgrade it to a paid plan. For more information, see [Using Free Service Plans](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/524e1081d8dc4b0f9d055a6bec383ec3.html).


6.  Choose *Create*.




<a name="loioc8ed09df9ebd4556ae2375feac829c24__result_ngz_dyf_zkb"/>

## Results

You’ve subscribed to SAP Continuous Integration and Delivery. As a result, you can access the service. See [Accessing the Service](accessing-the-service-9cec395.md).

