
.. _get-list-stack-by-tenant-id:

List stack data
~~~~~~~~~~~~~~~

.. code::

    GET /v1/{tenant_id}/stacks

Lists active stacks.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request could not be |
|                          |                         |understood by the server |
|                          |                         |due to malformed syntax. |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |The request requires     |
|                          |                         |user authentication.     |
+--------------------------+-------------------------+-------------------------+
|500                       |Internal Server Error    |The server encountered   |
|                          |                         |an unexpected condition  |
|                          |                         |which prevented it from  |
|                          |                         |fulfilling the request.  |
+--------------------------+-------------------------+-------------------------+


Request
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{tenant_id}               |String                   |The ID of the tenant. A  |
|                          |                         |tenant is also known as  |
|                          |                         |an account or project.   |
+--------------------------+-------------------------+-------------------------+

This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|id                        |String *(Optional)*      |Filters the stack list   |
|                          |                         |by a specified stack ID. |
|                          |                         |Use this filter multiple |
|                          |                         |times to filter by       |
|                          |                         |multiple IDs.            |
+--------------------------+-------------------------+-------------------------+
|status                    |String *(Optional)*      |Filters the stack list   |
|                          |                         |by a specified status.   |
|                          |                         |Use this filter multiple |
|                          |                         |times to filter by       |
|                          |                         |multiple statuses.       |
+--------------------------+-------------------------+-------------------------+
|name                      |String *(Optional)*      |Filters the stack list   |
|                          |                         |by a specified name. Use |
|                          |                         |this filter multiple     |
|                          |                         |times to filter by       |
|                          |                         |multiple names.          |
+--------------------------+-------------------------+-------------------------+
|action                    |String *(Optional)*      |Filters the stack list   |
|                          |                         |by a specified action.   |
|                          |                         |Use this filter multiple |
|                          |                         |times to filter by       |
|                          |                         |multiple actions.        |
+--------------------------+-------------------------+-------------------------+
|tenant                    |String *(Optional)*      |Filters the stack list   |
|                          |                         |by a specified tenant.   |
|                          |                         |Use this filter multiple |
|                          |                         |times to filter by       |
|                          |                         |multiple tenants.        |
+--------------------------+-------------------------+-------------------------+
|username                  |String *(Optional)*      |Filters the stack list   |
|                          |                         |by a specified user      |
|                          |                         |name. Use this filter    |
|                          |                         |multiple times to filter |
|                          |                         |by multiple user names.  |
+--------------------------+-------------------------+-------------------------+
|owner_id                  |String *(Optional)*      |Filters the stack list   |
|                          |                         |by a specified owner ID, |
|                          |                         |which is the ID of the   |
|                          |                         |parent stack of listed   |
|                          |                         |stack. Use this filter   |
|                          |                         |multiple times to filter |
|                          |                         |by multiple owner IDs.   |
+--------------------------+-------------------------+-------------------------+
|limit                     |Int *(Optional)*         |Requests a specified     |
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
|marker                    |String *(Optional)*      |Specifies the ID of the  |
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
|show_deleted              |String *(Optional)*      |Specifies whether to     |
|                          |                         |include deleted stacks   |
|                          |                         |in the list. Default is  |
|                          |                         |``False``, which         |
|                          |                         |excludes deleted stacks  |
|                          |                         |from the list.           |
+--------------------------+-------------------------+-------------------------+
|show_nested               |String *(Optional)*      |Specifies whether to     |
|                          |                         |include nested stacks in |
|                          |                         |the list. Default is     |
|                          |                         |``False``, which         |
|                          |                         |excludes nested stacks   |
|                          |                         |from the list.           |
+--------------------------+-------------------------+-------------------------+
|sort_keys                 |String *(Optional)*      |Sorts the stack list by  |
|                          |                         |``name``, ``status``,    |
|                          |                         |``created_at``, or       |
|                          |                         |``updated_at`` key.      |
+--------------------------+-------------------------+-------------------------+
|tags                      |String *(Optional)*      |Lists stacks that        |
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
|tags_any                  |String *(Optional)*      |Lists stacks that        |
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
|not_tags                  |String *(Optional)*      |Lists stacks that do not |
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
|not_tags_any              |String *(Optional)*      |Lists stacks that do not |
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
|sort_dir                  |String *(Optional)*      |The sort direction of    |
|                          |                         |the list. A valid value  |
|                          |                         |is ``asc`` (ascending)   |
|                          |                         |or ``desc`` (descending).|
+--------------------------+-------------------------+-------------------------+
|global_tenant             |String *(Optional)*      |Specifies whether to     |
|                          |                         |include stacks from all  |
|                          |                         |tenants in the stack     |
|                          |                         |list. Policy             |
|                          |                         |requirements are         |
|                          |                         |specified in the         |
|                          |                         |Orchestration            |
|                          |                         |``policy.json`` file.    |
|                          |                         |Default is ``False``.    |
+--------------------------+-------------------------+-------------------------+
|with_count                |String *(Optional)*      |Specifies whether to     |
|                          |                         |include a count key in   |
|                          |                         |the response. The count  |
|                          |                         |key value is the number  |
|                          |                         |of stacks that match the |
|                          |                         |query criteria. Default  |
|                          |                         |is ``False``.            |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

Response
--------

**Example List stack data: JSON response**


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
