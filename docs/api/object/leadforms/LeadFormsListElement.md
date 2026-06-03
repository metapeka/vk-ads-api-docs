# LeadFormsListElement

An object describing an item in the lead forms list. It represents shortened information about a lead form.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readable | Form identifier |
| name | string | readable | Form name |
| status | integer | readablewritable<br>choices = <br>- 1 \- Active<br>- 2 \- Archived | Form status. Moving an active form to the archive and back is performed only via special requests. Forms in the archive cannot be updated. |
| created | datetime | readable | Creation time |
| updated | datetime | readable | Last update time |
| leads\_count | integer | readable | Number of leads collected by the form |
| ad\_plans\_count | integer | readable | Number of ad campaigns where the form is used |
| ad\_plan\_ids | list of uint32 | readable | IDs of ad campaigns where the form is used |
| ad\_group\_ids | list of uint32 | readable | IDs of ad groups where the form is used |
| banner\_ids | list of uint32 | readable | IDs of ads where the form is used |
| active\_ad\_plan\_ids | list of uint32 | readable | IDs of active ad campaigns where the form is used |
| notification\_actions | list of string | readable<br>choices = <br>- email \- Email<br>- vk \- VK Messenger | List of destinations configured for form event notifications |
| logo | object | readable | Company logo |
| main\_image | object | readable | Form cover |
