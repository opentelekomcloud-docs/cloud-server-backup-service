:original_name: en-us_topic_0059304223.html

.. _en-us_topic_0059304223:

Creating a Backup Policy
========================

Function
--------

This API is used to create a backup policy to back up servers periodically.

URI
---

-  URI format

   POST https://{endpoint}/v1/{project_id}/policies

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

   .. table:: **Table 2** Parameter description

      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                              |
      +=================+=================+=================+==========================================================================+
      | policy          | Yes             | policy_create   | Creation parameters                                                      |
      |                 |                 |                 |                                                                          |
      |                 |                 |                 | For details, see :ref:`Table 3 <en-us_topic_0059304223__table44181619>`. |
      +-----------------+-----------------+-----------------+--------------------------------------------------------------------------+

-  Parameter description of field **policy_create**

   .. _en-us_topic_0059304223__table44181619:

   .. table:: **Table 3** Parameter description of field **policy_create**

      +----------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter            | Mandatory       | Type                             | Description                                                                                                                                                                           |
      +======================+=================+==================================+=======================================================================================================================================================================================+
      | description          | No              | String                           | Backup policy description                                                                                                                                                             |
      |                      |                 |                                  |                                                                                                                                                                                       |
      |                      |                 |                                  | The value consists of 0 to 255 characters and must not contain a greater-than sign (>) or less-than sign (<).                                                                         |
      +----------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                 | Yes             | String                           | Backup policy name                                                                                                                                                                    |
      |                      |                 |                                  |                                                                                                                                                                                       |
      |                      |                 |                                  | The value consists of 1 to 255 characters and can contain only letters, digits, underscores (_), and hyphens (-).                                                                     |
      +----------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | parameters           | Yes             | policy_param                     | Backup parameters                                                                                                                                                                     |
      |                      |                 |                                  |                                                                                                                                                                                       |
      |                      |                 |                                  | For details, see :ref:`Table 4 <en-us_topic_0059304223__table37852877>`.                                                                                                              |
      +----------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id          | Yes             | String                           | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**. |
      +----------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resources            | Yes             | List<resource>                   | Backup object list. The list can be blank.                                                                                                                                            |
      |                      |                 |                                  |                                                                                                                                                                                       |
      |                      |                 |                                  | For details, see :ref:`Table 5 <en-us_topic_0059304223__table50789269>`.                                                                                                              |
      +----------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scheduled_operations | Yes             | List<scheduled_operation_create> | Scheduling period                                                                                                                                                                     |
      |                      |                 |                                  |                                                                                                                                                                                       |
      |                      |                 |                                  | For details, see :ref:`Table 6 <en-us_topic_0059304223__table23951472>`.                                                                                                              |
      +----------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                 | No              | List<resource_tag>               | Tag list                                                                                                                                                                              |
      |                      |                 |                                  |                                                                                                                                                                                       |
      |                      |                 |                                  | This list cannot be an empty list.                                                                                                                                                    |
      |                      |                 |                                  |                                                                                                                                                                                       |
      |                      |                 |                                  | The list can contain up to 10 keys.                                                                                                                                                   |
      |                      |                 |                                  |                                                                                                                                                                                       |
      |                      |                 |                                  | Keys in this list must be unique.                                                                                                                                                     |
      +----------------------+-----------------+----------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **policy_param**

   .. _en-us_topic_0059304223__table37852877:

   .. table:: **Table 4** Parameter description of field **policy_param**

      +-----------+-----------+--------------+--------------------------------------------------------------+
      | Parameter | Mandatory | Type         | Description                                                  |
      +===========+===========+==============+==============================================================+
      | common    | No        | common_param | General backup policy parameters, which are blank by default |
      +-----------+-----------+--------------+--------------------------------------------------------------+

-  Parameter description of field **resource**

   .. _en-us_topic_0059304223__table50789269:

   .. table:: **Table 5** Parameter description of field **resource**

      +-----------------+-----------------+-----------------+----------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                        |
      +=================+=================+=================+====================================================+
      | id              | Yes             | String          | Backup object ID                                   |
      +-----------------+-----------------+-----------------+----------------------------------------------------+
      | type            | Yes             | String          | Entity object type of backup objects               |
      |                 |                 |                 |                                                    |
      |                 |                 |                 | The value is fixed at **OS::Nova::Server** (ECSs). |
      +-----------------+-----------------+-----------------+----------------------------------------------------+
      | name            | Yes             | String          | Backup object name                                 |
      +-----------------+-----------------+-----------------+----------------------------------------------------+
      | extra_info      | No              | Dict            | Additional information about the backup object     |
      +-----------------+-----------------+-----------------+----------------------------------------------------+

-  Parameter description of field **scheduled_operation_create**

   .. _en-us_topic_0059304223__table23951472:

   .. table:: **Table 6** Parameter description of field **scheduled_operation_create**

      +----------------------+-----------------+----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter            | Mandatory       | Type                 | Description                                                                                                                                                     |
      +======================+=================+======================+=================================================================================================================================================================+
      | description          | No              | String               | Scheduling period description                                                                                                                                   |
      |                      |                 |                      |                                                                                                                                                                 |
      |                      |                 |                      | The value consists of 0 to 255 characters and must not contain a greater-than sign (>) or less-than sign (<).                                                   |
      +----------------------+-----------------+----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | enabled              | Yes             | Boolean              | Whether the backup policy is enabled                                                                                                                            |
      |                      |                 |                      |                                                                                                                                                                 |
      |                      |                 |                      | If it is set to **true**, automatic scheduling is enabled. If it is set to **false**, automatic scheduling is disabled but you can execute the policy manually. |
      +----------------------+-----------------+----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                 | No              | String               | Scheduling period name                                                                                                                                          |
      |                      |                 |                      |                                                                                                                                                                 |
      |                      |                 |                      | The value consists of 1 to 255 characters and can contain only letters, digits, underscores (_), and hyphens (-).                                               |
      +----------------------+-----------------+----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | operation_type       | Yes             | String               | Operation type                                                                                                                                                  |
      |                      |                 |                      |                                                                                                                                                                 |
      |                      |                 |                      | Enumeration values: **backup**                                                                                                                                  |
      +----------------------+-----------------+----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | operation_definition | Yes             | operation_definition | Scheduling period parameters                                                                                                                                    |
      |                      |                 |                      |                                                                                                                                                                 |
      |                      |                 |                      | For details, see :ref:`Table 7 <en-us_topic_0059304223__table19271238>`.                                                                                        |
      +----------------------+-----------------+----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | trigger              | Yes             | trigger              | Scheduling policy                                                                                                                                               |
      +----------------------+-----------------+----------------------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **operation_definition**

   .. _en-us_topic_0059304223__table19271238:

   .. table:: **Table 7** Parameter description of field **operation_definition**

      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter               | Mandatory | Type    | Description                                                                                                                                                                                                                             |
      +=========================+===========+=========+=========================================================================================================================================================================================================================================+
      | max_backups             | No        | Integer | Maximum number of backups that can be automatically created for a backup object. The value can be **-1** or ranges from **0** to **99999**. If the value is set to **-1**, backups will not be cleared by quantity limit.               |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | retention_duration_days | No        | Integer | Duration of retaining a backup, in days. The value can be **-1** or ranges from **0** to **99999**. If the value is set to **-1**, backups will not be cleared by retention duration.                                                   |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | permanent               | No        | Boolean | Whether backups are permanently retained. **false**: no. **true**: yes                                                                                                                                                                  |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | plan_id                 | No        | String  | Backup policy ID                                                                                                                                                                                                                        |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id             | No        | String  | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**.                                                   |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | day_backups             | No        | Integer | Maximum number of daily backups that can be retained. The latest backup of each day is saved in the long term. This parameter and **max_backups** will both be applied. If this parameter is configured, **timezone** is mandatory.     |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | week_backups            | No        | Integer | Maximum number of weekly backups that can be retained. The latest backup of each week is saved in the long term. This parameter and **max_backups** will both be applied. If this parameter is configured, **timezone** is mandatory.   |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | month_backups           | No        | Integer | Maximum number of monthly backups that can be retained. The latest backup of each month is saved in the long term. This parameter and **max_backups** will both be applied. If this parameter is configured, **timezone** is mandatory. |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | year_backups            | No        | Integer | Maximum number of yearly backups that can be retained. The latest backup of each year is saved in the long term. This parameter and **max_backups** will both be applied. If this parameter is configured, **timezone** is mandatory.   |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | timezone                | No        | String  | Time zone where the user is located, for example, UTC+08:00. Set this parameter only after you have configured any of the parameters **day_backups**, **week_backups**, **month_backups**, and **year_backups**.                        |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  If **permanent** is set to **true**, backups will be retained permanently, despite the settings of **max_backups** and **retention_duration_days**.
      -  If **permanent** is set to **false**, settings of **max_backups** and **retention_duration_days** are effective.
      -  If none of **permanent**, **max_backups**, and **retention_duration_days** is set, backups will be retained permanently.

-  Parameter description of field **trigger**

   .. table:: **Table 8** Parameter description of field **trigger**

      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type               | Description                                                              |
      +=================+=================+====================+==========================================================================+
      | properties      | Yes             | trigger_properties | Scheduler properties                                                     |
      |                 |                 |                    |                                                                          |
      |                 |                 |                    | For details, see :ref:`Table 9 <en-us_topic_0059304223__table47916689>`. |
      +-----------------+-----------------+--------------------+--------------------------------------------------------------------------+

-  Parameter description of field **trigger_properties**

   .. _en-us_topic_0059304223__table47916689:

   .. table:: **Table 9** Parameter description of field **trigger_properties**

      +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter | Mandatory | Type   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                               |
      +===========+===========+========+===========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | pattern   | Yes       | String | Scheduling policy of the scheduler. The value consists of a maximum of 10,240 characters. The scheduling policy complies with iCalendar RFC 2445, but it supports only four parameters, which are **FREQ**, **BYDAY**, **BYHOUR**, and **BYMINUTE**. **FREQ** can be set only to **WEEKLY** or **DAILY**. **BYDAY** can be set to **MO**, **TU**, **WE**, **TH**, **FR**, **SA**, or **SU** (seven days of a week). **BYHOUR** ranges from 0 to 23 hours. **BYMINUTE** ranges from 0 to 59 minutes. The scheduling interval cannot be less than 1 hour. A maximum of 24 time points are allowed in a day. |
      +-----------+-----------+--------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **resource_tag**

   .. table:: **Table 10** Parameter description of field **resource_tag**

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

      POST https://{endpoint}/v1/{project_id}/policies
      {
        "policy" : {
          "name" : "my-plan",
          "description" : "My plan",
          "provider_id" : "fc4d5750-22e7-4798-8a46-f48f62c4c1da",
          "parameters" : {
            "common" : {
            }
          },
          "scheduled_operations" : [ {
            "name" : "my-backup-policy",
            "description" : "My backup policy",
            "enabled" : true,
            "operation_definition" : {
              "max_backups" : 20
            },
            "trigger" : {
              "properties" : {
                "pattern" : "BEGIN:VCALENDAR\r\nBEGIN:VEVENT\r\nRRULE:FREQ=WEEKLY;BYDAY=TH;BYHOUR=12;BYMINUTE=27\r\nEND:VEVENT\r\nEND:VCALENDAR\r\n"
              }
            },
            "operation_type" : "backup"
          }

          ],
          "resources" : [ {
            "id" : "45baf976-c20a-4894-a7c3-c94b7376bf55",
            "type" : "OS::Nova::Server",
            "name" : "resource1",
          }, {
            "id" : "5aa119a8-d25b-45a7-8d1b-88e127885635",
            "type" : "OS::Nova::Server",
            "name" : "resource2"
          } ]
        }
      }

Response
--------

-  Parameter description

   .. table:: **Table 11** Parameter description

      +-----------+-------------+---------------------------------------------------------------------------+
      | Parameter | Type        | Description                                                               |
      +===========+=============+===========================================================================+
      | policy    | policy_resp | For details, see :ref:`Table 12 <en-us_topic_0059304223__table17548940>`. |
      +-----------+-------------+---------------------------------------------------------------------------+

-  Parameter description of field **policy_resp**

   .. _en-us_topic_0059304223__table17548940:

   .. table:: **Table 12** Parameter description of field **policy_resp**

      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                           | Description                                                                                                                                                                           |
      +=======================+================================+=======================================================================================================================================================================================+
      | created_at            | String                         | Creation time, for example, **2017-04-18T01:21:52.701973**                                                                                                                            |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | description           | String                         | Backup policy description                                                                                                                                                             |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | The value consists of 0 to 255 characters and must not contain a greater-than sign (>) or less-than sign (<).                                                                         |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                         | Backup policy ID                                                                                                                                                                      |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                         | Backup policy name                                                                                                                                                                    |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | The value consists of 1 to 255 characters and can contain only letters, digits, underscores (_), and hyphens (-).                                                                     |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | parameters            | policy_param                   | Parameters of a backup policy                                                                                                                                                         |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | For details, see :ref:`Table 13 <en-us_topic_0059304223__table60850186>`.                                                                                                             |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                         | Project ID                                                                                                                                                                            |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id           | String                         | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**. |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resources             | List<resource>                 | Backup object list                                                                                                                                                                    |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | For details, see :ref:`Table 14 <en-us_topic_0059304223__table8223017>`.                                                                                                              |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scheduled_operations  | List<scheduled_operation_resp> | Scheduling period list                                                                                                                                                                |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | For details, see :ref:`Table 15 <en-us_topic_0059304223__table27342530>`.                                                                                                             |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                         | Backup policy status                                                                                                                                                                  |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | **disabled**: indicates that the backup policy is unavailable.                                                                                                                        |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | **enabled**: indicates that the backup policy is available.                                                                                                                           |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | tags                  | List<resource_tag>             | Tag list                                                                                                                                                                              |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | Keys in the tag list must be unique.                                                                                                                                                  |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **policy_param**

   .. _en-us_topic_0059304223__table60850186:

   .. table:: **Table 13** Parameter description of field **policy_param**

      ========= ============ ====================================
      Parameter Type         Description
      ========= ============ ====================================
      common    common_param Common parameters of a backup policy
      ========= ============ ====================================

-  Parameter description of field **resource**

   .. _en-us_topic_0059304223__table8223017:

   .. table:: **Table 14** Parameter description of field **resource**

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
      | extra_info            | Dict                  | Additional information about the backup object     |
      +-----------------------+-----------------------+----------------------------------------------------+

-  Parameter description of field **scheduled_operation_resp**

   .. _en-us_topic_0059304223__table27342530:

   .. table:: **Table 15** Parameter description of field **scheduled_operation_resp**

      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                    |
      +=======================+=======================+================================================================================================================================+
      | description           | String                | Scheduling period description                                                                                                  |
      |                       |                       |                                                                                                                                |
      |                       |                       | The value consists of 0 to 255 characters and must not contain a greater-than sign (>) or less-than sign (<).                  |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | enabled               | Boolean               | Whether the scheduling period is enabled                                                                                       |
      |                       |                       |                                                                                                                                |
      |                       |                       | The default value is **true**. If it is set to **false**, automatic scheduling is disabled but manual scheduling is supported. |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                | Scheduling period name                                                                                                         |
      |                       |                       |                                                                                                                                |
      |                       |                       | The value consists of 1 to 255 characters and can contain only letters, digits, underscores (_), and hyphens (-).              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | operation_type        | String                | Operation type                                                                                                                 |
      |                       |                       |                                                                                                                                |
      |                       |                       | Enumeration values: **backup**                                                                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | operation_definition  | operation_definition  | Scheduling period parameters                                                                                                   |
      |                       |                       |                                                                                                                                |
      |                       |                       | For details, see :ref:`Table 16 <en-us_topic_0059304223__table63384596>`.                                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | trigger               | trigger_resp          | Scheduling policy                                                                                                              |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                | Scheduling period ID                                                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | trigger_id            | String                | Scheduler ID                                                                                                                   |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **operation_definition**

   .. _en-us_topic_0059304223__table63384596:

   .. table:: **Table 16** Parameter description of field **operation_definition**

      +-------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter               | Type   | Description                                                                                                                                                                                                               |
      +=========================+========+===========================================================================================================================================================================================================================+
      | max_backups             | String | Maximum number of backups that can be automatically created for a backup object. The value can be **-1** or ranges from **0** to **99999**. If the value is set to **-1**, backups will not be cleared by quantity limit. |
      +-------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | retention_duration_days | String | Duration of retaining a backup, in days. The value can be **-1** or ranges from **0** to **99999**. If the value is set to **-1**, backups will not be cleared by retention duration.                                     |
      +-------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | permanent               | String | Whether backups are permanently retained                                                                                                                                                                                  |
      +-------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | plan_id                 | String | Backup policy ID                                                                                                                                                                                                          |
      +-------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id             | String | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**.                                     |
      +-------------------------+--------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

   .. note::

      -  If **permanent** is set to **true**, backups will be retained permanently, despite the settings of **max_backups** and **retention_duration_days**.
      -  If **permanent** is set to **false**, settings of **max_backups** and **retention_duration_days** are effective.
      -  If none of **permanent**, **max_backups**, and **retention_duration_days** is set, backups will be retained permanently.

-  Parameter description of field **trigger_resp**

   .. table:: **Table 17** Parameter description of field **trigger_resp**

      +-----------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                    | Description                                                                                                             |
      +=======================+=========================+=========================================================================================================================+
      | properties            | trigger_properties_resp | Scheduler properties                                                                                                    |
      |                       |                         |                                                                                                                         |
      |                       |                         | For details, see :ref:`Parameter description of field trigger_properties_resp <en-us_topic_0059304223__table55128598>`. |
      +-----------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                  | Scheduler ID                                                                                                            |
      +-----------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | name                  | String                  | Scheduler name                                                                                                          |
      +-----------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------+
      | type                  | String                  | Scheduling type. The value is fixed at **time**.                                                                        |
      +-----------------------+-------------------------+-------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **trigger_properties_resp**

   .. _en-us_topic_0059304223__table55128598:

   .. table:: **Table 18** Parameter description of field **trigger_properties_resp**

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | pattern               | String                | Scheduling policy of the scheduler                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                       |                       | The value consists of a maximum of 10,240 characters. The scheduling policy complies with iCalendar RFC 2445, but it supports only four parameters, which are **FREQ**, **BYDAY**, **BYHOUR**, and **BYMINUTE**. **FREQ** can be set to **WEEKLY** and **DAILY**, **BYDAY** can be set to **MO**, **TU**, **WE**, **TH**, **FR**, **SA**, and **SU** (seven days of a week), **BYHOUR** ranges from 0 hours to 23 hours, and **BYMINUTE** ranges from 0 minutes to 59 minutes. The scheduling interval must not be less than 1 hour. A maximum of 24 time points are allowed in a day. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time            | String                | Scheduler start time, for example, **2017-04-18T01:21:52**                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                             |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | format                | String                | Scheduler type                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **resource_tag**

   .. table:: **Table 19** Parameter description of field **resource_tag**

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

   .. code-block::

      {
        "policy" : {
          "created_at" : "2017-03-07T09:27:40.928000",
          "description" : "My plan",
          "id" : "f766c171-9336-479a-8b30-b83cabf6381e",
          "name" : "my-plan",
          "parameters" : {
            "common" : {
            }
          },
          "project_id" : "tenant",
          "provider_id" : "c714180d-ea34-4b13-9a5e-577c7c416eec",
          "resources" : [ {
            "id" : "45baf976-c20a-4894-a7c3-c94b7376bf55",
            "name" : "resource1",
            "type" : "OS::Nova::Server",
            "extra_info" : {
          }
          }, {
            "id" : "5aa119a8-d25b-45a7-8d1b-88e127885635",
            "name" : "resource2",
            "type" : "OS::Nova::Server"
          } ],
          "scheduled_operations" : [ {
            "description" : "My backup policy",
            "enabled" : true,
            "id" : "9303a23d-e433-48e7-b88a-5ee6442e434e",
            "name" : "my-backup-policy",
            "operation_definition" : {
              "max_backups" : "20",
              "plan_id" : "f766c171-9336-479a-8b30-b83cabf6381e",
              "provider_id" : "c714180d-ea34-4b13-9a5e-577c7c416eec"
            },
            "operation_type" : "backup",
            "trigger" : {
              "id" : "8178846b-766d-4fe6-941f-b38c76b6f3b9",
              "name" : "default",
              "properties" : {
                "pattern" : "BEGIN:VCALENDAR\r\nBEGIN:VEVENT\r\nRRULE:FREQ=WEEKLY;BYDAY=TH;BYHOUR=12;BYMINUTE=27\r\nEND:VEVENT\r\nEND:VCALENDAR\r\n",
                "start_time" : "2017-03-07 09:27:41",
                "format" : "ical"
              },
              "type" : "time"
            },
            "trigger_id" : "8178846b-766d-4fe6-941f-b38c76b6f3b9"
          }
      ,
         ],
          "status" : "suspended"
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
