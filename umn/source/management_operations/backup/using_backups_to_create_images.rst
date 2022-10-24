:original_name: en-us_topic_0067911222.html

.. _en-us_topic_0067911222:

Using Backups to Create Images
==============================

CSBS allows you to create images using ECS backups. You can use the images to provision ECSs for fast restoring the service running environment.

Prerequisites
-------------

-  The following operations have been performed before you use an ECS's backup to create an image:

   -  You have optimized the Linux ECS (referring to `(Optional) Optimizing a Linux Private Image <https://docs.otc.t-systems.com/usermanual/ims/en-us_topic_0047501133.html>`__) and installed Cloud-Init (referring to `Installing Cloud-Init <https://docs.otc.t-systems.com/usermanual/ims/en-us_topic_0030730603.html>`__).
   -  You have optimized the Windows ECS (referring to `(Optional) Optimizing a Windows Private Image <https://docs.otc.t-systems.com/usermanual/ims/en-us_topic_0047501112.html>`__) and installed Cloudbase-Init (referring to `Installing Cloudbase-Init <https://docs.otc.t-systems.com/usermanual/ims/en-us_topic_0030730602.html>`__).

-  The backup you want to use to create an image meets either of the following two conditions:

   -  The backup is in the **Available** state.
   -  The backup is in the **Creating** state which is marked with **Image can be created**.

   .. note::

      Once a backup creation starts, the backup enters the **Creating** state. After a while, a message stating "Image can be created" is displayed under **Creating**. In this case, the backup can be used for creating an image, even though it is still being created and cannot be used for restoration.

-  The backup you want to use to create an image contains the system disk data.

Description
-----------

-  Images created from a backup are the same, so CSBS allows you to use a backup to create only one full-ECS image that contains the whole data of the ECS's system disk and data disks, in order to save the image quota. After an image is created, you can use the image to provision multiple ECSs in a batch.
-  A backup with an image created cannot be deleted manually or automatically. If you want to delete such a backup, delete its image first. If a backup is automatically generated based on a backup policy and the backup has been used to create an image, the backup will not be counted as a retained backup and will not be deleted automatically.

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Backups** tab and locate the desired server backup. For details, see :ref:`Viewing a Backup <en-us_topic_0056584642>`.
#. In the row of the backup, click **Create Image**.
#. Create an image by referring to "Creating a Full-ECS Image Using a CSBS Backup" in the *Image Management Server User Guide*.
#. If you want to use an image to provision ECSs, see "Creating ECSs Using an Image" in the *Image Management Server User Guide*.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
