
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Resource Data -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Show Resource Data
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-resource-data-v1-tenant-id-stacks-stack-name-stack-id-resources-resource-name.html#request>`__
`Response <get-show-resource-data-v1-tenant-id-stacks-stack-name-stack-id-resources-resource-name.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name}

Shows data for a specified resource.



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
|{resource_name}           |*(Required)*             |The name of a resource   |
|                          |                         |in the stack.            |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Show Resource Data: JSON response**


.. code::

    {
        "resource": {
            "attributes": {
                "value": "I9S20uIp"
            },
            "creation_time": "2015-06-25T14:59:53",
            "description": "",
            "links": [
                {
                    "href": "http://hostname/v1/1234/stacks/mystack/629a32d0-ac4f-4f63-b58d-f0d047b1ba4c/resources/random_key_name",
                    "rel": "self"
                },
                {
                    "href": "http://hostname/v1/1234/stacks/mystack/629a32d0-ac4f-4f63-b58d-f0d047b1ba4c",
                    "rel": "stack"
                }
            ],
            "logical_resource_id": "random_key_name",
            "physical_resource_id": "mystack-random_key_name-pmjmy5pks735",
            "required_by": [],
            "resource_name": "random_key_name",
            "resource_status": "CREATE_COMPLETE",
            "resource_status_reason": "state changed",
            "resource_type": "OS::Heat::RandomString",
            "updated_time": "2015-06-25T14:59:53"
        }
    }
    

