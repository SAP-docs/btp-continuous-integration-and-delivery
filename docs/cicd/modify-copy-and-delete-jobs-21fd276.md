<!-- loio21fd276e5a014f18a9de7ec38aab57b1 -->

# Modify, Copy, and Delete Jobs

Modify, copy, or delete an existing job in SAP Continuous Integration and Delivery.



<a name="loio21fd276e5a014f18a9de7ec38aab57b1__prereq_pcy_jbz_ykb"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have an existing job in SAP Continuous Integration and Delivery. See [Configuring a Job](administering-jobs-d581ab5.md).




<a name="loio21fd276e5a014f18a9de7ec38aab57b1__steps_w4c_fkz_ykb"/>

## Procedure

1.  In the *Jobs* tab in SAP Continuous Integration and Delivery, choose the job you want to modify, copy, or delete.

2.  Depending on what you want to do, choose either *Edit*, *Copy*, or *Delete*.

3.  Choose one of the options:

    1.  If you chose *Edit*, make the necessary modification and choose *Save*.
    2.  If you chose *Copy*, your existing job will be duplicated. Enter a new *Job Name* and, depending on your needs, adapt or keep the existing parameters. Choose *Create.*
    3.  If you chose *Delete*, confirm the deletion. Deleting a job removes all metadata and build logs that belong to it.

    > ### Note:  
    > Deleting a job doesn’t remove webhooks. They must be manually removed in your source code management system. As webhooks work on repository level, you should remove them only if you have deleted all jobs of a repository.




<a name="loio21fd276e5a014f18a9de7ec38aab57b1__result_dyy_32z_ykb"/>

## Results

You have successfully modified, copied, or deleted your job.

