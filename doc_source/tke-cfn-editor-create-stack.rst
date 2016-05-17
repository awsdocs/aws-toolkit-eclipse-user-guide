.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

######################################
Deploying an |CFN| Template in Eclipse
######################################

.. note:: At this time, only files that end in :code:`.template` can be launched from the Eclipse IDE. If
    your file ends with another extension, such as :code:`.json`, you will need to rename it first
    with a :code:`.template` extension to use this feature.

**To deploy an CloudFormation template from Eclipse**

1.  With your |CFN| :code:`.template` file open in the |CFN| template editor (see
    :doc:`tke-cfn-editor-adding-template` for more information), right-click on the open template
    and select :guilabel:`Run on AWS`, then :guilabel:`Create Stack` on the context menu.

    .. image:: images/tke-cfn-editor-create-stack.png
        :scale: 50%

2.  In the :guilabel:`Create New CloudFormation Stack` dialog, enter your stack name in the
    :guilabel:`Stack Name` field. Your template file should be automatically chosen in the
    :guilabel:`Template File` field.

    .. image:: images/tke-cfn-editor-create-stack-dlg.png
        :scale: 50%

3.  Choose any (or none) of the following options:

    .. include:: tke-cfn-launch-options.txt

4.  Click :guilabel:`Next` to continue with entering parameter values.

5.  If your stack has parameters, you will enter values for them next. For parameters with a
    predefined list of possible responses, you can choose a value from the list provided.

    .. image:: images/tke-cfn-editor-create-stack-dlg-params.png
        :scale: 50%

6.  Click :guilabel:`Finish` to begin launching your stack.

While your stack is being launched, you can view its status by double-clicking the stack name
beneath the :guilabel:`CloudFormation` node in the :guilabel:`AWS Explorer` view, or by
right-clicking the stack name and selecting :guilabel:`Open in Stack Editor` on the context menu.

.. image:: images/tke-cfn-editor-stack-events.png
    :scale: 50%

.. note:: If you cannot see the stack you launched in :guilabel:`AWS Explorer`, you may need to manually
    refresh the view by clicking the :guilabel:`Refresh AWS Explorer` icon at the top of the
    :guilabel:`AWS Explorer` view.

    .. image:: images/tke-cfn-editor-refresh-view.png
        :scale: 50%

