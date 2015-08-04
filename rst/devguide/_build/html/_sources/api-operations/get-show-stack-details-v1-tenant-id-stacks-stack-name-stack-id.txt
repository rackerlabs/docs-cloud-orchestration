
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Stack Details -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Show Stack Details
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-stack-details-v1-tenant-id-stacks-stack-name-stack-id.html#request>`__
`Response <get-show-stack-details-v1-tenant-id-stacks-stack-name-stack-id.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/{stack_id}

Shows details for a specified stack.



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





**Example Show Stack Details: JSON response**


.. code::

    {
        "stack": {
            "capabilities": [],
            "creation_time": "2014-06-03T20:59:46Z",
            "description": "sample stack",
            "disable_rollback": "True",
            "id": "3095aefc-09fb-4bc7-b1f0-f21a304e864c",
            "links": [
                {
                    "href": "http://192.168.123.200:8004/v1/eb1c63a4f77141548385f113a28f0f52/stacks/simple_stack/3095aefc-09fb-4bc7-b1f0-f21a304e864c",
                    "rel": "self"
                }
            ],
            "notification_topics": [],
            "outputs": [],
            "parameters": {
                "OS::stack_id": "3095aefc-09fb-4bc7-b1f0-f21a304e864c",
                "OS::stack_name": "simple_stack"
            },
            "stack_name": "simple_stack",
            "stack_status": "CREATE_COMPLETE",
            "stack_status_reason": "Stack CREATE completed successfully",
            "template_description": "sample stack",
            "timeout_mins": "",
            "updated_time": "",
            "tags": ""
        }
    }
    

