
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Resource Events -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

List Resource Events
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-resource-events-v1-tenant-id-stacks-stack-name-stack-id-resources-resource-name-events.html#request>`__
`Response <get-list-resource-events-v1-tenant-id-stacks-stack-name-stack-id-resources-resource-name-events.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name}/events

Lists events for a specified stack resource.



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



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|resource_action           |*(Required)*             |Filters the event list   |
|                          |                         |by a specified resource  |
|                          |                         |action. You can use this |
|                          |                         |filter multiple times to |
|                          |                         |filter by multiple       |
|                          |                         |resource actions. Valid  |
|                          |                         |resource actions are     |
|                          |                         |``CREATE``, ``DELETE``,  |
|                          |                         |``UPDATE``,              |
|                          |                         |``ROLLBACK``,            |
|                          |                         |``SUSPEND``, ``RESUME``, |
|                          |                         |and ``ADOPT``.           |
+--------------------------+-------------------------+-------------------------+
|resource_status           |*(Required)*             |Filters the event list   |
|                          |                         |by a specified resource  |
|                          |                         |status. You can use this |
|                          |                         |filter multiple times to |
|                          |                         |filter by multiple       |
|                          |                         |resource statuses. Valid |
|                          |                         |resource statuses are    |
|                          |                         |``IN_PROGRESS``,         |
|                          |                         |``COMPLETE``, and        |
|                          |                         |``FAILED``.              |
+--------------------------+-------------------------+-------------------------+
|resource_name             |*(Required)*             |Filters the event list   |
|                          |                         |by a specified resource  |
|                          |                         |name. You can use this   |
|                          |                         |filter multiple times to |
|                          |                         |filter by multiple       |
|                          |                         |resource names.          |
+--------------------------+-------------------------+-------------------------+
|resource_type             |*(Required)*             |Filters the event list   |
|                          |                         |by a specified resource  |
|                          |                         |type. You can use this   |
|                          |                         |filter multiple times to |
|                          |                         |filter by multiple       |
|                          |                         |resource types. Valid    |
|                          |                         |resource types include   |
|                          |                         |``OS::Nova::Server``,    |
|                          |                         |``OS::Cinder::Volume``,  |
|                          |                         |``OS::Neutron::Port``,   |
|                          |                         |and so on.               |
+--------------------------+-------------------------+-------------------------+
|limit                     |xsd:int *(Required)*     |Requests a specified     |
|                          |                         |page size of returned    |
|                          |                         |items from the query.    |
|                          |                         |Returns a number of      |
|                          |                         |items up to the          |
|                          |                         |specified limit value.   |
|                          |                         |Use the ``limit``        |
|                          |                         |parameter to make an     |
|                          |                         |initial limited request  |
|                          |                         |and use the ID of the    |
|                          |                         |last-seen item from the  |
|                          |                         |response as the          |
|                          |                         |``marker`` parameter     |
|                          |                         |value in a subsequent    |
|                          |                         |limited request.         |
+--------------------------+-------------------------+-------------------------+
|marker                    |xsd:string *(Required)*  |Specifies the ID of the  |
|                          |                         |last-seen item. Use the  |
|                          |                         |``limit`` parameter to   |
|                          |                         |make an initial limited  |
|                          |                         |request and use the ID   |
|                          |                         |of the last-seen item    |
|                          |                         |from the response as the |
|                          |                         |``marker`` parameter     |
|                          |                         |value in a subsequent    |
|                          |                         |limited request.         |
+--------------------------+-------------------------+-------------------------+
|sort_keys                 |*(Required)*             |Sorts the list by the    |
|                          |                         |``resource_type`` or     |
|                          |                         |``created_at`` key.      |
+--------------------------+-------------------------+-------------------------+
|sort_dir                  |*(Required)*             |The sort direction of    |
|                          |                         |the list. A valid value  |
|                          |                         |is ``asc`` (ascending)   |
|                          |                         |or ``desc`` (descending).|
+--------------------------+-------------------------+-------------------------+







Response
^^^^^^^^^^^^^^^^^^





**Example List Resource Events: JSON response**


.. code::

    {
        "events": [
            {
                "resource_name": "port",
                "event_time": "2014-07-23T08:14:47Z",
                "links": [{
                    "href": "http://192.168.123.200:8004/v1/dc4b074874244f7693dd65583733a758/stacks/aws_port/db467ed1-50b5-4a3e-aeb1-396ff1d151c5/resources/port/events/474bfdf0-a450-46ec-a78a-0c7faa404073",
                    "rel": "self"
                },
                {
                    "href": "http://192.168.123.200:8004/v1/dc4b074874244f7693dd65583733a758/stacks/aws_port/db467ed1-50b5-4a3e-aeb1-396ff1d151c5/resources/port",
                    "rel": "resource"
                },
                {
                    "href": "http://192.168.123.200:8004/v1/dc4b074874244f7693dd65583733a758/stacks/aws_port/db467ed1-50b5-4a3e-aeb1-396ff1d151c5",
                    "rel": "stack"
                }],
                "logical_resource_id": "port",
                "resource_status": "CREATE_FAILED",
                "resource_status_reason": "NotFound: Subnet f8a699d0-3537-429e-87a5-6b5a8d0c2bf0 could not be found",
                "physical_resource_id": null,
                "id": "474bfdf0-a450-46ec-a78a-0c7faa404073"
            },
            {
                "resource_name": "port",
                "event_time": "2014-07-23T08:14:47Z",
                "links": [{
                    "href": "http://192.168.123.200:8004/v1/dc4b074874244f7693dd65583733a758/stacks/aws_port/db467ed1-50b5-4a3e-aeb1-396ff1d151c5/resources/port/events/66fa95b6-e6f8-4f05-b1af-e828f5aba04c",
                    "rel": "self"
                },
                {
                    "href": "http://192.168.123.200:8004/v1/dc4b074874244f7693dd65583733a758/stacks/aws_port/db467ed1-50b5-4a3e-aeb1-396ff1d151c5/resources/port",
                    "rel": "resource"
                },
                {
                    "href": "http://192.168.123.200:8004/v1/dc4b074874244f7693dd65583733a758/stacks/aws_port/db467ed1-50b5-4a3e-aeb1-396ff1d151c5",
                    "rel": "stack"
                }],
                "logical_resource_id": "port",
                "resource_status": "CREATE_IN_PROGRESS",
                "resource_status_reason": "state changed",
                "physical_resource_id": null,
                "id": "66fa95b6-e6f8-4f05-b1af-e828f5aba04c"
            }
        ]
    }

