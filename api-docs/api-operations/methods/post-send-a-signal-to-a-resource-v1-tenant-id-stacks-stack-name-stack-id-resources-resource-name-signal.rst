
.. _post-send-a-signal-to-a-resource-v1-tenant-id-stacks-stack-name-stack-id-resources-resource-name-signal:

Send a signal to a resource
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name}/signal

Sends a signal to a specified resource.

The contents of the request body depends on the resource to which you send a signal.

Some resources cannot receive signals. If you send them a signal, they return a 400 error code.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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
|{resource_name}           |String *(Required)*      |The name of a resource   |
|                          |                         |in the stack.            |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""






This operation does not return a response body.




