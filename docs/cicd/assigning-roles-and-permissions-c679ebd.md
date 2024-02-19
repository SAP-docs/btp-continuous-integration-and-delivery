<!-- loioc679ebdbe76142bd9fb1071e5e53511d -->

<link rel="stylesheet" type="text/css" href="css/sap-icons.css"/>

# Assigning Roles and Permissions

Administer the role assignment for SAP Continuous Integration and Delivery.



<a name="loioc679ebdbe76142bd9fb1071e5e53511d__prereq_e2j_gvp_tdb"/>

## Prerequisites

-   You’re an administrator of your global account and subaccount on SAP BTP.

-   **If you use an enterprise account \(no trial account\):** You’re a User & Role Administrator of your subaccount on SAP BTP and can therefore view the :shield: *Security* section in its navigation pane. See [Managing Subaccounts Using the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/55d0b6d8b96846b8ae93b85194df0944.html).

-   You have enabled SAP Continuous Integration and Delivery. See [Enabling the Service](enabling-the-service-c8ed09d.md).




<a name="loioc679ebdbe76142bd9fb1071e5e53511d__context_z3t_m3q_tdb"/>

## Context

For SAP Continuous Integration and Delivery, there are two different roles: **Administrator** and **Developer**. The following table provides an overview of their permissions:

**Roles and Permissions for SAP Continuous Integration and Delivery**


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

For more information about roles and permissions in the Cloud Foundry environment, see [Account Administration in the Cockpit](https://help.sap.com/viewer/65de2977205c403bbc107264b8eccf4b/Cloud/en-US/8061ecc529d74465b2b9566a634943ec.html).



<a name="loioc679ebdbe76142bd9fb1071e5e53511d__steps_wmd_x42_ykb"/>

## Procedure

1.  In your subaccount in the SAP BTP cockpit, choose :shield: *Security* \> *Trust Configuration*.

2.  Choose the name of your identity provider.

3.  Enter the e-mail address of the user to which you want to assign a role collection.

4.  Choose *Show Assignments*.

5.  If the user is new to the subaccount, choose *Add User* in the *Confirmation* dialog.

6.  Choose *Assign Role Collection*.

7.  From the dropdown list, select the role you want to assign and confirm your choice with *Assign Role Collection*.

    > ### Note:  
    > When you assign roles or remove role assignments, it can take up to 60 minutes for changes to take effect. Log off and then log on again for changes to take effect immediately.


