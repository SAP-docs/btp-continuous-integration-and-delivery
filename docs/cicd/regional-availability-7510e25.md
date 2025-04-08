<!-- loio7510e254d8384465a0a185ac59ebf723 -->

# Regional Availability

Get an overview of the regional availability of the service application and build execution components.



<a name="loio7510e254d8384465a0a185ac59ebf723__section_kgt_n31_ybc"/>

## Context

SAP Continuous Integration and Delivery consists of two different components:

-   The **application** comprises the user interface of the service as well as the data of the jobs and credentials created, and the repositories added. This data is at rest and is not permanently passed to the build execution IaaS provider.

-   The **build execution** includes the [build functionality](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/concepts?version=Cloud#job-and-build). To execute builds, it accesses the job, credentials, and repository data stored in the application without persisting it.


The SAP Continuous Integration and Delivery application is linked to the service subscription in the SAP BTP cockpit. This means it operates in the same region and is hosted by the same IaaS provider as your subaccount on SAP BTP. However, to improve the resource availability and quality of the service, the build execution may be hosted by a different IaaS provider and/or in a different region.



<a name="loio7510e254d8384465a0a185ac59ebf723__section_p5g_kj1_ybc"/>

## Overview

**Regional Availability of SAP Continuous Integration and Delivery**


<table>
<tr>
<th valign="top">

Application IaaS Provider

</th>
<th valign="top">

Application Region

</th>
<th valign="top">

Application Region Name

</th>
<th valign="top">

Application Technical Key

</th>
<th valign="top">

Technical Key of Application IaaS Provider

</th>
<th valign="top">

Build Execution IaaS Provider

</th>
<th valign="top">

Build Execution Region Name

</th>
<th valign="top">

Technical Key of Build Execution IaaS Provider

</th>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

ca10

</td>
<td valign="top">

Canada \(Montreal\)

</td>
<td valign="top">

cf-ca10

</td>
<td valign="top">

ca-central-1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Canada \(Montreal\)

</td>
<td valign="top">

ca-central-1

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

ap20

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

cf-ap20

</td>
<td valign="top">

Australia East

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

ap-southeast-2

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

jp20

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

cf-jp20

</td>
<td valign="top">

Japan East

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

ap-northeast-1

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

ap21

</td>
<td valign="top">

Singapore

</td>
<td valign="top">

cf-ap21

</td>
<td valign="top">

Southeast Asia

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Asia Pacific \(Singapore\)

</td>
<td valign="top">

ap-southeast-1

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

ch20

</td>
<td valign="top">

Switzerland \(Zurich\) EU Access

</td>
<td valign="top">

cf-ch20

</td>
<td valign="top">

Switzerland North

</td>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

Switzerland \(Zurich\)

</td>
<td valign="top">

switzerlandnorth

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

us21

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

cf-us21

</td>
<td valign="top">

East US

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

us-east-1

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

sa30

</td>
<td valign="top">

KSA \(Dammam\)

</td>
<td valign="top">

cf-sa30

</td>
<td valign="top">

me-central2

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

KSA \(Dammam\)

</td>
<td valign="top">

me-central2

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

ap30

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

cf-ap30

</td>
<td valign="top">

australia-southeast1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Asia Pacific \(Sydney\)

</td>
<td valign="top">

ap-southeast-2

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

ap12

</td>
<td valign="top">

Asia Pacific \(Seoul\)

</td>
<td valign="top">

cf-ap12

</td>
<td valign="top">

ap-northeast-2

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Asia Pacific \(Seoul\)

</td>
<td valign="top">

ap-northeast-2

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

br20

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

cf-br20

</td>
<td valign="top">

Brazil South

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

South America \(São Paulo\)

</td>
<td valign="top">

sa-east-1

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

eu10

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
<td valign="top">

cf-eu10

</td>
<td valign="top">

eu-central-1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Europe \(Ireland\)

</td>
<td valign="top">

eu-west-1

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

eu11

</td>
<td valign="top">

Europe \(Frankfurt\) EU Access

</td>
<td valign="top">

cf-eu11

</td>
<td valign="top">

eu-central-1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Europe \(Ireland\)

</td>
<td valign="top">

eu-west-1

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

eu20

</td>
<td valign="top">

Europe \(Netherlands\)

</td>
<td valign="top">

cf-eu20

</td>
<td valign="top">

West Europe

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Europe \(Ireland\)

</td>
<td valign="top">

eu-west-1

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

eu30

</td>
<td valign="top">

Europe \(Frankfurt\)

</td>
<td valign="top">

cf-eu30

</td>
<td valign="top">

europe-west3

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Europe \(Ireland\)

</td>
<td valign="top">

eu-west-1

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

us10

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

cf-us10

</td>
<td valign="top">

us-east-1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

us-east-1

</td>
</tr>
<tr>
<td valign="top">

Microsoft Azure

</td>
<td valign="top">

us20

</td>
<td valign="top">

US West \(WA\)

</td>
<td valign="top">

cf-us20

</td>
<td valign="top">

West US 2

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

us-east-1

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

us30

</td>
<td valign="top">

US Central \(IA\)

</td>
<td valign="top">

cf-us30

</td>
<td valign="top">

us-central1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

US East \(VA\)

</td>
<td valign="top">

us-east-1

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

jp10

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

cf-jp10

</td>
<td valign="top">

ap-northeast-1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Japan \(Tokyo\)

</td>
<td valign="top">

ap-northeast-1

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

il30

</td>
<td valign="top">

Israel \(Tel Aviv\)

</td>
<td valign="top">

cf-il30

</td>
<td valign="top">

me-west1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Europe \(Ireland\)

</td>
<td valign="top">

eu-west-1

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

ap10

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

cf-ap10

</td>
<td valign="top">

ap-southeast-2

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Australia \(Sydney\)

</td>
<td valign="top">

ap-southeast-2

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

ap11

</td>
<td valign="top">

Asia Pacific \(Singapore\)

</td>
<td valign="top">

cf-ap11

</td>
<td valign="top">

ap-southeast-1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Asia Pacific \(Singapore\)

</td>
<td valign="top">

ap-southeast-1

</td>
</tr>
<tr>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

br10

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

cf-br10

</td>
<td valign="top">

sa-east-1

</td>
<td valign="top">

Amazon Web Services

</td>
<td valign="top">

Brazil \(São Paulo\)

</td>
<td valign="top">

sa-east-1

</td>
</tr>
<tr>
<td valign="top">

Google Cloud

</td>
<td valign="top">

in30

</td>
<td valign="top">

India \(Mumbai\)

</td>
<td valign="top">

cf-in30

</td>
<td valign="top">

asia-south1

</td>
<td valign="top">

Google Cloud

</td>
<td valign="top">

India \(Mumbai\)

</td>
<td valign="top">

asia-south1

</td>
</tr>
</table>

**Related Information**  


[Regions](https://help.sap.com/docs/btp/sap-business-technology-platform/regions?version=Cloud)

[Regions and API Endpoints Available for the Cloud Foundry Environment](https://help.sap.com/docs/btp/sap-business-technology-platform/regions-and-api-endpoints-available-for-cloud-foundry-environment?version=Cloud)

