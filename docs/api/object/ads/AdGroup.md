# AdGroup

A resource for creating/modifying an ad group.

The available fields, targeting options, and other ad group settings are described in the [package object](https://ads.vk.com/en/doc/api/object/Package) within which the campaign is created.

Used in resources: [AdGroups](https://ads.vk.com/en/doc/api/resource/AdGroups)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | uint32 | readabledefault\_field | Group identifier |
| created | datetime | readable | Creation time |
| updated | datetime | readable | Last update time |
| name | string | readablerequiredwritabledefault\_field | Group name |
| status | string | readablewritable<br>choices = <br>- active \- Active<br>- deleted \- Deleted<br>- blocked \- Blocked | Group status. The `deleted` status may also be returned for deleted groups. In a group with status `deleted`, only the status itself can be changed. |
| ad\_plan\_id | uint32 | readablewritabledefault\_fieldmin\_value=1max\_value=2147483647 | Identifier of the [campaign](https://ads.vk.com/en/doc/api/object/AdPlan) |
| package\_id | integer | readablerequiredwritabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Identifier of the [package](https://ads.vk.com/en/doc/api/object/Package) |
| age\_restrictions | string | readablewritable | Age restrictions. Validated by the pattern `^[1-9]?[0-9]\\\\+$` |
| audit\_pixels | list of [AuditPixel](https://ads.vk.com/en/doc/api/object/AuditPixel) | readablewritable | List of audit pixels |
| autobidding\_mode | string | readablewritable<br>choices = <br>- max\_goals \- Goal maximization (features: no bid; a total budget and campaign period or a daily budget must be set) | Auction strategy |
| banner\_uniq\_shows\_limit | integer | readablewritablemax\_value=2147483647 | Number of unique impressions for banners |
| banners | list of [Banner](https://ads.vk.com/en/doc/api/object/Banner) | writablecreate\_only | Banners |
| budget\_limit | decimal | readablewritable | Total group budget |
| budget\_limit\_day | decimal | readablewritable | Daily group budget |
| date\_end | date | readablewritable | Group end date |
| date\_start | date | readablewritable | Group start date |
| delivery | string | readable<br>choices = <br>- pending<br>- delivering<br>- not\_delivering | Group delivery status |
| dynamic\_banners\_use\_storelink | boolean | readablewritable | Whether to show a deeplink in mobile dynamic remarketing |
| dynamic\_without\_remarketing | boolean | readablewritable | Ability to show dynamic remarketing banners without dynamic remarketing events |
| enable\_offline\_goals | boolean | readablewritable | Count offline conversions for the group |
| enable\_utm | boolean | readablewritable | Whether to add UTM tags to ad URLs |
| issues | list of object | readable | Description of reasons why the group's ads are not being shown (template variables are shown in curly braces):<br>- ACCOUNT\_INACTIVE \- Account is inactive.<br>- AD\_PLAN\_ARCHIVED \- The ad plan is removed.<br>- AD\_PLAN\_OUT\_OF\_DATE\_END \- Current date does not satisfy ad\_plan settings: end date is {date\_end}.<br>- AD\_PLAN\_OUT\_OF\_DATE\_START \- Current date does not satisfy ad\_plan settings: start date is {date\_start}.<br>- AD\_PLAN\_STOPPED \- The ad plan is stopped.<br>- ARCHIVED \- The campaign is removed.<br>- BALANCE\_OUT\_OF\_DAILY\_LIMIT \- The account has reached the daily limit of {limit\_value}<br>- BALANCE\_OUT\_OF\_FULL\_LIMIT \- The account has reached the balance limit {limit\_value}<br>- BALANCE\_OUT\_OF\_MONTHLY\_A\_LIMIT \- The account has reached the monthly limit of {limit\_value}<br>- BALANCE\_OUT\_OF\_MONTHLY\_LIMIT \- The account has reached the monthly limit of {limit\_value}<br>- BANNER\_FORMAT\_DELETED \- Ad format is obsolete and not supported anymore. You can not change campaign settings or add new ads into it.<br>- CHECK\_STOPPED \- Please check your campaign settings and resume.<br>- COUNTER\_DELETED \- Counter {counter} was deleted and campaign was stopped.<br>- DOOH\_NO\_MONEY \- Not enough balance for amount {amount}<br>- DOOH\_PAD\_DELETED \- Not enough surfaces<br>- GOAL\_DELETED \- Goal with string {goal} of {counter} was deleted and campaign was stopped.<br>- LAL\_ARCHIVED \- Look-alike {lookalike\_id} was archived and campaign was stopped.<br>- LAL\_FAILED \- Look-alike {lookalike\_id} was failed and campaign was stopped.<br>- NO\_ALLOWED\_BANNERS \- The campaign has no banners, approved by moderation.<br>- NO\_BANNERS\_WITH\_ACTIVE\_STATUS \- The campaign has no active banners.<br>- NO\_MONEY \- The account has no enough money.<br>- OFFER\_GROUP\_NOT\_LOADED \- Pricelist offer group is not loaded.<br>- OUT\_OF\_DATE\_END \- Current date does not satisfy campaign settings: end date is {date\_end}.<br>- OUT\_OF\_DATE\_START \- Current date does not satisfy campaign settings: start date is {date\_start}.<br>- OUT\_OF\_DAY\_LIMIT \- The campaign has reached the daily budget limit {day\_limit} {currency}.<br>- OUT\_OF\_FULL\_LIMIT \- The campaign has reached the full budget limit {full\_limit} {currency}.<br>- OUT\_OF\_TIME\_TARGETING \- The campaign is out of time targeting. Delivery will start at {time\_start}.<br>- PACKAGE\_DELETED \- Ad format is obsolete and not supported anymore. You can not change campaign settings or add new ads into it.<br>- PACKAGE\_UNAVAILABLE \- Ad format is not available for this account<br>- PARENT\_ACCOUNT\_INACTIVE \- Parent account is inactive.<br>- PRICELIST\_DELETED \- Pricelist {pricelist} was deleted and campaign was stopped.<br>- PRICELIST\_OFFER\_GROUP\_DELETED \- Offer group {offer\_group} for pricelist {pricelist} was deleted and campaign was stopped.<br>- REMARKETING\_AUDIENCE\_CHANGED \- Audience {audience} was changed and campaign was stopped.<br>- SEGMENT\_CHANGED \- Segment {segment} was changed and campaign was stopped.<br>- SEGMENT\_DELETED \- Segment {segment} was deleted and campaign was stopped.<br>- SK\_AD\_CAMPAIGN\_ID\_WITHDRAWN \- iOS ads id for campaign was withdrawn<br>- STOPPED \- The campaign is stopped. |
| language | string | readablewritable<br>choices = <br>- ru<br>- en | Language of creatives in the group |
| marketplace\_app\_client\_id | string | readablewritable | ID of the application that will manage the group |
| max\_price | decimal | readablewritablemax\_value=21474836 | Upper bound for automatic price adjustment |
| objective | string | readablewritable | Ad group objective; must match one of the objectives defined in `package.objective` |
| package\_priced\_event\_type | integer | readable | Identifier of the event the group delivery is optimized for. See [Package](https://ads.vk.com/en/doc/api/object/Package) |
| price | decimal | readablewritable | Price per event. The event type is determined by the group's package. |
| priced\_goal | [PricedGoal](https://ads.vk.com/en/doc/api/object/PricedGoal) | readablewritable | Payment by TOP goals / in-app events |
| pricelist\_id | integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Identifier of the remarketing price list |
| sk\_ad\_campaign\_id | integer or null | readablemin\_value=1max\_value=100 | Identifier of the SkAd Network group. Assigned when using iOS 14.5+ targeting. See [MobileApps](https://ads.vk.com/en/doc/api/resource/MobileApps), [SkAdNetworkIdentityShare](https://ads.vk.com/en/doc/api/resource/SkAdNetworkIdentityShare), and [SkAdNetworkIdentityWithdraw](https://ads.vk.com/en/doc/api/resource/SkAdNetworkIdentityWithdraw). |
| targetings | [Targetings](https://ads.vk.com/en/doc/api/object/Targetings) | readablewritable | Targeting structure |
| uniq\_shows\_limit | integer | readablewritablemax\_value=2147483647 | Number of unique impressions |
| uniq\_shows\_period | string | readablewritable<br>choices = <br>- day \- Day<br>- week \- Week<br>- month \- Month<br>- eternity \- Always | Impression periods |
| utm | text | readablewritable | UTM tags to be added to ad URLs. If not specified and `enable_utm=true`, the tags will be generated automatically. If `enable_utm=false`, tags will not be added to ad URLs even if specified. |
| not\_ad | boolean | readablewritable | Whether the group's banners are non-advertising content |
