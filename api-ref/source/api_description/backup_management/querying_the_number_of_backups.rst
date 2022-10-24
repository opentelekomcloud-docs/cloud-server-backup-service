:original_name: en-us_topic_0059304233.html

.. _en-us_topic_0059304233:

Querying the Number of Backups
==============================

Function
--------

This API is used to query the number of backups. Filtering parameters are supported.

URI
---

-  URI format

   GET https://{endpoint}/v1/{project_id}/checkpoint_items/count

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      project_id Yes       String Project ID
      ========== ========= ====== ===========

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                   |
      +=================+=================+=================+===============================================================================================================================================================================+
      | status          | No              | String          | Query based on field **status** is supported.                                                                                                                                 |
      |                 |                 |                 |                                                                                                                                                                               |
      |                 |                 |                 | Value range: waiting_protect, protecting, available, waiting_restore, restoring, error, waiting_delete, deleting, and deleted                                                 |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | all_tenants     | No              | Boolean         | Whether to query the backups of all tenants. Only administrators can query the backups of all tenants.                                                                        |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name            | No              | String          | Supports query by backup name.                                                                                                                                                |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | az              | No              | String          | AZ-based filtering is supported.                                                                                                                                              |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_id     | No              | String          | Filtering based on the backup object ID is supported.                                                                                                                         |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_name   | No              | String          | Filtering based on the backup object name is supported.                                                                                                                       |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time      | No              | String          | Filtering based on the backup time is supported. This is the backup start time. For example, 2017-04-15T04:25:38                                                              |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | end_time        | No              | String          | Filtering based on the backup time is supported. This is the backup end time. For example, 2017-04-15T04:25:38                                                                |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | image_type      | No              | String          | Supports filtering by backup image type. This parameter can be used only when images are created using backups. The image type can be obtained from Image Management Service. |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | policy_id       | No              | String          | Filtering based on **policy_id** is supported.                                                                                                                                |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | ip              | No              | String          | Searching based on the VM's IP address is supported.                                                                                                                          |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | checkpoint_id   | No              | String          | Filtering based on **checkpoint_id** is supported.                                                                                                                            |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_type   | No              | String          | Type of the backup object. For example, **OS::Nova::Server**                                                                                                                  |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description

   None

-  Example request

   .. code-block::

      Querying the total number of backups:
      GET https://{endpoint}/v1/{project_id}/checkpoint_items/count
      Querying the number of backups with certain conditions:
      GET https://{endpoint}/v1/{project_id}/checkpoint_items/count?status=error

Response
--------

-  Parameter description

   .. table:: **Table 3** Parameter description

      ========= ======= =================
      Parameter Type    Description
      ========= ======= =================
      count     Integer Number of backups
      ========= ======= =================

-  Example response

   .. code-block::

      {
        "count" : 10
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
