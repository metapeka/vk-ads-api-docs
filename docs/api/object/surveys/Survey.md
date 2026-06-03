# Survey

An object that describes a survey form.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readabledefault\_field | Survey identifier |
| name | string | readablewritablerequiredmax\_length=255 | Survey name |
| url | string | readable | Direct link to the survey |
| status | integer | readablewritable<br>choices = <br>- 1 \- Active<br>- 2 \- Archived | Survey status. Moving an active survey to the archive and back is performed only via special requests. Updates are not available for archived surveys. |
| created | datetime | readable | Creation time |
| updated | datetime | readable | Last update time |
| respondents\_count | integer | readable | Number of respondents collected by the survey |
| ad\_plans\_count | integer | readable | Number of ad campaigns in which the survey is used |
| ad\_plan\_ids | list of uint32 | readable | IDs of ad campaigns in which the survey is used |
| ad\_group\_ids | list of uint32 | readable | IDs of ad groups in which the survey is used |
| banner\_ids | list of uint32 | readable | IDs of ads (banners) in which the survey is used |
| active\_ad\_plan\_ids | list of uint32 | readable | IDs of active ad campaigns in which the survey is used |
| first\_screen\_type | string | readablewritablerequired<br>choices = <br>- text | Type of the first survey screen |
| title | string | readablewritablerequiredmax\_length=50 | Survey title |
| description | string | readablewritablemax\_length=35 | Survey description |
| company\_title | string | readablewritablerequiredmax\_length=30 | Company name |
| logo\_id | string | writeablerequired | Company logo identifier, returned when you [upload a logo](https://ads.vk.com/doc/api/resource/LeadFormImage) |
| logo | object | readable | Company logo |
| gradient | integer | readablewritable<br>choices = <br>- 0 \- #FF7583 0%, #E62E40 100%<br>- 1 \- #FF80D5 0%, #E645B1 100%<br>- 2 \- #FFD54F 0%, #E7A902 100%<br>- 3 \- #6CD97E 0%, #12B312 100%<br>- 4 \- #8AE6E6 0%, #12B3B3 100%<br>- 5 \- #73D0FF 0%, #3885E1 100%<br>- 6 \- #FF4D87 0%, #9F40FF 100% | Survey background color. Values from 0 to 6 are gradients. |
| result\_info | [SurveyResultInfo](https://ads.vk.com/en/doc/api/object/SurveyResultInfo) | readablewriteablerequired | Information for the final screen of the form |
| pages | list of [SurveyPage](https://ads.vk.com/en/doc/api/object/SurveyPage) | readablewriteablemax\_items=24 | List of survey pages |
| required\_answers | boolean | readablewritable | Flag indicating whether questions are required |
