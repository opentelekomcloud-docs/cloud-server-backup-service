:original_name: en-us_topic_0089772264.html

.. _en-us_topic_0089772264:

What Is Consistent Backup?
==========================

There are three types of backup consistency:

-  Inconsistent backup: During a backup, files and disks of an ECS are not backed up at the exact same time.
-  Crash-consistent backup: During a backup, files and disks of an ECS are backed up at the exact same point in time, while applications such as databases are not quiesced and memory data is not backed up. Therefore, application consistency is not ensured.
-  Application-consistent backup: During a backup, files and disks on the same ECS are backed up at the exact same point in time, and databases are quiesced and memory data is refreshed to ensure application consistency.
