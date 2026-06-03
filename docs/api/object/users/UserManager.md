# UserManager

The object contains data on an agency manager and links to related objects.

Used in objects: [AgencyManager](https://ads.vk.com/en/doc/api/object/AgencyManager)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| additional\_info | [AdditionalManagerInfo](https://ads.vk.com/en/doc/api/object/AdditionalManagerInfo) | readablewritable | The object that contains additional data on the manager. |
| clients | list of [ManagerClientInfo](https://ads.vk.com/en/doc/api/object/ManagerClientInfo) | readable | List of manager clients. |
| id | id | readablewritabledefault\_fieldmin\_value=1max\_value=2147483647 | Manager ID. |
| username | string | readablewritable | Manager name in VK Ads. |
