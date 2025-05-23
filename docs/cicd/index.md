# SAP Continuous Integration and Delivery

-   [What Is SAP Continuous Integration and Delivery](what-is-sap-continuous-integration-and-delivery-618ca03.md)
-   [What's New for SAP Continuous Integration and Delivery](what-s-new-for-sap-continuous-integration-and-delivery-8d3bf2e.md)
-   [Regional Availability](regional-availability-7510e25.md)
-   [Concepts](concepts-707017c.md)
-   [Initial Setup](initial-setup-719acaf.md)
    -   [Enabling the Service](enabling-the-service-c8ed09d.md)
    -   [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md)
    -   [Enabling the API Usage](enabling-the-api-usage-1aedc23.md)
-   [Configuration](configuration-39d0c2f.md)
    -   [Configuring Jobs](configuring-jobs-e293286.md)
        -   [Configure a Cloud Foundry Environment Job](configure-a-cloud-foundry-environment-job-6bd27c0.md#loio6bd27c07ee3b428f9ad5a2e89084f3a3)
        -   [Configure an SAP Fiori in the Neo Environment Job](configure-an-sap-fiori-in-the-neo-environment-job-619a864.md#loio619a864813584bd1a433cafac1fb0c1e)
            -   [\(Optional\) Configure the Deploy Credential](configure-an-sap-fiori-in-the-neo-environment-job-619a864.md#loio52bc22233ef84527bc409fbe748947b8)
        -   [Configure an SAP Fiori for the ABAP Platform Job](configure-an-sap-fiori-for-the-abap-platform-job-4c26bfb.md#loio4c26bfbeb6444805a933ca48a470b217)
            -   [\(Optional\) Configure the Additional Unit Test Stage](configure-an-sap-fiori-for-the-abap-platform-job-4c26bfb.md#loio642bcb08b27c4d7ab5008aa277225189)
        -   [Configure an SAP Integration Suite Artifacts Job](configure-an-sap-integration-suite-artifacts-job-3d5573f.md)
        -   [Configure a Kyma Runtime Job](configure-a-kyma-runtime-job-0700ecb.md)
        -   [Configuring Jobs in Your Repository](configuring-jobs-in-your-repository-af397b1.md)
            -   [Configure a Cloud Foundry Environment Job in Your Repository](configure-a-cloud-foundry-environment-job-in-your-repository-bfe48a4.md#loiobfe48a4b12ed41868f92fa564829f752)
            -   [Configure an SAP Fiori in the Neo Environment Job in Your Repository](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio4f6185c3282b4e998fd7d1b202b14615)
                -   [Enable the Build and Additional Unit Tests Stages](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio708413d4c586409489cbb17d1fbe1e5c)
                -   [\(Optional\) Configure the Deploy Credential](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio52bc22233ef84527bc409fbe748947b8)
                -   [\(Optional\) Integrate SAP Cloud Transport Management into Your Pipeline](configure-an-sap-fiori-in-the-neo-environment-job-in-your-repository-4f6185c.md#loio0b9c5d30aff3425c96a440dce60bd9c7)
            -   [Configure an SAP Fiori for the ABAP Platform Job in Your Repository](configure-an-sap-fiori-for-the-abap-platform-job-in-your-repository-a859560.md#loioa859560bca4149488f8e94e9c9a9adad)
            -   [Configure an SAP Integration Suite Artifacts Job in Your Repository](configure-an-sap-integration-suite-artifacts-job-in-your-repository-3daf56d.md)
            -   [Configure a Kyma Runtime Job in Your Repository](configure-a-kyma-runtime-job-in-your-repository-9f1c1e2.md)
            -   [Export Job Configuration Data](export-job-configuration-data-60a76d7.md)
        -   [Enhancing Jobs](enhancing-jobs-d581ab5.md)
            -   [Add Additional Commands to Stages](add-additional-commands-to-stages-c05a252.md)
            -   [Add Additional Credentials to Stages](add-additional-credentials-to-stages-af2d1a2.md)
            -   [Add Additional Variables to Stages](add-additional-variables-to-stages-74fe540.md)
            -   [Integrate Cloud Transport Management into Your Job](integrate-cloud-transport-management-into-your-job-a0f029b.md)
            -   [Enable Build Notifications](enable-build-notifications-de2a6e3.md)
            -   [Manage Timed Triggers for Jobs](manage-timed-triggers-for-jobs-3cd830e.md#loio3cd830ec08644e52b47cc3274732aacd)
                -   [Cron Schedule Syntax](manage-timed-triggers-for-jobs-3cd830e.md#loiob38912b3e5a54e04a6d32c58357f1d1b)
        -   [Configure a Multi-Branch Job](configure-a-multi-branch-job-d52d3ca.md)
        -   [Modify, Copy, and Delete Jobs](modify-copy-and-delete-jobs-21fd276.md)
        -   [Lifespan of Pipeline Versions](lifespan-of-pipeline-versions-8e596c0.md)
    -   [Administrating Repositories](administrating-repositories-1d68ad9.md)
        -   [Add a Repository](add-a-repository-fc55872.md)
        -   [\(Optional\) Add a Corporate Git Repository](optional-add-a-corporate-git-repository-4b6ee9a.md)
        -   [Create Credentials for Private Repositories](create-credentials-for-private-repositories-1771e7f.md)
            -   [Create a Credential for a Private GitHub Repository](create-a-credential-for-a-private-github-repository-3a22831.md)
            -   [Create a Credential for a Private GitLab Repository](create-a-credential-for-a-private-gitlab-repository-3fc8453.md)
            -   [Create a Credential for a Private Azure Repos Repository](create-a-credential-for-a-private-azure-repos-repository-2bb0b32.md)
            -   [Create a Credential for a Private Bitbucket Server Repository](create-a-credential-for-a-private-bitbucket-server-repository-81294f0.md)
            -   [Create a Credential for a Private Bitbucket Cloud Repository](create-a-credential-for-a-private-bitbucket-cloud-repository-3d77e44.md)
    -   [Creating Webhooks](creating-webhooks-a273cff.md)
        -   [Add a Webhook in GitHub](add-a-webhook-in-github-090d4aa.md)
        -   [Add a Webhook in GitLab](add-a-webhook-in-gitlab-e452155.md)
        -   [Add a Webhook in Azure Repos](add-a-webhook-in-azure-repos-e3efb69.md)
        -   [Add a Webhook in Bitbucket Server](add-a-webhook-in-bitbucket-server-7278c86.md)
        -   [Add a Webhook in Bitbucket Cloud](add-a-webhook-in-bitbucket-cloud-ef67342.md)
    -   [Creating Credentials](creating-credentials-6658c81.md)
    -   [Using the API](using-the-api-9819fa1.md)
    -   [Security Configuration](security-configuration-f1c10f4.md)
        -   [Manage Allowed Spaces](manage-allowed-spaces-0181fc5.md)
        -   [Configure a Credential List](configure-a-credential-list-907b44a.md)
-   [Using SAP Continuous Integration and Delivery](using-sap-continuous-integration-and-delivery-2f1072d.md)
    -   [Accessing the Service](accessing-the-service-9cec395.md)
    -   [Running and Monitoring CI/CD Jobs](running-and-monitoring-ci-cd-jobs-db8521c.md)
    -   [Supported Tools](supported-tools-5949283.md)
-   [Troubleshooting and Support](troubleshooting-and-support-3421448.md)
    -   [Troubleshooting](troubleshooting-b5d82cd.md)
        -   [Issues Related to Enabling the Service](issues-related-to-enabling-the-service-d617e97.md)
        -   [Issues Related to Accessing the Service](issues-related-to-accessing-the-service-58003b8.md)
        -   [Issues Related to A Build](issues-related-to-a-build-c3919d7.md)
    -   [Support, Feature Requests, and Feedback](support-feature-requests-and-feedback-6e10ad4.md)
-   [Security](security-1b3b53e.md)
    -   [Security Recommendations](security-recommendations-42fa013.md)
    -   [Identity and Access Management](identity-and-access-management-bb2cd0a.md#loiobb2cd0a57fc54525888a6988a7ab704c)
        -   [Git Repositories](git-repositories-8a57562.md#loio8a57562c7d2d4f7db53a29b2f1e146e9)
    -   [Network and Communication Security](network-and-communication-security-94a75a4.md#loio94a75a40f62c4cccaafec21a97a7ffdc)
        -   [Git Repositories](git-repositories-2568687.md#loio25686879a3a740ec9c5d01c6070c3610)
            -   [Internet-facing Git Repository Services](git-repositories-2568687.md#loio7e5df222287c4af98e06bd6df8c2a110)
            -   [Corporate Git Repositories](git-repositories-2568687.md#loiocc4fff321b5d486c943afe8f7fb5513f)
            -   [Repository Webhooks](git-repositories-2568687.md#loioeba30218adee444eb00e6819dbf4dae7)
        -   [Credential Handling](credential-handling-e26a096.md#loioe26a096409e344ad8a134a6eb39d8ee9)
            -   [Credential Scope](credential-handling-e26a096.md#loiob11b3021340746358e6a555a9d2a1fb9)
            -   [Preventing Credential Leakage](credential-handling-e26a096.md#loio649880c2cfcc43baa9341fb005af584e)
            -   [Security Recommendations](credential-handling-e26a096.md#loioa7c70ccc9ec24bb1bd2630cde60dedf9)
        -   [API Usage](api-usage-ae2f233.md#loioae2f233139df4697b48a589a936b6226)
    -   [Data Storage Security](data-storage-security-b19335f.md#loiob19335f16e934be69aea07fdd2d74003)
        -   [Build Logs](data-storage-security-b19335f.md#loio4721150df6b0415285ed6abc1b7044b8)
    -   [Audit Logging](audit-logging-a19a03a.md)
    -   [Data Protection and Privacy](data-protection-and-privacy-ece763a.md#loioece763abc3fb4ca39c19f908978cb69c)
        -   [Processing of Personal Data](data-protection-and-privacy-ece763a.md#loioca8276194a65407b80bae43b4faece47)
        -   [Information Retrieval](data-protection-and-privacy-ece763a.md#loio499058c8dabd4ebba7218a90bffdd901)
        -   [Deletion](data-protection-and-privacy-ece763a.md#loiob9bc56a3041a4d0fae2d6c98320fd787)
        -   [Source Repositories and Personal Data](data-protection-and-privacy-ece763a.md#loioce0c1c803600447dbcf41c891cb9fa0f)
        -   [Data Export](data-protection-and-privacy-ece763a.md#loio3845cad34e294213be4f2335ceb0a05d)
        -   [Glossary](data-protection-and-privacy-ece763a.md#loio99f4bba1621247c68aac6e6a7bfb0203)
-   [Accessibility Features in SAP Continuous Integration and Delivery](accessibility-features-in-sap-continuous-integration-and-delivery-e1d3af4.md)
-   [<TEST\>Configure a Cloud Foundry Environment Job](test-configure-a-cloud-foundry-environment-job-6b64174.md)

