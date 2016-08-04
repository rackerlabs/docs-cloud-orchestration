
.. _get-find-stack-events:

Find stack events
~~~~~~~~~~~~~~~~~

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/events

Finds the canonical URL for the event list of a specified stack.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|302                       |Found                    |The requested resource   |
|                          |                         |resides temporarily under|
|                          |                         |a different URI.         |
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

This operation does not return a response body.
