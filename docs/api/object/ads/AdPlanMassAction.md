# AdPlanMassAction

An object containing changes to campaign data.

Used in resources: [AdPlanMassAction](https://ads.vk.com/en/doc/api/resource/AdPlanMassAction)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | int32 | readablerequiredwritabledefault\_fieldmin\_value=1max\_value=2147483647 | Campaign identifier |
| status | string | readablewritabledefault\_field<br>choices = <br>- active \- Active<br>- deleted \- Deleted<br>- blocked \- Blocked | Campaign status |
| budget\_limit | decimal | readablewritable | Total campaign budget |
| budget\_limit\_day | decimal | readablewritable | Daily campaign budget |
| date\_start | date | readablewritable | Start date |
| date\_end | date | readablewritable | End date |
| max\_price | decimal | readablewritable | Conversion price cap |
