.. _common-dg-status:

=================
HTTP status codes
=================

When you send an API request to a Rackspace Cloud service, the service returns
an object containing an HTTP status code that denotes the status of the API
request. The response body returns additional information about the status.

HTTP status codes come in different classes. Classes are determined by the
first digit of the status code:

 - :ref:`2xx <common-dg-status-two>` (Success)
 - :ref:`4xx <common-dg-status-four>` (Client error)
 - :ref:`5xx <common-dg-status-five>` (Server error)

.. note::

   - HTTP status codes are not standard across all Rackspace Cloud services.
     The same code could have multiple status types. Read the response body
     carefully to accurately determine the nature of the request status.

   - For a more comprehensive list of HTTP status codes, refer to
     `RFC-7231`_.

.. _RFC-7231: http://www.iana.org/assignments/http-status-codes/http-status-codes.xhtml

.. _common-dg-status-body:

Response body
~~~~~~~~~~~~~

The response body of HTTP status codes varies by service and type. Responses
can contain some or all of these elements:

- ``title``

- ``type``

- ``code``

- ``message``

- ``details``

.. note::
   Elements such as ``type``, ``message``, and ``details`` only
   appear with 4xx (Client error)
   and 5xx (Server Error) status codes.

**Example: Error message syntax**

.. code::

   { "error": {
    "type": "failure type",
    "code": HTTP status code,
    "message": "detailed message",
    "details": "any specific details about the error"
    }
   }

.. _common-dg-status-two:

2xx (Success) status codes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The 2xx class status code confirms that a request has succeeded.

The following table lists possible 2xx status codes with their associated
descriptions:

  **Table: 2xx status codes**

  +-------------+----------------------------+---------------------------------+
  | Status code | Response                   | Description                     |
  +=============+============================+=================================+
  | 200         | ``OK``                     | The request has succeeded.      |
  |             |                            | (Some API calls might return    |
  |             |                            | 201 instead.)                   |
  +-------------+----------------------------+---------------------------------+
  | 201         | ``Created``                | The request has been fulfilled  |
  |             |                            | and a new resource was created. |
  +-------------+----------------------------+---------------------------------+
  | 202         | ``Accepted``               | The request has been accepted   |
  |             |                            | for processing.                 |
  +-------------+----------------------------+---------------------------------+
  | 204         | ``No Content``             | No additional content sent to   |
  |             |                            | response body despite the       |
  |             |                            | request being filled.           |
  +-------------+----------------------------+---------------------------------+

.. _common-dg-status-two-example:

The following examples show basic ``200 OK`` request. Since the request succeeded,
no ``type``, ``message``, or ``details`` elements are contained in the response
body:

**Example: basic success response, JSON**

.. code::

    Status: 200 OK
    Date: Thu, 28 Jul 2015 21:54:21 GMT
    X-API-VERSION: 1.0.17
    Content-Type: application/json
    Content-Length: 190

    {
      "status" : "COMPLETED",
      "jobId" : "3593a5e9-83af-4eb8-ae1a-25f07b747d80",
      "callbackUrl" : "https://dns.api.rackspacecloud.com/v1.0/1234/status/3593a5e9-83af-4eb8-ae1a-25f07b747d80"
    }

.. _common-dg-status-four:

4xx (Client error) status codes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The 4xx class status code indicates that a request contains errors or cannot
be fulfilled.

The following table lists possible 4xx status codes with their associated
descriptions:

  **Table: 4xx status codes**

  +-------------+-----------------------------+--------------------------------+
  | Status code | Response                    | Description                    |
  +=============+=============================+================================+
  | 400         | ``badRequest``              | Invalid parameter values,      |
  |             |                             | un-parsable data, or missing   |
  |             |                             | required values in the user    |
  |             |                             | request.                       |
  +-------------+-----------------------------+--------------------------------+
  | 401         | ``unauthorized``            | The supplied token is not      |
  |             |                             | authorized to access the       |
  |             |                             | resources, either it's         |
  |             |                             | expired or invalid.            |
  +-------------+-----------------------------+--------------------------------+
  | 403         | ``forbidden``               | Access to the requested        |
  |             |                             | resource was denied.           |
  +-------------+-----------------------------+--------------------------------+
  | 404         | ``Not Found``               | The back-end services did not  |
  |             |                             | find anything matching the     |
  |             |                             | request-URI.                   |
  +-------------+-----------------------------+--------------------------------+
  | 405         | ``badMethod``               | The requested method is not    |
  |             |                             | allowed for this resource.     |
  +-------------+-----------------------------+--------------------------------+
  | 409         | ``Conflict``                | Invalid action is requested for|
  |             |                             | the current stack status; more |
  |             |                             | than one object exists for the |
  |             |                             | specified non-unique           |
  |             |                             | identifier.                    |
  +-------------+-----------------------------+--------------------------------+
  | 413         | ``requestEntityTooLarge``   | When more than the allowed     |
  |             |                             | number of resources is         |
  |             |                             | specified for a given stack or |
  |             |                             | the supplied template exceeds  |
  |             |                             | the size limit. Also returned  |
  |             |                             | when the number of requests    |
  |             |                             | per time slice exceeds the     |
  |             |                             | limit.                         |
  +-------------+-----------------------------+--------------------------------+
  | 415         | ``badMediaType``            | The requested content type is  |
  |             |                             | not supported by this service  |
  +-------------+-----------------------------+--------------------------------+
  | 422         |``unprocessableEntity``      | The requested resource could   |
  |             |                             | not be processed on at the     |
  |             |                             | moment.                        |
  +-------------+-----------------------------+--------------------------------+

.. _common-dg-status-four-example:

The following ``badRequest`` examples show errors when the volume size of a request
is invalid.

**Example: badRequest fault on volume size errors, JSON**

.. code::

    HTTP/1.1 400 None
    Content-Length: 120
    Content-Type: application/json; charset=UTF-8
    Date: Tue, 29 Nov 2011 00:33:48 GMT

.. code::

    {
       "badRequest":{
          "code":400,
          "message":"Volume 'size' needs to be a positive integer value, -1.0 cannot be accepted."
       }
    }

.. _common-dg-status-five:

5xx (Server error) status codes
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The 5xx status code indicates that a request cannot be fulfilled because the
server has encountered an error.

The following table lists possible 5xx status codes with their associated
descriptions:

  **Table: 5xx status codes**

  +-------------+------------------------+-------------------------------------+
  | Status code | Response               | Description                         |
  +-------------+------------------------+-------------------------------------+
  | 500         | ``instanceFault``      | This is a generic server error and  |
  |             |                        | the message contains the reason     |
  |             |                        | for this error. This error could    |
  |             |                        | error could wrap several error      |
  |             |                        | messages and is a catch all.        |
  +-------------+------------------------+-------------------------------------+
  | 501         | ``notImplemented``     | The requested method or resource    |
  |             |                        | is not implemented.                 |
  +-------------+------------------------+-------------------------------------+
  | 503         | ``serviceUnavailable`` | The request has been accepted       |
  |             |                        | for processing.                     |
  +-------------+------------------------+-------------------------------------+

.. _common-dg-status-five-example:

The following ``instanceFault`` examples show the response header and body
information returned when the server cannot perform the requested operation
due to an error.

.. code::

    <?xml version="1.0" encoding="UTF-8"?>
    <instanceFault code="500"
        xmlns="http://docs.rackspace.com/cbs/api/v1.0">
        <message> The server has either erred or is incapable of
            performing the requested operation. </message>
    </instanceFault>


**Example: instanceFault response, JSON**

.. code::

    HTTP/1.1 500 Internal Server Error
    Content-Length: 120
    Content-Type: application/json; charset=UTF-8
    Date: Tue, 29 Jun 2015 00:33:48 GMT

.. code::

    {
       "instance_fault":{
          "code":500,
          "message":"The server has either erred or is incapable of performing the requested operation."
       }
    }
