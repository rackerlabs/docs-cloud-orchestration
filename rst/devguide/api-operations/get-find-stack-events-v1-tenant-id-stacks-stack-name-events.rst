
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Find Stack Events -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Find Stack Events
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-find-stack-events-v1-tenant-id-stacks-stack-name-events.html#request>`__
`Response <get-find-stack-events-v1-tenant-id-stacks-stack-name-events.html#response>`__

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/events

Finds the canonical URL for the event list of a specified stack.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|302                       |                         |                         |
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








Response
^^^^^^^^^^^^^^^^^^




