:original_name: en-us_topic_0059304221.html

.. _en-us_topic_0059304221:

Querying the Restoration Capability of a Resource
=================================================

Function
--------

This API is used to check whether a target resource can be restored.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/providers/{provider_id}/resources/action

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

      +------------------+-----------------+------------------------+--------------------------------------------------------------------------+
      | Parameter        | Mandatory       | Type                   | Description                                                              |
      +==================+=================+========================+==========================================================================+
      | check_restorable | Yes             | List<restorable_param> | Query parameter list                                                     |
      |                  |                 |                        |                                                                          |
      |                  |                 |                        | For details, see :ref:`Table 3 <en-us_topic_0059304221__table13617924>`. |
      +------------------+-----------------+------------------------+--------------------------------------------------------------------------+

-  Parameter description of field **restorable_param**

   .. _en-us_topic_0059304221__table13617924:

   .. table:: **Table 3** Parameter description of field **restorable_param**

      +--------------------+-----------------+-------------------+--------------------------------------------------------------------------+
      | Parameter          | Mandatory       | Type              | Description                                                              |
      +====================+=================+===================+==========================================================================+
      | checkpoint_item_id | Yes             | String            | ID of the backup used to restore data                                    |
      +--------------------+-----------------+-------------------+--------------------------------------------------------------------------+
      | target             | Yes             | restorable_target | Restoration target                                                       |
      |                    |                 |                   |                                                                          |
      |                    |                 |                   | For details, see :ref:`Table 4 <en-us_topic_0059304221__table29307618>`. |
      +--------------------+-----------------+-------------------+--------------------------------------------------------------------------+

-  Parameter description of field **restorable_target**

   .. _en-us_topic_0059304221__table29307618:

   .. table:: **Table 4** Parameter description of field **restorable_target**

      +-----------------+-----------------+------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type                         | Description                                                                                                        |
      +=================+=================+==============================+====================================================================================================================+
      | resource_id     | Yes             | String                       | ID of the resource to which the backup is restored                                                                 |
      +-----------------+-----------------+------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | resource_type   | Yes             | String                       | Type of the target to which the backup is restored, for example, **OS::Nova::Server** for an ECS                   |
      +-----------------+-----------------+------------------------------+--------------------------------------------------------------------------------------------------------------------+
      | volumes         | Yes             | List<restore_volume_mapping> | Disk mapping list for restoring an ECS. Enter the mapping between disks and backups based on the actual situation. |
      |                 |                 |                              |                                                                                                                    |
      |                 |                 |                              | For details, see :ref:`Table 5 <en-us_topic_0059304221__table52713489>`.                                           |
      +-----------------+-----------------+------------------------------+--------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **restore_volume_mapping**

   .. _en-us_topic_0059304221__table52713489:

   .. table:: **Table 5** Parameter description of field **restore_volume_mapping**

      +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                                                                                           |
      +===========+===========+========+=======================================================================================================================+
      | backup_id | Yes       | String | Disk backup ID. Use the API in :ref:`Querying a Single Backup <en-us_topic_0059304234>` to obtain the disk backup ID. |
      +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+
      | volume_id | Yes       | String | ID of the destination disk for the restoration                                                                        |
      +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{endpoint}/v1/{project_id}/providers/{provider_id}/resources/action
      {
        "check_restorable" : [ {
          "checkpoint_item_id" : "8986ce68-3da7-4d29-9cc2-1921e9504975",
          "target" : {
            "resource_type" : "OS::Nova::Server",
            "resource_id" : "5aa119a8-d25b-45a7-8d1b-88e127885635",
            "volumes" : [ {
              "backup_id" : "7ea119a8-d25b-43a7-8d1b-88e12788513a",
              "volume_id" : "45baf976-c20a-4894-a7c3-c94b7376bf55"
            } ]
          }
        } ]
      }

Response
--------

-  Parameter description

   .. table:: **Table 6** Parameter description

      +-----------------------+-----------------------+--------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                              |
      +=======================+=======================+==========================================================================+
      | restorable            | List<check_resp>      | Response parameter list                                                  |
      |                       |                       |                                                                          |
      |                       |                       | For details, see :ref:`Table 7 <en-us_topic_0059304221__table56868375>`. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------+

-  Parameter description of field **check_resp**

   .. _en-us_topic_0059304221__table56868375:

   .. table:: **Table 7** Parameter description of field **check_resp**

      ============= ======= ====================================
      Parameter     Type    Description
      ============= ======= ====================================
      result        Boolean Whether the resource can be restored
      resource_type String  Resource type
      error_code    String  Error code
      error_msg     String  Error reason
      resource_id   String  Resource ID
      ============= ======= ====================================

-  Example response

   .. code-block::

      {
        "restorable" : [ {
          "resource_id" : "6507cb66-90dc-4a12-a573-c9f3398f899d",
          "resource_type" : "OS::Nova::Server",
          "result" : true,
          "error_msg" : "",
          "error_code" : ""
        } ]
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
