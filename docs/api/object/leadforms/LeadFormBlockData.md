# LeadFormBlockData

An object describing the data of a lead form block.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| type | string | readablewritablerequired<br>choices = <br>- question \- Question | Form block data type |
| data | object | readablewritablerequired | Form block data. For type=question, an object of type [Question](https://ads.vk.com/en/doc/api/object/LeadFormQuestion) is expected. |
