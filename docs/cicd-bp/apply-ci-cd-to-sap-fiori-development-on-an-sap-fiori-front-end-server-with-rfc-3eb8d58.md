<!-- loio3eb8d5820728482389c69807117f174f -->

# Apply CI/CD to SAP Fiori Development on an SAP Fiori Front-End Server with RFC

Implement a CI/CD pipeline for the development of SAPUI5/SAP Fiori applications on an SAP Fiori front-end server with RFC.

> ### Tip:  
> If you use Jenkins or plan to use it, have a look at [**project "Piper"**](https://sap.github.io/jenkins-library/), instead.

For a full overview of the different solutions SAP provides for CI/CD, see [SAP Solutions for Continuous Integration and Delivery](https://help.sap.com/viewer/8cacec64ed854b2a88e9a0973e0f97a2/Cloud/en-US/e9fa320181124fa9808d4446a1bf69dd.html).



<a name="loio3eb8d5820728482389c69807117f174f__section_ivp_5c1_sjb"/>

## Prerequisites

-   You have an SAPUI5/SAP Fiori application as source in a source code management system of your choice.

-   In the top level directory of your project, you have a file called `Gruntfile.js`, whicht contains the following entries:

    ```
    module.exports = function (grunt) {
                "use strict";
                grunt.loadNpmTasks("@sap/grunt-sapui5-bestpractice-build");
                grunt.config.merge({ compatVersion: "1.38" });
                grunt.registerTask("default", [
                            "clean",
                            "lint",
                            "build"
                ]);
                grunt.loadNpmTasks("@sap/grunt-sapui5-bestpractice-test");
                grunt.registerTask("unit_and_integration_tests", ["test"]);
                grunt.config.merge({
                            coverage_threshold: {
                                        statements: 0,
                                        branches: 100,
                                        functions: 0,
                                        lines: 0
                            }
                });
    };
    ```

    For more information on how to set up your Grunt build in SAP Web IDE Full-Stack, see [Grunt Build in SAP Web IDE Full-Stack](https://developers.sap.com/tutorials/webide-grunt-basic.html).

-   In the top level directory of your project, you have a file called `package.json`, which contains the following lines:

    ```
    "devDependencies": {
      "@sap/grunt-sapui5-bestpractice-build": "1.4.1",
      "@sap/grunt-sapui5-bestpractice-test": "2.0.1"
    },
    
    "scripts": {
      "build": "ui5 build --a",
      "test": "uiveri5"
      "linting": "eslint ."
    }
    ```

    > ### Note:  
    > The build script executes the UI5 command line tool. In this example, the test script runs UIVeri5. You can, however, substitute `uiveri5` with any other automated tests you have implemented.

-   As it prevents clutter on your build system and improves both maintainability and flexibility, we recommend working with [Docker](https://www.docker.com/). Refer to the documentation of your CI tool to check whether it supports the usage of Docker containers in its pipelines.

    > ### Caution:  
    > Please check with your IT and security departments how to handle Docker images from public sources.

    Depending on whether you want or don't want to work with Docker, make sure that you meet the following additional prerequisites:

    -   **With Docker:**

        You have built the [RFC CTS+ Dockerfile](https://github.com/SAP/devops-docker-images/tree/master/node-rfc).

    -   **Without Docker:**

        -   You have installed NodeJS on your build machine.

        -   You have downloaded and installed the [SAP NetWeaver RFC Library](https://launchpad.support.sap.com/#/softwarecenter/search/netweaver%2520rfc%2520library).






<a name="loio3eb8d5820728482389c69807117f174f__section_yym_vc1_sjb"/>

## Procedure

Use the following procedure to create a pipeline in a CI/CD tool of your choice. It consists of two distinct parts: The continuous integration process and the ABAP life-cycle management. For more information, see [Apply CI/CD to SAP Fiori Development on an SAP Fiori Front-End Server](apply-ci-cd-to-sap-fiori-development-on-an-sap-fiori-front-end-server-3713b07.md).



### The Continuous Integration Process

![](images/Fiori_on_ABAP_-_CI_Process_d0b1f6b.png)

1.  To install all needed dependencies for your application, call Grunt, and execute the tasks in your `gruntfile.js`, choose one of the following options:

    -   **With Docker:**

        In your shell, execute the following commands:

        ```
        docker run -v "${PWD}":/project node:latest npm install
        ```

        ```
        docker run -v "${PWD}":/project node:latest node_modules/grunt-cli/bin/grunt default createZip
        ```

        > ### Note:  
        > The `-v` command mounts your current working directory. As many CI tools automatically mount the workspace, which contains the project sources into your Docker container, you may omit it.

    -   **Without Docker:**

        In your shell, execute the following commands:

        ```
        npm install
        ```

        ```
        node_modules/grunt-cli/bin/grunt default createZip
        ```


2.  To add automated tests to your pipeline, choose one of the following options:

    -   **With Docker:**

        Use a standard node image that fits your requirements from the Docker Hub. In your shell, execute the following commands:

        ```
        docker run -v "${PWD}":/project node:latest npm run-script test
        ```

        ```
        docker run -v "${PWD}":/project node:latest npm run-script linting
        ```

    -   **Without Docker:**

        In your shell, execute the following commands:

        ```
        npm run-script test
        ```

        ```
        npm run-script linting
        ```


    > ### Tip:  
    > For SAPUI5/ SAP Fiori, we recommend implementing UIVeri5 and OPA5 tests. See, for example [Add Automated System Tests to Your CI/CD Pipeline](https://developers.sap.com/tutorials/cp-cicd-sytem-test.html).

3.  Trigger your pipeline to test the CI build.




### The ABAP Life-Cycle Management

![](images/Fiori_on_ABAP_-_Upload_Release_Export_dd03a3e.png)

1.  To define the logic for RFC connections, create a Gruntfile with the name `run-rfc-task.js` on the top level of your directory, and copy the following code into it:

    ```
    "use strict";
    
    var rfc = require("node-rfc");
    var fs = require("fs");
    
    module.exports = function(grunt) {
    
        // Project specific variables
        var abapDevelopmentUser = process.env.ABAP_DEVELOPMENT_USER;
        var abapDevelopmentPassword = process.env.ABAP_DEVELOPMENT_PASSWORD;
        var abapDevelopmentServer = process.env.ABAP_DEVELOPMENT_SERVER;
        var abapDevelopmentInstance = process.env.ABAP_DEVELOPMENT_INSTANCE;
        var abapDevelopmentClient = process.env.ABAP_DEVELOPMENT_CLIENT;
        var abapApplicationName = process.env.ABAP_APPLICATION_NAME;
        var abapApplicationDesc = process.env.ABAP_APPLICATION_DESC;
        var abapPackage = process.env.ABAP_PACKAGE;
        var zipFileURL = process.env.ZIP_FILE_URL;
        var codePage = process.env.CODE_PAGE;
        var acceptUnixStyleLineEndings = process.env.ABAP_ACCEPT_UNIX_STYLE_EOL;
        var transportDescription = process.env.TRANSPORT_DESCRIPTION;
        var targetDir = process.env.SAPDATADIR;
        var verbose = process.env.VERBOSE;
        var failUploadOnWarning = process.env.FAIL_UPLOAD_ON_WARNING;
    
    
        // Global Variables
        var ctsDataFile = targetDir + "/CTS_Data.txt";
    
        // Project configuration.
        var abapConn = {
            user: abapDevelopmentUser,
            passwd: abapDevelopmentPassword,
            ashost: abapDevelopmentServer,
            sysnr: abapDevelopmentInstance,
            client: abapDevelopmentClient
        };
        grunt.initConfig({
            pkg: grunt.file.readJSON("package.json"),
            createTransportRequest: {
                options: {
                    conn: abapConn,
                    author: abapDevelopmentUser,
                    description: transportDescription,
                    verbose: verbose
                }
            },
            uploadToABAP: {
                options: {
                    conn: abapConn,
                    zipFileURL: zipFileURL,
                    codePage: codePage,
                    acceptUnixStyleLineEndings: acceptUnixStyleLineEndings,
                    verbose: verbose,
                    failUploadOnWarning: failUploadOnWarning
                }
            },
            releaseTransport: {
                options: {
                    conn: abapConn,
                    verbose: verbose
                }
            }
        });
    
        var rfcConnect = function(functionModule, importParameters, gruntContext) {
            return new Promise(function(resolve, reject) {
                var verbose = gruntContext.options().verbose
                var conn = gruntContext.options().conn;
                var client = new rfc.Client(conn);
    
                grunt.log.writeln("RFC client lib version:", client.version);
    
                client.connect(function(err) {
                    if (err) { // check for login/connection errors
                        grunt.log.errorlns("could not connect to server", err);
                        return reject();
                    }
                    // invoke remote enabled ABAP function module
                    grunt.log.writeln("Invoking function module", functionModule);
                    client.invoke(functionModule,
                        importParameters,
                        function(err, res) {
                            if (err) { // check for errors (e.g. wrong parameters)
                                grunt.log.errorlns("Error invoking", functionModule, err);
                                return reject();
                            }
                            client.close();
                            if(verbose == 'true') {
                                grunt.log.writeln("Result:", res);
                            }
                            return resolve(res);
                        });
                });
            });
        };
    
    
        grunt.registerTask("createTransportRequest", "Creates an ABAP Transport Request", function() {
            grunt.log.writeln("Creating Transport Request");
            var importParameters = {
                AUTHOR: this.options().author,
                TEXT: this.options().description
            };
            var done = this.async();
            rfcConnect("BAPI_CTREQUEST_CREATE", importParameters, this)
                .then(
                function(returnValue) {
                    if  (returnValue.RETURN.TYPE == "E" || returnValue.RETURN.TYPE == "W") {
                        grunt.log.errorlns("Error invoking BAPI_CTREQUEST_CREATE.");
                        grunt.log.writeln("Return:", returnValue);
                        done(false);
                        return;
                    }
                    if (returnValue.REQUESTID == "") {
                        grunt.log.errorlns("Error invoking BAPI_CTREQUEST_CREATE.");
                        grunt.log.errorlns("Transport request could not be created.");
                        grunt.log.errorlns(returnValue.RETURN.MESSAGE);
                        done(false);
                        return;
                    }
                    grunt.log.writeln("Transport request", returnValue.REQUESTID, "created.");
                    if (fs.existsSync(targetDir) === false) {
                        fs.mkdirSync(targetDir);
                    }
                    fs.writeFile(ctsDataFile,
                        JSON.stringify(
                            { REQUESTID: returnValue.REQUESTID }
                        ),
                        function(err) {
                            if (err) {
                                grunt.log.errorlns("Error Creating file:", err);
                                done(false);
                                return;
                            }
                            grunt.log.writeln("Created file:", ctsDataFile);
                            done();
                        }
                    )
                },
                function() {
                    done(false);
                });
        });
    
        grunt.registerTask("uploadToABAP", "Uploads the application to the ABAP System", function(transportRequest) {
            grunt.log.writeln("Uploading to ABAP");
            if (!transportRequest) {
                grunt.log.errorlns("No Transport request specified.");
                return (false);
            }
            grunt.log.writeln("Transport request:", transportRequest);
            var url = this.options().zipFileURL;
            var verbose = this.options().verbose;
            var failUploadOnWarning = this.options().failUploadOnWarning;
            var importParameters = {
                IV_URL: url,
                IV_SAPUI5_APPLICATION_NAME: abapApplicationName,
                IV_SAPUI5_APPLICATION_DESC: abapApplicationDesc,
                IV_PACKAGE: abapPackage,
                IV_WORKBENCH_REQUEST: transportRequest,
                IV_TEST_MODE: "-",
                IV_EXTERNAL_CODE_PAGE: this.options().codePage,
                IV_ACCEPT_UNIX_STYLE_EOL: this.options().acceptUnixStyleLineEndings
            };
            var done = this.async();
            grunt.log.writeln("Uploading application from", url);
            rfcConnect("/UI5/REPO_LOAD_FROM_ZIP_URL", importParameters, this)
                .then(
                function(returnValue) {
                    if (returnValue.EV_SUCCESS == "E" || (failUploadOnWarning != "false" && returnValue.EV_SUCCESS == "W")) {
                        grunt.log.errorlns("Error invoking", "/UI5/REPO_LOAD_FROM_ZIP_URL");
                        grunt.log.writeln("Return:", returnValue);
                        done(false);
                        return;
                    } else if (returnValue.EV_SUCCESS == 'S') {
                        grunt.log.writeln("Application uploaded.");
                        done();
                    } else {
                        grunt.log.writeln("Invalid return status (EV_SUCCESS): " + returnValue.EV_SUCCESS);
                        done(false);
                        return;
                    }
                    if(verbose == 'true' ) {
                        grunt.log.writeln("Return:", returnValue);
                    }
    
                    grunt.log.writeln("Application uploaded.");
                    done();
    
                },
                function() {
                    done(false);
                });
        });
    
        grunt.registerTask("releaseTransport", "Releases an ABAP Transport Request", function(transportRequest) {
            grunt.log.writeln("Releasing Transport Request");
            if (!transportRequest) {
                grunt.log.errorlns("No Transport request specified.");
                return (false);
            }
            grunt.log.writeln("Transport request:", transportRequest);
            var importParameters = {
                REQUESTID: transportRequest,
                COMPLETE: "X",
                BATCH_MODE: "X"
            }
            var done = this.async();
            rfcConnect("BAPI_CTREQUEST_RELEASE", importParameters, this)
                .then(
                function(returnValue) {
                if (returnValue.RETURN.TYPE == "E" || returnValue.RETURN.TYPE == "W") {
                        grunt.log.errorlns("Error invoking", "BAPI_CTREQUEST_RELEASE");
                        grunt.log.writeln("Return:", returnValue);
    
                        done(false);
                        return;
                    }
                    grunt.log.writeln("Transport request released.");
                    done();
                },
                function() {
                    done(false);
                });
        });
    };
    ```

    This Gruntfile implements the following tasks, which are passed as parameters to the `grunt` command in the next step:

    **Tasks in the run-rfc-task.js**


    <table>
    <tr>
    <th valign="top">

    Task
    
    </th>
    <th valign="top">

    Function
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `createTransportRequest` 
    
    </td>
    <td valign="top">
    
    Create a transport request in the ABAP system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `uploadToABAP` 
    
    </td>
    <td valign="top">
    
    Upload the application as ZIP file to the ABAP system.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `releaseTransport` 
    
    </td>
    <td valign="top">
    
    Release the transport request with all its transport tasks.
    
    </td>
    </tr>
    </table>
    
2.  To execute the tasks from the `run-rfc-task.js`, choose one of the following options:

    -   **With Docker:**

        In your shell, execute the following commands:

        ```
        docker run -v "${PWD}":/project node:latest npm install
        ```

        ```
        docker run -v "${PWD}":/project node:latest node_modules/grunt-cli/bin/grunt  --gruntfile run-rfc-task.js createTransportRequest uploadToABAP releaseTransport
        ```

    -   **Without Docker:**

        In your shell, execute the following commands:

        ```
        npm install
        ```

        ```
        node_modules/grunt-cli/bin/grunt  --gruntfile run-rfc-task.js createTransportRequest uploadToABAP releaseTransport
        ```



![](images/Fiori_on_ABAP_-_Import_c3ada45.png)

Use SAP Logon to manually import your transport request into the following system:

1.  In SAP Logon, open the transaction `stms`.

2.  Choose *Import Overview*.

3.  Select your target system and choose *Display Import Queue*.

4.  To import the waiting request, select it and choose *OK*.




<a name="loio3eb8d5820728482389c69807117f174f__section_fvj_zpx_tjb"/>

## Result

You have combined the ABAP life-cycle management with a basic CI pipeline, which you can enhance according to your needs.

> ### Note:  
> This guide also provides procedures to enhance your finished CI/CD pipelines. See [Procedures for CI/CD Pipelines](procedures-for-ci-cd-pipelines-e49a97d.md).

