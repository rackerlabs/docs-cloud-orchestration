
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _get-show-resource-schema-v1-tenant-id-resource-types-type-name:

Show resource schema
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1/{tenant_id}/resource_types/{type_name}

Shows the interface schema for a specified resource type. This schema describes the properties that can be set on the resource, their types, constraints, descriptions, and default values. Additionally, the resource attributes and their descriptions are provided.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request could not be |
|                          |                         |understood by the server |
|                          |                         |due to malformed syntax. |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |The request requires     |
|                          |                         |user authentication.     |
+--------------------------+-------------------------+-------------------------+


Request
""""""""""""""""




This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{tenant_id}               |String                   |The ID of the tenant. A  |
|                          |                         |tenant is also known as  |
|                          |                         |an account or project.   |
+--------------------------+-------------------------+-------------------------+
|{type_name}               |String *(Required)*      |The name of a resource   |
|                          |                         |type.                    |
+--------------------------+-------------------------+-------------------------+





This operation does not accept a request body.




Response
""""""""""""""""










**Example Show resource schema: JSON response**


.. code::

   {
       "attributes": {
           "an_attribute": {
               "description": "A runtime value of the resource."
           }
       },
       "properties": {
           "a_property": {
               "constraints": [
                   {
                       "description": "Must be between 1 and 255 characters",
                       "length": {
                           "max": 255,
                           "min": 1
                       }
                   }
               ],
               "description": "A resource description.",
               "required": true,
               "type": "string",
               "update_allowed": false
           }
       },
       "resource_type": "OS::Heat::AResourceName",
       "support_status": {
           "message": "A status message",
           "status": "SUPPORTED",
           "version": "2014.1"
       }
   }
   




