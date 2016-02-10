
.. _put-update-deployment-v1-tenant-id-software-deployments-deployment-id:

Update deployment
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v1/{tenant_id}/software_deployments/{deployment_id}

Updates a specified software deployment.



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
|{deployment_id}           |String *(Required)*      |The deployment ID.       |
+--------------------------+-------------------------+-------------------------+





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|config_id                 |String *(Required)*      |ID of the software       |
|                          |                         |configuration resource   |
|                          |                         |to run when applying to  |
|                          |                         |the server. This ID      |
|                          |                         |might not be the same    |
|                          |                         |configuration ID with    |
|                          |                         |which the deployment was |
|                          |                         |created because          |
|                          |                         |ephemeral configurations |
|                          |                         |are created throughout   |
|                          |                         |the life cycle of the    |
|                          |                         |deployment.              |
+--------------------------+-------------------------+-------------------------+
|action                    |String *(Required)*      |Current stack action in  |
|                          |                         |which this deployment    |
|                          |                         |resource is being        |
|                          |                         |triggered.               |
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
|output_values             |String *(Optional)*      |Map of output values for |
|                          |                         |the deployment, as       |
|                          |                         |signalled from the       |
|                          |                         |server.                  |
+--------------------------+-------------------------+-------------------------+





**Example Update deployment: JSON request**


.. code::

   {
       "status": "COMPLETE",
       "output_values": {
           "deploy_stdout": "Writing to /tmp/baaaaa\nWritten to /tmp/baaaaa\n",
           "deploy_stderr": "+ echo Writing to /tmp/baaaaa\n+ echo fooooo\n+ cat /tmp/baaaaa\n+ echo -n The file /tmp/baaaaa contains fooooo for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE\n+ echo Written to /tmp/baaaaa\n+ echo Output to stderr\nOutput to stderr\n",
           "deploy_status_code": 0,
           "result": "The file /tmp/baaaaa contains fooooo for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE"
       },
       "status_reason": "Outputs received"
   }





Response
""""""""""""""""










**Example Update deployment: JSON response**


.. code::

   {
       "software_deployment": {
           "status": "COMPLETE",
           "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
           "config_id": "3d5ec2a8-7004-43b6-a7f6-542bdbe9d434",
           "output_values": {
               "deploy_stdout": "Writing to /tmp/baaaaa\nWritten to /tmp/baaaaa\n",
               "deploy_stderr": "+ echo Writing to /tmp/baaaaa\n+ echo fooooo\n+ cat /tmp/baaaaa\n+ echo -n The file /tmp/baaaaa contains fooooo for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE\n+ echo Written to /tmp/baaaaa\n+ echo Output to stderr\nOutput to stderr\n",
               "deploy_status_code": 0,
               "result": "The file /tmp/baaaaa contains fooooo for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE"
           },
           "input_values": null,
           "action": "CREATE",
           "status_reason": "Outputs received",
           "id": "06e87bcc-33a2-4bce-aebd-533e698282d3",
           "creation_time": "2015-01-31T15:12:36Z",
           "updated_time": "2015-01-31T15:18:21Z"
       }
   }
   




