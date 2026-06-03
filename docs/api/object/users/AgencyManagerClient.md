# AgencyManagerClient

The object provides data on a manager's client.

Used in resources: [AgencyManagerClient](https://ads.vk.com/en/doc/api/resource/AgencyManagerClient)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| access\_type | string | readablerequiredwritabledefault\_field<br>choices = <br>- full\_access \- Full access.<br>- readonly \- Read only.<br>- fin\_readonly \- No access to the balance.<br>- ads\_readonly \- Access to the balance only. | Level of manager access to the client account. |
| status | string | readabledefault\_field<br>choices = <br>- active \- Active.<br>- deleted \- Deleted.<br>- blocked \- Blocked. | Relationship status between client and manager. |
| user | [UserManagerClient](https://ads.vk.com/en/doc/api/object/UserManagerClient) | readablewritabledefault\_field | Client. Returned in the GET request. |
