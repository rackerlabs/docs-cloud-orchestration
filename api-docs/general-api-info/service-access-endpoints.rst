
.. _service-access-endpoints:

Service Access/Endpoints
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

The Orchestration service is a regionalized service. 

.. tip

  To help you decide which regionalized endpoint to use, read about special
  considerations for choosing a region at http://www.rackspace.com/
  knowledge_center/article/about-regions.

Use one of the following service access/endpoint to access the Rackspace Cloud Orchestration service: 

+-------------------------+-----------------------------------------------------------------+
| Region                  | Endpoint                                                        |
+=========================+=================================================================+
| Chicago (ORD)           | https://ord.orchestration.api.rackspacecloud.com/v1/123456/     |
+-------------------------+-----------------------------------------------------------------+
| Dallas/Ft. Worth (DFW)  | https://dfw.orchestration.api.rackspacecloud.com/v1/123456/     |
+-------------------------+-----------------------------------------------------------------+
| Northern Virginia (IAD) | https://iad.orchestration.api.rackspacecloud.com/v1/123456/     |
+-------------------------+-----------------------------------------------------------------+
| London (LON)            | https://lon.orchestration.api.rackspacecloud.com/v1/123456/     |  
+-------------------------+-----------------------------------------------------------------+
| Sydney (SYD)            | https://syd.orchestration.api.rackspacecloud.com/v1/123456/     |
+-------------------------+-----------------------------------------------------------------+
| Hong Kong (HKG)         | https://hkg.orchestration.api.rackspacecloud.com/v1/123456/     |
+-------------------------+-----------------------------------------------------------------+

Replace ``123456`` with your Rackspace Cloud account number. 

..  note:: 

      You can find the complete URI to access the Cloud Orchestration API that includes 
      your account number in the service catalog returned in the 
      :ref:`authentication response <review-auth-resp>`. Search 
      the catalog for the service name, ``cloudOrchestration``. Then copy the URI from 
      the *publicURL* field included in the service information. 
