:original_name: en-us_topic_0089772265.html

.. _en-us_topic_0089772265:

Can an ECS with Application Systems Be Backed Up?
=================================================

Yes, it can be backed up. To back up applications requiring strict consistency, such as databases and email systems, you are advised to suspend all write operations and then perform backup. If write operations cannot be suspended, you can stop the application systems or the ECS for offline backup. Without doing these, status of the ECS after restoration is similar to restart upon an unexpected power failure and log rollback will be performed on databases to keep data consistent.
