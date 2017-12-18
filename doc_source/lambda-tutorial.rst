.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

#################################################################
Tutorial: How to Create, Upload, and Invoke an |LAMlong| Function
#################################################################

This tutorial guides you through the process of a typical |LAMlong| workflow, and provides you
with first-hand experience using |LAM| with the |tke|.

.. important:: The tutorial assumes that you have an AWS account, have already :doc:`installed the
   AWS Toolkit for Eclipse <getting-started>`, and that you understand the basic concepts and
   features of |LAM|. If you're unfamiliar with |LAM|, learn more at the |LAM|_ home
   page and in the |LAM-dg|_.


.. _lambda-tutorial-create-handler-class:

Create an |LAMlong| Project
===========================

To begin a |LAM| project, you first implement the code as a method in a handler class. The |tke| provides
a new project
wizard to help you create a new handler class. The |LAM| project is a Maven project that uses a
POM.xml file to manage package dependencies. You can use the Maven command line tool for
building, testing, and deploying your application. For more information about Maven, see the
`Maven project documentation <https://maven.apache.org>`_.

.. topic:: To create an |LAMlong| project

    #.  On the Eclipse toolbar, open the Amazon Web Services menu (identified by the AWS
        homepage icon), and then choose :guilabel:`New AWS Lambda Java project`. Or on the
        Eclipse menu bar, choose :guilabel:`File`, :guilabel:`New`, :guilabel:`AWS Lambda Java Project`.

    #.  Add a *Project name*, *Group ID*, *Artifact ID*, and *class name* in the associated input
        boxes. The Group ID and Artifact ID are the IDs that identify a Maven build artifact.
        This tutorial uses the following example values:

        * :guilabel:`Project name`: *HelloLambda*
        * :guilabel:`Group ID`: *com.example.lambda*
        * :guilabel:`Artifact ID`: *demo*
        * :guilabel:`Class name`: *Hello*

        The :guilabel:`Package Name` field is the package namespace for the |LAMlong| handler class.
        The default value for this field is a concatination of the Group ID and Artifact ID,
        following Maven project conventions. This field is automatically updated when the
        :guilabel:`Group ID` and :guilabel:`Artifact ID` fields are updated.

    #.  For :guilabel:`Input Type`, choose :guilabel:`Custom`. For information about each of the available
        input types, see :doc:`lambda-ref-create-project`.

    #.  Verify that your entries look like the following screenshot (modify them if they are not), and
        then choose :guilabel:`Finish`.

        .. image:: images/lambda_tutorial_create_project_filled.png
           :alt: Project name, Group ID, Artifact ID and class name values in the New AWS Lambda
                 Maven Project dialog box

        As you type, the code in the :guilabel:`Source preview` changes to reflect the
        changes you make in the dialog box.

    #.  After you choose :guilabel:`Finish`, your project's directory and source files are
        generated in your Eclipse workspace. A new web browser window opens, displaying
        :file:`README.html` (which was created for you in your project's root directory).
        :file:`README.html` provides instructions to guide you through the next steps of
        implementing, testing, uploading, and invoking your new |LAM| function. Read through it to
        gain some familiarity with the steps that are described here.

Next, you implement the function in the :code:`HelloLambda` Java project that was just created for
you in Eclipse.


.. _lambda-tutorial-implement-handler-method:

Implement the Handler Method
============================

You use the :guilabel:`Create New Project` dialog box to create a skeleton project. Now
fill in the code that will be run when your |LAM| function is invoked. (In this case, by a custom
event that sends a String to your function, as you specified when setting your method's input
parameter.)

.. topic:: To implement your Lambda handler method

    #.  In the Eclipse :guilabel:`Project Explorer`, open :file:`Hello.java` in the
        :guilabel:`HelloLambda` project. It will contain code similar to the following.

        .. literalinclude:: code/HelloLambda/src/example/Hello-orig.java
            :language: java
            :lines: 16-

    #.  Replace the contents of the :code:`handleRequest` function with the following code.

        .. literalinclude:: code/HelloLambda/src/example/Hello-imp.java
            :language: java
            :lines: 16-

.. _lambda-tutorial-assume-role:

Allow |LAM| to Assume an |IAM| Role
===================================

For |LAM| to be able to access your |LAM| function, you have to create an |IAM| role that gives
it access to your AWS resources. You can create the role in two ways, either through the |console| or
by using the |tke|.
This section describes how to create the |IAM| role in the console. See
:ref:`lambda-tutorial-upload-code` to create one using the |tke|.

.. topic:: To create an IAM role for Lambda

    #.  Sign in to the |console|_.

    #.  From the :guilabel:`Services` menu, open the :console:`IAM console <iam>`.

    #.  In the Navigation pane, choose :guilabel:`Roles`, and then choose :guilabel:`Create role`.

    #.  For :guilabel:`Select type of trusted entity`, choose :guilabel:`AWS service`, and then choose :guilabel:`Lambda`
        for the service that will use this role. Then choose :guilabel:`Next: Permissions`.

    #.  For :guilabel:`Attach permissions policy`, choose :guilabel:`AWSLambdaBasicExecutionRole`.
        This allows |LAM| to write to your |CW| Logs resources. Then choose :guilabel:`Next: Review`.

    #.  Add a name for your role, such as :code:`hello-lambda-role`, and a description for the role.
        Then choose :guilabel:`Create role` to finish creating the |IAM| role.


.. _lambda-tutorial-create-bucket:

Create an |S3| Bucket for Your |LAM| Code
=========================================

|LAMlong| requires an |S3| bucket to store your Java project when you upload it. You can either use
a bucket that already exists in the AWS Region in which you'll run your code, or you can create a
new one specifically for |LAM| to use (recommended).

You can create an |S3| bucket in two ways, either through the |console| or by using the |tke|.
This section describes how to create an |S3| bucket in the console. See
:ref:`lambda-tutorial-upload-code` to create one using the |tke|.

.. topic:: To create an Amazon S3 bucket for use with Lambda

    #.  Sign in to the |console|_.

    #.  From the :guilabel:`Services` menu, open the :console:`S3 console <s3>`.

    #.  Choose :guilabel:`Create bucket`.

    #.  Enter a bucket name, and then choose a region for your bucket. This region
        should be the same one in which you intend to run your |LAM| function. For a list of regions
        supported by |LAM| see :rande:`Regions and Endpoints <lambda>` in the |AWS-gr|.

    #.  Choose :guilabel:`Create` to finish creating your bucket.


.. _lambda-tutorial-upload-code:

Upload the Code
===============

Next, you upload your code to |LAMlong| in preparation for invoking it using the |console|.

.. topic:: To upload your function to Lambda

    #.  Right-click in your Eclipse code window, choose :guilabel:`AWS Lambda`,
        and then choose :guilabel:`Upload function to AWS Lambda`.

    #.  On the :guilabel:`Select Target Lambda Function` page, choose the AWS Region to use.
        This should be the same region that you chose for your :ref:`Amazon S3 bucket <lambda-tutorial-create-bucket>`.

        .. image:: images/lambda_tutorial_upload_function_create_new.png
           :alt: Select Target Lambda function page

    #.  Choose :guilabel:`Create a new Lambda function`, and then type a name for your function (for example, :code:`HelloFunction`).

    #.  Choose :guilabel:`Next`.

    #.  On the :guilabel:`Function Configuration` page, enter a description for your target |LAM| function,
        and then choose the |IAM| role and |S3| bucket that your function will use.

        .. image:: images/lambda_tutorial_upload_function_configure.png
           :alt: Function Configuration page

        For more information about the available options, see :doc:`lambda-ref-upload-function`.

    #.  On the :guilabel:`Function Configuration` page, choose :guilabel:`Create` in
        :guilabel:`Function Role` if you want to create a new |IAM| role
        for your |LAM| function. Enter a role name in the dialogue box the :guilabel:`Create Role`
        dialogue box.

        .. image:: images/lambda_tutorial_upload_create_iam_role.png
           :alt: Creating a new IAM role in the Function Configuration page

    #.  On the :guilabel:`Function Configuration` page, choose :guilabel:`Publish new version`
        if you want the upload to create a new version of the |LAM| function.
        To learn more about versioning and aliases in |LAM|, see
        :LAM-dg:`AWS Lambda Function Versioning and Aliases <versioning-aliases>` in the |LAM-dg|.

    #.  If you chose to publish a new version, the :guilabel:`Provide an alias to this new version`
        option is enabled. Choose this option if you want to associate an alias with this version of the
        |LAM| function.

    #.  On the :guilabel:`Function Configuration` page, choose :guilabel:`Create` in
        the :guilabel:`S3 Bucket for Function Code` section if you want
        to create a new |S3| bucket for your |LAM| function. Enter a bucket name in the
        :guilabel:`Create Bucket` dialogue box.

        .. image:: images/lambda_tutorial_upload_create_s3_bucket.png
           :alt: Create Bucket page

    #.  In the :guilabel:`S3 Bucket for Function Code` section, you can also choose to encrypt the
        uploaded code. For this example, leave :guilabel:`None` selected. To learn more about |S3| encryption, see
        :S3-dg:`Protecting Data Using Server-Side Encryption <serv-side-encryption>`
        in the |S3-dg|.

    #.  Leave the :guilabel:`Advanced Settings` options as they are. The |tke|
        selects default values for you. Choose :guilabel:`Finish` to upload your |LAM| function to AWS.

If the upload succeeds, you will see the |LAM| function name that you chose appear next to your
Java handler class in the :guilabel:`Project Explorer` view.

.. image:: images/lambda_tutorial_upload_function_success.png

If you don't see this happen, open the Eclipse :guilabel:`Error Log` view. |LAM| writes
information about failures to upload or run your function to this error log so you can debug them.


.. _lambda-tutorial-invoke-function:

Invoke the |LAM| Function
=========================

You can now invoke the function on |LAMlong|.

.. topic:: To invoke your Lambda function

    #.  Right-click in the Eclipse code window, choose :guilabel:`AWS Lambda`, and then choose :guilabel:`Run Function on AWS Lambda`.

    #.  Choose the handler class you want to invoke.

    #.  In the input box, type a valid JSON string, such as "AWS Lambda".

        .. image:: images/lambda_tutorial_invoke_function.png
           :alt: Choosing a Lambda handler to invoke

        .. tip:: You can add new JSON input files to your project, and they will show up in this dialog
                 box if the file name ends with .json. You can use this feature to provide standard input files for your |LAM| functions.

    #.  The :guilabel:`Show Live Log` box is checked by default. This displays the logs from the |LAM|
        function output in the Eclipse :guilabel:`Console`.

    #.  Choose :guilabel:`Invoke` to send your input data to your |LAM| function. If you have
        set up everything correctly, you should see the return value of your function printed out in the
        Eclipse :guilabel:`Console` view (which automatically appears if it isn't already shown).

        .. image:: images/lambda_tutorial_success.png

Congratulations, you've just run your first |LAM| function directly from the Eclipse IDE!


Next Steps
==========

Now that you've uploaded and deployed your function, try changing the code and rerunning the
function. |LAM| automatically reuploads and invokes the function for you, and prints output to
the Eclipse :guilabel:`Console`.

More Info
=========

For more information about each of the pages that were covered in this tutorial, as well as a full
description of each option, see the :doc:`lambda-ref`.

For more information about |LAM| and about writing Java code for |LAM|, see
:lam-dg:`Authoring Lambda Functions in Java <lambda-java-how-to-create-deployment-package>` in the
|LAM-dg|.
