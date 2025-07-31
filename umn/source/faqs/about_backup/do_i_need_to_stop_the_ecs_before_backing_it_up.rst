:original_name: en-us_topic_0056584623.html

.. _en-us_topic_0056584623:

Do I Need to Stop the ECS Before Backing It Up?
===============================================

No. CSBS allows you to back up ECSs that are in use. When a server is running, data is written into the EVS disks on the server, and some newly generated data is cached in the server memory. During a backup task, data in the memory will not be automatically written into disks, so the disk data and their backups may be inconsistent.

To ensure data integrity, you are advised to perform backup during off-peak hours when no data is written to the disks. For applications that require strict consistency, such as databases and email systems, you are advised to suspend all write operations before the backup. If write operations cannot be suspended, you can stop the application systems or the ECS for offline backup.
