<!-- loio25686879a3a740ec9c5d01c6070c3610 -->

# Git Repositories

To build a project, SAP Continuous Integration and Delivery needs access to the repository which contains the source code of the project. Our service facilitates secure network communication to both Internet-facing and corporate Git repositories.

<a name="loio7e5df222287c4af98e06bd6df8c2a110"/>

<!-- loio7e5df222287c4af98e06bd6df8c2a110 -->

## Internet-facing Git Repository Services

SAP Continuous Integration and Delivery enables you to connect to and interact with Internet-facing Git repositories.

For source code repositories exposed to the Internet, only secure HTTPS connections are supported. You can specify the protocol for each repository by configuring the parameter *Clone URL*. For more information, see [Add a Repository](https://help.sap.com/viewer/SAP-Cloud-Platform-Continuous-Integration-and-Delivery/fc55872ed1f04e7fb78bdee01a977d5a.html).

<a name="loiocc4fff321b5d486c943afe8f7fb5513f"/>

<!-- loiocc4fff321b5d486c943afe8f7fb5513f -->

## Corporate Git Repositories

SAP Continuous Integration and Delivery allows you to securely connect to your corporate repositories.

You can work with corporate Git repositories once a destination has been created in your subaccount and once you have installed and configured SAP Cloud Connector. As an intermediary, SAP Cloud Connector lets you establish a secure tunnel between your repositories and SAP Continuous Integration and Delivery. For more information, see [Cloud Connector](https://help.sap.com/viewer/cca91383641e40ffbe03bdc78f00f681/Cloud/en-US/e6c7616abb5710148cfcf3e75d96d596.html).

SAP Cloud Connector establishes a secure TLS \(Transport Layer Security\) tunnel between itself and SAP Continuous Integration and Delivery. After the tunnel is established, SAP Continuous Integration and Delivery uses it for all the connections to your repositories.

During the configuration of a repository in SAP Continuous Integration and Delivery, the parameter `Clone URL` needs to be specified. For corporate Git repositories, it cannot refer to the Git repository directly, but must point to a virtual resource within SAP Cloud Connector representing the actual Git repository. The `Clone URL` to address such a virtual SAP Cloud Connector resource must be an HTTP URL \(not HTTPS\).

Even though the HTTP protocol must be used, secure communication is always ensured because the surrounding tunnel established by SAP Cloud Connector is TLS-encrypted.

To learn more about how to connect SAP Continuous Integration and Delivery with your corporate Git repository, see [\(Optional\) Add a Corporate Git Repository](optional-add-a-corporate-git-repository-4b6ee9a.md) or the tutorial [Connect SAP Continuous Integration and Delivery with Your Corporate Git](https://developers.sap.com/tutorials/cicd-corporate-git.html).

<a name="loioeba30218adee444eb00e6819dbf4dae7"/>

<!-- loioeba30218adee444eb00e6819dbf4dae7 -->

## Repository Webhooks

SAP Continuous Integration and Delivery allows you to establish secure webhook connections from the supported source code management systems.

To allow SAP Continuous Integration and Delivery to validate and authenticate webhook requests, webhook endpoint secrets are required. In combination with the HTTPS protocol, webhook endpoint secrets ensure that your SAP Continuous Integration and Delivery service instance is only receiving the expected Git repository requests and that its content is not tampered with. For more information, see [Creating Webhooks](https://help.sap.com/viewer/SAP-Cloud-Platform-Continuous-Integration-and-Delivery/a273cffe863b4663b23942a9bb73071d.html).

