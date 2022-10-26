:original_name: en-us_topic_0056584638.html

.. _en-us_topic_0056584638:

Associating ECSs with a Backup Policy
=====================================

After creating a backup policy, you can add ECSs to it so that the ECSs are associated with the backup policy.

Prerequisites
-------------

-  You have created at least one backup policy.
-  At least one ECS in the **Running** or **Stopped** state is available.
-  A maximum of 64 ECSs can be associated with a backup policy.

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Policies** tab.

#. In the row of the backup policy with which you want to associate ECSs, click **Associate Server**.


   .. figure:: /_static/images/en-us_image_0164878450.png
      :alt: **Figure 1** Associating servers

      **Figure 1** Associating servers

#. In the server list, select the ECSs you want to associate. After ECSs are selected, they are added to the list of selected servers.

   .. note::

      -  A maximum of 64 ECSs can be associated with a backup policy.
      -  If a selected ECS has been associated with another backup policy, it will be disassociated from the original backup policy automatically and then associated with the new backup policy.
      -  If EVS disks on an ECS have been associated with a VBS backup policy, disassociate them from the VBS backup policy. Otherwise, two backups are generated for each of the EVS disks.
      -  You can only select ECSs that are in the **Running** or **Stopped** state.
      -  CSBS supports backing up ECSs with shared EVS disks.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
