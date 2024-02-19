<!-- loio60a76d7b5a2a46f684515b18e9cbbc08 -->

# Export Job Configuration Data

Export editor-based job configuration information as a YAML file. This allows you to easily move from a editor-based to repository-based configuration when a more advanced configuration of your job is required.



<a name="loio60a76d7b5a2a46f684515b18e9cbbc08__prereq_stg_5hw_pqb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have an existing job in SAP Continuous Integration and Delivery. See [Configuring a Job](administering-jobs-d581ab5.md).

-   In the repository of your project, you have a folder named `.pipeline`, which contains a file named `config.yml`. If you don't have this folder and file, yet, create them.




## Context

If you already have configured your job in the job editor, you can export the configuration data to facilitate the switch to configuration in your repository.



## Procedure

1.  In SAP Continuous Integration and Delivery, navigate to the *Stages* tab of your job and choose *YML* next to *Job Editor*.

2.  Choose *Copy*.

3.  Paste the content into the `.pipeline/config.yml` file in your repository.

4.  In SAP Continuous Integration and Delivery, navigate to your job and choose *Edit*.

5.  In the *Stages* tab of your job, choose *Source Repository* from the *Configuration Mode* dropdown list.

6.  Choose *Save*.


