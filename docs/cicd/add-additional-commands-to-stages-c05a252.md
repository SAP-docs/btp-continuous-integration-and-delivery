<!-- loioc05a2522c90a40069ead07bd81df37ab -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add Additional Commands to Stages

Configure additional commands in the stages of your job.



<a name="loioc05a2522c90a40069ead07bd81df37ab__section_e2d_1d4_42c"/>

## Context

If you want to execute tasks other than the default ones provided in the SAP Continuous Integration and Delivery stages, you can configure your own additional commands. These commands can be configured to run at the beginning or the end of a specific stage. They will be executed on a Node.js Docker image using a version based on Node 20. For more details, refer to the Node.js information on [Docker Hub](https://hub.docker.com/_/node).

You can configure additional commands using either the job editor or the configuration file in your source code management system. If you choose to use the configuration file, ensure you follow the security guidelines outlined in the [Additional Commands](https://help.sap.com/docs/CONTINUOUS_DELIVERY/99c72101f7ee40d0b2deb4df72ba1ad3/8a57562c7d2d4f7db53a29b2f1e146e9.html?version=Cloud#additional-commands) section of the SAP Continuous Integration and Delivery security guide.

> ### Tip:  
> Depending on which configuration mode you choose, expand one of the following sections for more information.

<a name="task_xlx_whk_jwb"/>

<!-- task\_xlx\_whk\_jwb -->

## Configure Additional Commands Using the Job Editor

Add additional commands to your job using the job editor in the SAP Continuous Integration and Delivery user interface.



<a name="task_xlx_whk_jwb__steps_a5l_xhk_jwb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, either create a new job or navigate to the job to which you want to add additional commands and choose *Edit*.

2.  In the *Stages* section of your job, navigate to the stage to which you want to add a command and choose :heavy_plus_sign: next to *Additional Commands*.

3.  From the drop-down list, choose one of the following options:

    -   *Run First in Stage* to run your command in the beginning of the stage

    -   *Run Last in Stage* to run your command at the end of the stage


4.  In the *Command* text field, enter the commands you want to run.

5.  Either choose *Create* to create your new job or choose *Save* to confirm your changes to an existing job.

    > ### Note:  
    > When you run your job, a folder named `cloudcitransfer` is automatically created in your job workspace. Please place all files that you want to reuse in later stages of your job into this folder.


**Related Information**  


[Next Level of Flexibility: Additional Commands in CI/CD Pipelines](https://blogs.sap.com/2023/06/22/next-level-of-flexibility-additional-commands-in-ci-cd-pipelines/)

<a name="task_g5g_xnd_lxb"/>

<!-- task\_g5g\_xnd\_lxb -->

## Configure Additional Commands in the Configuration File

Add additional commands to your job using the configuration file in your source code management system.



<a name="task_g5g_xnd_lxb__steps_h5g_xnd_lxb"/>

## Procedure

1.  In your source code repository, navigate to the `.pipeline/config.yml` file.

2.  In the `service` section, depending on the stage in which you want to set the commands, insert a code block as follows:

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

<a name="concept_yqv_ycp_42c"/>

<!-- concept\_yqv\_ycp\_42c -->

## Use Additional Commands in Stages

Once you've set up your additional commands, you can use them in your processes within a specific stage.

The following variables help you use your additional commands:


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

