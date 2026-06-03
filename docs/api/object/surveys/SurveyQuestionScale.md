# SurveyQuestionScale

An object describing scale settings for a survey question.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| min\_value | integer | readablewritablerequiredmin\_value=0max\_value=1 | The minimum selectable value on the scale |
| max\_value | integer | readablewritablerequiredmin\_value=1max\_value=10 | The maximum selectable value on the scale |
| scale\_signs | list of string | readablewritablemax\_items=2max\_length=30 | Scale labels |
