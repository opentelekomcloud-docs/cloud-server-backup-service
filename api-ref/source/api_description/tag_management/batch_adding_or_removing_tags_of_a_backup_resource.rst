:original_name: en-us_topic_0098635087.html

.. _en-us_topic_0098635087:

Batch Adding or Removing Tags of a Backup Resource
==================================================

Function
--------

This API is used to add or remove tags of a specific resource in batches.

TMS may use this API to manage service resource tags.

A resource can have up to 10 tags.

The API is idempotent.

If there are duplicate keys in the request body when you add tags, an error is reported.

If the key of the to-be-created tag is the same as that of an existing tag, the value of the existing tag will be overwritten.

When deleting tags, you can upload duplicate keys.

When tags are being deleted and some tags do not exist, the operation is considered successful by default, and the character set of the tags will not be checked upon deletion. A key and a value can respectively consist of up to 127 and 255 characters. The tag structure cannot be missing, and the key cannot be left blank or an empty string.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/csbs_backup/{resource_id}/tags/action

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

   .. table:: **Table 3** Parameter description

      +-----------------+-----------------+--------------------+-----------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type               | Description                                                                       |
      +=================+=================+====================+===================================================================================+
      | tags            | Yes             | List<resource_tag> | Tag list                                                                          |
      |                 |                 |                    |                                                                                   |
      |                 |                 |                    | This list cannot be an empty list.                                                |
      |                 |                 |                    |                                                                                   |
      |                 |                 |                    | The list can contain up to 10 keys.                                               |
      |                 |                 |                    |                                                                                   |
      |                 |                 |                    | Keys in this list must be unique.                                                 |
      +-----------------+-----------------+--------------------+-----------------------------------------------------------------------------------+
      | action          | Yes             | String             | Operation to be performed. The value can be set to **create** or **delete** only. |
      +-----------------+-----------------+--------------------+-----------------------------------------------------------------------------------+

-  Parameter description of field **resource_tag**

   .. table:: **Table 4** Parameter description of field **resource_tag**

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                     |
      +=================+=================+=================+=================================================================================================================================================================+
      | key             | Yes             | String          | Tag key (when **action** is set to **create**)                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It consists of up to 36 characters.                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It cannot be an empty string.                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | Spaces before and after a key will be deprecated.                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It can contain only letters, digits, hyphens (-), and underscores (_).                                                                                          |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | Tag key (when **action** is set to **delete**)                                                                                                                  |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It consists of up to 127 characters.                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It cannot be an empty string.                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | Spaces before and after a key will be deprecated.                                                                                                               |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | value           | Yes             | String          | Tag value (when **action** is set to **create**)                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | This parameter is mandatory.                                                                                                                                    |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It consists of up to 43 characters.                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It can be an empty string.                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | Spaces before and after a tag value will be deprecated.                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It can contain only letters, digits, hyphens (-), and underscores (_).                                                                                          |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | Tag value (when **action** is set to **delete**)                                                                                                                |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | The tag value can be passed or not.                                                                                                                             |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It consists of up to 255 characters.                                                                                                                            |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | It can be an empty string.                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | Spaces before and after a tag value will be deprecated.                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                 |
      |                 |                 |                 | If the value is not passed, the tag is located and deleted based on the key and value. If the value is passed, the tag is located and deleted based on the key. |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      POST https://{endpoint}/v1/{project_id}/csbs_backup/{resource_id}/tags/action

-  Request body

   .. code-block::

      {
          "action": "create",
          "tags": [
              {
                  "key": "key1",
                  "value": "value1"
              },
              {
                  "key": "key",
                  "value": "value3"
              }
          ]
      }
      or
      {
          "action": "delete",
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

Response
--------

-  Parameter description

None

Status Codes
------------

-  Normal

   =========== ===========
   Status Code Description
   =========== ===========
   204         No Content
   =========== ===========

-  Abnormal

   =========== =====================================================
   Status Code Description
   =========== =====================================================
   400         Invalid action.
   401         Authentication failed.
   403         You do not have permission to perform this operation.
   404         The requested resource was not found.
   500         A system exception occurs.
   =========== =====================================================

Error Codes
-----------

For details, see :ref:`Error Codes <en-us_topic_0071888297>`.
