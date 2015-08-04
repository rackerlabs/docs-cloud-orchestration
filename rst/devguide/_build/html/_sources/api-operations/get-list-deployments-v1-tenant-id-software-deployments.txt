
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Deployments -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

List Deployments
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-deployments-v1-tenant-id-software-deployments.html#request>`__
`Response <get-list-deployments-v1-tenant-id-software-deployments.html#response>`__

.. code::

    GET /v1/{tenant_id}/software_deployments

Lists all available software deployments.



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








Response
^^^^^^^^^^^^^^^^^^





**Example List Deployments: JSON response**


.. code::

    {
        "software_deployments": [
            {
                "status": "COMPLETE",
                "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
                "config_id": "8da95794-2ad9-4979-8ae5-739ce314c5cd",
                "output_values": {
                    "deploy_stdout": "Writing to /tmp/barmy\nWritten to /tmp/barmy\n",
                    "deploy_stderr": "+ echo Writing to /tmp/barmy\n+ echo fu\n+ cat /tmp/barmy\n+ echo -n The file /tmp/barmy contains fu for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE\n+ echo Written to /tmp/barmy\n+ echo Output to stderr\nOutput to stderr\n",
                    "deploy_status_code": 0,
                    "result": "The file /tmp/barmy contains fu for server ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5 during CREATE"
                },
                "input_values": null,
                "action": "CREATE",
                "status_reason": "Outputs received",
                "id": "ef422fa5-719a-419e-a10c-72e3a367b0b8"
            }
        ]
    }

