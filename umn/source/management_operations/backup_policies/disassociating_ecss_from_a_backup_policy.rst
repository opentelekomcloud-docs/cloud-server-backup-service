:original_name: en-us_topic_0056584632.html

.. _en-us_topic_0056584632:

Disassociating ECSs from a Backup Policy
========================================

When an ECS associated with a backup policy no longer needs to be backed up, you can disassociate it from the backup policy.

Prerequisites
-------------

-  You have created at least one backup policy.
-  The backup policy is associated with at least one ECS.

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Policies** tab.
#. In the row of the backup policy from which you want to disassociate the ECS, click |image2|.
#. Under **Associated Servers**, click **Disassociate** in the row of the target ECS, or select the target ECS from the list and then click **Disassociate** in the upper left corner of the list.

   .. note::

      -  When the target ECS is being backed up, you can still disassociate it. However, the backup job will continue and backups will be generated.
      -  After an ECS is disassociated from the associated backup policy, its existing backups will not be deleted. If you want to delete them, manually delete them.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
.. |image2| image:: /_static/images/en-us_image_0238025636.png
