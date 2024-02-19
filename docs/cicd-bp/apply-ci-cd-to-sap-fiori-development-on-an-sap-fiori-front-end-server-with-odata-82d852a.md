<!-- loio82d852a5d083461c90ff54b453f1f390 -->

# Apply CI/CD to SAP Fiori Development on an SAP Fiori Front-End Server with OData

Implement a CI/CD pipeline for the development of SAPUI5/SAP Fiori applications on an SAP Fiori front-end server with OData.

> ### Tip:  
> If you use Jenkins or plan to use it, have a look at [Project "Piper"](https://www.project-piper.io/scenarios/upload-to-transportrequest/Readme/), instead.

For a full overview of the different solutions SAP provides for CI/CD, see [SAP Solutions for Continuous Integration and Delivery](https://help.sap.com/viewer/8cacec64ed854b2a88e9a0973e0f97a2/Cloud/en-US/e9fa320181124fa9808d4446a1bf69dd.html).



<a name="loio82d852a5d083461c90ff54b453f1f390__section_up1_czh_prb"/>

## Context

This procedure allows you to implement a CI/CD pipeline to develop a SAPUI5/SAP Fiori application locally and to run it on an SAP Fiori front-end server using an OData service.

The **SAP Fiori front-end server** is an add-on product for SAP NetWeaver Application Server for ABAP \(AS ABAP\). See [SAP Fiori front-end server](https://help.sap.com/viewer/1f0c69c2f76b445c98b89cc1f41d7ae4/5_OVERVIEW/en-US/6cb9b4c90de345ca9a6182049ee6f8da.html).

The **OData service**is an interface of the Change and Transport System \(CTS\) with which you can manage transport requests and upload your SAPUI5/SAP Fiori application.



<a name="loio82d852a5d083461c90ff54b453f1f390__section_ivp_5c1_sjb"/>

## Prerequisites

-   You have an SAPUI5/SAP Fiori application as source in a source code management system of your choice.

-   You have installed the [SAP component SAP\_UI 7.53](https://help.sap.com/viewer/6f3c61a7a5b94447b80e72f722b0aad7/202009.002/en-US/35828457ed26452db8d51c840813f1bb.html) or higher on your ABAP system.

-   You have enabled the OData service to load data to the [SAPUI5 ABAP repository](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html).

-   You have the [S\_DEVELOP authorization](https://sapui5.hana.ondemand.com/#/topic/a883327a82ef4cc792f3c1e7b7a48de8.html) to perform operations in your SAPUI5 ABAP repository.




<a name="loio82d852a5d083461c90ff54b453f1f390__section_yym_vc1_sjb"/>

## Procedure

Use the following procedure to create a pipeline in a CI/CD tool of your choice. The pipeline consists of two distinct parts: a **continuous integration** process and an **ABAP life-cycle management** process.

It uses **npm** as a

-   package manager to set up the required environment on your build system,

-   task runner to run and automate the pipeline steps.


For more information, see [npm](https://docs.npmjs.com/).

> ### Recommendation:  
> Use the containerization platform **Docker** to avoid scrambling your build system. See [Docker](https://docs.docker.com/).



### Continuous Integration

![](images/Fiori_on_ABAP_-_CI_Process_d0b1f6b.png)

The continuous integration process comprises the following steps:

-   The **Build** step, which builds your SAPUI5/SAP Fiori application.

-   The **Test** step, which runs tests on your SAPUI5/SAP Fiori application.




### Preparing Your Build System

To prepare your build system, proceed as follows:

1.  If you don't want to use Docker, install the following dependencies on your build machine:

    -   [Node.js](https://nodejs.org/)
    -   [CM Client](https://github.com/SAP/devops-cm-client)

2.  Create a `package.json` file in the top-level directory of your project, if it doesn't exist yet. See [package.json](https://docs.npmjs.com/cli/v7/configuring-npm/package-json).

    Add the following lines:

    ```
    {
       ...
       "scripts": {
          "lint": "eslint webapp",
          "uiveri5": "uiveri5",
          "test": "npm run lint && npm run uiveri5",
          "build": "ui5 build --clean-dest",
          "build-self-contained": "ui5 build self-contained -a --clean-dest",
          "start": "ws --compress -d dist"
       },
        ...
       "devDependencies": {
          "@ui5/cli": "^2.11.2",
          "eslint": "^7.29.0",
          "local-web-server": "^4.2.1",
       }
       ...
    }
    ```




### Build

To build your SAPUI5/SAP Fiori application, proceed as follows:

-   In your shell, execute the following command:

    ```
    docker run -v "${PWD}":/project --workdir "/project" node:latest bash -c "npm run-script build"
    ```

-   If you don't use Docker, run the npm script in your shell:

    ```
    npm run-script build
    
    ```




### Test

To run tests on your SAPUI5/SAP Fiori application, proceed as follows:

-   In your shell, execute the following command:

    ```
    docker run -v "${PWD}":/project --workdir "/project" node:latest bash -c "npm run-script test"
    
    ```

-   If you don't use Docker, run the npm script in your shell:

    ```
    npm run-script test
    
    ```

    The test script executes **lint** and **uiVeri5** tests.

    > ### Note:  
    > For more information about how to create a uiVeri5 test, see [UIVeri5](https://github.com/SAP/ui5-uiveri5). You can, however, substitute UIVeri5 tests with any other automated tests you have implemented.




### The ABAP Life-Cycle Management

Run the following steps to deliver and release your SAPUI5/SAP Fiori application:

-   The **Upload** step, which uploads your SAPUI5/SAP Fiori application into a transport request of your developer system.

-   The **Release & Export** step, which releases and exports your transport request to be imported into the next system of the transport route.

-   The **Import** step, which imports your exported transport request into the next system of the transport route.

    For more information, see [Transport Requests in a Typical ABAP System Setup](https://help.sap.com/viewer/Continuous-Integration-and-Delivery-Best-Practices-Guide/3713b07025274c2fbc95467627921a7a.html)




### Upload

![](images/Fiori_on_ABAP_-_Upload_fa0d407.png)

To upload a file into your transport request, proceed as follows:

1.  Create a transport request, if it is not already existing:

    -   Use the **CM Client** if you want to automate the creation. See [CM Client](https://github.com/SAP/devops-cm-client).

        -   In your shell, execute the following command:

            ```
            docker run ppiper/cm-client:latest cmclient --endpoint "<ENDPOINT>" --user "<USER>" --password "<PASSWORD>" --backend-type CTS  create-transport --target-system "<TARGET SYSTEM>" --transport-type "<TRANSPORT TYPE>"  --owner "<OWNER>" --description "<DESCRIPTION>"
            
            ```

        -   Without Docker, run the CM Client in your shell:

            ```
            cmclient --endpoint "<ENDPOINT>" --user "<USER>" --password "<PASSWORD>" --backend-type CTS  create-transport --target-system "<TARGET SYSTEM>" --transport-type "<TRANSPORT TYPE>"  --owner "<OWNER>" --description "<DESCRIPTION>"
            ```


    -   Use the [Transport Organizer Web UI](https://help.sap.com/viewer/05c12df5b54849c49940a14bc089d8b4/2.0/en-US/098061d3d3b04e69be4a30e90bdc7458.html) of the **SAP Transport Management System** if you want to manually create the transport request.


2.  Use **SAP Fiori Tools** to upload your SAPUI5/SAP Fiori application. See [SAP Fiori Tools](https://www.npmjs.com/package/@sap/ux-ui5-tooling).

    -   In your shell, execute the following command:

        ```
        
        docker run --env ABAP_USER="<USER>" --env ABAP_PASSWORD="<PASS>" -v "${PWD}":/project --workdir "/project" node:latest bash -c "npm run-script upload -- --noConfig -f -y --username ABAP_USER --password ABAP_PASSWORD --url <URL_ENDPOINT> --client <CLIENT> --transport <TRANSPORT_ID> --package <PACKAGE> --name <APP_NAME> --description \"<DESCRIPTION>\""
        
        ```

    -   Without Docker, run the npm script in your shell:

        ```
        export ABAP_USER=<USER> 
        export ABAP_PASSWORD=<PASS>
        npm run-script upload -- --noConfig -f -y --username ABAP_USER --password ABAP_PASSWORD --url <URL_ENDPOINT> --client <CLIENT> --transport <TRANSPORT_ID> --package <PACKAGE> --name <APP_NAME> --description "<DESCRIPTION>"
        
        ```


    For more information about the command and its parameters, see [fiory deploy](https://www.npmjs.com/package/@sap/ux-ui5-tooling#fiori-deploy---performs-the-deployment-of-the-application-into-an-abap-system).


![](images/Fiori_on_ABAP_-_Release_and_Import_9c3ff98.png)



### Release & Export

To deliver and release your SAPUI5/SAP Fiori application, use SAP Logon and proceed as follows:

1.  In SAP Logon, open the transaction `stms`.

2.  Choose *Transport Organizer Web UI*.

3.  Select your transport request and choose *Release*.




### Import

To import your transport request into the following system, use SAP Logon and proceed as follows:

1.  In SAP Logon, open the transaction `stms`.

2.  Choose *Import Overview*.

3.  Choose your target system and choose *Display Import Queue*.

4.  To import the waiting request, select it and choose *OK*.




<a name="loio82d852a5d083461c90ff54b453f1f390__section_fvj_zpx_tjb"/>

## Result

You have combined the ABAP life-cycle management with a basic CI pipeline, which you can enhance according to your needs.

> ### Note:  
> This guide also provides procedures to enhance your finished CI/CD pipelines. See [Procedures for CI/CD Pipelines](procedures-for-ci-cd-pipelines-e49a97d.md).

