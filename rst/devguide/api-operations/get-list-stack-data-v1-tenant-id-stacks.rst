
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Stack Data -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

List Stack Data
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-stack-data-v1-tenant-id-stacks.html#request>`__
`Response <get-list-stack-data-v1-tenant-id-stacks.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks

Lists active stacks.



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



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id                        |*(Required)*             |Filters the stack list   |
|                          |                         |by a specified stack ID. |
|                          |                         |Use this filter multiple |
|                          |                         |times to filter by       |
|                          |                         |multiple IDs.            |
+--------------------------+-------------------------+-------------------------+
|status                    |*(Required)*             |Filters the stack list   |
|                          |                         |by a specified status.   |
|                          |                         |Use this filter multiple |
|                          |                         |times to filter by       |
|                          |                         |multiple statuses.       |
+--------------------------+-------------------------+-------------------------+
|name                      |*(Required)*             |Filters the stack list   |
|                          |                         |by a specified name. Use |
|                          |                         |this filter multiple     |
|                          |                         |times to filter by       |
|                          |                         |multiple names.          |
+--------------------------+-------------------------+-------------------------+
|action                    |*(Required)*             |Filters the stack list   |
|                          |                         |by a specified action.   |
|                          |                         |Use this filter multiple |
|                          |                         |times to filter by       |
|                          |                         |multiple actions.        |
+--------------------------+-------------------------+-------------------------+
|tenant                    |*(Required)*             |Filters the stack list   |
|                          |                         |by a specified tenant.   |
|                          |                         |Use this filter multiple |
|                          |                         |times to filter by       |
|                          |                         |multiple tenants.        |
+--------------------------+-------------------------+-------------------------+
|username                  |*(Required)*             |Filters the stack list   |
|                          |                         |by a specified user      |
|                          |                         |name. Use this filter    |
|                          |                         |multiple times to filter |
|                          |                         |by multiple user names.  |
+--------------------------+-------------------------+-------------------------+
|owner_id                  |*(Required)*             |Filters the stack list   |
|                          |                         |by a specified owner ID, |
|                          |                         |which is the ID of the   |
|                          |                         |parent stack of listed   |
|                          |                         |stack. Use this filter   |
|                          |                         |multiple times to filter |
|                          |                         |by multiple owner IDs.   |
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
|show_deleted              |*(Required)*             |Specifies whether to     |
|                          |                         |include deleted stacks   |
|                          |                         |in the list. Default is  |
|                          |                         |``False``, which         |
|                          |                         |excludes deleted stacks  |
|                          |                         |from the list.           |
+--------------------------+-------------------------+-------------------------+
|show_nested               |*(Required)*             |Specifies whether to     |
|                          |                         |include nested stacks in |
|                          |                         |the list. Default is     |
|                          |                         |``False``, which         |
|                          |                         |excludes nested stacks   |
|                          |                         |from the list.           |
+--------------------------+-------------------------+-------------------------+
|sort_keys                 |*(Required)*             |Sorts the stack list by  |
|                          |                         |``name``, ``status``,    |
|                          |                         |``created_at``, or       |
|                          |                         |``updated_at`` key.      |
+--------------------------+-------------------------+-------------------------+
|tags                      |*(Required)*             |Lists stacks that        |
|                          |                         |contain one or more      |
|                          |                         |simple string tags. To   |
|                          |                         |specify multiple tags,   |
|                          |                         |separate the tags with   |
|                          |                         |commas. For example,     |
|                          |                         |``tag1,tag2``. The       |
|                          |                         |boolean AND expression   |
|                          |                         |is used to combine       |
|                          |                         |multiple tags.           |
+--------------------------+-------------------------+-------------------------+
|tags_any                  |*(Required)*             |Lists stacks that        |
|                          |                         |contain one or more      |
|                          |                         |simple string tags. To   |
|                          |                         |specify multiple tags,   |
|                          |                         |separate the tags with   |
|                          |                         |commas. For example,     |
|                          |                         |``tag1,tag2``. The       |
|                          |                         |boolean OR expression is |
|                          |                         |used to combine multiple |
|                          |                         |tags.                    |
+--------------------------+-------------------------+-------------------------+
|not_tags                  |*(Required)*             |Lists stacks that do not |
|                          |                         |contain one or more      |
|                          |                         |simple string tags. To   |
|                          |                         |specify multiple tags,   |
|                          |                         |separate the tags with   |
|                          |                         |commas. For example,     |
|                          |                         |``tag1,tag2``. The       |
|                          |                         |boolean AND expression   |
|                          |                         |is used to combine       |
|                          |                         |multiple tags.           |
+--------------------------+-------------------------+-------------------------+
|not_tags_any              |*(Required)*             |Lists stacks that do not |
|                          |                         |contain one or more      |
|                          |                         |simple string tags. To   |
|                          |                         |specify multiple tags,   |
|                          |                         |separate the tags with   |
|                          |                         |commas. For example,     |
|                          |                         |``tag1,tag2``. The       |
|                          |                         |boolean OR expression is |
|                          |                         |used to combine multiple |
|                          |                         |tags.                    |
+--------------------------+-------------------------+-------------------------+
|sort_dir                  |*(Required)*             |The sort direction of    |
|                          |                         |the list. A valid value  |
|                          |                         |is ``asc`` (ascending)   |
|                          |                         |or ``desc`` (descending).|
+--------------------------+-------------------------+-------------------------+
|global_tenant             |*(Required)*             |Specifies whether to     |
|                          |                         |include stacks from all  |
|                          |                         |tenants in the stack     |
|                          |                         |list. Policy             |
|                          |                         |requirements are         |
|                          |                         |specified in the         |
|                          |                         |Orchestration            |
|                          |                         |``policy.json`` file.    |
|                          |                         |Default is ``False``.    |
+--------------------------+-------------------------+-------------------------+
|with_count                |*(Required)*             |Specifies whether to     |
|                          |                         |include a count key in   |
|                          |                         |the response. The count  |
|                          |                         |key value is the number  |
|                          |                         |of stacks that match the |
|                          |                         |query criteria. Default  |
|                          |                         |is ``False``.            |
+--------------------------+-------------------------+-------------------------+







Response
^^^^^^^^^^^^^^^^^^





**Example List Stack Data: JSON response**


.. code::

    {
        "stacks": [
            {
                "creation_time": "2014-06-03T20:59:46Z",
                "description": "sample stack",
                "id": "3095aefc-09fb-4bc7-b1f0-f21a304e864c",
                "links": [
                    {
                        "href": "http://192.168.123.200:8004/v1/eb1c63a4f77141548385f113a28f0f52/stacks/simple_stack/3095aefc-09fb-4bc7-b1f0-f21a304e864c",
                        "rel": "self"
                    }
                ],
                "stack_name": "simple_stack",
                "stack_status": "CREATE_COMPLETE",
                "stack_status_reason": "Stack CREATE completed successfully",
                "updated_time": "",
                "tags": ""
            }
        ]
    }
    

