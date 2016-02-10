
.. _get-list-resources-v1-tenant-id-stacks-stack-name-stack-id-resources:

List resources
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    GET /v1/{tenant_id}/stacks/{stack_name}/{stack_id}/resources

Lists resources in a stack.



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
|stack_name                |String *(Required)*      |The name of a stack.     |
+--------------------------+-------------------------+-------------------------+
|{stack_id}                |String *(Required)*      |The stack ID.            |
+--------------------------+-------------------------+-------------------------+



This table shows the query parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|nested_depth              |String *(Optional)*      |Includes resources from  |
|                          |                         |nested stacks up to the  |
|                          |                         |``nested_depth`` levels  |
|                          |                         |of recursion.            |
+--------------------------+-------------------------+-------------------------+
|with_detail               |String *(Optional)*      |Enables detailed         |
|                          |                         |resource information for |
|                          |                         |each resource in list of |
|                          |                         |resources.               |
+--------------------------+-------------------------+-------------------------+




This operation does not accept a request body.




Response
""""""""""""""""










**Example List resources: JSON response**


Lists resources in the specified stack in JSON format.

.. code::

   {
       "resources": [
           {
               "creation_time": "2015-06-25T14:59:53",
               "links": [
                   {
                       "href": "http://hostname/v1/1234/stacks/mystack/629a32d0-ac4f-4f63-b58d-f0d047b1ba4c/resources/random_key_name",
                       "rel": "self"
                   },
                   {
                       "href": "http://hostname/v1/1234/stacks/mystack/629a32d0-ac4f-4f63-b58d-f0d047b1ba4c",
                       "rel": "stack"
                   }
               ],
               "logical_resource_id": "random_key_name",
               "physical_resource_id": "mystack-random_key_name-pmjmy5pks735",
               "required_by": [],
               "resource_name": "random_key_name",
               "resource_status": "CREATE_COMPLETE",
               "resource_status_reason": "state changed",
               "resource_type": "OS::Heat::RandomString",
               "updated_time": "2015-06-25T14:59:53"
           }
       ]
   }
   




