<!-- loio3a228312200c4e07b7dcf41010ae22c9 -->

# Create a Credential for a Private GitHub Repository

Create a personal access token and Basic Authentication credential for your private GitHub repository.



<a name="loio3a228312200c4e07b7dcf41010ae22c9__prereq_fdd_lw4_zkb"/>

## Prerequisites

-   You're an administrator of SAP Continuous Integration and Delivery. See [Assigning Roles and Permissions](assigning-roles-and-permissions-c679ebd.md).

-   You have a **private** GitHub repository, in which the sources of your project reside.




## Context

To let SAP Continuous Integration and Delivery clone sources from a private GitHub repository, the service needs to authenticate itself. For security reasons, we recommend using a personal access token instead of a password. Personal access tokens are scope-based, allow you to restrict permissions for various operations on GitHub, and can be revoked at any time.



## Procedure

1.  In GitHub, open your personal settings.

2.  From the navigation pane, choose *Developer settings*.

3.  From the navigation pane, choose *Personal access tokens*.

4.  Choose *Generate new token*.

5.  In the *Note* text field, enter a meaningful description for your access token.

6.  Select the *repo* scope together with its subscopes.

7.  Choose *Generate token*.

8.  Copy the generated token.

    > ### Caution:  
    > The generated token is only displayed once.

9.  In SAP Continuous Integration and Delivery, create a Basic Authentication credential. As *Username*, enter your GitHub username and as *Password*, enter the personal access token. See [Creating Credentials](creating-credentials-6658c81.md).


