:original_name: en-us_topic_0098635094.html

.. _en-us_topic_0098635094:

Adding a Tag to a Backup Policy
===============================

Function
--------

A resource can have up to 10 tags.

The API is idempotent.

If a to-be-created tag has the same key as an existing tag, the tag will be created and overwrite the existing one.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/csbs_backup_policy/{resource_id}/tags

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

      ========= ========= ==== ============
      Parameter Mandatory Type Description
      ========= ========= ==== ============
      tag       Yes       tag  List of tags
      ========= ========= ==== ============

-  Parameter description of field **tag**

   .. table:: **Table 4** Parameter description of field **tag**

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

      POST https://{endpoint}/v1/{project_id}/csbs_backup_policy/{resource_id}/tags

-  Request body

   .. code-block::

      {
          "tag":
          {
              "key":"DEV",
              "value":"DEV1"
          }
      }

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
