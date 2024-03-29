:original_name: en-us_topic_0056725844.html

.. _en-us_topic_0056725844:

Related Services
================

.. table:: **Table 1** Related services

   +-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+--------------------------------------------------------------------------------+
   | Interactive Function                                                                                                                                                                                        | Related Service              | Reference                                                                      |
   +=============================================================================================================================================================================================================+==============================+================================================================================+
   | CSBS can back up data of the EVS disks on an ECS, and use the backups to restore lost or corrupted data. Generated backups can be used to create images for fast restoring the service running environment. | Elastic Cloud Server (ECS)   | :ref:`Creating a CSBS Backup <en-us_topic_0072046354>`                         |
   +-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+--------------------------------------------------------------------------------+
   | CSBS combines ECS and OBS to back up ECS data to object storage, enhancing backup data security.                                                                                                            | Object Storage Service (OBS) | :ref:`CSBS <en-us_topic_0056725842>`                                           |
   +-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+--------------------------------------------------------------------------------+
   | Cloud Trace Service (CTS) records operations of CSBS resources, facilitating query, audit, and backtracking.                                                                                                | Cloud Trace Service (CTS)    | :ref:`Events <en-us_topic_0056584634>`                                         |
   +-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+--------------------------------------------------------------------------------+
   | CSBS and VBS both provide data backup protection. :ref:`Table 2 <en-us_topic_0056725844__table1965919985417>` describes the differences between CSBS and VBS.                                               | Volume Backup Service (VBS)  | :ref:`What Are the Differences Between CSBS and VBS? <en-us_topic_0086428372>` |
   +-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------+--------------------------------------------------------------------------------+

.. _en-us_topic_0056725844__table1965919985417:

.. table:: **Table 2** CSBS and VBS

   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Item                           | CSBS                                                                                                                                            | VBS                                                                                           |
   +================================+=================================================================================================================================================+===============================================================================================+
   | Backup and restoration objects | All EVS disks (including system and data disks) on a single ECS                                                                                 | One or more specified EVS disks (system or data disks)                                        |
   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Recommended scenarios          | An entire ECS needs to be protected.                                                                                                            | Only data disks need to be backed up, because the system disk does not contain personal data. |
   |                                |                                                                                                                                                 |                                                                                               |
   |                                | Use images created using backups to fast restore the service running environment.                                                               |                                                                                               |
   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
   | Advantages                     | Consistency backup is supported. You can back up all EVS disks simultaneously, eliminating data inconsistency caused by backup time difference. | Backup cost is reduced while maintaining data security.                                       |
   +--------------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------------------------------------------------------------------------------+
