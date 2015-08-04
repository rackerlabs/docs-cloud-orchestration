
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Restore Snapshot -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Restore Snapshot
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-restore-snapshot-v1-tenant-id-stacks-stack-name-stack-id-snapshots-snapshot-id-restore.html#request>`__
`Response <post-restore-snapshot-v1-tenant-id-stacks-stack-name-stack-id-snapshots-snapshot-id-restore.html#response>`__

.. code::

    POST /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/snapshots/{snapshot_id}/restore

Restores a stack snapshot. You can restore only active stacks from a snapshot. Deleted stacks must be recreated.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |                         |                         |
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
|{snapshot_id}             |*(Required)*             |The snapshot ID.         |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




