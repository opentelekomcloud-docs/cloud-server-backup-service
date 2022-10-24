:original_name: en-us_topic_0059304225.html

.. _en-us_topic_0059304225:

Updating a Backup Policy
========================

Function
--------

This API is used to update a backup policy by ID.

URI
---

-  URI format

   PUT https://{endpoint}/v1/{project_id}/policies/{policy_id}

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

   .. table:: **Table 2** Parameter description

      +-----------+-----------+---------------+--------------------------------------------------------------------------+
      | Parameter | Mandatory | Type          | Description                                                              |
      +===========+===========+===============+==========================================================================+
      | policy    | Yes       | policy_update | For details, see :ref:`Table 3 <en-us_topic_0059304225__table55930959>`. |
      +-----------+-----------+---------------+--------------------------------------------------------------------------+

-  Parameter description of field **policy_update**

   .. _en-us_topic_0059304225__table55930959:

   .. table:: **Table 3** Parameter description of field **policy_update**

      +----------------------+-----------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | Parameter            | Mandatory       | Type                             | Description                                                                                                       |
      +======================+=================+==================================+===================================================================================================================+
      | description          | No              | String                           | Backup policy description                                                                                         |
      |                      |                 |                                  |                                                                                                                   |
      |                      |                 |                                  | The value consists of 0 to 255 characters and must not contain a greater-than sign (>) or less-than sign (<).     |
      +----------------------+-----------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | name                 | No              | String                           | Backup policy name                                                                                                |
      |                      |                 |                                  |                                                                                                                   |
      |                      |                 |                                  | The value consists of 1 to 255 characters and can contain only letters, digits, underscores (_), and hyphens (-). |
      +----------------------+-----------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | resources            | No              | List<resource>                   | Backup objects                                                                                                    |
      |                      |                 |                                  |                                                                                                                   |
      |                      |                 |                                  | For details, see :ref:`Table 4 <en-us_topic_0059304225__table29479947>`.                                          |
      +----------------------+-----------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------+
      | scheduled_operations | No              | List<scheduled_operation_update> | Scheduling period. A backup policy has only one backup period.                                                    |
      |                      |                 |                                  |                                                                                                                   |
      |                      |                 |                                  | For details, see :ref:`Table 5 <en-us_topic_0059304225__table43297870>`.                                          |
      +----------------------+-----------------+----------------------------------+-------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **resource**

   .. _en-us_topic_0059304225__table29479947:

   .. table:: **Table 4** Parameter description of field **resource**

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

-  Parameter description of field **scheduled_operation_update**

   .. _en-us_topic_0059304225__table43297870:

   .. table:: **Table 5** Parameter description of field **scheduled_operation_update**

      +----------------------+-----------------+----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | Parameter            | Mandatory       | Type                 | Description                                                                                                                    |
      +======================+=================+======================+================================================================================================================================+
      | description          | No              | String               | Scheduling period description                                                                                                  |
      |                      |                 |                      |                                                                                                                                |
      |                      |                 |                      | The value consists of 0 to 255 characters and must not contain a greater-than sign (>) or less-than sign (<).                  |
      +----------------------+-----------------+----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | enabled              | No              | Boolean              | Whether the backup policy is enabled                                                                                           |
      |                      |                 |                      |                                                                                                                                |
      |                      |                 |                      | The default value is **true**. If it is set to **false**, automatic scheduling is disabled but manual scheduling is supported. |
      +----------------------+-----------------+----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | name                 | No              | String               | Scheduling period name                                                                                                         |
      |                      |                 |                      |                                                                                                                                |
      |                      |                 |                      | The value consists of 1 to 255 characters and can contain only letters, digits, underscores (_), and hyphens (-).              |
      +----------------------+-----------------+----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | operation_definition | No              | operation_definition | Scheduling period parameter                                                                                                    |
      |                      |                 |                      |                                                                                                                                |
      |                      |                 |                      | For details, see :ref:`Table 6 <en-us_topic_0059304225__table13129592>`.                                                       |
      +----------------------+-----------------+----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | trigger              | No              | trigger              | Scheduling policy                                                                                                              |
      +----------------------+-----------------+----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | id                   | Yes             | String               | Scheduling period ID                                                                                                           |
      +----------------------+-----------------+----------------------+--------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **operation_definition**

   .. _en-us_topic_0059304225__table13129592:

   .. table:: **Table 6** Parameter description of field **operation_definition**

      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter               | Mandatory | Type    | Description                                                                                                                                                                                                                             |
      +=========================+===========+=========+=========================================================================================================================================================================================================================================+
      | max_backups             | No        | Integer | Maximum number of backups that can be automatically created for a backup object. The value can be **-1** or ranges from **0** to **99999**. If the value is set to **-1**, backups will not be cleared by quantity limit.               |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | retention_duration_days | No        | Integer | Duration of retaining a backup, in days. The value can be **-1** or ranges from **0** to **99999**. If the value is set to **-1**, backups will not be cleared by retention duration.                                                   |
      +-------------------------+-----------+---------+-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | permanent               | No        | Boolean | Whether backups are permanently retained                                                                                                                                                                                                |
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

   .. table:: **Table 7** Parameter description of field **trigger**

      +-----------------+-----------------+--------------------+-------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type               | Description                                                             |
      +=================+=================+====================+=========================================================================+
      | properties      | Yes             | trigger_properties | Scheduler properties                                                    |
      |                 |                 |                    |                                                                         |
      |                 |                 |                    | For details, see :ref:`Table 8 <en-us_topic_0059304225__table9771641>`. |
      +-----------------+-----------------+--------------------+-------------------------------------------------------------------------+

-  Parameter description of field **trigger_properties**

   .. _en-us_topic_0059304225__table9771641:

   .. table:: **Table 8** Parameter description of field **trigger_properties**

      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter       | Mandatory       | Type            | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      +=================+=================+=================+========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | pattern         | Yes             | String          | Scheduling policy of the scheduler                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                 |                 |                 |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                 |                 |                 | The value consists of a maximum of 10,240 characters. The scheduling policy complies with iCalendar RFC 2445, but it supports only four parameters, which are **FREQ**, **BYDAY**, **BYHOUR**, and **BYMINUTE**. **FREQ** can be set to **WEEKLY** and **DAILY**, **BYDAY** can be set to **MO**, **TU**, **WE**, **TH**, **FR**, **SA**, and **SU** (seven days of a week), **BYHOUR** ranges from 0 hours to 23 hours, and **BYMINUTE** ranges from 0 minutes to 59 minutes. The scheduling interval must not be less than 1 hour. A maximum of 24 time points are allowed in a day. |
      +-----------------+-----------------+-----------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example request

   .. code-block:: text

      PUT https://{endpoint}/v1/{project_id}/policies/{policy_id}
      {
        "policy" : {
          "name" : "my-plan",
          "parameters" : {
            "common" : {
            }
          },
          "scheduled_operations" : [ {
            "id" : "fed3c8f1-7b6e-4e24-b1ad-473838bad569",
            "name" : "my-backup-policy",
            "description" : "My backup policy ",
            "enabled" : true,
            "operation_definition" : {
              "retention_duration_days" : -1,
              "max_backups" : 20
            },
            "trigger" : {
              "properties" : {
                "pattern" : "BEGIN:VCALENDAR\r\nBEGIN:VEVENT\r\nRRULE:FREQ=WEEKLY;BYDAY=TH;BYHOUR=12;BYMINUTE=27\r\nEND:VEVENT\r\nEND:VCALENDAR\r\n"
              }
           }
       }
          ]
        }
      }

Response
--------

-  Parameter description

   .. table:: **Table 9** Parameter description

      +-----------+-------------+---------------------------------------------------------------------------+
      | Parameter | Type        | Description                                                               |
      +===========+=============+===========================================================================+
      | policy    | policy_resp | For details, see :ref:`Table 10 <en-us_topic_0059304225__table21576622>`. |
      +-----------+-------------+---------------------------------------------------------------------------+

-  Parameter description of field **policy_resp**

   .. _en-us_topic_0059304225__table21576622:

   .. table:: **Table 10** Parameter description of field **policy_resp**

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
      |                       |                                | For details, see :ref:`Table 11 <en-us_topic_0059304225__table61263219>`.                                                                                                             |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | project_id            | String                         | Project ID                                                                                                                                                                            |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id           | String                         | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**. |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | resources             | List<resource>                 | Backup object list                                                                                                                                                                    |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | For details, see :ref:`Table 12 <en-us_topic_0059304225__table63079129>`.                                                                                                             |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | scheduled_operations  | List<scheduled_operation_resp> | Scheduling period list                                                                                                                                                                |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | For details, see :ref:`Table 13 <en-us_topic_0059304225__table37683621>`.                                                                                                             |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | status                | String                         | Backup policy status                                                                                                                                                                  |
      |                       |                                |                                                                                                                                                                                       |
      |                       |                                | -  **disabled**: indicates that the backup policy is unavailable.                                                                                                                     |
      |                       |                                | -  **enabled**: indicates that the backup policy is available.                                                                                                                        |
      +-----------------------+--------------------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **policy_param**

   .. _en-us_topic_0059304225__table61263219:

   .. table:: **Table 11** Parameter description of field **policy_param**

      +-----------+--------------+--------------------------------------------------------------+
      | Parameter | Type         | Description                                                  |
      +===========+==============+==============================================================+
      | common    | common_param | General backup policy parameters, which are blank by default |
      +-----------+--------------+--------------------------------------------------------------+

-  Parameter description of field **resource**

   .. _en-us_topic_0059304225__table63079129:

   .. table:: **Table 12** Parameter description of field **resource**

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

   .. _en-us_topic_0059304225__table37683621:

   .. table:: **Table 13** Parameter description of field **scheduled_operation_resp**

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
      |                       |                       | Enum:[ backup]                                                                                                                 |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | operation_definition  | operation_definition  | Scheduling period parameters                                                                                                   |
      |                       |                       |                                                                                                                                |
      |                       |                       | For details, see :ref:`Table 14 <en-us_topic_0059304225__table40981795>`.                                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | trigger               | trigger_resp          | Scheduling policy                                                                                                              |
      |                       |                       |                                                                                                                                |
      |                       |                       | For details, see :ref:`Table 15 <en-us_topic_0059304225__table20863269>`.                                                      |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+
      | id                    | String                | Scheduling period ID                                                                                                           |
      +-----------------------+-----------------------+--------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **operation_definition**

   .. _en-us_topic_0059304225__table40981795:

   .. table:: **Table 14** Parameter description of field **operation_definition**

      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter               | Type                  | Description                                                                                                                                                                           |
      +=========================+=======================+=======================================================================================================================================================================================+
      | max_backups             | String                | Maximum number of backups that can be automatically created for a backup object.                                                                                                      |
      |                         |                       |                                                                                                                                                                                       |
      |                         |                       | The value can be **-1** or ranges from **0** to **99999**. If the value is set to **-1**, backups will not be cleared by quantity limit.                                              |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | retention_duration_days | String                | Duration of retaining a backup, in days.                                                                                                                                              |
      |                         |                       |                                                                                                                                                                                       |
      |                         |                       | The value can be **-1** or ranges from **0** to **99999**. If the value is set to **-1**, backups will not be cleared by retention duration.                                          |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | permanent               | String                | Whether backups are permanently retained                                                                                                                                              |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | plan_id                 | String                | Backup policy ID                                                                                                                                                                      |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | provider_id             | String                | Backup provider ID, which specifies whether the backup object is a server or disk. This parameter has a fixed value. For CSBS, the value is **fc4d5750-22e7-4798-8a46-f48f62c4c1da**. |
      +-------------------------+-----------------------+---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Parameter description of field **trigger_resp**

   .. _en-us_topic_0059304225__table20863269:

   .. table:: **Table 15** Parameter description of field **trigger_resp**

      +-----------------------+-------------------------+---------------------------------------------------------------------------+
      | Parameter             | Type                    | Description                                                               |
      +=======================+=========================+===========================================================================+
      | properties            | trigger_properties_resp | Scheduler properties                                                      |
      |                       |                         |                                                                           |
      |                       |                         | For details, see :ref:`Table 16 <en-us_topic_0059304225__table28343023>`. |
      +-----------------------+-------------------------+---------------------------------------------------------------------------+

-  Parameter description of field **trigger_properties_resp**

   .. _en-us_topic_0059304225__table28343023:

   .. table:: **Table 16** Parameter description of field **trigger_properties_resp**

      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | Parameter             | Type                  | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      +=======================+=======================+========================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================================+
      | pattern               | String                | Scheduling policy of the scheduler                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                       |                       | The value consists of a maximum of 10,240 characters. The scheduling policy complies with iCalendar RFC 2445, but it supports only four parameters, which are **FREQ**, **BYDAY**, **BYHOUR**, and **BYMINUTE**. **FREQ** can be set to **WEEKLY** and **DAILY**, **BYDAY** can be set to **MO**, **TU**, **WE**, **TH**, **FR**, **SA**, and **SU** (seven days of a week), **BYHOUR** ranges from 0 hours to 23 hours, and **BYMINUTE** ranges from 0 minutes to 59 minutes. The scheduling interval must not be less than 1 hour. A maximum of 24 time points are allowed in a day. |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | start_time            | String                | Start time of the scheduler                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                            |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+
      | format                | String                | Scheduler type                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
      |                       |                       |                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                        |
      |                       |                       | The value is fixed at **ical** (Internet calendar).                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
      +-----------------------+-----------------------+----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------+

-  Example response

   .. code-block::

      {
        "policy" : {
          "status" : "disabled",
          "provider_id" : "fc4d5750-22e7-4798-8a46-f48f62c4c1da",
          "description" : "",
          "parameters" : {
            "common" : {
            }
          },
          "scheduled_operations" : [ {
            "description" : "My backup policy ",
            "enabled" : true,
            "trigger" : {
              "properties" : {
                "pattern" : "BEGIN:VCALENDAR\r\nBEGIN:VEVENT\r\nRRULE:FREQ=WEEKLY;BYDAY=TH;BYHOUR=12;BYMINUTE=27\r\nEND:VEVENT\r\nEND:VCALENDAR\r\n",
                "start_time" : "2017-04-09 14:31:25",
                "format" : "ical"
              }
            },
            "operation_definition" : {
              "provider_id" : "fc4d5750-22e7-4798-8a46-f48f62c4c1da",
              "plan_id" : "17e2b861-3a35-434d-afbb-073d5cd5af08",
              "max_backups" : "20",
              "retention_duration_days" : "-1",
              "permanent" : "False",

            },
            "operation_type" : "backup",
            "id" : "fed3c8f1-7b6e-4e24-b1ad-473838bad569",
            "name" : "my-backup-policy"
          }
      ,
                "format" : "ical"
         ],
          "id" : "17e2b861-3a35-434d-afbb-073d5cd5af08",
          "name" : "my-plan",
          "parameters" : {
            "common" : {
            }
          },
          "created_at" : "2017-04-09T14:31:25.504569",
          "project_id" : "0c89d4e457c3401a89c65420fd45f3a2",
          "resources" : [ {
            "type" : "OS::Nova::Server",
            "id" : "8421f405-1334-4206-b71c-b3f64d39abc4",
            "name" : "wqeq3",
            "extra_info" : {
          }
          } ]
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
