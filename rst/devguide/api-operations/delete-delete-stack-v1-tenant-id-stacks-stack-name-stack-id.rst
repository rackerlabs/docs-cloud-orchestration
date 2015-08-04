
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Delete Stack -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Delete Stack
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <delete-delete-stack-v1-tenant-id-stacks-stack-name-stack-id.html#request>`__
`Response <delete-delete-stack-v1-tenant-id-stacks-stack-name-stack-id.html#response>`__

.. code::

    DELETE /v1/{tenant_id}/stacks/{stack_name}/{stack_id}

Deletes a specified stack and any snapshots of that stack.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{tenant_id}               |                         |The ID of the tenant. A  |
|                          |                         |tenant is also known as  |
|                          |                         |an account or project.   |
+--------------------------+-------------------------+-------------------------+
|{stack_name}              |string *(Required)*      |The name of a stack.     |
+--------------------------+-------------------------+-------------------------+
|{stack_id}                |*(Required)*             |The stack ID.            |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




