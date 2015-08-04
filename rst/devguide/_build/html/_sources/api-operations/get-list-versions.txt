
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Versions -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

List Versions
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-versions.html#request>`__
`Response <get-list-versions.html#response>`__

.. code::

    GET /

Lists all Orchestration API versions.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^









Response
^^^^^^^^^^^^^^^^^^





**Example List Versions: JSON response**


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

