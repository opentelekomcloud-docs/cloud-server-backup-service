:original_name: en-us_topic_0056584634.html

.. _en-us_topic_0056584634:

Events
======

In CSBS, you can use Cloud Trace Service (CTS) to trace operations in CSBS.

Prerequisites
-------------

CTS has been enabled.

Key Operations Recorded by CTS
------------------------------

.. table:: **Table 1** CSBS operations that can be recorded by CTS

   +--------------------------------------------------+----------------+---------------------------------------+
   | Operation                                        | Resource Type  | Trace Name                            |
   +==================================================+================+=======================================+
   | Creating a backup policy                         | backupPolicy   | createBackupPolicy                    |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Updating a backup policy                         | backupPolicy   | updateBackupPolicy                    |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Deleting a backup policy                         | backupPolicy   | deleteBackupPolicy                    |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Binding resources                                | backupPolicy   | bindResources                         |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Executing a backup                               | checkpointItem | createCheckpoint                      |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Restoring a backup                               | checkpointItem | restoreCheckpointItem                 |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Deleting a backup                                | checkpointItem | deleteCheckpointItem                  |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Backing up an ECS                                | cloudServer    | backupCloudServer                     |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Deleting a task                                  | operationLog   | deleteOperationLog                    |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Batch adding or deleting tags of a backup        | checkpointItem | batchCreateOrDeleteCheckpointItemTags |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Adding a backup tag                              | checkpointItem | createCheckpointItemTag               |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Deleting a backup tag                            | checkpointItem | deleteCheckpointItemTag               |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Batch adding or deleting tags of a backup policy | backupPolicy   | batchCreateOrDeleteBackupPolicyTags   |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Adding a backup policy tag                       | backupPolicy   | createBackupPolicyTag                 |
   +--------------------------------------------------+----------------+---------------------------------------+
   | Deleting a backup policy tag                     | backupPolicy   | deleteBackupPolicyTag                 |
   +--------------------------------------------------+----------------+---------------------------------------+

View Audit Logs
---------------

For details about how to view audit logs, see section **Querying Traces** in the *Cloud Trace Service User Guide.*

Disabling or Enabling a Tracker
-------------------------------

This section describes how to disable an existing tracker on the CTS console. After the tracker is disabled, the system will stop recording operations, but you can still view existing operation records.

#. Log in to the management console.
#. Click |image1| in the upper left corner and select a region and project.
#. Click **Service List** and choose **Management & Deployment** > **Cloud Trace Service**.
#. Click **Tracker** in the left pane.
#. Click **Disable** on the right of the tracker information.
#. Click **OK**.
#. After the tracker is disabled, its status changes from **Disable** to **Enable**. To enable the tracker again, click **Enable** and then click **OK**. The system will start recording operations again.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
