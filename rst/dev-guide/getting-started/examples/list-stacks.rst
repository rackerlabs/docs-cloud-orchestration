.. _list-stacks:

List stacks
~~~~~~~~~~~
Now you can list stacks and confirm that your stack was created.

Following are two methods to list stacks:

.. _list-stacks-heat:

List stacks by using the heat client
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Issue the following command:

.. code::

     heat stack-list

The command returns the `id`, `stack_name`, `stack_status`, and
`creation_time` for each of your stacks, as shown in the following example:

+--------------------------------------+---------------------+-----------------+----------------------+
| id                                   | stack_name          | stack_status    | creation_time        |
+--------------------------------------+---------------------+-----------------+----------------------+
| bd2c230-b02a-45d8-9f16-88c9a9f64d2d  | Single-Server-Stack | CREATE_COMPLETE | 2014-01-23T19:41:05Z |
+--------------------------------------+---------------------+-----------------+----------------------+

In this case, you have just the `Single-Server-Stack` and its
`stack_status` is `CREATE_COMPLETE`.

.. note::
   If you issue the stack-list command before the operation of creating
   the stack is complete, you might see the `stack_status` value
   of `CREATE_IN_PROGRESS.` If you wait a minute, and then
   reissue the command, you should see that the stack has been created.

.. _list-stacks-curl:

List stacks by using cURL
~~~~~~~~~~~~~~~~~~~~~~~~~

Execute the cURL request for list stacks:

.. code::

     curl -s \
     -H "X-Auth-Token: $OS_AUTH_TOKEN" \
     -H "Content-Type: application/json" \
     https://ord.orchestration.api.rackspacecloud.com/v1/$OS_TENANT_ID/stacks | python -m json.tool

The following example shows the response:

.. code::

     {
       "stacks": [
         {
           "description": "No description",
           "links": [
             {
               "href": "https://ord.orchestration.api.rackspacecloud.com/v1/1234/stacks/Single-Server-Stack/bd2c230-b02a-45d8-9f16-88c9a9f64d2d",
               "rel": "self"
             }
           ],
           "stack_status_reason": "Stack CREATE completed successfully",
           "stack_name": "Single-Server-Stack",
           "creation_time": "2014-01-23T19:41:05Z",
           "updated_time": null,
           "stack_status": "CREATE_COMPLETE",
           "id": "bd2c230-b02a-45d8-9f16-88c9a9f64d2d"
         }
       ]
     }

You can see that your stack named `Single-Server-Stack` with the
id `bd2c230-b02a-45d8-9f16-88c9a9f64d2d` was successfully created.

.. note::
   If you issue the stack-list command before the operation of creating
   the stack is complete, you might see the `stack_status` value
   of `CREATE_IN_PROGRESS.`` If you wait a minute, and then
   reissue the command, you should see that the stack has been created.
