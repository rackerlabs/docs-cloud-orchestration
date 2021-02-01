
.. _get-find-stack-resources:

Find stack resources
~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/resources

Finds the canonical URL for the resource list of a specified stack.

The canonical URL is returned for only non-deleted stacks. To fetch the resource list for deleted stacks, use the following endpoint:

 ``/v1/{tenant_id}/stacks/{stack_name}/{stack_id}/resources``


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

**Example Find stack resources: JSON response**


Lists resources for the specified stack in JSON format.
