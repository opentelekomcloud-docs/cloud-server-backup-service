:original_name: en-us_topic_0133120427.html

.. _en-us_topic_0133120427:

An ECS Created Using an Image Enters the Maintenance Mode After Login
=====================================================================

Symptom
-------

After you create an image using an ECS backup, use the image to create an ECS, and log in to the ECS, the ECS enters the maintenance mode and cannot be used properly.

Possible Cause
--------------

When the source ECS has data disks, the configuration parameters contained in the **/etc/fstab** file in the system disk of the new ECS are the source ECS's, causing the UUID information inconsistent with the new data disks. In such conditions, the ECS encounters an error when uploading **/etc/fstab** during the bootup and enters the maintenance mode.

Solution
--------

This section uses CentOS as an example.

#. After creating an ECS using an image, log in to the ECS console, click **Remote Login** in the row of the ECS.

#. In the maintenance interface that is displayed, access the system as prompted.


   .. figure:: /_static/images/en-us_image_0133157609.jpg
      :alt: **Figure 1** Interface displayed when an ECS enters the maintenance mode

      **Figure 1** Interface displayed when an ECS enters the maintenance mode

#. Run the **cat /etc/fstab** command to check the attachment information about the data disks.


   .. figure:: /_static/images/en-us_image_0133153500.jpg
      :alt: **Figure 2** Data disk UUIDs

      **Figure 2** Data disk UUIDs

#. Run the **vi /etc/fstab** command to open the file, press **i** to enter the editing mode, and delete the attachment information of all data disks. Then, press **Esc** to exit the editing mode and run **:wq!** to save the change and exit.


   .. figure:: /_static/images/en-us_image_0133153562.jpg
      :alt: **Figure 3** **/etc/fstab** after being updated

      **Figure 3** **/etc/fstab** after being updated

#. Run the **reboot** command to restart the system.


   .. figure:: /_static/images/en-us_image_0133153565.jpg
      :alt: **Figure 4** Normal bootup page

      **Figure 4** Normal bootup page

#. After entering the system, attach the data disks manually.


   .. figure:: /_static/images/en-us_image_0133153567.jpg
      :alt: **Figure 5** Attaching the data disks manually

      **Figure 5** Attaching the data disks manually

#. Run the **blkid** command to obtain the UUID information of the data disks.


   .. figure:: /_static/images/en-us_image_0133153569.jpg
      :alt: **Figure 6** Obtaining UUIDs of data disks

      **Figure 6** Obtaining UUIDs of data disks

#. Run the **vi /etc/fstab** command to open the file, press **i** to enter the editing mode, and add the attachment information of all data disks. Then, press **Esc** to exit the editing mode and run **:wq!** to save the change and exit.


   .. figure:: /_static/images/en-us_image_0133150825.jpg
      :alt: **Figure 7** Adding attachment information of data disks

      **Figure 7** Adding attachment information of data disks

   After the information is added, the system will automatically attach the data disks on restart.
