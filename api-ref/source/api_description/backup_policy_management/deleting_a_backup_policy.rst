:original_name: en-us_topic_0059304224.html

.. _en-us_topic_0059304224:

Deleting a Backup Policy
========================

Function
--------

This API is used to delete a backup policy by ID.

URI
---

-  URI format

   DELETE https://{endpoint}/v1/{project_id}/policies/{policy_id}

-  Parameter description

   .. table:: **Table 1** Parameter description

      ========== ========= ====== ================
      Parameter  Mandatory Type   Description
      ========== ========= ====== ================
      project_id Yes       String Project ID
      policy_id  Yes       String Backup policy ID
      ========== ========= ====== ================

Request
-------

-  Parameter description

None

-  Example request

   .. code-block:: text

      DELETE https://{endpoint}/v1/{project_id}/policies/{policy_id}

Response
--------

-  Parameter description

   None

-  Example response

   None

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
