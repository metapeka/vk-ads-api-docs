# LocalGeoPoint

An object containing information about a specific geographic area.

Used in objects: [LocalGeo](https://ads.vk.com/en/doc/api/object/LocalGeo)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| address | string | readablewritabledefault\_field | Exact address |
| label | string | readablerequiredwritabledefault\_field | Name |
| lat | float | readablerequiredwritabledefault\_fieldmin\_value=-90max\_value=90 | Latitude of the area's center |
| lng | float | readablerequiredwritabledefault\_fieldmin\_value=-180max\_value=180 | Longitude of the area's center |
| radius | integer | readablerequiredwritabledefault\_fieldmin\_value=500max\_value=10000 | Area radius, in meters |
