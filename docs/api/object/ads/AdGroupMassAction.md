# AdGroupMassAction

An object containing changes to a group's data.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | int32 | readablerequiredwritabledefault\_fieldmin\_value=1max\_value=2147483647 | Ad group identifier |
| status | string | readablewritabledefault\_field<br>choices = <br>- active \- Active<br>- deleted \- Deleted<br>- blocked \- Blocked | Ad group status |
| targetings | [TargetingsMassAction](https://ads.vk.com/en/doc/api/object/TargetingsMassAction) | readablewritable | Targeting structure |
| budget\_limit | decimal | readablewritable | Total ad group budget |
| budget\_limit\_day | decimal | readablewritable | Daily ad group budget |
| date\_start | date | readablewritable | Start date |
| date\_end | date | readablewritable | End date |
| max\_price | decimal | readablewritable | Conversion price cap |
