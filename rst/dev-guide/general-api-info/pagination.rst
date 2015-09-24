==========
Pagination
==========

Pagination provides the ability to limit the size of the returned data
in the response body as well as retrieve a specified subset of a large
data set. Pagination has two key concepts: *limit* and *marker*.

*  Limit is the restriction on the maximum number of items for that type
   that can be returned.

*  Marker is the ID of the last item in the previous list returned.

   The ID is the UUID in the case of stacks. For example, a query could
   request the next 10 stacks after the stack "1234" as follows:
   ``?limit=10&marker=1234``. Items are displayed sorted by ID.

If the content returned by a call is paginated, the response includes a
structured link with the basic structure
``{"href": "<url>", "rel": "next"}``. Any response
that is truncated by pagination will have a *next* link, which points to
the next item in the collection. If there are no more items, no *next*
link is returned.

Pagination applies only to GET /stacks which lists the information for all
stacks.

See the example for a paged List Stacks call that follows.

**Example: List Stacks Paged Request: JSON**

.. code::

    GET /v1/622dd71147164a92bf3915f5cbdfe261/stacks?limit=2 HTTP/1.1
    Accept: application/json
    Accept-Encoding: gzip, deflate, compress
    Host: 10.0.2.15:8004
    User-Agent: HTTPie/0.7.2
    X-Auth-Token: 286dbf02498f457399ee9b3db95ce65d



Notice that the paged request example above sets the limit to 2
(``?limit=2``), so the response that follows shows 2 stacks and returns
a *marker* set to the UUID of the last stack in the returned list
(``?marker=5d0daddb-2a24-475b-853d-4ab4e1522c63``). Also a link is
provided to retrieve the next 2 results (``limit=2``) in the link
element identified by the attribute ``"rel":"next"``:

**Example: List Stacks Paged Response: JSON**

.. code::

    HTTP/1.1 200 OK
    Content-Length: 1679
    Content-Type: application/json; charset=UTF-8
    Date: Thu, 16 Jan 2014 17:36:53 GMT

    {
        "links": [
            {
                "href": "http://10.0.2.15:8004/v1/622dd71147164a92bf3915f5cbdfe261/stacks?limit=2&marker=5d0daddb-2a24-475b-853d-4ab4e1522c63",
                "rel": "next"
            }
        ],
        "stacks": [
            {
                "creation_time": "2014-01-16T17:15:47Z",
                "description": "A simple stack that provides a single-instance Wordpress blog server",
                "id": "a240abd6-43c7-4479-9730-ea0bcd97fd9a",
                "links": [
                    {
                        "href": "http://10.0.2.15:8004/v1/622dd71147164a92bf3915f5cbdfe261/stacks/stack04/a240abd6-43c7-4479-9730-ea0bcd97fd9a",
                        "rel": "self"
                    }
                ],
                "stack_name": "stack04",
                "stack_status": "CREATE_COMPLETE",
                "stack_status_reason": "Create complete",
                "updated_time": "2014-01-16T17:15:48Z"
            },
            {
                "creation_time": "2014-01-16T17:15:31Z",
                "description": "A simple stack that provides a single-instance Wordpress blog server",
                "id": "5d0daddb-2a24-475b-853d-4ab4e1522c63",
                "links": [
                    {
                        "href": "http://10.0.2.15:8004/v1/622dd71147164a92bf3915f5cbdfe261/stacks/stack03/5d0daddb-2a24-475b-853d-4ab4e1522c63",
                        "rel": "self"
                    }
                ],
                "stack_name": "stack03",
                "stack_status": "CREATE_IN_PROGRESS",
                "stack_status_reason": "",
                "updated_time": "2014-01-16T17:15:32Z"
            }
        ]
    }

