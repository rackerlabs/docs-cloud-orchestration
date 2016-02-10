
.. _put-update-stack-v1-tenant-id-stacks-stack-name-stack-id:

Update stack
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

.. code::

    PUT /v1/{tenant_id}/stacks/{stack_name}/{stack_id}

Updates a specified stack.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|202                       |Accepted                 |The request has been     |
|                          |                         |accepted for processing, |
|                          |                         |but the processing has   |
|                          |                         |not been completed.      |
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





This table shows the body parameters for the request:

+-------------------+-------------------+--------------------------------------+
|Name               |Type               |Description                           |
+===================+===================+======================================+
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
|\ **environment**  |String *(Optional)*|A JSON environment for the stack.     |
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
|\ **tags**         |String *(Optional)*|One or more simple string tags to     |
|                   |                   |associate with the stack. To          |
|                   |                   |associate multiple tags with a stack, |
|                   |                   |separate the tags with commas. For    |
|                   |                   |example, ``tag1,tag2``.               |
+-------------------+-------------------+--------------------------------------+
|\ **parameters**   |Object *(Optional)*|This parameter supplies updated       |
|                   |                   |arguments for parameters defined in   |
|                   |                   |the stack template. The value is a    |
|                   |                   |JSON object, where each key is the    |
|                   |                   |name of a parameter defined in the    |
|                   |                   |template and the associated value is  |
|                   |                   |the argument to use for that          |
|                   |                   |parameter when instantiating the      |
|                   |                   |template. The following code shows    |
|                   |                   |the general structure of this         |
|                   |                   |parameter. In the example, ``a`` and  |
|                   |                   |``b`` are the names of two parameters |
|                   |                   |defined in the template. ``{...       |
|                   |                   |"parameters": { "a": "Value", "b":    |
|                   |                   |"3" }... }`` While the service        |
|                   |                   |accepts JSON numbers for parameters   |
|                   |                   |with the type ``number`` and JSON     |
|                   |                   |objects for parameters with the type  |
|                   |                   |``json``, all parameter values are    |
|                   |                   |converted to their string             |
|                   |                   |representation for storage in the     |
|                   |                   |created Stack. Clients are encouraged |
|                   |                   |to send all parameter values using    |
|                   |                   |their string representation for       |
|                   |                   |consistency between requests and      |
|                   |                   |responses from the Orchestration      |
|                   |                   |service. You must specify a value for |
|                   |                   |each template parameter that does not |
|                   |                   |have a default value. However, this   |
|                   |                   |parameter cannot contain JSON         |
|                   |                   |properties with names that do not     |
|                   |                   |match a parameter that is defined in  |
|                   |                   |the template.                         |
+-------------------+-------------------+--------------------------------------+
|\ **timeout_mins** |String *(Optional)*|The timeout for stack creation in     |
|                   |                   |minutes.                              |
+-------------------+-------------------+--------------------------------------+





**Example Update stack: JSON request**


.. code::

   {
       "template": {
           "heat_template_version": "2013-05-23",
           "description": "Create a simple stack",
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
                       "user_data": "#!/bin/bash -xv\necho \"hello world\" > /root/hello-world.txt\n"
                   }
               }
           }
       },
       "parameters": {
           "flavor": "2 GB General Purpose v1"
       }
   }
   





Response
""""""""""""""""






This operation does not return a response body.




