:original_name: en-us_topic_0103696542.html

.. _en-us_topic_0103696542:

Managing Backup Policy Tags
===========================

You can add tags to a backup policy as well as edit and delete these tags. These tags are used to filter and manage backup resources only.

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Policies** tab.
#. Select a backup policy and click |image2|. The **Tags** tab page displays existing tags of the backup policy.

   -  Adding a tag

      a. In the upper left corner of the **Tags** panel, click **Add Tag**.

      b. In the dialog box that is displayed, set the key and value of the new tag.

         A tag is represented in the form of a key-value pair. Tags are used to identify, classify, and search for cloud resources.

         Tags added in a backup policy apply to all backups generated using the backup policy. These tags are used to filter and manage backup resources only. A backup policy can have a maximum of 10 tags.

         :ref:`Table 1 <en-us_topic_0103696542__table1499463312>` describes parameters of a tag.

         .. _en-us_topic_0103696542__table1499463312:

         .. table:: **Table 1** Parameter description

            +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
            | Parameter             | Description                                                                                                                                  | Example Value         |
            +=======================+==============================================================================================================================================+=======================+
            | Key                   | Tag key. Each tag of a backup policy has a unique key. The key of a tag is user-definable or is selected from those of existing tags in TMS. | Key_0001              |
            |                       |                                                                                                                                              |                       |
            |                       | The naming rule of a tag key is as follows:                                                                                                  |                       |
            |                       |                                                                                                                                              |                       |
            |                       | -  It ranges from 1 to 36 Unicode characters.                                                                                                |                       |
            |                       | -  It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).                                       |                       |
            +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+
            | Value                 | Tag value. Tag values can be repetitive or null.                                                                                             | Value_0001            |
            |                       |                                                                                                                                              |                       |
            |                       | The naming rule of a tag value is as follows:                                                                                                |                       |
            |                       |                                                                                                                                              |                       |
            |                       | -  It ranges from 0 to 43 Unicode characters.                                                                                                |                       |
            |                       | -  It can contain only uppercase letters, lowercase letters, digits, hyphens (-), and underscores (_).                                       |                       |
            +-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------+-----------------------+

      c. Click **OK**.

   -  Editing a tag

      a. In the **Operation** column of the tag that you want to edit, click **Edit**.
      b. In the **Edit Tag** dialog box that is displayed, modify the tag value. :ref:`Table 1 <en-us_topic_0103696542__table1499463312>` describes the parameters.
      c. Click **OK**.

   -  Deleting a tag

      a. In the **Operation** column of the tag that you want to delete, click **Delete**.
      b. In the dialog box that is displayed, confirm the deletion information.
      c. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
.. |image2| image:: /_static/images/en-us_image_0148563132.png
