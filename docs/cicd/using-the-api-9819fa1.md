<!-- loio9819fa1fc2a54c1896189eae88535290 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Using the API

Discover, explore, and test the application programming interface \(API\) available for SAP Continuous Integration and Delivery on SAP API Business Hub.



<a name="loio9819fa1fc2a54c1896189eae88535290__prereq_hjd_4p2_ykb"/>

## Prerequisites

-   You have set up your global account and subaccount on SAP BTP. For an overview of the required steps, see [Getting Started in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/b328cc89ea14484d9655b8cfb8efb508.html).
-   You’re an administrator of your global account and subaccount on SAP BTP.
-   You have enabled SAP Continuous Integration and Delivery in your SAP BTP enterprise account. See [Enabling the Service](enabling-the-service-c8ed09d.md).

-   You have enabled API usage for SAP Continuous Integration and Delivery. See [Enabling the API Usage](enabling-the-api-usage-1aedc23.md).

-   You have created a service key for your Cloud Foundry service instance or a service binding if your instance belongs to another environment. See [Creating Service Keys](https://help.sap.com/viewer/09cc82baadc542a688176dce601398de/Cloud/en-US/6fcac08409db4b0f9ad55a6acd4d31c5.html) or [Creating Service Bindings in Other Environments](https://help.sap.com/docs/service-manager/sap-service-manager/creating-service-bindings-in-other-environments?version=Cloud).




## Context

SAP Continuous Integration and Delivery provides an API that can be used to configure the service, serving as an alternative configuration method to the previously described UI-based one and allowing you to integrate the service with custom workflows.

The various API requests and responses are documented on the SAP API Business Hub. You can also try them out to see if they meet your requirements. For more information, see [SAP API Business Hub](https://api.sap.com/getting-started).

The steps below show how to configure an environment for SAP API Business Hub to try out the SAP Continuous Integration and Delivery API. See [Trying Out APIs](https://help.sap.com/viewer/e56a6c50d31541ea826021dc8e721a53/Cloud/en-US/de255b9e0c374ce68151f6b9ad517aba.html).



## Procedure

1.  Log on to the [SAP API Business Hub](https://api.sap.com/) home page and navigate to [Overview | SAP Continuous Integration and Delivery Service](https://api.sap.com/api/CloudCiApiSuite/overview).

2.  Navigate to the *API Reference* section. The API resources are displayed on the left side, next to the corresponding API endpoints on the right side.

3.  Choose an endpoint to see the complete details. For more information, see [API Details](https://help.sap.com/viewer/84b35b9c39b247e3ba2a31f02beee46d/Cloud/en-US/2af1846a8f644797a5dbcd1f87b6c58e.html).

4.  Navigate to the *Try Out* section.

5.  Choose *Select Environment* and choose :heavy_plus_sign:. A dialog window appears.

6.  In the *Basic Information* section, enter a name for your environment. From the *Starting URL* dropdown list, select the URL for the region in which you have created your service instance.

7.  In the *Authentication* section, enter the parameters *Client ID*, *Client Secret*, and *Identityzone* from the service key you created.

    > ### Note:  
    > To access your service key, follow the steps:
    > 
    > 1.  Go to the SAP BTP cockpit and navigate to your subaccount.
    > 2.  Choose *Spaces* in the navigation panel and click on your space.
    > 3.  Choose *Services* \> *Instances and Subscriptions* in the navigation panel.
    > 4.  Click on your instance of the SAP Continuous Integration and Delivery service.
    > 5.  Choose *Service Keys* in the navigation panel and click on the name of your service key.
    > 
    > The service key details in JSON format containing the `clientid`, `clientsecret` and `identityzone` are displayed.

8.  Choose *Save this environment for future sessions* to save your configuration.

9.  From the left side navigation panel, choose the endpoint that you want to try out. Enter the required parameters and choose *Run*.




<a name="loio9819fa1fc2a54c1896189eae88535290__result_ngz_dyf_zkb"/>

## Results

You can now access the SAP Continuous Integration and Delivery API documentation and use the SAP API Business Hub *Try Out* feature to get an impression of it.

