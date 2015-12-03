
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

.. _post-create-stack-v1-tenant-id-stacks:

Create stack
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    POST /v1/{tenant_id}/stacks

Creates a stack.



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
|\ **stack_name**   |String *(Required)*|A name for the new stack. This value  |
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
|\ **tags**         |String *(Optional)*|One or more simple string tags to     |
|                   |                   |associate with the stack. To          |
|                   |                   |associate multiple tags with a stack, |
|                   |                   |separate the tags with commas. For    |
|                   |                   |example, ``tag1,tag2``.               |
+-------------------+-------------------+--------------------------------------+
|parameters.\       |String *(Optional)*|User-defined parameter names to pass  |
|**param_name-n**   |                   |to the template.                      |
+-------------------+-------------------+--------------------------------------+
|parameters.\       |String *(Optional)*|User-defined parameter values to pass |
|**param_value-n**  |                   |to the template.                      |
+-------------------+-------------------+--------------------------------------+





**Example Create stack: JSON request**


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
|\ **stack_name**          |String *(Required)*      |The name of the stack to |
|                          |                         |create.                  |
+--------------------------+-------------------------+-------------------------+
|\ **template_url**        |String *(Required)*      |The URL of the template. |
+--------------------------+-------------------------+-------------------------+
|\ **template**            |String *(Required)*      |A JSON template.         |
+--------------------------+-------------------------+-------------------------+
|\ **environment**         |String *(Optional)*      |A JSON environment for   |
|                          |                         |the stack.               |
+--------------------------+-------------------------+-------------------------+
|\ **files**               |String *(Optional)*      |A map of file names to   |
|                          |                         |JSON template bodies.    |
|                          |                         |File names are provider  |
|                          |                         |resource templates, as   |
|                          |                         |referenced in the        |
|                          |                         |environment.             |
+--------------------------+-------------------------+-------------------------+
|parameters.\ **param_name-|String *(Optional)*      |User-defined parameter   |
|n**                       |                         |names to pass to the     |
|                          |                         |template.                |
+--------------------------+-------------------------+-------------------------+
|parameters.\              |String *(Optional)*      |User-defined parameter   |
|**param_value-n**         |                         |values to pass to the    |
|                          |                         |template.                |
+--------------------------+-------------------------+-------------------------+
|\ **timeout_mins**        |Integer *(Optional)*     |The timeout for stack    |
|                          |                         |creation in minutes.     |
+--------------------------+-------------------------+-------------------------+
|\ **disable_rollback**    |String *(Optional)*      |Enables or disables      |
|                          |                         |deletion of all          |
|                          |                         |previously-created stack |
|                          |                         |resources when stack     |
|                          |                         |creation fails. Set to   |
|                          |                         |``True`` to keep all     |
|                          |                         |previously-created stack |
|                          |                         |resources when stack     |
|                          |                         |creation fails. Set to   |
|                          |                         |``False`` to delete all  |
|                          |                         |previously-created stack |
|                          |                         |resources when stack     |
|                          |                         |creation fails. Default  |
|                          |                         |is ``True``.             |
+--------------------------+-------------------------+-------------------------+
|\ **stack_id**            |String *(Required)*      |The system-assigned ID   |
|                          |                         |for the stack.           |
+--------------------------+-------------------------+-------------------------+
|\ **links**               |String *(Required)*      |A list of URLs for the   |
|                          |                         |stack.                   |
+--------------------------+-------------------------+-------------------------+
|\ **rel**                 |String *(Required)*      |A reference to the       |
|                          |                         |stack's parent. If no    |
|                          |                         |parent, reference is     |
|                          |                         |``self``.                |
+--------------------------+-------------------------+-------------------------+







**Example Create stack: JSON response**


.. code::

   {
       "stack": {
           "id": "3095aefc-09fb-4bc7-b1f0-f21a304e864c",
           "links": [
               {
                   "href": "http://192.168.123.200:8004/v1/eb1c63a4f77141548385f113a28f0f52/stacks/simple_stack/3095aefc-09fb-4bc7-b1f0-f21a304e864c",
                   "rel": "self"
               }
           ]
       }
   }
   




