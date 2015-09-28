=========================
Role Based Access Control
=========================

Role Based Access Control (RBAC) restricts access to the capabilities of Rackspace Cloud services, including the Cloud Orchestration API, to authorized users only. RBAC enables Rackspace Cloud customers to specify which account users of their Cloud account have access to which Cloud Orchestration API service capabilities, based on roles defined by Rackspace (see Cloud Orchestration Product Roles and Permissions). The permissions to perform certain operations in Cloud Orchestration API – create, read, update, delete – are assigned to specific roles. The account owner user assigns these roles, either global (multiproduct) or product-specific (for example, Cloud Orchestration), to account users.

Assigning Roles to Account Users
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The account owner (identity:user-admin) can create account users on the account and then assign roles to those users. The roles grant the account users specific permissions for accessing the capabilities of the Cloud Orchestration service. Each account has only one account owner, and that role is assigned by default to any Rackspace Cloud account when the account is created.

See the Cloud Identity Client Developer Guide for information about how to perform the following tasks:

-  `Create account users <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/POST_addUser_v2.0_users_User_Calls.html>`__

-  `Assign roles to account users <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/PUT_addUserRole__v2.0_users__userId__roles_OS-KSADM__roleid__Role_Calls.html>`__

-  `Delete global role from user <http://docs.rackspace.com/auth/api/v2.0/auth-client-devguide/content/DELETE_deleteUserRole__v2.0_users__userId__roles_OS-KSADM__roleid__Role_Calls.html>`__

.. note::

    The account owner (identity:user-admin) role cannot hold any additional roles because it already has full access to all capabilities.

Roles Available for Cloud Orchestration
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Three roles (observer, creator, and admin) can be used to access the Cloud Orchestration API specifically. The following table describes these roles and their permissions.

**Cloud Orchestration Product Roles and Permissions**

heat:admin - This role provides Create, Read, Update, and Delete permissions in Cloud Orchestration, where access is granted.

heat:creator - This role provides Create, Read, and Update permissions in Cloud Orchestration, where access is granted.

heat:observer - This role provides Read permission in Cloud Orchestration, where access is granted.

Additionally, two multiproduct roles apply to all products. Users with multiproduct roles inherit access to future products when those products become RBAC-enabled. The following table describes these roles and their permissions.

**Multiproduct (Global) Roles and Permissions**

admin - This role provides Create, Read, Update, and Delete permissions in all products, where access is granted.

observer - This role provides Read permission in all products, where access is granted.

Resolving Conflicts Between Roles
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The account owner can set roles for both multiproduct and Cloud Orchestration scope, and it is important to understand how any potential conflicts among these roles are resolved. When two roles appear to conflict, the role that provides the more extensive permissions takes precedence. Therefore, admin roles take precedence over observer and creator roles, because admin roles provide more permissions.

The following scenarios show examples of how potential conflicts between user roles in the Control Panel are resolved:

Scenario 1:
Configuration : User is assigned the following roles: multiproduct **observer** and Cloud Orchestration **admin**

View: Appears that the user has only the multiproduct **observer** role.

Permissions: The user can perform product admin functions in the control panel for Cloud Orchestration only. The user has the **observer** role for the rest of the products.

Scenario 2:
Configuration: User is assigned the following roles: multiproduct **admin** and Cloud Orchestration **observer**

View: Appears that the user has only the multiproduct **admin** role.

Permissions: The user can perform product admin functions in the control panel for all of the products. The Cloud Orchestration **observer** role is ignored.

RBAC Permissions Cross-reference to Cloud Orchestration API Operations
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

API operations for Cloud Orchestration may or may not be available to all roles. To see which operations are permitted to invoke which calls, please review `the Knowledge Center article <http://www.rackspace.com/knowledge_center/article/permissions-matrix-for-next-generation-cloud-servers>`_.
