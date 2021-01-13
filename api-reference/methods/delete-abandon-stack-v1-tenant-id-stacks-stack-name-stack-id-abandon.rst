
.. _delete-abandon-stack-v1-tenant-id-stacks-stack-name-stack-id-abandon:

Abandon stack
~~~~~~~~~~~~~

.. code::

    DELETE /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/abandon

Deletes a specified stack but leaves its resources intact, and returns data
describing the stack and its resources.

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
|404                       |Not Found                |The server has not found |
|                          |                         |anything matching the    |
|                          |                         |Request-URI.             |
+--------------------------+-------------------------+-------------------------+
|500                       |Internal Server Error    |The server encountered   |
|                          |                         |an unexpected condition  |
|                          |                         |which prevented it from  |
|                          |                         |fulfilling the request.  |
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
|stack_name                |String *(Required)*      |The name of a stack.     |
+--------------------------+-------------------------+-------------------------+
|{stack_id}                |String *(Required)*      |The stack ID.            |
+--------------------------+-------------------------+-------------------------+

This operation does not accept a request body.




Response
--------

**Example Abandon stack: JSON response**


.. code::

   {
       "status": "COMPLETE",
       "name": "g",
       "dry_run": true,
       "template": {
           "outputs": {
               "instance_ip": {
                   "value": {
                       "str_replace": {
                           "params": {
                               "username": "ec2-user",
                               "hostname": {
                                   "get_attr": [
                                       "server",
                                       "first_address"
                                   ]
                               }
                           },
                           "template": "ssh username@hostname"
                       }
                   }
               }
           },
           "heat_template_version": "2013-05-23",
           "resources": {
               "server": {
                   "type": "OS::Nova::Server",
                   "properties": {
                       "key_name": {
                           "get_param": "key_name"
                       },
                       "image": {
                           "get_param": "image"
                       },
                       "flavor": {
                           "get_param": "flavor"
                       }
                   }
               }
           },
           "parameters": {
               "key_name": {
                   "default": "heat_key",
                   "type": "string"
               },
               "image": {
                   "default": "Ubuntu 12.04 LTS (Precise Pangolin) (PV)",
                   "type": "string"
               },
               "flavor": {
                   "default": "1 GB General Purpose v1",
                   "type": "string"
               }
           }
       },
       "action": "CREATE",
       "id": "16934ca3-40e0-4fb2-a289-a700662ec05a",
       "resources": {
           "server": {
               "status": "COMPLETE",
               "name": "server",
               "resource_data": {},
               "resource_id": "39d5dad7-7d7a-4cc8-bd84-851e9e2ff4ea",
               "action": "CREATE",
               "type": "OS::Nova::Server",
               "metadata": {}
           }
       }
   }
