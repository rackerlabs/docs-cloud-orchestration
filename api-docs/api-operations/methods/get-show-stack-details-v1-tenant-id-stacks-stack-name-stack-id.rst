
.. _get-show-stack-details-v1-tenant-id-stacks-stack-name-stack-id:

Show stack details
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/{stack_id}

Shows details for a specified stack.



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
|404                       |Not Found                |The server has not found |
|                          |                         |anything matching the    |
|                          |                         |Request-URI.             |
+--------------------------+-------------------------+-------------------------+
|500                       |Internal Server Error    |The server encountered   |
|                          |                         |an unexpected condition  |
|                          |                         |which prevented it from  |
|                          |                         |fulfilling the request.  |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{tenant_id}               |String                   |The ID of the tenant. A  |
|                          |                         |tenant is also known as  |
|                          |                         |an account or project.   |
+--------------------------+-------------------------+-------------------------+
|stack_name                |String *(Required)*      |The name of a stack.     |
+--------------------------+-------------------------+-------------------------+
|{stack_id}                |String *(Required)*      |The stack ID.            |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Show stack details: JSON response**


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
   




