
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Deployment Details -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Show Deployment Details
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-deployment-details-v1-tenant-id-software-deployments-deployment-id.html#request>`__
`Response <get-show-deployment-details-v1-tenant-id-software-deployments-deployment-id.html#response>`__

.. code::

    GET /v1/{tenant_id}/software_deployments/{deployment_id}

Shows details for a specified software deployment.



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
|{deployment_id}           |*(Required)*             |The deployment ID.       |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Show Deployment Details: JSON response**


.. code::

    {
        "software_deployment": {
            "status": "IN_PROGRESS",
            "server_id": "ec14c864-096e-4e27-bb8a-2c2b4dc6f3f5",
            "config_id": "3d5ec2a8-7004-43b6-a7f6-542bdbe9d434",
            "output_values": null,
            "input_values": null,
            "action": "CREATE",
            "status_reason": "Deploy data available",
            "id": "06e87bcc-33a2-4bce-aebd-533e698282d3"
        }
    }

