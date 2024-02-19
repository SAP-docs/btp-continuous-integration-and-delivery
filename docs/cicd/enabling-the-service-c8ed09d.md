<!-- loioc8ed09df9ebd4556ae2375feac829c24 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Enabling the Service

Enable SAP Continuous Integration and Delivery in the SAP BTP cockpit.



<a name="loioc8ed09df9ebd4556ae2375feac829c24__prereq_gbn_5zg_vdb"/>

## Prerequisites

-   You have set up your global account and subaccount on SAP BTP in the Cloud Foundry environment. See [Getting Started in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/b328cc89ea14484d9655b8cfb8efb508.html).

-   You’re an administrator of your global account and subaccount on SAP BTP.

-   **Customers:** You use the CPEA \(Cloud Platform Enterprise Agreement\) license model. See [What Is the Consumption-Based Commercial Model](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7047eb4a15a84ac7be3c8612179e6d1f.html).

    **Partners:** You have a Test, Demonstration, and Development License. See [SAP Partner Licensing Services](https://partneredge.sap.com/en/partnership/licenses/tdd.html).




<a name="loioc8ed09df9ebd4556ae2375feac829c24__steps_dlx_5n2_sdb"/>

## Procedure

1.  In your subaccount in the SAP BTP cockpit, choose <span class="SAP-icons-V5"></span> *Services* \> *Service Marketplace*.

2.  In the *Foundation / Cross Services* category, choose *Continuous Integration & Delivery*.

3.  In the detail view of SAP Continuous Integration and Delivery, choose *Create*.

4.  In the *New Instance or Subscription* pop-up, select the following values from the drop-down lists:

    **Values for the New Instance or Subscription Pop-Up**


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
    
    Service
    
    </td>
    <td valign="top">
    
    *Continuous Integration & Delivery* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Plan
    
    </td>
    <td valign="top">
    
    Choose one of the following options:

    -   **Enterprise account:** *default - Subscription*

    -   **Enterprise account:** *free - Subscription*

        > ### Note:  
        > The free service plan is part of the free tier model for SAP BTP. It provides you access to learn, develop, and implement integrations and extensions in your enterprise account without time restrictions.
        > 
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
        > Once you've reached the limits of the free plan, you can easily upgrade it to a paid plan. For more information, see [Using Free Service Plans](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/524e1081d8dc4b0f9d055a6bec383ec3.html).



    
    </td>
    </tr>
    </table>
    
5.  Choose *Create*.




<a name="loioc8ed09df9ebd4556ae2375feac829c24__result_ngz_dyf_zkb"/>

## Results

You’ve subscribed to SAP Continuous Integration and Delivery. As a result, you can access the service. See [Accessing the Service](accessing-the-service-9cec395.md).

