
.. _service-access:

========================
Service access endpoints
========================

The |apiservice| service is a regionalized service.

The following table lists the |product name| endpoints that are available
for each region.

.. tip

  To help you decide which regionalized endpoint to use, read about special
  considerations for choosing a region in the
  :how-to:`About regions<about-regions>` article on the Rackspace Support site. 

.. _api-info-service-access-regional:

.. list-table:: **Regionalized service endpoints**
   :widths: 10 40
   :header-rows: 1

   * - Region
     - Endpoint
   * - Chicago (ORD)
     - ``https://ord.orchestration.api.rackspacecloud.com/v1/$TENANT_ID/``
   * - Dallas/Ft. Worth (DFW)
     - ``https://dfw.orchestration.api.rackspacecloud.com/v1/$TENANT_ID/```
   * - Northern Virginia (IAD)
     - ``https://iad.orchestration.api.rackspacecloud.com/v1/$TENANT_ID/``
   * - London (LON)
     - ``https://lon.orchestration.api.rackspacecloud.com/v1/$TENANT_ID/``
   * - Sydney (SYD)
     - ``https://syd.orchestration.api.rackspacecloud.com/v1/$TENANT_ID/``
   * - Hong Kong (HKG)
     - ``https://hkg.orchestration.api.rackspacecloud.com/v1/$TENANT_ID/``

Replace the ``$TENANT_ID`` with your actual account number that is returned
as part of the authentication response. The account number is
located  after the  final slash (/) in the ``publicURL`` field.

The correct service access endpoint to for your account is provided in the
service catalog included in the :ref:`response <review-auth-resp>`
that is returned when you authenticate to |product name|.
Use the service type (``rax:load-balancer``) to locate the
correct endpoint in the service catalog.
