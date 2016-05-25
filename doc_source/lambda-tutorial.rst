.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

################################################################
Tutorial: How to Create, Upload and Invoke an |LAMlong| Function
################################################################

This tutorial will guide you through the process of a typical |LAMlong| workflow and provide you
with first-hand experience in using |LAM| with the |tke|.

.. important:: The tutorial assumes that you have an AWS account, have already :doc:`installed the
   AWS Toolkit for Eclipse <getting-started>` and that you understand the basic concepts and features of
   |LAM|. If you are unfamiliar with |LAM|, you can find out more at the `AWS Lambda
   <http://aws.amazon.com/lambda/>`_ home page and in the |LAM-dg|_.

.. contents:: **Contents**
   :depth: 1
   :local:

.. _lambda-tutorial-create-handler-class:

Create a |LAM| handler class
============================

First, you will implement the code as a method in a handler class. The |tke| provides a new project
wizard to help you create a new handler class.

**To create an Lambda handler class**

1.  On the Eclipse toolbar, open the drop-down Amazon Web Services menu (identified by the AWS icon)
    and select :guilabel:`New AWS Lambda Java project...`

2.  Add your Java :emphasis:`project name`, :emphasis:`package name`, and :emphasis:`class name` in
    the associated input boxes. You can choose any valid names that you want. This tutorial will use
    the following sample values:

    * :guilabel:`Project name`: HelloLambda
    * :guilabel:`Package name`: :emphasis:`example`
    * :guilabel:`Class name`: :emphasis:`Hello`

    While you type, the code in the :guilabel:`Source preview` will change to reflect the changes
    you make in the dialog.

3.  For :guilabel:`Input Type`, choose :emphasis:`Custom`. For information about each of the
    available input types, see :doc:`lambda-ref-create-project`.

4.  The second :guilabel:`Input Type` field is name of the actual Java type that will be returned,
    which must be a Java class (not a primitive type such as :code:`float`, :code:`int` or
    :code:`boolean`). It defaults to :code:`Object`. Change this value to :userinput:`String`.

5.  Change the value of :guilabel:`Output Type` to :userinput:`String`, as well.

6.  Verify that your entries look like the following screenshot (modify them if they are not), and
    then click :guilabel:`Finish`.

    .. image:: images/lambda_tutorial_create_project_filled.png

7.  Once you click :guilabel:`Finish`, your project's directory and source files will be generated
    in your eclipse workspace, and a new web browser window will appear, displaying
    :file:`README.html` (which was created for you in your project's root directory).
    :file:`README.html` provides instructions to help guide you through the next steps of
    implementing, testing, uploading and invoking your new |LAM| function. Read through it to gain
    some familiarity with the next steps that will be covered here.

Next, we'll implement the function in the :code:`HelloLambda` Java project that was just created for
you in Eclipse.


.. _lambda-tutorial-implement-handler-method:

Implement the handler method
============================

The :guilabel:`Create New Project` dialog creates a skeleton project for you, but it's up to you to
fill in the code that will be run when your |LAM| function is invoked (in this case, by a custom
event that sends a String to your function, as you specified when setting your method's input
parameter.

**To implement your Lambda handler method**

1.  Using Eclipse's :guilabel:`Project Explorer`, open :file:`Hello.java` in the
    :guilabel:`HelloLambda` project. It will contain code similar to the following:

    .. literalinclude:: code/HelloLambda/src/example/Hello-orig.java
        :language: java
        :lines: 16-

2.  Replace the contents of the :code:`handleRequest` function with the following code:

    .. literalinclude:: code/HelloLambda/src/example/Hello-imp.java
        :language: java
        :lines: 16-

Your :file:`Hello.java` file should now contain:

.. literalinclude:: code/HelloLambda/src/example/Hello.java
    :language: java
    :lines: 16-


.. _lambda-tutorial-assume-role:

Allow |LAM| to assume an |IAM| role
===================================

In order for |LAM| to access your |LAM| function, you will need to create an |IAM| role that gives
it access to your AWS resources. The easiest way to do this is with the |console|.

**To create an IAM role for Lambda**

1.  Sign in to the `AWS Management Console <https://console.aws.amazon.com/>`_.

2.  Open the `AWS Identity and Access Management <https://console.aws.amazon.com/iam/>`_ console.

3.  Select :guilabel:`Roles` on the sidebar, then :guilabel:`Create New Role`.

4.  Add a name for your role, such as :userinput:`hello-lambda-role`, and click :guilabel:`Next
    Step`.

5.  On the :guilabel:`Select Role Type` page, select :emphasis:`AWS Lambda` within the
    :guilabel:`AWS Service Roles` list.

6.  For :guilabel:`Attach Policy`, check :emphasis:`AmazonS3FullAccess`, which allows |LAM| to
    access your |S3| resources, and then click :guilabel:`Next Step` to continue.

    .. note:: |S3| is required because |LAM| will upload your code to an |S3| bucket when you deploy
        and run your |LAM| function. You can use a bucket that you create (this is covered in the
        next section) or use an existing bucket.

7.  Review your role parameters, then click :guilabel:`Create Role` to finish creating the |IAM|
    role.


.. _lambda-tutorial-create-bucket:

Create an |S3| bucket for your |LAM| code
=========================================

|LAMlong| requires an |S3| bucket to store your Java project when you uplooad it. You can either use
a bucket that already exists in the AWS region in which you'll run your code, or you can create a
new one specifically for use by |LAM| (recommended).

**To create an Amazon S3 bucket for use with Lambda**

1.  Log in to AWS and go to the `Amazon S3 console <https://console.aws.amazon.com/s3>`_.

2.  Click :guilabel:`Create Bucket`.

3.  Enter a bucket name and select an `AWS region
    <http://docs.aws.amazon.com/general/latest/gr/glos-chap.html#region>`_ for your bucket. This
    region should be the same one in which you intend to run your |LAM| function. For a list of
    regions supported by |LAM| see the `Regions and Endpoints
    <http://docs.aws.amazon.com/general/latest/gr/rande.html#lambda_region>`_ topic in the
    :title:`AWS General Reference`

4.  Click :guilabel:`Create` to finish creating your bucket.


.. _lambda-tutorial-upload-code:

Upload the code
===============

Next, we'll upload your code to |LAMlong| in preparation for invoking it using the |console|.

**To upload your function to Lambda**

1.  Right-click in your code window and select :guilabel:`AWS Lambda`, then :guilabel:`Upload
    function to AWS Lambda...`.

2.  In the :guilabel:`Select Target Lambda Function` dialog that appears, select the AWS region to
    use. This should be the same region that you chose for your :ref:`Amazon S3 bucket
    <lambda-tutorial-create-bucket>`.

    .. image:: images/lambda_tutorial_upload_function_create_new.png

3.  Select :guilabel:`Create a new Lambda function` and enter the name of your function (such as
    :userinput:`HelloFunction`).

4.  Click :guilabel:`Next` to proceed to :guilabel:`Function Configuration`.

5.  Enter a description for your target |LAM| function. You can leave the rest of the options as
    they are; the |tke| chooses default values for you.

    .. image:: images/lambda_tutorial_upload_function_configure.png

    For more information about the available options, see :doc:`lambda-ref-upload-function`.

6.  Click :guilabel:`Finish` to upload your |LAM| function to AWS.

If the upload succeeds, you will see the |LAM| function name that you chose appear next to your
Eclipse project name in the :guilabel:`Project Explorer` view:

.. image:: images/lambda_tutorial_upload_function_success.png

If you don't see this happen, you should open Eclipse's :guilabel:`Error Log` view. |LAM| will write
information about failures to upload or run your function to the error log for further debugging.


.. _lambda-tutorial-invoke-function:

Invoke the |LAM| function
=========================

You can now invoke the function on |LAMlong|.

**To invoke your Lambda function**

1.  Right-click in your code window and select :guilabel:`AWS Lambda`, then :guilabel:`Run on AWS
    Lambda`.

2.  In the input box, type a valid JSON string, such as "AWS Lambda".

    .. image:: images/lambda_tutorial_invoke_function.png

    .. tip:: You can add new JSON input files in your project, and they will show up in this dialog as
        long as the file name ends with ".json". You can use this feature to provide standard input
        files for your |LAM| functions.

3.  Click :guilabel:`Invoke` and it will send your input data to your |LAM| function. If you have
    set up everything correctly, you should see the return value of your function printed out in the
    Eclipse :guilabel:`Console` view (which will automatically appear if it isn't already shown).

    .. image:: images/lambda_tutorial_success.png


Congratulations, you've just run your first |LAM| function directly from the Eclipse IDE!

Where to go from here
=====================

Now that you've uploaded and deployed your function, try changing the code and re-running the
function. |LAM| will automatically re-upload and invoke the function for you, and print output to
the console.

For more information about each of the screens that were covered in this tutorial, as well as a full
description of each option, see the :doc:`lambda-ref`.

For more information about |LAM| itself, and about writing Java code for |LAM|, see `Authoring
Lambda Functions in Java <http://docs.aws.amazon.com/lambda/latest/dg/java-lambda.html>`_ in the
:title:`AWS Lambda Developer Guide`.


