# RemarketingCounter

Data source is a [Top@Mail.ru](https://top.mail.ru/) counter.

Used in resources: [RemarketingCounters](https://ads.vk.com/en/doc/api/resource/RemarketingCounters), [RemarketingCounter](https://ads.vk.com/en/doc/api/resource/RemarketingCounter)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| counter\_id | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Counter ID in [Top@Mail.ru](https://top.mail.ru/). |
| created | datetime | readabledefault\_field | Time of counter creation. |
| domain | string | readable | Counter domain. |
| flags | list of string | readablewritabledefault\_field | Additional options: "cookie\_sync" enable cookie synchronization. |
| goals | list of [RemarketingCounterGoal](https://ads.vk.com/en/doc/api/object/RemarketingCounterGoal) | readable | List of counter goals. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Counter ID. |
| name | string | readablewritabledefault\_field | Counter name. |
| status | string | readabledefault\_field<br>choices = <br>- active \- Counter is active.<br>- deleted \- Counter was deleted from [Top@Mail.ru](https://top.mail.ru/).<br>- blocked \- Counter is not used. | Counter status in [Top@Mail.ru](https://top.mail.ru/). |
| system\_status | string | readabledefault\_field<br>choices = <br>- active \- Counter is active (the user owns the counter or was granted access to it).<br>- deleted \- Counter is not used.<br>- blocked \- Counter is awaiting the owner approval. | System status (active/blocked/deleted). Possible values: - active/blocked - awaits owner approval - deleted - not used |
| type | string | readable<br>choices = <br>- own \- Counter was added by the user.<br>- shared \- Counter is shared with another user. | Counter ownership. |
| users | list of [RemarketingCounterUser](https://ads.vk.com/en/doc/api/object/RemarketingCounterUser) | readable | Users who can access the counter. |
| users\_count | integer | readablemin\_value=-2147483647max\_value=2147483647 | Number of users who can access the counter. |
| working | boolean | readabledefault\_field | Counter activity flag. |
