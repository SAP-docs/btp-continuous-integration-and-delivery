<!-- loio6658c81f3e43456891852955b1ee11db -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Creating Credentials

Configure credentials for connecting SAP Continuous Integration and Delivery to other services.



<a name="loio6658c81f3e43456891852955b1ee11db__prereq_h55_s4n_zkb"/>

## Prerequisites

-   You've set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You’re assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).




## Context

During each job, SAP Continuous Integration and Delivery connects to other services \(for example, to GitHub or another source code management system to clone your sources, and to SAP BTP to deploy your application\). To authenticate SAP Continuous Integration and Delivery against these services, you need to configure credentials that can be referenced by a job. Each credential is stored under a unique name in your subaccount.



## Procedure

1.  In the *Credentials* tab in SAP Continuous Integration and Delivery, choose :heavy_plus_sign:.

2.  In the *Create Credentials* pop-up, enter the following values:


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
    
    Name
    
    </td>
    <td valign="top">
    
    Freely choose a unique name for your credential.

    To provide a valid credential name, adhere to the following rules:

    -   Start and end with an alphanumeric character.
    -   Only use lowercase letters, numbers, hyphens, and dots.
    -   Do not use dots next to each other or dots next to hyphens.
    -   Only use a maximum of 253 characters.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Description
    
    </td>
    <td valign="top">
    
    Enter a meaningful description for your credential.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Type
    
    </td>
    <td valign="top">
    
    From the drop-down list, choose the authentication type of your credential.

    For more information on which credential type is needed for which step within a job, see [Supported Pipelines](supported-pipelines-e293286.md).
    
    </td>
    </tr>
    </table>
    
3.  Depending on which type you choose, you're asked for additional values:


    <table>
    <tr>
    <th valign="top">

    Authentication Type
    
    </th>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="2">
    
    Basic Authentication
    
    </td>
    <td valign="top">
    
    Username
    
    </td>
    <td valign="top">
    
    Enter your username for the Basic Authentication credential.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Password
    
    </td>
    <td valign="top">
    
    Enter your password for the Basic Authentication credential.
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="3">
    
    Basic Authentication for Custom IdP
    
    </td>
    <td valign="top">
    
    Username
    
    </td>
    <td valign="top">
    
    Enter your username for the Basic Authentication for Custom IdP credential.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Password
    
    </td>
    <td valign="top">
    
    Enter your password for the Basic Authentication for Custom IdP credential.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Origin Key
    
    </td>
    <td valign="top">
    
    Enter the origin key to connect to Cloud Foundry. You can find it in your subaccount in the SAP BTP cockpit under *Cloud Foundry* \> *Org Members* in the *Origin* column.
    
    </td>
    </tr>
    <tr>
    <td valign="top" rowspan="4">
    
    OAuth

    > ### Note:  
    > For how to create an OAuth client, see **Create an OAuth Client** in [Using Platform APIs](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/392af9d162694d6595499f1549978aa6.html).
    > 
    > When creating an OAuth client for SAP Continuous Integration and Delivery, make sure that the API for **Solutions Lifecycle Management** is selected together with its scopes.


    
    </td>
    <td valign="top">
    
    Client ID
    
    </td>
    <td valign="top">
    
    Enter your client ID.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Client Secret
    
    </td>
    <td valign="top">
    
    Enter your client secret.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Cloud Region
    
    </td>
    <td valign="top">
    
    Enter the host of the service to which you want to connect SAP Continuous Integration and Delivery. See [Regions and Hosts Available for the Neo Environment](https://help.sap.com/viewer/ea72206b834e4ace9cd834feed6c0e09/Cloud/en-US/d722f7cea9ec408b85db4c3dcba07b52.html).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Service URL
    
    </td>
    <td valign="top">
    
    The URL of the OAuth service is generated automatically.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Service Key
    
    </td>
    <td valign="top">
    
    Service Key
    
    </td>
    <td valign="top">
    
    Create a service key in the space of the service instance to which you want to connect SAP Continuous Integration and Delivery. See [Creating Service Keys](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/4514a14ab6424d9f84f1b8650df609ce.html).

    Copy and paste this service key in the JSON format into the *Service Key* text field.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Secret Text
    
    </td>
    <td valign="top">
    
    Secret
    
    </td>
    <td valign="top">
    
    Enter an arbitrary string value. This string value is stored in a secret store.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Cloud Connector
    
    </td>
    <td valign="top">
    
    Location ID
    
    </td>
    <td valign="top">
    
    Enter the location ID of the Cloud Connector for your subaccount. You can find it in the SAP BTP cockpit under <span class="SAP-icons-V5"></span> *Connectivity* \> *Cloud Connectors*.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Webhook Secret
    
    </td>
    <td valign="top">
    
    Secret
    
    </td>
    <td valign="top">
    
    Freely enter a secret or choose the *Generate* button to generate a secret for your webhook.

    > ### Caution:  
    > This secret is only visible during the creation of the webhook credential. Make sure to copy and save it before closing the dialog.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Container Registry Configuration
    
    </td>
    <td valign="top">
    
    Content
    
    </td>
    <td valign="top">
    
    This is a JSON document used by the docker client to authenticate the container when registering. It can be created with the [docker login](https://docs.docker.com/engine/reference/commandline/login/) command.

    ```
    {
      "auths": {
        "my.registry.url.com": {
          "auth": "<base64(user:password)>"
        }
      }
    }
    ```


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Kubernetes Configuration
    
    </td>
    <td valign="top">
    
    Content
    
    </td>
    <td valign="top">
    
    This is a YAML document used by the Kubernetes client to authenticate a Kubernetes cluster.

    Use a Kubernetes configuration that contains an access token for a suitable service account. For how to create the service account and the configuration, see [Create a Kyma service account](https://developers.sap.com/tutorials/kyma-create-service-account.html). The required permissions \(Kubernetes roles and cluster roles\) of the service account depend on the types of resources that are created or updated during the deployment.

    > ### Note:  
    > For Kyma environments, you can't use a Kubernetes configuration downloaded from the SAP BTP cockpit because it only supports interactive signon.


    
    </td>
    </tr>
    </table>
    
4.  Choose *Save*.


