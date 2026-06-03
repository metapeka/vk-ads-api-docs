# InAppTracker

The object describes event tracker monitoring a mobile app.

Used in objects: [RemarketingInAppEvent](https://ads.vk.com/en/doc/api/object/RemarketingInAppEvent)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| events | list of [InAppEvent](https://ads.vk.com/en/doc/api/object/InAppEvent) | readabledefault\_field | Events registered in the tracker. |
| id | id | readabledefault\_fieldmin\_value=1max\_value=2147483647 | Tracker ID. |
| name | string | readabledefault\_field | Tracker name. |
