.. Copyright 2010-2016 Amazon.com, Inc. or its affiliates. All Rights Reserved.

   This work is licensed under a Creative Commons Attribution-NonCommercial-ShareAlike 4.0
   International License (the "License"). You may not use this file except in compliance with the
   License. A copy of the License is located at http://creativecommons.org/licenses/by-nc-sa/4.0/.

   This file is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND,
   either express or implied. See the License for the specific language governing permissions and
   limitations under the License.

###############################
Connecting to |RDSlong| (|RDS|)
###############################

In this section, we'll use the |tke| to connect to a database instance on the |RDSlong| (|RDS|).
Before stepping through the process described below, you will need to have an RDS database instance
associated with your AWS account. You can create a database instance on RDS using the |console|_.
When you create a database instance, set the TCP port that the database uses to receive connections
to a value that is accessible from your location. For example, if you are behind a firewall, choose
a TCP port to which your firewall allows connections. For more information, see the |RDS-ug|_.

1.  In :guilabel:`AWS Explorer`, expand the :guilabel:`Amazon RDS` node. You should see a list of
    the database instances that are associated with your AWS account. Right-click one of these
    instances, and then click :guilabel:`Connect` .

    .. figure:: images/tke-rds-aws-explorer-connect.png
        :scale: 50%

        Connect in context menu in AWS Explorer

2.  The |tke| displays an authentication dialog box. Enter the master password that you specified
    when you created the database instance. Click :guilabel:`Finish`.

    .. figure:: images/tke-rds-auth.png
        :scale: 50%

        Authenticate against the database instance

3.  The |tke| brings up the connection to the database instance in the Eclipse Data Source Explorer.
    From here, you can inspect the structure and data in the database.

    .. figure:: images/tke-rds-data-source-explorer.png
        :scale: 50%

        Data Source Explorer

