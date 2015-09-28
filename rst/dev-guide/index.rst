.. _index:

=========================================================
Rackspace Cloud Orchestration API, version 1.0
=========================================================

*Last updated:* |today|

Learn how to use the Cloud Orchestration service by using the ReST API. 

- See the :ref:`Developer Guide <developer-guide>` for details about using the API.
- See the :ref:`API reference <api-reference>`, for details about API resources, operations, requests and responses.

Rackspace Cloud Orchestration is the name of the Rackspace
orchestration, and application architecture management service.  Cloud
Orchestration provides a software API to create and manipulate stacks of
resources (for example load balancers, web servers, databases, and so
forth) and software that operates as part of those stacks (for example
Apache, PHP, MySQL, Wordpress, and so forth). Cloud Orchestration is an
engine that understands Cloud topologies, unlike Chef or Puppet, which
are concerned with software on servers. Where applicable, Cloud
Orchestration leverages software configuration management tools such as
Chef. Using simple template syntax, you can define a cloud stack, deploy
the stack, scale the stack (for example add/remove resources), delete
the stack, clone the stack, and more.

Systems Engineers, DevOps, and Developers who manage application
infrastructure in the cloud, want a simple way to deploy and manage the
resources of their application. Cloud Orchestration provides the ability
to declare resource provisioning and software configuration from a
template file to allow you to automate deployment of your applications
in a repeatable push-button method in order to spend less time managing
infrastructure and more time developing and operating your
application. Other solutions overly compartmentalize the work necessary
to deploy and manage an application’s cloud infrastructure.  Choosing to
use Cloud Orchestration at Rackspace provides for:

*  Portability of stacks between public and private OpenStack clouds

*  A declarative resource specification within a simple template syntax
   for better flexibility in repeated deployment of an application
   across varied environments

*  Standardized application stacks based on determined best practices by
   Rackspace and backed by expertise in Fanatical Support

Cloud Orchestration is not meant to replace software configuration tools
such as Chef, Puppet, Ansible, Salt, and so forth. Instead, the
orchestration service works with existing tools you are familiar with to
accomplish software configuration management. Rackspace Cloud
Orchestration, purposely built for any OpenStack cloud, not only eases
deployments across multiple environments, but also provides basic
configuration verification and eases application scaling. This is
possible because template authors can integrate knowledge of the design
of an application stack and the scripts that deploy and configure it.

Rackspace Cloud Orchestration Services are available to Rackspace Cloud
customers. Interactions with Rackspace Cloud Orchestration occur
programmatically via the Rackspace Cloud Orchestration API as described
in the *Cloud Orchestration Developer Guide*.

.. toctree:: :hidden:
   :maxdepth: 2

   About the API <overview/index>
   developer-guide
   concepts
   general-api-info/index
   api-reference
   api-operations/index
   
   
   