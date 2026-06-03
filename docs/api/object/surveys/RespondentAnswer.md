# RespondentAnswer

An object describing a respondent's answer to a survey question.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| block\_id | string | readable | Survey block identifier |
| question\_text | string | readable | The text of the question contained in the survey block |
| answer\_options | list of [RespondentAnswerOption](https://ads.vk.com/en/doc/api/object/RespondentAnswerOption) | readable | The answer options selected by the respondent for the survey question |
| answer\_text | string | readable | The respondent's free-text answer when such an option is selected, or when the question itself expects only a text answer |
| answer\_scale | integer | readable | The scale value selected by the respondent. If the specified survey block did not contain a scale, this field will be absent. |
