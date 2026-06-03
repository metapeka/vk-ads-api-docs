# SurveyQuestionAnswer

An object describing an answer option for a survey question.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readablewritabledefault\_field | Answer option identifier. When creating a survey and using conditions, you must pass a temporary id for each answer (must have the `new_` prefix). This is required because in [SurveyConditionAnswerExists](https://ads.vk.com/en/doc/api/object/SurveyConditionAnswerExists) conditions are defined based on the answer id. After the survey is created, the temporary id will be replaced with the real one. When updating a survey, the `new_` prefix is required only for new answer options. |
| type | integer | readablewritable<br>choices = <br>- 0 \- Custom answer option<br>- 1 \- Special answer "Other"<br>- 2 \- Special answer "None of the above"<br>- 3 \- Special answer "Hard to say"<br>- 4 \- Special answer "Your own option" with the ability to answer in text | Answer option type |
| text | string | readablewritablemax\_length=40 | The answer option text itself. This field should be provided only if a custom answer option type is selected. |
