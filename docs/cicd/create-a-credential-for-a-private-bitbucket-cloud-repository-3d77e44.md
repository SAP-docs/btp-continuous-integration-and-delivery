<!-- loio3d77e44ce14e48a98cebaf1ff78152b6 -->

# Create a Credential for a Private Bitbucket Cloud Repository

Create a personal access token and Basic Authentication credential for your private Bitbucket Cloud repository.



<a name="loio3d77e44ce14e48a98cebaf1ff78152b6__prereq_fdd_lw4_zkb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a **private** Bitbucket Cloud repository, in which the sources of your project reside.




<a name="loio3d77e44ce14e48a98cebaf1ff78152b6__context_ifh_vkj_ntb"/>

## Context

To let SAP Continuous Integration and Delivery clone sources from a private Bitbucket Cloud repository, the service needs to authenticate itself. For security reasons, we recommend using a personal access token instead of a password. Personal access tokens are scope-based, allow you to restrict permissions for various operations on Bitbucket Cloud, and can be revoked at any time.



<a name="loio3d77e44ce14e48a98cebaf1ff78152b6__steps_jfh_vkj_ntb"/>

## Procedure

1.  In [https://bitbucket.org/](https://bitbucket.org/), navigate to the target repository for the access token.

2.  From the navigation pane, choose *Repository settings*.

3.  From the *Security* section on the navigation pane, choose *Access tokens*.

4.  Choose *Create Repository Access Token*.

5.  Enter a meaningful name for your access token.

6.  For *Scopes*, select the *Read* permission under *Repositories*.

7.  Choose *Create*.

8.  Copy the generated token.

    > ### Caution:  
    > The generated token is only displayed once and can't be retrieved later.

9.  In SAP Continuous Integration and Delivery, create a Basic Authentication credential. As *Username*, use `x-token-auth` and as *Password*, enter the personal access token. See [Creating Credentials](creating-credentials-6658c81.md).


