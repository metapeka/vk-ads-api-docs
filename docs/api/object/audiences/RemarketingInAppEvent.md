# RemarketingInAppEvent

Data source is an event in a mobile app.

Used in resources: [RemarketingInAppEvents](https://ads.vk.com/en/doc/api/resource/RemarketingInAppEvents)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| app\_name | string | readabledefault\_field | Mobile app name. |
| created | datetime | readable | Date when the app was added to VK Ads. |
| platform | string | readabledefault\_field | Mobile app platform. |
| rb\_mobile\_app\_id | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | Mobile app ID. |
| status | string | readabledefault\_field<br>choices = <br>- new \- moderation of connection application<br>- approved \- mobile application is connected with account | Mobile application connection status. |
| trackers | list of [InAppTracker](https://ads.vk.com/en/doc/api/object/InAppTracker) | readabledefault\_field | Trackers that monitor the app. |
| url | string | readabledefault\_field | Link to the mobile app. |
| url\_object\_id | string | readabledefault\_field | ID of the related object. |
