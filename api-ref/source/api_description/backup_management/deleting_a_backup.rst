:original_name: en-us_topic_0059304232.html

.. _en-us_topic_0059304232:

Deleting a Backup
=================

Function
--------

This API is used to delete a backup.

.. note::

   The deletion operation is asynchronous. Tasks will be queued depending on the background task execution status. Therefore, the deletion will not be completed immediately. You need to query the task information continuously to obtain the deletion result. A maximum of 30 minutes is required.

   For example, a user can execute a maximum of five backup deletion tasks concurrently. If the number exceeds five, the sixth and subsequent tasks are queued.

URI
---

-  URI format

   DELETE https://{endpoint}/v1/{project_id}/providers/{provider_id}/checkpoints/{checkpoint_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter     | Mandatory | Type   | Description                                                                                                                                                                           |
      +===============+===========+========+=======================================================================================================================================================================================+
      | project_id    | Yes       | String | Project ID                                                                                                                                                                            |
      +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id   | Yes       | String | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**. |
      +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | checkpoint_id | Yes       | String | Backup record ID                                                                                                                                                                      |
      +---------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Mandatory | Type   | Description                                                                                                                                    |
      +==================+===========+========+================================================================================================================================================+
      | checkpoint_items | No        | String | Indicates the ID list of the backup records to be deleted. If this parameter is not set, all backup records of **checkpoint** will be deleted. |
      +------------------+-----------+--------+------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description

   None

-  Example request

   .. code-block::

      Deleting all backups in the specified backup record:
      DELETE https://{endpoint}/v1/{project_id}/providers/{provider_id}/checkpoints/{checkpoint_id}
      Deleting a single backup in the specified backup record:
      DELETE https://{endpoint}/v1/{project_id}/providers/{provider_id}/checkpoints/{checkpoint_id}?checkpoint_items={checkpoint_items_id}

Response
--------

-  Parameter description

   None

-  Example response

   .. code-block::

      {
      }

Status Codes
------------

-  Normal

   =========== ===========
   Status Code Description
   =========== ===========
   200         OK
   =========== ===========

-  Abnormal

   =========== ===========================
   Status Code Description
   =========== ===========================
   400         Invalid request parameters.
   401         Authentication failed.
   403         No operation permission.
   404         Requested object not found.
   500         Service internal error.
   503         Service unavailable.
   =========== ===========================

Error Codes
-----------

For details, see :ref:`Error Codes <en-us_topic_0071888297>`.
