# LeadFormAward

An object describing the reward for completing a lead form. Reward information will be displayed on every page of the form.

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| type | string | readablewritablerequired<br>choices = <br>- discount \- Discount<br>- bonus \- Bonus | Reward type |
| data | [Discount](https://ads.vk.com/en/doc/api/object/LeadFormDiscount) or [Bonus](https://ads.vk.com/en/doc/api/object/LeadFormBonus) | readablewritablerequired | Depending on the selected reward type, different data objects are provided. For type=discount, this is [Discount](https://ads.vk.com/en/doc/api/object/LeadFormDiscount); for type=bonus, it is [Bonus](https://ads.vk.com/en/doc/api/object/LeadFormBonus). |
