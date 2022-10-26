:original_name: en-us_topic_0059304219.html

.. _en-us_topic_0059304219:

Creating a Backup for a Resource
================================

Function
--------

This API is used to create a backup for a specified resource.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/providers/{provider_id}/resources/{resource_id}/action

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                                                                                                      |
      +=============+===========+========+==================================================================================================================================================================================================+
      | project_id  | Yes       | String | Project ID                                                                                                                                                                                       |
      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id | Yes       | String | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**.            |
      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_id | Yes       | String | ID of a backup server. For details about how to obtain the server ID, see the `Elastic Cloud Server API Reference <https://docs.otc.t-systems.com/en-us/api/ecs/en-us_topic_0020805967.html>`__. |
      +-------------+-----------+--------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. important::

      Backup provider IDs mentioned in this document are all **fc4d5750-22e7-4798-8a46-f48f62c4c1da**.

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                              |
      +=================+=================+=================+==========================================================================+
      | protect         | Yes             | protect_param   | Backup parameters                                                        |
      |                 |                 |                 |                                                                          |
      |                 |                 |                 | For details, see :ref:`Table 3 <en-us_topic_0059304219__table61231291>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+

-  Parameter description of field **protect_param**

   .. _en-us_topic_0059304219__table61231291:

   .. table:: **Table 3** Parameter description of field **protect_param**

      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type               | Description                                                                                                                                                                                |
      +=================+=================+====================+============================================================================================================================================================================================+
      | backup_name     | No              | String             | Backup name. The value consists of 1 to 255 characters and can contain only letters, digits, underscores (_), and hyphens (-).                                                             |
      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description     | No              | String             | Backup description. The value consists of 0 to 255 characters and must not contain a greater-than sign (>) or less-than sign (<).                                                          |
      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | incremental     | No              | Boolean            | Backup type. Value **True** indicates incremental backup and value **False** indicates full backup. For the initial backup, full backup is always adopted, in spite of which value is set. |
      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_type   | No              | String             | Entity object type of the backup object                                                                                                                                                    |
      |                 |                 |                    |                                                                                                                                                                                            |
      |                 |                 |                    | The current value is **OS::Nova::Server** indicating that the backup object is an ECS. If this parameter is not passed, the backup object type defaults to **OS::Nova::Server**.           |
      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags            | No              | List<resource_tag> | Tag list                                                                                                                                                                                   |
      |                 |                 |                    |                                                                                                                                                                                            |
      |                 |                 |                    | This list cannot be an empty list.                                                                                                                                                         |
      |                 |                 |                    |                                                                                                                                                                                            |
      |                 |                 |                    | The list can contain up to 10 keys.                                                                                                                                                        |
      |                 |                 |                    |                                                                                                                                                                                            |
      |                 |                 |                    | Keys in this list must be unique.                                                                                                                                                          |
      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | extra_info      | No              | Dict               | Additional information about the backup object                                                                                                                                             |
      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **resource_tag**

   .. table:: **Table 4** Parameter description of field **resource_tag**

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                            |
      +=================+=================+=================+========================================================================+
      | key             | Yes             | String          | Tag key                                                                |
      |                 |                 |                 |                                                                        |
      |                 |                 |                 | It consists of up to 36 characters.                                    |
      |                 |                 |                 |                                                                        |
      |                 |                 |                 | It cannot be an empty string.                                          |
      |                 |                 |                 |                                                                        |
      |                 |                 |                 | Spaces before and after a key will be deprecated.                      |
      |                 |                 |                 |                                                                        |
      |                 |                 |                 | It can contain only letters, digits, hyphens (-), and underscores (_). |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------+
      | value           | Yes             | String          | Tag value                                                              |
      |                 |                 |                 |                                                                        |
      |                 |                 |                 | It consists of up to 43 characters.                                    |
      |                 |                 |                 |                                                                        |
      |                 |                 |                 | It can be an empty string.                                             |
      |                 |                 |                 |                                                                        |
      |                 |                 |                 | Spaces before and after a tag value will be deprecated.                |
      |                 |                 |                 |                                                                        |
      |                 |                 |                 | It can contain only letters, digits, hyphens (-), and underscores (_). |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST
      https://{endpoint}/v1/b942cc8342734d15bcb246babb1953cf/providers/fc4d5750-22e7-4798-8a46-f48f62c4c1da/resources/9506416d-db6c-406e-8bca-c0f43793d914/action
      {
          "protect" : {
          "backup_name" : "backup",
          "description" : "backup des",
          "extra_info" : {
          }

        }
      }

Response
--------

-  Parameter description

   .. table:: **Table 5** Parameter description

      +-----------------------+-----------------------+-------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                             |
      +=======================+=======================+=========================================================================+
      | checkpoint            | protect_resp          | Backup response                                                         |
      |                       |                       |                                                                         |
      |                       |                       | For details, see :ref:`Table 6 <en-us_topic_0059304219__table6023603>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------+

-  Parameter description of field **protect_resp**

   .. _en-us_topic_0059304219__table6023603:

   .. table:: **Table 6** Parameter description of field **protect_resp**

      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                   |
      +=======================+=======================+===============================================================================================================================+
      | status                | String                | Backup status                                                                                                                 |
      |                       |                       |                                                                                                                               |
      |                       |                       | Value range: waiting_protect, protecting, available, waiting_restore, restoring, error, waiting_delete, deleting, and deleted |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | created_at            | String                | Creation time, for example, **2017-04-18T01:21:52.701973**                                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                | Backup record ID                                                                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | resource_graph        | String                | Resource diagram, which displays the inclusion relationship between backups and sub-backups                                   |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                | Project ID                                                                                                                    |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | protection_plan       | plan_resp             | Backup plan information                                                                                                       |
      |                       |                       |                                                                                                                               |
      |                       |                       | For details, see :ref:`Table 7 <en-us_topic_0059304219__table21049687>`.                                                      |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+
      | extra_info            | String                | Additional information                                                                                                        |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **plan_resp**

   .. _en-us_topic_0059304219__table21049687:

   .. table:: **Table 7** Parameter description of field **plan_resp**

      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                   |
      +=======================+=======================+===============================================================================+
      | id                    | String                | Backup policy ID                                                              |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | name                  | String                | Backup policy name                                                            |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+
      | resources             | List<resource>        | Backup object list                                                            |
      |                       |                       |                                                                               |
      |                       |                       | For details, see :ref:`Table 8 <en-us_topic_0059304219__table4765237103212>`. |
      +-----------------------+-----------------------+-------------------------------------------------------------------------------+

-  Parameter description of field **resource**

   .. _en-us_topic_0059304219__table4765237103212:

   .. table:: **Table 8** Parameter description of field **resource**

      +------------+--------+------------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Type   | Description                                                                                                                  |
      +============+========+==============================================================================================================================+
      | id         | String | Backup object ID                                                                                                             |
      +------------+--------+------------------------------------------------------------------------------------------------------------------------------+
      | type       | String | Entity object type of the backup object. The value is fixed at **OS::Nova::Server**, indicating that the object type is ECS. |
      +------------+--------+------------------------------------------------------------------------------------------------------------------------------+
      | name       | String | Backup object name                                                                                                           |
      +------------+--------+------------------------------------------------------------------------------------------------------------------------------+
      | extra_info | Dict   | Additional information about the backup object                                                                               |
      +------------+--------+------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "checkpoint" : {
          "status" : "protecting",
          "created_at" : "2017-04-18T01:21:52.701973",
          "id" : "4468f4b8-7c78-4222-a2ca-346b5d557dd2",
          "resource_graph" : null,
          "project_id" : "b942cc8342734d15bcb246babb1953cf",
          "extra_info" : null,
          "protection_plan" : {
            "id" : "fake_04f8ea0f-2000-4389-a5ce-93a3e20d0faf",
            "resources" : [ {
              "type" : "OS::Nova::Server",
              "id" : "9506416d-db6c-406e-8bca-c0f43793d914",
              "name" : "resource_9506416d-db6c-406e-8bca-c0f43793d914",
              "extra_info" : {
          }
            } ],
            "name" : "server protect plan for 9506416d-db6c-406e-8bca-c0f43793d914"
          }
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
