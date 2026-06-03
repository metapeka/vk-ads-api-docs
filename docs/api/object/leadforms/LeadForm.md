# LeadForm

A resource for creating/modifying a lead form.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readabledefault\_field | Form identifier |
| name | string | readablewritablerequiredmax\_length=255 | Form name |
| status | integer | readablewritable<br>choices = <br>- 1 \- Active<br>- 2 \- Archived | Form status. Moving an active form to the archive and back is performed only via special requests. Forms in the archive cannot be updated. |
| created | datetime | readable | Creation time |
| updated | datetime | readable | Last update time |
| leads\_count | integer | readable | Number of leads collected by the form |
| ad\_plans\_count | integer | readable | Number of ad campaigns where the form is used |
| ad\_plan\_ids | list of uint32 | readable | IDs of ad campaigns where the form is used |
| ad\_group\_ids | list of uint32 | readable | IDs of ad groups where the form is used |
| banner\_ids | list of uint32 | readable | IDs of ads where the form is used |
| active\_ad\_plan\_ids | list of uint32 | readable | IDs of active ad campaigns where the form is used |
| first\_screen\_type | string | readablewritablerequired<br>choices = <br>- compact \- compact<br>- long\_text \- long description<br>- award \- information about the reward for completing the form | Type of the welcome section that the user sees immediately when opening the form |
| title | string | readablewritablerequiredmax\_length=50 | Form title |
| description | string | readablewritablemax\_length=35 | Form description. Displayed (and required) only when first\_screen\_type=compact |
| long\_description | string | readablewritablemax\_length=350 | Long form description. Displayed (and required) only when first\_screen\_type=long\_text. Maximum number of consecutive line breaks is 2. |
| company\_title | string | readablewritablerequiredmax\_length=30 | Company name |
| logo\_id | string | writeablerequired | Company logo identifier, returned when uploading the logo |
| logo | object | readable | Company logo |
| award | [Award](https://ads.vk.com/en/doc/api/object/LeadFormAward) | readablewriteable | Reward for completing the form. Displayed (and required) only when first\_screen\_type=award |
| gradient | integer | readablewritable<br>choices = <br>- 0 \- #FF7583 0%, #E62E40 100%<br>- 1 \- #FF80D5 0%, #E645B1 100%<br>- 2 \- #FFD54F 0%, #E7A902 100%<br>- 3 \- #6CD97E 0%, #12B312 100%<br>- 4 \- #8AE6E6 0%, #12B3B3 100%<br>- 5 \- #73D0FF 0%, #3885E1 100%<br>- 6 \- #FF4D87 0%, #9F40FF 100%<br>- 100 \- default color<br>- 101 \- color is taken from main\_color | Form background color. Values from 0 to 6 are gradients. |
| contact\_fields | list of string | readablewritablerequired<br>choices = <br>- first\_name \- First name<br>- email \- Email address<br>- phone \- Phone number<br>- birth\_date \- Date of birth<br>- city \- City<br>- social\_media\_profile \- Link to a social media profile | Contact details collected after answering the form questions |
| result\_info | [ResultInfo](https://ads.vk.com/en/doc/api/object/LeadFormResultInfo) | readablewriteablerequired | Information for the form's final screen |
| agreement | [Agreement](https://ads.vk.com/en/doc/api/object/LeadFormAgreement) | readablewriteablerequired | Form user agreement |
| notifications | list of [Notification](https://ads.vk.com/en/doc/api/object/LeadFormNotification) | readablewriteable | Form notification settings |
| pages | list of [Page](https://ads.vk.com/en/doc/api/object/LeadFormPage) | readablewriteablemax\_items=1 | List of form pages. If no pages are specified, the user will proceed directly to entering contact details when filling out the form. |
| required\_answers | boolean | readablewritable | Flag indicating whether questions are required |
| main\_color | string | readablewritable | Form primary color in HEX format (example: #FFFAAA) |
| main\_image\_id | string | writeable | Form cover identifier, returned when uploading the cover |
| main\_image | object | readable | Form cover |
