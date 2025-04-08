<!-- loio74fe5409efad4efaae017eb90fa64b95 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add Additional Variables to Stages

Add environment variables that store user-defined strings to the stages of your job.

You can configure environment variables either using the SAP Continuous Integration and Delivery job editor or using the configuration file in your source code management system.

> ### Tip:  
> Depending on which configuration mode you choose, expand one of the following sections for more information.

<a name="task_svr_lnl_jwb"/>

<!-- task\_svr\_lnl\_jwb -->

## Configure Additional Variables Using the Job Editor

Add environment variables to your job using the job editor in the SAP Continuous Integration and Delivery user interface.



<a name="task_svr_lnl_jwb__steps_ay4_l4w_dwb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, either create a new job or navigate to the job to which you want to add credentials variables and choose *Edit*.

2.  In the *Stages* section of your job, navigate to the stage to which you want to add environment variables and choose :heavy_plus_sign: next to *Additional Variables*.

3.  In the *Name* text field, enter a name for your variable. Use only letters, digits, and underscores.

4.  In the *Value* field, enter a string value for your variable.

5.  Choose *Create*.


<a name="task_j3h_t3w_dwb"/>

<!-- task\_j3h\_t3w\_dwb -->

## Configure Additional Variables in the Configuration File

Add environment variables to your job using the configuration file in your source code management system.



<a name="task_j3h_t3w_dwb__steps_yxn_j4w_dwb"/>

## Procedure

1.  In your source code repository, navigate to the `.pipeline/config.yml` file.

2.  In the service section, depending on the stage in which you want to set the variable \(in this example, we used the "Build" stage\), insert the following code block. Assign your own values to the `name` and `value` parameters:

    ```
    service:
      stages:
        Build:
          stringVariables:
            - name: "MyVar"
              value: "blogs.sap.com"
    ```

    > ### Note:  
    > For `name`, use only letters, digits, and underscores.


<a name="concept_prh_zh4_42c"/>

<!-- concept\_prh\_zh4\_42c -->

## Use Additional Variables in Stages

Once you've set up your environment variables, you can use them in your processes within a specific stage.

In the following example, the variable is named `MyVar`:

> ### Sample Code:  
> ```
> !#/bin/bash
> echo "Injected variable: $MyVar"
> ```

Replace `MyVar` with the name of the variable you've just created.

