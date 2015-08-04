
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Snapshot Stack -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Snapshot Stack
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-snapshot-stack-v1-tenant-id-stacks-stack-name-stack-id-snapshots.html#request>`__
`Response <post-snapshot-stack-v1-tenant-id-stacks-stack-name-stack-id-snapshots.html#response>`__

.. code::

    POST /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/snapshots

Takes a snapshot of all the resources in the stack. All snapshots are deleted upon deletion of the stack.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
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
|name                      |*(Required)*             |The name of the snapshot.|
+--------------------------+-------------------------+-------------------------+





**Example Snapshot Stack: JSON request**


.. code::

    {
        "name": "vol_snapshot"
    }
    


Response
^^^^^^^^^^^^^^^^^^





**Example Snapshot Stack: JSON response**


.. code::

    {
        "id": "13c3a4b5-0585-440e-85a4-6f96b20e7a78",
        "name": "vol_snapshot",
        "status": "IN_PROGRESS",
        "status_reason": null,
        "data": null
    }
    

