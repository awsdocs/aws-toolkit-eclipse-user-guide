.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

##########################################
Managing Security Groups from AWS Explorer
##########################################

The |tke| enables you to create and configure security groups to use with |EC2long| (|EC2|)
instances. When you launch an |EC2| instance, you need to specify an associated security group.

A security group acts like a firewall on incoming network traffic. The security group specifies what
types of network traffic an |EC2| instance will allow to be received. It can also specify that
incoming traffic will be accepted only from certain IP addresses or only from other specified
security groups.

.. _tke-sg-create:

Creating a New Security Group
=============================

In this section, we'll create a new security group. Initially after creation, the security group
will not have any permissions configured. Configuring permissions is handled through an additional
operation.

**To create a new security group**

1.  In :guilabel:`AWS Explorer`, beneath the :guilabel:`Amazon EC2` node, right-click
    :guilabel:`Security Groups`, and then click :guilabel:`Open EC2 Security Groups View`.

2.  Right-click in the left pane of the :guilabel:`EC2 Security Groups` tab, and then click
    :guilabel:`New Group`.

    .. image:: images/tke-sg-ec2-sg-tab.png
        :scale: 50

3.  In the dialog box, enter a name and description for the new security group. Click
    :guilabel:`OK`.

    .. image:: images/tke-sg-new-dlg.png
        :scale: 50


.. _tke-permission-sg:

Adding Permissions to Security Groups
=====================================

In this section, we'll add permissions to the new security group to allow other computers to connect
to our |EC2| instance using Secure Shell (SSH) protocol.

:emphasis:`To add permissions to a security group`

1.  Right-click in the right pane of the :guilabel:`EC2 Security Groups` tab, and then click
    :guilabel:`Add Permissions`.

    .. image:: images/tke-sg-add-perms.png
        :scale: 50

    Invoke Add Permissions UI

2.  In the dialog box, select :guilabel:`Protocol, port and network`. Click :guilabel:`TCP` from the
    :guilabel:`Protocol` drop-down menu. Enter :userinput:`22` for :guilabel:`Port or Port Range`.
    Port 22 is the standard port for SSH. The :guilabel:`Network Mask` box specifies the allowed
    source IP addresses in CIDR format; it defaults to 0.0.0.0/0, which specifies that the security
    group will allow a TCP connection to port 22 (SSH) from any external IP address.

    You could also, for example, specify that connections should be allowed only from computers in
    your local computer's subnet. In this case, you would specify your local computer's IP address
    followed by a "/10". For example, "xxx.xxx.xxx.xxx/10" where the "xxx" correspond to the
    distinct octet values that make up your local computer's IP address.

    Click :guilabel:`OK`.

    .. image:: images/tke-sg-assign-perms-dlg.png
        :scale: 50

You could also set permissions to the security group by specifying a UserID and security group name.
In this case, |EC2| instances in this security group would accept all incoming network traffic from
|EC2| instances in the specified security group. It is necessary to also specify the UserID as a way
to disambiguate the security group name; security group names are not required to be unique across
all of AWS. For more information about security groups, see :ec2-ug:`Amazon EC2 Security Groups
<using-network-security.html>`.

