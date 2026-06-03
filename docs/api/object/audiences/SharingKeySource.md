# SharingKeySource

The object describes a data sources of the key.

Used in objects: [SharingKey](https://ads.vk.com/en/doc/api/object/SharingKey)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| key | string | readable | The sharing key. |
| object\_id | integer | readablerequiredwritabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | The data source id. |
| object\_type | string | readablerequiredwritabledefault\_field<br>choices = <br>- users\_list<br>- counter<br>- campaign\_list<br>- custom\_audience<br>- pricelist<br>- segment<br>- lookalike\_audience | The type of data source. |
