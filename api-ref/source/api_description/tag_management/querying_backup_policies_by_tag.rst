:original_name: en-us_topic_0098635092.html

.. _en-us_topic_0098635092:

Querying Backup Policies by Tag
===============================

Function
--------

This API is used to filter backup policies by tag.

TMS uses this API to filter and list resources of each service by tag. These services must have the query capabilities.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/csbs_backup_policy/resource_instances/action

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

   .. table:: **Table 3** Parameter description

      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                          |
      +=================+=================+=================+======================================================================================================================================================================================================================================================+
      | tags            | No              | List<tag>       | List of included tags. Backup resources with these tags will be filtered.                                                                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The list can contain up to 10 keys.                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list are in an AND relationship.                                                                                                                                                                                                        |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags_any        | No              | List<tag>       | List of tags. Backup resources with any tags in this list will be filtered.                                                                                                                                                                          |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The list can contain up to 10 keys.                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The response returns resources containing any tags in this list. Keys in this list are in an OR relationship while values in each key-value structure is in an OR relationship.                                                                      |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | not_tags        | No              | List<tag>       | List of excluded tags. Backup resources without these tags will be filtered.                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The list can contain up to 10 keys.                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The response returns resources containing no tags in this list. Keys in this list are in an AND relationship while values in each key-value structure is in an OR relationship.                                                                      |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | not_tags_any    | No              | List<tag>       | List of tags. Backup resources without any tags in this list will be filtered.                                                                                                                                                                       |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | This list cannot be an empty list.                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The list can contain up to 10 keys.                                                                                                                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | Keys in this list must be unique.                                                                                                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | The response returns resources without any tags in this list. Keys in this list are in an OR relationship while values in each key-value structure is in an OR relationship.                                                                         |
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
      | limit           | No              | String          | Query count (This parameter is not displayed if **action** is set to **count**.)                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | If **action** is set to **filter**, the value defaults to **1000**. The value ranges from **1** to **1000**. If you set a value out of this range, an error will be reported. The number of returned records does not exceed the value of **limit**. |
      +-----------------+-----------------+-----------------+------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | offset          | No              | String          | Query index (This parameter is not displayed if **action** is set to **count**.)                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                      |
      |                 |                 |                 | If **action** is set to **filter**, the value defaults to **0** (minimum value). The first record in the query result is the offset+1 record that meets the query criteria.                                                                          |
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

      POST https://{endpoint}/v1/{project_id}/csbs_backup_policy/resource_instances/action

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

      +-----------------------+-----------------------+--------------------------------------------+
      | Parameter             | Type                  | Description                                |
      +=======================+=======================+============================================+
      | resource_id           | String                | Resource ID                                |
      +-----------------------+-----------------------+--------------------------------------------+
      | resource_detail       | Object                | Resource details                           |
      |                       |                       |                                            |
      |                       |                       | The returned value is an empty dictionary. |
      +-----------------------+-----------------------+--------------------------------------------+
      | tags                  | List<resource_tag>    | Tag list                                   |
      +-----------------------+-----------------------+--------------------------------------------+
      | resource_name         | String                | Resource name                              |
      +-----------------------+-----------------------+--------------------------------------------+

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

   When **action** is set to **filter**:

   .. code-block::

      {
          "resources": [
              {
                  "resource_detail": {},
                  "resource_id": "cdfs_cefs_wesas_12_dsad",
                  "resource_name": "resouece1",
                  "tags": [
                      {
                         "key": "key1",
                         "value": "value1"
                      }
                   ]
               }
          ],
          "total_count": 1000
      }

   When **action** is set to **count**:

   .. code-block::

      {
             "total_count": 1000
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
