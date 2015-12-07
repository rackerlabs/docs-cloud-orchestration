.. _show-stack-details:

Showing stack details
~~~~~~~~~~~~~~~~~~~~~~~

In this section, you show the details for your stack.

Following are two methods to show stack details:

.. _show-stack-heat:

Show stack details by using the heat client
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Show the details for your stack `Single-Server-Stack` by issuing the
following command:

.. code::

     heat stack-show Single-Server-Stack

The command returns the details for the stack:


.. code::

   +----------------------+----------------------------------------------------------------------------------------------------------------------------+
   | capabilities         | []                                                                                                                         |
   | creation_time        | 2014-01-24T20:12:47Z                                                                                                       |
   | description          | No description                                                                                                             |
   | disable_rollback     | True                                                                                                                       |
   | id                   | 3bd2c230-b02a-45d8-9f16-88c9a9f64d2d                                                                                       |
   | links                | http://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Single-Server-Stack/3bd2c230-b02a-45d8-9f16-88c9a9f64d2d    |
   | notification_topics  | []                                                                                                                         |
   |                      |                                                                                                                            |
   | outputs              | [                                                                                                                          |
   |                      |   {                                                                                                                        |
   |                      |     "output_value": "23.253.88.131",                                                                                       |
   |                      |     "description": "public IP address of the deployed compute instance",                                                   |
   |                      |     "output_key": "public_ip"                                                                                              |
   |                      |   }                                                                                                                        |
   |                      | ]                                                                                                                          |
   |                      |                                                                                                                            |
   | parameters           | {                                                                                                                          |
   |                      |   "OS::stack_name": "Single-Server-Stack",                                                                                 |
   |                      |   "OS::stack_id": "3bd2c230-b02a-45d8-9f16-88c9a9f64d2d"                                                                   |
   |                      | }                                                                                                                          |
   |                      |                                                                                                                            |
   | stack_name           | Single-Server-Stack                                                                                                        |
   | stack_status         | CREATE_COMPLETE                                                                                                            |
   | stack_status_reason  | Stack CREATE completed successfully                                                                                        |
   | template_description | No description                                                                                                             |
   | timeout_mins         | 60                                                                                                                         |
   | updated_time         | None                                                                                                                       |
   +----------------------+----------------------------------------------------------------------------------------------------------------------------+



Notice this is where you can see the information created by the output
parameter that you created in the following section of your template
file in :ref:`create-simple-stack`.

**Outputs section for template single_server.template**

.. code::

      outputs:
        public_ip:
          description: public IP address of the deployed compute instance
          value: { get_attr: [compute_instance, accessIPv4] }

Locate the ``outputs`` property in the table of information returned
by the ``stack-show`` heat client command and look at the ``output value`` for
the ``output_key public_ip``. The ``output_value`` in the preceding
example is ``23.253.88.131``. That value is the public IP address for
the server that was created by the stack ``Single-Server-Stack``. If
the output parameter ``public_ip`` had not been provided in the
template, there would be no easy way to access the new server
(other than by using the Cloud Control Panel). Using output
parameters provides a method for returning important
information to API users.

.. _show-stack-curl:

Show stack details by using cURL
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^

Show stack details by executing the following request. This operation does
not require a request body.

**cURL show stack details: JSON request**

.. code::

      curl -s \
      -H "X-Auth-Token: $OS_AUTH_TOKEN" \
      -H "Content-Type: application/json" \
      https://ord.orchestration.api.rackspacecloud.com/v1/$OS_TENANT_ID/stacks/Single-Server-Stack/stack_id | python -m json.tool

Remember to replace the following example values with their actual values:

  * **Single-Server-Stack** - If you used a different name for your stack,
    specify it.

  * **stack_id** - Specify the ID returned in your create stack response.

The following example shows the response:

**Show stack details: JSON response**

.. code::

     {
        "stack": {
        "disable_rollback": true,
        "description": "No description",
        "parameters": {
        "OS::stack_name": "Single-Server-Stack",
        "OS::stack_id": "3bd2c230-b02a-45d8-9f16-88c9a9f64d2d"
          },
          "stack_status_reason": "Stack CREATE completed successfully",
          "stack_name": "Single-Server-Stack",
          "outputs": [
            {
              "output_value": "23.253.88.131",
              "description": "public IP address of the deployed compute instance",
              "output_key": "public_ip"
            }
          ],
          "creation_time": "2014-01-24T20:12:47Z",
          "links": [
            {
              "href": "http://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Single-Server-Stack/3bd2c230-b02a-45d8-9f16-88c9a9f64d2d",
              "rel": "self"
            }
          ],
          "capabilities": [

          ],
          "notification_topics": [

          ],
          "timeout_mins": 60,
          "stack_status": "CREATE_COMPLETE",
          "updated_time": null,
          "id": "3bd2c230-b02a-45d8-9f16-88c9a9f64d2d",
          "template_description": "No description"
        }
      }

The response shows the information created by the output parameter that
you created in the `outputs` section of your template file in
:ref:`create-simple-stack`.

**outputs section for template single_server.template**

.. code::

      outputs:
        public_ip:
          description: public IP address of the deployed compute instance
          value: { get_attr: [compute_instance, accessIPv4] }

Locate the ``outputs`` property in the response information and look at
the output value for the ``output_key public_ip``. The ``output_value`` in
the preceding example is ``23.253.88.131``. That value is the public
IP address for the server that was created by the
stack `Single-Server-Stack`. If the output parameter ``public_ip`` had
not been provided in the template, there would be no easy way to
access the new server (other than by using the Cloud Control Panel).
Using output parameters provides a method for returning
important information to API users.
