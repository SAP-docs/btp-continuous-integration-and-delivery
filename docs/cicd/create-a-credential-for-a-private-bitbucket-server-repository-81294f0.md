<!-- loio81294f00b4b544d0a6a6ccf5c5519ae8 -->

# Create a Credential for a Private Bitbucket Server Repository

Create a personal access token and Basic Authentication Credential for your private Bitbucket Server repository.



<a name="loio81294f00b4b544d0a6a6ccf5c5519ae8__prereq_u3x_yzw_s4b"/>

## Prerequisites

-   You’re an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a **private** Bitbucket Server repository, in which the sources of your project reside.




<a name="loio81294f00b4b544d0a6a6ccf5c5519ae8__context_dst_b1x_s4b"/>

## Context

To let SAP Continuous Integration and Delivery clone sources from a private Bitbucket Server repository, the service needs to authenticate itself. For security reasons, we recommend using a personal access token instead of a password. Personal access tokens are scope-based, allow you to restrict permissions for various operations on Bitbucket Server, and can be revoked at any time.



<a name="loio81294f00b4b544d0a6a6ccf5c5519ae8__steps_hwr_c1x_s4b"/>

## Procedure

1.  In Bitbucket Server, choose your profile picture ** \> ***Manage account* \> ***Personal access tokens*.

2.  Choose *Create a token*.

3.  In the *Token details*, enter a name for your token.

4.  In the *Permissions* section, select *Read* for both *Projects* and *Repositories*.

5.  Set *Automatic expiry* to *No* and choose *Create*.

6.  Copy your personal access token.

    > ### Caution:  
    > The personal access token is only displayed once.

7.  In SAP Continuous Integration and Delivery, create a Basic Authentication credential. As *Username*, enter your Bitbucket Server username and as *Password*, enter the personal access token. See [Creating Credentials](creating-credentials-6658c81.md).


