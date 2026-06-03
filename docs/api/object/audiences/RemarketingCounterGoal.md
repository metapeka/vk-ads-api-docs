# RemarketingCounterGoal

Counter goal.

Used in resources: [CounterGoals](https://ads.vk.com/en/doc/api/resource/CounterGoals), [CounterGoal](https://ads.vk.com/en/doc/api/resource/CounterGoal)

Used in objects: [RemarketingCounter](https://ads.vk.com/en/doc/api/object/RemarketingCounter)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| condition | string | readablerequiredwritablecreate\_only<br>choices = <br>- uss \- Substring in URL.<br>- rss \- Substring in Referer.<br>- jse \- JS event.<br>- hd \- Pages depth (minimum 2).<br>- ts \- Time the user spent on the website. | Type of condition for the goal achievement. |
| goal\_type | string | readablewritable<br>choices = <br>- content \- User viewed content.<br>- search \- User made a search.<br>- basket \- User added item to the cart.<br>- wishlist \- User added item to the wishlist.<br>- checkout \- User initiated checkout procedure.<br>- payment\_info \- User added payment details.<br>- purchase \- User completed purchase.<br>- lead \- Lead.<br>- registration \- User completed registration.<br>- custom \- User conversion rate. | Goal type (required for the goals other than pixels). |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Goal ID. |
| name | string | readablerequiredwritable | Goal name. |
| substr | string | readablerequiredwritablecreate\_only | Goal condition string (substr or substr\_uss, substr\_rss, ...). |
| value | integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Number of times the goal was achieved. |
