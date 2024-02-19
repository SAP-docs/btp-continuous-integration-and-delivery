<!-- loioa19a03a28b904855a9bfabfe38086d5d -->

# Audit Logging

SAP Continuous Integration and Delivery uses the built-in audit logging functions in SAP BTP.

The following information is recorded and stored in the SAP Audit Log service instance of your subaccount:

-   Creation and deletion of jobs and all modifications of a job resource
-   Creation and deletion of credentials and all modifications of a credential resource
-   Creation and deletion of repositories and all modifications of a repository resource
-   Modifications to the allowed spaces list \(see [Manage Allowed Spaces](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/0181fc51422e459fa79e717d433f94d4.html?version=Cloud#manage-allowed-spaces)\)
-   Failed authorization checks

The audit logs can be accessed via the Audit Log Retrieval API or viewed using the SAP Audit Log Viewer service. See [Audit Logging in the Cloud Foundry Environment](https://help.sap.com/products/BTP/65de2977205c403bbc107264b8eccf4b/f92c86ab11f6474ea5579d839051c334.html?version=Cloud).



<a name="loioa19a03a28b904855a9bfabfe38086d5d__section_yvv_nht_4xb"/>

## Audit Logging for Additional Commands

With the Additional Commands feature, users with administrator role can define arbitrary command sequences that will be executed before or after a given stage. See [Additional Commands](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/c05a2522c90a40069ead07bd81df37ab.html?version=Cloud). Since the additional commands belong to the job resource, all related changes are reflected in the audit logs.

Due to length limitations and for the sake of simplicity, administrators could decide to add references to more complex scripts located in Git repositories. However, the SAP Continuous Integration and Delivery audit log does not cover changes in scripts located in Git repositories. Changes to such scripts must be logged separately, for example, through the Git commit history.

