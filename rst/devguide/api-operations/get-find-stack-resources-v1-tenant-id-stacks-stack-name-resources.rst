
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Find Stack Resources -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Find Stack Resources
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-find-stack-resources-v1-tenant-id-stacks-stack-name-resources.html#request>`__
`Response <get-find-stack-resources-v1-tenant-id-stacks-stack-name-resources.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/resources

Finds the canonical URL for the resource list of a specified stack.

The canonical URL is returned for only non-deleted stacks. To fetch the resource list for deleted stacks, use the following endpoint:

/v1/{tenant_id}/stacks/{stack_name}/{stack_id}/resources

This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|302                       |                         |                         |
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








Response
^^^^^^^^^^^^^^^^^^




