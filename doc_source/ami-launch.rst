.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

################################################
Launch an |EC2| Instance from an |AMIlong| (AMI)
################################################

Before launching an EC2 instance, you should create a security group that will permit network
traffic that is appropriate to your application to connect to the instance. At a minimum, the
security group should enable access on port 22, so that you can SSH into the EC2 instance. You may
also want to create a keypair, although you can also create the keypair while going through the
launch wizard.  Finally, you should think about which instance type is appropriate to your
application; the price for an EC2 instance is typically higher for the more powerful types of
instances. You can find a list of instance types and pricing information on the |ec2-pricing|_ page.

**To launch an Amazon EC2 instance**

1.  In :guilabel:`AWS Explorer`, expand the :guilabel:`Amazon EC2` node. Right-click the
    :guilabel:`Amazon Machine Images (AMIs)` subnode and select :guilabel:`Open EC2 AMIs View`.

    .. figure:: images/amzn-exp-open-ami-view.png
        :scale: 50

        AMI configuration dialog box

2.  Configure the AMIs view to show the AMI that we'll use in this example. In the filter box, type
    :userinput:`start ebs`. This filters the list of AMIs to show only those AMIs with names that
    contains both "start" and "ebs".

    Right-click the :guilabel:`amazon/getting-started-with-ebs` AMI and select :guilabel:`Launch`
    from the context menu.

    .. figure:: images/ami-view-launch-start-ebs.png
        :scale: 50

        Select the Getting Started with EBS AMI

3.  In the :guilabel:`Launch EC2 Instance` dialog box, configure the AMI for your application.

    :emphasis:`Number of Hosts`
        Set this value to the number of EC2 instances to launch.

    :emphasis:`Instance Type`
        Select the type of the EC2 instance to launch. You can find a list of instance types and
        pricing information on the |ec2-pricing|_ page.

    :emphasis:`Availability Zone`
        Select an availability zone (AZ) in which to launch the instance. Note that not all AZs are
        available in all regions. If the AZ that you select is not available, the Toolkit will
        generate a message saying that you need to select a different AZ. For more information about
        AZs, go to the :ec2-ug:`Region and Availability Zone FAQ
        <FAQ_Regions_Availability_Zones.html>` in the |EC2-ug|.

    :emphasis:`Key Pair`
        A key pair is a set of public/private encryption keys that are used to authenticate you when
        you connect to the EC2 instance using SSH. Select a keypair for which you have access to the
        private key.

        .. image:: images/inline-keypair-create.png
            :scale: 50

    :emphasis:`Security Group`
        The security group controls what type of network traffic the EC2 instance will accept. You
        should select a security group that will allow incoming traffic on port 22, i.e. the port
        that is used by SSH, so that you can connect to the EC2 instance. For information about how
        to create security groups using the Toolkit, see :doc:`tke-sg`

    :emphasis:`Instance Profile`
        The instance profile is a logical container for an IAM role. When you select an instance
        profile, you associate the corresponding IAM role with the EC2 instance. IAM roles are
        configured with policies that specify access to particular AWS services and account
        resources. When an EC2 instance is associated with an IAM role, application software that
        runs on the instance runs with the permissions specified by the IAM role. This enables the
        application software to run without having to specify any AWS credentials of its own, which
        makes the software more secure. For in-depth information about IAM roles, go to
        :iam-ug:`Working with Roles <WorkingWithRoles>` in the |IAM-ug|.

    :emphasis:`User Data`
        The user data is data that you provide to the application software that runs on your EC2
        instance. The application software can access this data through the :ec2-ug:`Instance Meta
        Data Service (IMDS) <ec2-instance-metadata>`.

    .. figure:: images/launch-ami-tke.png
        :scale: 50

        Launching an AMI from AWS Explorer

4.  Click :guilabel:`Finish`.

5.  In AWS Explorer, under the :guilabel:`Amazon EC2` node, right-click the :guilabel:`Instances`
    subnode and select :guilabel:`Open EC2 Instances View`.

    Your EC2 instance should appear in the :guilabel:`EC2 Instances` view. It may take a few minutes
    for the instance to transition into the :guilabel:`running` state. Once the instance is running,
    you can right-click the instance to bring up a context menu of operations that you can perform
    on the instance. For example, you can terminate the instance from this menu. You can also copy
    the instance's public DNS address. You would use this address to connect to the instance using
    SSH.

    .. figure:: images/instances-view-ami-launch-start-ebs.png
        :scale: 50

        List of Amazon EC2 instances

