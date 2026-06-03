# AdPlan

A resource for creating/modifying an ad campaign.

Used in resources: [AdPlans](https://ads.vk.com/en/doc/api/resource/AdPlans), [AdPlan](https://ads.vk.com/en/doc/api/resource/AdPlan)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | uint32 | readabledefault\_field | Campaign identifier |
| created | datetime | readable | Creation time |
| updated | datetime | readable | Last modified time |
| name | string | readablerequiredwritabledefault\_field | Campaign name |
| status | string | readablewritable<br>choices = <br>- active \- Active<br>- deleted \- Deleted<br>- blocked \- Blocked | Campaign status. The `deleted` status can also be returned for deleted campaigns. In a campaign with status `deleted`, only the status itself can be changed. |
| vkads\_status | object | readable | Activity and delivery status |
| ad\_groups | list of [AdGroup](https://ads.vk.com/en/doc/api/object/AdGroup) | readablewritablerequired | Groups |
| autobidding\_mode | string | readablewritable<br>choices = <br>- max\_goals \- Goal maximization (features: no bid; a total budget and campaign period or a daily budget must be set) | Auction strategy |
| budget\_limit | decimal | readablewritablemin\_value=-1 | Total campaign budget |
| budget\_limit\_day | decimal | readablewritablemin\_value=-1 | Daily campaign budget |
| date\_start | date | readablewritable | Campaign start date |
| date\_end | date | readablewritable | Campaign end date |
| max\_price | decimal | readablewritable | Upper limit for automatic price adjustment |
| objective | string | readablewritable | Campaign objective |
| priced\_goal | [PricedGoal](https://ads.vk.com/en/doc/api/object/PricedGoal) | readablewritable | Payment by TOP goals |
| pricelist\_id | int32 | readablewritable | Remarketing price list identifier |
| enable\_offline\_goals | boolean | readablewritable | Count offline conversions for the campaign |
