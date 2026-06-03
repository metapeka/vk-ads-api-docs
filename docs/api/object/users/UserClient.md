# UserClient

The object contains data on a client and links to related objects.

Used in objects: [AgencyClient](https://ads.vk.com/en/doc/api/object/AgencyClient)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| account | [UserAccount](https://ads.vk.com/en/doc/api/object/UserAccount) | readable | Client balance data. |
| additional\_emails | list of email | readablewritable | The list that contains additional emails on the client. |
| additional\_info | [AdditionalClientInfo](https://ads.vk.com/en/doc/api/object/AdditionalClientInfo) | readablewritable | The object that contains additional data on the client. |
| id | id | readablewritabledefault\_fieldmin\_value=1max\_value=2147483647 | Client ID. |
| status | string | readable<br>choices = <br>- active \- Active.<br>- deleted \- Deleted.<br>- blocked \- Blocked. | Client status. |
| username | string | readable | Client name in VK Ads. |
