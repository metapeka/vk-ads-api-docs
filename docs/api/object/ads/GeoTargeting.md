# GeoTargeting

General geo targeting. Only one of the values can be set: `local_geo` or `regions`.

For region targeting, negative targeting is supported. To use it, pass a negative region identifier.

[List of available regions](https://ads.vk.com/en/doc/api/resource/Region)

Used in objects: [Targetings](https://ads.vk.com/en/doc/api/object/Targetings)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| local\_geo | [LocalGeoTargeting](https://ads.vk.com/en/doc/api/object/LocalGeoTargeting) | readablewritable | Geolocation |
| regions | list of integer | readablewritablemin\_value=-2147483647max\_value=2147483647 | Regions (list of region IDs). [List of available regions](https://ads.vk.com/en/doc/api/resource/Region) |
