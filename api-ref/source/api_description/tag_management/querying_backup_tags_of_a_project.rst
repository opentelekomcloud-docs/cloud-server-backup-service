:original_name: en-us_topic_0098635091.html

.. _en-us_topic_0098635091:

Querying Backup Tags of a Project
=================================

Function
--------

This API is used to query a tenant's tag set in a specific region and of a specific resource type.

TMS uses this API to list tags created by a tenant to facilitate tag creation and resource filtering on the console.

URI
---

-  URI format

   GET https://{endpoint}/v1/{project_id}/csbs_backup/tags

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

      GET https://{endpoint}/v1/{project_id}/csbs_backup/tags

Response
--------

-  Parameter description

   .. table:: **Table 3** Parameter description

      +-----------------------+-----------------------+--------------------------------------+
      | Parameter             | Type                  | Description                          |
      +=======================+=======================+======================================+
      | tags                  | List<tag>             | Tag list                             |
      |                       |                       |                                      |
      |                       |                       | Keys in the tag list must be unique. |
      +-----------------------+-----------------------+--------------------------------------+

-  Parameter description of field **tag**

   .. table:: **Table 4** Parameter description of field **tag**

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
      | values                | List<String>          | List of tag values                                                     |
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
                  "values": [
                      "value1",
                      "value2"
                   ]
              },
              {
                  "key": "key2",
                  "values": [
                      "value1",
                      "value2"
                   ]
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
