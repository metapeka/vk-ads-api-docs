# MobileApps

An object that describes a mobile app available to the user, along with the list of users who have access to it.

Used in resources: [MobileApps](https://ads.vk.com/en/doc/api/resource/MobileApps)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| app\_name | string | readabledefault\_field | Mobile app name |
| campaign\_ids | list of integer | readablemax\_value=2147483647 | Array of campaign IDs associated with this mobile app |
| platform | string | readabledefault\_field | Mobile app platform identifier |
| preview\_url | url | readable | Preview image URL |
| rb\_mobile\_app\_id | integer | readabledefault\_fieldmax\_value=2147483647 | Internal mobile app ID |
| category\_id | integer | readablemax\_value=2147483647 | Internal mobile app category ID |
| sk\_ad\_network\_ids | [SkAdNetworkIdsCounts](https://ads.vk.com/en/doc/api/object/SkAdNetworkIdsCounts) | readable | Object with information about available and used SkAd Network campaign identifiers |
| url | string | readable | App URL |
| url\_object\_id | string | readabledefault\_field | Internal identifier of the app URL |
| users | list of objects | readable | Users who have access to the mobile app |
