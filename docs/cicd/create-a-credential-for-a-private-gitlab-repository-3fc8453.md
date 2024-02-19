<!-- loio3fc84539f8824506b78ac4da8fe3bc56 -->

# Create a Credential for a Private GitLab Repository

Create a personal access token and Basic Authentication credential for your private GitLab repository.



<a name="loio3fc84539f8824506b78ac4da8fe3bc56__prereq_tbz_gdt_wpb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a **private** GitLab repository, in which the sources of your project reside.




<a name="loio3fc84539f8824506b78ac4da8fe3bc56__context_vbz_gdt_wpb"/>

## Context

To let SAP Continuous Integration and Delivery clone sources from a private GitLab repository, the service needs to authenticate itself. For security reasons, we recommend using a personal access token instead of a password. Personal access tokens are scope-based, allow you to restrict permissions for various operations on GitLab, and can be revoked at any time.



<a name="loio3fc84539f8824506b78ac4da8fe3bc56__steps_wbz_gdt_wpb"/>

## Procedure

1.  In the top-right corner in GitLab, select your avatar.

2.  Choose *Edit profile*.

3.  From the navigation pane, choose *Access Tokens*.

4.  Enter a name and optional expiry date for your access token.

5.  Select the *read\_repository* scope.

6.  Choose *Create personal access token*.

7.  Copy the generated token.

    > ### Caution:  
    > The generated token is only displayed once.

8.  In SAP Continuous Integration and Delivery, create a Basic Authentication credential. As *Username*, enter your GitLab username and as *Password*, enter the personal access token. See [Creating Credentials](creating-credentials-6658c81.md).


