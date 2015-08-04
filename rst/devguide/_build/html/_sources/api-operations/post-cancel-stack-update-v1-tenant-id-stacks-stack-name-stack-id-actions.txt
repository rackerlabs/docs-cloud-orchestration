
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Cancel Stack Update -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Cancel Stack Update
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-cancel-stack-update-v1-tenant-id-stacks-stack-name-stack-id-actions.html#request>`__
`Response <post-cancel-stack-update-v1-tenant-id-stacks-stack-name-stack-id-actions.html#response>`__

.. code::

    POST /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/actions

Cancels a currently running update of a stack.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |                         |                         |
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





This table shows the body parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|cancel_update             |*(Required)*             |Specify the              |
|                          |                         |``cancel_update`` action |
|                          |                         |in the request body.     |
+--------------------------+-------------------------+-------------------------+





**Example Cancel Stack Update: JSON request**


.. code::

    {
        "cancel_update": null
    }
    


Response
^^^^^^^^^^^^^^^^^^




