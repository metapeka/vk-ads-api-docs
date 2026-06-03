# UserManagerClient

The object provides data on a manager's client.

Used in objects: [AgencyManagerClient](https://ads.vk.com/en/doc/api/object/AgencyManagerClient)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| account | [UserAccount](https://ads.vk.com/en/doc/api/object/UserAccount) | readable | Level of manager access to the client account. |
| additional\_info | [AdditionalClientInfo](https://ads.vk.com/en/doc/api/object/AdditionalClientInfo) | readable | The object that contains additional information about the client. |
| id | id | readablewritabledefault\_fieldmin\_value=1max\_value=2147483647 | Client ID. |
| status | string | readable<br>choices = <br>- active \- Active.<br>- deleted \- Deleted.<br>- blocked \- Blocked. | Relationship status between client and manager. |
| username | string | readablewritable | Client name. |
