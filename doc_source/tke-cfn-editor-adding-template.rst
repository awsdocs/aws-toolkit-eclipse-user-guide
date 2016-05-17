.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

############################################################
Adding and Accessing |CFN| Templates in Your Eclipse Project
############################################################

**To add a CloudFormation template to your Eclipse project**

1. Locate the template you'd like to add to your project in your system's file manager, and drag the
   file into your project's :guilabel:`Package Explorer` window.

   .. image:: images/tke-cfn-editor-add-template.png
      :scale: 50

2. Choose how you would like to add the file to your project, and click :guilabel:`OK`.

   .. image:: images/tke-cfn-editor-add-template-2.png
      :scale: 50

**To access a CloudFormation template in your Eclipse project**

* Double-click the template name in :guilabel:`Package Explorer` to begin editing the file.

  .. image:: images/tke-cfn-editor-edit-template.png
     :scale: 50

.. note:: Files that end with :code:`.template` or :code:`.json` will automatically use the |CFN| template
    editor. If your file is not automatically recognized as an |CFN| template, you can select the
    editor by right-clicking the file name in :guilabel:`Package Explorer` or by right-clicking in
    the editor window with the file loaded, selecting :guilabel:`Open With`, then
    :guilabel:`CloudFormation Template Editor`

    .. image:: images/tke-cfn-editor-open-with.png
       :scale: 50

