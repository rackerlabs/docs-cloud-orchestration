======
Faults
======

The Cloud Orchestration Service returns the following error codes:

400 Bad Request
  Invalid parameter values, un-parsable data, or missing required values.

404 Not Found
  The stack or resource cannot be found.

409 Conflict
  Invalid action is requested for the current stack status; more than one
  object exists for the specified non-unique identifier.

413 Request Entity Too Large
  When more than the allowed number of resources is specified for a given
  stack or the supplied template exceeds the size limit. Also returned
  when the number of requests per time slice exceeds the limit.

500 Internal Server Error
  Reverting the previously failed action encountered an error, an
  operation failed on one or more resources, an unexpected error occurred.

.. todo: Need new orchestration examples to replace the fault response examples below.

.. The following two ``instanceFault`` examples show errors when the server has erred or cannot perform the requested operation:

.. The error code (``code``) is returned in the body of the response for convenience. The ``message`` element returns a human-readable message that is appropriate for display to the end user. The ``details`` element is optional and may contain information that is useful for tracking down an error, such as a stack trace. The ``details`` element may or may not be appropriate for display to an end user, depending on the role and experience of the end user.

.. The fault's root element (for example, ``instanceFault``) may change depending on the type of error.

.. The following two ``badRequest`` examples show errors when the volume size is invalid:

.. The next two examples show ``itemNotFound`` errors:

