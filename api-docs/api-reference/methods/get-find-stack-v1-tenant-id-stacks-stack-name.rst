
.. _get-find-stack-name:

Find stack
~~~~~~~~~~

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}

Finds the canonical URL for a specified stack.

Also works with verbs other than ``GET``, so you can perform ``PUT`` and ``DELETE`` operations on a current stack. Set your client to follow redirects. Note that when redirecting, the request method should not change, as defined in RFC2626. However, in many clients the default behavior is to change the method to ``GET`` when you receive a 302 because this behavior is ubiquitous in web browsers.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |The request has been     |
|                          |                         |accepted for processing, |
|                          |                         |but the processing has   |
|                          |                         |not been completed.      |
+--------------------------+-------------------------+-------------------------+
|302                       |Found                    |The requested resource   |
|                          |                         |resides temporarily under|
|                          |                         |a different URI.         |
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
-------

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

This operation does not accept a request body.

Response
--------

**Example Find stack: JSON response**


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
