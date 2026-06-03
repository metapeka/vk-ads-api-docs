# SurveyCondition

An object describing a survey screen display condition.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| operation\_tag | string | readablewritablerequired<br>choices = <br>- answer\_exists \- Checks whether the specified option is present among the respondent's answers<br>- or \- Combines nested conditions with a logical OR | The operation/check tag applied in the condition |
| value | object | readablewritablerequired<br>choices = <br>- [SurveyConditionAnswerExists](https://ads.vk.com/en/doc/api/object/SurveyConditionAnswerExists) \- The condition object used when operation\_tag=answer\_exists<br>- [SurveyConditionOr](https://ads.vk.com/en/doc/api/object/SurveyConditionOr) \- The condition object used when operation\_tag=or | The condition value object type |
