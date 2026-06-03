# LeadFormQuestionAnswer

An object describing an answer option for a lead form question.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readabledefault\_field | Answer option identifier |
| type | integer | readablewritable<br>choices = <br>- 0 \- Custom answer option<br>- 2 \- Special option "None of the above"<br>- 3 \- Special option "Hard to say"<br>- 4 \- Special option "Other" with the ability to enter a text answer | Answer option type |
| text | string | readablewritablemax\_length=40 | The answer option text. This field should be provided only if the custom answer option type is selected. |
