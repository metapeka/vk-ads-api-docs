# LocalGeoPointTargeting

A point on the map.

Used in objects: [LocalGeoTargeting](https://ads.vk.com/en/doc/api/object/LocalGeoTargeting)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| address | string | readablewritable | Point address |
| label | string | readablewritable | Point name |
| lat | decimal | readablerequiredwritable | Latitude |
| lng | decimal | readablerequiredwritable | Longitude |
| radius | integer | readablerequiredwritablemin\_value=500max\_value=10000 | Radius, in meters |
