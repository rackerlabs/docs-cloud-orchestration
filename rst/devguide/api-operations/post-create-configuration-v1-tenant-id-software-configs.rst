
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Create Configuration -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Create Configuration
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-create-configuration-v1-tenant-id-software-configs.html#request>`__
`Response <post-create-configuration-v1-tenant-id-software-configs.html#response>`__

.. code::

    POST /v1/{tenant_id}/software_configs

Creates a software configuration.



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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|config                    |*(Required)*             |Configuration script or  |
|                          |                         |manifest that defines    |
|                          |                         |which configuration is   |
|                          |                         |performed.               |
+--------------------------+-------------------------+-------------------------+
|group                     |*(Required)*             |Namespace that groups    |
|                          |                         |this software            |
|                          |                         |configuration by when it |
|                          |                         |is delivered to a        |
|                          |                         |server. This setting     |
|                          |                         |might simply define      |
|                          |                         |which configuration tool |
|                          |                         |performs the             |
|                          |                         |configuration.           |
+--------------------------+-------------------------+-------------------------+
|name                      |*(Required)*             |The name of the          |
|                          |                         |configuration to create. |
+--------------------------+-------------------------+-------------------------+
|inputs                    |*(Required)*             |Schema that represents   |
|                          |                         |the inputs that this     |
|                          |                         |software configuration   |
|                          |                         |expects.                 |
+--------------------------+-------------------------+-------------------------+
|outputs                   |*(Required)*             |Schema that represents   |
|                          |                         |the outputs that this    |
|                          |                         |software configuration   |
|                          |                         |produces.                |
+--------------------------+-------------------------+-------------------------+
|options                   |*(Required)*             |Map that contains        |
|                          |                         |options that are         |
|                          |                         |specific to the          |
|                          |                         |configuration management |
|                          |                         |tool that this resource  |
|                          |                         |uses.                    |
+--------------------------+-------------------------+-------------------------+





**Example Create Configuration: JSON request**


.. code::

    {
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
        "config": "#!/bin/sh -x\necho \"Writing to /tmp/$bar\"\necho $foo > /tmp/$bar\necho -n \"The file /tmp/$bar contains `cat /tmp/$bar` for server $deploy_server_id during $deploy_action\" > $heat_outputs_path.result\necho \"Written to /tmp/$bar\"\necho \"Output to stderr\" 1>&2",
        "options": null
    }


Response
^^^^^^^^^^^^^^^^^^





**Example Create Configuration: JSON response**


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

