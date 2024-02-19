<!-- loio907b44a608dd4b88b1d77b268fe8a159 -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# \(Optional\) Configure a Credential List

Specify the credentials that are passed to the build.



<a name="loio907b44a608dd4b88b1d77b268fe8a159__prereq_n5l_2bn_xzb"/>

## Prerequisites

-   You are assigned the Administrator role for SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have an existing job that you’ve configured in your repository.




## Context

If you configure SAP Continuous Integration and Delivery jobs in your repository, by default, all credentials defined in the service are passed to the [build](concepts-707017c.md#loio707017c681aa4bc09d0279f08115dcae__section_dxw_cp3_qnb). By configuring a credential list, however, you can specify which credentials are passed and at the same time, can’t be deleted in the user interface. If you create a credential list without specifying any credentials, no credential is passed to the build.



## Procedure

1.  In SAP Continuous Integration and Delivery, open an existing job that uses *Source Repository* as *Configuration Mode*.

2.  In the job overview pane, navigate to the *Credentials* section.

3.  Choose *Create* next to *Credential List*.

4.  Choose :heavy_plus_sign:.

5.  In the *Select Credentials* pop-up, choose the credentials you want to add to your credential list.


