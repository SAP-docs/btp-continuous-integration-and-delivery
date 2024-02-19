<!-- loiod52d3caf559f46a4a977797e740d22c5 -->

# Configure a Multi-Branch Job

Configure a job for multiple branches in your repository.



<a name="loiod52d3caf559f46a4a977797e740d22c5__prereq_q2l_4z1_xlb"/>

## Prerequisites

-   You have set up SAP Continuous Integration and Delivery. See [Initial Setup](initial-setup-719acaf.md).

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a repository and either a CAP, SAPUI5/SAP Fiori, SAP Cloud Integration or container-based applications project in your source code management system.




## Context

When configuring a job for SAP Continuous Integration and Delivery, you're asked to specify the branch from which you want the service to receive push events. Through the webhook connection between your repository and the service, these push events trigger your continuous integration and delivery job.

Instead of defining one specific branch for each job, you can also use special characters to configure jobs that run for multiple branches in your repository.



## Procedure

1.  In SAP Continuous Integration and Delivery, configure a new job as described in [Create a Job](create-a-job-d748920.md).

2.  For *Branch*, enter a common name base of the branches from which you want to receive push events. Use the following wildcard characters to replace the differing parts of your branch names:

    **Wildcard Characters for Multi-Branch Jobs**


    <table>
    <tr>
    <th valign="top">

    Character
    
    </th>
    <th valign="top">

    Function
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    ?
    
    </td>
    <td valign="top">
    
    Matches one character except for slashes

    **Example:** A job configured with `feature_?` builds the branches `feature_1` and `feature_b`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \*
    
    </td>
    <td valign="top">
    
    Matches one or more characters except for slashes

    **Example:** A job configured with `feature_*` builds the branches `feature_1`, `feature_10`, and `feature_new`.
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    \*\*
    
    </td>
    <td valign="top">
    
    Matches one or more characters including slashes

    **Example:** A job configured with `**feature` builds the branches `feature`, `pr/feature`, and `username/pr/feature`.
    
    </td>
    </tr>
    </table>
    



<a name="loiod52d3caf559f46a4a977797e740d22c5__result_zbq_rdx_xmb"/>

## Results

You've configured a job that runs for multiple branches in your repository. If you push changes in one of the branches, the connected continuous integration and delivery job runs for all of them.

If you manually trigger a multi-branch job, a pop-up message asks you to specify the exact branch name. See [Running and Monitoring CI/CD Jobs](running-and-monitoring-ci-cd-jobs-db8521c.md).

