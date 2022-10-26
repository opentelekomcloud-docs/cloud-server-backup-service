:original_name: en-us_topic_0056584596.html

.. _en-us_topic_0056584596:

Scenarios
=========

CSBS supports one-off backup and periodic backup. A one-off backup job is manually created by users and takes effect for only one time. Periodic backup jobs are automatically driven by a user-defined backup policy.

:ref:`Table 1 <en-us_topic_0056584596__table31963779194543>` describes the two backup options.

.. _en-us_topic_0056584596__table31963779194543:

.. table:: **Table 1** One-off backup and periodic backup

   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Item                        | One-Off Backup                                                                                                                                                                                        | Periodic Backup                                                                                                                                |
   +=============================+=======================================================================================================================================================================================================+================================================================================================================================================+
   | Backup policy               | None                                                                                                                                                                                                  | Required                                                                                                                                       |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Number of backup operations | Only one, manual                                                                                                                                                                                      | Periodic operations driven by the backup policy                                                                                                |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Backup name                 | User-defined backup name, which defaults to **manualbk\_**\ *xxxx*                                                                                                                                    | System-assigned backup name, which defaults to **autobk\_**\ *xxxx*                                                                            |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Backup method               | Full backup at the first time and incremental backup subsequently, by default.                                                                                                                        | Full backup at the first time and incremental backup subsequently, by default.                                                                 |
   |                             |                                                                                                                                                                                                       |                                                                                                                                                |
   |                             | CSBS allows you to use any backup (no matter it is a full or incremental one) to restore the full data of a server.                                                                                   | CSBS allows you to use any backup (no matter it is a full or incremental one) to restore the full data of a server.                            |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+
   | Application scenario        | Executed before patching or upgrading the OS or upgrading an application on an ECS. A one-off backup can be used to restore an ECS to the original state in case the patching or upgrading fails.     | Executed for routine maintenance of an ECS. The latest backup can be used to restore an ECS in case an unexpected failure or data loss occurs. |
   |                             |                                                                                                                                                                                                       |                                                                                                                                                |
   |                             | Executed before patching or upgrading the OS or upgrading an application on a server. A one-off backup can be used to restore a server to the original state in case the patching or upgrading fails. |                                                                                                                                                |
   +-----------------------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+------------------------------------------------------------------------------------------------------------------------------------------------+

You can also use the two backup options together if needed. For example, associate all ECSs with a backup policy to execute periodic backup of all ECSs, and manually perform one-off backups for the most important ECSs to further ensure those ECSs' data security, as shown in :ref:`Figure 1 <en-us_topic_0056584596__fig6436164020634>`.

.. _en-us_topic_0056584596__fig6436164020634:

.. figure:: /_static/images/en-us_image_0067805744.png
   :alt: **Figure 1** Intermixed use of the two backup options

   **Figure 1** Intermixed use of the two backup options
