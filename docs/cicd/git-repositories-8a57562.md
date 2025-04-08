<!-- loio8a57562c7d2d4f7db53a29b2f1e146e9 -->

# Git Repositories

This section provides security-relevant information for SAP Continuous Integration and Delivery jobs connected to Git repositories.

Besides source code, Git repositories can contain scripts and configuration files that might affect the security posture of a pipeline run. The role model concept of SAP Continuous Integration and Delivery is independent from the user management of associated Git repositories. There is no mapping between the roles and permissions configured in the service and the user permissions of the Git repositories.

A user who only has write access to an associated Git repository could manipulate pipeline-related files located in your Git repository. For example, they could manipulate files that are executed during a pipeline run or files containing pipeline configurations to gather information or to tamper with build artifacts. The user doesn't need to be assigned any role in the Continuous Integration and Delivery service to do so - a webhook can automatically start a build that fetches and executes manipulated scripts during the pipeline run. If no webhooks are configured for the repository, maliciously injected scripts can be executed with the next manual or time-triggered build.

The following sections give an overview of the security-relevant information that applies to pipeline-related scripts.



## Build and Test Scripts

Users with write permissions to an associated repository can manipulate build and test scripts located in the Git repository. Most build frameworks and package managers, for example, the Apache Maven software project management tool or the node package manager \(`npm`\), include the ability to execute arbitrary scripts.



## Additional Commands

With the Additional Commands feature, users with the administrator role can define arbitrary command sequences that will be executed before or after a given stage. See [Add Additional Commands to Stages](add-additional-commands-to-stages-c05a252.md).

Due to length limitations and for the sake of simplicity, administrators could decide to add references to more complex scripts located in Git repositories. In this case, however, users who only have write access in the Git repository could edit the scripts that are executed as part of the additional command.

You can separate user permissions for scripts called by additional commands as follows:

**Separate User Permissions for Additional Commands**

If the scripts used in additional commands are stored directly in the Git repository of the project, they are fetched automatically with the project sources. The drawback of this approach is that all users with write access to the source repository of the project and can edit them. To prevent this, one approach is to fetch the scripts from other locations besides the Git repository of the project.

> ### Example:  
> Assume that there is a separate GitHub repository for scripts used in additional commands. You can restrict the write access to this repository according to the principle of least privilege. The additional variable `GIT_REPO_RAW_SCRIPT_URL` holds the URL for a script in this repository. The additional credential `GIT_REPO_TOKEN` points to an SAP Continuous Integration and Delivery credential of type Secret Text with the corresponding access token for the script repository. With the following additional command, you can dynamically fetch and execute a script from a separate Git repository:
> 
> ```
> wget --header="Authorization: token $GIT_REPO_TOKEN" -O - ${GIT_REPO_RAW_SCRIPT_URL} | sh;
> 
> ```

> ### Note:  
> From a security perspective, if you require to separate user permissions for additional commands, we recommend you to opt for the SAP Continuous Integration and Delivery job editor configuration mode. In the source repository configuration mode, users with write access to the associated Git repositories can edit the additional commands directly in the pipeline configuration. See also section [Pipeline Stages Configuration](https://help.sap.com/docs/CONTINUOUS_DELIVERY/f3d64e9188f242ffb7873da5dfad4278/bb2cd0a57fc54525888a6988a7ab704c.html?state=Cloud#pipeline-stages-configuration).



## Pipeline Stages Configuration

With SAP Continuous Integration and Delivery, you can configure your jobs directly in your source repository. The configuration of the pipeline stages is stored there as well, see, for example, [Configure a Cloud Foundry Environment Job in Your Repository](configure-a-cloud-foundry-environment-job-in-your-repository-bfe48a4.md#loiobfe48a4b12ed41868f92fa564829f752). In contrast to the job editor mode, in which you need the administrator role to change the pipeline configuration, with the repository-based configuration, every user with write access to the Git repository of the project can change the pipeline configuration.



<a name="loio8a57562c7d2d4f7db53a29b2f1e146e9__section_nyr_5rf_4xb"/>

## Security Recommendations

The source code repository plays a key role in SAP Continuous Integration and Delivery. We strongly recommend that you put the following operational countermeasures in place:

-   Secure your source code repository with state of the art security techniques, for example, multi-factor authentication.

-   Provide repository write permissions only to persons you trust.

-   Do not use the source repository configuration mode if you have concerns that users with only write access to the repository might tamper the job configuration. In this case, use the job editor configuration mode. This ensures that only users with administrator role can edit the job configuration.

-   Apply the four-eyes principle and make sure each commit is reviewed by someone who is not the commit author.

-   Look for information on how to secure a specific source code repository supported by SAP Continuous Integration and Delivery in its respective documentation.




<a name="loio8a57562c7d2d4f7db53a29b2f1e146e9__section_shw_3xp_ybc"/>

## Trigger Jobs for Specific Commits

With the API, you can trigger a job for a specific commit using the `commitToBeBuilt` parameter. See [Enabling the API Usage](enabling-the-api-usage-1aedc23.md) and [SAP Business Accelerator Hub](https://api.sap.com/api/CloudCiApiSuite/overview).

If a specific Git branch is specified in the job configuration, SAP Continuous Integration and Delivery guarantees that the job is only executed if the commit passed through the API is reachable from the head of the specific branch \(for example, if the commit is an ancestor of the commit at the tip of the specified branch\). If this is not the case, the job fails in the Init stage.

However, if the job is configured as a [multi-branch job](configure-a-multi-branch-job-d52d3ca.md), the job runs for the commit passed through the API, which could undermine security and compliance checks.

> ### Tip:  
> Based on your security and compliance requirements, define a policy that specifies for which scenarios multi-branch jobs are suitable.

