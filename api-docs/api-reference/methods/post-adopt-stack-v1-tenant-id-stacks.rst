
.. _post-adopt-stack:

Adopt stack
~~~~~~~~~~~

.. code::

    POST /v1/{tenant_id}/stacks

Creates a stack from existing resources.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|201                       |Created                  |The request has been     |
|                          |                         |fulfilled and resulted in|
|                          |                         |a new resource being     |
|                          |                         |created.                 |
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
-------

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{tenant_id}               |String                   |The ID of the tenant. A  |
|                          |                         |tenant is also known as  |
|                          |                         |an account or project.   |
+--------------------------+-------------------------+-------------------------+


This table shows the body parameters for the request:

+---------------------+-----------------+--------------------------------------+
|Name                 |Type             |Description                           |
+=====================+=================+======================================+
|\ **stack_name**     |String           |A name for the new stack. The value   |
|                     |*(Required)*     |must be unique within a project. The  |
|                     |                 |name must start with an ASCII letter  |
|                     |                 |and can contain ASCII letters,        |
|                     |                 |digits, underscores, periods, and     |
|                     |                 |hyphens. Specifically, the name must  |
|                     |                 |match the ``^[a-zA-Z][a-zA-Z0-9_.-    |
|                     |                 |]*$`` regular expression. When you    |
|                     |                 |delete or abandon a stack, its name   |
|                     |                 |might not be available for reuse for  |
|                     |                 |an unspecified period of time.        |
+---------------------+-----------------+--------------------------------------+
|\ **template_url**   |String           |A URI to the location containing the  |
|                     |*(Optional)*     |stack template on which to perform    |
|                     |                 |the specified operation. See the      |
|                     |                 |description of the ``template``       |
|                     |                 |parameter for information about the   |
|                     |                 |expected template content located at  |
|                     |                 |the URI. This parameter is only       |
|                     |                 |required when you omit the            |
|                     |                 |``template`` parameter. If you        |
|                     |                 |specify both parameters, this         |
|                     |                 |parameter is ignored.                 |
+---------------------+-----------------+--------------------------------------+
|\ **template**       |String           |The stack template on which to        |
|                     |*(Optional)*     |perform the specified operation. This |
|                     |                 |parameter is always provided as a     |
|                     |                 |``string`` in the JSON request body.  |
|                     |                 |The content of the string is a JSON-  |
|                     |                 |or YAML-formatted Orchestration       |
|                     |                 |template. For example: ``"template":  |
|                     |                 |{ "heat_template_version": "2013-05-  |
|                     |                 |23", ...}`` This parameter is         |
|                     |                 |required only when you omit the       |
|                     |                 |``template_url`` parameter. If you    |
|                     |                 |specify both parameters, this value   |
|                     |                 |overrides the ``template_url``        |
|                     |                 |parameter value.                      |
+---------------------+-----------------+--------------------------------------+
|\ **environment**    |String           |A JSON environment for the stack.     |
|                     |*(Optional)*     |                                      |
+---------------------+-----------------+--------------------------------------+
|\ **files**          |Map *(Optional)* |Supplies the contents of files        |
|                     |                 |referenced in the template or the     |
|                     |                 |environment. Stack templates and      |
|                     |                 |resource templates can explicitly     |
|                     |                 |reference files by using the          |
|                     |                 |``get_file`` intrinsic function. In   |
|                     |                 |addition, the ``environment``         |
|                     |                 |parameter can contain implicit        |
|                     |                 |references to files. The value is a   |
|                     |                 |JSON object, where each key is a      |
|                     |                 |relative or absolute URI which serves |
|                     |                 |as the name of a file, and the        |
|                     |                 |associated value provides the         |
|                     |                 |contents of the file. The following   |
|                     |                 |code shows the general structure of   |
|                     |                 |this parameter. ``{ ... "files": {    |
|                     |                 |"fileA.yaml": "Contents of the file", |
|                     |                 |"file:///usr/fileB.template":         |
|                     |                 |"Contents of the file",               |
|                     |                 |"http://example.com/fileC.template":  |
|                     |                 |"Contents of the file" } ... }``      |
|                     |                 |Additionally, some template authors   |
|                     |                 |encode their user data in a local     |
|                     |                 |file. The Orchestration client        |
|                     |                 |examines the template for the         |
|                     |                 |``get_file`` intrinsic function and   |
|                     |                 |adds an entry to the ``files`` map    |
|                     |                 |with the path to the file as the name |
|                     |                 |and the file contents as the value.   |
|                     |                 |So, a simple example looks like this: |
|                     |                 |``{ "files": { "myfile":              |
|                     |                 |"#!/bin/bash\necho \"Hello world\" >  |
|                     |                 |/root/testfile.txt" }, ...,           |
|                     |                 |"stack_name": "teststack",            |
|                     |                 |"template": { ..., "resources": {     |
|                     |                 |"my_server": { "type":                |
|                     |                 |"OS::Nova::Server", "properties": {   |
|                     |                 |..., "user_data": { "get_file":       |
|                     |                 |"myfile" } } } } }, "timeout_mins":   |
|                     |                 |60 }`` Do not use this parameter to   |
|                     |                 |provide the content of the template   |
|                     |                 |located at the address specified by   |
|                     |                 |``template_url``. Instead, use the    |
|                     |                 |``template`` parameter to supply the  |
|                     |                 |template content as part of the       |
|                     |                 |request.                              |
+---------------------+-----------------+--------------------------------------+
|\ **parameters**     |Object           |Supplies arguments for parameters     |
|                     |*(Optional)*     |defined in the stack template. The    |
|                     |                 |value is a JSON object, where each    |
|                     |                 |key is the name of a parameter        |
|                     |                 |defined in the template and the       |
|                     |                 |associated value is the argument to   |
|                     |                 |use for that parameter when           |
|                     |                 |instantiating the template. The       |
|                     |                 |following code shows the general      |
|                     |                 |structure of this parameter. In the   |
|                     |                 |example, ``a`` and ``b`` would be the |
|                     |                 |names of two parameters defined in    |
|                     |                 |the template. ``{ ... "parameters": { |
|                     |                 |"a": "Value", "b": "3" } ... }``      |
|                     |                 |While the service accepts JSON        |
|                     |                 |numbers for parameters with the type  |
|                     |                 |``number`` and JSON objects for       |
|                     |                 |parameters with the type ``json``,    |
|                     |                 |all parameter values are converted to |
|                     |                 |their string representation for       |
|                     |                 |storage in the created Stack. Clients |
|                     |                 |are encouraged to send all parameter  |
|                     |                 |values using their string             |
|                     |                 |representation for consistency        |
|                     |                 |between requests and responses from   |
|                     |                 |the Orchestration service. A value    |
|                     |                 |must be provided for each template    |
|                     |                 |parameter which does not specify a    |
|                     |                 |default value. However, this          |
|                     |                 |parameter is not allowed to contain   |
|                     |                 |JSON properties with names that do    |
|                     |                 |not match a parameter defined in the  |
|                     |                 |template. The ``files`` parameter     |
|                     |                 |maps logical file names to file       |
|                     |                 |contents. Both the ``get_file``       |
|                     |                 |intrinsic function and provider       |
|                     |                 |template functionality use this       |
|                     |                 |mapping. When you want to use a       |
|                     |                 |provider template, for example, the   |
|                     |                 |Orchestration service adds an entry   |
|                     |                 |to the ``files`` map by using: * The  |
|                     |                 |URL of the provider template as the   |
|                     |                 |name. * The contents of that file as  |
|                     |                 |the value. Additionally, some         |
|                     |                 |template authors encode their user    |
|                     |                 |data in a local file. The             |
|                     |                 |Orchestration client examines the     |
|                     |                 |template for the ``get_file``         |
|                     |                 |intrinsic function and adds an entry  |
|                     |                 |to the ``files`` map with the path to |
|                     |                 |the file as the name and the file     |
|                     |                 |contents as the value. So, a simple   |
|                     |                 |example looks like this: ``{ "files": |
|                     |                 |{ "myfile": "#!/bin/bash\necho        |
|                     |                 |\"Hello world\" > /root/testfile.txt" |
|                     |                 |}, ..., "stack_name": "teststack",    |
|                     |                 |"template": { ..., "resources": {     |
|                     |                 |"my_server": { "type":                |
|                     |                 |"OS::Nova::Server", "properties": {   |
|                     |                 |..., "user_data": { "get_file":       |
|                     |                 |"myfile" } } } } }, "timeout_mins":   |
|                     |                 |60 }``                                |
+---------------------+-----------------+--------------------------------------+
|\ **timeout_mins**   |String           |The timeout for stack creation in     |
|                     |*(Optional)*     |minutes.                              |
+---------------------+-----------------+--------------------------------------+
|\                    |String           |Existing resources data to adopt a    |
|**adopt_stack_data** |*(Required)*     |stack. Data returned by abandon stack |
|                     |                 |could be provided as                  |
|                     |                 |``adopt_stack_data``.                 |
+---------------------+-----------------+--------------------------------------+
|\                    |String           |Enables or disables deletion of all   |
|**disable_rollback** |*(Optional)*     |stack resources when stack creation   |
|                     |                 |fails. Set to ``True`` to keep all    |
|                     |                 |resources when stack creation fails.  |
|                     |                 |Set to ``False`` to delete all        |
|                     |                 |resources when stack creation fails.  |
|                     |                 |Default is ``True``.                  |
+---------------------+-----------------+--------------------------------------+

**Example Adopt stack: JSON request**


.. code::

   {
       "adopt_stack_data": {
           "action": "CREATE",
           "id": "bxxxxx4-0xx2-4xx1-axx6-exxxxxxxc",
           "name": "teststack",
           "resources": {
               "MyServer": {
                   "action": "CREATE",
                   "metadata": {},
                   "name": "MyServer",
                   "resource_data": {},
                   "resource_id": "cxxxx3-dxx3-4xx-bxx2-3xxxxxxxxa",
                   "status": "COMPLETE",
                   "type": "OS::Trove::Instance"
               }
           },
           "status": "COMPLETE",
           "template": {}
       },
       "stack_name": "{stack_name}",
       "template_url": "{template_url}",
       "timeout_mins": "{timeout_mins}"
   }


Response
--------

**Example Adopt stack: JSON response**


.. code::

   {
       "action": "CREATE",
       "id": "46c927bb-671a-43db-a29c-16a2610865ca",
       "name": "trove",
       "resources": {
           "mysql_server": {
               "action": "CREATE",
               "metadata": {},
               "name": "mysql_server",
               "resource_data": {},
               "resource_id": "74c5be7e-3e62-41e7-b455-93d1c32d56e3",
               "status": "COMPLETE",
               "type": "OS::Trove::Instance"
           }
       },
       "status": "COMPLETE",
       "template": {
           "heat-template-version": "2013-05-23",
           "description": "MySQL server instance",
           "parameters": {
               "instance_name": {
                   "description": "The database instance name",
                   "type": "string"
               }
           },
           "resources": {
               "mysql_server": {
                   "properties": {
                       "databases": [
                           {
                               "name": "testdbonetwo"
                           }
                       ],
                       "flavor": "1 GB General Purpose v1",
                       "name": "test-trove-db",
                       "size": 30,
                       "users": [
                           {
                               "databases": [
                                   "testdbonetwo"
                               ],
                               "name": "testuser",
                               "password": "testpass123"
                           }
                       ]
                   },
                   "type": "OS::Trove::Instance"
               }
           }
       }
   }
