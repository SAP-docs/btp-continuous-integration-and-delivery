<!-- loiobb2cd0a57fc54525888a6988a7ab704c -->

# Identity and Access Management

For identity and access management, SAP Continuous Integration and Delivery uses functions provided by an identity provider that is hosted by the SAP Business Technology Platform or your own corporate identity provider. For more information on SAP BTP standards for identity and access management, see [SAP Authorization and Trust Management Service in the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/6373bb7a96114d619bfdfdc6f505d1b9.html).

Access to SAP Continuous Integration and Delivery is controlled by a role-based authorization management. This means that an account administrator can configure the service and assign roles or role-collections to users. These roles allow the user to access the service and perform certain business tasks.

To have access to SAP Continuous Integration and Delivery, your user needs to be assigned to one of the following predefined role collections:

-   CI/CD Service Administrator
-   CI/CD Service Developer

For more information, see [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).



<a name="loiobb2cd0a57fc54525888a6988a7ab704c__section_h55_cgm_15b"/>

## Session Security and Cookies

Once authenticated, a session is established and subsequent requests are executed within the session. The application router manages the sessions and issues the session cookies. For more information, see [Application Router](https://help.sap.com/docs/BTP/65de2977205c403bbc107264b8eccf4b/01c5f9ba7d6847aaaf069d153b981b51.html).

SAP Continuous Integration and Delivery itself does not set any cookies.

For information that specifically applies to access control security for SAP Continuous Integration and Delivery jobs connected to Git repositories, see the section **[Git Repositories](git-repositories-8a57562.md#loio8a57562c7d2d4f7db53a29b2f1e146e9)**.

