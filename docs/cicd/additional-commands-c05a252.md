<!-- loioc05a2522c90a40069ead07bd81df37ab -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Additional Commands

Configure additional commands in the stages of your SAP Continuous Integration and Delivery jobs.

> ### Note:  
> You can use this feature for all scenarios listed in [Supported Pipelines](supported-pipelines-e293286.md) except for [SAP Integration Suite Artifacts](sap-integration-suite-artifacts-019ed68.md).

If you want to perform a particular task apart from the ones covered in the SAP Continuous Integration and Delivery stages by default, you can configure your own additional commands. In the *Additional Commands* section, you can define commmands to be executed in the beginning or at the end of a given stage. The additional commands are executed inside a Node.js Docker image. For more information, see node on [Docker Hub](https://hub.docker.com/_/node).

You can configure additional commands either using the job editor or the configuration file in your source code management system. In the latter case, consider the security-relevant information described in the [Additional Commands](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/8a57562c7d2d4f7db53a29b2f1e146e9.html?version=Cloud#additional-commands) section of the SAP Continuous Integration and Delivery security guide.

The following variables help you configure your additional commands:

**Variables for Additional Commands in SAP Continuous Integration and Delivery**


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

`GIT_URL` 

</td>
<td valign="top">

The URL of your source repository

</td>
</tr>
<tr>
<td valign="top">

`CLOUDCI_PIPELINE_ENV_JSON` 

</td>
<td valign="top">

A collection of structured properties that are useful for your job

</td>
</tr>
</table>

<a name="task_xlx_whk_jwb"/>

<!-- task\_xlx\_whk\_jwb -->

## Configure Additional Commands Using the Job Editor

Configure additional commands to your job using the job editor in the SAP Continuous Integration and Delivery user interface.



<a name="task_xlx_whk_jwb__steps_a5l_xhk_jwb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, either create a new job or navigate to the job to which you want to add additional commands and choose *Edit*.

2.  In the *Stages* tab of your job, navigate to the stage to which you want to add a command and choose :heavy_plus_sign: next to *Additional Commands*.

3.  From the drop-down list, choose one of the following options:

    -   *Run First in Stage* to run your command in the beginning of the stage

    -   *Run Last in Stage* to run your command at the end of the stage


4.  In the *Command* text field, enter the commands you want to run.

5.  Choose *Create* to create your new job. If you made changes to an existing job, confirm them by choosing *Save*.

    > ### Note:  
    > At the start of your pipeline run, a folder named `cloudcitransfer` is automatically created in your pipeline workspace. Please place all files that you want to reuse in later stages of your job in this folder.


<a name="task_g5g_xnd_lxb"/>

<!-- task\_g5g\_xnd\_lxb -->

## Configure Additional Commands in the Configuration File

Configure additional commands to your job using the configuration file in your source code management system.



<a name="task_g5g_xnd_lxb__steps_h5g_xnd_lxb"/>

## Procedure

1.  In your source code repository, navigate to the `.pipeline/config.yml` file.

2.  In the service section, depending on the stage in which you want to set the commands, insert the following code block:

    -   To run your command in the beginning of the Build stage, for example:

        > ### Sample Code:  
        > ```
        > service:
        >   stages:
        >     Build:
        >       runFirst:
        >         command: "cd helloWorld && npm install && npm hello-world.js"
        > ```

    -   To run your command at the end of the Build stage, for example:

        > ### Sample Code:  
        > ```
        > service:
        >   stages:
        >     Build:
        >       runLast:
        >         command: "cd helloWorld && npm install && npm hello-world.js"
        > ```


    Replace `Build` with the name of the stage to which you want to add your command. Replace `"cd helloWorld && npm install && npm hello-world.js"` with the commands you want to execute.

    Using `&&` will execute the second command only when the first command was executed. If the stage you want to use has spaces in it, put quotes around the stage name, for example `'Additional Unit Tests'` or `"Additional Unit Tests"`.

    > ### Note:  
    > At the start of your pipeline run, a folder named `cloudcitransfer` is automatically created in your pipeline workspace. Please place all files that you want to reuse in later stages of your job in this folder.


**Related Information**  


[Next Level of Flexibility: Additional Commands in CI/CD Pipelines](https://blogs.sap.com/2023/06/22/next-level-of-flexibility-additional-commands-in-ci-cd-pipelines/)

