
.. _delete-stack-id:

Delete stack
~~~~~~~~~~~~

.. code::

    DELETE /v1/{tenant_id}/stacks/{stack_name}/{stack_id}

Deletes a specified stack and any snapshots of that stack.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |No Content               |The server has fulfilled |
|                          |                         |the request but does not |
|                          |                         |need to return an entity-|
|                          |                         |body, and might want to  |
|                          |                         |return updated meta-     |
|                          |                         |information.             |
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
|{stack_id}                |String *(Required)*      |The stack ID.            |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.

Response
--------

This operation does not return a response body.
