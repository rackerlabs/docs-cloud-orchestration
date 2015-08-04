
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Resource Schema -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Show Resource Schema
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-resource-schema-v1-tenant-id-resource-types-type-name.html#request>`__
`Response <get-show-resource-schema-v1-tenant-id-resource-types-type-name.html#response>`__

.. code::

    GET /v1/{tenant_id}/resource_types/{type_name}

Shows the interface schema for a specified resource type. This schema describes the properties that can be set on the resource, their types, constraints, descriptions, and default values. Additionally, the resource attributes and their descriptions are provided.



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
|{type_name}               |*(Required)*             |The name of a resource   |
|                          |                         |type.                    |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example Show Resource Schema: JSON response**


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
    

