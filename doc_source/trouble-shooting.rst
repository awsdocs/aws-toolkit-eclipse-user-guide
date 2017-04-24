.. Copyright 2010-2017 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

################
Trouble Shooting
################

AWS CodeCommit plugin -  Eclipse was unable to write to the secure store.
=========================================================================

*Problem:* when checking out or checking in an AWS CodeCommit repository, I got an error saying
*Writing to secure store failed, No password provided.*

*Solution:* Open up :emphasis:`Preferences` -> :emphasis:`General` -> :emphasis:`Security` ->
:emphasis:`Security Storage` -> :emphasis:`Contents` -> :emphasis:`GIT` -> :emphasis:`Delete`.
