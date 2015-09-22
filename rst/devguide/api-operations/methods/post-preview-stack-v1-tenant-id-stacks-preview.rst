
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-preview-stack-v1-tenant-id-stacks-preview:

Preview stack
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v1/{tenant_id}/stacks/preview

Previews a stack.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+
|400                       |Bad Request              |The request could not be |
|                          |                         |understood by the server |
|                          |                         |due to malformed syntax. |
+--------------------------+-------------------------+-------------------------+
|401                       |Unauthorized             |The request requires     |
|                          |                         |user authentication.     |
+--------------------------+-------------------------+-------------------------+
|409                       |Conflict                 |The request could not be |
|                          |                         |completed due to a       |
|                          |                         |conflict with the        |
|                          |                         |current state of the     |
|                          |                         |resource.                |
+--------------------------+-------------------------+-------------------------+
|500                       |Internal Server Error    |The server encountered   |
|                          |                         |an unexpected condition  |
|                          |                         |which prevented it from  |
|                          |                         |fulfilling the request.  |
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





This table shows the body parameters for the request:

+-------------------+-------------------+--------------------------------------+
|Name               |Type               |Description                           |
+===================+===================+======================================+
|\ **stack_name**   |String *(Required)*|A name for the new stack. The value   |
|                   |                   |must be unique within a project. The  |
|                   |                   |name must start with an ASCII letter  |
|                   |                   |and can contain ASCII letters,        |
|                   |                   |digits, underscores, periods, and     |
|                   |                   |hyphens. Specifically, the name must  |
|                   |                   |match the ``^[a-zA-Z][a-zA-Z0-9_.-    |
|                   |                   |]*$`` regular expression. When you    |
|                   |                   |delete or abandon a stack, its name   |
|                   |                   |might not be available for reuse for  |
|                   |                   |an unspecified period of time.        |
+-------------------+-------------------+--------------------------------------+
|\ **template_url** |String *(Optional)*|A URI to the location containing the  |
|                   |                   |stack template on which to perform    |
|                   |                   |the specified operation. See the      |
|                   |                   |description of the ``template``       |
|                   |                   |parameter for information about the   |
|                   |                   |expected template content located at  |
|                   |                   |the URI. This parameter is only       |
|                   |                   |required when you omit the            |
|                   |                   |``template`` parameter. If you        |
|                   |                   |specify both parameters, this         |
|                   |                   |parameter is ignored.                 |
+-------------------+-------------------+--------------------------------------+
|\ **template**     |String *(Optional)*|The stack template on which to        |
|                   |                   |perform the specified operation. This |
|                   |                   |parameter is always provided as a     |
|                   |                   |``string`` in the JSON request body.  |
|                   |                   |The content of the string is a JSON-  |
|                   |                   |or YAML-formatted Orchestration       |
|                   |                   |template. For example: ``"template":  |
|                   |                   |{ "heat_template_version": "2013-05-  |
|                   |                   |23", ...}`` This parameter is         |
|                   |                   |required only when you omit the       |
|                   |                   |``template_url`` parameter. If you    |
|                   |                   |specify both parameters, this value   |
|                   |                   |overrides the ``template_url``        |
|                   |                   |parameter value.                      |
+-------------------+-------------------+--------------------------------------+
|\ **files**        |Map *(Optional)*   |Supplies the contents of files        |
|                   |                   |referenced in the template or the     |
|                   |                   |environment. Stack templates and      |
|                   |                   |resource templates can explicitly     |
|                   |                   |reference files by using the          |
|                   |                   |``get_file`` intrinsic function. In   |
|                   |                   |addition, the ``environment``         |
|                   |                   |parameter can contain implicit        |
|                   |                   |references to files. The value is a   |
|                   |                   |JSON object, where each key is a      |
|                   |                   |relative or absolute URI which serves |
|                   |                   |as the name of a file, and the        |
|                   |                   |associated value provides the         |
|                   |                   |contents of the file. The following   |
|                   |                   |code shows the general structure of   |
|                   |                   |this parameter. ``{ ... "files": {    |
|                   |                   |"fileA.yaml": "Contents of the file", |
|                   |                   |"file:///usr/fileB.template":         |
|                   |                   |"Contents of the file",               |
|                   |                   |"http://example.com/fileC.template":  |
|                   |                   |"Contents of the file" } ... }``      |
|                   |                   |Additionally, some template authors   |
|                   |                   |encode their user data in a local     |
|                   |                   |file. The Orchestration client        |
|                   |                   |examines the template for the         |
|                   |                   |``get_file`` intrinsic function and   |
|                   |                   |adds an entry to the ``files`` map    |
|                   |                   |with the path to the file as the name |
|                   |                   |and the file contents as the value.   |
|                   |                   |So, a simple example looks like this: |
|                   |                   |``{ "files": { "myfile":              |
|                   |                   |"#!/bin/bash\necho \"Hello world\" >  |
|                   |                   |/root/testfile.txt" }, ...,           |
|                   |                   |"stack_name": "teststack",            |
|                   |                   |"template": { ..., "resources": {     |
|                   |                   |"my_server": { "type":                |
|                   |                   |"OS::Nova::Server", "properties": {   |
|                   |                   |..., "user_data": { "get_file":       |
|                   |                   |"myfile" } } } } }, "timeout_mins":   |
|                   |                   |60 }`` Do not use this parameter to   |
|                   |                   |provide the content of the template   |
|                   |                   |located at the address specified by   |
|                   |                   |``template_url``. Instead, use the    |
|                   |                   |``template`` parameter to supply the  |
|                   |                   |template content as part of the       |
|                   |                   |request.                              |
+-------------------+-------------------+--------------------------------------+
|\ **parameters**   |Object *(Optional)*|Supplies arguments for parameters     |
|                   |                   |defined in the stack template. The    |
|                   |                   |value is a JSON object, where each    |
|                   |                   |key is the name of a parameter        |
|                   |                   |defined in the template and the       |
|                   |                   |associated value is the argument to   |
|                   |                   |use for that parameter when           |
|                   |                   |instantiating the template. The       |
|                   |                   |following code shows the general      |
|                   |                   |structure of this parameter. In the   |
|                   |                   |example, ``a`` and ``b`` would be the |
|                   |                   |names of two parameters defined in    |
|                   |                   |the template. ``{ ... "parameters": { |
|                   |                   |"a": "Value", "b": "3" } ... }``      |
|                   |                   |While the service accepts JSON        |
|                   |                   |numbers for parameters with the type  |
|                   |                   |``number`` and JSON objects for       |
|                   |                   |parameters with the type ``json``,    |
|                   |                   |all parameter values are converted to |
|                   |                   |their string representation for       |
|                   |                   |storage in the created Stack. Clients |
|                   |                   |are encouraged to send all parameter  |
|                   |                   |values using their string             |
|                   |                   |representation for consistency        |
|                   |                   |between requests and responses from   |
|                   |                   |the Orchestration service. A value    |
|                   |                   |must be provided for each template    |
|                   |                   |parameter which does not specify a    |
|                   |                   |default value. However, this          |
|                   |                   |parameter is not allowed to contain   |
|                   |                   |JSON properties with names that do    |
|                   |                   |not match a parameter defined in the  |
|                   |                   |template. The ``files`` parameter     |
|                   |                   |maps logical file names to file       |
|                   |                   |contents. Both the ``get_file``       |
|                   |                   |intrinsic function and provider       |
|                   |                   |template functionality use this       |
|                   |                   |mapping. When you want to use a       |
|                   |                   |provider template, for example, the   |
|                   |                   |Orchestration service adds an entry   |
|                   |                   |to the ``files`` map by using: * The  |
|                   |                   |URL of the provider template as the   |
|                   |                   |name. * The contents of that file as  |
|                   |                   |the value. Additionally, some         |
|                   |                   |template authors encode their user    |
|                   |                   |data in a local file. The             |
|                   |                   |Orchestration client examines the     |
|                   |                   |template for the ``get_file``         |
|                   |                   |intrinsic function and adds an entry  |
|                   |                   |to the ``files`` map with the path to |
|                   |                   |the file as the name and the file     |
|                   |                   |contents as the value. So, a simple   |
|                   |                   |example looks like this: ``{ "files": |
|                   |                   |{ "myfile": "#!/bin/bash\necho        |
|                   |                   |\"Hello world\" > /root/testfile.txt" |
|                   |                   |}, ..., "stack_name": "teststack",    |
|                   |                   |"template": { ..., "resources": {     |
|                   |                   |"my_server": { "type":                |
|                   |                   |"OS::Nova::Server", "properties": {   |
|                   |                   |..., "user_data": { "get_file":       |
|                   |                   |"myfile" } } } } }, "timeout_mins":   |
|                   |                   |60 }``                                |
+-------------------+-------------------+--------------------------------------+





**Example Preview stack: JSON request**


.. code::

   {
       "files": {},
       "disable_rollback": true,
       "parameters": {
           "flavor": "2 GB General Purpose v1"
       },
       "stack_name": "teststack",
       "template": {
           "heat_template_version": "2013-05-23",
           "description": "Simple template to test heat commands",
           "parameters": {
               "flavor": {
                   "default": "1 GB General Purpose v1",
                   "type": "string"
               }
           },
           "resources": {
               "hello_world": {
                   "type": "OS::Nova::Server",
                   "properties": {
                       "key_name": "heat_key",
                       "flavor": {
                           "get_param": "flavor"
                       },
                       "image": "Ubuntu 12.04 LTS (Precise Pangolin) (PV)",
                       "user_data": "#!/bin/bash -xv\necho \"hello world\" &gt; /root/hello-world.txt\n"
                   }
               }
           }
       },
       "timeout_mins": 60
   }
   





Response
""""""""""""""""





This table shows the body parameters for the response:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|\ **parent**              |String *(Required)*      |The stack ID of the      |
|                          |                         |parent stack, if this is |
|                          |                         |a nested stack.          |
+--------------------------+-------------------------+-------------------------+
|\ **id**                  |String *(Required)*      |The stack ID.            |
+--------------------------+-------------------------+-------------------------+
|\ **stack_name**          |String *(Required)*      |The name of the stack.   |
+--------------------------+-------------------------+-------------------------+
|\ **description**         |String *(Required)*      |A description of the     |
|                          |                         |stack.                   |
+--------------------------+-------------------------+-------------------------+
|template_description      |String *(Required)*      |A description of the     |
|                          |                         |template that defines    |
|                          |                         |the stack.               |
+--------------------------+-------------------------+-------------------------+
|\ **timeout_mins**        |Integer *(Required)*     |Timelines for stack      |
|                          |                         |creation.                |
+--------------------------+-------------------------+-------------------------+
|\ **disable_rollback**    |String *(Required)*      |Enables or disables      |
|                          |                         |stack rollback when      |
|                          |                         |stack creation fails.    |
|                          |                         |Set to ``True`` to       |
|                          |                         |rollback the stack when  |
|                          |                         |stack creation fails.    |
|                          |                         |Set to ``False`` to      |
|                          |                         |disable stack rollback   |
|                          |                         |when stack creation      |
|                          |                         |fails. Default is        |
|                          |                         |``True``.                |
+--------------------------+-------------------------+-------------------------+
|\ **capabilities**        |String *(Required)*      |List of stack            |
|                          |                         |capabilities for stack.  |
+--------------------------+-------------------------+-------------------------+
|\ **notification_topics** |String *(Required)*      |List of notification     |
|                          |                         |topics for stack.        |
+--------------------------+-------------------------+-------------------------+
|\ **updated_time**        |String *(Required)*      |Time of last stack       |
|                          |                         |update in the following  |
|                          |                         |format: ``YYYY-MM-       |
|                          |                         |DDThh:mm:ssTZD``, where  |
|                          |                         |``TZD`` is the time zone |
|                          |                         |designator.              |
+--------------------------+-------------------------+-------------------------+
|\ **stack_owner**         |String *(Required)*      |Stack owner name.        |
+--------------------------+-------------------------+-------------------------+
|\ **parameters**          |String *(Required)*      |List of parameters       |
|                          |                         |defined for the stack.   |
+--------------------------+-------------------------+-------------------------+
|\ **resources**           |String *(Required)*      |List of stack resources. |
+--------------------------+-------------------------+-------------------------+







**Example Preview stack: JSON response**


.. code::

   {
       "stack": {
           "capabilities": [],
           "creation_time": "2015-01-31T15:12:36Z",
           "description": "HOT template for Nova Server resource.\n",
           "disable_rollback": true,
           "id": "None",
           "links": [
               {
                   "href": "http://192.168.122.102:8004/v1/6e18cc2bdbeb48a5basad2dc499f6804/stacks/test_stack/None",
                   "rel": "self"
               }
           ],
           "notification_topics": [],
           "parameters": {
               "OS::project_id": "6e18cc2bdbeb48a5basad2dc499f6804",
               "OS::stack_id": "None",
               "OS::stack_name": "teststack",
               "admin_user": "cloud-user",
               "flavor": "1 GB General Purpose v1",
               "image": "Ubuntu 12.04 LTS (Precise Pangolin) (PV)",
               "key_name": "heat_key",
               "server_name": "MyServer"
           },
           "parent": null,
           "resources": [
               {
                   "attributes": {},
                   "description": "",
                   "metadata": {},
                   "physical_resource_id": "",
                   "properties": {
                       "description": "Ping and SSH",
                       "name": "the_sg",
                       "rules": [
                           {
                               "direction": "ingress",
                               "ethertype": "IPv4",
                               "port_range_max": null,
                               "port_range_min": null,
                               "protocol": "icmp",
                               "remote_group_id": null,
                               "remote_ip_prefix": null,
                               "remote_mode": "remote_ip_prefix"
                           },
                           {
                               "direction": "ingress",
                               "ethertype": "IPv4",
                               "port_range_max": 65535,
                               "port_range_min": 1,
                               "protocol": "tcp",
                               "remote_group_id": null,
                               "remote_ip_prefix": null,
                               "remote_mode": "remote_ip_prefix"
                           },
                           {
                               "direction": "ingress",
                               "ethertype": "IPv4",
                               "port_range_max": 65535,
                               "port_range_min": 1,
                               "protocol": "udp",
                               "remote_group_id": null,
                               "remote_ip_prefix": null,
                               "remote_mode": "remote_ip_prefix"
                           }
                       ]
                   },
                   "required_by": [
                       "server1"
                   ],
                   "resource_action": "INIT",
                   "resource_identity": {
                       "path": "/resources/the_sg_res",
                       "stack_id": "None",
                       "stack_name": "teststack",
                       "tenant": "6e18cc2bdbeb48a5b3cad2dc499f6804"
                   },
                   "resource_name": "the_sg_res",
                   "resource_status": "COMPLETE",
                   "resource_status_reason": "",
                   "resource_type": "OS::Neutron::SecurityGroup",
                   "stack_identity": {
                       "path": "",
                       "stack_id": "None",
                       "stack_name": "teststack",
                       "tenant": "6e18cc2bdbeb48a5b3cad2dc499f6804"
                   },
                   "stack_name": "teststack",
                   "updated_time": "2015-01-31T15:12:36Z"
               },
               {
                   "attributes": {
                       "accessIPv4": "",
                       "accessIPv6": "",
                       "addresses": "",
                       "console_urls": "",
                       "first_address": "",
                       "instance_name": "",
                       "name": "MyServer",
                       "networks": "",
                       "show": ""
                   },
                   "description": "",
                   "metadata": {},
                   "physical_resource_id": "",
                   "properties": {
                       "admin_pass": null,
                       "admin_user": "cloud-user",
                       "availability_zone": null,
                       "block_device_mapping": null,
                       "config_drive": null,
                       "diskConfig": null,
                       "flavor": "1 GB General Purpose v1",
                       "flavor_update_policy": "RESIZE",
                       "image": "Ubuntu 12.04 LTS (Precise Pangolin) (PV)",
                       "image_update_policy": "REPLACE",
                       "key_name": "heat_key",
                       "metadata": {
                           "ha_stack": "None"
                       },
                       "name": "MyServer",
                       "networks": [
                           {
                               "fixed_ip": null,
                               "network": "private",
                               "port": null,
                               "uuid": null
                           }
                       ],
                       "personality": {},
                       "reservation_id": null,
                       "scheduler_hints": null,
                       "security_groups": [
                           "None"
                       ],
                       "software_config_transport": "POLL_SERVER_CFN",
                       "user_data": "",
                       "user_data_format": "HEAT_CFNTOOLS"
                   },
                   "required_by": [],
                   "resource_action": "INIT",
                   "resource_identity": {
                       "path": "/resources/hello_world",
                       "stack_id": "None",
                       "stack_name": "teststack",
                       "tenant": "6e18cc2bdbeb48a3433cad2dc499sdf32234"
                   },
                   "resource_name": "hello_world",
                   "resource_status": "COMPLETE",
                   "resource_status_reason": "",
                   "resource_type": "OS::Nova::Server",
                   "stack_identity": {
                       "path": "",
                       "stack_id": "None",
                       "stack_name": "teststack",
                       "tenant": "6e18cc2bdbeb48a3433cad2dc499sdf32234"
                   },
                   "stack_name": "teststack",
                   "updated_time": "2015-01-31T15:12:36Z"
               }
           ],
           "stack_name": "test_stack",
           "stack_owner": "admin",
           "template_description": "HOT template for Nova Server resource.\n",
           "timeout_mins": null,
           "updated_time": null
       }
   }
   




