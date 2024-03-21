<!-- loioece763abc3fb4ca39c19f908978cb69c -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Data Protection and Privacy

Governments place legal requirements on industry to protect data and privacy. We provide features and functions to help you meet these requirements.

> ### Note:  
> SAP does not provide legal advice in any form. SAP software supports data protection compliance by providing security features and data protection-relevant functions, such as blocking and deletion of personal data. In many cases, compliance with applicable data protection and privacy laws is not covered by a product feature. Furthermore, this information should not be taken as advice or a recommendation regarding additional features that would be required in specific IT environments. Decisions related to data protection must be made on a case-by-case basis, taking into consideration the given system landscape and the applicable legal requirements. Definitions and other terms used in this documentation are not taken from a specific legal source.

The following sections provide information about SAP Continuous Integration and Delivery. For the central data protection and privacy statement for SAP BTP, see [Data Protection and Privacy](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7e513d31704a4a87831191e504ca850a.html).

> ### Caution:  
> SAP Continuous Integration and Delivery does not provide the technical capabilities to support the collection, processing, and storage of personal data. To prioritize data privacy and protection, we recommend to minimize the amount of personal data processed by SAP Continuous Integration and Delivery.

During a pipeline run, SAP Continuous Integration and Delivery copies and processes data from the assigned source code repositories. You as the data controller are legally responsible to apply best practices in protecting your personal data. We strongly advise you not to store any personal data in the source code repositories processed by SAP Continuous Integration and Delivery.

Credentials are required to securely connect to source code management and other services during a pipeline run. See [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9). If credentials are associated with a personal user, they must be considered as personal data. Therefore, and from a general security perspective, it is strongly recommended to use a technical user instead of your personal user when creating credentials. For more information, see *Security Recommendations* in [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9).

Please be aware that source code management systems may include your usernames and passwords in repository clone URLs. While SAP Continuous Integration and Delivery rejects URLs containing passwords, URLs containing usernames are accepted. However, a warning is displayed if a username is detected as part of a clone URL. To protect your personal data, we recommend omitting usernames from your clone URLs.

The functionality of SAP Continuous Integration and Delivery requires to process some personal data. The following paragraphs provide transparency on the processing of personal data by SAP Continuous Integration and Delivery.

<a name="loioca8276194a65407b80bae43b4faece47"/>

<!-- loioca8276194a65407b80bae43b4faece47 -->

## Processing of Personal Data

Within a pipeline run, SAP Continuous Integration and Delivery processes and temporarily stores the following information to identify users:

-   **E-mail addresses of users who triggered a build**

    To be able to trace who triggered a pipeline run, SAP Continuous Integration and Delivery stores the e-mail address of the corresponding user. It is also directly visible in the detailed view of your CI/CD build. Depending on how a job is triggered, SAP Continuous Integration and Delivery stores one of the following:

    -   The e-mail address of the SAP BTP user, if the job is triggered manually using the API or UI

    -   The e-mail address of the commit author, if the job is triggered from the source code repisotory using a webhook

        SAP Continuous Integration and Delivery is not the primary storage location of the e-mail addresses. The e-mail addresses are taken from the source code management system or an identity provider \(IdP\) connected to your SAP BTP subaccount.


-   **Usernames and e-mail addresses from commit events**

    When fetching the sources from your repository, usernames and e-mail addresses of the commit authors will be obtained. However, this data is stored only temporarily for the duration of the job execution. Once the pipeline run is completed, this data will be deleted.


<a name="loio499058c8dabd4ebba7218a90bffdd901"/>

<!-- loio499058c8dabd4ebba7218a90bffdd901 -->

## Information Retrieval

The user information processed by SAP Continuous Integration and Delivery can be retrieved the following way for the two use cases:

-   **E-mail addresses of users who triggered a build**

    The e-mail address of the user who triggered a build can be retrieved in the following manner:

    -   Via the UI by navigating to the detail view of your build

    -   Via the API by using the `/{version}/jobs/{jobReference}/builds` endpoint. See SAP Continuous Integration and Delivery service on [SAP API Business Hub](https://api.sap.com/api/CloudCiApiSuite/overview).


-   **User names and e-mail addresses from commit events**

    The build logs may contain personal data in the form of user names and e-mail addresses. They can be retrieved in the following manner:

    -   Via the UI by navigating to the detail view of your build.

        To access the build log data, select the build tile of the corresponding build and choose <span class="SAP-icons-V5"></span> \(Actions\)** \> *Show Full Log* in the *Build Stages* view. See [Running and Monitoring CI/CD Jobs](https://help.sap.com/viewer/SAP-Cloud-Platform-Continuous-Integration-and-Delivery/db8521cc85924f78b7e92b1ea69fdf94.html).

    -   Via the API by using the `/{version}/jobs/{jobReference}/builds/{buildReference}/log` endpoint. See SAP Continuous Integration and Delivery service on [SAP API Business Hub](https://api.sap.com/api/CloudCiApiSuite/overview).



<a name="loiob9bc56a3041a4d0fae2d6c98320fd787"/>

<!-- loiob9bc56a3041a4d0fae2d6c98320fd787 -->

## Deletion

The project administrator can delete builds together with their metadata, and therefore all personal data that is stored in SAP Continuous Integration and Delivery. See [Modify, Copy, and Delete Jobs](modify-copy-and-delete-jobs-21fd276.md).

By default, SAP Continuous Integration and Delivery stores builds and their logs for 7 days and keeps a maximum of 50 builds. You can adjust the maximum values in the pipeline configuration to a maximum of 28 days and 99 builds. See [Create a Job](create-a-job-d748920.md). If these numbers are exceeded, the oldest builds and their logs are deleted automatically.

If you disable SAP Continuous Integration and Delivery in the SAP BTP cockpit, all data that belongs to your account is deleted automatically. Audit log data is automatically deleted after a defined retention period. For information, see [Audit Log Retention for the Cloud Foundry Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/adaefa64228e49ddbe40c15f63a4f74b.html).

<a name="loio3845cad34e294213be4f2335ceb0a05d"/>

<!-- loio3845cad34e294213be4f2335ceb0a05d -->

## Data Export

There are two options to export your data from SAP Continuous Integration and Delivery in a standard \(JSON\) format:

-   The recommended way to retrieve data is to raise a customer incident and request a copy of your data. See [Support, Feature Requests, and Feedback](support-feature-requests-and-feedback-6e10ad4.md).

-   If you prefer to export your data on your own, you can utilize SAP Continuous Integration and Delivery's REST API. You can use it to access and download all your data. Since there is no single API endpoint to export your whole data, we recommend you to implement a small script to automate the sequence of API calls needed to retrieve the required data. For more information, see [Enabling the API Usage](enabling-the-api-usage-1aedc23.md) and [SAP API Buisness Hub](https://api.sap.com/api/CloudCiApiSuite/overview).


Due to security reasons, the secrets of credentials are not included in the exported data.

<a name="loio99f4bba1621247c68aac6e6a7bfb0203"/>

<!-- loio99f4bba1621247c68aac6e6a7bfb0203 -->

## Glossary

See [Glossary for Data Protection and Privacy](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/a57e0ab085404ef483a8c99e50cbf91e.html).

