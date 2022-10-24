:original_name: en-us_topic_0056725845.html

.. _en-us_topic_0056725845:

Basic Concepts
==============

Backup Policies
---------------

A backup policy is a set of rules for backing up data, including the policy name, policy status, execution time of backup jobs, backup period, and retention rules. The retention rules specify the retention duration and number of retained backups. After an ECS is associated with a backup policy, it can be automatically backed up according to the backup policy.

Backup
------

A backup is a copy of the original data that is backed up. A backup is used to restore the original data. It can be generated in a one-off or periodic method.

CSBS supports one-off backup and periodic backup. A one-off backup job is manually created by users and takes effect for only one time. Periodic backup jobs are automatically driven by a user-defined backup policy.

-  The name of a one-off backup is **manualbk\_**\ *xxxx*. It can be user- or system-defined.
-  The name of a periodic backup is assigned automatically by the system. The name of a periodic backup is **autobk\_**\ *xxxx*.

.. _en-us_topic_0056725845__section181448505477:

Instant Restore
---------------

Instant Restore restores ECS data and creating images for backups, which is much faster than normal restoration.

Backups generated before Instant Restore is enabled do not support instant restoration. To use the feature, perform a full backup and select **Enable** next to **Full Backup** when creating the backup. For details, see :ref:`Creating a CSBS Backup <en-us_topic_0072046354>`. After Instant Restore is enabled, manual backups for ECSs that have not been backed up automatically support instant restoration, without requiring the selection of **Enable** next to **Full Backup**.

No matter whether an ECS has been backed up or not, its automatic backups generated after Instant Restore is enabled do not support instant restoration, unless you manually perform a full backup on it.

Enhanced backup
---------------

Backups whose backup type is **Common backup** do not support Instant Restore. Backups whose backup type is **Enhanced backup** support Instant Restore.

Project
-------

Projects are used to group and isolate OpenStack resources (computing, storage, and network resources). A project can be a department or a project team. Multiple projects can be created for one account.
