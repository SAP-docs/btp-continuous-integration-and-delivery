<!-- loio42fa013e0bb74506abc6a606def095b7 -->

# Security Recommendations

These recommendations help you evaluate the security of the configuration of SAP Continuous Integration and Delivery.

> ### Note:  
> As part of the [cloud shared responsibility model](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fsupport.sap.com%2Fen%2Fmy-support%2Ftrust-center%2Ftools-documentation.html%3FanchorId%3Dcde4601b0afb44f79a790b599c2cd8b2), you're responsible for determining if any of these recommendations are relevant to your environment and to what extent.
> 
> The security recommendations are provided as a courtesy, without a warranty, and may be subject to change. For more information, see the [disclaimer](https://help.sap.com/docs/disclaimer).

SAP Continuous Integration and Delivery comes with secure default configurations wherever this is possible. However, you might want to review some settings and adjust them to your particular use case and corporate policies.

See also [Explanation of Table Headings](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/explanation-of-table-headings?version=Cloud).

****


<table>
<tr>
<th valign="top">

Service

</th>
<th valign="top">

Priority

</th>
<th valign="top">

Secure Operations Map

</th>
<th valign="top">

Topic

</th>
<th valign="top">

Default Setting or Behavior

</th>
<th valign="top">

Recommendation

</th>
<th valign="top">

More Information

</th>
<th valign="top">

Last Update

</th>
<th valign="top">

Index

</th>
</tr>
<tr>
<td valign="top">

Continuous Integration & Delivery

</td>
<td valign="top">

Recommended

</td>
<td valign="top">

Security Monitoring and Forensics

</td>
<td valign="top">

Audit Logs

</td>
<td valign="top">

SAP Continuous Integration and Delivery uses the SAP Audit Log service in the Cloud Foundry environment for audit logging. The retention time is 90 days.

</td>
<td valign="top">

To keep audit entries longer than 90 days, download and archive the audit log entries regularly.

See also [BTP-AUD-0001](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-AUD-0001&version=Cloud).

</td>
<td valign="top">

[Audit Logging in the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/audit-logging-in-cloud-foundry-environment).

</td>
<td valign="top">

2024-01-26

</td>
<td valign="top">

BTP-CID-0001

</td>
</tr>
<tr>
<td valign="top">

Continuous Integration & Delivery

</td>
<td valign="top">

Critical

</td>
<td valign="top">

Client Security

</td>
<td valign="top">

REST API Service Keys

</td>
<td valign="top">

Service keys serve as authentication mechanism for granting authorized access to the REST API of SAP Continuous Integration and Delivery. Service keys for REST API service instances don't expire.

</td>
<td valign="top">

Periodically rotate your service keys for the SAP Continuous Integration and Delivery REST API to mitigate the effects of a potential exposure.

See also [BTP-UAA-0004](https://help.sap.com/docs/btp/sap-btp-security-recommendations-c8a9bb59fe624f0981efa0eff2497d7d/sap-btp-security-recommendations?seclist-index=BTP-UAA-0004&version=Cloud).

</td>
<td valign="top">

[Enabling the API Usage](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/optional-enabling-api-usage?language=en-US) 

</td>
<td valign="top">

2024-01-26

</td>
<td valign="top">

BTP-CID-0002

</td>
</tr>
<tr>
<td valign="top">

Continuous Integration & Delivery

</td>
<td valign="top">

Recommended

</td>
<td valign="top">

Roles and Authorizations

</td>
<td valign="top">

Administrator Authorizations

</td>
<td valign="top">

If the Administrator role is assigned, a user has more privileges, including the management of credentials within the service.

</td>
<td valign="top">

To keep the number of administrators as small as possible, regularly check which users have the Administrator role assigned and whether the additional authorizations are still required.

</td>
<td valign="top">

[Assigning Roles and Permissions](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/assigning-roles-and-permissions?language=en-US&version=Cloud) 

</td>
<td valign="top">

2024-01-26

</td>
<td valign="top">

BTP-CID-0003

</td>
</tr>
<tr>
<td valign="top">

Continuous Integration & Delivery

</td>
<td valign="top">

Recommended

</td>
<td valign="top">

Roles and Authorizations

</td>
<td valign="top">

API Roles

</td>
<td valign="top">

REST API service instances grant authorizations corresponding to those of a user with the Administrator role.

</td>
<td valign="top">

Following the principle of least privilege, consider to create a REST API service instance with restricted authorizations corresponding to the Developer role.

</td>
<td valign="top">

[Enabling the API Usage](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/optional-enabling-api-usage?version=Cloud&language=en-US)

</td>
<td valign="top">

2024-01-26

</td>
<td valign="top">

BTP-CID-0004

</td>
</tr>
<tr>
<td valign="top">

Continuous Integration & Delivery

</td>
<td valign="top">

Recommended

</td>
<td valign="top">

Security Hardening

</td>
<td valign="top">

Credential List

</td>
<td valign="top">

For jobs with repository-based configuration, all credentials managed by SAP Continuous Integration and Delivery can be used within a build.

</td>
<td valign="top">

For jobs with repository-based configuration, users with the Administrator role should configure credential lists to define which credential can be used by a build.

</td>
<td valign="top">

[Configure a Credential List](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/optional-configure-credential-list?version=Cloud&language=en-US&q=repository-based%20) 

</td>
<td valign="top">

2024-01-26

</td>
<td valign="top">

BTP-CID-0005

</td>
</tr>
</table>

