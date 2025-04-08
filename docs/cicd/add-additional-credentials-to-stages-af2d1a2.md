<!-- loioaf2d1a253d0d4f35b17935ab42f32a0b -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Add Additional Credentials to Stages

Add environment variables that store values injected from credentials to the stages of your job.

You can configure additional credentials using either the job editor or the configuration file in your source code management system.

> ### Tip:  
> Depending on which configuration mode you choose, expand one of the following sections for more information.

<a name="task_xlx_whk_jwb"/>

<!-- task\_xlx\_whk\_jwb -->

## Configure Additional Credentials Using the Job Editor

Add additional credentials to your job using the job editor in the SAP Continuous Integration and Delivery user interface.



<a name="task_xlx_whk_jwb__steps_a5l_xhk_jwb"/>

## Procedure

1.  In SAP Continuous Integration and Delivery, either create a new job or navigate to the job to which you want to add credentials variables and choose *Edit*.

2.  In the *Stages* section of your job, navigate to the stage to which you want to add additional credentials and choose :heavy_plus_sign: next to *Additional Credentials*.

3.  In the *Name* text field, enter a name for the environment variable you want to add. Use only letters, digits, and underscores.

4.  In the *Credentials Name* field, either choose a credential you've created in SAP Continuous Integration and Delivery from the dropdown list, or choose *Create Credential* to create a new one. You can use a Basic Authentication, Secret Text, or Service Key credential. See [Creating Credentials](creating-credentials-6658c81.md).

5.  Choose *Create*.


<a name="task_j3h_t3w_dwb"/>

<!-- task\_j3h\_t3w\_dwb -->

## Configure Additional Credentials in the Configuration File

Add additional credentials to your job using the configuration file in your source code management system.



<a name="task_j3h_t3w_dwb__steps_tfl_psw_dwb"/>

## Procedure

1.  In your source code repository, navigate to the `.pipeline/config.yml` file.

2.  In the `service` section, depending on the stage in which you want to set the commands, insert a code block as follows. In this example, the additional command is added to the Build stage:

    ```
    service:
      stages:
        Build:
          credentialVariables:
            - name: "BasicAuth"
              credentialId: "myCredentials"
    
    ```

    Replace `Build` with the name of the stage to which you want to add your credential variables. If the name of the stage you want to use has spaces in it, put quotes around the stage name, for example `'Additional Unit Tests'` or `"Additional Unit Tests"`.

    For `name`, enter a name for your environment variable. For `credentialID`, enter the *Credential Name* of the credential you've created in SAP Continuous Integration and Delivery. See [Creating Credentials](creating-credentials-6658c81.md).

    > ### Note:  
    > For `name`, use only letters, digits, and underscores.


<a name="concept_wyj_fg4_42c"/>

<!-- concept\_wyj\_fg4\_42c -->

## Use Additional Credentials in Stages

Once you've set up the environment variables for your credentials, you can use them in your processes within a specific stage.

The content of the injected variable depends on the credential type:


<table>
<tr>
<th valign="top">

Credential Type

</th>
<th valign="top">

Variable Content

</th>
</tr>
<tr>
<td valign="top">

Basic Authentication

</td>
<td valign="top">

Assuming the chosen variable name is `VAR`, two environment variables will be injected:

-   `VAR_user` which contains the user name
-   `VAR_password` which contains the password



</td>
</tr>
<tr>
<td valign="top">

Basic Authentication for Custom IdP

</td>
<td valign="top">

The variable contains a JSON document with the following structure:

```
{
    "username": "...",
    "password": "...",
    "origin": "..."
}
```



</td>
</tr>
<tr>
<td valign="top">

Service Key

</td>
<td valign="top">

The variable contains the content of the credential, which is the service key in JSON format.

</td>
</tr>
<tr>
<td valign="top">

Secret Text

</td>
<td valign="top">

The variable contains the content of the credential.

</td>
</tr>
<tr>
<td valign="top">

Cloud Connector

</td>
<td valign="top">

The variable contains an HTTP URL of the connectivity proxy. Requests sent via that proxy will be tunneled through the Cloud Connector defined in the credential.

In the following example, the variable is named `PROXY`:

> ### Sample Code:  
> ```
> curl --proxy "$PROXY" http://my-virtual-system
> ```



</td>
</tr>
<tr>
<td valign="top">

Container Registry Configuration

</td>
<td valign="top">

The variable contains the content of the credential, which is the container registry configuration, typically in JSON format.

</td>
</tr>
<tr>
<td valign="top">

Kubernetes Configuration

</td>
<td valign="top">

The variable contains the content of the credential, which is the Kubernetes configuration, typically in yaml format.

</td>
</tr>
</table>

