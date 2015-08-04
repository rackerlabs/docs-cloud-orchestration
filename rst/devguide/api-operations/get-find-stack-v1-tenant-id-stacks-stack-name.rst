
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Find Stack -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Find Stack
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-find-stack-v1-tenant-id-stacks-stack-name.html#request>`__
`Response <get-find-stack-v1-tenant-id-stacks-stack-name.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}

Finds the canonical URL for a specified stack.

Also works with verbs other than ``GET``, so you can perform ``PUT`` and ``DELETE`` operations on a current stack. Set your client to follow redirects. Note that when redirecting, the request method should not change, as defined in RFC2626. However, in many clients the default behavior is to change the method to ``GET`` when you receive a 302 because this behavior is ubiquitous in web browsers.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|302                       |                         |                         |
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








Response
^^^^^^^^^^^^^^^^^^





**Example Find Stack: JSON response**


.. code::

    {
        "stack": {
            "capabilities": [],
            "creation_time": "2014-06-04T20:36:12Z",
            "description": "sample stack",
            "disable_rollback": true,
            "id": "5333af0c-cc26-47ee-ac3d-8784cefafbd7",
            "links": [
                {
                    "href": "http://192.168.123.200:8004/v1/eb1c63a4f77141548385f113a28f0f52/stacks/simple_stack/5333af0c-cc26-47ee-ac3d-8784cefafbd7",
                    "rel": "self"
                }
            ],
            "notification_topics": [],
            "outputs": [],
            "parameters": {
                "OS::stack_id": "5333af0c-cc26-47ee-ac3d-8784cefafbd7",
                "OS::stack_name": "simple_stack"
            },
            "stack_name": "simple_stack",
            "stack_status": "CREATE_COMPLETE",
            "stack_status_reason": "Stack CREATE completed successfully",
            "template_description": "sample stack",
            "timeout_mins": null,
            "updated_time": null
        }
    }

