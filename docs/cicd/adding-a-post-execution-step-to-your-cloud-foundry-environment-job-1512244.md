<!-- loio1512244f4e5842c19a5aa880a32bc338 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Adding a Post-Execution Step to Your Cloud Foundry Environment Job

Learn how to add a command that runs at the end of a Cloud Foundry Environment job and configure environment variables using credentials or user-defined values.



## Context

To execute tasks beyond the default ones in the Cloud Foundry Environment pipeline in SAP Continuous Integration and Delivery, you can a add post-execution step to your job. The post-execution step consists of a command that runs at the end of the job and, optionally, environment variables derived from credentials or user-defined values.

The post-execution command is executed even if the job fails. It runs in a Node.js Docker image using a Node.js version based on Node 22. For more information, see the Node.js image on [Docker Hub](https://hub.docker.com/_/node).

You can configure a post-execution step either by using the built-in job editor in the service interface or by defining it in your source repository. When using a configuration file, make sure to follow the security guidelines described in the [Additional Commands](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/git-repositories?version=Cloud#additional-commands) section of the SAP Continuous Integration and Delivery security guide.

> ### Tip:  
> Depending on which configuration mode you choose, expand one of the following sections for more information.

<a name="task_hcb_4h3_13c"/>

<!-- task\_hcb\_4h3\_13c -->

## Configure a Post-Execution Step Using the Job Editor

Use the service user interface to add a post-execution command and optional environment variables derived from credentials or user-defined values to your job.



## Procedure

1.  In SAP Continuous Integration and Delivery, either create a new Cloud Foundry Environment job or navigate to the job to which you want to add a post-execution step and choose *Edit*.

2.  In the *Post-Execution Step* section of your job, choose :heavy_plus_sign: next to *Final Command*.

3.  In the *Command* text field, enter a shell command. You can use multiple sub‑commands by separating them with a semicolon \(`;`\) or the short‑circuit AND operator \(`&&`\), for example "cd helloWorld && npm install && npm hello-world.js". Using `&&` ensures that each subsequent command is only executed if the preceding command succeeds.

    > ### Note:  
    > The final command runs even if the job fails.

4.  \(Optional\) If you want to add environment variables using credentials, choose :heavy_plus_sign: next to *Credentials*.

    1.  In the *Name* text field, enter a name for the credential you want to add. Use only letters, digits, and underscores.

    2.  In the *Credential Name* text field, either choose an existing credential in SAP Continuous Integration and Delivery from the dropdown list or choose :heavy_plus_sign: to create a new one. See [Creating Credentials](creating-credentials-6658c81.md).


5.  \(Optional\) If you want to add environment variables using user-defined values, choose :heavy_plus_sign: next to *Variables*.

    1.  In the *Name* text field, enter a name for the variable you want to add. Use only letters, digits, and underscores.

    2.  In the *Value* field, enter a string value for your variable.


6.  Choose *Create*.


<a name="task_akz_jk3_13c"/>

<!-- task\_akz\_jk3\_13c -->

## Configure a Post-Execution Step in the Configuration File

Use the configuration file in your source code management system to add a post-execution command and optional environment variables derived from credentials or user-defined values to your job.



## Procedure

1.  In your source repository, navigate to the `.sap_cid/config.yaml` file.

2.  After the `stages` section, add another section named `lifeCycle` with the following content:

    > ### Sample Code:  
    > ```
    > --- 
    > stages:
    >   build:
    >     ...
    >   ...
    > lifeCycle:
    >   afterAllStages:
    >     command: "cd helloWorld && npm install && npm hello-world.js"
    >     credentialVariables:
    >     - name: "BasicAuth"
    >       valueSource: "my-credential"
    >     stringVariables:
    >     - name: "myVar"
    >       value: "blogs.sap.com"
    > ```

    -   **`command:`** Replace `"cd helloWorld && npm install && npm hello-world.js"` with the command and, optionally, any sub-commands you want to execute. Using `&&` ensures that each subsequent command is only executed if the preceding command succeeds.
    -   **`credential variables:`** For `name`, enter a name for your environment variable. For `valueSource`, enter the *Credential Name* of the credential you've created in SAP Continuous Integration and Delivery. See [Creating Credentials](creating-credentials-6658c81.md). For `valueSource`, use only letters, digits, and underscores.
    -   **`stringVariables:`** Assign your own values to the `name` and `value` parameters. For `name`, use only letters, digits, and underscores.


<a name="concept_y3y_sp3_13c"/>

<!-- concept\_y3y\_sp3\_13c -->

## Variables Available for the Final Command

Learn which variables are available for use in your final command.

The following variables are already defined in the post‑execution step. You can use them in your final command along with your environment variables.


<table>
<tr>
<th valign="top">

Variable

</th>
<th valign="top">

Description

</th>
</tr>
<tr>
<td valign="top">

`BUILD_ID` 

</td>
<td valign="top">

The ID of the current build.

</td>
</tr>
<tr>
<td valign="top">

`RESULT` 

</td>
<td valign="top">

The result of the current build.

</td>
</tr>
<tr>
<td valign="top">

`CLOUDCI_PIPELINE_ENV_JSON` 

</td>
<td valign="top">

A collection of structured properties that are useful for your job.

</td>
</tr>
<tr>
<td valign="top">

`JOB_NAME` 

</td>
<td valign="top">

The name of the job that is being executed.

</td>
</tr>
<tr>
<td valign="top">

`PIPELINE` 

</td>
<td valign="top">

The pipeline type of the job that is being executed.

</td>
</tr>
<tr>
<td valign="top">

`PIPELINE_VERSION` 

</td>
<td valign="top">

The version of the pipeline of the job that is being executed.

</td>
</tr>
<tr>
<td valign="top">

`CLOUDCI_GIT_COMMIT` 

</td>
<td valign="top">

The hash of the commit for which the job is executed.

</td>
</tr>
<tr>
<td valign="top">

`GIT_BRANCH` 

</td>
<td valign="top">

The branch for which the current job is executed.

</td>
</tr>
<tr>
<td valign="top">

`GIT_URL` 

</td>
<td valign="top">

The URL of your source repository

</td>
</tr>
</table>

