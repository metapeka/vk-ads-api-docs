# AgencyClient

The object provides data on an agency client.

Used in resources: [AgencyClients](https://ads.vk.com/en/doc/api/resource/AgencyClients), [AgencyClient](https://ads.vk.com/en/doc/api/resource/AgencyClient)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| access\_type | string | readablerequiredwritabledefault\_field<br>choices = <br>- full\_access \- Full access.<br>- readonly \- Read only.<br>- fin\_readonly \- No access to the balance.<br>- ads\_readonly \- Access to the balance only. | Level of agency access to the client account. |
| status | string | readabledefault\_field<br>choices = <br>- active \- Active.<br>- deleted \- Deleted.<br>- blocked \- Blocked. | Relationship status between client and agency. |
| user | [UserClient](https://ads.vk.com/en/doc/api/object/UserClient) | readablewritabledefault\_field | Client. |
