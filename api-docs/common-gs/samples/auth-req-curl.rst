.. _auth-curl-request:

.. code::

	  $ curl https://identity.api.rackspacecloud.com/v2.0/tokens \
	         -X POST \
	         -d '{"auth":{"RAX-KSKEY:apiKeyCredentials":{"username":"$username","apiKey":"$apiKey"}}}' \
	         -H "Content-type: application/json" | python -m json.tool
