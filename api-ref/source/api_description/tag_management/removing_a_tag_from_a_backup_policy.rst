:original_name: en-us_topic_0098635095.html

.. _en-us_topic_0098635095:

Removing a Tag from a Backup Policy
===================================

Function
--------

The API is idempotent.

When you delete a nonexistent tag, error code **404** will be returned. Tag keys cannot be empty or be empty character strings.

URI
---

-  URI format

   DELETE https://{endpoint}/v1/{project_id}/csbs_backup_policy/{resource_id}/tags/{key}

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

      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                               |
      +=================+=================+=================+===========================================================================================================================================================================================================================================================+
      | project_id      | Yes             | String          | Project ID                                                                                                                                                                                                                                                |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resource_id     | Yes             | String          | Resource ID                                                                                                                                                                                                                                               |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | key             | Yes             | String          | Tag key                                                                                                                                                                                                                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | A tag key consists of up to 127 characters.                                                                                                                                                                                                               |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | A tag key cannot be an empty string.                                                                                                                                                                                                                      |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | Spaces before and after a key will be deprecated.                                                                                                                                                                                                         |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | It cannot contain the following characters: ASCII (0-31), asterisks (*), less-than signs (<), greater-than signs (>), backslashes (\), equal signs (=), commas (,), vertical bars (|), and slashes (/).                                                   |
      |                 |                 |                 |                                                                                                                                                                                                                                                           |
      |                 |                 |                 | (The code only verifies whether the key is an empty character string, instead of the length and character set. Keys are checked and used after deleting the spaces before and after them. Even invalid tags existing at the bottom layer can be deleted.) |
      +-----------------+-----------------+-----------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

Request
-------

-  Example request

   .. code-block:: text

      DELETE https://{endpoint}/v1/{project_id}/csbs_backup_policy/{resource_id}/tags/{key}

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
   400         Invalid parameters.
   401         Authentication failed.
   403         You do not have permission to perform this operation.
   404         The requested resource was not found.
   500         A system exception occurs.
   =========== =====================================================

Error Codes
-----------

For details, see :ref:`Error Codes <en-us_topic_0071888297>`.
