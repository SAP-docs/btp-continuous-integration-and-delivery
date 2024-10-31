<!-- loioe26a096409e344ad8a134a6eb39d8ee9 -->

# Credential Handling

This section contains information about the security and compliance aspects of credentials supplied to SAP Continuous Integration and Delivery.

SAP Continuous Integration and Delivery provides secure authentication for connections to Git repositories and other SAP BTP services. To manage access to these services, it is important to provide credentials for secure authentication. To protect this sensitive data, credentials are encrypted immediately after being created. Credentials are securely stored in encrypted form in an internal credential store. SAP Continuous Integration and Delivery cannot use one-way hashes to encode credentials, because, when requested by the pipeline, they need to be restored into their original form. However, neither the UI nor the API provide access to plain text credentials.

<a name="loiob11b3021340746358e6a555a9d2a1fb9"/>

<!-- loiob11b3021340746358e6a555a9d2a1fb9 -->

## Credential Scope

With SAP Continuous Integration and Delivery, the scope of credentials is not limited to specific jobs. Credentials stored in a particular service subscription can be used in all jobs within the subscription.

Credentials stored in one service subscription can be directly used by all users of this subscription. Users with the administrator role can create, edit, and use credentials when creating new jobs. Users with the developer role can trigger builds that use credentials for authentication.

> ### Recommendation:  
> From a security perspective, it is strongly recommended that you do not use an SAP Continuous Integration and Delivery subscription on company or department level, but rather have one subscription per team.

As described in the previous section, SAP Continuous Integration and Delivery securely stores credentials at rest and uses them when the pipeline is running. Thus, during a pipeline run, also users with write access to the connected repository can indirectly use the credentials. You can find out more about how to mitigate potential security risks implied by SAP Continuous Integration and Delivery pipeline credentials in the next chapter.

<a name="loio649880c2cfcc43baa9341fb005af584e"/>

<!-- loio649880c2cfcc43baa9341fb005af584e -->

## Preventing Credential Leakage



To protect credentials from malicious and unauthorized use, SAP Continuous Integration and Delivery includes a role-based security model.



<a name="loio649880c2cfcc43baa9341fb005af584e__section_n3z_vlq_gwb"/>

## Implications from Roles and Permissions

As users with the administrator role have access to more priviledged functions, they can quite easily uncover credentials in plain text again. For instance, it is possible that a malicious user with administrator role could create a mock repository with a fraudulent endpoint \(`Clone URL`\). Such an endpoint could be a server that allows to observe incoming requests. If a basic authentication credential is added to the mock repository, SAP Continuous Integration and Delivery will send the authentication requests to the fraudulent endpoint, possibly revealing the credential to the malicious user.

> ### Remember:  
> All users with the administrator role can use and potentially read credentials. Therefore, please consider credentials added to SAP Continuous Integration and Delivery as shared credentials for all users with the administrator role.

User permissions in the associated Git repositories also affect credential security. Even users with only write access to a connected repository could gain access to the credentials used in pipeline runs. For more information, see [Identity and Access Management](identity-and-access-management-bb2cd0a.md#loiobb2cd0a57fc54525888a6988a7ab704c).



<a name="loio649880c2cfcc43baa9341fb005af584e__section_tbj_lmq_gwb"/>

## Credentials in Logs

SAP Continuous Integration and Delivery has measures in place to prevent credential exposure in pipeline build logs. However, parts of a job \(for example, build process or test execution\) allow a high degree of freedom to add additional pipeline-specific coding.

SAP Continuous Integration and Delivery adheres to a shared responsibilty model, meaning that the customer maintains some responsibility for the logged content. Please share the following portions of the security responsibilities to prevent credentials ending up in build logs:

-   Ensure that your source code and build scripts do not write credentials in plain text into your build logs.

-   Don't run bash scripts in debug mode \(`set -x`\) and don't print the environment.

-   Ensure that no additional tools and libraries log credentials.




<a name="loio649880c2cfcc43baa9341fb005af584e__section_kcw_ylq_gwb"/>

## Supply Chain Attacks

Using additional open-source components like libraries and their dependencies within your CI/CD pipeline \(for example, during the Build or Additional Unit Test stage\), may make your CI/CD pipeline vulnerable to open-source supply chains attacks. If attackers manage to insert malicious code into these components, credentials that are available to the pipeline could be leaked.

For more information, see SAP blog [Attacks on Open Source Supply Chains: How Hackers Poison the Well](https://blogs.sap.com/2020/06/26/attacks-on-open-source-supply-chains-how-hackers-poison-the-well/).



<a name="loio649880c2cfcc43baa9341fb005af584e__section_fbz_mgk_zzb"/>

## Credential Lists

If you configure SAP Continuous Integration and Delivery jobs in your repository, by default, all credentials defined in the service are passed to the [build](concepts-707017c.md#loio707017c681aa4bc09d0279f08115dcae__section_dxw_cp3_qnb). By configuring a credential list, however, you can specify which credentials are passed. See [Configure a Credential List](configure-a-credential-list-907b44a.md).

<a name="loioa7c70ccc9ec24bb1bd2630cde60dedf9"/>

<!-- loioa7c70ccc9ec24bb1bd2630cde60dedf9 -->

## Security Recommendations

We strongly recommend that you put the following operational countermeasures in place when handling credentials:

-   Use a technical user instead of your personal credentials.

-   Only provide minimal privileges for technical users.

-   Restrict write access to your source code repository only to trusted contributors of the project.

-   Secure your source code repository with state of the art security techniques, for example, multi-factor authentication.

    The source code repository plays a key role in SAP Continuous Integration and Delivery. You can find useful information on how to secure each source code repository supported by SAP Continuous Integration and Delivery on the Internet.

-   Apply the four-eyes principle and make sure each commit is reviewed by someone who is not the commit author.

-   Rotate credentials used in your SAP Continuous Integration and Delivery jobs regularly.

    SAP Continuous Integration and Delivery allows you to change credentials at any time without affecting the already running builds. Before changing your credentials, please verify that they are valid for the corresponding Git source repository or SAP BTP service.

-   Configure a credential list to specify which credentials to pass to the build. See [Configure a Credential List](configure-a-credential-list-907b44a.md).


