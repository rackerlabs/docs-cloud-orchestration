
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Resume Stack -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Resume Stack
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-resume-stack-v1-tenant-id-stacks-stack-name-stack-id-actions.html#request>`__
`Response <post-resume-stack-v1-tenant-id-stacks-stack-name-stack-id-actions.html#response>`__

.. code::

    POST /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/actions

Resumes a suspended stack.



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
|resume                    |*(Required)*             |Specify the ``resume``   |
|                          |                         |action in the request    |
|                          |                         |body.                    |
+--------------------------+-------------------------+-------------------------+





**Example Resume Stack: JSON request**


.. code::

    {
        "resume": null
    }


Response
^^^^^^^^^^^^^^^^^^




