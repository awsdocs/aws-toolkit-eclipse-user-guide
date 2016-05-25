.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

################################################
Associate Private Keys with Your |EC2| Key Pairs
################################################

The |tke| can obtain your |EC2| key pairs from AWS. However, you will need to associate private keys
to use them with the |tke|.

**To view your Amazon EC2 key pairs in the AWS Toolkit for Eclipse and associate private keys with them**

1.  Open Eclipse's :guilabel:`Preferences` dialog box and click the triangle next to :guilabel:`AWS
    Toolkit` in the sidebar to show additional categories of |tke| settings.

    .. image:: images/tke-preferences-node.png

2.  Select :guilabel:`Key Pairs`.

    Eclipse displays a scrollable list of your key pairs. If a key pair has a red :guilabel:`X` next
    to it, you will need to associate a private key with the key pair to use it.

    .. image:: images/tke-preferences-keypairs.png

3.  Right-click the key pair and, from the context menu, select :guilabel:`Select Private Key
    File...`

    .. image:: images/tke-preferences-select-private-key-file.png

4.  Navigate to the private key file and select it to associate it with your key pair.

