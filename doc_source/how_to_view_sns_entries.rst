.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

######################################
Viewing and Adding |SNS| Notifications
######################################

You can use the |tke| to view |SNSlong| (|SNS|) topics associated with your application. |SNS| is a
service that enables your application to send notifications, using a protocol such as email, when
specified events occur. To learn more about |SNS|, see the |SNS-dg|_.

.. _view_travel_log_notification:

View an |SNS| Notification
==========================

The following process illustrates how to view an |SNS| notification.


**To view a notification**

1.  In :guilabel:`AWS Explorer`, click the triangle to the left of the :guilabel:`Amazon SNS` node
    to expand it and see the |SNS| topics it contains.

    .. image:: images/tke-tl-sns-aws-explorer.png
        :scale: 50%

2.  Double-click this SNS topic to open a detail view in the Eclipse editor pane. In this example,
    the :guilabel:`Subscription ARN` column says that the topic is pending confirmation. |SNS|
    requires a confirmation from the individual specified by the email address before SNS will send
    email notifications to that individual.

    .. image:: images/tke-tl-sns-detail.png
        :scale: 50%


.. _add_travel_log_notification:

Add an |SNS| Notification
=========================

You can add new |SNS| notifications through AWS Explorer.

**To add a new notification**

1.  In :guilabel:`AWS Explorer`, right-click :guilabel:`Amazon SNS`, and then click
    :guilabel:`Create New Topic`. Enter a name for the new topic and click :guilabel:`OK`.

    .. image:: images/tke-sns-create-new-topic.png
        :scale: 50%

2.  Double-click the new topic to display the detail view for the topic. Right-click in the
    :guilabel:`Subscriptions` area, and then click :guilabel:`Create Subscription`. Leave the
    :guilabel:`Subscription Protocol` box as :guilabel:`Email (plain text)` and enter an email
    address for the endpoint. Click :guilabel:`OK` . The detail view for the notification will now
    include this subscription.

    .. figure:: images/tke-sns-create-new-proto.png
        :scale: 50%

        Select the notification protocol and endpoint.

3.  To delete the subscription, right-click the entry in the :guilabel:`Protocol` column for the
    subscription and click :guilabel:`Delete Subscription`.

.. note:: The creation of the subscription will cause a verification email to be sent to the individual
    specified by the subscription "endpoint" email address. This email address will be used by AWS
    only to send notifications. It will not be used for any other purpose by AWS or Amazon.com.


