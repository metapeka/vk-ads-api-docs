# PricedGoal

Payment based on TOP goals / in-app events.

Used in objects: [AdPlan](https://ads.vk.com/en/doc/api/object/AdPlan), [AdGroup](https://ads.vk.com/en/doc/api/object/AdGroup)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| name | string | readablerequiredwritable | Event name or goal identifier in the `condition:substr` format |
| source\_id | id | readablerequiredwritabledefault\_fieldmin\_value=1max\_value=2147483647 | ID of the in-app event tracker or the counter ID of [Top@Mail.ru](https://top.mail.ru/) |
