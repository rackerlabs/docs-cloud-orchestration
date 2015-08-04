
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Send A Signal To A Resource -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Send A Signal To A Resource
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-send-a-signal-to-a-resource-v1-tenant-id-stacks-stack-name-stack-id-resources-resource-name-signal.html#request>`__
`Response <post-send-a-signal-to-a-resource-v1-tenant-id-stacks-stack-name-stack-id-resources-resource-name-signal.html#response>`__

.. code::

    POST /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/resources/{resource_name}/signal

Sends a signal to a specified resource.

The contents of the request body depends on the resource to which you send a signal.

Some resources cannot receive signals. If you send them a signal, they return a 400 error code.



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




