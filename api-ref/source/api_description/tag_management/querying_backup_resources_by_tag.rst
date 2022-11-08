:original_name: en-us_topic_0098635086.html

.. _en-us_topic_0098635086:

Querying Backup Resources by Tag
================================

Function
--------

This API is used to filter resources by tag.

Tag Management Service (TMS) uses this API to filter and list resources of each service by tag. These services must have the query capabilities.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/csbs_backup/resource_instances/action

-  Request header

   .. table:: **Table 1** Request header

      +--------------+-----------+--------------------------------------+------------------+
      | Parameter    | Mandatory | Type                                 | Description      |
      +==============+===========+======================================+==================+
      | Content-type | Yes       | MIME type of the body in the request | application/json |
      +--------------+-----------+--------------------------------------+------------------+
      | X-Auth-Token | Yes       | User token                           | ``-``            |
      +--------------+-----------+--------------------------------------+------------------+

-  Parameter description

   .. table:: **Table 2** Parameter description

      ========== ========= ====== ===========
      Parameter  Mandatory Type   Description
      ========== ========= ====== ===========
      project_id Yes       String Project ID
      ========== ========= ====== ===========

Request
-------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                          |
      +=================+=================+=================+======================================================================================================================================================================================================================================================+
      | tags            | No              | List<tag>       | List of included tags. Backups with these tags will be filtered.                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The list can contain up to 10 keys.                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list are in an AND relationship.                                                                                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The response returns resources containing all tags in this list. Keys in this list are in an AND relationship while values in each key-value structure is in an OR relationship.                                                                     |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags_any        | No              | List<tag>       | List of tags. Backups with any tags in this list will be filtered.                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The list can contain up to 10 keys.                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The response returns resources containing any tags in this list. Keys in this list are in an OR relationship while values in each key-value structure is in an OR relationship.                                                                      |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | not_tags        | No              | List<tag>       | List of excluded tags. Backups without these tags will be filtered.                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The list can contain up to 10 keys.                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The response returns resources containing no tags in this list. Keys in this list are in an AND relationship while values in each key-value structure is in an OR relationship.                                                                      |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | not_tags_any    | No              | List<tag>       | List of tags. Backups without any tags in this list will be filtered.                                                                                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The list can contain up to 10 keys.                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The response returns resources without any tags in this list. Keys in this list are in an OR relationship while values in each key-value structure is in an OR relationship.                                                                         |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | limit           | No              | String          | Query count (This parameter is not displayed if **action** is set to **count**.)                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | If **action** is set to **filter**, the value defaults to **1000**. The value ranges from **1** to **1000**. If you set a value out of this range, an error will be reported. The number of returned records does not exceed the value of **limit**. |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | String          | Query index (This parameter is not displayed if **action** is set to **count**.)                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | If **action** is set to **filter**, the value defaults to **0** (minimum value). The first record in the query result is the offset+1 record that meets the query criteria.                                                                          |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | action          | Yes             | String          | Operation type                                                                                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Possible values are **filter** and **count**.                                                                                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | **filter** indicates pagination query and **count** indicates that a specified number of queried records will be returned.                                                                                                                           |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | matches         | No              | List<match>     | List of query criteria supported by resources                                                                                                                                                                                                        |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **tag**

   .. table:: **Table 4** Parameter description of field **tag**

      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                             |
      +=================+=================+=================+=========================================================================+
      | key             | Yes             | String          | Tag key                                                                 |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | A tag key consists of up to 127 characters.                             |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | A tag key cannot be an empty string.                                    |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | Spaces before and after a key will be deprecated.                       |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------+
      | values          | Yes             | List<String>    | List of tag values                                                      |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | The list can contain up to 10 values.                                   |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | A tag value consists of up to 255 characters.                           |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | Spaces before and after a key will be deprecated.                       |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | Values in this list must be unique.                                     |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | Values in this list are in an OR relationship.                          |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | This list can be empty and each value can be an empty character string. |
      |                 |                 |                 |                                                                         |
      |                 |                 |                 | If this list is left blank, it indicates that all values are included.  |
      +-----------------+-----------------+-----------------+-------------------------------------------------------------------------+

-  Parameter description of field **match**

   .. table:: **Table 5** Parameter description of field **match**

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                   |
      +=================+=================+=================+===============================================================================================================================================+
      | key             | Yes             | String          | Tag key                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                               |
      |                 |                 |                 | Possible values are:                                                                                                                          |
      |                 |                 |                 |                                                                                                                                               |
      |                 |                 |                 | **resource_name**: indicates the resource name.                                                                                               |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Tag value                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                               |
      |                 |                 |                 | A tag value consists of up to 255 characters.                                                                                                 |
      |                 |                 |                 |                                                                                                                                               |
      |                 |                 |                 | If **key** is set to **resource_name**, an empty character string indicates exact matching and any non-empty string indicates fuzzy matching. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{endpoint}/v1/{project_id}/csbs_backup/resource_instances/action

-  When **action** is set to **filter**:

   .. code-block::

      {
          "offset": "100",
          "limit": "100",
          "action": "filter",
          "matches": [{
                  "key": "resource_name",
                  "value": "resource1"
              }
          ],
          "not_tags": [{
                  "key": "key1",
                  "values": [
                      "*value1",
                      "value2"
                  ]
              }
          ],
          "tags": [{
                  "key": "key1",
                  "values": [
                      "*value1",
                      "value2"
                  ]
              }
          ],
          "tags_any": [{
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "not_tags_any": [{
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ]
      }

-  When **action** is set to **count**:

   .. code-block::

      {
          "action": "count",
          "not_tags": [{
                  "key": "key1",
                  "values": [
                      "value1",
                      "*value2"
                  ]
              }
          ],
          "tags": [{
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "tags_any": [{
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "not_tags_any": [{
                  "key": "key1",
                  "values": [
                      "value1",
                      "value2"
                  ]
              }
          ],
          "matches": [{
                  "key": "resource_name",
                  "value": "resource1"
              }
          ]
      }

Response
--------

-  Parameter description

   .. table:: **Table 6** Parameter description

      +-------------+----------------+------------------------------------------------------------------------------------------------+
      | Parameter   | Type           | Description                                                                                    |
      +=============+================+================================================================================================+
      | resources   | List<resource> | List of matched resources (This parameter is not displayed if **action** is set to **count**.) |
      +-------------+----------------+------------------------------------------------------------------------------------------------+
      | total_count | Integer        | Total number of matched resources                                                              |
      +-------------+----------------+------------------------------------------------------------------------------------------------+

-  Parameter description of field **resource**

   .. table:: **Table 7** Parameter description of field **resource**

      +-----------------------+-----------------------+------------------------------------+
      | Parameter             | Type                  | Description                        |
      +=======================+=======================+====================================+
      | resource_id           | String                | Resource ID                        |
      +-----------------------+-----------------------+------------------------------------+
      | resource_detail       | Object                | Resource details                   |
      |                       |                       |                                    |
      |                       |                       | Backup details, including **tags** |
      +-----------------------+-----------------------+------------------------------------+
      | tags                  | List<resource_tag>    | Tag list                           |
      +-----------------------+-----------------------+------------------------------------+
      | resource_name         | String                | Resource name                      |
      +-----------------------+-----------------------+------------------------------------+

-  Parameter description of field **resource_detail**

   .. table:: **Table 8** Parameter description of field **resource_detail**

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
      | tags                  | List<resource_tag>    | Tag list                                                                                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | resource_type         | String                | Backup object type                                                                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **extend_info**

   .. table:: **Table 9** Parameter description of field **extend_info**

      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | Parameter              | Type                  | Description                                                                 |
      +========================+=======================+=============================================================================+
      | auto_trigger           | Boolean               | Whether automatic trigger is enabled                                        |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | average_speed          | Integer               | Average speed                                                               |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | copy_from              | String                | This parameter is left blank by default.                                    |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | copy_status            | String                | This parameter is left blank by default.                                    |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | fail_code              | fail_code             | Error code                                                                  |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | fail_op                | String                | Type of the failed operation                                                |
      |                        |                       |                                                                             |
      |                        |                       | Enum: [backup, restore, delete, verify, copy]                               |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | fail_reason            | String                | Description of the failure cause                                            |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | image_type             | String                | Backup type                                                                 |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | incremental            | Boolean               | Whether incremental backup is used                                          |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | progress               | Integer               | Backup progress. The value is an integer ranging from 0 to 100.             |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | resource_az            | String                | AZ to which the backup resource belongs                                     |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | resource_name          | String                | Backup object name                                                          |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | resource_type          | String                | Backup object type                                                          |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | size                   | Integer               | Backup capacity                                                             |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | space_saving_ratio     | Integer               | Space saving rate                                                           |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | volume_backups         | List<volume_backup>   | Disk backup list                                                            |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | finished_at            | String                | Backup completion time, for example, **2017-04-18T01:21:52.701973**         |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | supported_restore_mode | String                | Restoration mode. Possible values are **na**, **snapshot**, and **backup**. |
      |                        |                       |                                                                             |
      |                        |                       | **snapshot**: Data is restored from snapshots of the disks of the server.   |
      |                        |                       |                                                                             |
      |                        |                       | **backup**: Data is restored from backups of the disks of the server.       |
      |                        |                       |                                                                             |
      |                        |                       | **na**: Restoration is not supported.                                       |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+
      | tags                   | List<resource_tag>    | Tag list                                                                    |
      +------------------------+-----------------------+-----------------------------------------------------------------------------+

-  Parameter description of field **backup_data**

   .. table:: **Table 10** Parameter description of field **backup_data**

      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
      | Parameter                | Type                  | Description                                                                                                          |
      +==========================+=======================+======================================================================================================================+
      | \__openstack_region_name | String                | Name of the AZ where the ECS resides                                                                                 |
      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
      | cloudservicetype         | String                | ECS type                                                                                                             |
      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
      | disk                     | String                | System disk size corresponding to the ECS specifications                                                             |
      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
      | imagetype                | String                | Image type. Possible values are **gold** (public image), **private** (private image), and **market** (market image). |
      |                          |                       |                                                                                                                      |
      |                          |                       | Enum: [gold, private, market]                                                                                        |
      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
      | ram                      | String                | Memory size of the ECS, in MB                                                                                        |
      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
      | vcpus                    | String                | CPU cores corresponding to the ECS                                                                                   |
      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
      | eip                      | String                | Elastic IP address of the ECS                                                                                        |
      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+
      | private_ip               | String                | Internal IP address of the ECS                                                                                       |
      +--------------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **image_data**

   .. table:: **Table 11** Parameter description of field **image_data**

      ========= ====== ===========
      Parameter Type   Description
      ========= ====== ===========
      image_id  String Image ID
      ========= ====== ===========

-  Parameter description of field **fail_code**

   .. table:: **Table 12** Parameter description of field **fail_code**

      =========== ====== =================
      Parameter   Type   Description
      =========== ====== =================
      Code        Long   Error code
      Description String Error description
      =========== ====== =================

-  Parameter description of field **volume_backup**

   .. table:: **Table 13** Parameter description of field **volume_backup**

      +-----------------------+-----------------------+-------------------------------------------------------+
      | Parameter             | Type                  | Description                                           |
      +=======================+=======================+=======================================================+
      | average_speed         | Integer               | Average speed                                         |
      +-----------------------+-----------------------+-------------------------------------------------------+
      | bootable              | Boolean               | Whether the disk functions as a system disk           |
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

   .. table:: **Table 14** Parameter description of field **resource_tag**

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

   When **action** is set to **filter**:

   .. code-block::

      {
          "status":"aviable",
          "backup_data":{
              "eip":"",
              "cloudservicetype":"QEMU",
              "ram":1024,
              "__openstack_region_name":"",
              "vcpus":1,
              "private_ip":"",
              "disk":0,
              "imagetype":"gold"
          },
          "periodic_type":null,
          "name":"manualbk_ea67",
          "resource_id":"58482e0b-a357-4125-bdad-102f796b0e0c",
          "created_at":"2020-02-11T06:34:43.897750",
          "checkpoint_id":"ee45c782-71f8-4265-8392-e31fc701836c",
          "replication_records":[

          ],
          "updated_at":"2020-02-11T06:38:29.765609",
          "protected_at":"2020-02-11T06:30:26.000000",
          "tags":[

          ],
          "extend_info":{
              "auto_trigger":false,
              "finished_at":"2020-02-11T06:38:29.748932",
              "volume_backups":[

              ],
              "incremental":true,
              "copy_from":null,
              "dec_size":0,
              "size":0,
              "resource_az":"br-iaas-odin1b",
              "copy_status":"na",
              "image_type":"backup",
              "average_speed":0,
              "taskid":"e9c97c75-59fa-4b99-8b4b-1dd991dbba33",
              "progress":8,
              "resource_type":"OS::Nova::Server"
          },
          "progress":null,
          "expired_at":null,
          "id":"a6d04e0e-0121-41d1-8371-eaeab14482f8",
          "resource_type":"OS::Nova::Server",
          "description":"--"
      }

   When **action** is set to **count**:

   .. code-block::

      {
          total_count": 1000
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

   =========== =====================================================
   Status Code Description
   =========== =====================================================
   400         Invalid parameters.
   401         Authentication failed.
   403         You do not have permission to perform this operation.
   404         The requested resource was not found.
   500         A system exception occurs.
   =========== =====================================================

Error Codes
-----------

For details, see :ref:`Error Codes <en-us_topic_0071888297>`.
