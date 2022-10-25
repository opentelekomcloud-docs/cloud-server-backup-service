:original_name: en-us_topic_0056584600.html

.. _en-us_topic_0056584600:

Deleting a Backup
=================

You can delete unwanted backups to reduce space usage and costs.

Context
-------

CSBS supports manual deletion of backups and automatic deletion of expired backups. The latter deletion method is implemented using the backup retention rule in the backup policy. For details, see :ref:`Creating a Backup Policy <en-us_topic_0056584629>`.

Prerequisites
-------------

-  At least one backup exists in CSBS.
-  The backups are in the **Available** or **Error** state.

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Backups** tab. Locate the ECS backup. For details, see :ref:`Viewing a Backup <en-us_topic_0056584642>`.

#. In the row of the backup, click **More** > **Delete**. See :ref:`Figure 1 <en-us_topic_0056584600__fig10341833105744>`. Alternatively, select the backups you want to delete and click **Delete** in the upper left corner to delete them in a batch.

   .. _en-us_topic_0056584600__fig10341833105744:

   .. figure:: /_static/images/en-us_image_0164873120.png
      :alt: **Figure 1** Deleting a backup

      **Figure 1** Deleting a backup

#. Click **Yes**.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
