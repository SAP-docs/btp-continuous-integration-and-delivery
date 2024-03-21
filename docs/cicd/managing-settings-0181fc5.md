<!-- loio0181fc51422e459fa79e717d433f94d4 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Managing Settings

View or edit relevant settings using the settings dialog.



<a name="loio0181fc51422e459fa79e717d433f94d4__section_s4k_nlv_qwb"/>

## Manage Allowed Spaces

Maintain a list of the Cloud Foundry spaces that are allowed to request service bindings for a service instance of the SAP Continuous Integration and Delivery service. This prevents unauthorized users from having API access to the service.

This section is relevant if you:

-   want to enable the API usage for SAP Continuous Integration and Delivery and create a service instance in the Cloud Foundry runtime environment. See [Enabling the API Usage](enabling-the-api-usage-1aedc23.md).
-   are an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

> ### Note:  
> If you create instances or bindings on subaccount level, you can skip these steps.

To add an allowed space:

1.  Choose the icon :gear: from the header of the SAP Continuous Integration and Delivery application. A settings dialog opens.

2.  From the left-hand side list, choose *Allowed Spaces* and choose :heavy_plus_sign:.

3.  In the *Add Allowed Space* pane, enter the following values:

    **Values for Adding an Allowed Space in SAP Continuous Integration and Delivery**


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
    
    Space GUID
    
    </td>
    <td valign="top">
    
    Enter the GUID of your Could Foundry space.

    To retrieve it, use the Cloud Foundry Command Line Interface \(cf CLI\). Log on to your org, and execute the following command:

    `cf space <my-space.name> --guid` 

    > ### Example:  
    > Sample URL for the Cloud Foundry API endpoint:
    > 
    > `api.cf.eu10-004.hana.ondemand.com` and `<my-space-guid>: 977a24d6-2eaf-432d-a3e1-5294451551a3:`
    > 
    > `https://deploy-service.cf.eu10-004.hana.ondemand.com/slprot/977a24d6-2eaf-432d-a3e1-5294451551a3/slp`


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Comment
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a comment to provide more detailed information about why the space was listed.
    
    </td>
    </tr>
    </table>
    
4.  Choose *OK* to add your space to the allow list. You can also edit and delete the spaces in the list.

5.  To save your settings, choose *Save*.

    Service bindings can now only be created in those Cloud Foundry spaces which are in the list.


**Related Information**  


[Using the API](using-the-api-9819fa1.md "Discover, explore, and test the application programming interface (API) available for SAP Continuous Integration and Delivery on SAP API Business Hub.")

