<!-- loioc13a897bd1b54ad4904c5ea298e382ea -->

# Integrate Change Request Management with SAP Solution Manager into Your CI/CD Pipeline

Add change management processes that are compliant with the Information Technology Infrastructure Library \(ITIL\) to your CI/CD pipeline and facilitate the synchronization of changes made both on-premise and on SAP BTP.

> ### Tip:  
> If you use Jenkins or plan to use it, have a look at the [**project "Piper"**](https://www.project-piper.io) scenario [Build and Deploy Hybrid Applications with Jenkins and SAP Solution Manager](https://www.project-piper.io/scenarios/changeManagement/), instead.

For a full overview of the different solutions SAP provides for CI/CD, see [SAP Solutions for Continuous Integration and Delivery](https://help.sap.com/viewer/8cacec64ed854b2a88e9a0973e0f97a2/Cloud/en-US/e9fa320181124fa9808d4446a1bf69dd.html).



<a name="loioc13a897bd1b54ad4904c5ea298e382ea__section_axw_kvh_lkb"/>

## Context

This scenario explains how to add Change Request Management to your CI/CD pipeline with an SAP Cloud Transport Management integration. For more information about Change Request Management with SAP Solution Manager, see [Change Request Management](https://help.sap.com/viewer/8b923a2175be4939816f0981b73856c7/LATEST/en-US/4c3acb82b50843b4e10000000a42189e.html).

The following graphic provides an overview about the interplay between continuous integration, SAP Cloud Transport Management, and Change Request Management:

  
  
**Detailed Procedure When Combining CI and Change Request Management**

![Detailed Procedure When Combining CI and Change Request Management](images/ChaRM_Scenario_Flow_a280a2b.png "Detailed Procedure When Combining CI and Change Request
						Management")

The interplay comprises the following steps:

1.  As a result of the continuous intgeration build, a [multitarget application \(MTA\)](https://www.sap.com/documents/2016/06/e2f618e4-757c-0010-82c7-eda71af511fa.html) is created, uploaded to SAP Cloud Transport Management, and attached to a new transport request in the import queue of the PRE-PROD node.

2.  The Transport Management transport requests are visible in SAP Solution Manager.

3.  The developer assigns the request to a change document.

4.  The developer approves the change document, which in the transport management service, triggers the import of the MTA into the PRE-PROD node.

5.  Through the import, the deployment of the MTA to the PRE-PROD subaccount is triggered.

6.  At the same time, the import forwards the transport request with the MTA to the PROD import queue in SAP Cloud Transport Management.

7.  This transport is also reflected in SAP Solution Manager, where the change document is transported to the PROD requests.

8.  The change manager approves the change document for production, which in the transport management service, triggers the import of the MTA into the PROD node.

9.  The import triggers the deployment of the MTA to the PROD subaccount.




<a name="loioc13a897bd1b54ad4904c5ea298e382ea__section_uwf_rvh_lkb"/>

## Prerequisites

-   You have enhanced your CI/CD pipeline with SAP Cloud Transport Management, as described in [Integrate SAP Cloud Transport Management into Your CI/CD Pipeline](integrate-sap-cloud-transport-management-into-your-ci-cd-pipeline-6b27ecd.md).

-   You have access to an SAP Solution Manager system in version 7.2 SP10 or higher.

-   You have configured Change Request Management with SAP Solution Manager, as described in [Configuring Change Request Management](https://help.sap.com/viewer/8b923a2175be4939816f0981b73856c7/7.2.10/en-US/55b5804ec50840bb947db20c899874b5.html).




<a name="loioc13a897bd1b54ad4904c5ea298e382ea__section_vww_xvh_lkb"/>

## Procedure

1.  From Setting up [SAP BTP TMS for Change Control Management](https://help.sap.com/viewer/8b923a2175be4939816f0981b73856c7/LATEST/en-US/6e32450a4b1341f5917c84219eff51a9.html), execute the tasks in the following sections:

    -   Set-up Steps in the Change Control Management

    -   Set-up Steps in the Landscape Management Database \(LMDB\)

    -   Set-up Steps in the Solution Administration \(SLAN\)


2.  To prevent manual imports into the nodes that you want to be controlled by Change Request Management, set the flag *Controlled by SAP Solution Manager* in their configurations in SAP Cloud Transport Management.




<a name="loioc13a897bd1b54ad4904c5ea298e382ea__section_dlp_hwh_lkb"/>

## Result

SAP Cloud Transport Management is now visible in the landscape view of SAP Solution Manager. If you use your continuous delivery pipeline to upload an MTA \(or another content archive\) to the transport management service, the content is now attached to the import queue of the first node that is controlled by SAP Cloud Transport Management.

In SAP Solution Manager, you can now search for transport requests that are waiting in the import queue and assign them to the correct change request in the change control management. Whenever in a change request, the change reaches an appropriate state \(for example, *To be tested*\), you can trigger its import into the node.

