.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

#################################
New |LAMlong| Java Project Dialog
#################################

The :guilabel:`New Lambda Java Project` dialog helps you to create and configure a new Java project
that you can use to author a |LAM| function.

.. contents:: **Contents**
   :depth: 1
   :local:

Launching the dialog
====================

The :guilabel:`New Lambda Java Project` dialog can be launched in the following ways:

*   by opening the AWS menu in the Eclipse toolbar and selecting :guilabel:`New AWS Lambda Java
    project...`.

*   by selecting :guilabel:`File` > :guilabel:`New` > :guilabel:`Other...` in the Eclipse menu, and
    then choosing :guilabel:`AWS` > :guilabel:`AWS Lambda Java Project` in the resulting dialog.


Create Project Dialog user interface
====================================

.. image:: images/lambda_create_project_default.png

Project name
    :emphasis:`Required`. You must provide a name for your project.

Package name
    An optional name for your Java package. It must be a valid Java package name, such as
    "com.mycompany.myproject". When you enter the package name in the text entry field, it will be
    added to the contents of the :guilabel:`Source Preview` window.

    :emphasis:`Default`: None, this parameter is optional.

Class name
    :emphasis:`Required`. The name that identifies the Java class that contains your |LAM| code. It
    must be a valid Java class name. The default value is generic; you can specify your own name
    here or change the :guilabel:`Package name` to avoid conflicts with similarly-named classes.

    :emphasis:`Default`: :emphasis:`LambdaFunctionHandler`


Input type
    :emphasis:`Required`. The type of input that will be used to call your |LAM| function. You can
    select a category from the drop-down list:

    *   :emphasis:`S3 Event` |ndash| receives an event from `Amazon S3
        <http://docs.aws.amazon.com/lambda/latest/dg/walkthrough-s3-events-adminuser.html>`_ event.

    *   :emphasis:`SNS Event` |ndash| receives an event from `Amazon SNS
        <http://docs.aws.amazon.com/sns/latest/dg/sns-lambda.html>`_.

    *   :emphasis:`Kinesis Event` |ndash| receives an event from an `Amazon Kinesis stream
        <http://docs.aws.amazon.com/lambda/latest/dg/walkthrough-kinesis-events-adminuser.html>`_.

    *   :emphasis:`Cognito Event` |ndash| receives an event from `Amazon Cognito
        <http://docs.aws.amazon.com/cognito/devguide/sync/cognito-events/>`_.

    *   :emphasis:`Custom` |ndash| receives an event from custom code. If you set the input type to
        :emphasis:`Custom`, then you can also set the name of the custom input type in the box next
        to the type selection. By default, the generic :emphasis:`Object` type is used.

        .. important:: The custom input type :emphasis:`must` be a valid Java class name, and not a primitive
            type such as :code:`int`, :code:`float`, and so on. You can use Java's standard boxed
            types (:code:`Integer`, :code:`Float`, ...) for these cases.

        Use the :emphasis:`Custom` input type for setting up event sources such as the following:

        *   `user applications
            <http://docs.aws.amazon.com/lambda/latest/dg/getting-started-custom-events.html>`_

        *   `mobile applications
            <http://docs.aws.amazon.com/lambda/latest/dg/wt-user-app-android.html>`_

        *   The `AWS Management Console
            <http://docs.aws.amazon.com/lambda/latest/dg/getting-started-custom-events.html>`_.

        *   The `AWS CLI invoke command
            <http://docs.aws.amazon.com/lambda/latest/dg/API_Invoke.html>`_.

    :emphasis:`Default`: :emphasis:`S3 Event`

Output type
    The output type. This must be a valid Java object.

    :emphasis:`Default`: :emphasis:`Object`


