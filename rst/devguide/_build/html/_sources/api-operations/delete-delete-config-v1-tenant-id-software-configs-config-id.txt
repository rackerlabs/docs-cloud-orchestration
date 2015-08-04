
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Delete Config -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Delete Config
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <delete-delete-config-v1-tenant-id-software-configs-config-id.html#request>`__
`Response <delete-delete-config-v1-tenant-id-software-configs-config-id.html#response>`__

.. code::

    DELETE /v1/{tenant_id}/software_configs/{config_id}

Deletes a software configuration.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|204                       |                         |                         |
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
|{config_id}               |*(Required)*             |The configuration ID.    |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




