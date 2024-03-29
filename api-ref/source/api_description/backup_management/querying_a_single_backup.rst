:original_name: en-us_topic_0059304234.html

.. _en-us_topic_0059304234:

Querying a Single Backup
========================

Function
--------

This API is used to query a single backup by ID.

URI
---

-  URI format

   GET https://{endpoint}/v1/{project_id}/checkpoint_items/{checkpoint_item_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      ================== ========= ====== ===========
      Parameter          Mandatory Type   Description
      ================== ========= ====== ===========
      project_id         Yes       String Project ID
      checkpoint_item_id Yes       String Backup ID
      ================== ========= ====== ===========

Request
-------

-  Parameter description

   None

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v1/{project_id}/checkpoint_items/{checkpoint_item_id}

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+--------------------------------------------------------------------------+
      | Parameter       | Type            | Description                                                              |
      +=================+=================+==========================================================================+
      | checkpoint_item | checkpoint_item | For details, see :ref:`Table 3 <en-us_topic_0059304234__table31284045>`. |
      +-----------------+-----------------+--------------------------------------------------------------------------+

-  Parameter description of field **checkpoint_item**

   .. _en-us_topic_0059304234__table31284045:

   .. table:: **Table 3** Parameter description of field **checkpoint_item**

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                   |
      +=======================+=======================+===============================================================================================================================+
      | checkpoint_id         | String                | Backup record ID                                                                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                | Creation time, for example, **2017-04-18T01:21:52.701973**                                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | extend_info           | Dict                  | Extension information                                                                                                         |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                | Backup ID                                                                                                                     |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Backup name                                                                                                                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | resource_id           | String                | Backup object ID                                                                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                | Backup status                                                                                                                 |
      |                       |                       |                                                                                                                               |
      |                       |                       | Value range: waiting_protect, protecting, available, waiting_restore, restoring, error, waiting_delete, deleting, and deleted |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | updated_at            | String                | Modification time, for example, **2017-04-18T01:21:52.701973**                                                                |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | backup_data           | Dict                  | VM metadata                                                                                                                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | description           | string                | Backup description                                                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | List<resource_tag>    | List of backup tags                                                                                                           |
      |                       |                       |                                                                                                                               |
      |                       |                       | Keys in the tag list must be unique.                                                                                          |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | resource_type         | String                | Backup object type                                                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **extend_info**

   .. table:: **Table 4** Parameter description of field **extend_info**

      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | Parameter              | Type                  | Description                                                                           |
      +========================+=======================+=======================================================================================+
      | auto_trigger           | Boolean               | Whether automatic trigger is enabled                                                  |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | average_speed          | Integer               | Average rate. The unit is kb/s                                                        |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | copy_from              | String                | The destination region of a backup replication. The value is left blank by default.   |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | copy_status            | String                | Backup replication status. The default value is **na**.                               |
      |                        |                       |                                                                                       |
      |                        |                       | Possible values are **na**, **waiting_copy**, **copying**, **success**, and **fail**. |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | fail_code              | fail_code             | Error code                                                                            |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | fail_op                | String                | Type of the failed operation                                                          |
      |                        |                       |                                                                                       |
      |                        |                       | Enum: [backup, restore, delete]                                                       |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | fail_reason            | String                | Description of the failure cause                                                      |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | image_type             | String                | Backup type, for example, **backup**                                                  |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | incremental            | Boolean               | Whether the backup is an enhanced backup                                              |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | progress               | Integer               | Backup progress. The value is an integer ranging from **0** to **100**.               |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | resource_az            | String                | AZ to which the backup resource belongs                                               |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | resource_name          | String                | Backup object name                                                                    |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | resource_type          | String                | Type of the backup object. For example, **OS::Nova::Server**                          |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | size                   | Integer               | Backup capacity. The unit is MB.                                                      |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | space_saving_ratio     | Integer               | Space saving rate                                                                     |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | volume_backups         | List<volume_backup>   | Disk backup list                                                                      |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | finished_at            | String                | Backup completion time, for example, **2017-04-18T01:21:52.701973**                   |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | supported_restore_mode | String                | Restoration mode. Possible values are **na**, **snapshot**, and **backup**.           |
      |                        |                       |                                                                                       |
      |                        |                       | **backup**: Data is restored from backups of the disks of the server.                 |
      |                        |                       |                                                                                       |
      |                        |                       | **na**: Restoration is not supported.                                                 |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | os_images_data         | List<image_data>      | Image data. This parameter has a value if an image has been created for the VM.       |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | support_lld            | Boolean               | Whether to allow lazyloading for fast restoration                                     |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | taskid                 | String                | Job ID                                                                                |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+
      | hypervisor_type        | String                | Virtualization type                                                                   |
      |                        |                       |                                                                                       |
      |                        |                       | The value is fixed at **QEMU**.                                                       |
      +------------------------+-----------------------+---------------------------------------------------------------------------------------+

-  Parameter description of field **backup_data**

   .. table:: **Table 5** Parameter description of field **backup_data**

      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter                | Type                  | Description                                                                                                                           |
      +==========================+=======================+=======================================================================================================================================+
      | \__openstack_region_name | String                | Name of the AZ where the server is located. If this parameter is left blank, such information about the server has not been obtained. |
      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | cloudservicetype         | String                | Server type                                                                                                                           |
      |                          |                       |                                                                                                                                       |
      |                          |                       | The value is fixed at **server** (ECSs).                                                                                              |
      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | disk                     | Integer               | System disk size corresponding to the server specifications                                                                           |
      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | imagetype                | String                | Image type                                                                                                                            |
      |                          |                       |                                                                                                                                       |
      |                          |                       | The value can be:                                                                                                                     |
      |                          |                       |                                                                                                                                       |
      |                          |                       | **gold**: public image                                                                                                                |
      |                          |                       |                                                                                                                                       |
      |                          |                       | **private**: private image                                                                                                            |
      |                          |                       |                                                                                                                                       |
      |                          |                       | **market**: market image                                                                                                              |
      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | ram                      | Integer               | Memory size of the server, in MB                                                                                                      |
      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | vcpus                    | Integer               | CPU cores corresponding to the server                                                                                                 |
      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | eip                      | String                | Elastic IP address of the server. If this parameter is left blank, such information about the server has not been obtained.           |
      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+
      | private_ip               | String                | Internal IP address of the server. If this parameter is left blank, such information about the server has not been obtained.          |
      +--------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **image_data**

   ========= ====== ===========
   Parameter Type   Description
   ========= ====== ===========
   image_id  String Image ID
   ========= ====== ===========

-  Parameter description of field **fail_code**

   .. table:: **Table 6** Parameter description of field **fail_code**

      =========== ====== =================
      Parameter   Type   Description
      =========== ====== =================
      Code        Long   Error code
      Description String Error description
      =========== ====== =================

-  Parameter description of field **volume_backup**

   .. table:: **Table 7** Parameter description of field **volume_backup**

      +-----------------------+-----------------------+-------------------------------------------------------+
      | Parameter             | Type                  | Description                                           |
      +=======================+=======================+=======================================================+
      | average_speed         | Integer               | Average rate, in MB/s                                 |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | bootable              | Boolean               | Whether the disk functions as a system disk           |
      |                       |                       |                                                       |
      |                       |                       | The value can be **true** or **false**.               |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | id                    | String                | Cinder backup ID                                      |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | image_type            | String                | Backup set type                                       |
      |                       |                       |                                                       |
      |                       |                       | Enum:[ backup]                                        |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | incremental           | Boolean               | Whether incremental backup is used                    |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | name                  | String                | Disk backup name                                      |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | size                  | Integer               | Accumulated size (MB) of backups                      |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | source_volume_id      | String                | Source disk ID                                        |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | source_volume_size    | Integer               | Source disk size in GB                                |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | space_saving_ratio    | Integer               | Space saving rate                                     |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | status                | String                | Status                                                |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | source_volume_name    | String                | Source disk name                                      |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | snapshot_id           | String                | ID of the snapshot from which the backup is generated |
      +-----------------------+-----------------------+-------------------------------------------------------+

-  Parameter description of field **resource_tag**

   .. table:: **Table 8** Parameter description of field **resource_tag**

      +-----------------------+-----------------------+------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                            |
      +=======================+=======================+========================================================================+
      | key                   | String                | Tag key                                                                |
      |                       |                       |                                                                        |
      |                       |                       | It consists of up to 36 characters.                                    |
      |                       |                       |                                                                        |
      |                       |                       | It cannot be an empty string.                                          |
      |                       |                       |                                                                        |
      |                       |                       | It can contain only letters, digits, hyphens (-), and underscores (_). |
      +-----------------------+-----------------------+------------------------------------------------------------------------+
      | value                 | String                | Tag value                                                              |
      |                       |                       |                                                                        |
      |                       |                       | It consists of up to 43 characters.                                    |
      |                       |                       |                                                                        |
      |                       |                       | It can be an empty string.                                             |
      |                       |                       |                                                                        |
      |                       |                       | It can contain only letters, digits, hyphens (-), and underscores (_). |
      +-----------------------+-----------------------+------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "checkpoint_item": {
          "status": "available",
          "backup_data": {
            "eip": "",
            "cloudservicetype": "",
            "ram": 4096,
            "vcpus": 4,
            "__openstack_region_name": "",
            "private_ip": "",
            "disk": 0,
            "imagetype": ""
          },
          "name": "backup_d32c",
          "resource_id": "f45c477a-57e5-465f-999f-d845083962db",
          "created_at": "2017-04-15T04:20:37.277880",
          "checkpoint_id": "f672a1bb-6912-446a-816c-72792c5263e0",
          "updated_at": "2017-04-15T04:25:38.680638",
          "resource_type": "OS::Nova::Server",
          "extend_info": {
            "auto_trigger": false,
            "space_saving_ratio": 0,
            "copy_status": "na",
            "fail_reason": "",
            "resource_az": "az1.dc1",
            "image_type": "backup",
            "finished_at": "2017-04-15T04:25:38.675478",
            "average_speed": 0,
            "copy_from": "",
            "supported_restore_mode": "backup",
            "support_lld": false,
            "os_images_data": [
                  {
                      "image_id": "fe84dd80-0229-4918-8d3d-cbb33154b565"
                  }
              ],
            "volume_backups": [
              {
                "status": "available",
                "space_saving_ratio": 0,
                "name": "manualbk_47222",
                "bootable": true,
                "average_speed": 0,
                "source_volume_size": 20,
                "source_volume_id": "ee27f809-6fb5-40ae-ac46-c932bb4ee8fe",
                "incremental": false,
                "image_type": "backup",
                "source_volume_name": "karbor_02",
                "id": "70675cbc-d3a8-43a7-9f81-c8b6bc3f5d6d",
                "size": 0,
                "snapshot_id": "36f520e1-d2ea-4907-956a-3d9cd53e2d38"
              },
              {
                "status": "available",
                "space_saving_ratio": 0,
                "name": "manualbk_47222",
                "bootable": true,
                "average_speed": 0,
                "source_volume_size": 20,
                "source_volume_id": "e7f48980-927c-48de-afd4-f0245d2e5100",
                "incremental": false,
                "image_type": "backup",
                "source_volume_name": "karbor_01",
                "id": "8eb98e91-8924-4d4b-b6d6-28fb7b751e9c",
                "size": 0,
                "snapshot_id": "36f520e1-d2ea-4907-956a-3d9cd53e2d38"
              }
            ],
            "fail_code": {},
            "incremental": false,
            "taskid": "e0a21692-2192-11e7-bf23-0242ac110007",
            "hypervisor_type": "QEMU",
            "progress": 100,
            "fail_op": "",
            "resource_name": "karbor_02",
            "size": 0
          },
          "id": "90c1d5fa-1b9f-4aeb-b2f4-81c806e98190"
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
   500         Service unavailable.
   =========== ===========================

Error Codes
-----------

For details, see :ref:`Error Codes <en-us_topic_0071888297>`.
