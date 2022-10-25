:original_name: en-us_topic_0072046354.html

.. _en-us_topic_0072046354:

Creating a CSBS Backup
======================

This section explains how to create CSBS backup jobs to protect ECS data.

Prerequisites
-------------

-  If you want to use a backup to create an image, perform the following operations before creating a CSBS backup:

   -  You have optimized the Linux ECS (referring to `(Optional) Optimizing a Linux Private Image <https://docs.otc.t-systems.com/usermanual/ims/en-us_topic_0047501133.html>`__) and installed Cloud-Init (referring to `Installing Cloud-Init <https://docs.otc.t-systems.com/usermanual/ims/en-us_topic_0030730603.html>`__).
   -  You have optimized the Windows ECS (referring to `(Optional) Optimizing a Windows Private Image <https://docs.otc.t-systems.com/usermanual/ims/en-us_topic_0047501112.html>`__) and installed Cloudbase-Init (referring to `Installing Cloudbase-Init <https://docs.otc.t-systems.com/usermanual/ims/en-us_topic_0030730602.html>`__).

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. In the upper right corner of the page, click **Create CSBS Backup**.

#. In the ECS list, select the ECSs you want to back up. After ECSs are selected, they are added to the list of selected ECSs. See :ref:`Figure 1 <en-us_topic_0072046354__fig7683103644515>`.

   .. _en-us_topic_0072046354__fig7683103644515:

   .. figure:: /_static/images/en-us_image_0164859557.png
      :alt: **Figure 1** Selecting servers

      **Figure 1** Selecting servers

   .. note::

      -  The selected ECSs must be in the **Running** or **Stopped** state.
      -  ECSs with shared EVS disks can be backed up.

#. In the **Configure Backup** area, configure a backup scheme for the selected servers. See :ref:`Figure 2 <en-us_topic_0072046354__fig599112219464>`.

   .. _en-us_topic_0072046354__fig599112219464:

   .. figure:: /_static/images/en-us_image_0152874351.png
      :alt: **Figure 2** Configuring backup schemes

      **Figure 2** Configuring backup schemes

   -  **Auto Backup**:

      In the **Backup Policy** drop-down list, select a backup policy. Alternatively, click **Create Policy** to create a backup policy. For details about the parameters of a backup policy, see :ref:`Creating a Backup Policy <en-us_topic_0056584629>`.

      After a backup job is created, the selected ECSs are associated with the backup policy and will be periodically backed up according to the backup policy.

      .. note::

         If a selected ECS has been associated with another backup policy, it will be disassociated from the original backup policy automatically and then associated with the new backup policy.

   -  **Immediate Backup**:

      After a backup job is created, all selected ECSs will be backed up immediately for once.

      Set the **Name** and **Description** of the backup, as described in :ref:`Table 1 <en-us_topic_0072046354__table4829135361311>`.

      .. _en-us_topic_0072046354__table4829135361311:

      .. table:: **Table 1** Parameter description

         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Parameter             | Description                                                                                                                                       | Remarks               |
         +=======================+===================================================================================================================================================+=======================+
         | Name                  | Name of the backup you are creating.                                                                                                              | manualbk_cbf0         |
         |                       |                                                                                                                                                   |                       |
         |                       | It is a string of 1 to 255 characters that can contain only digits, letters, underscores (_), and hyphens (-).                                    |                       |
         |                       |                                                                                                                                                   |                       |
         |                       | .. note::                                                                                                                                         |                       |
         |                       |                                                                                                                                                   |                       |
         |                       |    You can use the default name, which is in the format of **manualbk\_**\ *xxxx*.                                                                |                       |
         |                       |                                                                                                                                                   |                       |
         |                       |    If multiple ECSs are to be backed up, the system automatically adds suffixes to their names, for example, **backup-0001** and **backup-0002**. |                       |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
         | Description           | Supplementary information about the backup.                                                                                                       | --                    |
         |                       |                                                                                                                                                   |                       |
         |                       | It cannot exceed 255 characters.                                                                                                                  |                       |
         +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

   You can select both the backup methods at the same time.

#. Determine whether to select **Enable** next to **Full Backup**. If **Full Backup** is enabled, the generated full backup and later generated incremental backups will support :ref:`Instant Restore <en-us_topic_0056725845__section181448505477>`. See :ref:`Figure 3 <en-us_topic_0072046354__fig21211503353>`.

   .. _en-us_topic_0072046354__fig21211503353:

   .. figure:: /_static/images/en-us_image_0127861516.png
      :alt: **Figure 3** Enabling Full Backup or not

      **Figure 3** Enabling Full Backup or not

#. Add tags to the backup. (This operation is optional if you select **Immediate Backup**.)

   A tag is represented in the form of a key-value pair. Tags are used to identify, classify, and search for cloud resources. These tags are used to filter and manage backup resources only. A backup can have a maximum of 10 tags.

   See :ref:`Figure 4 <en-us_topic_0072046354__fig09521715453>`.

   .. _en-us_topic_0072046354__fig09521715453:

   .. figure:: /_static/images/en-us_image_0164859985.png
      :alt: **Figure 4** Adding a tag

      **Figure 4** Adding a tag

   :ref:`Table 2 <en-us_topic_0072046354__table191162312815>` describes parameters of a tag.

   .. _en-us_topic_0072046354__table191162312815:

   .. table:: **Table 2** Parameter description

      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Parameter             | Description                                                                                                                                                    | Example Value         |
      +=======================+================================================================================================================================================================+=======================+
      | Key                   | Tag key. Each tag of a backup has a unique key. The key of a tag is user-definable or is selected from those of existing tags in Tag Management Service (TMS). | Key_0001              |
      |                       |                                                                                                                                                                |                       |
      |                       | The naming rule of a tag key is as follows:                                                                                                                    |                       |
      |                       |                                                                                                                                                                |                       |
      |                       | -  It ranges from 1 to 36 Unicode characters.                                                                                                                  |                       |
      |                       |                                                                                                                                                                |                       |
      |                       | -  It can contain only letters, digits, hyphens (-), and underscores (_).                                                                                      |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
      | Value                 | Tag value. Tag values can be repetitive or null.                                                                                                               | Value_0001            |
      |                       |                                                                                                                                                                |                       |
      |                       | The naming rule of a tag value is as follows:                                                                                                                  |                       |
      |                       |                                                                                                                                                                |                       |
      |                       | -  It ranges from 0 to 43 Unicode characters.                                                                                                                  |                       |
      |                       |                                                                                                                                                                |                       |
      |                       | -  It can contain only letters, digits, hyphens (-), and underscores (_).                                                                                      |                       |
      +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

#. Click **Create Now**.

#. On the **Confirm** page, confirm resource details and click **Submit**.

#. Return to the CSBS page as prompted.

   -  Auto Backup

      On the **Policies** tab page, click |image2| on the left of the backup policy name. If all selected ECSs are displayed under **Associated Servers**, they are associated with the backup policy successfully, and automatic backup will be periodically performed as scheduled.

   -  Immediate Backup

      On the **Backups** tab page, if the generated backups are in the **Available** state, the one-off backup job is successful.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
.. |image2| image:: /_static/images/en-us_image_0238025636.png
