.. _update-stack-lb:

Updating a stack with a load balancer
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

In this section you update your stack by adding a load balancer
to use with the two servers.

  1. Make a copy of your **servers-with-lb.template** from the previous
     section and name the copy **servers-with-lb-add.template**.

  2. Add the load balancer to your **servers-with-lb-add.template** file
     by adding the highlighted text in the following example.

.. code::

     heat_template_version: 2014-10-16

     description: |
       Heat Orchestration Template that spins up a
       resource group with 2 cloud servers
       and a cloud load balancer.

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

       lb:
         type: Rackspace::Cloud::LoadBalancer
         properties:
           name: LB-Compute load balancer
           nodes:
           - addresses: { get_attr: [web_nodes, accessIPv4]} # This is where the
                                                            # wiring magic happens
             port: 80
             condition: ENABLED
           healthMonitor:
             attemptsBeforeDeactivation: 3
             delay: 10
             timeout: 120
             type: HTTP
             path: "/"
             statusRegex: "."
             bodyRegex: "."
           protocol: HTTP
           port: 80
           virtualIps:
           - type: PUBLIC
             ipVersion: IPV4

     outputs:
       lb_public_ip:
         description: The public IP address of the load balancer
         value: { get_attr: [lb, PublicIp]}

In the `description` section, you added the information that the
template now also creates a load balancer.

For the `lb` resource (in the `resources` section), you added the information
to create the load balancer. The resource type
is `Rackspace::Cloud::LoadBalancer`. The load balancer has the
following properties:

  * It is named `LB-Compute` load balancer.

  * It defines a list of `addresses` for the back-end nodes by calling
    the `get_attr` intrinsic function, passing it the name of the
    resource group (`web_nodes`) and the IP address for each
    server resource (`accessIPv4`), as defined in the resource group.
    These back-end nodes are the servers that you created in
    :ref:`create-stack-resource-group`. Each node uses port 80, and all
    nodes are enabled.

  * The load balancer protocol is HTTP and the service is defined on port 80.

  * One public IPV4 virtual IP address should be added for the load balancer.

.. note::
   To create a ServiceNet address for the load balancer instead of a
   public virtual IP address, use the following value for ``type`` instead:

   .. code::

        - type: SERVICENET

   You will also need to change the outputs as follows:

   .. code::

        outputs:
          lb_servicenet_ip:
            description: The Servicenet IP address of the load balancer
            value: { get_attr: [lb, virtualIps, 0, address ]}

   Since `virtualIps` is an array, you need to request the `address`
   in the first element of the array (array subscript 0) to get
   the Servicenet address.

  * A health monitor is defined with the following attributes set:

      * `attemptsBeforeDeactivation` - Number of attempts made before the node
        is removed from the rotation

      * `delay` - Number of seconds to wait before executing the health
        monitor

      * `timeout` - Number of seconds to wait for a connection to be made
        before timing out

      * `type` - Type of the health monitor

      * `path` - HTTP path used in the monitor request

      * `statusRegex` - Regular expression used to evaluate the HTTP status
        code returned in the response

      * `bodyRegex` - Regular expression used to evaluate the contents of the
        body of the response

The `outputs` section defines a single output `lb_public_ip`, which is the
public IP address for the load balancer. Its value is assigned to the
result of calling the `get_attr` intrinsic function with the name of the
resource (`lb`) and its attribute (`PublicIp`).

Following are two methods to update a stack with a load balancer:

.. _update-stack-heat:

Update a stack with a load balancer by using the heat client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Issue the following command:

.. code::

     heat stack-update Servers-With-LB-Stack --template-file servers-with-lb-add.template

The command returns the information about the stack, including its
status `UPDATE_IN_PROGRESS`:

+--------------------------------------+-----------------------+--------------------+----------------------+
| id                                   | stack_name            | stack_status       | creation_time        |
+--------------------------------------+-----------------------+--------------------+----------------------+
| e7b67698-3929-43af-8e59-9652d00b7250 | Servers-With-LB-Stack | UPDATE_IN_PROGRESS | 2014-01-28T18:00:27Z |
+--------------------------------------+-----------------------+--------------------+----------------------+

Wait a couple of minutes and then issue the following command:

.. code::

     heat stack-show Servers-With-LB-Stack


The command returns the details about the stack, including its
status `UPDATE_COMPLETE`:

.. code::

   +----------------------+------------------------------------------------------------------------------------------------------------------------------+
   | Property             | Value                                                                                                                        |
   +----------------------+------------------------------------------------------------------------------------------------------------------------------+
   | capabilities         | []                                                                                                                           |
   | creation_time        | 2014-01-28T18:00:27Z                                                                                                         |
   | description          | Heat Orchestration Template that spins up a resource                                                                         |
   |                      | group with 2 cloud servers and a Cloud Load                                                                                  |
   |                      | Balancer.                                                                                                                    |
   | disable_rollback     | True                                                                                                                         |
   | id                   | e7b67698-3929-43af-8e59-9652d00b7250                                                                                         |
   | links                | http://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Servers-With-LB-Stack/e7b67698-3929-43af-8e59-9652d00b7250    |
   | notification_topics  | []                                                                                                                           |
   |                      |                                                                                                                              |
   | outputs              | [                                                                                                                            |
   |                      |   {                                                                                                                          |
   |                      |     "output_value": "162.242.141.48",                                                                                        |
   |                      |     "description": "The public IP address of the load balancer",                                                             |
   |                      |     "output_key": "lb_public_ip"                                                                                             |
   |                      |   }                                                                                                                          |
   |                      | ]                                                                                                                            |
   |                      |                                                                                                                              |
   | parameters           | {                                                                                                                            |
   |                      |   "OS::stack_name": "Servers-With-LB-Stack",                                                                                 |
   |                      |   "OS::stack_id": "e7b67698-3929-43af-8e59-9652d00b7250"                                                                     |
   |                      | }                                                                                                                            |
   |                      |                                                                                                                              |
   | stack_name           | Servers-With-LB-Stack                                                                                                        |
   | stack_status         | UPDATE_COMPLETE                                                                                                              |
   | stack_status_reason  | Stack successfully updated                                                                                                   |
   | template_description | Heat Orchestration Template that spins up a resource                                                                         |
   |                      | group with 2 cloud servers and a Cloud Load                                                                                  |
   |                      | Balancer.                                                                                                                    |
   | timeout_mins         | 60                                                                                                                           |
   | updated_time         | 2014-01-28T21:34:47Z                                                                                                         |
   +----------------------+------------------------------------------------------------------------------------------------------------------------------+

The `outputs` property (set in the `outputs` section of the template),
shows that the public IP address of the new load balancer is 162.242.141.48.

.. _update-stack-curl:

Update a stack with a load balancer by using cURL
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Update the stack by executing the following request:

Remember to replace the names in the example preceding with their actual
respective values:

  * **Server-With-LB-Stack** - The name of the stack, if you changed it

  * **stack_id** - The ID of the stack, as returned in your 
    :ref:`create stack<post-create-stack-v1-tenant-id-stacks>`.


**cURL update stack with load balancer: JSON request**

.. code::

     curl -i -X PUT -H  'Accept: application/json' -H  'Content-Type: application/json' -H  "X-Auth-Token: $OS_AUTH_TOKEN" -d \
     '{
       "stack_name": "Servers-With-LB-Stack",
       "disable_rollback": true,
       "parameters": {},
       "template": "heat_template_version: 2014-10-16\n\ndescription: |   \n  Heat Orchestration Template that spins up a\n  resource group with 2 cloud servers\n  and a cloud load balancer.\n\nresources:\n  web_nodes:\n    type: OS::Heat::ResourceGroup\n    properties:\n      count: 2\n      resource_def:\n        type: OS::Nova::Server\n        properties:\n          flavor: 1 GB General Purpose v1\n          image: CentOS 6 (PV)\n          name: LB-Compute Web Nodes  \n\n  lb:\n    type: Rackspace::Cloud::LoadBalancer\n    properties:\n      name: LB-Compute load balancer\n      nodes:\n      - addresses: { get_attr: [web_nodes, accessIPv4]} # This is where the\n                                                       # wiring magic happens\n        port: 80\n        condition: ENABLED\n      healthMonitor:\n        attemptsBeforeDeactivation: 3\n        delay: 10\n        timeout: 120\n        type: HTTP\n        path: \"/\"\n        statusRegex: \".\"\n        bodyRegex: \".\"\n      protocol: HTTP\n      port: 80\n      virtualIps:\n      - type: PUBLIC\n        ipVersion: IPV4\n\noutputs:\n  lb_public_ip:\n    description: The public IP address of the load balancer\n    value: { get_attr: [lb, PublicIp]}  \n\n",
       "timeout_mins": 60
     }' \
     https://ord.orchestration.api.rackspacecloud.com/v1/$OS_TENANT_ID/stacks/Servers-With-LB-Stack/stack_id

The following example shows the response for update stack with load
balancer:

.. code::

     HTTP/1.1 100 Continue

     HTTP/1.1 202 Accepted
     Server: nginx/1.2.1
     Date: Fri, 31 Jan 2014 22:06:57 GMT
     Content-Type: text/plain;charset=UTF-8
     Content-Length: 58
     Connection: keep-alive
     Via: 1.0 Repose (Repose/2.13.0)

     202 Accepted

The request is accepted for processing.

After a few minutes, you can execute the show stack details operation to
ensure that the update completed successfully:

Remember to replace the names in the example with their actual respective
values:

  * **Servers-With-LB-Stack** - If you used a different name for your
    stack, specify it.

  * **stack_id** - The stack ID, as returned in your create stack response.


**cURL show stack details: JSON request**

.. code::

     curl -s \
     -H "X-Auth-Token: $OS_AUTH_TOKEN" \
     -H "Content-Type: application/json" \
     https://ord.orchestration.api.rackspacecloud.com/v1/$OS_TENANT_ID/stacks/Servers-With-LB-Stack/stack_id | python -m json.tool

The following example shows the response:

.. code::

     {
       "stack": {
       "capabilities": [],
       "creation_time": "2014-01-31T22:02:46Z",
       "description": "Heat Orchestration Template that spins up a\nresource group with 2 cloud servers\nand a cloud load balancer.\n",
       "disable_rollback": true,
       "id": "6574e1b1-4c22-49f5-a06d-6d99eb8d87c6",
       "links": [
           {
             "href": "http://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Servers-With-LB-Stack/6574e1b1-4c22-49f5-a06d-6d99eb8d87c6",
             "rel": "self"
           }
       ],
       "notification_topics": [],
       "outputs": [
           {
             "description": "The public IP address of the load balancer",
             "output_key": "lb_public_ip",
             "output_value": "184.106.100.140"
           }
       ],
       "parameters": {
       "OS::stack_name": "Servers-With-LB-Stack",
       "OS::stack_id": "6574e1b1-4c22-49f5-a06d-6d99eb8d87c6"
           },
       "stack_name": "Servers-With-LB-Stack",
       "stack_status": "UPDATE_COMPLETE",
       "stack_status_reason": "Stack successfully updated",
       "template_description": "Heat Orchestration Template that spins up a\nresource group with 2 cloud servers\nand a cloud load balancer.\n",
       "timeout_mins": 60,
       "updated_time": "2014-01-31T22:08:01Z"
           }
     }
