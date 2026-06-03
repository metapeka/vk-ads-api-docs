# ManagerClientInfo

The object provides data on a manager client.

Used in objects: [UserManager](https://ads.vk.com/en/doc/api/object/UserManager)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| access\_type | string | readable<br>choices = <br>- full\_access \- Full access.<br>- readonly \- Read only.<br>- fin\_readonly \- No access to the balance.<br>- ads\_readonly \- Access to the balance only. | Level of manager access to the client account. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Client ID. |
