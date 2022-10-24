:original_name: en-us_topic_0056584627.html

.. _en-us_topic_0056584627:

Can an ECS Be Restored Using Its Backups After It Has Been Changed?
===================================================================

Yes. If an ECS has been backed up and changed such as adding, deleting, or expanding EVS disks, its backups can still be used to restore data. You are advised to back up data again after the change.

If you have added an EVS disk after backup, using the backup to restore data will not change the data on the EVS disk.

If you have deleted an EVS disk after backup, using the backup to restore data will not include the data on the EVS disk.
