# SurveyQuestion

An object describing a survey question.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| is\_required | boolean | readablewritable | A flag indicating whether the respondent is required to answer the question. At the moment, all questions are required, so this flag must be set to `true`. |
| text | string | readablewritablerequiredmax\_length=68 | Question text |
| type | string | readablewritablerequired<br>choices = <br>- one\_answer \- A question that allows selecting only one answer option<br>- multiple\_answers \- A question that allows selecting multiple answer options<br>- text\_answer \- A question with a free-text answer<br>- scale\_answer \- A question with a scale | Question type |
| answers | list of [Answer](https://ads.vk.com/en/doc/api/object/SurveyQuestionAnswer) | readablewritablerequiredmax\_items=7 | List of answer options. For questions with type=text\_answer and type=scale\_answer, you do not need to specify answer options. For all other types, at least 2 answer options are required. Special answer option types must not be duplicated among the options. |
| scale | [Scale](https://ads.vk.com/en/doc/api/object/SurveyQuestionScale) | readablewritable | Scale settings. Must be provided only when type=scale\_answer. |
