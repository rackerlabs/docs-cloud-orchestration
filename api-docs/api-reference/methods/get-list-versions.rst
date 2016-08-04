
.. _get-list-versions:

List versions
~~~~~~~~~~~~~

.. code::

    GET /

Lists all Orchestration API versions.

This table shows the possible response codes for this operation:

+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |Success                  |Request succeeded.       |
+--------------------------+-------------------------+-------------------------+


Request
-------

This operation does not accept a request body.




Response
--------

**Example List versions: JSON response**


.. code::

   {
       "versions": [
           {
               "status": "CURRENT",
               "id": "v1.0",
               "links": [
                   {
                       "href": "http://23.253.228.211:8000/v1/",
                       "rel": "self"
                   }
               ]
           }
       ]
   }
