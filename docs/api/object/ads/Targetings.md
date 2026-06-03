# Targetings

Targetings. Available targetings are described in the [package object](https://ads.vk.com/en/doc/api/object/Package) within which the campaign is created.

Used in objects: [AdGroup](https://ads.vk.com/en/doc/api/object/AdGroup)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| age | [AgeTargeting](https://ads.vk.com/en/doc/api/object/AgeTargeting) | readablewritable | Age (list of ages). `0` — show to users whose age is not defined |
| birthday | [BirthdayTargeting](https://ads.vk.com/en/doc/api/object/BirthdayTargeting) | readablewritable | Birthday |
| fulltime | [FulltimeTargeting](https://ads.vk.com/en/doc/api/object/FulltimeTargeting) | readablewritable | Time (days and hours) |
| geo | [GeoTargeting](https://ads.vk.com/en/doc/api/object/GeoTargeting) | readablewritable | General geo targeting combining [geolocations](https://ads.vk.com/en/doc/api/object/LocalGeoTargeting) and regions (list of region IDs). Only one of the values can be set: `local_geo` or `regions`. [List of available regions](https://ads.vk.com/en/doc/api/resource/Region) |
| group\_members | string | readablewritable<br>choices = <br>- all \- All<br>- group\_member \- In the group<br>- not\_group\_member \- Not in the group | OK/VK group membership |
| interests | list of integer | readablewritablemax\_value=2147483647 | User interests. [List of available interests](https://ads.vk.com/en/doc/api/resource/TargetingsTree) |
| interests\_soc\_dem | list of integer | readablewritablemax\_value=2147483647 | Socio-demographic user interests. [List of available interests](https://ads.vk.com/en/doc/api/resource/TargetingsTree) |
| interests\_stable | list of integer | readablewritablemax\_value=2147483647 | Long-term user interests. [List of available interests](https://ads.vk.com/en/doc/api/resource/TargetingsTree) |
| local\_geo | [LocalGeoTargeting](https://ads.vk.com/en/doc/api/object/LocalGeoTargeting) | readablewritable | Geolocation targeting |
| mobile\_apps | string | readablewritable<br>choices = <br>- never\_installed \- Never installed<br>- now \- Installed now<br>- deleted \- Deleted now | App installation status |
| mobile\_operation\_systems | list of integer | readablewritablemax\_value=2147483647 | Mobile operating systems. [List of available OS](https://ads.vk.com/en/doc/api/resource/MobileOperationSystem) |
| mobile\_operators | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Mobile carriers. [List of available carriers](https://ads.vk.com/en/doc/api/resource/MobileOperator) |
| mobile\_prefix | list of string | readablewritable | Mobile prefixes. Available prefixes: `mts`, `beeline`, `megafon` |
| mobile\_types | list of string | readablewritable | Mobile device types. [List of available devices](https://ads.vk.com/en/doc/api/resource/MobileTypes) |
| mobile\_vendors | list of integer | readablewritablemax\_value=2147483647 | Mobile device manufacturers. [List of available manufacturers](https://ads.vk.com/en/doc/api/resource/MobileVendors) |
| pad\_category | [PadCategoryTargeting](https://ads.vk.com/en/doc/api/object/PadCategoryTargeting) | readablewritable | App category targeting |
| pads | list of id | readablewritablemin\_value=1max\_value=2147483647 | Ad placements. Available placements are defined in the campaign package |
| regions | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Regions (list of region IDs). [List of available regions](https://ads.vk.com/en/doc/api/resource/Region) |
| segments | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Membership in [audience segments](https://ads.vk.com/en/doc/api/resource/Segments) |
| sex | list of string | readablewritable | Gender (combinations of `male` and `female`) |
| mobile\_operation\_systems\_sk\_ad\_network | [MobileOperatingSystemsSkAdNetworkTargeting](https://ads.vk.com/en/doc/api/object/MobileOperatingSystemsSkAdNetworkTargeting) | readablewritable | Targeting for iOS 14.5+ via SkAd Network |
| device\_types | list of string | readablewritable | Device targeting (`desktop` — 1, `mobile` — 2) |
