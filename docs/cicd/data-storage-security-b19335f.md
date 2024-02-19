<!-- loiob19335f16e934be69aea07fdd2d74003 -->

# Data Storage Security

All data collected from SAP Continuous Integration and Delivery is stored in encrypted form.

SAP Continuous Integration and Delivery uses mechanisms in the SAP Business Technology Platform \(SAP BTP\) Cloud Foundry environment to store business and costumer data in SAP HANA Cloud. The solution runs in a multitenant environment with a tenant for each customer.

For more information about data storage security in SAP HANA Cloud running on SAP BTP, see [Data Storage Security](https://help.sap.com/viewer/c82f8d6a84c147f8b78bf6416dae7290/latest/en-US/b30fda1483b34628802a8d62bd5d39df.html).

<a name="loio4721150df6b0415285ed6abc1b7044b8"/>

<!-- loio4721150df6b0415285ed6abc1b7044b8 -->

## Build Logs

The build log data of SAP Continuous Integration and Delivery is stored separately and encrypted using one shared encryption key for all subscriptions.

The encryption key pertains only to the underlying persistence layer. The authorization concepts of SAP Continuous Integration and Delivery provided by the SAP Authorization and Trust Management service for SAP BTP ensure that only authorized users can access your build logs. See [SAP Authorization and Trust Management Service in the Cloud Foundry Environment](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/6373bb7a96114d619bfdfdc6f505d1b9.html?version=Cloud).

When creating a SAP Continuous Integration and Delivery job, you must use authentication secrets to access various services, such as your Git repository services and deployment services. These secrets are highly sensitive and SAP Continuous Integration and Delivery does not store them in build logs. However, since all the build logs are encrypted with one shared encryption key, it is recommended to double check that no sensitive information ends up in your build logs.

> ### Caution:  
> When configuration data includes sensitive information such as personal data or authentication secrets, you want to keep this information out of the code repository for security reasons. Collecting or storing any sensitive data in your source code, test scripts or test data may indirectly affect the logged content.

