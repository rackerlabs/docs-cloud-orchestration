=======================
General API Information
=======================

The Cloud Orchestration API is implemented using a ReSTful web service
interface. Like other Rackspace services, the Cloud Orchestration
Service shares a common token-based authentication system that allows
seamless access between products and services.

Authentication
--------------

Every ReST request against the Cloud Orchestration Service requires the
inclusion of a specific authorization token, supplied by the
``X-Auth-Token`` HTTP header. Customers obtain this token by first using
the Rackspace Cloud Authentication Service and supplying a valid
username and API access key.

Geographic Endpoints
~~~~~~~~~~~~~~~~~~~~

The Rackspace Cloud Authentication Service serves as the entry point to
all Rackspace Cloud APIs and is itself a ReSTful web service.

Use the following endpoint to access the Authentication Service,
regardless of US or UK identities:

*  https://identity.api.rackspacecloud.com/v2.0/

Your account may be based in either the US or the UK; this is not
determined by your physical location but by the location of the
Rackspace retail site which was used to create your account:

*  If your account was created via http://www.rackspacecloud.com, it is
   a US-based account.

*  If your account was created via http://www.rackspace.co.uk, it is a
   UK-based account.

Retrieving the Authentication Token
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

POS v2.0/tokens
   Authenticate to receive a token and a service catalog.
   Normal Response Code(s): 200, 203

   Error Response Code(s): unauthorized (401), userDisabled (403), badRequest
   (400), authFault (500), serviceUnavailable (503)

The authenticate operation provides clients with an authentication token and a list of regional cloud endpoints. The sample requests and responses in this section illustrate a general case. In your authentication request, use your own credentials rather than the sample values shown here for username and apiKey. When you authenticate successfully, the response to your authentication request will include a catalog of the services to which you have subscribed rather than the sample values shown here.

.. note::

   If you authenticate with username and password credentials, you can set up
   multi-factor authentication to add an additional level of security to your
   account. This feature is not available for username and API key credentials.
   For information about setting up and using multi-factor authentication, see
   Multi-factor authentication in the Cloud Identity Client Developer Guide.

For information about other authentication methods with examples, see
Authentication tokens in the Cloud Identity Client Developer Guide.

Example: Auth Request for US Endpoint: JSON

.. code::

    POST /v2.0/tokens HTTP/1.1
    User-Agent: curl/7.21.0 (x86_64-pc-linux-gnu) libcurl/7.21.0 OpenSSL/0.9.8o zlib/1.2.3.4 libidn/1.15 libssh2/1.2.6
    Host: identity.api.rackspacecloud.com
    Accept: application/json
    Content-Type: application/json
    Content-Length: 54

    {
       "auth":
       {
          "RAX-KSKEY:apiKeyCredentials":
          {
             "username": (1)"jsmith",
             "apiKey": (2)"aaaaa-bbbbb-ccccc-12345678"
          }
       }
    }


The username supplied here is your common Rackspace Cloud username.

The apiKkey is your API access key.

To find your API Key:

#. Log in to the Cloud Control Panel (https://mycloud.rackspace.com).

#. On the upper-right side of the top navigation pane, click your username.

#. From the menu, select Account Settings.

#. In the Login Details section of the Account Settings page, locate the API
   Key field and click Show.

#. Copy the value of the API Key and paste it into a text editor of your
   choice.

#. Click Hide to hide the value of the API Key.

.. code::

   HTTP/1.1 200 OK
   Content-Type: application/json; charset=UTF-8
   Content-Length: 477
   Date: Thu, 12 Apr 2012 18:45:13 GMT

   {
    "access": {
      
        "token": {
            "expires": "2011-12-08T22:51:02.000-06:00", 
            "id": "xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx"
        }, 
        "user": {
            "id": "123456", 
            "name": "jsmith",
            "RAX-AUTH:defaultRegion": "DFW",
            "roles": [
                {
                    "description": "Admin Role.", 
                    "id": "identity:admin", 
                    "name": "identity:admin"
                }, 
                {
                    "description": "Default Role.", 
                    "id": "identity:default", 
                    "name": "identity:default"
                }
            ]
        },
        "serviceCatalog": [
            {
                "endpoints": [
                    {
                        "publicURL": "https://dfw.databases.api.rackspacecloud.com/v1.0/1100111", 
                        "region": "DFW", 
                        "tenantId": "1100111"
                    }, 
                    {
                        "publicURL": "https://ord.databases.api.rackspacecloud.com/v1.0/1100111", 
                        "region": "ORD", 
                        "tenantId": "1100111"
                    }
                ], 
                "name": "cloudDatabases", 
                "type": "rax:database"
            },
            {
                "endpoints": [
                    {
                        "publicURL": "https://dfw.loadbalancers.api.rackspacecloud.com/v1.0/1100111", 
                        "region": "DFW", 
                        "tenantId": "1100111"
                    }, 
                    {
                        "publicURL": "https://ord.loadbalancers.api.rackspacecloud.com/v1.0/1100111", 
                        "region": "ORD", 
                        "tenantId": "1100111"
                    }
                ], 
                "name": "cloudLoadBalancers", 
                "type": "rax:load-balancer"
            }, 
            {
                "endpoints": [
                    {
                        "tenantId": "1100111",
                        "region": "DFW",
                        "publicURL": "https://dfw.servers.api.rackspacecloud.com/v2/1100111", 
                        "versionId": "2", 
                        "versionInfo": "https://dfw.servers.api.rackspacecloud.com/v2/", 
                        "versionList": "https://dfw.servers.api.rackspacecloud.com/"
                    },
                    {
                        "tenantId": "1100111",
                        "region": "ORD",
                        "publicURL": "https://ord.servers.api.rackspacecloud.com/v2/1100111", 
                        "versionId": "2", 
                        "versionInfo": "https://ord.servers.api.rackspacecloud.com/v2/", 
                        "versionList": "https://ord.servers.api.rackspacecloud.com/"
                    }
                ],
                "name": "cloudServersOpenStack", 
                "type": "compute"
            },
            {
                "endpoints": [
                    {
                        "tenantId": "1100111", 
                        "publicURL": "https://servers.api.rackspacecloud.com/v1.0/1100111", 
                        "versionId": "1.0", 
                        "versionInfo": "https://servers.api.rackspacecloud.com/v1.0/", 
                        "versionList": "https://servers.api.rackspacecloud.com/"
                    }
                ],
                "name": "cloudServers", 
                "type": "compute"
            }, 
            {
                "endpoints": [
                    {
                        "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee",
                        "publicURL": "https://storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                        "internalURL": "https://snet-storage101.dfw1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                        "region": "DFW"
                    },
                    {
                        "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee",
                        "publicURL": "https://storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                        "internalURL": "https://snet-storage101.ord1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                        "region": "ORD"
                    }
                ], 
                "name": "cloudFiles", 
                "type": "object-store"
            }, 
            {
                "endpoints": [ 
                    {
                        "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                        "publicURL": "https://cdn1.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                        "region": "DFW"
                    }, 
                    {
                        "tenantId": "MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                        "publicURL": "https://cdn2.clouddrive.com/v1/MossoCloudFS_aaaaaaaa-bbbb-cccc-dddd-eeeeeeee", 
                        "region": "ORD"
                    }
                ],
                "name": "cloudFilesCDN", 
                "type": "rax:object-cdn"
            }, 
            { 
                "endpoints": [
                    {
                        "region": "SYD",
                        "tenantId": "1100111",
                        "publicURL": "https://syd.orchestration.api.rackspacecloud.com/v1/1100111"
                    },
                    {
                        "region": "IAD",
                        "tenantId": "1100111",
                        "publicURL": "https://iad.orchestration.api.rackspacecloud.com/v1/1100111"
                    },
                    {
                         "region": "ORD",
                         "tenantId": "1100111",
                         "publicURL": "https://ord.orchestration.api.rackspacecloud.com/v1/1100111"
                    },
                    {
                          "region": "DFW",
                          "tenantId": "1100111",
                          "publicURL": "https://dfw.orchestration.api.rackspacecloud.com/v1/1100111"
                    }
                ],
                "name": "cloudOrchestration",
                "type": "orchestration"
            },
            {
                "endpoints": [
                    {
                        "tenantId": "1100111",
                        "publicURL": "https://dns.api.rackspacecloud.com/v1.0/1100111"
                    }
                ],
                "name": "cloudDNS", 
                "type": "rax:dns"
            }
        ]
    }
   }

Cloud Orchestration service endpoints are published in the service catalog in the Auth response with the account number, which is a required element of the service endpoints. The examples shown here are for authentication for US customers. Customers with UK-based accounts will see different values in the service catalog. Refer to the next section for more information about service endpoints.