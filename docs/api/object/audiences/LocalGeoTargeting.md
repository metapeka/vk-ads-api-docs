# LocalGeoTargeting

Local advertising.

Used in objects: [Targetings](https://ads.vk.com/en/doc/api/object/Targetings), [GeoTargeting](https://ads.vk.com/en/doc/api/object/GeoTargeting)

| Field name | Type | Conditions | Description |
| --- | --- | --- | --- |
| loc\_type | list of string | readablewritable | Visit time. Possible values: `home`, `work` |
| locations | list of [LocalGeoPointTargeting](https://ads.vk.com/en/doc/api/object/LocalGeoPointTargeting) | readablerequiredwritable | List of points |
| visit\_type | string | readablerequiredwritable<br>choices = <br>- now \- Now<br>- usual \- Usually<br>- all \- Usually or now | Visit type |
