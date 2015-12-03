.. code-block:: json
   :emphasize-lines: 10, 18, 26, 34

          {
               "name": "cloudOrchestration",
               "endpoints": [
                   {
                       "region": "IAD",
                       "tenantId": "123456",
                       "publicURL": "https://iad.orchestration.api.rackspacecloud.com/v1.0/123456",
                       "versionInfo": "httpis://iad.orchestration.api.rackspacecloud.com/v1.0",
                       "versionList": "https://iad.orchestration.api.rackspacecloud.com/",
                       "versionId": "1"
                   },
                   {
                       "region": "DFW",
                       "tenantId": "123456",
                       "publicURL": "https://dfw.orchestration.api.rackspacecloud.com/v1.0/123456",
                       "versionInfo": "https://dfw.orchestration.api.rackspacecloud.com/v1.0",
                       "versionList": "https://dfw.orchestration.api.rackspacecloud.com/",
                       "versionId": "1"
                   },
                   {
                       "region": "IAD",
                       "tenantId": "123456",
                       "publicURL": "https://iad.orchestration.api.rackspacecloud.com/v2/123456",
                       "versionInfo": "https://iad.orchestration.api.rackspacecloud.com/v2",
                       "versionList": "https://iad.orchestration.api.rackspacecloud.com/",
                       "versionId": "2"
                   },
                   {
                       "region": "DFW",
                       "tenantId": "123456",
                       "publicURL": "https://dfw.orchestration.api.rackspacecloud.com/v2/123456",
                       "versionInfo": "https://dfw.orchestration.api.rackspacecloud.com/v2",
                       "versionList": "https://dfw.orchestration.api.rackspacecloud.com/",
                       "versionId": "2"
                   }
               ],
               "type": "rax:orchestration"
           },
