
.. THIS OUTPUT IS GENERATED FROM THE WADL. DO NOT EDIT.

=============================================================================
List Resource Types -  Rackspace Cloud Orchestration Developer Guide
=============================================================================

List Resource Types
~~~~~~~~~~~~~~~~~~~~~~~~~

`Request <get-list-resource-types-v1-tenant-id-resource-types.html#request>`__
`Response <get-list-resource-types-v1-tenant-id-resource-types.html#response>`__

.. code::

    GET /v1/{tenant_id}/resource_types

Lists the supported template resource types.



This table shows the possible response codes for this operation:


+--------------------------+-------------------------+-------------------------+
|Response Code             |Name                     |Description              |
+==========================+=========================+=========================+
|200                       |                         |                         |
+--------------------------+-------------------------+-------------------------+


Request
^^^^^^^^^^^^^^^^^

This table shows the URI parameters for the request:

+--------------------------+-------------------------+-------------------------+
|Name                      |Type                     |Description              |
+==========================+=========================+=========================+
|{tenant_id}               |                         |The ID of the tenant. A  |
|                          |                         |tenant is also known as  |
|                          |                         |an account or project.   |
+--------------------------+-------------------------+-------------------------+








Response
^^^^^^^^^^^^^^^^^^





**Example List Resource Types: JSON response**


.. code::

    {
        "resource_types": [
            "AWS::EC2::Instance",
            "OS::Heat::ScalingPolicy",
            "AWS::CloudFormation::Stack",
            "OS::Keystone::Group",
            "OS::Glance::Image",
            "AWS::EC2::Volume",
            "OS::Heat::SoftwareDeployment",
            "AWS::AutoScaling::ScalingPolicy",
            "AWS::EC2::InternetGateway",
            "OS::Heat::SoftwareDeployments",
            "AWS::EC2::VolumeAttachment",
            "AWS::CloudFormation::WaitConditionHandle",
            "OS::Cinder::VolumeAttachment",
            "OS::Cinder::EncryptedVolumeType",
            "OS::Heat::AutoScalingGroup",
            "OS::Nova::FloatingIP",
            "OS::Heat::HARestarter",
            "OS::Keystone::Project",
            "OS::Keystone::Endpoint",
            "OS::Heat::InstanceGroup",
            "AWS::CloudWatch::Alarm",
            "AWS::AutoScaling::AutoScalingGroup",
            "OS::Heat::CloudConfig",
            "OS::Heat::SoftwareComponent",
            "OS::Cinder::Volume",
            "OS::Keystone::Service",
            "OS::Heat::WaitConditionHandle",
            "OS::Heat::SoftwareConfig",
            "AWS::CloudFormation::WaitCondition",
            "OS::Heat::StructuredDeploymentGroup",
            "OS::Heat::RandomString",
            "OS::Heat::SoftwareDeploymentGroup",
            "OS::Nova::KeyPair",
            "OS::Heat::MultipartMime",
            "OS::Heat::UpdateWaitConditionHandle",
            "OS::Nova::Server",
            "AWS::IAM::AccessKey",
            "AWS::EC2::SecurityGroup",
            "AWS::EC2::EIPAssociation",
            "AWS::EC2::EIP",
            "OS::Heat::AccessPolicy",
            "AWS::IAM::User",
            "OS::Heat::WaitCondition",
            "OS::Heat::StructuredDeployment",
            "AWS::RDS::DBInstance",
            "AWS::AutoScaling::LaunchConfiguration",
            "OS::Heat::Stack",
            "OS::Nova::FloatingIPAssociation",
            "OS::Heat::ResourceGroup",
            "OS::Heat::StructuredConfig",
            "OS::Nova::ServerGroup",
            "OS::Heat::StructuredDeployments",
            "OS::Keystone::Role",
            "OS::Keystone::User",
            "AWS::ElasticLoadBalancing::LoadBalancer",
            "OS::Nova::Flavor",
            "OS::Cinder::VolumeType"
        ]
    }
    

