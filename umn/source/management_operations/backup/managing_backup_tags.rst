:original_name: en-us_topic_0103696541.html

.. _en-us_topic_0103696541:

Managing Backup Tags
====================

You can add tags to a backup as well as edit and delete these tags. These tags are used to filter and manage backup resources only.

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Backups** tab. Locate the ECS backup. For details, see :ref:`Viewing a Backup <en-us_topic_0056584642>`.

#. Click |image2| on the left of a backup name to view details about the backup.

#. Click **Tags** in the details area to expand the tag management panel.

   The panel displays all tags of the backup.

   -  Adding a tag

      a. Click **Add Tag** in the upper left corner.

      b. In the dialog box displayed, set the key and value of the new tag.

         A tag is represented in the form of a key-value pair. Tags are used to identify, classify, and search for cloud resources. These tags are used to filter and manage backup resources only. A backup can have a maximum of 10 tags.

         :ref:`Table 1 <en-us_topic_0103696541__table191162312815>` describes parameters of a tag.

         .. _en-us_topic_0103696541__table191162312815:

         .. table:: **Table 1** Parameter description

            +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
            | Parameter             | Description                                                                                                                           | Example Value         |
            +=======================+=======================================================================================================================================+=======================+
            | Key                   | Tag key. Each tag of a backup has a unique key. The key of a tag is user-definable or is selected from those of existing tags in TMS. | Key_0001              |
            |                       |                                                                                                                                       |                       |
            |                       | The naming rule of a tag key is as follows:                                                                                           |                       |
            |                       |                                                                                                                                       |                       |
            |                       | -  It ranges from 1 to 36 Unicode characters.                                                                                         |                       |
            |                       |                                                                                                                                       |                       |
            |                       | -  It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).                                |                       |
            +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
            | Value                 | Tag value. Tag values can be repetitive or null.                                                                                      | Value_0001            |
            |                       |                                                                                                                                       |                       |
            |                       | The naming rule of a tag value is as follows:                                                                                         |                       |
            |                       |                                                                                                                                       |                       |
            |                       | -  It ranges from 0 to 43 Unicode characters.                                                                                         |                       |
            |                       |                                                                                                                                       |                       |
            |                       | -  It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).                                |                       |
            +-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

      c. Click **OK**.

   -  Editing a tag

      a. In the **Operation** column of the tag that you want to edit, click **Edit**.

      b. In the **Edit Tag** dialog box displayed, modify the tag value. :ref:`Table 1 <en-us_topic_0103696541__table191162312815>` describes the parameters.

         If the updated tag is identical to an existing one, only one is retained.

      c. Click **OK**.

   -  Deleting a tag

      a. In the **Operation** column of the tag that you want to delete, click **Delete**.
      b. In the dialog box that is displayed, confirm the deletion information.
      c. Click **Yes**.

   -  Searching for backups by tag

      For details, see :ref:`View Backup Details <en-us_topic_0056584642__section20267152222857>`.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
.. |image2| image:: /_static/images/en-us_image_0148563132.png
