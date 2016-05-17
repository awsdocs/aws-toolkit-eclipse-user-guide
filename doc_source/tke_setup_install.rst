.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

####################
Installing the |tke|
####################

**To install the AWS Toolkit for Eclipse from the AWS website using the Eclipse user interface**

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

Once you have set up the |tke| you should :doc:`configure your AWS Credentials <tke_setup_creds>`.

.. note:: Depending on the options selected, and on factors such as network speed, server latency
   and system capabilities, it may take up to 30 minutes for the installation to complete.
