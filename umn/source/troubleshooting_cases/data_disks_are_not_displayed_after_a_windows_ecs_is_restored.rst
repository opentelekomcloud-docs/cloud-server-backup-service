:original_name: en-us_topic_0095219826.html

.. _en-us_topic_0095219826:

Data Disks Are Not Displayed After a Windows ECS Is Restored
============================================================

Symptom
-------

When a Windows ECS is restored, the data disks are not displayed.

Possible Cause
--------------

Due to the limitations of Windows operating systems, data disks are in offline mode after an ECS is stored.

Solution
--------

#. On the Windows desktop, right-click the **My Computer** icon.

#. Choose **Manage** from the shortcut menu. The **Computer Management** page is displayed.

#. In the navigation tree, choose **Storage** > **Disk Management**.

   Data disks are in the offline state, as shown in :ref:`Figure 1 <en-us_topic_0095219826__fig413741135513>`.

   .. _en-us_topic_0095219826__fig413741135513:

   .. figure:: /_static/images/en-us_image_0095223848.png
      :alt: **Figure 1** Data disks in the offline state


      **Figure 1** Data disks in the offline state

#. Right-click a data disk in the offline state and choose **Online**, as shown in :ref:`Figure 2 <en-us_topic_0095219826__fig179301858016>`.

   .. _en-us_topic_0095219826__fig179301858016:

   .. figure:: /_static/images/en-us_image_0095227273.png
      :alt: **Figure 2** Setting a data disk to be online


      **Figure 2** Setting a data disk to be online

   After the data disk status changes to **Online**, the data disk will be displayed in the disk list, as shown in :ref:`Figure 3 <en-us_topic_0095219826__fig9869427131715>`.

   In addition, the data disk will be properly displayed on the ECS.

   .. _en-us_topic_0095219826__fig9869427131715:

   .. figure:: /_static/images/en-us_image_0095233951.png
      :alt: **Figure 3** Viewing online data disks


      **Figure 3** Viewing online data disks
