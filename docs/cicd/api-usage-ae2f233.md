<!-- loioae2f233139df4697b48a589a936b6226 -->

# API Usage

> ### Note:  
> This section is only relevant if you have enabled API usage for SAP Continuous Integration and Delivery. See [\(Optional\) Enabling the API Usage](optional-enabling-the-api-usage-1aedc23.md).

It is recommended to rotate the service keys for API usage regularly, that is, by creation of new keys and deletion of the retired keys. Service keys can be created within the SAP BTP cockpit or by using the Cloud Foundry command line interface. See [Creating Service Keys](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/4514a14ab6424d9f84f1b8650df609ce.html).

After adjusting the API clients to use the new service key, you can delete the corresponding retired service key in the SAP BTP cockpit or via the Cloud Foundry command line interface.

