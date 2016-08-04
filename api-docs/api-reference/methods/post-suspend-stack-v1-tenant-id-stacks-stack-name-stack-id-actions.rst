
.. _post-suspend-stack-id-actions:

Suspend stack
~~~~~~~~~~~~~

.. code::

    POST /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/actions

Suspends a stack.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |                         |                         |
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


This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|suspend                   |String *(Required)*      |Specify the ``suspend``  |
|                          |                         |action in the request    |
|                          |                         |body.                    |
+--------------------------+-------------------------+-------------------------+

**Example Suspend stack: JSON request**


.. code::

   {
       "suspend": null
   }


Response
--------

This operation does not return a response body.
