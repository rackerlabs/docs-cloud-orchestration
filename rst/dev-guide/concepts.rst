.. _concepts:


========
Concepts
========

To use Cloud Orchestration effectively, you should understand several
key concepts:

Template
--------

A Cloud Orchestration template is a portable file, written in a
user-readable language, that describes how a set of resources should be
assembled and what software should be installed in order to produce a
working stack. The template specifies what resources should be used,
what attributes can be set, and other parameters that are critical to
the successful, repeatable automation of a specific application stack.

Resource
--------

A resource is a template artifact that represents some component of your
desired architecture (a Cloud Server, a group of scaled Cloud Servers, a
load balancer, some configuration management system, and so forth).

Stack
-----

A stack is a group of resources (servers, load balancers, databases, and
so forth) combined to fulfill a useful purpose. Based on a template,
Heat orchestration engine creates an instantiated set of resources (a
stack) to run the application framework or component specified (in the
template). A stack is a running instance of a template. The result of
creating a stack is a deployment of the application framework or
component.

