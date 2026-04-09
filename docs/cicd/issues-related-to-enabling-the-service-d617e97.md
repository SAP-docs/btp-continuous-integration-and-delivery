<!-- loiod617e970056747568e32e907d8316b4a -->

# Issues Related to Enabling the Service

Learn how to handle issues related to the enablement of SAP Continuous Integration and Delivery.

Depending on what kind of issue you are facing, expand one of the following sections for more information.



## Missing *Continuous Integration & Delivery* Tile in Service Marketplace



### Symptom

You want to enable SAP Continuous Integration and Delivery as described in [Enabling the Service](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/enabling-service?language=en-US). However, you can't view the Continuous Integration & Delivery tile in the Service Marketplace.



### Solution

Make sure that you have one of the following licenses:

-   If you’re a **customer**, you need to use the CPEA \(Cloud Platform Enterprise Agreement\) license model. See [What Is the Consumption-Based Commercial Model](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/7047eb4a15a84ac7be3c8612179e6d1f.html).
-   If you’re a **partner**, you need a Test, Demonstration, and Development License. See [SAP Partner Licensing Services](https://partneredge.sap.com/en/partnership/licenses/tdd.html).




## Service Instance Creation Failed



### Symptom

You want to create a service instance of SAP Continuous Integration and Delivery in a Cloud Foundry space. The creation of the service instance fails, and you get the following error message:

> ### Output Code:  
> ```
> Creation Failed
> 
> Couldn’t create an instance of service 'Continuous Integration & Delivery' with plan 'default'.
> 
> .
> Service broker error: Service broker cicd-service-broker failed with: Binding creation was rejected: The tenant ‘<TENANT_ID>’ is not subscribed to the SAP Continuous Integration and Delivery Service.
> 
> ```



### Solution

Before creating an SAP Continuous Integration and Delivery service instance, you need to subscribe to the service as described in [Enabling the Service](enabling-the-service-c8ed09d.md).

> ### Note:  
> Creating a service instance of SAP Continuous Integration and Delivery in a Cloud Foundry space is only necessary if you want to use the service API. See [Enabling the Service](enabling-the-service-c8ed09d.md). If you want to use the application, instead, following the steps in [Enabling the Service](enabling-the-service-c8ed09d.md) is sufficient.

