# UserSegment

Data source that that can be accessed with the key.

Used in objects: [SharingKeyUser](https://ads.vk.com/en/doc/api/object/SharingKeyUser)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| key | string | readable | Access key. |
| object\_id | integer | readablerequiredwritabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Data source ID. |
| object\_type | string | readablerequiredwritabledefault\_field<br>choices = <br>- users\_list \- Users list.<br>- counter \- Counter.<br>- campaign\_list \- Campaigns list.<br>- custom\_audience \- Typical audience.<br>- pricelist \- Price list.<br>- segment \- Audience segment.<br>- lookalike\_audience \- Lookalike audience. | Data source type. |
| params | object | readabledefault\_field | Data source parameters: - "id" - "name" - "entries\_count" - "type" |
