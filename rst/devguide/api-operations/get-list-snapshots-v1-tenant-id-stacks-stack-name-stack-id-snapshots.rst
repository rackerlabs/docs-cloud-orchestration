
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Snapshots -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

List Snapshots
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-snapshots-v1-tenant-id-stacks-stack-name-stack-id-snapshots.html#request>`__
`Response <get-list-snapshots-v1-tenant-id-stacks-stack-name-stack-id-snapshots.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/snapshots

Lists the stack snapshots.



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








Response
^^^^^^^^^^^^^^^^^^





**Example List Snapshots: JSON response**


.. code::

    {
        "snapshots": [
            {
                "id": "7c4e1ef4-bf1b-41ab-a0c8-ce01f4ffdfa1",
                "name": "vol_snapshot",
                "status": "IN_PROGRESS",
                "status_reason": null,
                "data": null
            }
        ]
    }
    

