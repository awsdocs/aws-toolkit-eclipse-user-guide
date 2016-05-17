.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

#######################################
Validating an |CFN| Template in Eclipse
#######################################

**To validate an CloudFormation template in Eclipse**

* Perform either one of the following actions:

    *   Right-click the template name in the :guilabel:`Package Explorer` view and click
        :guilabel:`Validate` on the context menu.

        .. image:: images/tke-cfn-editor-validate-template-1.png
            :scale: 50%

    *   Right-click the template that you are editing in the editor pane and click
        :guilabel:`Validate` on the context menu.

        .. image:: images/tke-cfn-editor-validate-template-2.png
            :scale: 50%

.. important:: Your template will be validated for :emphasis:`JSON correctness` only; it will not be
   validated for :emphasis:`CloudFormation correctness`. A stack template validated in this way can
   still fail to launch or update.

