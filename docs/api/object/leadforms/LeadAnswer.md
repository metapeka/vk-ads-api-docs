# LeadAnswer

An object describing a lead's response to a form question.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| block\_id | string | readable | Form block identifier |
| question\_text | string | readable | The text of the question contained in the form block |
| answer\_options | list of [LeadAnswerOption](https://ads.vk.com/en/doc/api/object/LeadAnswerOption) | readable | The answer options selected by the lead for the form question |
| answer\_text | string | readable | The lead's free-text answer when such an option is selected, or when the question itself expects only a text answer |
