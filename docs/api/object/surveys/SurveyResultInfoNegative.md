# SurveyResultInfoNegative

An object describing the information for the negative final screen of a survey (stop screen).

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| title | string | readablewritablerequiredmax\_length=25 | Title of the final screen of the survey questionnaire. |
| description | string | readablewritablemax\_length=160 | Supporting text for the final screen of the survey questionnaire. |
| site\_url | url | readablewritablemax\_length=2000 | URL of an external landing page. The URL supports [UTM tagging](https://ads.vk.com/help/articles/utm#tags). |
| condition | [SurveyCondition](https://ads.vk.com/en/doc/api/object/SurveyCondition) | readablewritablerequired | The condition whose fulfillment will route the respondent to the negative final screen of the survey. |
