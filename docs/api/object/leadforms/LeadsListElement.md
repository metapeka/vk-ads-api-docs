# LeadsListElement

An object describing an item in the list of leads from lead forms. It represents detailed information about a lead.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | string | readable | Lead identifier |
| form\_id | string | readable | Form identifier |
| form\_name | string | readable | Form name |
| ad\_plan\_id | uint32 | readable | Identifier of the ad campaign from which the lead was received |
| ad\_group\_id | uint32 | readable | Identifier of the ad group from which the lead was received |
| banner\_id | uint32 | readable | Identifier of the ad from which the lead was received |
| created\_at | datetime | readable | Lead received time |
| contact\_info | [ContactInfo](https://ads.vk.com/en/doc/api/object/LeadContactInfo) | readable | Lead contact details |
| answers | list of [LeadAnswer](https://ads.vk.com/en/doc/api/object/LeadAnswer) | readable | Lead's answers to the form questions |
