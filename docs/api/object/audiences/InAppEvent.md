# InAppEvent

The object describes an event in a mobile app.

Used in resources: [InAppEvent](https://ads.vk.com/en/doc/api/resource/InAppEvent)

Used in objects: [InAppTracker](https://ads.vk.com/en/doc/api/object/InAppTracker)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| count | [RemarketingInAppEventCount](https://ads.vk.com/en/doc/api/object/RemarketingInAppEventCount) | readabledefault\_field | The number of events that occurred in the last few days. |
| id | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Event ID. |
| inapp\_event\_category\_id | integer | readablewritabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Event category id. |
| name | string | readabledefault\_field | Event name. |
| campaign\_ids | list of integer | readabledefault\_field | Campaigns in which this event is used. |
