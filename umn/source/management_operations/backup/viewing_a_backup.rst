:original_name: en-us_topic_0056584642.html

.. _en-us_topic_0056584642:

Viewing a Backup
================

After a backup job is delivered or completed, you can set search criteria to filter backups from the backup list and view backup details.

Prerequisites
-------------

A backup job has been created.

.. _en-us_topic_0056584642__section20267152222857:

View Backup Details
-------------------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Backups** tab. Search for backups by filtering conditions.

   -  You can search for backups by selecting a state from the **All statuses** drop-down list in the upper right corner of the backup list.

      :ref:`Table 1 <en-us_topic_0056584642__table27644511104124>` describes each state.

      .. _en-us_topic_0056584642__table27644511104124:

      .. table:: **Table 1** State description

         +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | State                 | State Attribute       | Description                                                                                                                                                                                              |
         +=======================+=======================+==========================================================================================================================================================================================================+
         | All statuses          | --                    | All statuses of backups.                                                                                                                                                                                 |
         +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Available             | A stable state        | A stable state of a backup after the backup is created                                                                                                                                                   |
         |                       |                       |                                                                                                                                                                                                          |
         |                       |                       | This state allows various operations.                                                                                                                                                                    |
         +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Creating              | An intermediate state | An intermediate state of a backup from the start of a backup job to the completion of the backup job.                                                                                                    |
         |                       |                       |                                                                                                                                                                                                          |
         |                       |                       | In this state, a progress bar is displayed indicating the backup progress. If the progress bar remains unchanged for a long time, an exception has occurred. Contact the administrator for support.      |
         +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Restoring             | An intermediate state | An intermediate state when using the backup to restore data.                                                                                                                                             |
         |                       |                       |                                                                                                                                                                                                          |
         |                       |                       | In this state, a progress bar is displayed indicating the restoration progress. If the progress bar remains unchanged for a long time, an exception has occurred. Contact the administrator for support. |
         +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Deleting              | An intermediate state | An intermediate state from the start of deleting the backup to the completion of deleting the backup.                                                                                                    |
         |                       |                       |                                                                                                                                                                                                          |
         |                       |                       | In this state, a progress bar is displayed indicating the deletion progress. If the progress bar remains unchanged for a long time, an exception has occurred. Contact the administrator for support.    |
         +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
         | Error                 | A stable state        | A backup enters the **Error** state when an exception occurs when the backup is being used.                                                                                                              |
         |                       |                       |                                                                                                                                                                                                          |
         |                       |                       | A backup in this state cannot be used for backup or restoration, and must be deleted manually. If manual deletion fails, contact the administrator for support.                                          |
         +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   -  You can search for backups by selecting a time segment displayed in the upper right corner of the backup list.

   -  You can search for backups by server name, server ID, backup name, or backup ID. Click |image2| to search for target backups.

   -  You can click **Search by Tag** in the upper right corner to search for backups by tag.

      -  On the **Search by Tag** tab page that is displayed, enter a tag key and a tag value (must be among existing keys and values) and click |image3|. The added tag search criteria are displayed under the text boxes. Click **Search** in the lower right corner.
      -  You can use more than one tag for a combination search. Each time after a key and a value are entered, click |image4|. The added tag search criteria are displayed under the text boxes. When more than one tag is added, they will be applied together for a combination search. A maximum of 10 tags can be added at the same time.
      -  You can click **Reset** in the upper right corner to reset the search criteria.

      .. note::

         Backups whose backup type is **Enhanced backup** support Instant Restore. Backups whose backup type is **Enhanced backup** support Instant Restore. For details, see :ref:`Instant Restore <en-us_topic_0056725845__section181448505477>`.

#. Click |image5| on the left of a backup name to view details about the backup.

View Backup Space Usage
-----------------------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image6| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Backups** tab and then the number indicating the used storage space in the backup overview. :ref:`Figure 1 <en-us_topic_0056584642__fig635912816013>` provides an example.

   .. _en-us_topic_0056584642__fig635912816013:

   .. figure:: /_static/images/en-us_image_0164860175.png
      :alt: **Figure 1** Backup overview

      **Figure 1** Backup overview

#. In the displayed dialog box, view the storage space usage.

   **Backups** specifies the number of backups created for an ECS and **Total Backup Capacity (GB)** specifies the capacity used by the ECS's backups in total.


   .. figure:: /_static/images/en-us_image_0164860652.png
      :alt: **Figure 2** Storage space usage

      **Figure 2** Storage space usage

.. |image1| image:: /_static/images/en-us_image_0148411635.png
.. |image2| image:: /_static/images/en-us_image_0148561644.png
.. |image3| image:: /_static/images/en-us_image_0238025638.png
.. |image4| image:: /_static/images/en-us_image_0238025638.png
.. |image5| image:: /_static/images/en-us_image_0148563132.png
.. |image6| image:: /_static/images/en-us_image_0148411635.png
