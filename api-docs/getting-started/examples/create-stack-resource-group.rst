.. _create-stack-resource-group:

Create a stack by using a resource group
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Assume that you would like to create a cloud load balancer to use with
some cloud servers. You begin working on this task by creating a resource
group to hold the servers. The advantage of this technique is that you
can create the entire set of servers by creating one resource group,
rather than specifying each server resource separately.

First, use your text editor to create the following template and save
it in a file named **servers-with-lb.template**:

.. code::

     heat_template_version: 2014-10-16

     description: |
       Heat Orchestration Template that spins up a
       resource group with 2 cloud servers.

     resources:
       web_nodes:
         type: OS::Heat::ResourceGroup
         properties:
           count: 2
           resource_def:
             type: OS::Nova::Server
             properties:
               flavor: 1 GB General Purpose v1
               image: CentOS 6 (PV)
               name: LB-Compute Web Nodes

In the preceding example, a description is provided for the template. It
is good practice to always provide a brief description for what a
template does in order to inform potential future users about the template.

The `resources` section contains a resource group named `web_nodes`
of type `OS::Heat::ResourceGroup`. In the `properties` section for the
group, the attribute `count` is set to `2`, which means that two
resources of the type `OS::Nova::Server` (as defined in the resource
definition `resource_def`) will be created in the group.
The `properties` section for the resource definition for each resource
in the group specifies the following values:

  * `1 GB General Purpose v1` flvor
  * `CentOS 6 (PV)` image
  * the name `LB-Compute Web Nodes`

.. note::
   The advantage of using a resource group to define your servers is the
   fact that you can set the desired number of servers to create by
   simply setting the value of `count` in the template. For example, to
   create three Cloud Servers instead of two, you could modify the
   value of count as follows:

   .. code::

        count: 3

Following are two methods to create a stack by using a resource group:

.. _create-stack-rg-heat:

Create a stack by using a resource group with the heat client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Issue the following command, which includes the name of the template
file that you just created:

.. code::

     heat stack-create Servers-With-LB-Stack --template-file servers-with-lb.template

The command returns the information about the stack, including its
status `CREATE_IN_PROGRESS`:

+--------------------------------------+-----------------------+--------------------+----------------------+
| id                                   | stack_name            | stack_status       | creation_time        |
+--------------------------------------+-----------------------+--------------------+----------------------+
| e7b67698-3929-43af-8e59-9652d00b7250 | Servers-With-LB-Stack | CREATE_IN_PROGRESS | 2014-01-28T18:00:27Z |
+--------------------------------------+-----------------------+--------------------+----------------------+

After a couple of minutes, you can issue the list stacks (:ref:`list-stacks`)
to confirm that your stack is now created:

+--------------------------------------+-----------------------+-----------------+----------------------+
| id                                   | stack_name            | stack_status    | creation_time        |
+--------------------------------------+-----------------------+-----------------+----------------------+
| e7b67698-3929-43af-8e59-9652d00b7250 | Servers-With-LB-Stack | CREATE_COMPLETE | 2014-01-28T18:00:27Z |
+--------------------------------------+-----------------------+-----------------+----------------------+

.. _create-stack-rg-curl:

Create a stack by using a resource group with cURL
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Issue the following command:

.. code::

     curl -i -X POST -H 'Accept: application/json' -H 'Content-Type: application/json' -H "X-Auth-Token: $OS_AUTH_TOKEN" -d \
     '{
       "stack_name": "Servers-With-LB-Stack",
       "disable_rollback": true,
       "parameters": {},
       "template": "heat_template_version: 2014-10-16\n\ndescription: |   \n  Heat Orchestration Template that spins up a\n  resource group with 2 cloud servers.\n\nresources:\n  web_nodes:\n    type: OS::Heat::ResourceGroup\n    properties:\n      count: 2\n      resource_def:\n        type: OS::Nova::Server\n        properties:\n          flavor: 1 GB General Purpose v1\n          image: CentOS 6 (PV)\n          name: LB-Compute Web Nodes  \n\n\n",
       "timeout_mins": 60
       }' \
       https://ord.orchestration.api.rackspacecloud.com/v1/$OS_TENANT_ID/stacks

The following example shows the response:

.. code::

     HTTP/1.1 201 Created
     Server: nginx/1.2.1
     Date: Fri, 31 Jan 2014 17:09:37 GMT
     Content-Type: application/json
     Content-Length: 192
     Location: https://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Servers-With-LB-Stack/e7b67698-3929-43af-8e59-9652d00b7250
     Connection: keep-alive
     Via: 1.0 Repose (Repose/2.13.0)

     {"stack": {"id": "e7b67698-3929-43af-8e59-9652d00b7250", "links": [{"href": "http://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Servers-With-LB-Stack/e7b67698-3929-43af-8e59-9652d00b7250", "rel": "self"}]}}

The stack `Servers-With-LB-Stack` was successfully created and has
the id `e7b67698-3929-43af-8e59-9652d00b7250`.
