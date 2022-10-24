:original_name: en-us_topic_0056584626.html

.. _en-us_topic_0056584626:

Executing a Backup Policy at Once
=================================

You can manually execute a backup policy to back up an associated ECS immediately.

Context
-------

-  If an ECS is being backed up, you cannot manually execute a backup policy on it.
-  If a manual backup job is still in progress, scheduled automatic backup operations will be postponed to the next backup cycle. An interval of at least 3 hours is recommended between a manual backup operation and a scheduled automatic backup operation.

Prerequisites
-------------

At least one backup policy has been created and has been associated with at least one ECS.

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Policies** tab.
#. In the upper right corner of the backup policy you want to execute, choose **More** > **Backup Now**.
#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
