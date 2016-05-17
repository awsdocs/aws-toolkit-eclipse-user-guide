.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

################################
Building an AWS Java Application
################################

In this section, we'll use the |tke| to build and run a local Java application that accesses AWS
resources.

The |tke| includes the |sdk-java| and a number of Java sample programs. The |tke| makes it easy to
build and run any of these samples. To demonstrate how the |tke| can help you build and run AWS
applications in Java, we'll use the :emphasis:`AmazonSimpleQueueService` sample as an example. The
AWS Explorer that is provided with the |tke| can be used to view the running |SQS| queue.

.. note:: The |sdk-java| samples are provided in the :file:`samples` directory in the SDK download,
   and can also be viewed on :github:`GitHub <aws-sdk-java/tree/master/src/samples>`.  For more
   information about the |sdk-java| itself, view the |sdk-java-dg|_.


.. _buid_run_sqs_sample:

Build and Run the |SQSlong| Sample
==================================

**To build and run the Amazon Simple Queue Service sample**

#.  Click the AWS icon on the Eclipse toolbar, and then click :guilabel:`New AWS Java Project`.

#.  In the dialog box that appears, type a name for the project in the :guilabel:`Project name` box
    and select :guilabel:`Amazon Simple Queue Service Sample`.

    .. image:: images/tke-aws-java-project.png

#.  Click :guilabel:`Finish`.

#.  The sample application appears in :guilabel:`Project Explorer`. Expand the tree view for this
    project.

#.  Beneath the :guilabel:`src` node, double-click the :file:`SimpleQueueService.java` source file
    to open it in the editor pane. Locate the following line:

    .. code-block:: java

        System.out.println("Receiving messages from MyQueue.\n");

#.  Right-click in the left margin of the editor pane, and select :guilabel:`Toggle Breakpoint`.

#.  Right-click the project node in :guilabel:`Project Explorer` |mdash| in our example, this would
    be the node named :userinput:`myJavaSqsApp` |mdash| then click :guilabel:`Debug As` >
    :guilabel:`Java Application`.

#.  In the :guilabel:`Select Java Application` dialog box, select the SQS application and then click
    :guilabel:`OK`.

#.  When the application stops at the breakpoint, Eclipse will ask if it should switch to the Debug
    perspective. Click :guilabel:`No` (the Debug perspective does not include AWS Explorer).

#.  Go to :guilabel:`AWS Explorer` and expand the :guilabel:`Amazon SQS` node.

#.  Double-click :guilabel:`MyQueue` and view the contents of the queue that was created by the Java
    client application.

    .. image:: images/tke-aws-explorer-sqs-queue.png

#.  Press :userinput:`F8`. The Java client application will continue running and terminate normally.

#.  Refresh the view in :guilabel:`AWS Explorer`. You will see that the :guilabel:`MyQueue` queue is
    no longer present; the application deletes the queue before the application exits.

.. note:: If you run this sample application repeatedly, you should wait at least 60 seconds between
    subsequent runs. |SQS| requires that at least 60 seconds elapse after deleting a queue before
    creating a queue with the same name.

