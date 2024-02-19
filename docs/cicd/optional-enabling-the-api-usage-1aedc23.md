<!-- loio1aedc23d3d8a4802b66f4a3bb795030e -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# \(Optional\) Enabling the API Usage

Allow other SAP BTP services to access SAP Continuous Integration and Delivery.



<a name="loio1aedc23d3d8a4802b66f4a3bb795030e__prereq_hjd_4p2_ykb"/>

## Prerequisites

-   You have set up your global account and subaccount on SAP BTP. For an overview of the required steps, see [Getting Started in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/b328cc89ea14484d9655b8cfb8efb508.html).
-   You’re an administrator of your global account and subaccount on SAP BTP.
-   You have enabled SAP Continuous Integration and Delivery in your SAP BTP enterprise account. See [Enabling the Service](enabling-the-service-c8ed09d.md).




## Procedure

1.  In your subaccount in the SAP BTP cockpit, choose <span class="SAP-icons-V5"></span> *Entitlements* from the navigation pane.

2.  Choose *Configure Entitlements*.

3.  Choose *Add Service Plans*.

4.  Select *Continuous Integration & Delivery*.

5.  Make sure that in *Available Plans*, the option *default* is checked.

    > ### Note:  
    > If you enabled SAP Continuous Integration and Delivery using the *Free* service plan, API usage will be free of charge regardless of having chosen the *default* option.

6.  Choose *Add 1 Service Plan*.

7.  Choose *Save*.

8.  From the navigation in your subaccount, choose <span class="SAP-icons-V5"></span> *Services* \> *Service Marketplace*.

9.  In the *Foundation / Cross Services* category, choose *Continuous Integration & Delivery*.

10. In the detail view of SAP Continuous Integration and Delivery, choose *Create*.

11. In the *New Instance or Subscription* pop-up, select the following values from the drop-down lists:

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
    
    *default - Instance* 
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Runtime Environment
    
    </td>
    <td valign="top">
    
    From the dropdown list, choose the environment in which you want to create your instance, for example, *Cloud Foundry* or *Other environments*.

    > ### Note:  
    > If you chose *Cloud Foundry*, please maintain a list of allowed spaces as described in [Managing Settings](managing-settings-0181fc5.md).


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Space
    
    </td>
    <td valign="top">
    
    Enter the name of the Cloud Foundry space in which you want to create your instance, for example, cicd-api-access.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Instance Name
    
    </td>
    <td valign="top">
    
    Choose a CLI-friendly name for your instance.
    
    </td>
    </tr>
    </table>
    
12. Choose *Create*.

13. Depending on which runtime environment you chose, proceed as follows:

    -   For the Cloud Foundry environment, create a service key. For more information, see [Service Keys](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-keys-in-cloud-foundry?version=Cloud).

    -   For other enrivonments, create a service binding. For more information, see [Creating Service Bindings in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-bindings-in-other-environments?version=Cloud).





<a name="loio1aedc23d3d8a4802b66f4a3bb795030e__postreq_xds_35s_swb"/>

## Next Steps

To try out and use the SAP Continuous Integration and Delivery API, see [Using the API](using-the-api-9819fa1.md).

