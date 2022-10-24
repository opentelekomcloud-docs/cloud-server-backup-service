:original_name: en-us_topic_0056725842.html

.. _en-us_topic_0056725842:

CSBS
====

Cloud Server Backup Service (CSBS) enables you to back up Elastic Cloud Servers (ECSs). It works based on the consistency snapshot technology for disks. With CSBS, you can seamlessly use backup data to restore ECS data.

CSBS enhances data integrity and service continuity. For example, if an ECS is faulty or a misoperation causes data loss, you can use data backups to restore data quickly.

By default, CSBS executes a full backup for an ECS that has not been backed up, and performs incremental backups subsequently. Both full backup and incremental backup can restore an ECS to the state at the backup point in time.

CSBS works with ECS and OBS to back up ECS data to object storage, enhancing backup data security. :ref:`Figure 1 <en-us_topic_0056725842__fig11831525164545>` shows the CSBS product architecture.

.. _en-us_topic_0056725842__fig11831525164545:

.. figure:: /_static/images/en-us_image_0067805991.png
   :alt: **Figure 1** CSBS product architecture


   **Figure 1** CSBS product architecture

Main Functions
--------------

CSBS provides the following functions:

-  Policy-driven data backup
-  Data backup management
-  Image creation using backups
