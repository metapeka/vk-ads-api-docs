# LocalGeo

A local geography list.

Used in resources: [LocalGeos](https://ads.vk.com/en/doc/api/resource/LocalGeos), [LocalGeo](https://ads.vk.com/en/doc/api/resource/LocalGeo)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| id | integer | readabledefault\_fieldmin\_value=-2147483647max\_value=2147483647 | List identifier |
| name | string | readablerequiredwritabledefault\_field | List name |
| regions | list of [LocalGeoPoint](https://ads.vk.com/en/doc/api/object/LocalGeoPoint) | readablerequiredwritabledefault\_field | List of regions specified by the user |
