# SurveyPage

An object describing a survey page.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readabledefault\_field | Survey page identifier |
| blocks | list of [SurveyBlock](https://ads.vk.com/en/doc/api/object/SurveyBlock) | readablewriteablerequiredmax\_items=1 | List of blocks on the survey page |
| condition | [SurveyCondition](https://ads.vk.com/en/doc/api/object/SurveyCondition) | readablewritable | Condition for displaying the survey questionnaire page. If it is set and not satisfied, the screen will not be shown to the respondent filling out the survey questionnaire. |
