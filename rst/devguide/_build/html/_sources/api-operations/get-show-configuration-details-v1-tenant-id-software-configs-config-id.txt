
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Configuration Details -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Show Configuration Details
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-configuration-details-v1-tenant-id-software-configs-config-id.html#request>`__
`Response <get-show-configuration-details-v1-tenant-id-software-configs-config-id.html#response>`__

.. code::

    GET /v1/{tenant_id}/software_configs/{config_id}

Shows details for a software configuration.



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
|{config_id}               |*(Required)*             |The configuration ID.    |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Show Configuration Details: JSON response**


.. code::

    {
        "software_config": {
            "inputs": [
                {
                    "default": null,
                    "type": "String",
                    "name": "foo",
                    "description": null
                },
                {
                    "default": null,
                    "type": "String",
                    "name": "bar",
                    "description": null
                }
            ],
            "group": "script",
            "name": "a-config-we5zpvyu7b5o",
            "outputs": [
                {
                    "type": "String",
                    "name": "result",
                    "error_output": false,
                    "description": null
                }
            ],
            "options": null,
            "config": "#!/bin/sh -x\necho \"Writing to /tmp/$bar\"\necho $foo > /tmp/$bar\necho -n \"The file /tmp/$bar contains `cat /tmp/$bar` for server $deploy_server_id during $deploy_action\" > $heat_outputs_path.result\necho \"Written to /tmp/$bar\"\necho \"Output to stderr\" 1>&2",
            "id": "ddee7aca-aa32-4335-8265-d436b20db4f1"
        }
    }

