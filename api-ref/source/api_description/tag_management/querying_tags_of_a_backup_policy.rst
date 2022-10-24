:original_name: en-us_topic_0098635096.html

.. _en-us_topic_0098635096:

Querying Tags of a Backup Policy
================================

Function
--------

This API is used to query tags of a specific resource.

TMS uses this API to query all tags of a specific resource.

URI
---

-  URI format

   GET https://{endpoint}/v1/{project_id}/csbs_backup_policy/{resource_id}/tags

-  Request header

   .. table:: **Table 1** Request header

      +--------------+-----------+--------------------------------------+------------------+
      | Parameter    | Mandatory | Type                                 | Description      |
      +==============+===========+======================================+==================+
      | Content-type | Yes       | MIME type of the body in the request | application/json |
      +--------------+-----------+--------------------------------------+------------------+
      | X-Auth-Token | Yes       | User token                           | -                |
      +--------------+-----------+--------------------------------------+------------------+

-  Parameter description

   .. table:: **Table 2** Parameter description

      =========== ========= ====== ===========
      Parameter   Mandatory Type   Description
      =========== ========= ====== ===========
      project_id  Yes       String Project ID
      resource_id Yes       String Resource ID
      =========== ========= ====== ===========

Request
-------

-  Parameter description

   None

-  Example request

   .. code-block:: text

      GET https://{endpoint}/v1/{project_id}/csbs_backup_policy/{resource_id}/tags

Response
--------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+--------------------------------------+
      | Parameter             | Type                  | Description                          |
      +=======================+=======================+======================================+
      | tags                  | List<resource_tag>    | Tag list                             |
      |                       |                       |                                      |
      |                       |                       | Keys in the tag list must be unique. |
      +-----------------------+-----------------------+--------------------------------------+

-  Parameter description of field **resource_tag**

   .. table:: **Table 4** Parameter description of field **resource_tag**

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
      | value                 | List<String>          | Tag value                                                              |
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
             "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key2",
                  "value": "value3"
              }
          ]
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
