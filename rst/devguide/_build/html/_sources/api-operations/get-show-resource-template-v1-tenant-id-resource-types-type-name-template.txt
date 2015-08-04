
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Show Resource Template -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Show Resource Template
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-show-resource-template-v1-tenant-id-resource-types-type-name-template.html#request>`__
`Response <get-show-resource-template-v1-tenant-id-resource-types-type-name-template.html#response>`__

.. code::

    GET /v1/{tenant_id}/resource_types/{type_name}/template

Shows the template representation for a specified resource type.

The returned template contains a single resource of the specified type. Each resource property is mapped to a template parameter and each resource attribute is mapped to a template output.

You can use these templates as a starting place for creating customized, template-based resources or as examples of using the particular resource in another template.



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





**Example Show Resource Template: JSON response**


.. code::

    {
        "HeatTemplateFormatVersion": "2012-12-12",
        "Outputs": {
            "private_key": {
                "Description": "The private key if it has been saved.",
                "Value": "{\"Fn::GetAtt\": [\"KeyPair\", \"private_key\"]}"
            },
            "public_key": {
                "Description": "The public key.",
                "Value": "{\"Fn::GetAtt\": [\"KeyPair\", \"public_key\"]}"
            }
        },
        "Parameters": {
            "name": {
                "Description": "The name of the key pair.",
                "Type": "String"
            },
            "public_key": {
                "Description": "The optional public key. This allows users to supply the public key from a pre-existing key pair. If not supplied, a new key pair will be generated.",
                "Type": "String"
            },
            "save_private_key": {
                "AllowedValues": [
                    "True",
                    "true",
                    "False",
                    "false"
                ],
                "Default": false,
                "Description": "True if the system should remember a generated private key; False otherwise.",
                "Type": "String"
            }
        },
        "Resources": {
            "KeyPair": {
                "Properties": {
                    "name": {
                        "Ref": "name"
                    },
                    "public_key": {
                        "Ref": "public_key"
                    },
                    "save_private_key": {
                        "Ref": "save_private_key"
                    }
                },
                "Type": "OS::Nova::KeyPair"
            }
        }
    }
    

