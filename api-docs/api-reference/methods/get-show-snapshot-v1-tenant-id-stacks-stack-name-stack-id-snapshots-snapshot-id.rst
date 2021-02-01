
.. _get-show-snapshot-id:

Show snapshot
~~~~~~~~~~~~~

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/snapshots/{snapshot_id}

Shows details for a specified snapshot.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+

Request
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{tenant_id}               |String                   |The ID of the tenant. A  |
|                          |                         |tenant is also known as  |
|                          |                         |an account or project.   |
+--------------------------+-------------------------+-------------------------+
|stack_name                |String *(Required)*      |The name of a stack.     |
+--------------------------+-------------------------+-------------------------+
|{stack_id}                |String *(Required)*      |The stack ID.            |
+--------------------------+-------------------------+-------------------------+
|{snapshot_id}             |String *(Required)*      |The snapshot ID.         |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

Response
--------

**Example Show snapshot: JSON response**


.. code::

   {
       "snapshot": {
           "id": "7c4e1ef4-bf1b-41ab-a0c8-ce01f4ffdfa1",
           "name": "vol_snapshot",
           "status": "COMPLETE",
           "status_reason": "Stack SNAPSHOT completed successfully",
           "data": {
               "status": "COMPLETE",
               "name": "stack_vol1",
               "stack_user_project_id": "fffa11067b1c48129ddfb78fba2bf09f",
               "environment": {
                   "parameters": {},
                   "resource_registry": {
                       "resources": {}
                   }
               },
               "template": {
                   "heat_template_version": "2013-05-23",
                   "resources": {
                       "volume": {
                           "type": "OS::Cinder::Volume",
                           "properties": {
                               "size": 1
                           }
                       }
                   }
               },
               "action": "SNAPSHOT",
               "project_id": "ecdb08032cd042179692a1b148f6565e",
               "id": "656452c2-e151-40da-8704-c844e69b485c",
               "resources": {
                   "volume": {
                       "status": "COMPLETE",
                       "name": "volume",
                       "resource_data": {
                           "backup_id": "99108cf8-398f-461b-a043-bdceb7c9f572"
                       },
                       "resource_id": "3ab8cf79-807b-4c40-b743-0655f91e072f",
                       "action": "SNAPSHOT",
                       "type": "OS::Cinder::Volume",
                       "metadata": {}
                   }
               }
           }
       }
   }
