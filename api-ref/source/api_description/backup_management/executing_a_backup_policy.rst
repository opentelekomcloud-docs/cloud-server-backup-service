:original_name: en-us_topic_0059304230.html

.. _en-us_topic_0059304230:

Executing a Backup Policy
=========================

Function
--------

This API is used to manually execute a backup policy and create a backup task.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/providers/{provider_id}/checkpoints

-  Parameter description

   .. table:: **Table 1** Parameter description

      +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter   | Mandatory | Type   | Description                                                                                                                                                                           |
      +=============+===========+========+=======================================================================================================================================================================================+
      | project_id  | Yes       | String | Project ID                                                                                                                                                                            |
      +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id | Yes       | String | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**. |
      +-------------+-----------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Parameter description

   .. table:: **Table 2** Parameter description

      +------------+-----------+----------------+------------------------------------------------------------+
      | Parameter  | Mandatory | Type           | Description                                                |
      +============+===========+================+============================================================+
      | checkpoint | Yes       | checkpoint_req | For details, see the **checkpoint_req** field description. |
      +------------+-----------+----------------+------------------------------------------------------------+

-  Parameter description of field **checkpoint_req**

   .. table:: **Table 3** Parameter description of field **checkpoint_req**

      +------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter  | Mandatory | Type             | Description                                                                                                                                     |
      +============+===========+==================+=================================================================================================================================================+
      | parameters | Yes       | checkpoint_param | Backup parameters                                                                                                                               |
      +------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+
      | plan_id    | Yes       | String           | Backup policy ID. Refer to the backup policy ID that is returned by the API of :ref:`Querying the Backup Policy List <en-us_topic_0059304227>`. |
      +------------+-----------+------------------+-------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **checkpoint_param**

   .. table:: **Table 4** Parameter description of field **checkpoint_param**

      ============ ========= ============ ====================================
      Parameter    Mandatory Type         Description
      ============ ========= ============ ====================================
      auto_trigger No        Boolean      Whether automatic trigger is enabled
      resources    No        List<String> ID list of resources to be backed up
      ============ ========= ============ ====================================

-  Example request

   .. code-block:: text

      POST https://{endpoint}/v1/{project_id}/providers/{provider_id}/checkpoints
      {
        "checkpoint" : {
          "plan_id" : "62171999-3df1-42f7-9513-6f9b1bea4744",
          "parameters" : {
            "auto_trigger" : false,
            "resources" : [ "7a32a8b5-7977-4e24-b5da-e0eb457db75b", "b2b433bf-7dd6-4a74-aa8f-85673dfbda48" ]
          }
        }
      }

Response
--------

-  Parameter description

   .. table:: **Table 5** Parameter description

      +------------+-----------------+------------------------------------------------+
      | Parameter  | Type            | Description                                    |
      +============+=================+================================================+
      | checkpoint | checkpoint_resp | See the **checkpoint_resp** field description. |
      +------------+-----------------+------------------------------------------------+

-  Parameter description of field **checkpoint_resp**

   .. table:: **Table 6** Parameter description of field **checkpoint_resp**

      +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Type      | Description                                                                                                                                                                       |
      +=================+===========+===================================================================================================================================================================================+
      | status          | String    | Status. The value can be **protecting**, **deleting**, **available**, or **error**.                                                                                               |
      +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | created_at      | String    | Creation time, for example, 2016-12-06T21:20:29.898823                                                                                                                            |
      +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id              | String    | Backup record ID                                                                                                                                                                  |
      +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_graph  | String    | Resource diagram, which displays the mapping relationship between resources and backups. If the value is null, the backup contains only the resource backup of the entire system. |
      +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | project_id      | String    | Project ID                                                                                                                                                                        |
      +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | protection_plan | plan_resp | Backup policy information                                                                                                                                                         |
      +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | extra_info      | String    | Additional information about the backup object, such as the backup creation mode                                                                                                  |
      +-----------------+-----------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **plan_resp**

   .. table:: **Table 7** Parameter description of field **plan_resp**

      ========= ============== ==================
      Parameter Type           Description
      ========= ============== ==================
      id        String         Backup policy ID
      name      String         Backup policy name
      resources List<resource> Backup object list
      ========= ============== ==================

-  Parameter description of field **resource**

   .. table:: **Table 8** Parameter description of field **resource**

      +-----------------------+-----------------------+----------------------------------------------------+
      | Parameter             | Type                  | Description                                        |
      +=======================+=======================+====================================================+
      | id                    | String                | Backup object ID                                   |
      +-----------------------+-----------------------+----------------------------------------------------+
      | type                  | String                | Entity object type of backup objects               |
      |                       |                       |                                                    |
      |                       |                       | The value is fixed at **OS::Nova::Server** (ECSs). |
      +-----------------------+-----------------------+----------------------------------------------------+
      | name                  | String                | Backup object name                                 |
      +-----------------------+-----------------------+----------------------------------------------------+
      | extra_info            | String                | Additional information of the resource             |
      +-----------------------+-----------------------+----------------------------------------------------+

-  Example response

   .. code-block::

      {
        "checkpoint" : {
          "status" : "protecting",
          "created_at" : "2016-12-06T21:20:29.898823",
          "id" : "14626f11-b54a-44ea-8e69-7463e527506a",
          "resource_graph" : null,
          "project_id" : "b942cc8342734d15bcb246babb1953cf",
          "protection_plan" : {
            "id" : "6a6cda7e-7b89-4b14-8e5c-3b6821a97d2c",
            "resources" : [ {
              "type" : "OS::Nova::Server",
              "id" : "1c960fe4-e679-421a-97cd-4f7463d2344b",
              "name" : "server0",
              "extra_info": "{}"
            } ],
            "name" : "backup"
          },
          "extra_info": "{"created_by": "manual"}"
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
