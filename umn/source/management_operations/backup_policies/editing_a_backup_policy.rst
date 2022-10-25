:original_name: en-us_topic_0056584602.html

.. _en-us_topic_0056584602:

Editing a Backup Policy
=======================

This section describes how to edit a backup policy.

.. note::

   Changing the backup period does not actually change the time of the day when the backup is scheduled to run. For example, you set to run a backup job every seven days. Three days later, you modified the policy to run a backup job every five days. Then the associated server will be backed up two days after your modification.

   To actually change when the backup is scheduled to run, dissociate the original policy and associate the server with a new backup policy.

Prerequisites
-------------

You have created at least one backup policy.

Procedure
---------

#. Log in to the CSBS management console.

   a. Log in to the management console.
   b. Click |image1| in the upper left corner of the management console and select a region and a project.
   c. Under Storage > **Cloud Server Backup Service**.

#. Click the **Policies** tab.

#. In the row of the backup policy you want to modify, click **Edit**.

#. Edit the backup policy. See :ref:`Figure 1 <en-us_topic_0056584602__fig232654615382>`.

   .. _en-us_topic_0056584602__fig232654615382:

   .. figure:: /_static/images/en-us_image_0164876805.png
      :alt: **Figure 1** Editing a backup policy

      **Figure 1** Editing a backup policy

   Related parameters are described in :ref:`Table 1 <en-us_topic_0056584629__table18975142115146>`.

   For details about how to modify backup policy tags, see :ref:`Managing Backup Policy Tags <en-us_topic_0103696542>`.

#. Click **OK**.

.. |image1| image:: /_static/images/en-us_image_0148411635.png
