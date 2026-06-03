# LeadFormQuestion

An object describing a lead form question.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| is\_required | boolean | readablewritable | Flag indicating whether the user must answer the question. Currently, all questions are required, so this flag must be set to `true`. |
| text | string | readablewritablerequiredmax\_length=68 | Question text |
| type | string | readablewritablerequired<br>choices = <br>- one\_answer \- A question where only one answer option can be selected<br>- multiple\_answers \- A question where multiple answer options can be selected<br>- text\_answer \- A question with a free-text answer | Question type |
| answers | list of [Answer](https://ads.vk.com/en/doc/api/object/LeadFormQuestionAnswer) | readablewritablerequiredmax\_items=7 | List of answer options. For questions with type=text\_answer, answer options should not be provided. For all other types, at least 2 answer options are required. Special option types must not be duplicated among the options. |
