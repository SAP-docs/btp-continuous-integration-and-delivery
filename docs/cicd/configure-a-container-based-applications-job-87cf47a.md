<!-- loio87cf47a7820d4a00abd8a8526366c129 -->

# Configure a Container-Based Applications Job

Configure the stages of your container-based applications job directly in the SAP Continuous Integration and Delivery service.



<a name="loio87cf47a7820d4a00abd8a8526366c129__prereq_gtz_fsj_x4b"/>

## Prerequisites

-   You are an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have write permission for the repository in which your project sources reside.
-   You have a container registry or a Docker Hub account that stores your container images.
-   You have created a Kubernetes cluster or provisioned the Kyma environment to your SAP BTP subaccount. See [Getting Started in the Kyma Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d1abd18556f24fb091d081b2e3454b8b.html?q=prerequisites%20kubernetes%20cluster%20or%20sap%20kyma%20environment).




## Context

Depending on your configuration, the container-based applications pipeline can comprise the following stages:

![](images/Container_Based_Application_8a14c51.png)

> ### Note:  
> Upon the completion of your pipeline’s run, an additional *Declarative: Post Actions* stage is executed to perform finalization tasks. The outcome of the *Declarative: Post Actions* stage does not influence the success of your build.



## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in  <?sap-ot O2O class="- topic/xref " href="d748920175554221be1ba8b461ada030.xml" text="" desc="" xtrc="xref:7" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/87cf47a7820d4a00abd8a8526366c129.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> . As *Pipeline*, choose *Container-Based Applications*.

2.  In the *Stages* tab, choose *Job Editor* from the *Configuration Mode* dropdown list.

    > ### Note:  
    > After you have configured your job, you can export the editor-based configuration information to a YAML file using the YML button. Choose *Edit* and switch to *Source Repository* to move from editor-based configuration to the more advanced configuration in the source repository when necessary.

3.  In the *Stages* tab, specify the following *General Parameters*:

    **Configuring the General Parameters of a Container-Based Applications Pipeline with the Job Editor**


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
    
    Container Registry URL
    
    </td>
    <td valign="top">
    
    Enter the container registry URL which is used by Kubernetes to push your images.

    The container registry URL must follow the format `<Hostname>:<port>`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Container Image Name
    
    </td>
    <td valign="top">
    
    Enter a name for your container image.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Tag Container Image Automatically
    
    </td>
    <td valign="top">
    
    \(Optional\) If you want your container image to be automatically tagged with a new version for each build, check the *Tag Container Image Automatically* checkbox.

    When you check this checkbox, please add the following line to your container image file directly after the `FROM` line:

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
    
    Container Image Tag
    
    </td>
    <td valign="top">
    
    If you do not want your container image to be automatically tagged, enter a tag for your container image.

    > ### Note:  
    > It is mandatory to configure the parameters above if you want to push content during development or release your application.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Container Registry Credentials
    
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

    Choose this credential from the dropdown list.
    
    </td>
    </tr>
    </table>
    
4.  In the *Stages* tab, configure the *Build* stage as follows:

    **Configuring the Build Stage of a Container-Based Applications Pipeline with the Job Editor**


    <table>
    <tr>
    <th valign="top">

    Stage
    
    </th>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="2">
    
    Build
    
    </td>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    Either switch the execution of the *Build* stage on or off.

    We enable you to configure the build of your application using these options:

    -   Switch the *Build* stage on and specify a *Container Registry URL* to execute the build and push it to your container registry.
    -   Switch the *Build* stage on but do not specify a *Container Registry URL* to execute the build locally.
    -   Switch the *Build* stage off to deploy the content already existing in the container registry.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Container File Path
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter the relative file path to the file containing your container image. The default value is `Dockerfile`.

    > ### Note:  
    > You can skip this step if your container image file is named `Dockerfile` and resides in the main folder of your repository.


    
    </td>
    </tr>
    </table>
    
5.  In the *Stages* tab, configure the *Acceptance* stage as follows:

    **Configuring the Acceptance Stage of a Container-Based Applications Pipeline with the Job Editor**


    <table>
    <tr>
    <th valign="top">

    Stage
    
    </th>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="4">
    
    Acceptance
    
    </td>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    Either switch the execution of the *Acceptance* stage on or off.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Kubernetes Credentials
    
    </td>
    <td valign="top">
    
    To authenticate your pipeline against the Kubernetes cluster in which you want to test your application, create a *Secret Text* credential.

    In the *Secret* field, enter the entire content of your `kubeconfig.yml` file.

    > ### Tip:  
    > Avoid using a technical user credential and create a special test user instead.

    Choose this credential from the dropdown list.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Namespace
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a name for your Kubernetes cluster namespace in which you want to test your application.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Deploy Tool
    
    </td>
    <td valign="top">
    
    Choose between the following deployment tools to deploy your application to the Kubernetes cluster in which you want to test your application:

    -   *helm3*
    -   *kubectl*


    
    </td>
    </tr>
    </table>
    
    1.  For deployment using the *helm3* deploy tool, specify the following parameters in the *Acceptance* stage:

        **Configuring Additional helm3 Parameters of a Container-Based Applications Pipeline with the Job Editor**


        <table>
        <tr>
        <th valign="top">

        Stage
        
        </th>
        <th valign="top">

        Parameter
        
        </th>
        <th valign="top">

        Action
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="7">
        
        Acceptance
        
        </td>
        <td valign="top">
        
        Chart Path
        
        </td>
        <td valign="top">
        
        Enter the path to your Helm chart folder.

        The chart path must contain the `/helm/` subdirectory.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Deployment Name
        
        </td>
        <td valign="top">
        
        Enter a name for your deployment.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Helm Values Path
        
        </td>
        <td valign="top">
        
        \(Optional\) Enter the path to the YAML file containing the Helm values if you want to use placeholders in your Helm chart.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Helm Values Secret
        
        </td>
        <td valign="top">
        
        \(Optional\) You can also set your Helm values using a Secret Text credential. See [Creating Credentials](creating-credentials-6658c81.md).

        In the *Secret* field, enter the entire content of the YALM file containing your Helm values.

        Choose this credential from the dropdown list.

        > ### Note:  
        > You can set both the *Helm Values Path* and *Helm Values Secret* parameters. In case of overlapping fields, *Helm Values Secret* will have priority.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Force Resource Updates
        
        </td>
        <td valign="top">
        
        \(Optional\) If you want to add a force tag to your deployment, check the *Force Resource Updates* checkbox.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Run Helm Tests
        
        </td>
        <td valign="top">
        
        Either switch the execution of Helm tests on or off.

        To run Helm tests, copy them to the following folder:

        `<your_chart_path>/templates/tests`
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Show Test Logs
        
        </td>
        <td valign="top">
        
        \(Optional\) If you want to display the logs of the Helm test results, check the *Show Test Logs* checkbox.
        
        </td>
        </tr>
        </table>
        
    2.  For deployment using the *kubectl* deploy tool, specify the following parameters in the *Acceptance* stage:

        **Configuring Additional kubectl Parameters of a Container-Based Applications Pipeline with the Job Editor**


        <table>
        <tr>
        <th valign="top">

        Stage
        
        </th>
        <th valign="top">

        Parameter
        
        </th>
        <th valign="top">

        Action
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="4">
        
        Acceptance
        
        </td>
        <td valign="top">
        
        Application Template File
        
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
        
        Deploy Command
        
        </td>
        <td valign="top">
        
        Choose between the following Kubernetes deployment commands:

        -   *apply* \(default\)

            Choose this option if you want to create a resource if it does not exist or update it if it already exists.

        -   *replace*

            Choose this option if you want to update and replace an already existing resource.



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Create Container Registry Secret
        
        </td>
        <td valign="top">
        
        If you want to save the *Container Registry Secret* in your Kubernetes cluster, check the *Create Container Registry Secret* checkbox.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Force Resource Updates
        
        </td>
        <td valign="top">
        
        If you want to add a force tag to your deployment, check the *Force Resource Updates* checkbox.

        > ### Note:  
        > This parameter appears only if you choose *replace* in the *Deploy Command* field.


        
        </td>
        </tr>
        </table>
        

6.  In the *Stages* tab, configure the *Release* stage as follows:

    **Configuring the Release Stage of a Container-Based Applications Pipeline with the Job Editor**


    <table>
    <tr>
    <th valign="top">

    Stage
    
    </th>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Action
    
    </th>
    </tr>
    <tr>
    <td valign="top" rowspan="4">
    
    Release
    
    </td>
    <td valign="top">
    
    State
    
    </td>
    <td valign="top">
    
    Either switch the execution of the *Release* stage on or off.

    Switching the *Release* stage on enables you to deploy your application to the defined Kubernetes namespace within the Kubernetes cluster using either the kubectl or helm3 deploy tool.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Kubernetes Credentials
    
    </td>
    <td valign="top">
    
    To authenticate your pipeline against your Kubernetes cluster, create a *Secret Text* credential of a user, who has the appropriate permissions. See [Creating Credentials](creating-credentials-6658c81.md).

    In the *Secret* field, enter the entire content of your `kubeconfig.yml` file.

    > ### Tip:  
    > Use a dedicated service user in your cluster to avoid short-living credentials.

    Choose this credential from the dropdown list.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Namespace
    
    </td>
    <td valign="top">
    
    \(Optional\) Enter a name for your Kubernetes cluster namespace.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    Deploy Tool
    
    </td>
    <td valign="top">
    
    Choose between the following deployment tools to deploy your application to the Kubernetes cluster:

    -   *helm3*
    -   *kubectl*


    
    </td>
    </tr>
    </table>
    
    1.  For deployment using the *helm3* deploy tool, specify the following parameters in the *Release* stage:

        **Configuring Additional helm3 Parameters of a Container-Based Applications Pipeline with the Job Editor**


        <table>
        <tr>
        <th valign="top">

        Stage
        
        </th>
        <th valign="top">

        Parameter
        
        </th>
        <th valign="top">

        Action
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="5">
        
        Release
        
        </td>
        <td valign="top">
        
        Chart Path
        
        </td>
        <td valign="top">
        
        Enter the path to your Helm chart folder.

        The chart path must contain the `/helm/` subdirectory.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Deployment Name
        
        </td>
        <td valign="top">
        
        Enter a name for your deployment.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Helm Values Path
        
        </td>
        <td valign="top">
        
        \(Optional\) Enter the path to the YAML file containing the Helm values if you want to use placeholders in your Helm chart.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Helm Values Secret
        
        </td>
        <td valign="top">
        
        \(Optional\) You can also set your Helm values using a Secret Text credential. See [Creating Credentials](creating-credentials-6658c81.md).

        In the *Secret* field, enter the entire content of the YALM file containing your Helm values.

        Choose this credential from the dropdown list.

        > ### Note:  
        > You can set both the *Helm Values Path* and *Helm Values Secret* parameters. In case of overlapping fields, *Helm Values Secret* will have priority.


        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Force Resource Updates
        
        </td>
        <td valign="top">
        
        If you want to add a force tag to your deployment, check the *Force Resource Updates* checkbox.
        
        </td>
        </tr>
        </table>
        
    2.  For deployment using the *kubectl* deploy tool, specify the following parameters in the *Release* stage:

        **Configuring Additional kubectl Parameters of a Container-Based Applications Pipeline with the Job Editor**


        <table>
        <tr>
        <th valign="top">

        Stage
        
        </th>
        <th valign="top">

        Parameter
        
        </th>
        <th valign="top">

        Action
        
        </th>
        </tr>
        <tr>
        <td valign="top" rowspan="4">
        
        Release
        
        </td>
        <td valign="top">
        
        Application Template File
        
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
        
        Deploy Command
        
        </td>
        <td valign="top">
        
        Choose between the following Kubernetes deployment commands:

        -   *apply* \(default\)

            Choose this option if you want to create a resource if it does not exist or update it if it already exists.

        -   *replace*

            Choose this option if you want to update and replace an already existing resource.



        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Create Container Registry Secret
        
        </td>
        <td valign="top">
        
        If you want to save the *Container Registry Secret* in your Kubernetes cluster, check the *Create Container Registry Secret* checkbox.
        
        </td>
        </tr>
        <tr>
        <td valign="top">
        
        Force Resource Updates
        
        </td>
        <td valign="top">
        
        If you want to add a force tag to your deployment, check the *Force Resource Updates* checkbox.

        > ### Note:  
        > This parameter appears only if you choose *replace* in the *Deploy Command* field.


        
        </td>
        </tr>
        </table>
        

    > ### Note:  
    > You can add environment variables to provide additional configuration to each stage. They will only apply to the stage in which they're defined. For more information, see  <?sap-ot O2O class="- topic/xref " href="c8314b6c8e564f42925e9d10453bd541.xml" text="" desc="" xtrc="xref:12" xtrf="file:/home/builder/src/dita-all/nyp1624030053288/loio3d9e638cafea4b6c8160689ae0af37c8_en-US/src/content/localization/en-us/87cf47a7820d4a00abd8a8526366c129.xml" output-class="" outputTopicFile="file:/home/builder/tp.net.sf.dita-ot/2.3/plugins/com.elovirta.dita.markdown_1.3.0/xsl/dita2markdownImpl.xsl" ?> .

7.  Choose *Create*.


