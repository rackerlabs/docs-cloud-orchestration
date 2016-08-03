.. _request-using-heat-client:

Using the heat client
~~~~~~~~~~~~~~~~~~~~~

The heat client is a command-line tool that provides access to all public
Cloud Orchestration API methods. To send requests using the client, you
have to install the client and set environment variables.

**Prerequisites**

- Linux or Mac OS X
- Python 2.7 or later
- **setuptools** package, installed by default on Mac OS X
- **pip** package
- Rackspace Cloud account and access to Rackspace Cloud Orchestration


Install the heat client
-----------------------

Install the python-heatclient using pip.

.. code::

     $ sudo pip install python-heatclient

.. note::
   If you previously installed the python-heatclient package, run the following
   command to upgrade it:

   .. code::

        $ sudo pip install --upgrade python-heatclient


.. _set-environment-variables:

Set environment variables
-------------------------

Edit your **bash.profile** file or **.bashrc** file to add and set environment
variables that enable the heat client to connect to your Rackspace
Cloud account. Use nano, or a text editor of your choice, to edit the file.

.. code::

     $ nano ~/.bash_profile

Add the following sets of lines to your bash profile and save the file.
Information about the environment variables is provided after the examples.

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
| OS_AUTH_URL           | The endpoint for the Rackspace Cloud Identity   |
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

Be sure to source the file containing the environment variables after
editing so that the new settings will take effect immediately. For example,
`source .bash_profile`.

Run the help command to ensure that the client has installed correctly and
to review information about using the client.

.. code::

     $ heat help

For a complete list of heat commands, see the
:os-docs:`OpenStack heat client command-line reference
<cli-reference/content/heatclient_commands.html>`.
