<!-- loioaf2d1a253d0d4f35b17935ab42f32a0b -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Additional Credentials

Add environment variables that store values injected from credentials to the stages of your SAP Continuous Integration and Delivery jobs.

> ### Note:  
> You can use this feature for all scenarios listed in [Supported Pipelines](supported-pipelines-e293286.md) except for [SAP Integration Suite Artifacts](sap-integration-suite-artifacts-019ed68.md).

You can configure environment variables either using the SAP Continuous Integration and Delivery job editor or using the configuration file in your source code management system.

<a name="task_xlx_whk_jwb"/>

<!-- task\_xlx\_whk\_jwb -->

## Add Additional Credentials Using the Job Editor

Add credential variables to your job using the job editor in the SAP Continuous Integration and Delivery user interface.



<a name="task_xlx_whk_jwb__steps_a5l_xhk_jwb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, either create a new job or navigate to the job to which you want to add credentials variables and choose *Edit*.

2.  In the *Stages* tab of your job, navigate to the stage to which you want to add additional credentials and choose :heavy_plus_sign: next to *Additional Credentials*.

3.  In the *Name* text field, enter a name for the environment variable you want to add. Use only letters, digits, and underscores.

4.  In the *Credentials Name* field, choose a credential you've created in SAP Continuous Integration and Delivery from the dropdown list, or choose *Create Credential* to create a new one. You can use a Basic Authentication, Secret Text, or Service Key credential. See [Creating Credentials](creating-credentials-6658c81.md).

5.  Choose *Create*.

    Now every script that is executed within the stage has access to the environment variable you just created.




<a name="task_xlx_whk_jwb__postreq_gkg_llt_jwb"/>

## Next Steps

Once you've set up the environment variables for your credentials, you can use them in your scripts within a specific stage as follows:

-   For credentials of type Basic Authentication use:

    ```
    #!/bin/bash
    curl -u "$BasicAuth_user:$BasicAuth_password" https://my-server/secured_endpoint
    ```

    Replace `BasicAuth` with the name of your environment variable that has been injected from a basic authentication credential.

    > ### Note:  
    > Since there are two parts to a Basic Authentication credential, you need to add the suffixes "\_user" and "\_password" to access each individual part.

-   For other credential types use:

    ```
    #!/bin/bash
    curl -H "Authorization: Bearer $SecretText" https://my-server/secured_endpoint
    ```

    Replace `SecretText` with the name of your environment variable that has been injected from a credential.


<a name="task_j3h_t3w_dwb"/>

<!-- task\_j3h\_t3w\_dwb -->

## Add Additional Credentials to the Configuration File

Add credential variables to your job using the configuration file in your source code management system.



<a name="task_j3h_t3w_dwb__steps_tfl_psw_dwb"/>

## Procedure

1.  In your source code repository, navigate to the `.pipeline/config.yml` file.

2.  In the service section, depending on the stage in which you want to set the variable \(in this example, the Build stage\), insert the following code block:

    ```
    service:
      stages:
        Build:
          credentialVariables:
            - name: "BasicAuth"
              credentialId: "myCredentials"
    
    ```

    Replace `Build` with the name of the stage to which you want to add your credential variables. If the stage you want to use has spaces in it, put quotes around the stage name, for example `'Additional Unit Tests'` or `"Additional Unit Tests"`.

    For `name`, enter a name for your environment variable. For `credentialID`, enter the *Credentials Name* of the credential you've created in SAP Continuous Integration and Delivery. See [Creating Credentials](creating-credentials-6658c81.md).

    > ### Note:  
    > For `name`, use only letters, digits, and underscores.

    Now every script that is executed in the stage has access to the environment variable you just created.




<a name="task_j3h_t3w_dwb__postreq_vq5_cmt_jwb"/>

## Next Steps

Once you've set up the environment variables for your credentials, you can use them in your scripts within a stage as follows:

-   For credentials of type Basic Authentication use:

    ```
    #!/bin/bash
    curl -u "$BasicAuth_user:$BasicAuth_password" https://my-server/secured_endpoint
    ```

    Replace `BasicAuth` with the name of your environment variable that has been injected from a basic authentication credential.

    > ### Note:  
    > Since there are two parts to a Basic Authentication credential, you need to add the suffixes "\_user" and "\_password" to access each individual part.

-   For other credential types use:

    ```
    #!/bin/bash
    curl -H "Authorization: Bearer $SecretText" https://my-server/secured_endpoint
    ```

    Replace `SecretText` with the name of your environment variable that has been injected from a credential.


