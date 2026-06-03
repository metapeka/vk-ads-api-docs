# MobileOperatingSystemsSkAdNetworkTargeting

Targeting for iOS 14.5+ using SkAd Network.

Used in objects: [Targetings](https://ads.vk.com/en/doc/api/object/Targetings)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| app\_url\_id | integer | readablewritablemax\_value=2147483647 | ID of the [URL](https://ads.vk.com/en/doc/api/object/URL) associated with the campaign's iOS app |
| mobile\_operation\_systems\_ids | list of integer | readablewritablemax\_value=2147483647 | IDs of mobile operating systems. [List of available OS](https://ads.vk.com/en/doc/api/resource/MobileOperationSystem). You cannot use the same operating systems that are already used in the [mobile\_operation\_system](https://ads.vk.com/en/doc/api/object/Targetings) targeting. |
