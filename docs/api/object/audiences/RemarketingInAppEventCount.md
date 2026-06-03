# RemarketingInAppEventCount

The object describes the number of app events that occurred in the last few days.

Used in objects: [InAppEvent](https://ads.vk.com/en/doc/api/object/InAppEvent)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| rows | list of [RemarketingInAppEventCountDate](https://ads.vk.com/en/doc/api/object/RemarketingInAppEventCountDate) | readabledefault\_field | The number of events on the specified date. |
| total | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Total number of events. |
