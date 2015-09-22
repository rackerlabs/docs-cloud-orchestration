
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-deployment-v1-tenant-id-software-deployments:

Create deployment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v1/{tenant_id}/software_deployments

Creates a software deployment.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{tenant_id}               |String                   |The ID of the tenant. A  |
|                          |                         |tenant is also known as  |
|                          |                         |an account or project.   |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|config_id                 |String *(Required)*      |The ID of the software   |
|                          |                         |configuration resource   |
|                          |                         |that runs when applying  |
|                          |                         |to the server.           |
+--------------------------+-------------------------+-------------------------+
|server_id                 |String *(Required)*      |The ID of the compute    |
|                          |                         |server to which the      |
|                          |                         |configuration applies.   |
+--------------------------+-------------------------+-------------------------+
|action                    |String *(Required)*      |The current stack action |
|                          |                         |that triggers this       |
|                          |                         |deployment resource.     |
+--------------------------+-------------------------+-------------------------+
|stack_user_project_id     |String *(Optional)*      |Authentication project   |
|                          |                         |ID, which can also       |
|                          |                         |perform operations on    |
|                          |                         |this deployment.         |
+--------------------------+-------------------------+-------------------------+
|status                    |String *(Optional)*      |Current status of the    |
|                          |                         |deployment. Value is     |
|                          |                         |``IN_PROGRESS``,         |
|                          |                         |``COMPLETE``, or         |
|                          |                         |``FAILED``.              |
+--------------------------+-------------------------+-------------------------+
|status_reason             |String *(Optional)*      |Error description for    |
|                          |                         |the last status change,  |
|                          |                         |which is ``FAILED``      |
|                          |                         |status.                  |
+--------------------------+-------------------------+-------------------------+





**Example Create deployment: JSON request**


.. code::

   {
       "status": "IN_PROGRESS",
       "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
       "config_id": "8da95794-2ad9-4979-8ae5-739ce314c5cd",
       "stack_user_project_id": "c024bfada67845ddb17d2b0c0be8cd79",
       "action": "CREATE",
       "status_reason": "Deploy data available"
   }





Response
""""""""""""""""










**Example Create deployment: JSON response**


.. code::

   {
       "software_deployment": {
           "status": "IN_PROGRESS",
           "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
           "config_id": "8da95794-2ad9-4979-8ae5-739ce314c5cd",
           "output_values": null,
           "input_values": null,
           "action": "CREATE",
           "status_reason": "Deploy data available",
           "id": "ef422fa5-719a-419e-a10c-72e3a367b0b8",
           "creation_time": "2015-01-31T15:12:36Z",
           "updated_time": "2015-01-31T15:18:21Z"
       }
   }
   




