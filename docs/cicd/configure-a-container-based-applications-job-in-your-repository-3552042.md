<!-- loio355204259a90412d86cfc043e504a91f -->

# Configure a Container-Based Applications Job in Your Repository

Configure the stages of your container-based applications job in your source code management system.



<a name="loio355204259a90412d86cfc043e504a91f__prereq_jsb_3gc_clb"/>

## Prerequisites

-   You are an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have write permission for the repository in which your project sources reside.

-   You have a container registry or a Docker Hub account to store your container images.
-   You have created a Kubernetes cluster or provisioned the Kyma environment to your SAP BTP subaccount. See [Getting Started in the Kyma Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d1abd18556f24fb091d081b2e3454b8b.html?q=prerequisites%20kubernetes%20cluster%20or%20sap%20kyma%20environment).

-   In the repository of your project, you have a folder named `.pipeline`, which contains a file named `config.yml`.




## Context

Depending on your configuration, the container-based applications pipeline can comprise the following stages:

![](images/Container_Based_Application_8a14c51.png)



## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in  <?sap-ot O2O class="- topic/xref " href="d748920175554221be1ba8b461ada030.xml" text="" desc="" xtrc="xref:7" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/355204259a90412d86cfc043e504a91f.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . As *Pipeline*, choose *Container-Based Applications*.

2.  In the *Stages* tab, choose *Source Repository* from the *Configuration Mode* dropdown list.

3.  Choose *Create*.

4.  In your `.pipeline/config.yml` file, configure the **general** parameters of your job as follows:

    **General Parameters**

    > ### Sample Code:  
    > ```
    > # Project configuration
    > general:
    >   buildTool: "docker"
    >   containerImageName: "<container_tag>"                              # set all three parameters if you want to release or push your application during build
    >   containerImageTag: "<container_tag>"                               
    >   containerRegistryUrl: "<registry_url>"                             
    >                                     
    > ```

    **Details of the General Parameters**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `buildTool` 
    
    </td>
    <td valign="top">
    
    Enter `"docker"` to execute a build for creating a container image.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `containerImageName` 
    
    </td>
    <td valign="top">
    
    Enter a name for your container image.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `containerImageTag` 
    
    </td>
    <td valign="top">
    
    Enter a tag for your container image.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `containerRegistryURL` 
    
    </td>
    <td valign="top">
    
    Enter the container registry URL which is used by Kubernetes to push your images.

    The container registry URL must follow the format `<Hostname>:<port>`.

    > ### Note:  
    > It is mandatory to configure all the parameters above if you want to push content during development or release your application.


    
    </td>
    </tr>
    </table>
    
5.  Configure the **service** parameters of your job as follows:

    > ### Note:  
    > Please note that some of the **service** parameters need to be nested in stages.

    **Service Parameters**

    > ### Sample Code:  
    > ```
    > 
    > service:
    >   automaticVersioning: false                                     
    >   dockerConfigJsonSecretTextCredentialsId: "<credentials_Id>"
    >   Acceptance:
    >     kubeConfigSecretTextCredentialsId: "<credentials_Id>" 
    >     helmValuePath: "<helmValuesTest.yaml>"   	
    >     helmValueSecret: "<credentials_Id>"                  
    >   Release:
    >     kubeConfigSecretTextCredentialsId: "<credentials_Id>" 
    >     helmValuePath: "<helmValuesTest.yaml>"   	
    >     helmValueSecret: "<credentials_Id>"                                       
    > ```

    **Details of the Service Parameters**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `automaticVersioning` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enable or disable the automatic versioning by choosing either `true` or `false`. Choose `true` if you want your container image to be automatically tagged with a new version for each build.

    > ### Remember:  
    > If you want to use automatic versioning, make sure that you remove `containerImageTag` from your configuration file. Otherwise, automatic versioning will not work.

    When you enable this step, please add the following line to your container image file directly after the `FROM` line:

    ```
    ENV VERSION x.y         
    ```

    `x.y` represents the base version, for example, `1.0`.

    Now your container image will automatically receive a unique version tag with every build, consisting of a unified timestamp in the format `yyyyMMddHHmmss` and a shortened Git commit hash:

    `<ContainerImageName>:<BaseVersion>-<Timestamp>_<ShortGitHash>`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dockerConfigJsonSecretTextCredentialsId` 
    
    </td>
    <td valign="top">
    
    To authenticate your pipeline against your container image repository, create a *Secret Text* credential of a user, who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

    In the *Secret* field, enter the following code and replace the placeholders in brackets with your actual values:

    ```
    {
      "auths": {
        "https://<Container Registry URL>": {
          "username": "<USERNAME>",
          "password": "<PASSWORD OR ACCESS TOKEN>"
        }
      }
    }
    ```

    `"<USERNAME>"` is your container registry username and `"<PASSWORD OR ACCESS TOKEN>"` corresponds to your password or access token.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `kubeConfigSecretTextCredentialsId` 
    
    </td>
    <td valign="top">
    
    To authenticate your pipeline against your Kubernetes cluster, create a *Secret Text* credential.

    In the *Secret* field, enter the entire content of your `kubeconfig.yml` file.

    > ### Tip:  
    > Avoid using a technical user credential and create a special test user instead.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `helmValuePath` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter the path to the file containing the Helm values if you want to use placeholders in your Helm chart.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `helmValueSecret` 
    
    </td>
    <td valign="top">
    
    \(Optional\) You can also set your Helm values using a *Secret Text* credential. See [Creating Credentials](creating-credentials-6658c81.md).

    In the *Secret* field, enter the entire content of the YALM file containing your Helm values.

    Choose this credential from the dropdown list.

    > ### Note:  
    > You can set both the `helmValuePath` and `helmValueSecret` parameters. In case of overlapping fields, `helmValueSecret` will have priority.


    
    </td>
    </tr>
    </table>
    
6.  Configure the **Build** stage of your job as follows:

    > ### Sample Code:  
    > ```
    > # Stages configuration
    > stages:
    >   Build:
    >     kanikoExecute: true                             # true, if you want to turn the build stage on for creating a container image (default: false)
    >   
    > ```

    **Details of the Build Stage**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `kanikoExecute`
    
    </td>
    <td valign="top">
    
    Enable or disable the *Build* stage by choosing either `true` or `false`.
    
    </td>
    <td valign="top">
    
    We enable you to configure the build of your application using these options:

    -   Enable the *Build* stage and specify a *Container Registry URL* to execute the build and push it to your container registry.
    -   Enable the *Build* stage but do not specify a *Container Registry URL* to execute the build locally.
    -   Disable the *Build* stage to deploy the content already existing in the container registry.


    
    </td>
    </tr>
    </table>
    
7.  Depending on which deployment tool you choose, configure the **Acceptance** stage of your job as follows:

    **Acceptance Stage for Deployment with `kubectl` Deploy Tool**

    > ### Sample Code:  
    > ```
    > # Stages configuration specific only to the "kubectl" deployment tool
    >   
    >   Acceptance:
    >     kubernetesDeploy: true                             # true, if you want to turn the acceptance stage on for executing automated end-to-end acceptance tests (default: false)
    >     deployTool: "kubectl" 
    >     namespace: "<namespace>"                           # specify the name of the Kubernetes namespace where you want to test your application (default: "default")
    >     createDockerRegistrySecret: true                   # (optional) true, if you want to save the secret in your Kubernetes cluster
    >     appTemplate: "<path/to/appTemplate.yaml>"          # enter the path to your apptemplate.yaml file
    >     deployCommand: "apply"                             # (optional) or "replace" if you want to update and replace an already existing resource (default: apply) 
    >     force: true                                        # (only for deployCommand "replace") true, if you want to add a force tag to your deployment (default: true)
    > ```

    **Details of the Acceptance Stage Configuration Parameters with kubectl Deploy Tool**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `kubernetesDeploy` 
    
    </td>
    <td valign="top">
    
    Enable or disable the **Acceptance** stage by choosing either `true` or `false`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployTool` 
    
    </td>
    <td valign="top">
    
    Choose `kubectl` as the deployment tool to deploy your application to the Kubernetes cluster.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `namespace` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a name for the Kubernetes cluster namespace. If you don't define a name, a default one \(`"default"`\) is used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `createDockerRegistrySecret` 
    
    </td>
    <td valign="top">
    
    Enable or disable the `createDockerRegistrySecret` step by choosing either `true` or `false`. Enabling the step saves your secret in your Kubernetes cluster.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `appTemplate` 
    
    </td>
    <td valign="top">
    
    Enter the path to the application template YAML file. The application template contains the Kubernetes objects, for example, Deployment, Service and APIRule.

    > ### Tip:  
    > You can also add the following placeholder to your application template YAML file:
    > 
    > `image: <image-name>`.
    > 
    > In this case, instead of using a static value, the image value is taken from the pipeline configuration.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployCommand` 
    
    </td>
    <td valign="top">
    
    Enter one of the following Kubernetes deployment commands:

    -   `apply` \(default\)

        Enter this option if you want to create a resource if it does not exist or update it if it already exists.

    -   `replace`

        Enter this option if you want to update and replace an already existing resource.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `force` 
    
    </td>
    <td valign="top">
    
    Enable or disable the `force` step by choosing either `true` or `false`. Enabling the step adds a force tag to your deployment.

    > ### Note:  
    > Configure this parameter only if you enter `replace` as the `deployCommand` parameter value.


    
    </td>
    </tr>
    </table>
    
    **Acceptance Stage for Deployment with `helm3` Deploy Tool**

    > ### Sample Code:  
    > ```
    > # Stages configuration specific only to the "helm3" deployment tool
    >  
    >   Acceptance:
    >     kubernetesDeploy: true                              # true, if you want to turn the acceptance stage on for executing automated end-to-end acceptance tests (default: false)
    >     deployTool: "helm3"                               
    >     namespace: "<namespace>"                            # (optional) specify the name of the Kubernetes namespace where you want to test your application (default: "default")
    >     chartPath: "helm/<my_chart_folder>"                 # enter the path to your chart folder (has to be in the /helm/ subdirectory)
    >     deploymentName: "<deployment_name>"                  
    >     force: true                                         # (default : true)
    >     runHelmTests: false                                 # (optional) enable Helm tests
    >     showTestLogs: false                                 # (optional) can only be set to true if runHelmTests is true
    > ```

    **Details of the Acceptance Stage Configuration Parameters with helm3 Deploy Tool**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `kubernetesDeploy` 
    
    </td>
    <td valign="top">
    
    Enable or disable the **Acceptance** stage by choosing either `true` or `false`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployTool` 
    
    </td>
    <td valign="top">
    
    Choose `helm3` as the deployment tool to deploy your application to the Kubernetes cluster.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `namespace` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a name for the Kubernetes cluster namespace. If you don't define a name, a default one \(`"default"`\) is used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `chartPath` 
    
    </td>
    <td valign="top">
    
    Enter the path to your Helm chart folder.

    > ### Note:  
    > The chart path must contain the `/helm/`subdirectory.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deploymentName` 
    
    </td>
    <td valign="top">
    
    Enter a name for your deployment.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `force` 
    
    </td>
    <td valign="top">
    
    Enable or disable the `force` step by choosing either `true` or `false`. Enabling the step adds a force tag to your deployment.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `runHelmTests` 
    
    </td>
    <td valign="top">
    
    Enable or disable the execution of Helm tests by choosing either `true` or `false`.

    To run Helm tests, copy them to the following folder:

    `helm/<my_chart_folder>/templates/tests`
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `showTestLogs` 
    
    </td>
    <td valign="top">
    
    Determine if you want to display the logs of the Helm test results by choosing either `true` or `false`.
    
    </td>
    </tr>
    </table>
    
8.  Depending on which deployment tool you choose, configure the **Release** stage of your job as follows:

    **Release Stage for Deployment with `kubectl` Deploy Tool**

    > ### Sample Code:  
    > ```
    > # Stages configuration specific only to the "kubectl" deployment tool
    > 
    >   Release:
    >     kubernetesDeploy: true                                # true, if you want to turn the release stage on for deployment to a Kubernetes namespace within the specified Kubernetes cluster (default: false)
    >     deployTool: "kubectl"                                   
    >     namespace: "<namespace>"                              # (optional) specify the name of the Kubernetes namespace (default: "default")
    >     createDockerRegistrySecret: true                      # (optional) true, if you want to save the secret in your Kubernetes cluster
    >     appTemplate: "<path/to/appTemplate.yaml>"             # enter the path to your apptemplate.yaml file
    >     deployCommand: "apply"                                # (optional) or "replace" if you want to update and replace an already existing resource (default: apply) 
    >     force: true                                           # (only for deployCommand "replace") true, if you want to add a force tag to your deployment
    > 
    > ```

    **Details of the Release Stage Configuration Parameters with kubectl Deploy Tool**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `kubernetesDeploy` 
    
    </td>
    <td valign="top">
    
    Enable or disable the **Release** stage by choosing either `true` or `false`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployTool` 
    
    </td>
    <td valign="top">
    
    Choose `kubectl` as the deployment tool to deploy your application to the Kubernetes cluster.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `namespace` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a name for the Kubernetes cluster namespace. If you don't define a name, a default one \(`"default"`\) is used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `createDockerRegistrySecret` 
    
    </td>
    <td valign="top">
    
    Enable or disable the `createDockerRegistrySecret` step by choosing either `true` or `false`. Enabling the step saves your secret in your Kubernetes cluster.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `appTemplate` 
    
    </td>
    <td valign="top">
    
    Enter the path to the application template YAML file. The application template contains the Kubernetes objects, for example, Deployment, Service and APIRule.

    > ### Tip:  
    > You can also add the following placeholder to your application template YAML file:
    > 
    > `image: <image-name>`.
    > 
    > In this case, instead of using a static value, the image value is taken from the pipeline configuration.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployCommand` 
    
    </td>
    <td valign="top">
    
    Enter one of the following Kubernetes deployment commands:

    -   `apply` \(default\)

        Enter this option if you want to create a resource if it does not exist or update it if it already exists.

    -   `replace`

        Enter this option if you want to update and replace an already existing resource.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `force` 
    
    </td>
    <td valign="top">
    
    Enable or disable the `force` step by choosing either `true` or `false`. Enabling the step adds a force tag to your deployment.

    > ### Note:  
    > Configure this parameter only if you enter `replace` as the `deployCommand` parameter value.


    
    </td>
    </tr>
    </table>
    
    **Release Stage for Deployment with `helm3` Deploy Tool**

    > ### Sample Code:  
    > ```
    > # Stages configuration specific only to the "helm3" deployment tool 
    > 
    >   Release:
    >     kubernetesDeploy: true                                # true, if you want to turn the release stage on for deployment to a Kubernetes namespace within the specified Kubernetes cluster (default: false)
    >     deployTool: "helm3" 
    >     namespace: "<namespace>"                              # (optional) specify the name of the Kubernetes namespace (default: "default")
    >     chartPath: "helm/<my_chart_folder>"                   # enter the path to the chart folder (has to be in the /helm/ subdirectory)
    >     deploymentName: "<deployment_name>"       
    >     force: true                                           # true, if you want to add a force tag to your deployment
    >  
    > ```

    **Details of the Release Stage Configuration Parameters with helm3 Deploy Tool**


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `kubernetesDeploy` 
    
    </td>
    <td valign="top">
    
    Enable or disable the **Release** stage by choosing either `true` or `false`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `kubeConfigSecretTextCredentialsId` 
    
    </td>
    <td valign="top">
    
    To authenticate your pipeline against your Kubernetes cluster, create a *Secret Text* credential of a user, who has the appropriate permissions. See [Creating Credentials](https://help.sap.com/viewer/SAP-Cloud-Platform-Continuous-Integration-and-Delivery/6658c81f3e43456891852955b1ee11db.html).

    In the *Secret* field, enter the entire content of your `kubeconfig.yml` file.

    > ### Tip:  
    > Use a dedicated service user in your cluster to avoid short-living credentials.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deployTool` 
    
    </td>
    <td valign="top">
    
    Choose `helm3` as the deployment tool to deploy your application to the Kubernetes cluster.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `namespace` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a name for the Kubernetes cluster namespace. If you don't define a name, a default one \(`"default"`\) is used.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `chartPath` 
    
    </td>
    <td valign="top">
    
    Enter the path to your Helm chart folder.

    > ### Note:  
    > The chart path must contain the `/helm/`subdirectory.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `deploymentName` 
    
    </td>
    <td valign="top">
    
    Enter a name for your deployment.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `force` 
    
    </td>
    <td valign="top">
    
    Enable or disable the `force` step by choosing either `true` or `false`. Enabling the step adds a force tag to your deployment.
    
    </td>
    </tr>
    </table>
    
9.  Configure the **steps** of your configuration as follows:

    > ### Sample Code:  
    > ```
    > # Steps configuration  
    > 
    >  steps:
    >   kanikoExecute:
    >     dockerfilePath: "<Dockerfile123>"                              # (optional) default: "Dockerfile"
    > ```

    **Details of the Step Configuration**


    <table>
    <tr>
    <th valign="top">

    Step
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `dockerfilePath` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter the relative file path to the file containing your container image. The default value is `Dockerfile`.

    > ### Note:  
    > You can skip this step if your container image file is named `Dockerfile` and resides in the main folder of your repository.


    
    </td>
    </tr>
    </table>
    
    > ### Note:  
    > You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see  <?sap-ot O2O class="- topic/xref " href="c8314b6c8e564f42925e9d10453bd541.xml" text="" desc="" xtrc="xref:11" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/355204259a90412d86cfc043e504a91f.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

10. Commit and push your configuration.




<a name="loio355204259a90412d86cfc043e504a91f__result_vgz_szy_cpb"/>

## Results

Depending on your configuration, your complete `config.yml` file should look as follows:

> ### Sample Code:  
> ```
> # Project configuration
> general:
>   buildTool: "docker"
>   containerImageName: "<container_tag>"
>   containerImageTag: "<container_tag>"
>   containerRegistryUrl: "<registry_url>"
> 
> service:
>   automaticVersioning: false 
>   dockerConfigJsonSecretTextCredentialsId: "<credentials_Id>"
>   Acceptance:
>     kubeConfigSecretTextCredentialsId: "<credentials_Id>" 
>     helmValuePath: "<helmValuesTest.yaml>"   	
>     helmValueSecret: "<credentials_Id>"                  
>   Release:
>     kubeConfigSecretTextCredentialsId: "<credentials_Id>" 
>     helmValuePath: "<helmValuesTest.yaml>"   	
>     helmValueSecret: "<credentials_Id>" 
> 
> # Stages configuration
> stages:
>   Build:
>     kanikoExecute: true  
>             
> # Stages configuration specific only to the "kubectl" deployment tool
>   Acceptance:
>     kubernetesDeploy: true                             
>     deployTool: "kubectl" 
>     namespace: "<namespace>"                             
>     createDockerRegistrySecret: true                  
>     appTemplate: "<path/to/appTemplate.yaml>"           
>     deployCommand: "apply"                             
>     force: true
>   Release:
>     kubernetesDeploy: true                               
>     deployTool: "kubectl"                                   
>     namespace: "<namespace>"                              
>     createDockerRegistrySecret: true                      
>     appTemplate: "<path/to/appTemplate.yaml>"             
>     deployCommand: "apply"                                
>     force: true   
> 
> # Stages configuration specific only to the "helm3" deployment tool
>   Acceptance:
>     kubernetesDeploy: true                             
>     deployTool: "helm3"                               
>     namespace: "<namespace>"                           
>     chartPath: helm/"<my_Chart_Folder>"                   
>     deploymentName: "<deployment_name>"                  
>     force: true                                        
>     runHelmTests: false                                
>     showTestLogs: false
>   Release:
>     kubernetesDeploy: true                               
>     deployTool: "helm3" 
>     namespace: "<namespace>" 						       	
>     chartPath: "helm/<my_Chart_Folder>"					    
>     deploymentName: "<deployment_name>"       
>     force: true										   
>  
> # Steps configuration
> steps:
>   kanikoExecute: 
>     dockerfilePath: "<docker_file_path>"     
> 
> ```

