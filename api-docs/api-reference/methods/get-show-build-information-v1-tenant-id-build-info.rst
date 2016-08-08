
.. _get-show-build-information:

Show build information
~~~~~~~~~~~~~~~~~~~~~~

.. code::

    GET /v1/{tenant_id}/build_info

Shows build information for an Orchestration deployment.



This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
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


This operation does not accept a request body.

Response
--------

**Example Show build information: JSON response**


.. code::

   {
       "api": {
           "revision": "{api_build_revision}"
       },
       "engine": {
           "revision": "{engine_build_revision}"
       }
   }
