
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
Validate Template -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

Validate Template
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <post-validate-template-v1-tenant-id-validate.html#request>`__
`Response <post-validate-template-v1-tenant-id-validate.html#response>`__

.. code::

    POST /v1/{tenant_id}/validate

Validates a specified template.



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





This table shows the body parameters for the request:

+-------------------------+-------------------------+--------------------------+
|Name                     |Type                     |Description               |
+=========================+=========================+==========================+
|template_url             |string *(Required)*      |A URI to the location     |
|                         |                         |containing the stack      |
|                         |                         |template on which to      |
|                         |                         |perform the specified     |
|                         |                         |operation. See the        |
|                         |                         |description of the        |
|                         |                         |``template`` parameter    |
|                         |                         |for information about the |
|                         |                         |expected template content |
|                         |                         |located at the URI. This  |
|                         |                         |parameter is only         |
|                         |                         |required when you omit    |
|                         |                         |the ``template``          |
|                         |                         |parameter. If you specify |
|                         |                         |both parameters, this     |
|                         |                         |parameter is ignored.     |
+-------------------------+-------------------------+--------------------------+
|template                 |string *(Required)*      |The stack template on     |
|                         |                         |which to perform the      |
|                         |                         |specified operation. This |
|                         |                         |parameter is always       |
|                         |                         |provided as a ``string``  |
|                         |                         |in the JSON request body. |
|                         |                         |The content of the string |
|                         |                         |is a JSON- or YAML-       |
|                         |                         |formatted Orchestration   |
|                         |                         |template. For example:    |
|                         |                         |"template": {             |
|                         |                         |"heat_template_version":  |
|                         |                         |"2013-05-23", ...}This    |
|                         |                         |parameter is required     |
|                         |                         |only when you omit the    |
|                         |                         |``template_url``          |
|                         |                         |parameter. If you specify |
|                         |                         |both parameters, this     |
|                         |                         |value overrides the       |
|                         |                         |``template_url``          |
|                         |                         |parameter value.          |
+-------------------------+-------------------------+--------------------------+
|environment              |string *(Required)*      |A JSON environment for    |
|                         |                         |the stack.                |
+-------------------------+-------------------------+--------------------------+





**Example Validate Template: JSON request**


.. code::

    {
        "template_url": "/PATH_TO_HEAT_TEMPLATES/WordPress_Single_Instance.template"
    }
    


Response
^^^^^^^^^^^^^^^^^^


This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|Description               |*(Required)*             |The description          |
|                          |                         |specified in the         |
|                          |                         |template.                |
+--------------------------+-------------------------+-------------------------+
|Parameters                |object *(Required)*      |An object that defines   |
|                          |                         |all input parameters     |
|                          |                         |that are defined in the  |
|                          |                         |template. Indexed by     |
|                          |                         |parameter name.          |
+--------------------------+-------------------------+-------------------------+
|ParameterGroups           |list *(Required)*        |A list of parameter      |
|                          |                         |groups. Each group       |
|                          |                         |contains a list of       |
|                          |                         |parameter names.         |
+--------------------------+-------------------------+-------------------------+





**Example Validate Template: JSON response**


.. code::

    {
        "Description": "A template that provides a single server instance.",
        "Parameters": {
            "server-size": {
                "default": "1GB Standard Instance",
                "description": "Server size",
                "type": "String",
                "constraints": [
                    {
                        "allowed_values": [
                            "512MB Standard Instance",
                            "1GB Standard Instance",
                            "4GB Standard Instance",
                            "8GB Standard Instance"
                        ],
                        "description": "Must be a valid server size."
                    }
                ]
            },
            "key_name": {
                "description": "Keypair name for SSH access to the server",
                "required": true,
                "type": "String"
            },
            "server_name": {
                "default": "My server",
                "description": "My server",
                "type": "String"
            }
        },
        "ParameterGroups": [
            {
                "label": "Parameter groups",
                "description": "My parameter groups",
                "parameters": [
                    "param_name-1",
                    "param_name-2"
                ]
            }
        ]
    }
    

