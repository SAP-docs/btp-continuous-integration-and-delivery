<!-- loiodb8521cc85924f78b7e92b1ea69fdf94 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Running and Monitoring CI/CD Jobs

Trigger the build of a continuous integration and delivery job and monitor its outcome.



<a name="loiodb8521cc85924f78b7e92b1ea69fdf94__prereq_srz_q2v_zkb"/>

## Prerequisites

-   You have connected your Git repository with SAP Continuous Integration and Delivery. See [Add a Repository](add-a-repository-fc55872.md).

-   \(Optional\) You have configured a webhook between your repository and SAP Continuous Integration and Delivery to automate your builds.

-   You have configured a job for your Git repository and branch. See [Create a Job](create-a-job-d748920.md).




<a name="loiodb8521cc85924f78b7e92b1ea69fdf94__steps_ahx_x2v_zkb"/>

## Procedure

1.  To run your job, choose one of the following options:

    -   If you've configured a webhook between your repository and SAP Continuous Integration and Delivery, create a code change and push it to your repository. Thereby, your source code management system sends a push event to SAP Continuous Integration and Delivery, which runs a job.

    -   In the *Jobs* tab in SAP Continuous Integration and Delivery, choose the job for which you want to trigger a build and choose *Run*.


    After a few seconds, a new tile appears in the *Builds* view of your job. Depending on the status of your build, the tile is marked with one of the following icons:

    **Build Statuses**


    <table>
    <tr>
    <th valign="top">

    Icon
    
    </th>
    <th valign="top">

    Status
    
    </th>
    <th valign="top">

    Description
    
    </th>
    </tr>
    <tr>
    <td valign="top">
    
    <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> 
    
    </td>
    <td valign="top">
    
    Waiting
    
    </td>
    <td valign="top">
    
    Build is waiting in queue
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> 
    
    </td>
    <td valign="top">
    
    Deferred
    
    </td>
    <td valign="top">
    
    Build has been temporarily deferred due to too many active builds
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    <span style="color:#666666;"><span class="SAP-icons-V5"></span></span> 
    
    </td>
    <td valign="top">
    
    In Progress
    
    </td>
    <td valign="top">
    
    Build is executed
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    <span style="color:#666666;"><span class="SAP-icons-watt"></span></span> 
    
    </td>
    <td valign="top">
    
    Aborted
    
    </td>
    <td valign="top">
    
    Build has been aborted
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    <span style="color:#cc1919;"><span class="SAP-icons-watt"></span></span> 
    
    </td>
    <td valign="top">
    
    Error
    
    </td>
    <td valign="top">
    
    Build failed due to an error in the project content
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    <span style="color:#cc1919;"><span class="SAP-icons-watt"></span></span> 
    
    </td>
    <td valign="top">
    
    Infrastructure Error
    
    </td>
    <td valign="top">
    
    Build failed due to an error related to the build infrastructure
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    <span style="color:#cc1919;"><span class="SAP-icons-watt"></span></span> 
    
    </td>
    <td valign="top">
    
    Timeout
    
    </td>
    <td valign="top">
    
    Build did not finish within the time limit
    
    </td>
    </tr>
    <tr>
    <td valign="top">
    
    <span style="color:#007833;"><span class="SAP-icons-V5"></span></span> 
    
    </td>
    <td valign="top">
    
    Success
    
    </td>
    <td valign="top">
    
    Build succeeded
    
    </td>
    </tr>
    </table>
    
2.  To view the single stages of your build and their statuses, click on the respective build tile.

3.  To view the detailed log of your build, choose *Show Full Log* in the *Build Stages* view. You can also download it using the *Download Full Log* button.


<a name="concept_s5w_nqv_zkb"/>

<!-- concept\_s5w\_nqv\_zkb -->

## Actions in the Builds View

Cancel, retrigger, and delete a build.

In the *Builds* view of your job, you can perform various actions:



<a name="concept_s5w_nqv_zkb__section_gnq_hrv_zkb"/>

## Cancel a Build

To cancel a pending build or one that is in progress, choose *Cancel* on the respective build tile in the *Builds* view of your job.



<a name="concept_s5w_nqv_zkb__section_bqt_mrv_zkb"/>

## Retrigger a Build

To retrigger a build that has failed due to infrastructural issues, choose *Retrigger* on the respective build tile in the *Builds* view of your job.

> ### Note:  
> The original commit that has triggered the build is reproduced, not the most current one in the branch.



<a name="concept_s5w_nqv_zkb__section_vpd_wrv_zkb"/>

## Delete a Build

To delete a build and remove its metadata and logs, choose *Delete* on the respective build tile in the *Builds* view of your job.

