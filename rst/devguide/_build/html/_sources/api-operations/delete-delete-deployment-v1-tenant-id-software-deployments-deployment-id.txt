
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Delete Deployment -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Delete Deployment
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <delete-delete-deployment-v1-tenant-id-software-deployments-deployment-id.html#request>`__
`Response <delete-delete-deployment-v1-tenant-id-software-deployments-deployment-id.html#response>`__

.. code::

    DELETE /v1/{tenant_id}/software_deployments/{deployment_id}

Deletes a specified software deployment.



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
|{deployment_id}           |*(Required)*             |The deployment ID.       |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^




