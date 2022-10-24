:original_name: en-us_topic_0059304243.html

.. _en-us_topic_0059304243:

Querying Quotas
===============

Function
--------

This API is used to query tenant quotas.

URI
---

-  URI format

   GET https://{endpoint}/v1/{project_id}/quotas

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

   None

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v1/{project_id}/quotas

Response
--------

-  Parameter description

   .. table:: **Table 2** Parameter description

      ========= ===== ====================================
      Parameter Type  Description
      ========= ===== ====================================
      quotas    quota See the **quota** field description.
      ========= ===== ====================================

-  Parameter description of field **quota**

   .. table:: **Table 3** Parameter description of field **quota**

      ========= =================== ===============
      Parameter Type                Description
      ========= =================== ===============
      resources List<resource_resp> Quota resources
      ========= =================== ===============

-  Parameter description of field **resource_resp**

   .. table:: **Table 4** Parameter description of field **resource_resp**

      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                               |
      +=======================+=======================+===========================================================================================================================+
      | unit                  | String                | Unit                                                                                                                      |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | used                  | Integer               | Used quota                                                                                                                |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | quota                 | Integer               | Quota size                                                                                                                |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                | Type                                                                                                                      |
      |                       |                       |                                                                                                                           |
      |                       |                       | **backup_capacity** specifies the backup storage capacity quota. Value **-1** indicates no restriction on the quota size. |
      |                       |                       |                                                                                                                           |
      |                       |                       | **backups** specifies the number of retained backups.                                                                     |
      +-----------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "quotas" : {
          "resources" : [{
            "type" : "backup_capacity",
            "unit" : "GB",
            "quota" : -1,
            "used" : 0
          },
          {
              "used": 0,
              "type": "backups",
              "quota": 600
          }]
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
