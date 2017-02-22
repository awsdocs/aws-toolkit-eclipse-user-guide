.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

##############################
Identity and Access Management
##############################

|IAMlong| (|IAM|) lets you control who can access your AWS resources and what they can do with them.
The |explorer| lets you create and manage |IAM| users, groups, and roles. You can also set a
password policy for users, which lets you specify password requirements like minimum length, and
lets you specify whether users are allowed to change their own passwords.

.. note:: It is a best practice for *all users, even the account owner*, to access AWS resources as
   IAM users. This ensures that if the credentials for one of the IAM users are compromised, the
   affected credentials can be revoked without needing to change the root credentials for the
   account.


About |IAMlong|
===============

Instead of sharing the password and security credentials for your account (the access key ID and
secret access key), you can create :emphasis:`IAM users` that can each have their own password and
security credentials. You can then attach :emphasis:`policies` to users; in the policies you specify
permissions that determine what actions a user can take and what resources the user is allowed
access to.

For convenience, instead of adding policies to individual users, you can create :emphasis:`IAM
groups` (for example, *Admins* and *Developers*) attach policies to them, and then add users to
those groups. You can also create :emphasis:`roles` that have policies with permissions. Roles can
be assumed by users who are in other accounts, by services, and by users who do not have an IAM
identity. For more information about |IAM|, see the |IAM-ug|_.

.. _tke-create-an-iam-user:

Create an IAM User
==================

You create IAM users so that others in your organization can have their own AWS identity. You can
assign permissions to an IAM user either by attaching an IAM policy to the user or by assigning the
user to a group. IAM users that are assigned to a group derive their permissions from the policies
that are attached to the group. For more information, see :ref:`tke-create-an-iam-group` and
:ref:`tke-add-an-iam-user-to-an-iam-group`.

Using the Toolkit, you can also generate AWS credentials (access key ID and secret access key) for
the IAM user. For more information, see :ref:`tke-generate-credentials-for-an-iam-user`.

.. topic:: To create an IAM User

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node,
        right-click the :guilabel:`Users` node, and then select :guilabel:`Create New Users`.

        .. image:: images/iam-users-create-menu.png

    #.  In the :guilabel:`Create New Users` dialog box, enter up to five names for new IAM users, and
        then click :guilabel:`Finish`. For information about constraints on names for IAM users, see
        :iam-ug:`Limitations on IAM Entities <reference_iam-limits>` in the |IAM-ug|.

        .. image:: images/iam-users-create-dlg.png

For information about adding a user to a group, see :ref:`tke-add-an-iam-user-to-an-iam-group`. For
information about how to create a policy and attach it to the user, see
:ref:`tke-create-an-iam-policy`.


.. _tke-create-an-iam-group:

Create an IAM Group
===================

You can add |IAM| users to groups in order to make it easier to manage permissions. Any permissions
that are attached to the group apply to any users in that group. For more information about IAM
groups, see :iam-ug:`Working with Users and Groups <id>` in the |IAM-ug|.

When you create a group, you can create a policy that includes the permissions that members of the
group will have.

.. topic:: To create an IAM group

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node,
        right-click the :guilabel:`Groups` node, and then select :guilabel:`Create New Group`.

        .. image:: images/iam-group-create-menu.png

    #.  Enter a name for the new IAM group and then click :guilabel:`Next`.

        .. image:: images/iam-group-create-dlg.png

    #.  Enter a name for the policy that establishes what members of the group are allowed to do.
        Enter the policy as a JSON document, and then click :guilabel:`OK`.

        .. image:: images/iam-create-group-permissions.png

        The policy name must be unique within your account. The JSON that you enter for the policy
        must validate, or you will not be able to save the policy. For information about how to
        create a policy, see :iam-ug:`Overview of Policies <access_policies>` in the |IAM-ug|.

    #.  Click :guilabel:`Finish`.

For information about attaching additional policies to the IAM group, see
:ref:`tke-create-an-iam-policy`.


.. _tke-add-an-iam-user-to-an-iam-group:

Add an IAM User to an IAM Group
===============================

If an IAM user is added to a group, any policies that are attached to the group are also in effect
for the user. For more information about IAM users, see :iam-ug:`Users and Groups <id>` in the
|IAM-ug|.

.. topic:: To add an IAM user to a IAM group

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node,
        right-click the :guilabel:`Groups` node, and then select :guilabel:`Open Groups Editor`. Note
        that you add IAM users to IAM groups from the :guilabel:`Groups` node in :guilabel:`AWS
        Explorer` rather than from the :guilabel:`Users` node.

    #.  In the :guilabel:`Groups` editor, select the group you want to add users to, and then click the
        :guilabel:`Users` tab.

        .. image:: images/iam-group-users-tab.png

    #.  On the right-hand side of the bottom pane, click the :guilabel:`Add Users` button.

        .. image:: images/iam-group-add-users-button.png

    #.  In the :guilabel:`Add Users to Group` dialog box, select the users you want to add, and then
        click :guilabel:`OK`.

        .. image:: images/iam-group-add-users-to-group-dlg.png


.. _tke-generate-credentials-for-an-iam-user:

Manage Credentials for an IAM User
==================================

For each user, you can add a password. IAM users use a password to work with AWS resources in the
|console|.

.. topic:: To create a password for an IAM user

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node,
        right-click the :guilabel:`Users` node, and then select :guilabel:`Open Users Editor`.

    #.  In the users listing, select the user you want to create a password for, and then click the
        :guilabel:`Summary` tab.

        .. image:: images/iam-users-summary-tab.png

    #.  On the right-hand side of the bottom pane, click the :guilabel:`Update Password` button.

        .. image:: images/iam-users-update-password-button.png

    #.  In the :guilabel:`Update User Password` dialog box, enter a password and then click
        :guilabel:`OK`.

        .. note:: The new password will overwrite any existing password.

        .. image:: images/iam-users-update-user-password-dlg.png

For each user you can also generate a set of access keys (an access key ID and a secret access key).
These keys can be used to represent the user for programmatic access to AWS |mdash| for example, to
use the AWS command-line interface (CLI), to sign programmatic requests using the SDK, or to access
AWS services through the Toolkit. (For information about how to specify credentials for use with the
Toolkit, see :doc:`setup-credentials`.)

.. topic:: To generate access keys for an IAM user

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node,
        right-click the :guilabel:`Users` node, and then select :guilabel:`Open Users Editor`.

    #.  In the users listing, select the user you want to generate keys for, and then click the
        :guilabel:`Summary` tab.

        .. image:: images/iam-users-summary-tab.png

    #.  Click the :guilabel:`Manage Access Keys` button.

        .. image:: images/iam-users-manage-access-keys-button.png

        A window is displayed where you can manage access keys for the user.

        .. image:: images/iam-user-create-access-key-listing-dlg.png

    #.  Click the :guilabel:`Create Access Key` button.

        The :guilabel:`Manage Access Key` dialog box is displayed.

        .. image:: images/iam-user-manage-access-key-dlg.png

    #.  Click the :guilabel:`Download` button to download a comma-separated value (CSV) file that
        contains the credentials that were generated.

        .. note:: This will be your only opportunity to view and download these access keys. If you
           lose these keys, you must delete them and create a new set of access keys.

You can generate only two sets of credentials per IAM user. If you already have two sets of
credentials and you need to create an additional set, you must delete one of the existing sets
first.

You can also deactivate credentials. In that case, the credentials still exist, but any requests to
AWS that are made using those credentials will fail. This is useful if you want to temporarily
disable access to AWS for that set of credentials. You can reactivate credentials that were
previously deactivated.

.. topic:: To delete, deactivate, or reactivate access keys for an IAM user

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node,
        right-click the :guilabel:`Users` node, and then select :guilabel:`Open Users Editor`.

    #.  In the users listing, select the user you want to manage access keys for, click the
        :guilabel:`Summary` tab, and then click the :guilabel:`Manage Access Keys` button.

    #.  In the window that lists the access keys for that user, right-click the credentials you want to
        manage and then choose one of the following:

        +   :guilabel:`Delete Access Key`

        +   :guilabel:`Make Inactive`

        +   :guilabel:`Make Active`

        .. image:: images/iam-user-delete-inactivate-keys-menu.png


.. _tke-create-an-iam-role:

Create an IAM Role
==================

Using the AWS Toolkit, you can create IAM :emphasis:`roles`. The role can then be
:emphasis:`assumed` by entities that you want to allow access to your AWS resources. Policies that
you attach to the role determine who can assume the role (the :emphasis:`trusted entity` or
:emphasis:`principal`) and what those entities are allowed to do.

In the Toolkit, you can specify the following trusted entities:

* An AWS service. For example, you can specify that an |EC2| can call other AWS services or that
  |AWSDP| is allowed to manage |EC2| instances. This is known as a :emphasis:`service role`.

* A different account that you own. If you have multiple AWS accounts, you might need to let users
  in one account use a role to get permissions to access resources that are in another account of
  yours.

* A third-party account. You might let a third-party vendor manage your AWS resources. In that case,
  you can create a role in which the trusted entity is the third party's AWS account.

After you specify who the trusted entity is, you can specify a policy that determines what the role
is allowed to do.

For example, you could create a role and attach a policy to that role that limits access to only one
of your |S3| buckets. You can then associate the role with an |EC2| instance. When an application
runs on the |EC2| instance, the application can access only the |S3| bucket that you allowed access
to in the role's policy.

For more information about IAM roles, see :iam-ug:`IAM Roles <id_roles>` in the |IAM-ug|.

.. topic:: To create an IAM role

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node,
        right-click the :guilabel:`Roles` node, and then select :guilabel:`Create New Role`.

        .. image:: images/iam-role-create-menu.png

    #.  Enter a name for the IAM role and then click :guilabel:`Next`.

        .. image:: images/iam-role-create-dlg.png

    #.  Select the trusted entity for the role. To create a service role, select :guilabel:`AWS Service
        Roles` and then select a service role from the drop-down list.

        .. image:: images/iam-create-role-service-role.png

        To provide access for a user that's defined in a different AWS account that you own, select
        :guilabel:`Account ID` and enter the AWS account number of the other account.

        .. image:: images/iam-create-role-cross-account.png

        To provide access for a third-party account, select :guilabel:`Account ID` and enter the third
        party's AWS account number. If the third party has provided you with an :iam-ug:`external ID
        <id_roles_create_for-user_externalid>`, enter that as well.

        .. image:: images/iam-create-role-third-party.png

    #.  Click :guilabel:`Next`.

    #.  Enter a name for the policy that establishes what the role is allowed to do. Then enter the
        policy as a JSON document, and click :guilabel:`OK`.

        .. image:: images/iam-create-role-permissions.png

        The policy name must be unique within your account. The JSON that you enter for the policy must
        validate, or you will not be able to save the policy. For information about how to create a
        policy, see :iam-ug:`Overview of Policies <access_policies>` in the :emphasis:`Using IAM`
        guide.

    #.  Click :guilabel:`Finish`.

        The new IAM role appears in the :guilabel:`Roles` editor.

For examples that show how to access AWS using the IAM role associated with an |EC2| instance, see
:sdk-java-dg:`Using IAM Roles to Grant Access to AWS Resources on Amazon EC2 <java-dg-roles>` in the
|sdk-java-dg|.

.. _tke-create-an-iam-policy:

Attach an IAM Policy to a User, Group, or Role
==============================================

Policies are documents that define permissions. For example, a policy that's attached to a user can
specify what AWS actions the user is allowed to call and what resources the user is allowed to
perform the actions on. If the policy is attached to a group, the permissions apply to users in the
group. If the policy is attached to a role, the permissions apply to whoever assumes the role.

The process for attaching a policy to a user or group is similar. For roles, you can attach a policy
that specifies what the role is allowed to do. You use a separate process to attach or edit the
policy that determines who is allowed to assume the role (that is, to manage the trust
relationship.)

.. note:: If you attached a policy to a user, group, or role previously, you can use this procedure to
    attach an additional policy. To edit an existing policy on a user, group, or role, use the |IAM|
    console, command-line tools, or API calls.

.. topic:: To create an IAM policy for a user, group, or role

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node and
        then double-click the :guilabel:`Groups` node, the :guilabel:`Users` node, or the
        :guilabel:`Roles` node.

    #.  Select the group, user, or role you want to attach the policy to, and then click the
        :guilabel:`Permissions` tab.

        .. image:: images/iam-groups-permissions-tab.png

    #.  On the right-hand side of the bottom pane, click the :guilabel:`Attach Policy` button.

        .. image:: images/iam-groups-attach-policy-btn.png

    #.  In the :guilabel:`Manage Group Policy`, :guilabel:`Manage User Policy`, or :guilabel:`Manage
        Role Permissions` dialog box, enter a name for the policy. Then enter the policy as a JSON
        document, and click :guilabel:`OK`.

        .. image:: images/iam-groups-manage-group-policy-dlg.png

        The policy name must be unique within your account. The JSON that you enter for the policy must
        validate, or you will not be able to save the policy. For information about how to create a
        policy, see :iam-ug:`Overview of IAM Policies <access_policies>` in the |IAM-ug|.

.. topic:: To create or manage a trust relationship for a role

    #.  In :guilabel:`AWS Explorer`, expand the :guilabel:`AWS Identity and Access Management` node and
        then double-click the :guilabel:`Roles` node.

    #.  In the :guilabel:`Roles` editor, select the role you want to manage, and then click the
        :guilabel:`Trust Relationships` tab.

        .. image:: images/iam-roles-trustrelationships-tab.png

    #.  On the right-hand side of the bottom pane, click the :guilabel:`Edit Trust Relationship` button.

        .. image:: images/iam-role-trustrelationship-btn.png

    #.  In the :guilabel:`Edit Trust Relationship` dialog box, edit the JSON policy document and then
        click :guilabel:`OK`.

        .. image:: images/iam-roles-edittrustrelationship-dlg.png


.. _tke-set-password-policy:

Set Password Policy
===================

In the |tke| you can set a password policy for your account. This lets you make sure that passwords
that are created for IAM users follow certain guidelines for length and complexity. It also lets you
specify whether users are allowed to change their own passwords. For more information, see
:iam-ug:`Managing an IAM Password Policy <id_credentials_passwords_account-policy>` in the |IAM-ug|.

.. topic:: To create an IAM policy for a user or group

   #. In :guilabel:`AWS Explorer`, under :guilabel:`Identity and Access Management`, double-click
      the :guilabel:`Password Policy` node.

   #. In the :guilabel:`Password Policy` pane, specify the policy options that you want for your AWS
      account, and then click :guilabel:`Apply Password Policy`.

      .. image:: images/iam-password-policy.png

