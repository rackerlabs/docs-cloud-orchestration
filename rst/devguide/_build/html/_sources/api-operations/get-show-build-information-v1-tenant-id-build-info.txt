
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Build Information -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Show Build Information
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-build-information-v1-tenant-id-build-info.html#request>`__
`Response <get-show-build-information-v1-tenant-id-build-info.html#response>`__

.. code::

    GET /v1/{tenant_id}/build_info

Shows build information for an Orchestration deployment.



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








Response
^^^^^^^^^^^^^^^^^^





**Example Show Build Information: JSON response**


.. code::

    {
        "api": {
            "revision": "{api_build_revision}"
        },
        "engine": {
            "revision": "{engine_build_revision}"
        }
    }

