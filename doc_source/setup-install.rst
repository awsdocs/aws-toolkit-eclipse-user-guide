.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

.. meta::
    :description: Install the |tke|.
    :keywords: tke, install, upgrade, setup

##################
Set up the Toolkit
##################

This section desribes how to install or upgrade the |tke|.

Prerequisites
=============

The |tke| has the following prerequisites:

* *An Amazon Web Services account* |ndash| To obtain an AWS account, go to the `AWS home page
  <https://aws.amazon.com/>`_ and click :guilabel:`Sign Up Now`. Signing up will enable you to use
  all of the services offered by AWS.

* *A supported operating system* |ndash| The |tke| is supported on Windows, |unixes|.

* *Java 1.8*

* *Eclipse IDE for Java Developers 4.2 or later* |ndash| We attempt to keep the |tke| current with
  the default version available on the `Eclipse download page <https://eclipse.org/downloads/>`_.

  .. tip:: Eclipse provides a number of different downloads. We recommend installing the
     :emphasis:`Eclipse IDE for Enterprise Java Developers`, which includes the `Eclipse Web Tools Platform
     <https://projects.eclipse.org/projects/webtools>`_ required by |EB|, the `Eclipse Data
     Tools Platform <http://www.eclipse.org/datatools/>`_ required for |SDB| features, the `Eclipse EGit <http://www.eclipse.org/egit/>`_, and the `M2Eclipse <http://www.eclipse.org/m2e/>`_. If you
     install another version of Eclipse, make sure that you have (or that you install, using the
     provided links) support for these features.

* *(Optional) Google Android Development Tools (ADT)* |ndash| if you want |tke| support for the
  |sdk-android|_, you must `install the ADT
  <https://developer.android.com/studio/tools/sdk/eclipse-adt.html>`_ first.

.. _install-tke:

Install the |tke|
=================

.. topic:: To install the AWS Toolkit for Eclipse

    #.  Within Eclipse, click :guilabel:`Help` and then click :guilabel:`Install New Software`.

    #.  In the :guilabel:`Work with` box, type |eclipse-update-url| and then press :kbd:`Enter`.

    #.  Choose the components of the |tke| that you want to install. Click :guilabel:`Select All` to
        install all components at once.

        .. note::

           * *AWS Toolkit for Eclipse Core* (in the *AWS Core Management Tools* section) is
             **required**; all other components are optional.

           * Support for the |sdk-android|_ *requires* that you have the Google Android Developer
             Tools (ADT) for Eclipse installed first. If you have not yet installed the ADT, make
             sure that :guilabel:`AWS SDK for Android` is *unchecked*, or installation will fail.

           * Support for the |RDS| or |SDB| managers requires that the *Eclipse Data Tools Platform*
             (DTP) is installed. The DTP is installed by default with the "Java EE Developers"
             version of Eclipse, or can be `installed separately
             <https://eclipse.org/datatools/downloads.php>`_.

    #.  Once you have made your selections, click :guilabel:`Next` (or :guilabel:`Finish`) to
        complete installation.

Once you have set up the |tke| you should :doc:`configure your AWS Credentials <setup-credentials>`.

.. note:: Depending on the options selected, and on factors such as network speed, server latency
   and system capabilities, it may take up to 30 minutes for the installation to complete.


Upgrade the |tke|
=================

To upgrade or reinstall the |tke|, use the same instructions for :ref:`installing the toolkit
<install-tke>`.

Some versions of Eclipse, (notably *Mars* and *Neon*), may fail to fetch the latest artifacts due to
a bug in old versions of the `Oomph plugin <https://projects.eclipse.org/projects/tools.oomph>`_. To
work around this issue:

#. Make sure that you're using :code:`https://aws.amazon.com/eclipse/site.xml` as the |tke| update
   site.

#. Delete the :file:`~/.eclipse/org.eclipse.oomph.p2/cache/` directory to remove cached content.

#. Install the latest version of `Oomph (Eclipse Installer)
   <https://wiki.eclipse.org/Eclipse_Installer>`_.

