# SurveysListElement

An object describing an item in the survey list. It represents abbreviated information about a survey.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readable | Survey identifier |
| name | string | readable | Survey name |
| url | string | readable | Direct link to the survey |
| status | integer | readablewritable<br>choices = <br>- 1 \- Active<br>- 2 \- Archived | Survey status. Moving an active survey to the archive and back is performed only via special requests. Surveys in the archive cannot be updated. |
| created | datetime | readable | Creation time |
| updated | datetime | readable | Last update time |
| respondents\_count | integer | readable | Number of respondents collected by the survey |
| ad\_plans\_count | integer | readable | Number of ad campaigns in which the survey is used |
| ad\_plan\_ids | list of uint32 | readable | Identifiers of ad campaigns in which the survey is used |
| ad\_group\_ids | list of uint32 | readable | Identifiers of ad groups in which the survey is used |
| banner\_ids | list of uint32 | readable | Identifiers of ads in which the survey is used |
| active\_ad\_plan\_ids | list of uint32 | readable | Identifiers of active ad campaigns in which the survey is used |
| logo | object | readable | Company logo |
