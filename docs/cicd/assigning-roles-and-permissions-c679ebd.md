<!-- loioc679ebdbe76142bd9fb1071e5e53511d -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Assigning Roles and Permissions

Manage the authorization for SAP Continuous Integration and Delivery.



<a name="loioc679ebdbe76142bd9fb1071e5e53511d__prereq_e2j_gvp_tdb"/>

## Prerequisites

> ### Note:  
> If you are using this service as part of SAP Build Code, follow the [SAP Build Code Initial Setup](https://help.sap.com/docs/build_code/d0d8f5bfc3d640478854e6f4e7c7584a/07698d7c31284e4db370acdf017cfd14.html?version=SHIP) instructions instead.

-   You’re an administrator of your global account and subaccount on SAP BTP.

-   **If you use an enterprise account \(no trial account\):** You’re a User & Role Administrator of your subaccount on SAP BTP and can therefore view the :shield: *Security* section in its navigation pane. See [Managing Subaccounts Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/55d0b6d8b96846b8ae93b85194df0944.html).

-   You've enabled SAP Continuous Integration and Delivery. See [Enabling the Service](enabling-the-service-c8ed09d.md).




<a name="loioc679ebdbe76142bd9fb1071e5e53511d__context_z3t_m3q_tdb"/>

## Context

There are two different roles for SAP Continuous Integration and Delivery: **Administrator** and **Developer**.

The following table provides an overview of their permissions:


<table>
<tr>
<th valign="top">

Category

</th>
<th valign="top">

Permission

</th>
<th valign="top">

Administrator

</th>
<th valign="top">

Developer

</th>
</tr>
<tr>
<td valign="top" rowspan="4">

Credentials

</td>
<td valign="top">

Create a credential

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Modify a credential

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Delete a credential

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

View a credential\*

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

**Yes** 

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Jobs

</td>
<td valign="top">

Create a job

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Modify a job

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Delete a job

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

View a job

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

**Yes** 

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Repositories

</td>
<td valign="top">

Create a repository

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Modify a repository

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

Delete a repository

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

No

</td>
</tr>
<tr>
<td valign="top">

View a repository

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

**Yes** 

</td>
</tr>
<tr>
<td valign="top" rowspan="4">

Builds

</td>
<td valign="top">

Trigger a build

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

**Yes** 

</td>
</tr>
<tr>
<td valign="top">

View a build

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

**Yes** 

</td>
</tr>
<tr>
<td valign="top">

Delete a build

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

**Yes** 

</td>
</tr>
<tr>
<td valign="top">

View a build log

</td>
<td valign="top">

**Yes** 

</td>
<td valign="top">

**Yes** 

</td>
</tr>
</table>

\*You can only view the metadata of a credential. Once it has been entered, the secret itself is hidden.

Corresponding to its roles, SAP Continuous Integration and Delivery comes with two predefined role collections: **CICD Service Administrator** and **CICD Service Developer**. The following procedure shows how you can assign them to your users.



<a name="loioc679ebdbe76142bd9fb1071e5e53511d__steps_wmd_x42_ykb"/>

## Procedure

1.  In your subaccount in the SAP BTP cockpit, choose :shield: *Security* \> *Users*.

2.  Choose the name of your user.

3.  From the *Role Collections* section, choose *...* \> *Assign Role Collection*.

4.  From the drop-down list, select either *CICD Service Administrator* or *CICD Service Developer*.

5.  Confirm your choice with *Assign Role Collection*.

    > ### Note:  
    > When you assign roles or remove role assignments, it can take up to 60 minutes for changes to take effect. Log off and then log on again for changes to take effect immediately.


**Related Information**  


[Identity and Access Management](identity-and-access-management-bb2cd0a.md#loiobb2cd0a57fc54525888a6988a7ab704c "Obtain information about authorization and user roles in SAP Continuous Integration and Delivery.")

