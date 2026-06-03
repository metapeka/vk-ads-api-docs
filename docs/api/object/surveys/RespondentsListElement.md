# RespondentsListElement

An object describing an item in the list of survey respondents. It represents detailed information about a respondent.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readable | Respondent identifier |
| survey\_id | string | readable | Survey identifier |
| survey\_name | string | readable | Survey name |
| ad\_plan\_id | uint32 | readable | Identifier of the ad campaign from which the respondent was acquired |
| ad\_group\_id | uint32 | readable | Identifier of the ad group from which the respondent was acquired |
| banner\_id | uint32 | readable | Identifier of the ad from which the respondent was acquired |
| created\_at | datetime | readable | Time when the respondent was acquired |
| answers | list of [RespondentAnswer](https://ads.vk.com/en/doc/api/object/RespondentAnswer) | readable | Respondent's answers to the survey questions |
| is\_direct | boolean | readable | A flag indicating how the respondent entered the survey. `True` — the respondent completed the survey questionnaire via a direct link. `False` — the respondent completed the survey questionnaire from an ad. |
