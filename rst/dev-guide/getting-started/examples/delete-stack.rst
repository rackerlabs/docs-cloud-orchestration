.. _delete-stack:

Delete a stack
~~~~~~~~~~~~~~
Since you are done using the stack, you can delete it.

Following are two methods to delete a stack:

.. _delete-stack-heat:

Delete a stack by using the heat client
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Delete your stack `Single-Server-Stack` by issuing the following
command:

.. code::

     heat stack-delete Single-Server-Stack

The command returns the following information for the stack:

+--------------------------------------+---------------------+--------------------+----------------------+
| id                                   | stack_name          | stack_status       | creation_time        |
+--------------------------------------+---------------------+--------------------+----------------------+
| bd2c230-b02a-45d8-9f16-88c9a9f64d2d  | Single-Server-Stack | DELETE_IN_PROGRESS | 2014-01-23T19:41:05Z |
+--------------------------------------+---------------------+--------------------+----------------------+

The stack_status value shows that the stack is in the process of being
deleted. After a minute or so, you can execute the list stacks operation
(:ref:`list-stacks`) and observe that the `Single-Server`Stack` is not
listed.

.. _delete-stack-curl:

Delete a stack by using cURL
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Delete your `Single-Server-Stack` by executing the following request.

This operation does not require a request body. This operation does not
return a response body.

**cURL delete stack: JSON request***

.. code::

     curl  -i -X DELETE \
     -H "X-Auth-Token: $OS_AUTH_TOKEN" \
     -H "Content-Type: application/json" \
     https://ord.orchestration.api.rackspacecloud.com/v1/$OS_TENANT_ID/stacks/Single-Server-Stack/stack_id

Remember to replace the following example values with their actual
respective values:

  * **Single-Server-Stack** - If you used a different name for a stack,
    specify it.

  * **stack_id** - Specify the ID returned in your create stack response.

The following example shows the response:

**Delete stack: JSON response**

.. code::

     HTTP/1.1 204 No Content
     Server: nginx/1.2.1
     Date: Fri, 31 Jan 2014 16:36:24 GMT
     Content-Type: text/html;charset=UTF-8
     Content-Length: 0
     Connection: keep-alive
     Via: 1.0 Repose (Repose/2.13.0)

After a minute or so, you can execute the list stacks operation
(:ref:`list-stacks`) and observe that the `Single-Server-Stack` is not
listed.
