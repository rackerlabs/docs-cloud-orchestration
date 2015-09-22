
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-show-orchestration-engine-status-v1-tenant-id-services:

Show orchestration engine status
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1/{tenant_id}/services

Enables administrative users to view details for all orchestration engines.

Orchestration engine details include ``engine_id``, topic name, last updated time, health status, and host name.

Troubleshooting



*  A ``503`` error code indicates that the heat engines are down. Run the ``heat-manage service list`` command or contact your cloud provider to find out why the heat engines are down.




This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|403                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|503                       |                         |                         |
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





This operation does not accept a request body.




Response
""""""""""""""""










**Example Show orchestration engine status: JSON response**


.. code::

   {
       "services": [
           {
               "status": "up",
               "binary": "heat-engine",
               "report_interval": 60,
               "engine_id": "9d9242c3-4b9e-45e1-9e74-7615fbf20e5d",
               "created_at": "2015-02-03T05:55:59.000000",
               "hostname": "mrkanag",
               "updated_at": "2015-02-03T05:57:59.000000",
               "topic": "engine",
               "host": "engine-1",
               "deleted_at": null,
               "id": "e1908f44-42f9-483f-b778-bc814072c33d"
           },
           {
               "status": "down",
               "binary": "heat-engine",
               "report_interval": 60,
               "engine_id": "2d2434bf-adb6-4453-9c6b-b22fb8bd2306",
               "created_at": "2015-02-03T06:03:14.000000",
               "hostname": "mrkanag",
               "updated_at": "2015-02-03T06:09:55.000000",
               "topic": "engine",
               "host": "engine",
               "deleted_at": null,
               "id": "582b5657-6db7-48ad-8483-0096350faa21"
           }
       ]
   }
   





**Example Show orchestration engine status: JSON response**


All Orchestration engines are down.




**Example Show orchestration engine status: JSON response**


You are not authorized to complete this action.



