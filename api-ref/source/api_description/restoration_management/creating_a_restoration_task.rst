:original_name: en-us_topic_0059304237.html

.. _en-us_topic_0059304237:

Creating a Restoration Task
===========================

Function
--------

This API is used to perform backup-based restoration.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/restores

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

      ========= ========= =========== ===================
      Parameter Mandatory Type        Description
      ========= ========= =========== ===================
      restore   Yes       restore_req Restoration request
      ========= ========= =========== ===================

-  Parameter description of field **restore_req**

   .. table:: **Table 3** Parameter description of field **restore_req**

      +----------------+-----------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter      | Mandatory | Type          | Description                                                                                                                                                                           |
      +================+===========+===============+=======================================================================================================================================================================================+
      | checkpoint_id  | Yes       | String        | Backup record ID                                                                                                                                                                      |
      +----------------+-----------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | parameters     | Yes       | restore_param | Restoration parameters                                                                                                                                                                |
      +----------------+-----------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id    | Yes       | String        | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**. |
      +----------------+-----------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restore_target | No        | String        | Restoration target                                                                                                                                                                    |
      +----------------+-----------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **restore_param**

   .. table:: **Table 4** Parameter description of field **restore_param**

      +--------------------+-----------+----------------+--------------------------------------------------------+
      | Parameter          | Mandatory | Type           | Description                                            |
      +====================+===========+================+========================================================+
      | checkpoint_item_id | Yes       | String         | Backup ID                                              |
      +--------------------+-----------+----------------+--------------------------------------------------------+
      | power_on           | Yes       | Boolean        | Whether to instantly power on the VM after restoration |
      +--------------------+-----------+----------------+--------------------------------------------------------+
      | targets            | Yes       | restore_target | Restoration target                                     |
      +--------------------+-----------+----------------+--------------------------------------------------------+

-  Parameter description of field **restore_target**

   .. table:: **Table 5** Parameter description of field **restore_target**

      +-----------+-----------+------------------------------+------------------------------------------------------------+
      | Parameter | Mandatory | Type                         | Description                                                |
      +===========+===========+==============================+============================================================+
      | server_id | Yes       | String                       | ID of the ECS to be restored                               |
      +-----------+-----------+------------------------------+------------------------------------------------------------+
      | volumes   | Yes       | List<restore_volume_mapping> | List of the mappings between disk backups and target disks |
      +-----------+-----------+------------------------------+------------------------------------------------------------+

-  Parameter description of field **restore_volume_mapping**

   .. table:: **Table 6** Parameter description of field **restore_volume_mapping**

      +-----------+-----------+--------+------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                    |
      +===========+===========+========+================================================+
      | backup_id | Yes       | String | Disk backup ID                                 |
      +-----------+-----------+--------+------------------------------------------------+
      | volume_id | Yes       | String | ID of the destination disk for the restoration |
      +-----------+-----------+--------+------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{endpoint}/v1/{project_id}/restores
      {
        "restore" : {
          "provider_id" : "fc4d5750-22e7-4798-8a46-f48f62c4c1da",
          "checkpoint_id" : "a2b9fb53-2770-4fcd-9bad-6cadd56e6c09",
          "parameters" : {
            "checkpoint_item_id" : "504b7d59-c361-411f-9ed3-814f35d08e3d",
            "power_on" : true,
            "targets" : {
              "server_id" : "f45c477a-57e5-465f-999f-d845083962db",
              "volumes" : [ {
                "backup_id" : "bc118c24-3234-4afd-8423-d66d3d677649",
                "volume_id" : "ee27f809-6fb5-40ae-ac46-c932bb4ee8fe"
              }]
            }
          }
        }
      }

Response
--------

-  Parameter description

   .. table:: **Table 7** Parameter description

      ========= ============ ====================
      Parameter Type         Description
      ========= ============ ====================
      restore   restore_resp Restoration response
      ========= ============ ====================

-  Parameter description of field **restore_resp**

   .. table:: **Table 8** Parameter description of field **restore_resp**

      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter        | Type          | Description                                                                                                                                                                           |
      +==================+===============+=======================================================================================================================================================================================+
      | id               | String        | Restoration ID                                                                                                                                                                        |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | checkpoint_id    | String        | Backup record ID                                                                                                                                                                      |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | parameters       | restore_param | Restoration parameters                                                                                                                                                                |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | project_id       | String        | Project ID                                                                                                                                                                            |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id      | String        | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**. |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resources_reason | Dict          | Cause of the resource restoration failure                                                                                                                                             |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resources_status | Dict          | Resource status after the resource is restored, for example, **available**                                                                                                            |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | restore_target   | String        | Restoration target                                                                                                                                                                    |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status           | String        | Status                                                                                                                                                                                |
      +------------------+---------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **restore_param**

   .. table:: **Table 9** Parameter description of field **restore_param**

      +--------------------+----------------+----------------------------------------------+
      | Parameter          | Type           | Description                                  |
      +====================+================+==============================================+
      | checkpoint_item_id | String         | Backup ID                                    |
      +--------------------+----------------+----------------------------------------------+
      | power_on           | Boolean        | Whether to power on the VM after restoration |
      +--------------------+----------------+----------------------------------------------+
      | targets            | restore_target | Restoration target                           |
      +--------------------+----------------+----------------------------------------------+

-  Parameter description of field **restore_target**

   .. table:: **Table 10** Parameter description of field **restore_target**

      +-----------+------------------------------+------------------------------------------------------------+
      | Parameter | Type                         | Description                                                |
      +===========+==============================+============================================================+
      | server_id | String                       | ID of the ECS to be restored                               |
      +-----------+------------------------------+------------------------------------------------------------+
      | volumes   | List<restore_volume_mapping> | List of the mappings between disk backups and target disks |
      +-----------+------------------------------+------------------------------------------------------------+

-  Parameter description of field **restore_volume_mapping**

   .. table:: **Table 11** Parameter description of field **restore_volume_mapping**

      ========= ====== ========================================
      Parameter Type   Description
      ========= ====== ========================================
      backup_id String Disk backup ID
      volume_id String ID of the disk to which data is restored
      ========= ====== ========================================

-  Example response

   .. code-block::

      {
        "restore" : {
          "restore_target" : "http://192.168.1.2:35357/v2.0/",
          "status" : "in_progress",
          "provider_id" : "fc4d5750-22e7-4798-8a46-f48f62c4c1da",
          "resources_status" : in_progress,
          "parameters" : {
            "power_on" : true,
            "targets" : {
              "server_id" : "f45c477a-57e5-465f-999f-d845083962db",
              "volumes" : [ {
                "backup_id" : "bc118c24-3234-4afd-8423-d66d3d677649",
                "volume_id" : "ee27f809-6fb5-40ae-ac46-c932bb4ee8fe"
              } ]
            },
            "checkpoint_item_id" : "504b7d59-c361-411f-9ed3-814f35d08e3d"
          },
          "checkpoint_id" : "a2b9fb53-2770-4fcd-9bad-6cadd56e6c09",
          "project_id" : "b942cc8342734d15bcb246babb1953cf",
          "id" : "d3a54e80-6483-485d-98f6-c0409e6f2e0a",
          "resources_reason" : { }
        }
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
