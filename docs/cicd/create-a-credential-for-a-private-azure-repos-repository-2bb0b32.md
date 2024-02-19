<!-- loio2bb0b3288f364a4387575f66b22fa67f -->

# Create a Credential for a Private Azure Repos Repository

Create a personal access token and Basic Authentication credential for your private Azure Repos repository.



<a name="loio2bb0b3288f364a4387575f66b22fa67f__prereq_fdd_lw4_zkb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a **private** Azure Repos repository, in which the sources of your project reside.




<a name="loio2bb0b3288f364a4387575f66b22fa67f__context_ifh_vkj_ntb"/>

## Context

To let SAP Continuous Integration and Delivery clone sources from a private Azure Repos repository, the service needs to authenticate itself. For security reasons, we recommend using a personal access token instead of a password. Personal access tokens are scope-based, allow you to restrict permissions for various operations on Azure Repos, and can be revoked at any time.



<a name="loio2bb0b3288f364a4387575f66b22fa67f__steps_jfh_vkj_ntb"/>

## Procedure

1.  In Azure Repos, choose *User settings*.

2.  From the navigation pane, choose *Personal access tokens*.

3.  Choose *New token*.

4.  In the *Name* text field, enter a meaningful name for your access token.

5.  Enter your *Organization* and an optional *Expiration* for your access token.

6.  For *Scopes*, select *Custom defined*. In the *Code* section, select *Read*.

7.  Choose *Create*.

8.  Copy the generated token.

    > ### Caution:  
    > The generated token is only displayed once.

9.  In SAP Continuous Integration and Delivery, create a Basic Authentication credential. As *Username*, enter your Azure Repos username and as *Password*, enter the personal access token. See [Creating Credentials](creating-credentials-6658c81.md).


