.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

##################
Set up the Toolkit
##################

.. contents::
    :local:

Prerequisites
=============

The |tke| has the following prerequisites:

* :emphasis:`An Amazon Web Services account` |ndash| To obtain an AWS account, go to the `AWS home
  page <http://aws.amazon.com/>`_ and click :guilabel:`Sign Up Now`. Signing up will enable you to
  use all of the services offered by AWS.

* :emphasis:`A supported operating system` |ndash| The |tke| is supported on Windows, |unixes|.

* :emphasis:`Java 1.6 or later`

* :emphasis:`Eclipse IDE for Java Developers 3.6 or later` |ndash| We attempt to keep the |tke|
  current with the default version available on the `Eclipse download page
  <https://eclipse.org/downloads/>`_.

  .. tip:: Eclipse provides a number of different downloads. We recommend installing the
      :emphasis:`Eclipse IDE for Java EE Developers`, which includes the `Eclipse Web Tools Platform
      <http://www.eclipse.org/projects/project_summary.php?projectid=webtools>`_ required by |EB|,
      and the `Eclipse Data Tools Platform <http://www.eclipse.org/datatools/>`_ required for |SDB|
      features. If you install another version of Eclipse, make sure that you have (or that you
      install, using the provided links) support for these features.

* :emphasis:`(Optional) Google Android Development Tools (ADT)` |ndash| if you want |tke| support
  for the `AWS SDK for Android <http://aws.amazon.com/sdkforandroid/>`_, you must `install the ADT
  <https://developer.android.com/sdk/installing/installing-adt.html>`_ first.

.. _install-tke:

Install the |tke|
=================

**To install the AWS Toolkit for Eclipse**

#.  Start Eclipse.

#.  Click :guilabel:`Help` and then click :guilabel:`Install New Software`.

#.  In the :guilabel:`Work with` box, type |eclipse-update-url| and then press :kbd:`Enter`.

#.  Choose the components of the |tke| that you want to install. If you want to install *all*
    components, click :guilabel:`Select All`. Also note:

    * *AWS Toolkit for Eclipse Core* (in the *AWS Core Management Tools* section) is **required**;
      all other components are optional.

    * Support for the `AWS SDK for Android <http://aws.amazon.com/sdkforandroid/>`_
      :emphasis:`requires` that you have the Google Android Developer Tools (ADT) for Eclipse
      installed first. If you have not yet installed the ADT, make sure that *AWS SDK for Android*
      is :emphasis:`unchecked`, or installation will fail.

    * Support for the |RDS| or |SDB| managers requires that the *Eclipse Data Tools Platform* (DTP)
      is installed. The DTP is installed by default with the "Java EE Developers" version of
      Eclipse, or can be `installed separately <https://eclipse.org/datatools/downloads.php>`_.

#.  Once you have made your selections, click :guilabel:`Next` (or :guilabel:`Finish`) to complete
    installation.

Once you have set up the |tke| you should :doc:`configure your AWS Credentials <setup-credentials>`.

.. note:: Depending on the options selected, and on factors such as network speed, server latency
   and system capabilities, it may take up to 30 minutes for the installation to complete.

