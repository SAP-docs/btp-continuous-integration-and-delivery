<!-- loio0181fc51422e459fa79e717d433f94d4 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Manage Allowed Spaces

Prevent unauthorized users from having API access to SAP Continuous Integration and Delivery by maintaining a list of Cloud Foundry spaces that are allowed to request service instances.



<a name="loio0181fc51422e459fa79e717d433f94d4__prereq_qpz_y35_cbc"/>

## Prerequisites

> ### Note:  
> If you create instances or bindings on subaccount level, you can skip this procedure.

-   You want to enable the API usage for SAP Continuous Integration and Delivery and create a service instance in the Cloud Foundry environment. See [Enabling the API Usage](enabling-the-api-usage-1aedc23.md).

-   You’re assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).




<a name="loio0181fc51422e459fa79e717d433f94d4__steps_itn_fj5_cbc"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, choose :gear:.

    As a result, the *Settings* dialog opens.

2.  From the navigation pane, choose <span class="SAP-icons-V5"></span> *Allowed Spaces*.

3.  Choose :heavy_plus_sign:.

4.  In the *Add Allowed Space* pop-up window, enter the following values:

    -   *Space GUID:* Enter the GUID of your Cloud Foundry space.

        To retrieve it, execute the following command in the Cloud Foundry command line interface \(cf CLI\):

        ```
        cf space <my-space.name> --guid
        ```

        The following example shows a sample URL for the Cloud Foundry API endpoint:

        > ### Example:  
        > `api.cf.eu10-004.hana.ondemand.com` and `<my-space-guid>: 977a24d6-2eaf-432d-a3e1-5294451551a3:`
        > 
        > `https://deploy-service.cf.eu10-004.hana.ondemand.com/slprot/977a24d6-2eaf-432d-a3e1-5294451551a3/slp`

    -   *Comment:* \(Optional\) Enter a comment to provide more detailed information about why the space was listed.


5.  Choose *OK* to add your space to the allow list and then *Save* to confirm your changes.




<a name="loio0181fc51422e459fa79e717d433f94d4__result_tpp_2m5_cbc"/>

## Results

You can now create service instances in the Cloud Foundry spaces that are listed in the allow list.

**Related Information**  


[Using the API](using-the-api-9819fa1.md "Discover, explore, and test the application programming interface (API) available for SAP Continuous Integration and Delivery on SAP Business Accelerator Hub.")

