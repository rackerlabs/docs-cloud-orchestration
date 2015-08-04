
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Check Stack Resources -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Check Stack Resources
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-check-stack-resources-v1-tenant-id-stacks-stack-name-stack-id-actions.html#request>`__
`Response <post-check-stack-resources-v1-tenant-id-stacks-stack-name-stack-id-actions.html#response>`__

.. code::

    POST /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/actions

Checks whether the resources are in expected states for the specified stack.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |                         |                         |
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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|check                     |*(Required)*             |Specify the ``check``    |
|                          |                         |action in the request    |
|                          |                         |body.                    |
+--------------------------+-------------------------+-------------------------+





**Example Check Stack Resources: JSON request**


.. code::

    {
        "check": null
    }
    


Response
^^^^^^^^^^^^^^^^^^




