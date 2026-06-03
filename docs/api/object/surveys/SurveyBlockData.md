# SurveyBlockData

An object describing the data of a survey block.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| type | string | readablewritablerequired<br>choices = <br>- question \- Question | Survey block data type |
| data | object | readablewritablerequired | Form block data. When type=question, a [Question](https://ads.vk.com/en/doc/api/object/SurveyQuestion) object is expected. |
