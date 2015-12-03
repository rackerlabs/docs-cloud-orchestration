
.. _service-access-endpoints:

Service Access/Endpoints
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Orchestration service is a regionalized service. 

.. tip

  To help you decide which regionalized endpoint to use, read about special
  considerations for choosing a region at http://www.rackspace.com/
  knowledge_center/article/about-regions.

Use one of the following service access/endpoint to access the Rackspace Cloud Orchestration service: 

+-------------------------+-----------------------------------------------------------+
| Region                  | Endpoint                                                  |
+=========================+===========================================================+
| Chicago (ORD)           | https://ord.orchestration.api.rackspacecloud.com/v1/1234/ |
+-------------------------+-----------------------------------------------------------+
| Dallas/Ft. Worth (DFW)  | https://dfw.orchestration.api.rackspacecloud.com/v1/1234/ |
+-------------------------+-----------------------------------------------------------+
| Northern Virginia (IAD) | https://iad.orchestration.api.rackspacecloud.com/v1/1234/ |
+-------------------------+-----------------------------------------------------------+
| London (LON)            | https://lon.orchestration.api.rackspacecloud.com/v1/1234/ |
+-------------------------+-----------------------------------------------------------+
| Sydney (SYD)            | https://syd.orchestration.api.rackspacecloud.com/v1/1234/ |
+-------------------------+-----------------------------------------------------------+
| Hong Kong (HKG)         | https://hkg.orchestration.api.rackspacecloud.com/v1/1234/ |
+-------------------------+-----------------------------------------------------------+

..  note:: 

    The service catalog returned in the auth response specifies the correct
    service access endpoint for your account to use for accessing Orchestration. Use
    the service name (cloudOrchestration) to locate the correct endpoint in the
    service catalog. For an example of the service catalog, see the
    :ref:`authentication response example<review-auth-resp>`.

Replace the sample account ID number, ``1234``, with your Rackspace Cloud account number.

You can find the account number after the final '/' in the
``publicURL`` field found in the Service catalog returned in the authentication response. For an 
example of the service catalog, see the authentication response example.  
