# SurveyResultInfo

An object describing the information for the final screen of a survey.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| positive | [SurveyResultInfoPositive](https://ads.vk.com/en/doc/api/object/SurveyResultInfoPositive) | readablewritablerequired | Positive final survey screen. positive will be shown to the respondent if the negative screen condition is not met. |
| negative | [SurveyResultInfoNegative](https://ads.vk.com/en/doc/api/object/SurveyResultInfoNegative) | readablewritable | Negative final survey screen. The respondent is taken to this screen immediately after meeting the specified condition. |
