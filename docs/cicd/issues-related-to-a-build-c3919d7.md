<!-- loioc3919d786e924fe38ae075e98e83553c -->

# Issues Related to A Build

Learn how to handle issues related to a build in SAP Continuous Integration and SAP Continuous Integration and Delivery.

Depending on what kind of issue you are facing, expand one of the following sections for more information.



<a name="loioc3919d786e924fe38ae075e98e83553c__section_gst_j3s_fdc"/>

## `Failed to Load Build Stages`



### Symptom

You have triggered a job as described in [Running and Monitoring CI/CD Jobs](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/db8521cc85924f78b7e92b1ea69fdf94.html?language=en-US) and get the following error message:

> ### Output Code:  
> ```
> Failed to load build stages
> ```



### Solution

Choose *Show Full Log* to view the log for your build.

There are various reasons for a build to fail at an early stage. If the issue is related to the pipeline configuration, you might find the solution in [Configuring Jobs](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/supported-pipelines?version=Cloud).

If this issue persists, please open a ticket as described in [Support](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/support-feature-requests-and-feedback?version=Cloud).



<a name="loioc3919d786e924fe38ae075e98e83553c__section_ddy_xjs_fdc"/>

## `Service Operation Failed`



### Symptom

You have triggered the build of a job as described in [Running and Monitoring CI/CD Jobs](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/db8521cc85924f78b7e92b1ea69fdf94.html?language=en-US). Your job fails and in the build log, you get the following error message:

> ### Output Code:  
> ```
> Service operation failed
> ```



### Example of the Complete Error Message

> ### Output Code:  
> ```
> Service operation failed: Controller operation failed: 404 Updating service "..." failed: Not Found: Error creating service "..." from offering "html5-apps-repo" and plan "app-host": Could not create service instance "...". Service plan "app-host" from service offering "html5-apps-repo" was not found.
> ```



### Solution

Make sure that the mentioned service has been entitled and the required quota is set. See [Managing Entitlements and Quotas Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/c8248745dde24afb91479361de336111.html).



<a name="loioc3919d786e924fe38ae075e98e83553c__section_dhl_mls_fdc"/>

## `A Valid Gruntfile Cannot be Found`



### Symptom

You have triggered the build of a job for an SAP Fiori project as described in [Running and Monitoring CI/CD Jobs](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/db8521cc85924f78b7e92b1ea69fdf94.html?language=en-US). Your build fails and in the build log, you get the following error message:

> ### Output Code:  
> ```
> A valid Gruntfile could not be found
> ```



### Solution

Add a valid `Gruntfile.js` in the top-level folder of your project.

Depending on which pipeline you use, choose one of the following options for more information:

-   [Configure a Cloud Foundry Environment Job](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-job-editor?version=Cloud) 
-   [Configure an SAP Fiori in the Neo Environment Job](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-fiori-in-neo-environment-job-in-job-editor?version=Cloud)
-   [Configure an SAP Fiori for the ABAP Platform Job](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-fiori-for-abap-platform-job-in-job-editor?version=Cloud)



<a name="loioc3919d786e924fe38ae075e98e83553c__section_xtm_2ms_fdc"/>

## `Local Npm module “@sap/grunt-sapui5-bestpractice-build” not Found`



### Symptom

You have triggered a job for an SAP Fiori project as described in [Running and Monitoring CI/CD Jobs](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/db8521cc85924f78b7e92b1ea69fdf94.html?language=en-US). Your build fails and in the build log, you get the following error message:

> ### Output Code:  
> ```
> Local Npm module “@sap/grunt-sapui5-bestpractice-build” not found
> ```



### Solution

Add the requested npm libraries as dependencies to your package.json file.

Depending on which pipeline type you use, choose one of the following options for more information:

-   [Configure a Cloud Foundry Environment Job](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-cloud-application-programming-model-job-in-job-editor?version=Cloud)
-   [Configure an SAP Fiori in the Neo Environment Job](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-fiori-in-neo-environment-job-in-job-editor?version=Cloud)
-   [Configure an SAP Fiori for the ABAP Platform Job](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/configure-sap-fiori-for-abap-platform-job-in-job-editor?version=Cloud)



<a name="loioc3919d786e924fe38ae075e98e83553c__section_yl4_nms_fdc"/>

## `/usr/lib/libstdc++.so.6: no version information available`



### Symptom

You have triggered the build of a Cloud Foundry Environment job as described in Running and Monitoring CI/CD Jobs. Your build fails and in the build log, you get the following error message:

> ### Output Code:  
> ```
>  /usr/lib/libstdc++.so.6: no version information available
> ```



### Solution

There are two possible root causes for this issue:

-   Your `package.json` file contains the following line in the `devDependencies` section:

    ```
     "@sap/grunt-tests-webide-bestpractice": "<X.X.XX>" 
    ```

    In this case, change the line as follows:

    ```
     "@sap/grunt-sapui5-bestpractice-test": "^2.0.0"
    
    ```


-   Your `Gruntfile.js` contains the following line:

    ```
    grunt.loadNpmTasks("@sap/grunt-tests-webide-bestpractice");
    ```

    In this case, change the line as follows:

    ```
    grunt.loadNpmTasks("@sap/grunt-sapui5-bestpractice-test");
    ```




<a name="loioc3919d786e924fe38ae075e98e83553c__section_pkd_bns_fdc"/>

## `Error staging application "...": BuildpackCompileFailed - App staging failed in buildpack compile phase`



### Symptom

You have triggered the build of a job as described in [Running and Monitoring CI/CD Jobs](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/db8521cc85924f78b7e92b1ea69fdf94.html?language=en-US). Your build fails and in the build log, you get the following error message:

> ### Output Code:  
> ```
> info cloudFoundryDeploy - Error staging application "…": BuildpackCompileFailed - App staging failed in the buildpack compile phase
> ```



### Solution

Make sure that the engines section in your `package.json` file contains the following lines:

```
{
  "name": "...",
  "description": "...",
  "engines": {
    "node": "^14.0.0"
  },
  ...
}
```

For more information, see SAP Note [3124191](https://launchpad.support.sap.com/#/notes/0003124191).



<a name="loioc3919d786e924fe38ae075e98e83553c__section_ocw_44s_fdc"/>

## `npm ERR! Network Request to Failed`



### Symptom

You have triggered the build of a job as described in [Running and Monitoring CI/CD Jobs](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/db8521cc85924f78b7e92b1ea69fdf94.html?language=en-US). Your build fails and in the build log, you get the following error message:

> ### Output Code:  
> ```
> npm ERR! network request to failed
> ```



### Solution

Follow the instructions in [SAP Note 3216731](https://me.sap.com/notes/0003216731).



<a name="loioc3919d786e924fe38ae075e98e83553c__section_jtg_x4s_fdc"/>

## `stderr: error: RPC failed; HTTP 401 curl 22 The requested URL returned error: 401`



### Symptom

You’ve triggered the build of a job as described in [Running and Monitoring CI/CD Jobs](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/db8521cc85924f78b7e92b1ea69fdf94.html?version=Cloud) and it either doesn’t start or aborts quickly, and you get an error message that looks as follows:

> ### Output Code:  
> ```
> using GIT_ASKPASS to set credentials 
> 
> > git fetch --tags --force --progress -- https://github.com/SAP-samples/cap-bookshop-wdi5.git +refs/heads/*:refs/remotes/origin/* # timeout=10
> 
> ERROR: Error cloning remote repo 'origin'
> 
> hudson.plugins.git.GitException: Command "git fetch --tags --force --progress -- https://github.com/SAP-samples/cap-bookshop-wdi5.git +refs/heads/*:refs/remotes/origin/*" returned status code 128:
> 
> stdout: 
> 
> stderr: error: RPC failed; HTTP 401 curl 22 The requested URL returned error: 401
> 
> fatal: expected flush after ref listing
> 
> ```



### Solution

The reason for this issue might be an incorrect token. To solve it, check the credentials in SAP Continuous Integration and Delivery and/or your source code management system and make sure that they correspond to the instructions in [Creating Credentials](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/6658c81f3e43456891852955b1ee11db.html?version=Cloud).



<a name="loioc3919d786e924fe38ae075e98e83553c__section_vgh_kps_fdc"/>

## `This build reached the log quota. All further messages have been discarded`



### Symptom

The detailed log of your build is cut off and shows the following error message:

> ### Output Code:  
> ```
> This build reached the log quota. All further messages have been discarded.
> ```



### Solution

There is a limit of logs that are persisted. Please check whether you're writing too many logs, for example, in your test scripts.

If this issue persists, please open a ticket as described in [Support](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/support-feature-requests-and-feedback?version=Cloud).

