
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Get Stack Template -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Get Stack Template
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-get-stack-template-v1-tenant-id-stacks-stack-name-stack-id-template.html#request>`__
`Response <get-get-stack-template-v1-tenant-id-stacks-stack-name-stack-id-template.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/template

Gets a template for a specified stack.



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





**Example Get Stack Template: JSON response**


.. code::

    {
        "description": "Hello world HOT template that just defines a single server. Contains just base features to verify base HOT support.\n",
        "heat_template_version": "2013-05-23",
        "outputs": {
            "foo": {
                "description": "Show foo parameter value",
                "value": {
                    "get_param": "foo"
                }
            }
        },
        "parameters": {
            "foo": {
                "default": "secret",
                "description": "Name of an existing key pair to use for the server",
                "hidden": true,
                "type": "string"
            }
        },
        "resources": {
            "random_key_name": {
                "properties": {
                    "length": 8
                },
                "type": "OS::Heat::RandomString"
            }
        }
    }
    

