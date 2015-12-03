.. _create-simple-stack:

Create a simple stack for a cloud server
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Assume that you want to create a simple stack that defines a single
cloud server. Use a text editor such as nano or vi to create the
following heat orchestration template (HOT) file and then save
it as **single_server.template**:

.. code::

     heat_template_version: 2014-10-16

     resources:
       compute_instance:
         type: "OS::Nova::Server"
         properties:
           flavor: 1 GB General Purpose v1
           image: CentOS 6 (PV)
           name: Single Server Stack

     outputs:
       public_ip:
         description: public IP address of the deployed compute instance
         value: { get_attr: [compute_instance, accessIPv4] }

.. note::
   * If you enter in the template example text manually, remember
     to use a two-space indent (not Tab) for each subsection of the template.


This template has a resources section that creates a single cloud server
with a 1 GB General Purpose v1 flavor size (which identifies a
particular combination of memory capacity and priority for CPU time).
It has CentOS 6 installed, and is called Single Server Stack.

.. note::
   * You can find the information for resources types either by looking it
     up or by using the API.

   * You can look up the names for the supported attributes in the 
     Supported resources reference`_ .

   * To find the various types of supported template resources, use the
     list resource types API operation (GET /resoure_types). The cURL
     command for this operation is as follows. Be sure to use the correct
     values for your `X-Auth-Token` and `tenant_id`:

     .. code::

          curl -i -X GET -H 'X-Auth-Token: xxxxxx' \
          -H 'Content-Type: application/json' \
          -H 'Accept: application/json'  https://dfw.orchestration.rackspacecloud.com/v1/<tenant_id>/resource_types

This template also has an ``outputs`` section. Outputs are used to provide
important information to users, such as the IP address for the
server in this example. The output in this example is named `public_ip`.
Its value is set by calling the intrinsic function `get_attr`, and
passing it the name of the cloud server resource (`compute_instance`) and
the attribute whose value is needed (`accessIPv4`). You will see shortly how
this public IP address is displayed to the user. You can find out more
about intrinsic functions in the `Supported resources reference`_ . 


.. _Supported resources reference: http://orchestration.rackspace.com/raxdox/index.html

Following are two methods to create the stack:

.. _create-stack-heat:

Create a stack with the heat client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Issue the following command, which includes the name of the template
file that you just created:

.. code::

     heat stack-create Single-Server-Stack --template-file single_server.template

You should get a list of your stacks, including one with a stack_name of
`Single-Server-Stack` with a stack_status of `CREATE_IN_PROGRESS`.
For example:

+--------------------------------------+---------------------+--------------------+----------------------+
| id                                   | stack_name          | stack_status       | creation_time        |
+--------------------------------------+---------------------+--------------------+----------------------+
| 3bd2c230-b02a-45d8-9f16-88c9a9f64d2d | Single-Server-Stack | CREATE_IN_PROGRESS | 2014-01-24T20:12:47Z |
+--------------------------------------+---------------------+--------------------+----------------------+

.. _create-stack-curl:

Create a stack by using cURL
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Use the create stack API operation (`/stacks`) in the cURL request, as
shown in the following example:

.. code::

     curl -i -X POST \
     -H 'Accept: application/json' \
     -H 'Content-Type: application/json'  \
     -H  "X-Auth-Token: $OS_AUTH_TOKEN" -d \
        '{
           "stack_name": "Single-Server-Stack",
           "disable_rollback": true,
           "parameters": {},
           "template": "heat_template_version: 2014-10-16\n \nresources:\n  compute_instance:  \n    type: \"OS::Nova::Server\"\n    properties:\n      flavor: 1 GB General Purpose v1\n      image: CentOS 6 (PV)\n      name: Single Server Stack\n       \noutputs:\n  public_ip:\n    description: public IP address of the deployed compute instance\n    value: { get_attr: [compute_instance, accessIPv4] }      \n\n\n",
           "timeout_mins": 60
         }' \
         https://ord.orchestration.api.rackspacecloud.com/v1/$OS_TENANT_ID/stacks

We recommend that you produce the value for the template attribute by
executing the following heat client command:

.. code::

     $ heat --debug stack-create Single-Server-Stack --template-file single_server.template

Copy the value for the template attribute from the cURL command that
is shown in the output from the preceding command.

Although you can manually produce the required value for the template
attribute from the template file, to do so you must replace every
line break with **\n**, escape any double quotation marks
(for example `type: \"OS::Nova::Server\"`), and maintain correct spacing
to indicate the correct nesting level for each block in the template.
So it is easier to use the `template value` in the generated cURL command
from the `--debug` output.

Note that executing the stack-create heat client command actually
creates the stack, so you  must delete that stack before you issue
the cURL command to create a stack.

As an alternative, you can also just use the entire cURL command
generated by the `--debug` output rather than the cURL command
shown in the previous example.

The following example shows the response:

.. code::

     HTTP/1.1 201 Created
     content-length: 192
     via: 1.0 Repose (Repose/2.13.0)
     server: nginx/1.2.1
     connection: keep-alive
     location: https://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Single-Server-Stack/3bd2c230-b02a-45d8-9f16-88c9a9f64d2d
     date: Thu, 23 Jan 2014 19:38:09 GMT
     content-type: application/json

     {
        "stack": {
         "id": "3bd2c230-b02a-45d8-9f16-88c9a9f64d2d",
         "links": [
           {
             "href": "http://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Single-Server-Stack/3bd2c230-b02a-45d8-9f16-88c9a9f64d2d",
             "rel": "self"
           }
         ]
       }
      }

The example shows that the stack was created and has the
ID `3bd2c230-b02a-45d8-9f16-88c9a9f64d2d`.

Notice that there is a self link that contains a versioned link to
the stack resource. Use this link in cases where the link will be
followed immediately.
