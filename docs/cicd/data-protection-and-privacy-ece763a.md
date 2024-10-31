<!-- loioece763abc3fb4ca39c19f908978cb69c -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Data Protection and Privacy

Governments place legal requirements on industry to protect data and privacy. We provide features and functions to help you meet these requirements.

> ### Note:  
> SAP does not provide legal advice in any form. SAP software supports data protection compliance by providing security features and data protection-relevant functions, such as blocking and deletion of personal data. In many cases, compliance with applicable data protection and privacy laws is not covered by a product feature. Furthermore, this information should not be taken as advice or a recommendation regarding additional features that would be required in specific IT environments. Decisions related to data protection must be made on a case-by-case basis, taking into consideration the given system landscape and the applicable legal requirements. Definitions and other terms used in this documentation are not taken from a specific legal source.

The following sections provide information about SAP Continuous Integration and Delivery. For the central data protection and privacy statement for SAP BTP, see [Data Protection and Privacy](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7e513d31704a4a87831191e504ca850a.html).

> ### Caution:  
> SAP Continuous Integration and Delivery does not provide the technical capabilities to support the collection, processing, and storage of personal data.

> ### Caution:  
> Please don’t enter personal data in fields such as job names, job descriptions, and job parameters like branch name, repository name, or additional commands. These fields aren’t intended to process personal data.
> 
> Credentials are required to securely connect to source code management and other services during a build. See [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9). If credentials are associated with a personal user, they must be considered personal data. Therefore, and from a general security perspective, we strongly recommend to use a technical user instead of a personal user when creating credentials. For more information, see *Security Recommendations* in [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9).

The functionality of SAP Continuous Integration and Delivery requires to process some personal data. The following paragraphs provide transparency on this processing.

<a name="loioca8276194a65407b80bae43b4faece47"/>

<!-- loioca8276194a65407b80bae43b4faece47 -->

## Processing of Personal Data

Within a build, SAP Continuous Integration and Delivery processes and temporarily stores the following information to identify users:

-   **E-mail addresses of users who triggered a build**

    To be able to trace who triggered a build of a job, SAP Continuous Integration and Delivery stores the e-mail address of the corresponding user. Depending on how a job is triggered, SAP Continuous Integration and Delivery stores one of the following e-mail addresses:

    -   If the build is triggered manually using the service user interface or API: The e-mail address of the SAP BTP user

    -   If the build is triggered automatically through a webhook with the source code repository: The e-mail address of the commit author


    SAP Continuous Integration and Delivery is not the primary storage location of the e-mail addresses. They are retrieved from the source code management system or an identity provider \(IdP\) connected to your SAP BTP subaccount.


<a name="loio499058c8dabd4ebba7218a90bffdd901"/>

<!-- loio499058c8dabd4ebba7218a90bffdd901 -->

## Information Retrieval

To retrieve the e-mail addresses stored by SAP Continuous Integration and Delivery, use one of the following options:

-   In the service user interface, navigate to the detail view of your build.

-   To retrieve build logs through the API, use the following endpoint:

    ```
    /{version}/jobs/{jobReference}/builds
    ```

    See [SAP Business Accelerator Hub](https://api.sap.com/getting-started).


<a name="loiob9bc56a3041a4d0fae2d6c98320fd787"/>

<!-- loiob9bc56a3041a4d0fae2d6c98320fd787 -->

## Deletion

The project administrator can delete builds together with their metadata, and therefore all personal data that is stored in SAP Continuous Integration and Delivery. See [Modify, Copy, and Delete Jobs](modify-copy-and-delete-jobs-21fd276.md).

By default, SAP Continuous Integration and Delivery stores builds and their logs for 7 days and keeps a maximum of 50 builds. You can adjust the maximum values in the job configuration to a maximum of 28 days and 99 builds. If these numbers are exceeded, the oldest builds and their logs are deleted automatically.

If you disable SAP Continuous Integration and Delivery in the SAP BTP cockpit, all data that belongs to your account is deleted automatically. Audit log data is automatically deleted after a defined retention period. For information, see [Audit Log Retention for the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/adaefa64228e49ddbe40c15f63a4f74b.html).

<a name="loioce0c1c803600447dbcf41c891cb9fa0f"/>

<!-- loioce0c1c803600447dbcf41c891cb9fa0f -->

## Source Repositories and Personal Data

During a build of a job, SAP Continuous Integration and Delivery copies and processes data from the assigned source code repository. Therefore, we strongly advise you not to store any personal data in the source code repositories processed by the service. Examples for this kind of data are user IDs as part of branch names or test data that contains personal information.

If there is personal data in a source repository that is referenced by a job, this data is not only processed during the build process but may also be stored in the build logs.

Please be aware that source code management systems may include your usernames and passwords in repository clone URLs. While SAP Continuous Integration and Delivery rejects URLs containing passwords, URLs containing usernames are accepted. However, a warning is displayed if a username is detected as part of a clone URL. To protect your personal data, we recommend omitting usernames from your clone URLs.

To retrieve build logs, you can use one of the following options:

-   In the service user interface, navigate to the detail view of your build. To access the build log data, select the build tile of the corresponding build and choose <span class="SAP-icons-V5"></span> \(Actions\)** \> *Show Full Log* in the *Build Stages* view. See [Running and Monitoring CI/CD Jobs](running-and-monitoring-ci-cd-jobs-db8521c.md).

-   To retrieve build logs through the API, use the following endpoint:

    ```
    /{version}/jobs/{jobReference}/builds/{buildReference}/log
    ```

    See [SAP Business Accelerator Hub](https://api.sap.com/getting-started).


<a name="loio3845cad34e294213be4f2335ceb0a05d"/>

<!-- loio3845cad34e294213be4f2335ceb0a05d -->

## Data Export

There are two options to export your data from SAP Continuous Integration and Delivery in a standard \(JSON\) format:

-   The recommended way to retrieve data is to raise a customer incident and request a copy of your data. See [Support, Feature Requests, and Feedback](support-feature-requests-and-feedback-6e10ad4.md).

-   If you prefer to export your data on your own, you can utilize the SAP Continuous Integration and Delivery REST API. You can use it to access and download all your data. Since there is no single API endpoint to export your complete data, we recommend you to implement a small script to automate the sequence of API calls needed to retrieve the required data. For more information, see [Enabling the API Usage](enabling-the-api-usage-1aedc23.md) and [SAP Business Accelerator Hub](https://api.sap.com/getting-started).


Due to security reasons, the secrets of credentials are not included in the exported data.

<a name="loio99f4bba1621247c68aac6e6a7bfb0203"/>

<!-- loio99f4bba1621247c68aac6e6a7bfb0203 -->

## Glossary

See [Glossary for Data Protection and Privacy](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a57e0ab085404ef483a8c99e50cbf91e.html).

