.. _request-using-heat-client:

Using the heat client
~~~~~~~~~~~~~~~~~~~~~

The heat client is a command-line tool that provides access to all
Cloud Orchestration API methods. Before you can send requests using the
client, you must install the client and set the environment variables
that enable the heat client to connect to your Rackspace
Cloud account.

Before installing the heat client, make sure the following software and
packages are available on your system:

- Linux or Mac OS X
- Python 2.7 or later
- **setuptools** package, installed by default on Mac OS X
- **pip** package
- Rackspace Cloud account and access to Rackspace Cloud Orchestration

To install the python-client, perform the following steps:

1. Install the python-heatclient using pip.

   .. code::

      $ sudo pip install python-heatclient

   .. note::

      If you previously installed the python-heatclient package, run the
      following command to upgrade it:

      .. code::

         $ sudo pip install --upgrade python-heatclient

2. Export the following environment variables manually, or update your
   ``.bash_profile`` or ``.bashrc`` files with these variables:

   .. code::

        export OS_AUTH_URL=https://identity.api.rackspacecloud.com/v2.0/
        export OS_USERNAME=yourUserName
        export OS_TENANT_ID=yourTenantId
        export OS_REGION_NAME=yourRegionName
        export OS_PASSWORD=yourPassword

The following table describes the environment variables:

+-----------------------+-------------------------------------------------+
| Environment variable  | Description                                     |
+=======================+=================================================+
| OS_AUTH_URL           | The endpoint for the Identity                   |
|                       | service, which the heat client uses for         |
|                       | authentication.                                 |
+-----------------------+-------------------------------------------------+
| OS_USERNAME           | Your Rackspace Cloud user name.                 |
+-----------------------+-------------------------------------------------+
| OS_TENANT_ID          | Your Rackspace Cloud tenant ID (account number) |
+-----------------------+-------------------------------------------------+
| OS_REGION_NAME        | The regional endpoint (for example, DFW) where  |
|                       | you want to deploy the Cloud Orchestration      |
|                       | resources. For details, see                     |
|                       | :ref:`service-access`.                          |
+-----------------------+-------------------------------------------------+
| OS_PASSWORD           | Your Rackspace Cloud password.                  |
+-----------------------+-------------------------------------------------+

After you update the ``bash_profile`` or ``bash.rc`` file, make sure to source
the file so that the new settings take effect immediately, for example
``source .bash_profile``.

Run the help command to ensure that the client has installed correctly and
to review information about using the client.

.. code::

     $ heat help

For a complete list of heat commands, see the
:os-docs:`OpenStack heat client command-line reference
<cli-reference/content/heatclient_commands.html>`.
