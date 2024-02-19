<!-- loio9f1c1e29369b45ae89a1d75f2eeae5d0 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Configure a Kyma Runtime Job in Your Repository

Create a job for SAP Cloud Application Programming Model projects in the Kyma Runtime, and configure its stages in your source repository.



<a name="loio9f1c1e29369b45ae89a1d75f2eeae5d0__prereq_h3b_412_gzb"/>

## Prerequisites

-   You have the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   In your source code management system, you have an SAP Cloud Application Programming Model project with the recommended files and folder structure for deploying to a Kyma Runtime. See the [CAP documentation](https://help.sap.com/docs/link-disclaimer?site=https%3A%2F%2Fcap.cloud.sap%2Fdocs%2Fget-started%2F).

-   You have a container registry or a Docker Hub account to store your container images.

-   You provisioned the Kyma Runtime in your SAP BTP cockpit subaccount. See [Getting Started in the Kyma Environment](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/d1abd18556f24fb091d081b2e3454b8b.html?q=prerequisites%20kubernetes%20cluster%20or%20sap%20kyma%20environment).

-   In the repository of your project, you have a folder named `.pipeline` that contains a file named `config.yml`. If you don't have this folder and file yet, create them.



## Context

Depending on your configuration, your Kyma Runtime job can comprise the following stages:

> ### Tip:  
> Hover over the arrow shapes for a short description of each stage.

![](images/Kyma_Pipeline_Steps_245059f.png)

<a name="task_mbj_jkx_1zb"/>

<!-- task\_mbj\_jkx\_1zb -->

## Create a Kyma Runtime Job

Create a job for SAP Cloud Application Programming Model projects in the Kyma Runtime.



<a name="task_mbj_jkx_1zb__steps_alg_nkx_1zb"/>

## Procedure

1.  In the *Jobs* tab in SAP Continuous Integration and Delivery, choose :heavy_plus_sign:.

    As a result, the *Create Job* pane opens.

2.  In the *Job Name* text field, enter a unique name for your job.

    > ### Tip:  
    > We recommend a name that contains both the name and the branch of your project in your source code management system.

3.  In the *Description* text field, enter a meaningful description for your job.

4.  Choose the *Repository* text field to open the *Select Repository* pop-up.

    Either choose your repository from the list or choose *Add Repository* to add your project repository to SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

5.  In the *Branch* text field, enter the branch from which you want to receive push events.

    You can also configure a job for multiple branches in your repository. See [Configure a Multi-Branch Job](configure-a-multi-branch-job-d52d3ca.md).

6.  From the *Pipeline* drop-down list, choose *Kyma Runtime*.

7.  Skip the *Version* drop-down list.

    If you create a new job, the latest version is selected by default. If you edit an existing job, you can change the version by choosing an option from the drop-down list.

8.  To enable your job, choose *ON*.

    By choosing *OFF*, you can deactivate your job without deleting its configuration.

    > ### Note:  
    > Jobs that are created in a trial account or using the Free service plan are automatically deactivated after remaining unchanged for one week. You can use this switch to reactivate them.

9.  In the *Keep logs for* text field in the *Build Retention* section, enter the number of days \(between 1 and 28\) after which your builds are automatically deleted.

10. In the *Keep maximum* text field, enter the maximum number of builds \(between 1 and 99\) you want to keep. If your number of builds exceeds this maximum, the oldest ones are deleted automatically.

11. From the *Configuration Mode* drop-down list, choose *Source Repository*.

    > ### Note:  
    > If you've already created a Kyma Runtime job in the job editor, you can export its configuration information to a YAML file. See [Export Job Configuration Data](export-job-configuration-data-60a76d7.md).

12. \(Optional\) Enable build notifications through the SAP Alert Notification service for SAP BTP. See [Enable Build Notifications](enable-build-notifications-de2a6e3.md).

13. Choose *Create*.


<a name="task_b4v_4nx_1zb"/>

<!-- task\_b4v\_4nx\_1zb -->

## Configure the Stages of Your Kyma Runtime Job

Configure the stages of your Kyma Runtime job in your source repository.



<a name="task_b4v_4nx_1zb__steps_wx2_h4x_1zb"/>

## Procedure

1.  Check if in your source repository project, there is a folder named `.pipeline``config.yml`. If you don't have this folder and file, yet, create them.

2.  In the `.pipeline/config.yml` file, add the following basic structure:

    ```
    # Project configuration
    general:
    
    service:
    
    # Stages configuration
    stages:
    
    # Steps configuration
    steps:
    ```

    For the relation between pipelines, stages, and steps, see [Concepts](concepts-707017c.md).

3.  In the `# Project configuration` section, add the following parameters:

    > ### Sample Code:  
    > ```
    > general:
    >   buildTool: "npm"
    >   chartPath: path/to/helmChart
    > service:
    >   buildToolVersion: "N18"
    > ```


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `buildTool` 
    
    </td>
    <td valign="top">
    
    The build tool you want to use. See [Supported Tools](supported-tools-5949283.md).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `chartPath` 
    
    </td>
    <td valign="top">
    
    The path to the Helm chart in your source repository. For how to generate the relevant files, see [About CAP Helm Chart](https://cap.cloud.sap/docs/guides/deployment/deploy-to-kyma#about-cap-helm).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `buildToolVersion` 
    
    </td>
    <td valign="top">
    
    The version of the build tool you want to use. See [Supported Tools](supported-tools-5949283.md).
    
    </td>
    </tr>
    </table>
    
4.  Configure the stages of your job as follows:

    > ### Note:  
    > The following sections correspond to the stages of your Kyma Runtime job. Open them for more information.


<a name="task_olt_1px_1zb"/>

<!-- task\_olt\_1px\_1zb -->

### Build



<a name="task_olt_1px_1zb__steps_y5n_rw2_bzb"/>

## Procedure

1.  \(Optional\) If you use the `npm` build tool, you can run additional scripts. To do that, first run a `cds build` to make sure that all folders are set up correctly for creating the images. Next, set up the scripts in your `package.json` file. For example:

    > ### Sample Code:  
    > ```
    > "cds-build": "npm install --include=dev && cds build --production"
    > ```

2.  In your `.config.yml` file, add the following step to the `# Steps configuration` section:

    > ### Sample Code:  
    > ```
    > steps:
    >   buildExecute:
    >     npmRunScripts: [ 'cds-build' ]  
    >     npmInstall: false             
    >     cnbBuild: true                  
    >     helmExecute: true  
    > ```


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `npmRunScripts` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Contains a list of script names that should be run during the Build stage.

    > ### Restriction:  
    > This parameter is only available for the `npm` build tool. See the previous step.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `npmInstall` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Depending on your configuration, either runs an `npm install` or `yarn install`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `cnbBuild` 
    
    </td>
    <td valign="top">
    
    Activates the Cloud Native Buildpack based container image build. This parameter must be set to **true**.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `helmExecute` 
    
    </td>
    <td valign="top">
    
    \(Optional\) This parameter enables downloading of Helm chart dependencies. If your chart does not have dependencies, you can leave it set to **false**. If set to **true**, you must also configure `steps.helmExecute`.

    See [Helm Dependency Update](https://helm.sh/docs/helm/helm_dependency_update/).
    
    </td>
    </tr>
    </table>
    
3.  Configure the `cnbBuild` step.

    > ### Sample Code:  
    > ```
    > steps:
    >   cnbBuild:
    >     containerRegistryUrl: https://my.registry.url.com
    >     dockerConfigJsonCredentialsId: docker-config
    >     multipleImages:
    >       - path: path/to/directoryOrArtifact
    >         containerImageName: image/name
    >       - path: path/to/directoryOrArtifact
    >         containerImageName: image/name2
    >         containerImageAlias: image2	# Optional (see Value description)
    >         containerImageTag: v1.0.0	  # Optional
    >       - path: target/myApp-*.jar
    >         containerImageName: image/name3
    > ```

    ****


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `containerRegistryUrl`
    
    </td>
    <td valign="top">
    
    Enter the URL of the container registry where you want to push the build container images.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `dockerConfigJsonCredentialsId`
    
    </td>
    <td valign="top">
    
    Enter the ID of a container registry credential with permissions to push images to the specified container registry. See [Creating Credentials](https://help.sap.com/docs/continuous-integration-and-delivery/sap-continuous-integration-and-delivery/creating-credentials?version=Cloud).
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `multipleImages`
    
    </td>
    <td valign="top">
    
    You can add several container images \(at least one\) to your Kyma Runtime job. The images are created during the Build stage.

    ****


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `path`
    
    </td>
    <td valign="top">
    
    The path that either points to a source directory or an artifact in `ZIP` format. This property determines the input to the buildpack. The path can have wildcard characters.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `containerImageName`
    
    </td>
    <td valign="top">
    
    The container image name.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `containerImageAlias`
    
    </td>
    <td valign="top">
    
    \(Optional\) The alias for the container image.

    > ### Note:  
    > If the `containerImageName` contains . characters, add a `containerImageAlias` without . characters.


    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `containerImageTag`
    
    </td>
    <td valign="top">
    
    \(Optional\) The tag for the container image. If you don't set a tag, latest is used.
    
    </td>
    </tr>
    </table>
    

    
    </td>
    </tr>
    </table>
    
4.  Configure the `kubernetesDeploy` step.

    The **cnbBuild** step generates container images and pushes them to a container registry. In order to use those exact images, the \(dynamic\) repository and tag parameters need to be injected as Helm chart values during the deployment.

    You need to configure `valueMappings` specific to your Helm chart and generated images. The value mappings are a bit tricky because not only do you have to care for the value, but you also have to care for the key \(left side in front of the : \).

    **< \> Sample Code**

    ```
    steps:
      kubernetesDeploy:
        valuesMapping:
          # --- Definition ---
          # <defined.repository.value.path>: image.<defined-image-name>.repository
          # <defined.tag.value.path>: image.<defined-image-name>.tag
    
          # --- Example with containerImageName ---
          app1.image.repository: image.image/name.repository
          app1.image.tag: image.image/name.tag
          # --- Example with containerImageAlias ---
          app2.image.repository: image.image2.repository
          app2.image.tag: image.image2.tag
    ```


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `<defined.repository.value.path>` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Define the path to the repository value in your Helm chart and the image you want to use.

    -   For the **key** \(left side\), define the path in the Helm chart values to the **repository** parameter of this image.

    -   For the **value** \(right side\), define `image.<defined-image-name>.repository` where `<defined-image-name>` is replaced by either the `containerImageName` or `containerImageAlias` as defined in the **cnbBuild** configuration.



    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `<defined.tag.value.path>` 
    
    </td>
    <td valign="top">
    
    \(Optional\) Define the path to the tag value in your Helm chart and the image you want to use.

    -   For the **key** \(left side\), define the path in the Helm chart values to the **tag** parameter of this image.

    -   For the **value** \(right side\), define `image.<defined-image-name>.tag` where `<defined-image-name>` is replaced by either the `containerImageName` or `containerImageAlias` as defined in the **cnbBuild** configuration.



    
    </td>
    </tr>
    </table>
    
5.  Add the following step to the `# Steps configuration`:

    > ### Sample Code:  
    > ```
    > steps:
    >   helmExecute:
    >     helmCommand: dependency
    >     dependency: update
    > ```

    This step is mandatory if in the `buildExecute` step, `helmExecute` is set to `true`.

6.  Run a lint check.

    > ### Sample Code:  
    > ```
    > # Stages configuration
    > stages:
    >   Build:
    >     npmExecuteLint: true
    > ```

    ****


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `npmExecuteLint`
    
    </td>
    <td valign="top">
    
    Run a lint check to verify the syntax of your JavaScript code.

    By default, this stage executes linting with a general-purpose configuration. It doesn’t fail through lint findings but warns you against potential errors in the programming style.

    > ### Note:  
    > You must have at least one JavaScript or TypeScript file in your project.


    
    </td>
    </tr>
    </table>
    

<a name="task_ygs_gpx_1zb"/>

<!-- task\_ygs\_gpx\_1zb -->

### Additional Unit Tests



<a name="task_ygs_gpx_1zb__steps_kv4_5z2_bzb"/>

## Procedure

In the `# Stages configuration` section, add the following stage:

> ### Sample Code:  
> ```
>   Additional Unit Tests:
>      karmaExecuteTests: false   # true, if you want to execute the Karma Test Runner
>      npmExecuteScripts: false   # true, if you want to execute test scripts that you've defined in the npmExecuteScripts step
> ```


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`karmaExecuteTests` 

</td>
<td valign="top">

\(Optional\) Executes the [Karma Test Runner](http://karma-runner.github.io/latest/index.html).

</td>
</tr>
<tr>
<td valign="top">

`npmExecuteScripts` 

</td>
<td valign="top">

\(Optional\) Executes additional test scripts that you've defined in your `package.json` file.

> ### Restriction:  
> This parameter is only available for the `npm` build tool.



</td>
</tr>
</table>

<a name="task_exy_gbt_bzb"/>

<!-- task\_exy\_gbt\_bzb -->

#### \(Optional\) Add Additional Unit Tests to Your Job

Add the test configuration for the Additional Unit Tests stage to your project.



<a name="task_exy_gbt_bzb__steps_t5l_qbt_bzb"/>

## Procedure

1.  Make sure that the following dependencies and scripts are part of your `package.json` file:

    > ### Sample Code:  
    > ```
    > {
    >     (...)
    >     "devDependencies": {
    >         (...)
    >         "karma": "^5.0.4",
    >         "karma-chrome-launcher": "^3.1.0",
    >         "karma-coverage": "^2.0.2",
    >         "karma-ui5": "^2.1.0"
    >     },
    >     "scripts": {
    >         (...)
    >         "test": "karma start",
    >     }
    > }
    > ```

2.  In the same folder as your `package.json` file, add a file named `karma.conf.js`.

3.  Add the following minimal configuration to your `karma.conf.js` file to describe that the tests should use a custom web driver launcher to connect to a remote Chrome browser:

    > ### Sample Code:  
    > ```
    >  ```
    >  module.exports = function(config) {
    >      config.set({
    >         frameworks: ["ui5"],
    >         ui5: {
    >            url: "https://ui5.sap.com"
    >         },
    >         browsers: ["ChromeHeadless"],
    >         browserConsoleLogOptions: {
    >            level: "error"
    >         },
    >         singleRun: true
    >      });
    >  };
    >  ```
    > ```

4.  To report the coverage and see the coverage data in the logs, add the following additional configuration to the file:

    > ### Sample Code:  
    > ```
    > ```
    > module.exports = function(config) {
    >   config.set({
    > 
    >     frameworks: ["ui5"],
    >     ui5: {
    >       url: "https://ui5.sap.com"
    >     },
    >     preprocessors: {
    > 			"{webapp,webapp/!(test)}/!(mock*).js": ["coverage"]
    > 		},
    >     coverageReporter: {
    >             includeAllSources: true,
    >             reporters: [
    >                 {
    >                     type: "html",
    >                     dir: "coverage"
    >                 },
    >                 {
    >                     type: "text"
    >                 }
    >             ],
    >     check: {
    >        each: {
    >                statements: <THRESHOLD>,
    >                branches: <THRESHOLD>,
    >                functions: <THRESHOLD>,
    >                lines: <THRESHOLD>
    >                 }
    >             }
    >         },
    >      reporters: ["progress", "coverage"],
    > 
    >     browsers: ["ChromeHeadless"],
    >     browserConsoleLogOptions: {
    >          level: "error"
    >     },
    >     singleRun: true
    >   });
    > };
    > ```
    > ```

    For `<THRESHOLD>`, enter the percentage of your code that you want to cover with tests. If the defined threshold isn’t met, the build breaks.


<a name="task_jbb_3px_1zb"/>

<!-- task\_jbb\_3px\_1zb -->

### Acceptance



<a name="task_jbb_3px_1zb__steps_e2f_k2f_bzb"/>

## Procedure

In the `# Stages configuration` section, add the following stage:

> ### Sample Code:  
> ```
>   Acceptance:
>     kubernetesDeploy: false        # true, if you want to deploy to Kubernetes during the Acceptance stage
>     kubeConfigFileCredentialsId: kube-config
>     deploymentName: helm-release-name
>     namespace: kyma-namespace 
>     helmValues:
>     - acceptance.yaml
>     additionalParameters:
>       - --debug
>       - --set
>       - global.imagePullSecret.name=existing-secret-in-kyma-namespace
>       - --set
>       - my.path=myValue
> ```


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`kubernetesDeploy` 

</td>
<td valign="top">

Turns the deployment for the Acceptance stage and the Acceptance stage itself either on or off.

</td>
</tr>
<tr>
<td valign="top">

`kubeConfigFileCredentialsId` 

</td>
<td valign="top">

Credentials of the type Kubernetes Configuration used for accessing the Kyma cluster

</td>
</tr>
<tr>
<td valign="top">

`deploymentName` 

</td>
<td valign="top">

The name of the Helm release that will be shown in the Kyma namespace. Start with an alphanumeric character and only use lower case alphanumeric characters, `-` characters, or `.` characters. `-` and `.` characters can't be next to each other.

</td>
</tr>
<tr>
<td valign="top">

`namespace` 

</td>
<td valign="top">

Specifies the Kyma namespace where the Helm release should be deployed.

</td>
</tr>
<tr>
<td valign="top">

`helmValues` 

</td>
<td valign="top">

Define yaml file\(s\) with Helm values to be set during the deployment of the Helm chart.

</td>
</tr>
<tr>
<td valign="top">

`additionalParameters` 

</td>
<td valign="top">

Define values to be set for the specified Helm value paths during the deployment of the Helm chart.

</td>
</tr>
</table>

<a name="task_prq_jct_bzb"/>

<!-- task\_prq\_jct\_bzb -->

#### \(Optional\) Add wdi5 Tests to Your Job

Enable wdi5 tests in your project.



<a name="task_prq_jct_bzb__steps_cgx_4ct_bzb"/>

## Procedure

In your `config.yml` file, add the following parameters to your Acceptance stage configuration:

> ### Sample Code:  
> ```
>   npmExecuteEndToEndTests:
>     runScript: 'wdio'
>     baseUrl: '<base-url>'
>     credentialsId: 'myUI5Credential'
> ```


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`runScript` 

</td>
<td valign="top">

The name of the test script to be executed

</td>
</tr>
<tr>
<td valign="top">

`baseURL` 

</td>
<td valign="top">

URL of the application against which the tests should be executed

</td>
</tr>
<tr>
<td valign="top">

`credentialsID` 

</td>
<td valign="top">

\(Optional\) Basic authentication credentials needed to access the running application

You can access the username and password in your individual test files by using:

```
    const usernameVar=process.env.e2e_username
    const passwordVar=process.env.e2e_password
```



</td>
</tr>
</table>

<a name="task_dry_3px_1zb"/>

<!-- task\_dry\_3px\_1zb -->

### Compliance



<a name="task_dry_3px_1zb__steps_ng3_bbf_bzb"/>

## Procedure

1.  In the `# Stages configuration` section, add the following stage:

    > ### Sample Code:  
    > ```
    >   Compliance:
    >     sonarExecuteScan: false   # true, if you want to add SonarQube scans to your job
    > ```


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `sonarExecuteScan` 
    
    </td>
    <td valign="top">
    
    Integrates continuous code quality and security analysis into your pipeline.

    > ### Restriction:  
    > For this stage, you need a running SonarQube server or SonarCloud instance. For more information, see [Sonar](https://www.sonarsource.com/products/sonarqube/).


    
    </td>
    </tr>
    </table>
    
2.  \(Optional\) If in the `Compliance` stage, you've set the `sonarExecuteScan` parameter to `true`, add the following step to the `# Steps configuration` section:

    > ### Sample Code:  
    > ```
    >   sonarExecuteScan:
    >     mode: "SonarCloud"
    >     serverUrl: "https://sonarcloud.io"
    >     organization: "org"
    >     projectKey: "pk"
    >     sonarTokenCredentialsId: "token"
    > ```


    <table>
    <tr>
    <th valign="top">

    Parameter
    
    </th>
    <th valign="top">

    Value
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    `mode` 
    
    </td>
    <td valign="top">
    
    The type of Sonar instance you use: Either `SonarQube` or `SonarCloud`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `serverUrl` 
    
    </td>
    <td valign="top">
    
    The full URL to your backend system. If you use `SonarQube`, enter the custom URL to your internet-facing SonarQube server.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `organization` 
    
    </td>
    <td valign="top">
    
    \(Optional\) If you use `SonarCloud`, enter the organization for your project.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `projectKey` 
    
    </td>
    <td valign="top">
    
    The project key for your project
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    `sonarTokenCredentialsId` 
    
    </td>
    <td valign="top">
    
    ID of a Secret Text credential to authenticate your pipeline against your SonarQube instance
    
    </td>
    </tr>
    </table>
    

<a name="task_x4k_jpx_1zb"/>

<!-- task\_x4k\_jpx\_1zb -->

### Release



<a name="task_x4k_jpx_1zb__steps_rcz_rgt_bzb"/>

## Procedure

In the `# Stages configuration` section, add the following stage:

> ### Sample Code:  
> ```
>   Release:
>     kubernetesDeploy: false        # true, if you want to deploy to Kubernetes during the Release stage
>     kubeConfigFileCredentialsId: kube-config
>     deploymentName: helm-release-name
>     namespace: kyma-namespace 
>     helmValues:
>     - generic.yaml
>     - release.yaml
>     additionalParameters:
>       - --debug
>       - --set
>       - global.imagePullSecret.name=existing-secret-in-kyma-namespace
>       - --set
>       - my.path=myValue
> ```


<table>
<tr>
<th valign="top">

Parameter

</th>
<th valign="top">

Value

</th>
</tr>
<tr>
<td valign="top">

`kubernetesDeploy` 

</td>
<td valign="top">

Turns the deployment for the Release stage and the Release stage itself either on or off.

</td>
</tr>
<tr>
<td valign="top">

`kubeConfigFileCredentialsId` 

</td>
<td valign="top">

Credentials of the type Kubernetes Configuration used for accessing the Kyma cluster

</td>
</tr>
<tr>
<td valign="top">

`deploymentName` 

</td>
<td valign="top">

The name of the Helm release that will be shown in the Kyma namespace. Start with an alphanumeric character and only use lower case alphanumeric characters, `-` characters, or `.` characters. `-` and `.` characters can't be next to each other.

</td>
</tr>
<tr>
<td valign="top">

`namespace` 

</td>
<td valign="top">

Specifies the Kyma namespace where the Helm release should be deployed.

</td>
</tr>
<tr>
<td valign="top">

`helmValues` 

</td>
<td valign="top">

Define yaml file\(s\) with Helm values to be set during the deployment of the Helm chart.

</td>
</tr>
<tr>
<td valign="top">

`additionalParameters` 

</td>
<td valign="top">

Define values to be set for the specified Helm value paths during the deployment of the Helm chart.

</td>
</tr>
</table>

<a name="concept_ak2_4wx_1zb"/>

<!-- concept\_ak2\_4wx\_1zb -->

## Example of a Complete Kyma Runtime Job Configuration

Depending on your configuration, your complete `.pipeline/config.yml` file can look as follows:

> ### Sample Code:  
> ```
> general:
>   buildTool: "npm"
>   chartPath: charts/project
> service:
>   buildToolVersion: "N18"
> stages:
>   Build:
>     npmExecuteLint: true
>   Additional Unit Tests:
>     npmExecuteScripts: true
>   Acceptance:
>     npmExecuteEndToEndTests: true
>     deploymentName: deploy-acceptance
>     kubeConfigFileCredentialsId: kube-config-acceptance
>     namespace: namespace-acceptance
>     additionalParameters:
>       - --set
>       - customer.defined.acceptance.imagePullSecret.name=secrets-acceptance
>       - --set
>       - customer.defined.path=customer-defined-value
>     helmValues:
>       - generic.yaml
>       - acceptance.yaml
>   Compliance:
>     sonarExecuteScan: true
>   Release:
>     kubernetesDeploy: true
>     deploymentName: deploy-release
>     kubeConfigFileCredentialsId: kube-config-release
>     namespace: namespace-release
>     additionalParameters:
>       - --set
>       - customer.defined.release.imagePullSecret.name=secrets-release
> steps:
>   npmExecuteLint:
>     failOnError: true
>   npmExecuteScripts:
>     runScripts:
>       - "test"
>   sonarExecuteScan:
>     mode: "SonarCloud"
>     serverUrl: "https://sonarcloud.io"
>     organization: "org"
>     projectKey: "pk"
>     sonarTokenCredentialsId: "token"
>   npmExecuteEndToEndTests:
>     runScript: "config.js"
>     baseUrl: "https://test.sap.com"
>     credentialsId: "appcred"
>   buildExecute:
>     npmRunScripts: [ 'cds-build' ]
>     npmInstall: false
>     cnbBuild: true
>     helmExecute: true
>   cnbBuild:
>     containerRegistryUrl: https://my.registry.url.com
>     dockerConfigJsonCredentialsId: docker-config
>     multipleImages:
>       - path: path/to/directoryOrArtifact
>       containerImageName: image/name
>       - path: path/to/directoryOrArtifact
>       containerImageName: image/name2
>       containerImageAlias: image2 # Optional (see Value description)
>       containerImageTag: v1.0.0 # Optional
>   helmExecute:
>     helmCommand: dependency
>     dependency: update
>   kubernetesDeploy:
>     valuesMapping:
>       app1.image.repository: image.image/name.repository
>       app1.image.tag: image.image/name.tag
>       app2.image.repository: image.image2.repository
>       app2.image.tag: image.image2.tag
> ```

